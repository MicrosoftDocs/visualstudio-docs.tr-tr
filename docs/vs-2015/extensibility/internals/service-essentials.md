---
title: Hizmet temel bileşenleri | Microsoft Docs
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
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90cec13c403194c70b9d44cff349b53495a0e160
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776466"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sözleşme iki Vspackage'lar arasında olan bir hizmettir. Bir VSPackage'ı kullanmak başka bir VSPackage arabirimleri belirli sunmaktadır. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kendisini diğer Vspackages'a hizmetleri sağlayan VSPackages oluşan bir koleksiyondur.  
  
 Örneğin, etkinlik günlüğüne yazmak için kullanabileceğiniz bir IVsActivityLog arabirimi almak için SVsActivityLog hizmetini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: etkinlik günlüğü'nün](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ayrıca, kayıtlı olmayan bazı yerleşik hizmetler sağlar. VSPackage'ları, yerleşik veya diğer Hizmetleri hizmeti geçersiz kılma sağlayarak değiştirebilirsiniz. Yalnızca bir hizmeti geçersiz kılma için herhangi bir hizmeti izin verilir.  
  
 Hiçbir bulunabilirliği hizmetleriniz var. Bu nedenle, hizmet tanımlayıcısı (SID) kullanmak isteyen bir hizmetin bilmeniz gerekir ve sağladığı hangi arabirimleri bilmeniz gerekir. Hizmet için başvuru belgeleri, bu bilgileri sağlar.  
  
-   Hizmet sağlayan VSPackages hizmet sağlayıcıları çağrılır.  
  
-   Küresel hizmetler, diğer Vspackages'a sağlanan hizmetleri çağrılır.  
  
-   Bunları uygulayan VSPackage veya oluşturur, herhangi bir nesne için kullanılabilen hizmetler, yerel Hizmetleri olarak adlandırılır.  
  
-   Yerleşik hizmetlere ya da diğer paketleri tarafından sağlanan hizmetleri değiştirmek Hizmetleri hizmeti geçersiz kılmaları çağrılır.  
  
-   Hizmetleri ya da hizmeti geçersiz kılmaları, isteğe bağlı olarak yüklenen, sağladığı hizmet başka bir VSPackage'ı tarafından istendiğinde, diğer bir deyişle, hizmet sağlayıcısı yüklenir.  
  
-   İsteğe bağlı yükleme desteklemek için bir hizmet sağlayıcısı, küresel hizmetler ile kaydeder [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Daha fazla bilgi için [kayıt hizmetleri](../../misc/registering-services.md).  
  
-   Bir hizmet edindikten sonra kullanın [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (yönetilmeyen kod) veya istenen arabirim, örneğin almak için (yönetilen kod için) atama:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Yönetilmeyen kod bir hizmet tarafından GUID'sine başvuruyor ancak yönetilen kod bir hizmet türünü ifade eder.  
  
-   Zaman [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yükleri VSPackage bir VSPackage'ı için küresel hizmetler VSPackage erişim vermek için bir hizmet sağlayıcısı geçirir. Bu "VSPackage siting" olarak adlandırılır.  
  
-   VSPackage oluşturdukları nesneler için hizmet sağlayıcıları olabilir. Örneğin, bir form renk hizmet isteği isteği geçebilir çerçevesini gönderebilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   İç içe girmiş veya hiç tarihli değil yönetilen nesneleri çağırıp <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> küresel hizmetler doğrudan erişim için. Daha fazla bilgi için [nasıl yapılır: kullanım GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanılabilen hizmetlerin listesi](../../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md)   
 [Atama ve tür dönüşümleri](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Atama](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

