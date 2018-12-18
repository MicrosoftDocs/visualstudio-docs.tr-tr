---
title: 'Nasıl yapılır: Hizmetleri sorunlarını giderme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d2e1e59b5d2bd1210511b355676407a1368143f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834220"
---
# <a name="how-to-troubleshoot-services"></a>Nasıl yapılır: hizmetlerde sorun giderme
Bir hizmet almayı deneyin gerektiğinde oluşabilecek bazı ortak sorunlar vardır:  
  
- Hizmet ile kayıtlı değil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Arabirim türü ve hizmet türü tarafından değil hizmet istenen.  
  
- Hizmet isteyen VSPackage tarihli değil.  
  
- Yanlış hizmet sağlayıcısı kullanılır.  
  
  İstenen hizmet elde edilemiyor varsa, çağrı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null döndürür. Bir hizmet istedikten sonra her zaman null için test etmeniz gerekir:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="to-troubleshoot-a-service"></a>Bir hizmette sorun gidermek için  
  
1. Hizmet doğru şekilde kayıtlı olup olmadığını görmek için sistem kayıt defterine inceleyin. Daha fazla bilgi için [nasıl yapılır: bir hizmet sağlamak](../extensibility/how-to-provide-a-service.md).  
  
    Aşağıdaki *.reg* dosya parça gösterir nasıl SVsTextManager hizmet kayıtlı:  
  
   ```  
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
   "Name"="SVsTextManager"  
   ```  
  
    Yukarıdaki örnekte, sürüm numarası sürümüdür [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]12.0 veya 14.0, ' % s'anahtarı {F5E7E71D-1401-11d1-883B-0000F87579D2} hizmeti, SVsTextManager ve varsayılan değer {hizmet tanımlayıcısı (SID) gibi F5E7E720-1401-11D1-883B-0000F87579D2} GUID metin Yöneticisi hizmeti sağlayan VSPackage paketidir.  
  
2. GetService çağırdığınızda hizmet türü ve arabirim türünü kullanın. Bir hizmet isteğinde bulunurken [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> GUID türünden çıkarır. Aşağıdaki koşullar doğruysa, bir hizmet bulunmaz:  
  
   1.  Bir arabirim türü yerine hizmet türünün GetService için geçirilir.  
  
   2.  Hiçbir GUID arabirime açıkça atanır. Bu nedenle, sistem gerektiği gibi bir nesne için varsayılan bir GUID oluşturur.  
  
3. Hizmet isteyen VSPackage tarihli emin olun. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sonra oluşturmak ve çağırmadan önce VSPackage siteleri <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
    Bir hizmet gerektiren bir VSPackage oluşturucuda kodunuz varsa, taşımak için `Initialize` yöntemi.  
  
4. Doğru hizmet sağlayıcısı kullandığınızdan emin olun.  
  
    Tüm hizmet sağlayıcıları benzer. Hizmet sağlayıcısı, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vspackage'a başarılı bir geçiş için bir araç penceresi farklıdır. Araç penceresi hizmet sağlayıcısı bildiği <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, hakkında bilgi sahibi değildir ancak <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> VSPackage hizmet sağlayıcısından bir araç penceresi içinden almak için.  
  
    Araç penceresi, bir kullanıcı denetimi veya başka bir denetim kapsayıcısı barındırıyorsa, kapsayıcı tarafından Windows Bileşen modeli tarihli ve herhangi bir erişim sağlamazsınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hizmetleri. Çağırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> bir VSPackage hizmet sağlayıcısından bir denetim kapsayıcısı içinden almak için.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanılabilen hizmetlerin listesi](../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri sağlamak ve kullanın](../extensibility/using-and-providing-services.md)   
 [Hizmet temel bileşenleri](../extensibility/internals/service-essentials.md)