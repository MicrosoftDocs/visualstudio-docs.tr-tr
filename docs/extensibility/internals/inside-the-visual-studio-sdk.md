---
title: Visual Studio SDK içinde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e72c5033554310555005de17872ee83110768687
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757048"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK’nın İçinde
Bu bölümde, Visual Studio mimarisi, bileşenleri, hizmetleri, şemalar, yardımcı programlar ve benzeri dahil olmak üzere Visual Studio uzantıları hakkında ayrıntılı bilgi sağlar.

## <a name="extensibility-architecture"></a>Genişletilebilirlik mimarisi
 Aşağıdaki çizimde, Visual Studio genişletilebilirlik mimari gösterilir. VSPackages IDE arasında paylaşılan hizmetler uygulama işlevselliği sağlar. Standart IDE çok çeşitli hizmetler gibi sunduğu <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, IDE Pencereleme işlevine erişim sağlar.

 ![Ortam Mimarisi grafiği](../../extensibility/internals/media/environment.gif "ortam") Visual Studio mimari görünümünü genelleştirilmiş

## <a name="vspackages"></a>VSPackage’lar
 VSPackages oluşturan ve Visual Studio kullanıcı Arabirimi öğeleri, hizmetleri, projeler, düzenleyiciler ve tasarımcılar ile genişleten yazılım modülleri olan. VSPackages Visual Studio Merkezi mimari ölçü var. Daha fazla bilgi için bkz: [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Kabuğu
 Visual Studio Kabuğu'nu temel işlevi sağlar ve bileşen VSPackages ve MEF uzantıları arasında arası iletişimi destekler. Daha fazla bilgi için bkz: [Visual Studio Kabuğu](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Kullanıcı Deneyimi Yönergeleri
 Visual Studio için yeni özellikler tasarım planlıyorsanız, tasarım ve kullanılabilirlik ipuçları için bu yönergeleri göz atın: [Visual Studio kullanıcı deneyimi yönergeleri](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Komutlar
 Belge yazdırma, bir görünümü yenileme veya yeni bir dosya oluşturmak gibi görevleri gerçekleştirmek işlevleri komutlardır.

 Visual Studio genişlettiğinizde, komutları oluşturun ve bunları Visual Studio Kabuğu ile kaydedin. Bu komutlar IDE içinde Örneğin, menü veya araç çubuğunda görüntülenme belirtebilirsiniz. Özel bir komut genellikle görünür **Araçları** menü ve araç penceresi görüntülemek için komut çubuğunda görüneceği **diğer pencereler** alt **Görünüm** menüsü.

 Bir komut oluşturduğunuzda, aynı zamanda bir olay işleyicisi için oluşturmanız gerekir. Olay işleyicisi ne zaman komutu görünür veya etkin, kendi metin değiştirmenize olanak tanır ve zaman etkinleştirildiğini komutu uygun şekilde yanıtlayan garanti eder belirler. Çoğu durumda, IDE kullanarak komutları işleyen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Visual Studio komutları yerel seçimine göre ve genel seçimine göre en dıştaki bağlamı için devam en içteki komut bağlamı başlayarak ele alınır. Ana menüsüne eklenen komutlar komut dosyası için hemen kullanılabilir.

 Daha fazla bilgi için bkz: [komutları, menüleri ve araç çubuklarını](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menüleri ve araç çubukları
 Menüleri ve araç çubuklarını komutları çağırmak bir yol sağlar. Menüleri satır veya sütun üst araç penceresi bireysel metin öğeleri olarak genellikle görüntülenen komutların ' dir. Alt menüler kullanıcı küçük bir ok içerir komutları tıkladığında, görünen ikincil menüleri ' dir. Bir kullanıcı belirli kullanıcı Arabirimi öğeleri tıklattığında bağlam menülerini görünür. Bazı ortak menü adları **dosya**, **Düzenle**, **Görünüm**, ve **penceresi**. Daha fazla bilgi için bkz: [genişletme menüleri ve komutları](../../extensibility/extending-menus-and-commands.md).

 Araç çubukları satır veya sütun düğmeleri ve birleşik giriş kutuları, liste kutuları ve metin kutuları gibi diğer denetimlerin ' dir. Araç çubuğu düğmeleri için klasör simgesine gibi simge görüntüleri genellikle sahip bir **açık dosya** komutu veya bir yazıcı için bir **yazdırma** komutu. Tüm araç çubuğu öğelerinin komutları ile ilişkilendirilir. Araç çubuğu düğmesini tıklattığınızda, ilişkili komutu çalıştırır. Aşağı açılır denetimin söz konusu olduğunda, açılan listedeki her bir öğe farklı komutu ile ilişkilidir. Bölümlendirici denetimi gibi bazı araç çubuğu denetimleri sınıflarınızın bir karmasını bulunur. Denetimin sütunlardan araç çubuğu düğmesi ve diğer taraftaki çeşitli komutlar tıklandığında görüntüleyen bir aşağı oka.

## <a name="tool-windows"></a>Araç pencereleri
 Araç Pencereleri IDE içinde bilgileri görüntülemek için kullanılır. **Araç kutusu**, **Çözüm Gezgini**, **özellikleri** penceresinde ve **Web tarayıcısı** aracı windows gösterilebilir.

 Araç pencereleri normalde çeşitli denetimleri ile kullanıcı etkileşim kurabilen sunar. Örneğin, **özellikleri** pencere kullanıcının belirli bir amaca nesnelerin özelliklerini ayarlamasına olanak sağlar. **Özellikleri** penceresi olduğundan bu bağlamda özelleştirilmiş, ancak aynı zamanda genel birçok farklı durumlarda kullanılabilir. Benzer şekilde, **çıkış** penceresi birçok alt sistemleri Visual Studio için Visual Studio kullanıcı çıkış sağlamak için kullanabileceğiniz için genel ancak metin tabanlı çıkış sağladığından özelleştirilmiş.

 Aşağıdaki resimde birkaç araç pencereleri içeren Visual Studio göz önünde bulundurun.

 ![Ekran görüntüsü](../../extensibility/internals/media/t1gui.png "T1gui")

 Araç pencereleri bazıları birlikte Solution Explorer araç penceresi görüntüler ve diğer aracı windows gizler ancak sekmeleri tıklatarak kullanılabilir kılar tek bölmesindeki sabitlenir. Diğer iki aracı windows resim gösterir **hata listesi** ve **çıkış** birlikte üzerinde tek bir bölme yerleşik penceresi.

 Ayrıca gösterilen birkaç düzenleyici pencereleri gösterir ana belge bölmesinde olur. Araç pencereleri genellikle sadece bir örnek sahip olsa da (örneğin, yalnızca birini açabilirsiniz **Çözüm Gezgini**), düzenleyici pencereleri her biri ayrı bir belge düzenlemek için kullanılır, ancak her biri içinde yerleşik birden çok örneği olabilir aynı bölmesi. Resim iki düzenleyici pencereleri, bir form tasarımcısı penceresinin ve başlangıç sayfası gösteren bir tarayıcı penceresi sahip bir belge bölmesi gösterir. Sekmeleri tıklatarak belge bölmesinde tüm windows kullanılabilir, ancak EditorPane.cs dosyasını içeren Düzenleyicisi görünür ve etkin bir penceredir.

 Visual Studio genişlettiğinizde, Visual Studio kullanıcıların izin windows etkileşim aracı uzantısı ile oluşturabilirsiniz. Visual Studio kullanıcıların belgeleri düzenlemesine izin kendi düzenleyiciler de oluşturabilirsiniz. Araç pencereleri ve editörler Visual Studio'ya tümleşik olduğundan, yerleştirme ya da bir sekmesinde doğru şekilde görünen program gerekmez. Visual Studio'da doğru şekilde kaydedildiğinden, bunlar otomatik olarak tipik özelliklerini araç pencereleri ve belge pencereleri Visual Studio'da olur. Daha fazla bilgi için bkz: [genişletme ve Özelleştirme Aracı Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Belge Pencereleri
 Bir belge bir Çerçeveli alt birden çok belge arabirimi (MDI) penceresinin penceresidir. Belge pencereleri genellikle metin düzenleyicileri, form Düzenleyicileri (Designer'ları olarak da bilinir) veya düzenleme denetimleri barındırmak için kullanılır, ancak diğer işlev türleri de barındırabilir. **Yeni dosya** iletişim kutusu, Visual Studio sağlayan bir belge windows örnekleri içerir.

 Çoğu düzenleyicileri bir programlama dili veya HTML sayfaları, çerçeve kümeleri, C++ dosyaları ya da üst bilgi dosyaları gibi bir dosya türü için özeldir. Bir şablon seçerek **yeni dosya** iletişim kutusu, bir kullanıcı dinamik olarak oluşturur belge penceresine Düzenleyicisi şablonuyla ilişkili olduğundan dosya türü için. Varolan bir dosyanın bir kullanıcı oturum açtığında bir belge penceresi de oluşturulur.

 Belge pencereleri MDI istemci alanını kısıtlanır. Her belge penceresine üstte bir sekmesi vardır ve sekme sırası MDI alanında açık diğer windows bağlantılıdır. Bir belge penceresinin sekmesine sağ MDI alanı birden çok yatay veya dikey sekme gruplara ayırın seçeneklerini içeren bir kısayol menüsünü görüntüler. MDI alanı bölme aynı anda görüntülenmek üzere birden çok dosya sağlar. Daha fazla bilgi için bkz: [belge pencereleri](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Düzenleyiciler
 Visual Studio düzenleyicisinde özelleştirin ve kendi içerik türü için Yönetilen Genişletilebilirlik Çerçevesi'yoluyla (MEF) kullanmanıza olanak sağlar. Çoğu durumda (örneğin, bir komutu veya bir kısayol tuşu) Kabuk özelliklerinden dahil etmek istiyorsanız, bir MEF uzantısı ile VSPackage birleştirebilirsiniz rağmen Düzenleyicisi'ni genişletmek için VSPackage oluşturmak gerekmez.

 Örneğin özel bir düzenleyici okuma ve veritabanına yazmak isterseniz, veya bir tasarımcı kullanmak isterseniz de oluşturabilirsiniz. Not Defteri veya Microsoft WordPad gibi harici bir düzenleyici de kullanabilirsiniz. Daha fazla bilgi için bkz: [Düzenleyicisi ve dil hizmeti uzantılarını](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Dil Hizmetleri
 Yeni programlama anahtar sözcükleri veya daha yeni bir programlama dili desteklemek için Visual Studio düzenleyicisinde istiyorsanız, bir dil hizmeti oluşturun. Her dil hizmet belirli Düzenleyicisi özellikleri tam olarak, kısmen veya hiç uygulayabilir. Nasıl yapılandırıldığına bağlı olarak, sözdizimi vurgulama, eşleşen ayraç, IntelliSense desteği ve diğer özellikleri Düzenleyicisi'nde dil hizmeti sağlayabilir.

 Bir dil hizmeti Kalp bir Ayrıştırıcıyı ve tarayıcı ' dir. Bir tarayıcı (veya lexer) belirteçleri bilinen öğe kaynak dosyası böler ve bir Ayrıştırıcıyı konusu belirteçleri arasındaki ilişkiler oluşturur. Bir dil hizmeti oluşturduğunuzda, böylece Visual Studio belirteçleri ve dil dilbilgisi anlayabileceği bir ayrıştırıcı ve tarayıcı uygulamanız gerekir. Yönetilen veya yönetilmeyen dil hizmetler oluşturabilirsiniz. Daha fazla bilgi için bkz: [eski dil hizmeti genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projeler
 Visual Studio'da projeler düzenlemek ve kaynak kodu ve diğer kaynakları oluşturmak için geliştiriciler kullanın kapsayıcılardır. Düzenleme, yapı, hata ayıklama ve kaynak kodu dağıtmanıza olanak sağlayan projeleri, Web Hizmetleri ve veritabanları ve diğer kaynaklara başvuruyor. VSPackages Visual Studio Proje sistemi proje türleri, proje subtypes ve özel araçlar sağlayarak genişletebilirsiniz.

 Projeleri, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla projeleri grubudur bir çözümde de toplanan. Çözüme ilgilidir proje ve durum bilgilerini iki çözüm dosyaları, metin tabanlı çözüm (.sln) dosyası ve ikili çözüm kullanıcı seçeneği (.suo) dosyasında depolanır. Bu dosyalar'ın önceki sürümlerinde kullanılan Grup (.vbg) dosyalarını benzer [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], çalışma (.dsw) ve kullanıcı seçeneklerini'nın önceki sürümlerinde kullanılan (.opt) dosyaları [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

 Daha fazla bilgi için bkz: [projeleri](../../extensibility/internals/projects.md) ve [çözümleri](../../extensibility/internals/solutions.md).

## <a name="project-and-item-templates"></a>Proje ve Öğe Şablonları
 Visual Studio, önceden tanımlanmış proje şablonları ve proje öğesi şablonları içerir. Ayrıca kendi şablonlarınızı olun veya topluluk şablonlardan edinmeli ve bunları Visual Studio'ya tümleştirin. [MSDN kod Galerisi'nden](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) şablonları ve uzantıları için Git yerdir.

 Şablonlar proje yapısını ve belirli bir uygulama, Denetim, kitaplığı veya sınıf türünü yapılandırmak için gerekli olan temel dosyaları içerir. Şablonlardan birini benzer yazılım geliştirme istediğinizde, şablona dayalı bir proje oluşturun ve bu proje dosyalarında değiştirin.

> [!NOTE]
> Bu şablonu mimarisi desteklenmez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeleri.

 Daha fazla bilgi için bkz: [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Özellikleri ve seçenekleri
 **Özellikleri** penceresi, tek veya birden çok seçili öğe özelliklerini görüntüler: [genişletme özellikleri](../../extensibility/internals/extending-properties.md) seçenekleri sayfalar gibi belirli bir bileşene ait seçenekleri kümesi içeren bir programlama dili veya bir VSPackage: [seçenekleri ve seçenekleri sayfaları](../../extensibility/internals/options-and-options-pages.md). Ayarlar, içeri ve dışarı genellikle UI ilgili özellikler şunlardır: [kullanıcı ayarları desteği](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio Hizmetleri
 Bir hizmeti arabirimleri tüketmeye bileşenleri için belirli bir kümesini sağlar. Visual Studio uzantıları dahil olmak üzere tüm bileşenleri tarafından kullanılan hizmetler kümesini sağlar. Örneğin, aracı windows gösterilecek veya dinamik olarak gizli Yardım, durum çubuğu veya UI olayları erişim sağlamak Visual Studio hizmetleri sağlar. Visual Studio düzenleyicisinde Düzenleyici uzantıları tarafından içe aktarılabilir hizmetleri de sağlar. Daha fazla bilgi için bkz: [kullanma ve servisleri](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Hata ayıklayıcı
 Hata ayıklayıcı dile özgü hata ayıklama bileşenleri için kullanıcı arabirimidir. Yeni dil hizmetini oluşturduysanız, hata ayıklayıcı için için belirli hata ayıklama altyapısı oluşturmanız gerekir. Daha fazla bilgi için bkz: [Visual Studio hata ayıklayıcısı genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Kaynak Denetimi
 Kaynak denetimi eklenti veya VSPackage uygulama hakkında daha fazla bilgi için bkz: [kaynak denetimi](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Sihirbazlar
 Yeni bir proje türü ile birlikte bir sihirbaz oluşturabilirsiniz, böylece sihirbaz yardımcı olabilir bu türdeki yeni bir proje oluşturduğunuzda, kullanıcılarınızın doğru kararlar. Daha fazla bilgi için bkz: [sihirbazlar](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Özel Araçlar
 Özel Araçlar projesinde bir öğesiyle bir aracı ilişkilendirin ve dosya kaydedilmiş olduğunda bu aracı sağlar. Daha fazla bilgi için bkz: [özel Araçlar](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>VSSDK Yardımcı Programları
 VSSDK bir VSPackages farklı yönlerini çalışması için gereken araçları içerir. Daha fazla bilgi için bkz: [VSSDK yardımcı programları](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Windows Installer kullanma
 Bazı durumlarda VSIX yükleyici yerine Windows Installer kullanmanız gerekebilir: Örneğin, kayıt defterine yazma gerekebilir. Windows Installer uzantıları ile kullanma hakkında daha fazla bilgi için bkz: [yükleme VSPackages ile Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Yardım Görüntüleyicisi
 Yardım Görüntüleyicisi'ne kendi Yardım ve F1 sayfaları tümleştirebilirsiniz. Daha fazla bilgi için bkz: [Microsoft Yardım Görüntüleyicisi SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).