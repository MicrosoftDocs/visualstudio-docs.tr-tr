---
title: Hizmet temel bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26bfa7ce51249adc883415d09689ed390b7dfabc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934411"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
Bir sözleşme iki Vspackage'lar arasında olan bir hizmettir. Bir VSPackage'ı kullanmak başka bir VSPackage arabirimleri belirli sunmaktadır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kendisini diğer Vspackages'a hizmetleri sağlayan VSPackages oluşan bir koleksiyondur.  
  
 Örneğin, etkinlik günlüğüne yazmak için kullanabileceğiniz bir IVsActivityLog arabirimi almak için SVsActivityLog hizmetini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: etkinlik günlüğü'nün](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayrıca, kayıtlı olmayan bazı yerleşik hizmetler sağlar. VSPackage'ları, yerleşik veya diğer Hizmetleri hizmeti geçersiz kılma sağlayarak değiştirebilirsiniz. Yalnızca bir hizmeti geçersiz kılma için herhangi bir hizmeti izin verilir.  
  
 Hiçbir bulunabilirliği hizmetleriniz var. Bu nedenle, hizmet tanımlayıcısı (SID) kullanmak isteyen bir hizmetin bilmeniz gerekir ve sağladığı hangi arabirimleri bilmeniz gerekir. Hizmet için başvuru belgeleri, bu bilgileri sağlar.  
  
- Hizmet sağlayan VSPackages hizmet sağlayıcıları çağrılır.  
  
- Küresel hizmetler, diğer Vspackages'a sağlanan hizmetleri çağrılır.  
  
- Bunları uygulayan VSPackage veya oluşturur, herhangi bir nesne için kullanılabilen hizmetler, yerel Hizmetleri olarak adlandırılır.  
  
- Yerleşik hizmetlere ya da diğer paketleri tarafından sağlanan hizmetleri değiştirmek Hizmetleri hizmeti geçersiz kılmaları çağrılır.  
  
- Hizmetleri ya da hizmeti geçersiz kılmaları, isteğe bağlı olarak yüklenen, sağladığı hizmet başka bir VSPackage'ı tarafından istendiğinde, diğer bir deyişle, hizmet sağlayıcısı yüklenir.  
  
- İsteğe bağlı yükleme desteklemek için bir hizmet sağlayıcısı, küresel hizmetler ile kaydeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daha fazla bilgi için [nasıl yapılır: bir hizmet sağlamak](../../extensibility/how-to-provide-a-service.md).  
  
- Bir hizmet edindikten sonra kullanın [QueryInterface](/cpp/atl/queryinterface) (yönetilmeyen kod) veya istenen arabirim, örneğin almak için (yönetilen kod için) atama:  
  
  ```vb  
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
  ```  
  
  ```csharp  
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  ```  
  
- Yönetilmeyen kod bir hizmet tarafından GUID'sine başvuruyor ancak yönetilen kod bir hizmet türünü ifade eder.  
  
- Zaman [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükleri VSPackage bir VSPackage'ı için küresel hizmetler VSPackage erişim vermek için bir hizmet sağlayıcısı geçirir. Bu "VSPackage siting" olarak adlandırılır.  
  
- VSPackage oluşturdukları nesneler için hizmet sağlayıcıları olabilir. Örneğin, bir form renk hizmet isteği isteği geçebilir çerçevesini gönderebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- İç içe girmiş veya hiç tarihli değil yönetilen nesneleri çağırıp <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> küresel hizmetler doğrudan erişim için.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>GetGlobalService kullanın  
  
Bazen bir araç penceresinden bir hizmet almaya veya değil tarihli, aksi takdirde, istediğiniz hizmeti hakkında bilgi sahibi değildir bir hizmet sağlayıcısı ile tarihli kapsayıcı denetimi gerekebilir. Örneğin, etkinlik günlüğünde denetimdeki yazmak isteyebilirsiniz. Bu ve diğer senaryolar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri sorun giderme](../../extensibility/how-to-troubleshoot-services.md).  
  
Statik çağırarak çoğu Visual Studio Hizmetleri alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> bağımlı bir önbelleğe alınan hizmet, herhangi bir VSPackage türetilmiş paketinden ilk kez başlatılmadan sağlayıcısı tarihli. Bu koşul karşılandığında, aksi takdirde null bir hizmet için hazırlıklı olmalıdır garanti etmeniz gerekir.  
  
Neyse ki, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> çoğu zaman düzgün şekilde çalışır.  
  
-   VSPackage yalnızca başka bir Vspackage'e bilinen hizmet sağlıyorsa, hizmet talep eden VSPackage'ı hizmet yüklü sağlama VSPackage'ı önce tarihli.  
  
-   Araç penceresi tarafından VSPackage oluşturduysanız, araç penceresi oluşturulmadan önce VSPackage tarihli.  
  
-   Bir denetim kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırılıyorsa, Denetim kapsayıcısı oluşturulmadan önce VSPackage tarihli.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Araç penceresi ya da Denetim kapsayıcısı içinden bir hizmetten alınamıyor  
  
-   Bu kod Oluşturucu, araç penceresi veya denetim kapsayıcısı ekleyin:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Bu kod bir SVsActivityLog hizmeti alır ve etkinlik günlüğüne yazmak için kullanılan bir IVsActivityLog arabirime çevirir. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğü'nün](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanılabilen hizmetlerin listesi](../../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md)   
 [Atama ve tür dönüşümleri](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Atama](/cpp/cpp/casting)