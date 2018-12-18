---
title: Visual Studio 2017’deki yenilikler
titleSuffix: ''
description: Visual Studio 2017'de yeni özellikler hakkında bilgi edinin.
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c490d15f27801dff6bb09f6356ad7c665b09c558
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160198"
---
# <a name="what39s-new-in-visual-studio-2017"></a>Hangi&#39;Visual Studio 2017'deki yenilikler

**İçin güncelleştirilmiş [15,9 sürüm](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Visual Studio'nun önceki bir sürümden yükseltme mi istiyorsunuz? Hangi Visual Studio 2017, sunabileceğiniz aşağıda verilmiştir: Herhangi bir geliştirme, herhangi bir uygulama ve tüm platformlar için eşsiz üretkenlik. Android, iOS, Windows, Linux, web ve bulut için uygulamalar geliştirmek için Visual Studio 2017'yi kullanın. Hızlı kod yazın, kolayca hata ayıklama ve tanılama yapın, sık sık test edin ve güvenle kullanıma sunun. Ayrıca, kendi uzantılarınızı oluşturarak Visual Studio’yu özelleştirebilir ve kapsamını genişletebilirsiniz. Sürüm denetimi kullanın, Çevik ve bu sürümle birlikte verimli bir şekilde işbirliği yapın!

Önceki sürümden itibaren Visual Studio 2015 yapılan değişiklikler üst düzey bir özeti aşağıda verilmiştir:

* **[Yeniden Temelleri](#redefined-fundamentals)**. Yeni bir kurulum deneyimi, daha hızlı bir şekilde yüklemek ve ihtiyacınız olduğunda istediğiniz yükleme anlamına gelir.
* **[Performans ve üretkenlik](#performance-and-productivity)**. Yeni ve modern mobil, Bulut ve masaüstü geliştirme özellikleri odaklanan. Ve Visual Studio daha hızlı başlatılan, daha hızlı ve daha önce daha az bellek kullanır.
* **[Bulut uygulaması geliştirme sürecini Azure ile](#cloud-app-development-with-azure)**. Bir yerleşik Azure araç paketi Microsoft Azure tarafından desteklenen bulut öncelikli uygulamaları kolayca oluşturmanıza olanak tanır. Visual Studio, yapılandırmak, derleme, hata ayıklama, paket ve uygulamalarınızı ve hizmetlerinizi azure'da dağıtmak kolaylaştırır.
* **[Windows uygulama geliştirme](#windows-app-development)**. Tüm Windows 10 cihazlar için tek bir proje oluşturmak için Visual Studio 2017'deki UWP şablonlarını kullanma &ndash; PC, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazla.
* **[Mobil uygulama geliştirme](#mobile-app-development)**. Yenilik yapın ve hızlı Xamarin, çok platformlu mobil gereksinimlerinizi bir çekirdek kod temeli ve becerileri kümesini birleştiren ile sonuçlar elde edin.
* **[Platformlar arası geliştirme](#cross-platform-development)**. Sorunsuz bir şekilde hedeflenen her platforma yazılım sunun. SQL Server'a Redgate veri araçları aracılığıyla DevOps süreçlerini genişletin ve Visual Studio'dan veritabanı dağıtımlarını güvenle otomatikleştirin. Veya .NET Core uygulamaları ve Windows, Linux ve macOS işletim sistemleri arasında değiştirilmeden çalıştırılmasını kitaplıklar yazmak için kullanın.
* **[Oyunlar geliştirme](#games-development)**. Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz.
* **[Yapay ZEKA geliştirme](#ai-development)**. AI için Visual Studio Araçları ile yapay ZEKA yeniliği hızlandırmaya yönelik Visual Studio üretkenlik özelliklerini kullanabilirsiniz. Derleme, test etme ve dağıtma derin öğrenme / AI çözümleri, sorunsuz şekilde tümleştirin Azure Machine Learning ile sağlam deneme özellikleri için.

> [!NOTE]
> Yeni özellikler ve işlevler Visual Studio 2017'de tam listesi için bkz: [geçerli sürüm notları](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Ve gelecekteki özellik teklifleri bir bilgi için bkz: [Preview sürüm notları](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Bazı en önemli geliştirmeler ve Visual Studio 2017'de yeni özellikler hakkında daha ayrıntılı bilgi aşağıda verilmiştir.

## <a name="redefined-fundamentals"></a>Temel kavramlar yeniden tanımlandı

### <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi

[Visual Studio 2017'yi indirin](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) veya [denetleyin Visual Studio sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs?context=visualstudio/default&contextView=vs-2017)

 Visual Studio, daha kolay ve yalnızca ihtiyacınız olduğunda, ihtiyacınız olan özellikleri yüklemek için daha hızlı bir şekilde getirir. Ve iz bırakmadan, çok kaldırılır.

 Visual Studio yüklediğinizde dikkat edilecek en önemli yeni kurulum deneyimini farklıdır. Üzerinde **iş yükleri** sekmesi, ortak çerçeveleri, dilleri ve platformları temsil etmek için gruplandırılır yükleme seçenekleri göreceksiniz. .NET masaüstü geliştirme için Windows, Linux ve iOS uygulama geliştirmeyi C++ kadar her şeyi kapsar.

İş yükleri gerekir ve gerektiğinde bunları değiştirin seçin.

 ![Visual Studio 2017 Kurulum iletişim kutusu](../install/media/install-visual-studio-enterprise.png)

Ve yüklemenizi çok ince ayar seçenekleriniz var:

* İş yükleri kullanmak yerine kendi bileşenleri çekme istiyorsunuz? Seçin **tek tek bileşenler** yükleyici sekmesinden.
* Ayrıca Windows dil seçeneğini değiştirmek zorunda kalmadan dil paketlerini yüklemek istiyorsunuz? Seçin **dil paketlerini** yükleyici sekmesi.
* **15.7 sürümündeki yeni**: Burada Visual Studio'yu yükler konumu değiştirilsin mi? Seçin **yükleme seçenekleri** yükleyici sekmesi.

Size yol gösteren yönergeler dahil olmak üzere yeni yükleme deneyimi hakkında daha fazla bilgi için bkz: [Visual Studio'yu yükleyin](../install/install-visual-studio.md) sayfası.

### <a name="a-focus-on-accessibility"></a>Erişilebilirlik odaklanır

**15.3 yeni**, Visual Studio kullanan birden çok müşteriye yardımcı teknolojiler arasındaki uyumluluğu artırmak için 1700 hedeflenen düzeltmeleri yaptık. Daha önce hiç olmadığı kadar ekran okuyucuları, yüksek karşıtlıklı tema ve diğer yardımcı teknolojiler ile daha uyumlu olan senaryoları onlarca vardır. Hata ayıklayıcı, düzenleyici ve kabukta tüm gotten önemli geliştirmeler içerir.

Daha fazla bilgi için [erişilebilirlik geliştirmeleri Visual Studio 2017 sürüm 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisi.

## <a name="performance-and-productivity"></a>Performans ve üretkenlik

### <a name="sign-in-across-multiple-accounts"></a>Birden fazla hesabında oturum açın

Biz, Visual Studio'da, kullanıcı hesaplarını Takım Gezgini, Azure Araçları, Microsoft Store yayımlama ve daha fazlası arasında paylaşmamıza olanak tanıyan yeni bir kimlik hizmetini kullanıma sunduk.

Artık, çok oturum açmış durumda kalabilir. Visual Studio 12 saatte yeniden imzalamanız sormaz. Daha fazla bilgi için bkz. [daha az Visual Studio oturum açma ister](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) blog gönderisi.

### <a name="start-visual-studio-faster"></a>Visual Studio daha hızlı başlayın

Yeni Visual Studio performans Merkezi'ni, IDE başlatma süresini en iyi hale getirmenize yardımcı olabilir. Performans merkezi tüm araç pencerelerini IDE başlatma yavaşlatabilir ve uzantıları listeler. Uzantılar ne zaman başlar ve araç pencerelerini başlangıçta açık olup belirleyerek başlangıç performansını artırmak için kullanabilirsiniz.

### <a name="faster-on-demand-loading-of-extensions"></a>Uzantı hızlı isteğe bağlı yükleme

Visual Studio uzantılarını taşıma (ve üçüncü taraf uzantıları çok çalışma) ve böylece bunlar üzerine yüklemek yerine, IDE başlangıçta. Hangi uzantıları etkisi başlangıç, çözüm yükü ve yazma performansını merak ediyor? Bu bilgileri görebilirsiniz **yardımcı** > **Visual Studio performansını Yönet**.

  ![Visual Studio 2017'de, Seçenekler iletişim kutusu](../ide/media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Uzantılarınızı uzantı dolaşımı Yöneticisi ile yönetme

Visual Studio'da oturum açtığınızda tüm geliştirme ortamlarını sık kullandığınız uzantıların ayarlamak daha kolaydır. Yeni eklenen uzantı dolaşımı Yöneticisi, sık kullandığınız uzantıların bulutta eşitlenmiş bir liste oluşturarak izler.

Visual Studio, uzantıların listesini görmek için tıklayın **Araçları** > **Uzantılar ve güncelleştirmeler**ve ardından **uzantı dolaşımı Yöneticisi**.

![Visual Studio 2017 - Uzantılar ve güncelleştirmeler iletişim kutusu](../ide/media/vs2017ide-extensions-and-updates.png)

Uzantı dolaşımı Yöneticisi yüklediğiniz uzantıları izler, ancak Dolaşım listenize eklemek istediklerinizi seçebilirsiniz.

![Visual Studio 2017 - Uzantılar ve güncelleştirmeler iletişim kutusu](../ide/media/vs2017ide-RoamingExtensionManager.png)

Uzantı dolaşımı Yöneticisi'ni kullandığınızda, listenizde üç simge türü vardır:

* ![Dolaşıma açıldı simgesi](../ide/media/vs2017ide-roamedicon.png)  **_dolaşıma_**: Dolaşım bu listenin parçası, ancak, makinede yüklü olmayan bir uzantı.
  (Bu kullanarak yükleyebileceğiniz **indirme** düğmesi.)
* ![Dolaşıma açıldı ve yüklendi simgesi](../ide/media/vs2017ide-roamedinstalledicon.png)  **_dolaşıma açıldı ve yüklü_**: Dolaşım bu listenin parçası olan ve geliştirme ortamınızda yüklenen tüm uzantıları.
  (Dolaşımda olabilen istemediğiniz karar verirseniz, bu kullanarak kaldırabilirsiniz **dolaşımı Durdur** düğmesi.)
* ![Yüklü simgesi](../ide/media/vs2017ide-installedicon.png)  **_yüklü_**: Bu ortamda yüklü, ancak Dolaşım listenize parçası olmayan tüm uzantıları.
  (Kullanarak uzantılar Dolaşım listesine ekleyebilirsiniz **Başlat Dolaşım** düğmesi.)

Oturumunuz sırasında indirdiğiniz herhangi bir uzantı listenize eklenir **dolaşıma açıldı ve yüklü**. Uzantı için herhangi bir makineden erişmenizi sağlar, dolaşım listenizin bir parçası olur.

### <a name="experience-live-unit-testing"></a>Live unit Testing deneyimi

Visual Studio Enterprise 2017'de, Canlı birim sınama kodlamaya devam ederken, birim testi sonuçlarını ve kod kapsamını düzenleyicide Canlı sağlar. .NET Framework ve .NET Core için C# ve Visual Basic projeleri ile çalışır ve MSTest, xUnit ve NUnit çerçevelerini destekler.

![Live Unit Testing](../ide/media/lut-codewindow.png)

Daha fazla bilgi için [giriş Live Unit Testing](../test/live-unit-testing-intro.md). Her Visual Studio Enterprise 2017 sürümünde eklenen yeni özelliklerin bir listesi için bkz. [Live Unit Testing yenilikler](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Bir CI/CD işlem hattı ayarlayın

#### <a name="automated-testing"></a>Otomatik test

Otomatikleştirilmiş test, herhangi bir DevOps işlem hattına önemli bir parçasıdır. Bu, tutarlı bir şekilde sağlar ve güvenilir bir şekilde test ve çözümünüzü daha kısa Döngülerde üzerinde bırakın. CI/CD (sürekli tümleştirme ve sürekli teslim) akışlar, işlem daha verimli olun yardımcı olabilir.

Otomatikleştirilmiş testleri hakkında daha fazla bilgi için bkz: [DevOps otomatikleştirilmiş testler CI/CD işlem hattı](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) blog gönderisi.

Ve yenilikler hakkında daha fazla bilgi için [Visual Studio için sürekli teslim Araçları](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) adlı DevLabs uzantısının bkz [güvenle işleyin: İşleme zamanı kod kalitesini](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) blog gönderisi.

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE geliştirmeleri

#### <a name="multi-caret-editing"></a>Birden çok giriş işaretini düzenleme

**Yeni 15,8**: Aynı anda birden fazla konumda bir dosya düzenlemeye hemen kolaydır. Bir dosya içinde birden çok konumda ekleme noktaları ve seçimleri oluşturarak başlayın. Ardından, aynı anda iki veya daha fazla yerde aynı düzenleme yapmak birden çok giriş işaretini düzenleme özelliğini kullanın.

Daha fazla bilgi için [birden çok giriş işaretini seçimi](finding-and-replacing-text.md#multi-caret-selection) bölümünü, [metin bulma ve değiştirme](finding-and-replacing-text.md) sayfası.

#### <a name="keep-keybinding-profiles-consistent"></a>Tuş profilleri tutarlı tutun

**Yeni 15,8**: Şimdi, tuş bağlamaları tutarlı iki yeni klavye profilleriyle araçlar arasında tutabildiğiniz: Visual Studio Code ve ReSharper (Visual Studio). Bu düzenleri altında bulabilirsiniz **Araçları** > **seçenekleri** > **genel** > **klavye**ve üstteki açılan menüsü.

  ![Visual Studio Code ve ReSharper yeni tuş profilleri](../ide/media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Yeni yeniden düzenlemeler kullanın

Yeniden düzenleme, yazıldıktan sonra kodu geliştirme işlemidir. Yeniden düzenleme, kod iç yapısını davranışını değiştirmeden değiştirir. Biz genellikle yeni yeniden düzenlemeler ekleyin; birkaçı şunlardır:

* Parametre Ekle (çağıran site)
* Geçersiz kılmaları oluştur
* Adlandırılmış bağımsız değişkeni ekleyin
* Parametre için null denetimi Ekle
* Rakam ayırıcıları değişmez değerleri Ekle
* Sayısal değişmez değerleri (örneğin, ikili onaltılık) için temel değiştirme
* İf anahtar Dönüştür
* Kullanılmayan değişkeni Kaldır

Daha fazla bilgi için [hızlı Eylemler](../ide/common-quick-actions.md).

#### <a name="interact-with-git"></a>Git ile etkileşim kurma

Visual Studio'da bir proje ile çalışırken, ayarlayabilir ve hızlı bir şekilde işleyin ve kodu bir Git hizmetinde yayımlayın. Git depolarınız sağ alt köşede IDE'nin düğme tıklama menüsünü kullanarak da yönetebilirsiniz.

![Visual Studio 2017 ile Git iletişim etkileşim kurar.](../ide/media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>İyileştirilmiş Gezinti denetimlerinin deneyimi

Biz A B daha güvenle ve daha az dikkat dağıtıcı faktör almanıza yardımcı olması için gezinti deneyimini de yeniledik.

* **15.4 yeni**: **Tanıma Git** (**Ctrl**+**tıklayın** veya **F12**) &ndash; fare kullanıcınız tanımına gitmek için daha kolay bir yolu bir üye tuşuna basarak **Ctrl** tıklayıp üyesi. Tuşuna basarak **Ctrl** ve bir kod simgesinin geldiğinizde, alt çizgi ve bir bağlantıya açın. Bkz: [tanıma ve Özet tanım](../ide/go-to-and-peek-definition.md) daha fazla bilgi için.

* **Uygulamaya Git** (**Ctrl**+**F12**) &ndash; , çeşitli uygulamaları herhangi bir temel tür veya üye gidin.

* **Tümüne Git** (**Ctrl**+**T** veya **Ctrl**+**,**) &ndash; gidin doğrudan bir dosya/türü/üyeye/sembole bildirimi için. Sonuç listenizi filtrelemek veya sorgu sözdizimi (örneğin, "f searchTerm" dosyalarının.), "t searchTerm" türleri gibi şeyler için kullanın.

  ![Geliştirilmiş tüm Git](../ide/media/vs2017ide-navigation-go-to.png)

* **Tüm başvuruları Bul** (**Shift**+**F12**) &ndash; söz dizimi renklendirme ile proje, tanım, bir birleşimi tarafından tüm başvuruları Bul sonuçları gruplandırabilirsiniz ve yolu. "Diğer başvurular özgün sonuçlarınızı kaybetmeden bulmak devam edebilmesi için ayrıca sonuçları kilitleyebilirsiniz".

  ![Yeni bir tüm başvuruları Bul aracı](../ide/media/vs2017ide-find-all-references.png)

* **Yapı Görselleştirici** &ndash; noktalı gri dikey çizgileri (Girinti kılavuzları) görünümünün çerçeveniz içinde bağlam sağlamak için kod yer işareti olarak davranır. Bunları popüler Productivity Power Tools algılayabilir. Görselleştirme ve hangi kod bloğunun herhangi bir zamanda kaydırma yapmak zorunda kalmadan bulunduğunuz bulmak için bunları kullanabilirsiniz. Satırlar üzerinde bekleyerek, o blok ve onun ana öğelerinden başlangıcını gösteren araç ipucu görüntülenir. TextMate dil bilgisi, hem de C#, Visual Basic ve XAML desteklenen tüm diller için kullanılabilir.

  ![Visual Studio 2017 yapı Görselleştirici](../ide/media/vsIDE-StructureVisualizer.png)

Yeni verimlilik özellikleri hakkında daha fazla bilgi için bkz: [üretkenlik Visual Studio 2017'de](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) blog gönderisi işareti Wilson-Thomas'tarafından.

### <a name="visual-c"></a>Visual C++

C++ temel yönergeleri, derleyici C ++ 11 ve C++ özellikleri ve ekleme ve C++ kitaplıklarında işlevselliği güncelleştirmek için gelişmiş destek ekleyerek güncelleştirme Visual Studio ile dağıtma gibi Visual Studio'da, çeşitli iyileştirmeler görürsünüz. C++ IDE, yükleme iş yükleri ve daha fazla performans de geliştirdik.

De biz 250'den fazla hatalar düzeltildi ve bildirilen sorunları derleyici ve araçları, çoğu aracılığıyla müşteriler tarafından gönderilen [c++ Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/62/index.html "c++ Geliştirici topluluğu").

Tüm Ayrıntılar için bkz. [Visual 2017'deki Visual c++ yenilikleri](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) sayfası.

### <a name="debugging-and-diagnostics"></a>Hata ayıklama ve tanılama

#### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Şimdi, daha kolay gerçekleştirmek istediğiniz satırda durdurmak için kesme noktası ayarlamadan hata ayıklama sırasında atlayabilirsiniz. Hata ayıklayıcıda durdurulduklarında görünen kod satırının yanındaki simgeye tıklamanız yeterlidir. Kodunuzu çalıştırın ve söz konusu satıra kod yolunuzda isabet durur.

![Visual Studio 2017 hata ayıklama - tıklanan satıra kadar Çalıştır](../ide/media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Yeni özel durum Yardımcısı

Yeni özel durum Yardımcısı, özel durum bilgilerini bir bakışta görmenizi sağlar. Bilgiler, iç özel durumlara anında erişim compact formda sunulur. NullReferenceException tanılayın, şu özel durum Yardımcısı null hızlıca görebilirsiniz.

![Visual Studio'da yeni bir özel durum Yardımcısı iletişim kutusu](../ide/media/vs2017ide-ExceptionHelper.png)

Daha fazla bilgi için [Visual Studio'da yeni özel durum Yardımcısı'nı kullanın](https://blogs.msdn.microsoft.com/devops/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) blog gönderisi.

#### <a name="snapshots-and-intellitrace-step-back"></a>Anlık görüntüler ve IntelliTrace geri adım atma

**15.5 yeni**: IntelliTrace geri adım, otomatik olarak adım olay, her bir kesme noktası ve hata ayıklayıcı uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntü, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntülemek etkinleştirin. IntelliTrace geri adım atma önceki uygulama durumu görmek istiyorsanız ancak hata ayıklamayı yeniden başlatın veya istenen uygulama durumu yeniden istemediğiniz durumlarda size zaman kazandırabilir.

Gidin ve anlık görüntüleri kullanarak görüntüle **adım geriye dönük** ve **İleri** içinde düğmeleri **hata ayıklama** araç çubuğu. Bu düğmeler görünen olaylar gidin **olayları** sekmesinde **tanılama araçları** penceresi. Geriye veya ileriye doğru bir olay için otomatik olarak Adımlama Seçili olayda geçmiş hata ayıklamayı etkinleştirir.

![Visual Studio'da yeni bir özel durum Yardımcısı iletişim kutusu](../debugger/media/intellitrace-step-back-icons-description.png  "adım geri ve İleri düğmelerini")

Daha fazla bilgi için [IntelliTrace geri adım atmayı kullanarak anlık görüntüleri görüntüle](../debugger/how-to-use-intellitrace-step-back.md) sayfası.

### <a name="containerization"></a>Kapsayıcı

Kapsayıcılar ile daha fazla uygulama yoğunluğu ve daha düşük bir dağıtım maliyeti yanı sıra geliştirilmiş üretkenlik ve DevOps çeviklik sağlayın.

#### <a name="docker-container-tooling"></a>Docker kapsayıcısı araçları

**15.5 yeni**:

* Visual Studio artık iyileştirilmiş kapsayıcı görüntülerinin hangi basitleştirin oluşturma çok aşamalı dockerfile'ları destekliyor Docker kapsayıcılarına ilişkin araçları içerir.
* Varsayılan olarak Visual Studio, Docker desteği olan bir projeyi açtığınızda gerekli kapsayıcı görüntülerini otomatik olarak çeker, derler ve arka planda çalıştırır. Bunu, Visual Studio'da **Kapsayıcıları arka planda otomatik olarak başlat** ayarı ile devre dışı bırakabilirsiniz.

## <a name="cloud-app-development-with-azure"></a>Azure ile bulut uygulaması geliştirme

### <a name="azure-functions-tools"></a>Azure işlevleri araçları

"Azure geliştirme" iş yükünün parçası, önceden derlenmiş C# sınıf kitaplıkları kullanarak Azure işlevleri geliştirmenize yardımcı olacak araçlar ekledik. Artık derleme, çalıştırmak ve yerel geliştirme makinenizde hata ayıklayın ve ardından Visual Studio'dan doğrudan Azure'a yayımlama.

Daha fazla bilgi için [Visual Studio için Azure işlevleri Araçları](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) sayfası.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Anlık görüntü noktaları ve günlüğe kaydetme noktaları Canlı Azure uygulamalarında kullanarak canlı ASP.NET uygulamalarının hatalarını ayıklama

**15.5 yeni**: Snapshot Debugger, ilgilendiğiniz kod yürütüldüğünde, üretim uygulamalarınızı anlık görüntüsünü alır. Bir anlık görüntüsünü almak için hata ayıklayıcı açmasını sağlamak için anlık görüntü noktaları ve günlüğe kaydetme noktaları kodunuzda ayarlayın. Hata ayıklayıcı, tam olarak üretim uygulamanızın trafiğini etkilemeden, çıktığına görmenizi sağlar. Snapshot Debugger, üretim ortamlarında ortaya çıkan sorunları çözmek için gereken süreyi ciddi ölçüde azaltmaya yardımcı olabilir.

Anlık görüntü koleksiyonunu, Azure App Service'te çalışan aşağıdaki web uygulamaları için kullanılabilir:

* .NET Framework 4.6.1 üzerinde çalışan ASP.NET uygulamalarından veya üzeri.
* .NET Core 2.0 veya daha sonra Windows üzerinde çalışan ASP.NET Core uygulamaları.

Daha fazla bilgi için [anlık görüntü noktaları ve günlüğe kaydetme noktaları'nı kullanarak canlı ASP.NET uygulamaları için hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Windows uygulaması geliştirme

### <a name="universal-windows-platform"></a>Evrensel Windows Platformu

Evrensel Windows Platformu (UWP), Windows 10 için uygulama platformudur. Tek bir API kümesi, bir uygulama paketi ve tüm Windows 10 cihazlarına erişmek için bir depo için UWP uygulamaları geliştirebilirsiniz &ndash; PC, tablet, telefon, Xbox, HoloLens, Surface Hub ve daha fazla. UWP dokunma, fare ve klavye, oyun kumandası ya da bir kalem oluşmasından farklı ekran boyutları ve çeşitli etkileşim modelleri destekler. UWP uygulamaları özünde kullanıcıların deneyimlerini tüm cihazlarıyla mobil olmasını istediğiniz ve cihaz ne olursa olsun en kullanışlı veya üretken elinizdeki için kullanmak istediğiniz olur.

 ![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

Tercih ettiğiniz geliştirme dilinizi&mdash;C#, Visual Basic, C++ veya JavaScript&mdash;Windows 10 cihazları için bir evrensel Windows platformu uygulaması oluşturmak için. Visual Studio 2017 UWP uygulaması şablonu, tüm cihazlar için tek bir proje oluşturmanıza olanak tanır. her bir dilin sağlar. İş tamamlandığında, uygulama paketi üretmek ve uygulamanızı tüm Windows 10 cihazlarda müşterilere ulaşmak için Visual Studio içinden Microsoft Store için gönderin.

**15.5 yeni**: Visual Studio 2017 sürüm 15.5 Windows 10 Fall Creators Update SDK (10.0.16299.0) için en iyi destek sağlar. Windows 10 Fall Creators Update, UWP geliştiricileri için birçok iyileştirme de getirir. En önemli değişikliklerden bazıları şunlardır: 

* **.NET Standard 2.0 desteği**<br/>Kolaylaştırılmış uygulama dağıtımı ek olarak, Windows 10 Fall Creators Update .NET Standard 2.0 desteği sağlamak için Windows 10 'un ilk sürümdür. Etkili bir şekilde [.NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) herhangi bir .NET platform uygulayabilirsiniz temel sınıf kitaplığı başvurusu uygulamasıdır. .NET Standard'ın üzerinde çalışmak üzere seçtikleri herhangi bir .NET platform arasında kod paylaşmak, .NET geliştiricileri için mümkün olduğu kadar kolay hale getirmek için hedeftir.
* **En iyi hem UWP ve Win32**<br/>Windows 10 platformu ile geliştirildi [Masaüstü köprüsü](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) kendi geçerli odak UWP, WPF, Windows Forms veya Xamarin olup Windows 10 tüm .NET geliştiricileri için daha iyi hale getirmek için. Yeni Uygulama paketleme projesi türü ile Visual Studio 2017 sürüm 15.5 UWP projeleri için gibi WPF veya Windows Forms projeleri için Windows uygulama paketleri oluşturabilirsiniz. Uygulamanızı paketleme sonra tüm Windows 10 uygulamasını dağıtım avantajlarından yararlanın ve iş ve eğitim için Microsoft Store (tüketici uygulamaları için) veya Microsoft Store aracılığıyla dağıtma seçeneğine sahipsiniz. Paketlenmiş uygulamalar masaüstünde hem tam UWP API yüzeyi hem de Win32 API'ları erişime sahip olduğundan, WPF ve Windows Forms uygulamalarınızla kademeli olarak UWP API'lerine ve Windows 10 özellikleri artık modernleştirmelisiniz. Ayrıca, UWP uygulamalarınızda tüm Win32 özellikleriyle masaüstünde vurgulamasında Win32 bileşenlerinizi içerebilir.

UWP hakkında daha fazla bilgi için bkz: [Evrensel Windows Platformu (UWP) uygulamaları geliştirin](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) sayfası.

## <a name="mobile-app-development"></a>Mobil uygulama geliştirme

### <a name="xamarin"></a>Xamarin

".NET ile mobil uygulama geliştirme" iş yükünün parçası, geliştiriciler C#, .NET ve Visual Studio ile Xamarin kullanarak yerel Android, iOS ve Windows uygulamaları sunabilirsiniz. Geliştiriciler keyfini aynı verimlilik ve güç Xamarin ile Android, iOS ve Windows cihazlarda uzaktan hata ayıklama da dahil olmak üzere, mobil uygulamalar için çalışırken&mdash;yerel öğrenmek zorunda kalmadan Objective-C ya da Java gibi dillerin kodlama.

Daha fazla bilgi için [Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md) sayfası.

### <a name="entitlements-editor"></a>Yetkilendirmeler Düzenleyicisi

**15.3 yeni**: İOS geliştirme ihtiyaçlarınız için tek başına bir yetkilendirmeler Düzenleyicisi ekledik. Bu, kolayca gözatılabilir kolay bir kullanıcı Arabirimi içerir. Başlatmak için çift tıklayın, *entitlements.plist* dosya.

![Xamarin için yetkilendirme Düzenleyicisi](../ide/media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Xamarin için Visual Studio Araçları

**15.4 yeni**: Xamarin Live, geliştiricilerin doğrudan iOS ve Android cihazlarında uygulamaları üzerinde sürekli olarak dağıtım, test ve hata ayıklama işlemleri gerçekleştirmesine olanak tanır. Xamarin Live Player'ı indirdikten sonra&mdash;App Store veya Google Play'de kullanılabilir&mdash;Cihazınızı Visual Studio ile eşleştirebilir ve mobil uygulamaları derleme yönteminde çığır. Bu işlevsellik artık Visual Studio’ya eklenmiştir ve **Araçlar** > **Seçenekler** > **Xamarin** > **Diğer** > **Xamarin Live Player’ı Etkinleştir** seçeneği kullanılarak etkinleştirilebilir.

![Xamarin Live Player'da eşleştirme, dağıtım ve canlı düzenleme modlarına ilişkin animasyon](../ide/media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android öykünücüsü için destek

**Yeni 15,8**: Artık Hyper-V kullandığınızda, Hyper-V sunucusundaki Hyper-V sanal makineleri, Docker araçları, HoloLens öykünücü ve daha fazla gibi tabanlı diğer teknolojilerle Google Android öykünücüsü yan yana kullanabilirsiniz. (Bu özellik Windows gerektirir 10 Nisan 2018 güncelleştirmesi veya sonrası.)

![Hyper-V teknolojisi Google Android öykünücüsü](../ide/media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer Bölünmüş Görünüm Düzenleyicisi

Ayrıca **15,8 yeni**: Xamarin.Android için tasarımcı deneyiminde önemli geliştirmeler yaptık. Bir vurgulama oluşturabilir, düzenleyebilir ve aynı anda katmanlarınızı Önizleme olanak tanıyan yeni bir Bölünmüş Görünüm düzenleyicisidir.

![Xamarin.Adroid Designer Bölünmüş Görünüm Düzenleyicisi](../ide/media/android-designer-split-view.png)

Daha fazla bilgi için [emulator performansını için donanım hızlandırma](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**15.5 yeni**: Visual Studio App Center&mdash;, artık Android, iOS, macOS ve Windows uygulamaları için genel kullanıma sunulan&mdash;ihtiyacınız olan her şey otomatik derlemeler de dahil olmak üzere uygulamalarınızın yaşam döngüsünü yönetirken buluttaki gerçek cihazlarda test sahip Dağıtım beta test uzmanlarına ve uygulama mağazalarının ve kilitlenme ve analiz verileri gerçek kullanımını izleme. Objective-C, Swift, Java, C#, Xamarin ve React Native içinde yazılmış uygulamalar, tüm özellikleri arasında desteklenir.

  ![Visual Studio App Center test ortamı](../ide/media/app-center-test-env.png)

Daha fazla bilgi için [Introducing App Center: Oluşturun, test edin, dağıtın ve izleyin uygulamalarını bulutta](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) blog gönderisi.

## <a name="cross-platform-development"></a>Platformlar arası geliştirme

### <a name="redgate-data-tools"></a>Redgate veri araçları

DevOps özelliklerini SQL veritabanı geliştirmeye genişletmek amacıyla Redgate veri araçları artık Visual Studio'da kullanılabilir.

Visual Studio 2017 Enterprise ile şunları sunar:

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) veritabanı değişikliklerinin yanı sıra uygulama değişikliklerinin geçiş betikleri geliştirmenize, kaynak denetimini kullanarak veritabanı değişikliklerini yönetmenize ve SQL Server dağıtımlarını güvenli bir biçimde otomatikleştirmenize yardımcı olur.
* [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) yardımcı SQL kodu yazmanıza daha hızlı ve doğru bir şekilde yardımıyla akıllı kod tamamlama. SQL Prompt, veritabanı ve sistem nesnelerinin yanı sıra anahtar sözcükleri de otomatik olarak tamamlar ve yazdığınız sırada sütun önerileri sunar. Her bir sütun adı ve diğer adları hatırlamanız gerekmediğinden bu temizleyici kod ve daha az hatayla sonuçlanır.

Tüm Visual Studio 2017 sürümlerine dahil:

* [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) Hızlı Bul SQL parçalarını ve nesnelerini birden fazla veritabanında yardımcı olarak üretkenliğinizi artırır.

Daha fazla bilgi için bkz. [Redgate veri araçları, Visual Studio 2017'de](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) blog gönderisi.

### <a name="net-core"></a>.NET Core

.NET core, genel amaçlı, modüler, platformlar arası ve açık kaynak uygulaması .NET Standard ve .NET Framework ile aynı API'ler çoğunu içerir.

.NET Core platformu yönetilen derleyiciler, çalışma zamanı, taban sınıfı kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modelleri dahil birçok bileşenin yapılır. .NET core üç ana işletim sistemlerini destekler: Windows, Linux ve Macos'ta. .NET Core, cihaz, Bulut ve katıştırılmış IOT senaryoları kullanabilirsiniz.

Ayrıca, artık Docker desteği içerir.

**15.3 yeni**: Visual Studio 2017 sürüm 15.3, .NET Core 2.0 geliştirmeyi destekler. .NET Core 2.0 kullanarak, indirme ve .NET Core 2.0 SDK'yı ayrı olarak yüklenmesi gerektirir.

Daha fazla bilgi için [.NET Core Kılavuzu](/dotnet/core/index) sayfası.

## <a name="games-development"></a>Oyun Geliştirme

### <a name="visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları

"İçin Unity oyun geliştirme" iş yükünün parçası olarak, 2B ve 3B oyunlar ve etkileşimli içerik oluşturmak için platformlar arası geliştirmenize yardımcı olacak araçlar ekledik. Bir kez oluşturun ve için Visual Studio 2017 ve Unity 5.6 kullanarak tüm mobil platformlar, WebGL, Mac, PC ve Linux Masaüstü, web veya konsollar da dahil olmak üzere 21 platformda yayınlayın.

Daha fazla bilgi için [Unity için Visual Studio Araçları](../cross-platform/visual-studio-tools-for-unity.md) sayfası.

## <a name="ai-development"></a>Yapay ZEKA geliştirme

### <a name="visual-studio-tools-for-ai"></a>AI için Visual Studio Araçları

**15.5 yeni**: Bugün AI yeniliği hızlandırmaya yönelik Visual Studio üretkenlik özelliklerini kullanabilirsiniz. Söz dizimi vurgulama, IntelliSense ve metin otomatik biçimlendirme gibi kullanım yerleşik Kod Düzenleyicisi özellikleri. Etkileşimli olarak, ayrıntılı adım adım yerel değişkenleri ve modelleri üzerinde hata ayıklamayı kullanarak uygulama yerel ortamınızda öğrenme test edebilirsiniz.

  ![Derin öğrenme IDE](../ai/media/about/ide.png)

Daha fazla bilgi için [yapay ZEKA için Visual Studio Araçları](../ai/about-ai-tools.md) sayfası.

## <a name="whats-next"></a>Yenilikler

Visual Studio 2017 genellikle, geliştirme deneyimini daha da iyi hale getirebilir yeni özelliklerle güncelleştiriyoruz. Deneysel Önizleme aşamasında olan en önemli güncelleştirmeler bazılarını bir özeti aşağıda verilmiştir:

* **[Paylaşım canlı](https://visualstudio.microsoft.com/services/live-share/)**, bir kod temeli ve onun bağlamı arkadaşınızla paylaşın ve anlık yönlü işbirliği doğrudan Visual Studio'dan elde etmenize olanak tanıyan yeni bir aracı. Live Share ile bir teammate okuma gidin, düzenlemek ve onlarla paylaştıktan bir projede hata ayıklamak ve sorunsuz ve güvenli bir şekilde bunu.<br><br>Daha fazla bilgi için [Canlı Paylaşım SSS](/visualstudio/liveshare/faq).<br><br>
* **[Intellicode](https://visualstudio.microsoft.com/services/intellicode/)**, geliştiriciler kod desenleri ve ekip stili için catch zor kod sorunlarını bulmak için daha iyi bağlama duyarlı kod tamamlama, teslim etmek için yapay ZEKA kullanarak yazılım geliştirme geliştiren yeni bir özellik Kılavuzu , ve odağı kod incelemeleri açısından gerçekten önemli alana odaklanılmıştır. <br><br>Daha fazla bilgi için [Intellicode SSS](../ide/not-in-toc/intellicode-faq.md).

Daha fazla geliştirilme Visual Studio 2017 için ne hakkında olduğu edinmek ister misiniz? Bkz: [Visual Studio yol haritası](/visualstudio/productinfo/vs2018-roadmap) sayfası.

## <a name="contact-us"></a>Bizimle iletişim kurun

 Neden Visual Studio ekibine geri bildirim gönderilsin mi? Size müşteri geri bildirimi ciddiye olduğundan. Ne yapıyoruz çoğunu yürütür.

Nasıl size Visual Studio geliştirmek, veya ürün destek seçenekleri hakkında daha fazla bilgi ilgili öneride bulunmak istiyorsanız lütfen bkz [konuşmak bize](../ide/talk-to-us.md) sayfası.

### <a name="report-a-problem"></a>Sorun bildir

 Bazı durumlarda, bir ileti karşılaştığınız sorunun tam etkisini iletmek için yeterli değildir. Bir yanıt vermemesine, kilitlenme veya diğer performans sorunu yaşarsanız, kolayca yineleme adımları ve destekleyici dosyaları paylaşabilirsiniz (ekran görüntüleri, izleme ve yığın gibi düküm dosyalarında) kullanarak bizimle **sorun bildir** aracı. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [bir sorun bildirme](how-to-report-a-problem-with-visual-studio-2017.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 sürüm notları](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)
* [Visual C++ yenilikleri](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# Yenilikleri](/dotnet/csharp/whats-new)
* [Team Foundation Server için yenilikler nelerdir?](/tfs/server/whats-new?view=vsts)
* [Mac için Visual Studio'daki yenilikler](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019 yenilikler](whats-new-visual-studio-2019.md)
