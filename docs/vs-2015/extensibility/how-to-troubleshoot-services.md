---
title: 'Nasıl yapılır: Hizmetleri sorunlarını giderme | Microsoft Docs'
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
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8df01dcc2c8e15144f6049148286012bda6ac3f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798215"
---
# <a name="how-to-troubleshoot-services"></a>Nasıl yapılır: hizmetlerde sorun giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir hizmet almayı deneyin gerektiğinde oluşabilecek bazı ortak sorunlar vardır:  
  
- Hizmet ile kayıtlı değil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Arabirim türü ve hizmet türü tarafından değil hizmet istenen.  
  
- Hizmet isteyen VSPackage tarihli değil.  
  
- Yanlış hizmet sağlayıcısı kullanılır.  
  
  İstenen hizmet elde edilemiyor varsa, çağrı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null döndürür. Bir hizmet istedikten sonra her zaman null için test etmeniz gerekir:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Bir hizmette sorun gidermek için  
  
1.  Hizmet doğru şekilde kayıtlı olup olmadığını görmek için sistem kayıt defterine inceleyin. Daha fazla bilgi için [kayıt hizmetleri](../misc/registering-services.md).  
  
     Aşağıdaki .reg dosyasını parçası nasıl SVsTextManager hizmet kayıtlı gösterir:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Yukarıdaki örnekte, sürüm numarası sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]12.0 veya 14.0, ' % s'anahtarı {F5E7E71D-1401-11d1-883B-0000F87579D2} hizmeti, SVsTextManager ve varsayılan değer {hizmet tanımlayıcısı (SID) gibi F5E7E720-1401-11D1-883B-0000F87579D2} GUID metin Yöneticisi hizmeti sağlayan VSPackage paketidir.  
  
2.  GetService çağırdığınızda hizmet türü ve arabirim türünü kullanın. Bir hizmet isteğinde bulunurken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:Microsoft.VisualStudio.Shell.Package> GUID türünden çıkarır. Aşağıdaki koşullar doğruysa, bir hizmet bulunmaz:  
  
    1.  Bir arabirim türü yerine hizmet türünün GetService için geçirilir.  
  
    2.  Hiçbir GUID arabirime açıkça atanır. Bu nedenle, sistem gerektiği gibi bir nesne için varsayılan bir GUID oluşturur.  
  
3.  Hizmet isteyen VSPackage tarihli emin olun. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sonra oluşturmak ve çağırmadan önce VSPackage siteleri <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Bir hizmet gerektiren bir VSPackage oluşturucuda kodunuz varsa, bu dosyayı Initialize yöntemi başına taşıyın.  
  
4.  Doğru hizmet sağlayıcısı kullandığınızdan emin olun.  
  
     Tüm hizmet sağlayıcıları benzer. Hizmet sağlayıcısı, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vspackage'a başarılı bir geçiş için bir araç penceresi farklıdır. Araç penceresi hizmet sağlayıcısı bildiği <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, hakkında bilgi sahibi değildir ancak <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> VSPackage hizmet sağlayıcısından bir araç penceresi içinden almak için.  
  
     Araç penceresi, bir kullanıcı denetimi veya başka bir denetim kapsayıcısı barındırıyorsa, kapsayıcı tarafından Windows Bileşen modeli tarihli ve herhangi bir erişim sağlamazsınız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hizmetleri. Çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> bir VSPackage hizmet sağlayıcısından bir denetim kapsayıcısı içinden almak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanılabilen hizmetlerin listesi](../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)

