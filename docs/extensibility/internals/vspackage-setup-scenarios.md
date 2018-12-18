---
title: VSPackage Kurulum senaryoları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c194588de8dfa8746bb79a8d86bff005d90e7550
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495940"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları

VSPackage yükleyicinizi esneklik tasarlamak önemlidir. Örneğin, bir güvenlik düzeltme eki gelecekte serbest bırakmanız gerekebilir veya kapsamlı yan yana sürüm oluşturma desteği gerektiren işletme stratejisinin değişebilir.

İçinde [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), avantajlar ve yan yana yüklemeleri destekleme sorunlar hakkında bilgi edinebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , VSPackage paylaşılan veya yan yana yüklemeleri ile. Kısacası, yan yana VSPackages yeni özellikleri desteklemek için en fazla esnekliği size [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Bu konuda tartışılan senaryoların yalnızca seçimlerinizi değildir ancak onlara önerilen en iyi yöntemler olarak gösterilir.

## <a name="components-privacy-and-sharing"></a>Bileşenler, gizlilik ve paylaşma

### <a name="make-your-components-independent"></a>Bileşenlerinizin bağımsız olun

Tanımlamak ve doldurmak bir bileşen sonra Ata bir `GUID`ve bileşen dağıtmak, kendi bileşim değiştiremezsiniz. Bir bileşenin bileşim değiştirirseniz, yeni bir bileşen yeni bir sonuç bileşeni olmalıdır `GUID`. Bu bilgiler verildiğinde, her bileşen birimini bağımsız ve kendi sağlayarak en büyük sürüm oluşturma esnekliği gösterilen. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için bkz: [bileşeni kodunun değiştirilmesi](/windows/desktop/Msi/changing-the-component-code) ve [ne olur bileşen kuralları bozuk olduğu?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Bir bileşen içinde paylaşılan ve özel kaynakları karıştırmamanızı

Başvuru sayımı, bileşen düzeyinde gerçekleşir. Sonuç olarak, paylaşılan ve özel kaynakların bir bileşende karıştırma olanaksız bir yürütülebilir dosya gibi özel kaynaklar da paylaşılan kaynakları yazmadan güncelleştirme yapar. Bu senaryo, geriye dönük uyumluluk sorunları oluşturur ve yan yana özellik oluşturmaktan kısıtlar.

Örneğin, kayıt defteri değerlerini kullanılan, VSPackage ile kaydetmek için [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bir bileşen, bir Visual Studio ile VSPackage'ı kaydetmek için kullanılan ayrı olarak tutulmalıdır. Paylaşılan dosyalar veya kayıt defteri değerlerini başka bir bileşenin gidin.

## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage'ı

Bu senaryoda, Paylaşılan VSPackage (Visual Studio'nun birden çok sürümünü destekleyen tek bir ikili bir Windows yükleyici paketinde sevk edilir. Visual Studio'nun her sürümü ile kaydetme, kullanıcı tarafından seçilebilen özellikleri tarafından denetlenir. Ayrıca özellikleri ayırmak için atandığında, her bir bileşeni ayrı ayrı yüklenmesi ve kaldırılması, kullanıcı denetimi VSPackage'nün farklı sürümlerini tümleştirme koymak için seçilebileceğini gösterir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Bkz [Windows Yükleyici'nin özellikleri](/windows/desktop/Msi/windows-installer-features) Windows yükleyici paketinde özelliklerini kullanma hakkında daha fazla bilgi için.)

![VS Paylaşılan VSPackage yükleyici](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Çizimde gösterildiği gibi paylaşılan bileşenler her zaman yüklü Feat_Common özelliğinin bir parçası olarak yapılır. Feat_VS2002 ve Feat_VS2003 özellikleri görünür hale getirerek kullanıcıların Visual Studio'nun hangi sürümlere istedikleri VSPackage'ı tümleştirmek için yükleme sırasında seçebilirsiniz. Kullanıcılar, Windows Installer Bakım modu eklemek veya özellikleri, bu durumda ekler veya VSPackage kayıt bilgilerini farklı Visual Studio sürümlerinden kaldırır kaldırmak için de kullanabilirsiniz.

> [!NOTE]
> Bir özelliğin görüntü sütunu 0 olarak ayarlanması gizler. 1 gibi bir alt düzey sütun değeri her zaman yüklenecek sağlar. Daha fazla bilgi için [INSTALLLEVEL özelliği](/windows/desktop/Msi/installlevel) ve [özellik tablosu](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage'ı güncelleştirme

Bu senaryoda, Senaryo 1 VSPackage yükleyicide güncelleştirilmiş bir sürümünü sevk edilir. Tartışma için güncelleştirme Visual Studio için destek ekler, ancak de daha basit bir güvenlik düzeltme eki olabilir veya hata-hizmet paketi düzeltmesi. Zaten sistemde değişmeden bileşenleri değil yeniden yeni bileşenleri yüklemek için Windows Installer'ın kuralları zorunlu kılar. Bu durumda, sürüm 1.0 zaten sistemiyle güncelleştirilen bileşenin Comp_MyVSPackage.dll üzerine ve kullanıcıların kendi bileşeniyle Comp_VS2005_Reg Feat_VS2005 yeni özellik eklemek seçin.

> [!CAUTION]
> VSPackage birden çok sürümünü arasında paylaşılan her [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], VSPackage'ı sonraki sürümlerini Visual Studio'nun önceki sürümleriyle geriye dönük uyumluluk sağlamak önemlidir. Geriye dönük uyumluluk koruyamadığını burada yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS VS paket güncelleştirmesi paylaşılan yükleyici](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Bu senaryo yeni bir VSPackage yükleyici, küçük yükseltmeler için Windows Installer'ın destek avantajlarını sunar. Kullanıcılar yalnızca sürüm 1.1 yükleyin ve sürüm 1.0 yükseltir. Ancak, sistemdeki sürüm 1.0 gerekli değildir. Aynı Yükleyici sürüm 1.1, 1.0 sürümü olmadan bir sistemde yükler. Bu şekilde Küçük yükseltmeler sağlamayı avantajı, bir yükseltme yükleyici ve bir tam ürün yükleyicisi geliştirme iş gitmek gerekli değildir, ' dir. Bir yükleyici, her iki iş yapar. Bir güvenlik düzeltme ya da hizmet paketi kaybolabileceğini bunun yerine Windows Installer düzeltme eklerinin avantajlarından yararlanın. Daha fazla bilgi için [düzeltme eki uygulama ve yükseltmeler](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: Yan yana VSPackage'ı

Bu senaryo iki VSPackage yükleyici sunar — bir Visual Studio .NET 2003 ve Visual Studio'nun her sürümü için. Her bir yükleyici, yan yana veya özel, VSPackage'ı (özel olarak oluşturduğu ve belirli bir Visual Studio sürümü için yüklü bir) yükler. Her VSPackage'ı kendi bileşenidir. Sonuç olarak, her tek tek düzeltme ekleri veya bakım ile hizmet verilebilir serbest bırakır. VSPackage DLL artık sürüme özgü olduğundan, aynı bileşeni DLL olarak kayıt bilgileri dahil güvenlidir.

![VS Yan Yana VS Package Installer](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Her yükleyicisi Ayrıca iki yükleyici arasında paylaşılan kod içerir. Hem .msi dosyaları yüklendiğinde paylaşılan kodun bir ortak konuma yüklediyseniz, paylaşılan kod yalnızca bir kez yüklenir. İkinci yükleyici, yalnızca bir bileşene başvuru sayısını artırır. Başvuru sayısı VSPackages birini kaldırdığınızda, paylaşılan kodun bir VSPackage için kalmasını sağlar. İkinci VSPackage de kaldırılırsa, paylaşılan kod kaldırılacak.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: Yan yana VSPackage'ı güncelleştirme

Bu senaryoda, VSPackage'ı Visual Studio için bir güvenlik açığını çalışmaya başlayamıyorsa ve bir güncelleştirme vermeniz gerekir. Senaryo 2 olduğu gibi güncelleştirmeleri yanı sıra güvenlik düzeltme ekini içeren yeni yüklemeleri yerinde zaten güvenlik düzeltme ile dağıtmak için mevcut bir yüklemesi yeni bir .msi dosyasını oluşturabilirsiniz.

Bu durumda, genel derleme önbelleğinde (GAC) yüklü yönetilen VSPackage VSPackage olur. Güvenlik düzeltme ekini içerecek şekilde yeniden derlerken, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Kayıt bilgileri yeni derleme sürüm numarası, önceki sürümü üzerine yazar için neden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sabit derlemesi yüklenemiyor.

![VS Yan Yana VS paket güncelleştirme yükleyicisi](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için bkz. [dağıtım basitleştirme ve .NET Framework ile çözme DLL cehennemi](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Ayrıca Bkz.

[Windows Installer](/windows/desktop/Msi/windows-installer-portal)  
[Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)