---
title: VSPackage Kurulum senaryoları | Microsoft Docs
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
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34181e5b03b29662188e368561b0f43049629ec1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788556"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage yükleyicinizi esneklik tasarlamak önemlidir. Örneğin, bir güvenlik düzeltme eki gelecekte serbest bırakmanız gerekebilir veya kapsamlı yan yana sürüm oluşturma desteği gerektiren işletme stratejisinin değişebilir.  
  
 İçinde [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), avantajlar ve yan yana yüklemeleri destekleme sorunlar hakkında bilgi edinebilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , VSPackage paylaşılan veya yan yana yüklemeleri ile. Kısacası, yan yana VSPackages yeni özellikleri desteklemek için en fazla esnekliği size [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Bu konuda tartışılan senaryoların yalnızca seçimlerinizi değildir ancak onlara önerilen en iyi yöntemler olarak gösterilir.  
  
## <a name="components-privacy-and-sharing"></a>Bileşenler, gizlilik ve paylaşma  
  
##### <a name="make-your-components-independent"></a>Bileşenlerinizin bağımsız olun  
 Tanımlamak ve doldurmak bir bileşen sonra Ata bir `GUID`ve bileşen dağıtmak, kendi bileşim değiştiremezsiniz. Bir bileşenin bileşim değiştirirseniz, yeni bir bileşen yeni bir sonuç bileşeni olmalıdır `GUID`. Bu bilgiler verildiğinde, her bileşen birimini bağımsız ve kendi sağlayarak en büyük sürüm oluşturma esnekliği gösterilen. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için bkz: [bileşeni kodunun değiştirilmesi](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) ve [ne olur bileşen kuralları bozuk olduğu?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Bir bileşen içinde paylaşılan ve özel kaynakları karıştırmamanızı  
 Başvuru sayımı, bileşen düzeyinde gerçekleşir. Sonuç olarak, paylaşılan ve özel kaynakların bir bileşende karıştırma olanaksız bir yürütülebilir dosya gibi özel kaynaklar da paylaşılan kaynakları yazmadan güncelleştirme yapar. Bu senaryo, geriye dönük uyumluluk sorunları oluşturur ve yan yana özellik oluşturmaktan kısıtlar.  
  
 Örneğin, kayıt defteri değerlerini kullanılan, VSPackage ile kaydetmek için [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] bir bileşeni, VSPackage ile kaydetmek için kullanılan birinden ayrı olarak tutulmalıdır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Paylaşılan dosyalar veya kayıt defteri değerlerini başka bir bileşenin gidin.  
  
## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage'ı  
 Bu senaryoda, paylaşılan bir VSPackage'ı (birden çok sürümünü destekleyen tek bir ikili [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]) bir Windows yükleyici paketinde sevk edilir. Her sürümü ile kaydetme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanıcı tarafından seçilebilen özellikleri tarafından denetlenir. Ayrıca özellikleri ayırmak için atandığında, her bir bileşeni ayrı ayrı yüklenmesi ve kaldırılması, kullanıcı denetimi VSPackage'nün farklı sürümlerini tümleştirme koymak için seçilebileceğini gösterir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. (Bkz [Windows Yükleyici'nin özellikleri](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) Windows yükleyici paketinde özelliklerini kullanma hakkında daha fazla bilgi için.)  
  
 ![VS Paylaşılan VSPackage grafiği](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Paylaşılan VSPackage yükleyici  
  
 Çizimde gösterildiği gibi paylaşılan bileşenler her zaman yüklü Feat_Common özelliğinin bir parçası olarak yapılır. Feat_VS2002 ve Feat_VS2003 özellikleri görünür hale getirerek kullanıcıların hangi sürümlere yükleme sırasında seçebilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage'ı tümleştirmek için istedikleri. Kullanıcılar ayrıca kullanabilir Windows Installer Bakım modu ekleyip özellikleri, bu durumda ekler veya VSPackage kayıt bilgilerini farklı sürümlerinden kaldırır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  Bir özelliğin görüntü sütunu 0 olarak ayarlanması gizler. 1 gibi bir alt düzey sütun değeri her zaman yüklenecek sağlar. Daha fazla bilgi için [INSTALLLEVEL özelliği](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) ve [özellik tablosu](http://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage'ı güncelleştirme  
 Bu senaryoda, Senaryo 1 VSPackage yükleyicide güncelleştirilmiş bir sürümünü sevk edilir. Tartışma için güncelleştirme için destek ekler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ancak daha basit bir güvenlik düzeltme eki veya hata düzeltmesi hizmet paketi olabilir. Zaten sistemde değişmeden bileşenleri değil yeniden yeni bileşenleri yüklemek için Windows Installer'ın kuralları zorunlu kılar. Bu durumda, sürüm 1.0 zaten sistemiyle güncelleştirilen bileşenin Comp_MyVSPackage.dll üzerine ve kullanıcıların kendi bileşeniyle Comp_VS2005_Reg Feat_VS2005 yeni özellik eklemek seçin.  
  
> [!CAUTION]
>  VSPackage birden çok sürümünü arasında paylaşılan her [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], sonraki sürümlerini VSPackage'nın önceki sürümleriyle geriye dönük uyumluluk korumak önemlidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Geriye dönük uyumluluk koruyamadığını burada yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![VS VS paket güncelleştirme resmi paylaşılan](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
VSPackage'ı güncelleştirme yükleyicisi paylaşılan  
  
 Bu senaryo yeni bir VSPackage yükleyici, küçük yükseltmeler için Windows Installer'ın destek avantajlarını sunar. Kullanıcılar yalnızca sürüm 1.1 yükleyin ve sürüm 1.0 yükseltir. Ancak, sistemdeki sürüm 1.0 gerekli değildir. Aynı Yükleyici sürüm 1.1, 1.0 sürümü olmadan bir sistemde yükler. Bu şekilde Küçük yükseltmeler sağlamayı avantajı, bir yükseltme yükleyici ve bir tam ürün yükleyicisi geliştirme iş gitmek gerekli değildir, ' dir. Bir yükleyici, her iki iş yapar. Bir güvenlik düzeltme ya da hizmet paketi kaybolabileceğini bunun yerine Windows Installer düzeltme eklerinin avantajlarından yararlanın. Daha fazla bilgi için [düzeltme eki uygulama ve yükseltmeler](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: Yan yana VSPackage'ı  
 Bu senaryo iki VSPackage yükleyici sunar — Visual Studio .NET 2003'ün her sürümü için bir tane ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Yan yana veya özel, VSPackage her yükleyici yükler (özel olarak oluşturduğu ve belirli bir sürümü için yüklü bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]). Her VSPackage'ı kendi bileşenidir. Sonuç olarak, her tek tek düzeltme ekleri veya bakım ile hizmet verilebilir serbest bırakır. VSPackage DLL artık sürüme özgü olduğundan, aynı bileşeni DLL olarak kayıt bilgileri dahil güvenlidir.  
  
 ![VS Yan&#45;tarafından&#45;yan VS Paketi grafiği](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Yan yana VSPackage yükleyici  
  
 Her yükleyicisi Ayrıca iki yükleyici arasında paylaşılan kod içerir. Hem .msi dosyaları yüklendiğinde paylaşılan kodun bir ortak konuma yüklediyseniz, paylaşılan kod yalnızca bir kez yüklenir. İkinci yükleyici, yalnızca bir bileşene başvuru sayısını artırır. Başvuru sayısı VSPackages birini kaldırdığınızda, paylaşılan kodun bir VSPackage için kalmasını sağlar. İkinci VSPackage de kaldırılırsa, paylaşılan kod kaldırılacak.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: Yan yana VSPackage'ı güncelleştirme  
 Bu senaryoda, VSPackage için [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] çalışmaya başlayamıyorsa güncelleştirme vermek güvenlik açığı ve güvenlik ile gerekir. Senaryo 2 olduğu gibi güncelleştirmeleri yanı sıra güvenlik düzeltme ekini içeren yeni yüklemeleri yerinde zaten güvenlik düzeltme ile dağıtmak için mevcut bir yüklemesi yeni bir .msi dosyasını oluşturabilirsiniz.  
  
 Bu durumda, genel derleme önbelleğinde (GAC) yüklü yönetilen VSPackage VSPackage olur. Güvenlik düzeltme ekini içerecek şekilde yeniden derlerken, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Kayıt bilgileri yeni derleme sürüm numarası, önceki sürümü üzerine yazar için neden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sabit derlemesi yüklenemiyor.  
  
 ![VS Yan&#45;tarafından&#45;yan VS Paketi güncelleştirme grafiği](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Yan yana VSPackage güncelleştirme yükleyicisi  
  
 **Not** yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için bkz. [dağıtım basitleştirme ve .NET Framework ile çözme DLL cehennemi](http://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

