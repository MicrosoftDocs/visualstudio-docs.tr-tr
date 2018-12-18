---
title: Tasarımcıyı başlatma ve meta verileri yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58f103ae1dcf445c5bdfe322eeea7a88a7b25683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843281"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Tasarımcı başlatma ve meta verileri yapılandırma
Bir tasarımcı veya Tasarımcısı bileşen ile ilişkili meta verileri ve filtre özniteliklerini işleme uygulamalarının farklı işlemek için kullanılan araçlar tarafından belirli bir tasarımcı tanımlamak bir mekanizma sağlar <xref:System.Type> nesne (örneğin, veri yapıları sınıflar, veya grafik varlıkları) Tasarımcı kullanılabilir olduğunda ve Visual Studio IDE Tasarımcı destekleyecek şekilde nasıl yapılandırıldığını (örnek, **araç kutusu** kategori veya sekme bulunur).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Denetim Tasarımcısı veya tasarımcı bileşenin başlatma ve meta verilerini bir VSPackage'ı tarafından işlenmesini kolaylaştırmak için çeşitli mekanizmalar sağlar.  
  
## <a name="initialize-metadata-and-configuration-information"></a>Meta verileri ve yapılandırma bilgileri Başlat  
 İsteğe bağlı olarak yüklenen olduklarından, VSPackages olarak yüklenmiş olabilir değil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir tasarımcı örneğinin önce ortamı. VSPackage standart mekanizması bir tasarımcı veya tasarımcı bileşeni işlemek için olan oluşturma özelliğini yapılandırmak için bu nedenle, kullanamazsınız bir <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> olay. Bunun yerine, örneği bir VSPackage'ı uygulayan <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> arabirim ve kendi tasarım yüzeyi uzantıları başvurulan özelleştirmeleri sağlamak için kaydeder.  
  
### <a name="customize-initialization"></a>Başlatma özelleştirme  
 Bir tasarımcı, bir bileşen veya bir tasarımcı yüzeyine özelleştirme içerir:  
  
1. Tasarımcı meta verileri değiştirme ve belirli bir nasıl etkili bir şekilde değiştirme <xref:System.Type> erişilen veya dönüştürülür.  
  
    Bu genellikle aracılığıyla yapılır <xref:System.Drawing.Design.UITypeEditor> veya <xref:System.ComponentModel.TypeConverter> mekanizmaları.  
  
    Örneğin, <xref:System.Windows.Forms>-tabanlı tasarımcıları başlatılır, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortam değiştirir <xref:System.Drawing.Design.UITypeEditor> için <xref:System.Web.UI.WebControls.Image> tasarımcı ile dosya sistemi yerine bit eşlemler almak için Kaynak Yöneticisi'ni kullanmak için kullanılan nesneleri.  
  
2. Bir ortam gibi olaylara abone olma ya da proje yapılandırma bilgilerini elde etmeyi tümleştirme. Proje yapılandırma bilgilerini edinmek ve elde ederek olaylara abone <xref:System.ComponentModel.Design.ITypeResolutionService> arabirimi.  
  
3. Uygun etkinleştirme tarafından kullanıcı ortamını değiştirilmesini **araç kutusu** kategorileri veya örneği uygulayarak tasarımcının Uygulanabilirlik kısıtlayarak <xref:System.ComponentModel.ToolboxItemFilterAttribute> sınıfı için tasarımcı.  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage tarafından tasarımcıyı başlatma  
 VSPackage tarafından tasarımcıyı başlatma işlemesi gerekir:  
  
1. Bir nesneyi uygulama oluşturma <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> sınıfı.  
  
   > [!NOTE]
   >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Sınıfı hiçbir zaman uygulanmasını aynı nesne üzerinde <xref:Microsoft.VisualStudio.Shell.Package> sınıfı.  
  
2. Sınıf uygulama kaydetme <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> örneklerini uygulayarak VSPackage'nın Tasarımcı uzantıları için destek sunarak olarak <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> ve <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage'nın uygulaması sağlama sınıfa <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Herhangi bir tasarımcı veya Tasarımcısı bileşen oluşturulduğunda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortam:  
  
