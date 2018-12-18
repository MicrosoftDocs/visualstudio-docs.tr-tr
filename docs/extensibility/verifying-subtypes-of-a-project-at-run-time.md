---
title: Çalışma zamanında proje alt türlerini doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22e3205f3a8bd8ef7ce7e44b775ae1ef5a30cfa5
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586215"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Çalışma zamanında proje alt türlerini doğrulama
Özel proje alt türü üzerinde olduğu bir VSPackage'ı alt tür ve böylece alt mevcut değilse düzgün bir şekilde devredebilirsiniz aramak için mantık eklemeniz gerekir. Aşağıdaki yordam, belirtilen alt varlığını doğrulamak gösterilmektedir.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Bir alt varlığını doğrulamak için  
  
1.  Proje ve çözüm nesneler olarak proje hiyerarşisi alın bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , VSPackage için aşağıdaki kodu ekleyerek nesne.  
  
    ```csharp  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Hiyerarşi için cast <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> arabirimi.  
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Çağırarak proje türü GUID'ın listesini alın <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Belirtilen alt türe GUİD'i kontrol edin.  
  
    ```csharp  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Proje alt türleri](../extensibility/internals/project-subtypes.md)   
 [Proje alt türleri tasarımı](../extensibility/internals/project-subtypes-design.md)   
 [Özellikleri ve yöntemleri proje alt türleri tarafından genişletilen](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)