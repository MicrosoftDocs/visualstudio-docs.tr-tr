---
title: Visual Studio SDK'sı içindeki | Microsoft Docs
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
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7a7642d8cd33d53bb7d6d2a472a0690713e25d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795836"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK’nın İçinde
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölüm, Visual Studio mimari, bileşenleri, hizmetleri, şemalar, yardımcı programlar ve benzeri gibi Visual Studio uzantıları hakkında ayrıntılı bilgi sağlar.  
  
## <a name="extensibility-architecture"></a>Genişletilebilirlik mimarisi  
 Aşağıdaki çizim Visual Studio genişletilebilirlik mimarisi gösterilmektedir. VSPackage IDE hizmet olarak paylaşılır uygulama işlevselliği sağlar. Standart IDE Hizmetleri, çok geniş bir yelpazede gibi sunduğu <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, IDE Pencereleme işlevi erişim sağlar.  
  
 ![Ortam mimari grafiği](../../extensibility/internals/media/environment.gif "ortamı")  
Visual Studio mimari genelleştirilmiş görünümü  
  
## <a name="vspackages"></a>VSPackage’lar  
 VSPackage oluşturan ve Visual Studio UI öğeleri, hizmetleri, projeler, düzenleyiciler ve tasarımcılar ile genişleten yazılım modülleri olan. VSPackage'ları Visual Studio'nun Merkezi mimari birim var. Daha fazla bilgi için [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Kabuğu  
 Visual Studio Kabuğu, temel işlevleri sağlar ve bileşen VSPackages ve MEF uzantıları arasında arası iletişimi destekler. Daha fazla bilgi için [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Kullanıcı Deneyimi Yönergeleri  
 Visual Studio için yeni özellikler tasarlama, planlama, tasarım ve kullanılabilirlik ipuçları için bu yönergeleri göz atın: [Visual Studio kullanıcı deneyimi yönergeleri](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Komutlar  
 Yazdırma, bir görünümü yenileme veya yeni bir dosya oluşturmak gibi görevleri gerçekleştirmek işlevleri komutlardır.  
  
 Visual Studio genişlettiğinizde, komutları oluşturabilir ve bunları Visual Studio Kabuğu ile kaydedin. Bu komutlar IDE'de, örneğin, bir menü veya araç görüntülenme belirtebilirsiniz. Özel komut genellikle görünür **Araçları** menü ve araç penceresini görüntülemek için komut çubuğunda görüneceği **diğer Windows** alt **görünümü** menüsü.  
  
 Bir komut oluşturduğunuzda, aynı zamanda bir olay işleyicisi için oluşturmanız gerekir. Olay işleyicisi, ne zaman komut görünür veya etkin yazısının değiştirmenize olanak tanır ve bu etkinleştirildiğinde komutu uygun şekilde yanıt garanti eder belirler. Çoğu durumda, IDE komutlarını kullanarak işleme <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Visual Studio komutları yerel seçimi temel alınarak ve genel seçime göre en dıştaki bağlamı geçmeden en içteki komut bağlam başlayarak işlenir. Ana menüye eklenen komutlar, komut dosyası için hemen kullanılabilir.  
  
 Daha fazla bilgi için [komutlar, menüler ve araç çubukları](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menüleri ve araç çubukları  
 Menüleri ve araç çubuklarını komutları çağırmak bir yol sağlar. Satırlar veya sütunlar genellikle tek bir metin öğeleri üst araç penceresi olarak görüntülenen komutların menüler şunlardır. Alt menüler kullanıcı küçük bir ok içerir komutları tıkladığında görüntülenen ikincil menüler şunlardır. Bağlam menüleri, bir kullanıcı belirli bir kullanıcı Arabirimi öğeleri tıkladığında görüntülenir. Bazı ortak menü adları **dosya**, **Düzenle**, **görünümü**, ve **penceresi**. Daha fazla bilgi için [genişletme menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
 Araç çubukları, satırlar veya sütunlar düğmeler ve birleşik giriş kutuları ve liste kutuları metin kutuları gibi diğer denetimlerin ' dir. Araç çubuğu düğmeleri, genellikle bir klasör simgesini gibi simge görüntüleri sahip bir **açık dosya** komut veya yazıcı için bir **yazdırma** komutu. Tüm araç çubuğu öğelerini komutları ile ilişkilidir. Araç çubuğu düğmesini tıkladığınızda, ilişkili komutunu çalıştırır. Aşağı açılan denetim söz konusu olduğunda, açılan listedeki her öğe başka bir komut ile ilişkilidir. Bölümlendirici denetimi gibi bazı araç çubuğu denetimleri sınıflarınızın bir karmasını ' dir. Denetimin bir tarafı araç çubuğu düğmesi ve diğer tarafı birkaç komut tıklatıldığında görüntüleyen bir aşağı oku.  
  
## <a name="tool-windows"></a>Aracı Windows  
 Araç Pencereleri IDE içinde bilgilerini görüntülemek için kullanılır. **Araç kutusu**, **Çözüm Gezgini**, **özellikleri** penceresinde ve **Web tarayıcısı** araç pencereleri örnekleridir.  
  
 Araç pencereleri, normalde kullanıcı ile etkileşim kurabilir çeşitli denetimler sunar. Örneğin, **özellikleri** pencere kullanıcının belirli bir amaca hizmet nesnelerin özelliklerini ayarlamasına olanak sağlar. **Özellikleri** penceresi olduğundan bu bağlamda özel ancak aynı zamanda genel birçok farklı durumlarda kullanılabilir. Benzer şekilde, **çıkış** penceresi çünkü Visual Studio'da birçok alt sistemleri için Visual Studio kullanıcı çıkış sağlamak için kullanabilirsiniz, ancak genel metin temelli çıktı sağladığından özelleştirilmiş.  
  
 Aşağıdaki resimde birçok araç pencereleri içeren Visual Studio göz önünde bulundurun.  
  
 ![Ekran görüntüsü](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Bazı araç pencereleri birlikte, Çözüm Gezgini araç penceresini görüntüler ve diğer araç pencereleri gizliyor ancak sekmeleri tıklayarak kullanılabilir kılar tek bölmesindeki sabitlenir. Diğer iki araç pencereleri, resim gösterir **hata listesi** ve **çıkış** birlikte bir bölmeden yerleştirilmiş penceresinde.  
  
 Ayrıca gösterilen çeşitli düzenleyici pencereleri gösterir ana belge bölmesinde olur. Araç pencereleri, genellikle yalnızca bir örneğine sahip olsa da (örneğin, yalnızca bir açabilirsiniz **Çözüm Gezgini**), düzenleyici pencerelerini, her biri ayrı bir belge düzenlemek için kullanılır, ancak her biri olarak yerleştirilen birden çok örneği olabilir aynı bölme. Resim iki düzenleyici pencereleri, bir form tasarımcısı penceresi ve başlangıç sayfası gösteren bir tarayıcı penceresi sahip bir belge bölmesi gösterir. Sekmeleri tıklayarak tüm windows belge bölmesinde kullanılabilir, ancak EditorPane.cs dosyasını içeren Düzenleyicisi penceresi görünür ve etkin.  
  
 Visual Studio genişlettiğinizde, Visual Studio kullanıcıların windows etkileşim aracı uzantınız ile oluşturabilirsiniz. Visual Studio kullanıcılarına belgeleri düzenlemesine izin veren kendi düzenleyicileri de oluşturabilirsiniz. Araç pencereleri ve düzenleyicileri Visual Studio ile tümleşik olduğundan, yerleştirme ya da bir sekmesinde doğru şekilde görünen program gerekmez. Visual Studio'da kayıtlı doğru olduğunda otomatik olarak araç pencereleri ve belge pencereleri Visual Studio'da tipik özellikler sahip olacaktır. Daha fazla bilgi için [genişletme ve özelleştirme araç Windows](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Belge Pencereleri  
 Bir belge penceresi, bir Çoklu belge arabirimi (MDI) penceresi Çerçeveli alt penceredir. Belge pencereleri genellikle metin düzenleyiciler, form Düzenleyicileri (tasarımcıları olarak da bilinir) veya düzenleme denetimleri barındırmak için kullanılan, ancak işlev diğer türleri de barındırabilir. **Yeni dosya** iletişim kutusu, Visual Studio sağlayan bir belge windows örneklerini içerir.  
  
 Çoğu düzenleyicileri, belirli bir programlama dili veya HTML sayfaları, çerçeve, C++ dosyaları ve üstbilgi dosyaları gibi bir dosya türü için. Bir şablon seçerek **yeni dosya** iletişim kutusu, bir kullanıcı dinamik olarak bir belge penceresi Düzenleyicisi şablonu ile ilişkili dosya türü için. Mevcut bir dosyayı kullanıcı oturum açtığında bir belge penceresi de oluşturulur.  
  
 Belge pencereleri için MDI istemci alanını kısıtlanır. Her belge penceresinde üstte bir sekmesi vardır ve sekme sırası MDI alanında açık olabilir. diğer windows bağlantılıdır. Bir belge penceresi sekmesine sağ tıklayarak MDI alan birden çok yatay veya dikey sekme grupları bölmek için seçenekleri içeren bir kısayol menüsünü görüntüler. MDI alanı bölme birden çok dosyayı aynı anda görüntülenmesini sağlar. Daha fazla bilgi için [belge Windows](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Düzenleyiciler  
 Visual Studio Düzenleyicisi, özelleştirebilir ve Yönetilen Genişletilebilirlik Çerçevesi'yoluyla (MEF) kendi içerik türü kullanmak sağlar. Çoğu durumda (örneğin, bir menü komutu veya bir kısayol tuşu) kabuğundan özelliklerini dahil etmek istiyorsanız, bir MEF uzantısı ile VSPackage birleştirebilirsiniz ancak Düzenleyicisi'ni genişletmek için bir VSPackage'ı oluşturma gerekmez.  
  
 Örneğin, özel bir düzenleyici Ayrıca, okuma ve yazma için bir veritabanı istiyorsanız ya da bir tasarımcı kullanmak istiyorsanız da oluşturabilirsiniz. Not Defteri veya Microsoft WordPad gibi harici bir düzenleyici kullanabilirsiniz. Daha fazla bilgi için [düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Dil Hizmetleri  
 Yeni programlama anahtar sözcük ya da daha yeni bir programlama dili desteklemek için Visual Studio Düzenleyicisi istiyorsanız, bir dil hizmeti oluşturun. Her dil hizmeti belirli bir düzenleyici özellikleri tam olarak, kısmen veya hiç uygulayabilir. Dil hizmeti nasıl yapılandırıldığına bağlı olarak, söz dizimi vurgulama, ayraç eşleştirme, IntelliSense desteği ve diğer Düzenleyici özellikleri sağlayabilir.  
  
 Bir dil hizmetinin temelini, bir ayrıştırıcı ve tarayıcı ' dir. Bir tarayıcı (veya sözcük temelli çözümleyici) belirteçleri bilinen öğeleri bir kaynak dosyası böler ve bu belirteçleri arasındaki ilişkileri bir ayrıştırıcı oluşturur. Dil hizmeti oluşturduğunuzda, Visual Studio dilinin dil bilgisi ve belirteçleri anlayabilmeniz ayrıştırıcısı ve tarayıcısı uygulamalıdır. Yönetilen veya yönetilmeyen dil Hizmetleri oluşturabilirsiniz. Daha fazla bilgi için [eski dil hizmeti genişletilebilirliği](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projeler  
 Visual Studio'da projeler geliştiriciler düzenleyebilir ve kaynak kodu ve diğer kaynakları oluşturmak için kullandığınız kapsayıcılardır. Düzenleme, derleme, hata ayıklama ve kaynak kodunu Dağıt let projeleri, Web Hizmetleri ve veritabanları ve diğer kaynaklara başvuruyor. VSPackage'ları, Visual Studio Proje sistemi proje türleri, proje alt türleri ve özel araçlar sağlayarak genişletebilirsiniz.  
  
 Projeleri, bir uygulama oluşturmak için birlikte çalışan bir veya daha fazla proje gruplandırmasıdır bir çözümde de toplanan. İlgili çözüme proje ve durum bilgilerini iki çözüm dosyaları, metin tabanlı çözüm (.sln) dosyasını ve ikili çözüm kullanıcı seçeneği (.suo) dosyası depolanır. Bu dosyalar, önceki sürümlerinde kullanılan Grup (.vbg) dosyaları benzer [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], çalışma alanı (.dsw) ve kullanıcı seçeneklerini'nın önceki sürümlerinde kullanılan (.opt) dosyaları [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Daha fazla bilgi için [projeleri](../../extensibility/internals/projects.md) ve [çözümleri](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Proje ve Öğe Şablonları  
 Visual Studio, önceden tanımlanmış proje şablonları ve proje öğesi şablonları içerir. Ayrıca kendi şablonlarınızı olun veya topluluk şablonlarını almak ve sonra bunları Visual Studio ile tümleştirin. [MSDN Kod Galerisi](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) şablonları ve uzantılar için Git yerdir.  
  
 Şablonlar, Proje yapısı ve belirli bir uygulama, Denetim, kitaplık veya sınıf türünü oluşturmak için gereken temel dosyaları içerir. Şablonlardan birini benzer yazılım geliştirme istediğinizde, şablonu temel alan bir proje oluşturun ve ardından bu projedeki dosyaları değiştirin.  
  
> [!NOTE]
>  Bu şablonu mimarisi için desteklenmiyor [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projeleri. Nasıl oluşturulacağı hakkında daha fazla bilgi için [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje şablonları, bkz: [sihirbaz tasarlama](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Daha fazla bilgi için [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Özellikleri ve seçenekleri  
 **Özellikleri** penceresi tek veya birden çok Seçili öğelerin özelliklerini görüntüler: [genişletme özellikleri](../../extensibility/internals/extending-properties.md) seçenekler sayfaları gibi belirli bir bileşene ait seçenekleri kümesi içeren bir programlama dili veya VSPackage: [seçenekler ve Seçenekler sayfaları](../../extensibility/internals/options-and-options-pages.md). Ayarları içeri ve dışarı genellikle kullanıcı Arabirimi güvenlikle ilgili özellikler şunlardır: [kullanıcı ayarları desteği](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Visual Studio Hizmetleri  
 Bir hizmet arabirimleri tüketmeye bileşenleri için belirli bir kümesini sağlar. Visual Studio uzantıları dahil olmak üzere tüm bileşenleri tarafından kullanılabilecek Hizmetleri kümesi sağlar. Örneğin, araç pencerelerini gösterilecek veya dinamik olarak gizli Yardım, durum çubuğu veya UI olayları erişmesini sağlamak Visual Studio hizmetleri sağlar. Visual Studio Düzenleyicisi, düzenleyici uzantıları tarafından içe aktarılabilir hizmetleri de sağlar. Daha fazla bilgi için [kullanma ve sağlama Hizmetleri](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Hata Ayıklayıcısı  
 Hata ayıklayıcı, dile özgü hata ayıklama bileşenleri için kullanıcı arabirimidir. Yeni bir dil hizmeti oluşturduysanız, hata ayıklayıcıya için belirli hata ayıklama altyapısı oluşturmak gerekir. Daha fazla bilgi için [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Kaynak Denetimi  
 Kaynak Denetimi Eklentisi veya VSPackage'ı uygulama hakkında daha fazla bilgi için bkz: [kaynak denetimi](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Sihirbazlar  
 Yeni bir proje türü ile birlikte bir sihirbaz oluşturabilirsiniz, böylece sihirbaz yardımcı olabilir, bu türdeki yeni bir proje oluşturduğunuzda, kullanıcılarınızın doğru kararlar. Daha fazla bilgi için [sihirbazları](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Özel Araçlar  
 Özel Araçlar bir aracı bir projede bir öğe ile ilişkilendirmek ve dosyanın kaydedildiği zaman bu aracı sağlar. Daha fazla bilgi için [özel Araçlar](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>VSSDK Yardımcı Programları  
 VSSDK birtakım farklı yönlerini VSPackage'ları ile çalışmak için ihtiyacınız olan araçları içerir. Daha fazla bilgi için [VSSDK yardımcı programları](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Windows Installer kullanarak  
 Bazı durumlarda VSIX yükleyicisi yerine Windows Yükleyici kullanmanız gerekebilir: Örneğin, kayıt defterine yazma gerekebilir. Windows Installer uzantılarınız ile kullanma hakkında daha fazla bilgi için bkz: [yükleme VSPackage'ları ile Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Yardım Görüntüleyicisi  
 Yardım Görüntüleyicisi'ne kendi Yardım ve F1 sayfaları tümleştirebilirsiniz. Daha fazla bilgi için [Microsoft Yardım Görüntüleyicisi SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).