3. Her kayıtlı tasarım yüzeyi uzantısı Sağlayıcısı'na erişir.  
  
4. Oluşturur ve her tasarım yüzeyi uzantısı sağlayıcısının bir örneğini başlatır <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> nesnesi  
  
5. Her tasarım yüzeyi uzantısı sağlayıcısının çağırır <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> yöntemi veya <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> yöntemi (hangisi uygunsa).  
  
   Uygularken <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> nesnesi bir VSPackage'ı bir üyesi olarak anlamak önemlidir:  
  
6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ortamı, herhangi bir denetime hangi meta verileri sağlamaz veya belirli bir diğer yapılandırma ayarlarını `DesignSurfaceExtension` sağlayıcısının değiştirir. İki veya daha fazla mümkündür `DesignSurfaceExtension` aynı Tasarımcısı özelliğiyle kesin olan son değişikliği ile çakışan yollarla değiştirme sağlayıcıları. Hangi değişiklik son uygulanan da belirsiz.  
  
7. Açıkça uygulaması kısıtlamak mümkündür <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> örneklerini uygulayarak belirli tasarımcıları, nesneye <xref:System.ComponentModel.ToolboxItemFilterAttribute> bu uygulama için. Daha fazla bilgi için **araç kutusu** öğesi filtreleme için bkz: <xref:System.ComponentModel.ToolboxItemFilterAttribute> ve <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Ek meta veri sağlama  
 VSPackage tasarım zamanında bir tasarımcı veya dışında Tasarımcısı bileşen yapılandırmasını değiştirebilirsiniz.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Sınıfı programlı olarak kullanılabilir veya bir tasarımcı sağlayan bir Vspackage'e uygulanması.  
  
 Örneği <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> sınıfı, bir tasarım yüzeyi üzerinde oluşturulan bileşenleri meta verilerini değiştirmek için kullanılır. Örneğin, biri tarafından kullanılan varsayılan özellik tarayıcısını yerini alabilir <xref:System.Windows.Forms.CommonDialog> nesneleri, bir özel özellik tarayıcısı.  
  
 Örneği tarafından sağlanan değişiklikleri <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> uygulanmasına VSPackage'nın uygulanan <xref:Microsoft.VisualStudio.Shell.Package> iki kapsamların biri olabilir:  
  
- Genel--için belirli bir bileşenin tüm yeni örnekleri  
  
- Yerel--yalnızca geçerli VSPackage'ı tarafından sağlanan bir tasarım yüzeyi üzerinde oluşturulan bileşeninin örneği tıklarsınız.  
  
  `IsGlobal` Özelliği <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> uygulanmasına VSPackage'nın uygulanan örneği <xref:Microsoft.VisualStudio.Shell.Package> bu kapsamı belirler.  
  
  Özniteliği uygulaması için uygulama <xref:Microsoft.VisualStudio.Shell.Package> ile <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> özelliği <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> nesne kümesine `true`, tüm tarayıcı olarak aşağıdaki değişiklikleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortam:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Genel Bayrak olarak ayarlandı, `false`, meta veri değişikliği geçerli VSPackage'ı tarafından desteklenen geçerli Tasarımcı için yerel ise:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  Mevcut zaman tasarım yüzeyine bileşenler oluşturma yalnızca destekler ve bu nedenle yalnızca bileşenleri yerel meta verilerine de sahip. Yukarıdaki örnekte, biz bir özelliği değiştirmek çalıştığınız `Color` özelliği bir nesne. Varsa `false` genel bayrak için geçirilen `CustomBrowser` Tasarımcı örneği asla gerçekten oluşturur çünkü hiçbir zaman görüneceği `Color`. Genel Bayrak ayarlayarak `false` denetimleri, zamanlayıcılar ve iletişim kutuları gibi bileşenleri için kullanışlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Tasarım zamanı desteğini genişletmek](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)