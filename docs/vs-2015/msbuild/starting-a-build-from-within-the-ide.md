---
title: IDE içinden derleme başlatma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c741b8dfd0607de41ca7b53bdd88244ae3957a9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230392"
---
# <a name="starting-a-build-from-within-the-ide"></a>IDE İçinden Derleme Başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Özel proje sistemleri kullanmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> yapıları başlatmak için. Bu konu bunun nedenlerini açıklar ve yordamı açıklar.  
  
## <a name="parallel-builds-and-threads"></a>Paralel yapılar ve iş parçacıkları  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ortak kaynaklara erişim için dolayımlama gerektiren paralel yapılar sağlar. Proje sistemleri çalıştırabilirsiniz yapıları zaman uyumsuz olarak, ancak bu tür sistemleri çağrı içinden yapı işlevlerini çağırmamalıdır telefonla geri yapı yöneticisine sağlanan.  
  
 Proje sistemi ortam değişkenlerini değiştiriyorsa, yapı Outofproc olarak ayarlaması gerekir. Bu, bunlar işlemde düğüm gerektirdiklerinden, ana bilgisayar nesnelerini kullanamayacağınız anlamına gelir.  
  
## <a name="using-ivsbuildmanageraccessor"></a>Ivsbuildmanageraccessor kullanma  
 Aşağıdaki kod, proje sistemi bir derlemeyi başlatmak için kullanabileceğiniz bir yöntemin anahatlarını vermektedir:  
  
```  
  
public bool Build(Project project, bool isDesignTimeBuild)  
{  
    // Get the accessor from the IServiceProvider interface for the   
    // project system  
    IVsBuildManagerAccessor accessor =  
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as     
        IVsBuildManagerAccessor;  
    bool releaseUIThread = false;  
    try  
    {  
        if(accessor != null)  
        {  
            // Claim the UI thread under the following conditions:  
            // 1. The build must use a resource that uses the UI thread  
            // or,  
            // 2. The build requires the in-proc node AND waits on the   
            // UI thread for the build to complete  
            if(NeedsUIThread)  
            {  
                int result = accessor.ClaimUIThreadForBuild();  
                if(result != S_OK)  
                {  
                     // Not allowed to claim the UI thread right now  
                     return false;  
                }  
                releaseUIThread = true;  
             }  
             if(isDesignTimeBuild)  
             {  
// Start the design time build  
                  int result = accessor.BeginDesignTimeBuild();  
                  if(result != S_OK)  
                  {  
                      // Not allowed to begin a design-time build at  
                      // this time. Try again later.  
                      return false;  
                  }  
             }  
         }  
         bool buildSucceeded = false;  
         // perform project-system specific build set up tasks  
         // Create your BuildRequestData  
         // This assumes a IHostServices variable (hostServices) set   
   // to your host services. If you don't use a project instance   
         // (you build from a file for example) then use another   
         // constructor.  
         BuildRequestData requestData = new   
             BuildRequestData(project.CreateProjectInstance(),   
             "myTarget", hostServices,   
             BuildRequestData.BuildRequestDataFlags.None);  
         // Mark your your submission as Pending  
         BuildSubmission submission =  
              BuildManager.DefaultBuildManager.  
              PendBuildRequest(requestData);  
         // Register the loggers in BuildLoggers  
         if (accessor != null)  
         {  
               foreach (ILogger logger in BuildLoggers)  
               {  
                    accessor.RegisterLogger(submission.SubmissionId,   
                        logger);  
               }  
         }  
         BuildResult buildResult = submission.Execute();  
         return buildResult;  
     }  
     // Clean up resources  
     finally  
     {  
         if(accessor != null)  
         {  
             // Unregister the loggers, if necessary.  
             accessor.UnregisterLoggers(submission.SubmissionId);  
             // Release the UI thread, if used  
             if(releaseUIThread)  
             {  
                  accessor.ReleaseUIThreadForBuild();  
             }  
             // End the design time build, if used  
             if(isDesignTimeBuild)  
             {  
                  accessor.EndDesignTimeBuild();  
             }  
         }  
     }  
}  
  
```



