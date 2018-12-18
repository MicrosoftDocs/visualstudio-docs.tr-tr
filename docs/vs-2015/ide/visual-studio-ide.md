---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6bd4e34e25add01de6e6e54c2439c2ca80ccf33
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062489"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 için kullanıcı Arabirimi tasarımı aracılığıyla planlama aşamasında den yazılım oluşturma, kodlama, test etme, hata ayıklama, kod kalitesini ve performansını analiz araçları, müşterileri ve kullanım telemetri toplama dağıtma paketidir. Bu araçlar, birlikte mümkün olan tüm Visual Studio tümleşik geliştirme ortamı (IDE üzerinden) sunulan olarak sorunsuz bir şekilde çalışmak üzere tasarlanmıştır.

Visual Studio, birçok türde uygulamalar, güç kurumlar ve veri merkezlerine büyük ve karmaşık sistemleri için basit mağazası uygulamaları ve mobil istemciler için oyunlar oluşturmak için kullanabilirsiniz. Oluşturabilirsiniz:

- Uygulama ve yalnızca Windows üzerinde çalışan oyunlar de Android ve iOS.

- ASP.NET, JQuery, AngularJS ve diğer popüler çerçeveleri dayalı Web siteleri ve web hizmetleri.

- Uygulamalar için Platform ve cihazlarda Azure, Office, Sharepoint, Hololens, Kinect ve nesnelerin interneti, yalnızca birkaç örnek adı için farklı.

- Oyunlar ve Xbox dahil olmak üzere, DirectX kullanarak Windows cihazları, çeşitli grafik kullanımı yoğun uygulamalar.

Varsayılan olarak Visual Studio için destek sağlar C#, C ve C++, JavaScript, F#ve Visual Basic. Visual Studio çalışır ve iyi Unity gibi üçüncü taraf uygulamaları ile tümleşir [Unity için Visual Studio Araçları](../cross-platform/visual-studio-tools-for-unity.md) uzantısı ve Apache Cordova aracılığıyla [ApacheCordovaiçinVisualStudioAraçları](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Visual Studio kendinize özel görevleri gerçekleştirmek özel araçlar oluşturarak genişletebilirsiniz.

Visual Studio'da daha önce hiç kullanmadıysanız, temel kavramları öğrenin bizim [alma başlatıldı geliştirmeyle Visual Studio](../ide/get-started-developing-with-visual-studio.md) öğreticiler ve Kılavuzlar.

Visual Studio 2015'te yeni özellikler hakkında bilgi edinmek, bkz: [Visual Studio 2015'teki yenilikler](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Visual Studio Kurulumu
 Visual Studio'nun hangi sürümünün size uygun olduğunu bulabilirsiniz [Visual Studio sürümleri](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Visual Studio 2015 buradan indirip yükleyebileceğiniz [Visual Studio indirmeleri](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Yükleme işlemi hakkında daha fazla bilgi edinmek istiyorsanız bkz [yükleme Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>IDE temelleri
 Aşağıdaki görüntüde bir Proje Aç ile Visual Studio IDE gösterir ve proje dosyaları içinde gezinmek için Çözüm Gezgini penceresinde ve gezinme kaynağı için Takım Gezgini penceresi denetim ve iş öğesi izleme. Anılmaktadır başlık çubuğunda özellikleri aşağıda daha ayrıntılı olarak açıklanmıştır.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Oturum açma
 Visual Studio'yu ilk kez başlattığınızda, Microsoft hesabınızı veya iş kullanarak oturum açın ya da Okul hesabı. İmzalı birden çok cihazda gibi pencere düzenlerini, ayarlarınızı eşitlemek ve Azure abonelikleri ve Visual Studio Team Services gibi gerekebilir hizmetleri otomatik olarak bağlamak sağlar. Abonelik tabanlı bir lisansınız varsa, lisans belirteci güncel kalması için düzenli olarak Visual Studio'ya oturum gerekecektir. Bir ürün anahtarı lisansınız varsa, oturum açmasına gerek yoktur, ancak bunu yaparsanız bu nedenle Visual Studio Team Services hesaplarınızı Azure veya Office 365, Salesforce.com ile bağlanmak daha kullanışlı kolaylaştırır. Daha fazla bilgi için [Visual Studio'da oturum açma](../ide/signing-in-to-visual-studio.md).

 Birden çok Visual Studio Team Services hesapları, Azure hesapları veya MSDN aboneliği varsa, tek bir oturum açma ile tüm hesaplarınızda bunları ve kaynak ve hizmetlere bağlayabilirsiniz. Daha fazla bilgi için [birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Güncel kalma
 Bildirim simgesine sağ üst kısmındaki başlık çubuğunda ne zaman Visual Studio için güncelleştirmeler kullanılabilir veya ilgili tüm bileşenlerin yüklü olduğunu söyler. Kapat veya bu bildirimlere işlem seçebilirsiniz. Daha fazla bilgi için [Visual Studio bildirimleri](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Öğeleri bulma ve Yardım alma
 [Hızlı başlatma](../ide/reference/quick-launch-environment-options-dialog-box.md) aşağıda gösterilen penceresi, Bul Visual Studio komutları, Araçlar, özellikler ve klavye kısayol ya da menü konumu bilmediğinizde benzeri hızlı bir yoludur. Aradığınız ne yazmanız yeterlidir ve Hızlı Başlat, bir bağlantı için size sunar.

 !['Yeni project' hızlı başlatma sonuçları](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN teknik belgeler için Microsoft web sitesi olur; MSDN bu sayfada şu anda okumakta olduğunuz! Visual Studio'da basabilirsiniz **F1** etkin pencere MSDN yardım sayfasına gidin. Tuşlarına da basabilirsiniz **F1** Kod düzenleyicisinde API veya anahtar sözcüğü geçerli giriş işareti konumunda MSDN yardım sayfasına gidin. Örneğin, bir C# dosyasında yere olarak veya yalnızca sonunda yer işaretini yerleştirin bir `System.String` bildirimi ve ENTER tuşuna **F1** MSDN yardım sayfasına gitmek için <xref:System.String>.

### <a name="giving-feedback"></a>Geri bildirim
 Dilediğiniz zaman bize geri bildirim Visual Studio sağlamak kolay bir işlemdir. Başlık çubuğundaki geri bildirim simgesini tıklayın **hızlı başlatma** ve ardından **sorun bildir** veya **bir öneride**. Visual Studio'nun yayın öncesi sürümlerinde de bir **bu ürünü değerlendirin** seçeneği. Bu açıklamalar arayın ve bunları ürünü iyileştirmek için kullanırız. Daha fazla bilgi için [konuşmak bize](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>IDE’yi kişiselleştirme
 Pencere düzenini geliştirme stilinize uyacak şekilde özelleştirebilirsiniz. Yerleştirme, float veya herhangi bir zamanda herhangi bir pencereyi gizle ve düzenleyici tam ekran modunda da çalıştırabilirsiniz. Oluşturun ve yalnızca belirli bağlamlarda için gereksinim duyduğunuz pencerelerini Göster birden çok özel pencere düzenlerini kaydedin. Örneğin, Kod düzenleyicisinde gördüğünüz tüm böylece bir tam ekran düzeni oluşturabilirsiniz. Ve hata ayıklama ve ekip işlemleri alan farklı düzenler oluşturabilirsiniz. Daha fazla bilgi için [pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

 Visual Studio'yu diğer birçok şekilde özelleştirin ve zorlanmazsa ayarlarınızı birden fazla makinede çalışır. Daha fazla bilgi için bkz. [IDE’yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

 Neredeyse her şey için klavye kısayolları vardır ve de özelleştirebilirsiniz. Yeni kısayol oluşturmak için hızlı klavye iletişim kutusunu açmak için Başlat "Klavye" yazın. Burada, seçenekleri hakkında daha fazla bilgiye ihtiyacınız varsa, MSDN yardım sayfasına gitmek için F1 tuşuna basabilirsiniz. Daha fazla bilgi için [Visual Studio'daki klavye kısayollarını varsayılan](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Visual Studio Team Services ve Team Foundation Server'a bağlanma
 Visual Studio Team Services (VSTS) barındırma yazılım projeler ve takımlar etkinleştirme işbirliği için bulut tabanlı bir hizmettir. VSTS, Scrum ve CMMI Çevik Geliştirme yöntemleri yanı sıra, hem Git hem de Team Foundation kaynak denetimi sistemlerini destekler. Team Foundation sürüm denetimi (TFVC) izlemek için bir tek, merkezi sunucu deposu ve sürüm dosyalarını kullanır. Yerel değişiklikler her zaman diğer geliştiricilerin son değişiklikleri nereden merkez sunucuya iade edilir. Team Foundation Server (TFS) 2015, Visual Studio uygulama yaşam döngüsü yönetimi hub ' dir. Tek bir çözüm kullanarak katılmak için geliştirme işlemine dahil olan herkes sağlar. TFS, heterojen takımlara ve projelere, çok yönetimi için avantajlıdır.

 Ağınızda bir Team Foundation Server veya Visual Studio Team Services hesabı varsa, için Takım Gezgini penceresi bağlanın. Bu pencereden içine veya dışına kaynak denetimi kodunu kontrol edin, çalışma öğelerini yönetmek, derlemeler ve erişim takım odaları ve çalışma alanları başlatın. Takım Gezgini'nden açabileceğiniz **hızlı başlatma** veya ana menüden **görünümü &#124; Takım Gezgini** veya **takım &#124; bağlantıları Yönet**.  Visual Studio Team Services hakkında daha fazla bilgi için bkz. [www.visualstudio.com](https://www.visualstudio.com/). Team Foundation Server hakkında daha fazla bilgi için bkz. [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Aşağıdaki görüntüde, VSTS'de barındırılan bir çözüm için Takım Gezgini bölmesinde gösterilmektedir:

 ![Visual Studio Takım Gezgini](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Çözümler ve projeler oluşturma
 Tek bir kod dosyalara göz atmak için Visual Studio kullanmanız mümkün olmakla birlikte, daha sık, çalışacaksınız bir *proje*. Visual Studio projesi, dosyalar ve uygulamalar (örneğin, bir .exe, DLL veya appx) için tek bir ikili yürütülebilir dosyasına derlenir kaynakları koleksiyonudur. Olmayan ASP.NET Web siteleri için herhangi bir yürütülebilir dosya oluşturulur ve projeyi görüntüler ve yalnızca HTML, JavaScript dosyaları içerir. Bazen birden çok ikili dosyaları veya yakından ilgili Web siteleri oluşturmanız gerekebilir, Visual Studio çözüm, birden çok proje veya Web siteleri içerebilir kavramını sahip olacaktır. Bir proje oluşturduğunuzda, aslında bir proje içinde-çözüm oluşturuyorsanız ve gerekirse daha fazla projeler bu çözüme daha sonra ekleyebilirsiniz. Örneğin, bir DLL projesi varsa, .exe projesinde yükleyen ve DLL kullanan bir çözüme ekleyebilirsiniz.

 A *proje şablonu* aldığınız yapılandırma ayarlarını hızlı bir şekilde ayarlamak uygulamanın belirli bir tür oluşturmak için ve önceden doldurulmuş kodu dosyalarının bir koleksiyondur. Visual Studio aralarından seçim yapabileceğiniz birçok proje şablonları bulunur ve varsayılan şablonlarından hiçbiri işinize yaramazsa kendi oluşturabilirsiniz. Bir şablonla bir projesi oluşturduktan sonra sağlanan dosyaları veya eklediğiniz yeni dosyalar da, kendi kod yazmaya başlayabilirsiniz. Daha fazla bilgi için [çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md). ASP.NET uygulamaları için kullanılabilir proje şablonları ile yeni proje iletişim aşağıda gösterilmiştir.

 ![Visual Studio'da yeni proje iletişim](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Kullanıcı arabirimi tasarlama
 Bir tasarımcı, bir kullanıcı arabirimi, kod yazmaya gerek kalmadan oluşturmanıza olanak sağlayan sezgisel bir araçtır. Düğmelerden liste kutuları ve takvim gibi kullanıcı Arabirimi denetimleri sürükleyebilirsiniz [araç kutusu](../ide/reference/toolbox.md) penceresi bir tasarım yüzeyine pencerede veya iletişim kutusunu temsil eder. Yeniden boyutlandırma ve herhangi bir kod yazmadan öğelerini yeniden düzenleyebilir. Tasarımcılar, bir kullanıcı arabirimi olan herhangi bir proje türü için dahil edilir.

 Projenizin bir XAML tabanlı kullanıcı arabirimi varsa varsayılan Tasarımcısı, Visual Studio ile sorunsuz çalışır bir Gelişmiş grafik aracı olan Visual Studio için Blend olur.

 ![Çalışma yüzeyine](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Tasarım görünümü** belgenizin görsel tasarımını görüntüler. Bu görünümde, çizime veya tasarım yüzeyinde nesneleri değiştirebilirsiniz.|
|![](../designers/media/b1-2.png "B1_2")|**İçerik haritası** şablon düzenleme modu, stil düzenleme modu ve nesne düzenleme arasında hızlıca taşımak için seçilen bir nesne kapsam.|
|![](../designers/media/b1-3.png "B1_3")|**Yakınlaştırma** tasarım yüzeyinde nesneleri ve tasarım yüzeyini yakınlaştırmak için kullanın.|
|![](../designers/media/b1-4.png "B1_4")|**Tasarım yüzeyi denetimleri** bu denetimleri kullanın (**Show kılavuza**, **çizgilerine ya** ve **dayama çizgilerine yaslamayı açma veya kapatma**) yaslama seçenekleri ayarlamak için. Yaslamayı birbiriyle en fazla veya eşit aralıklı satırları tasarım yüzeyinde nesneleri hizalama için kullanışlıdır.|
|![](../designers/media/b1-5.png "B1_5")|**Kod Düzenleyicisi** XAML, C#, C++ veya Visual Basic kodunu el ile Kod düzenleyicisinde düzenleyin.|

 Daha fazla bilgi için [Visual Studio ve Visual Studio için Blend, XAML tasarlama](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Gezinme, yazma ve kod anlama
 Geliştirici misiniz, düzenleyici penceresinde zamanınızın çoğunu burada büyük olasılıkla geçirir olur. Visual Studio için düzenleyicileri içerir C#, C++, Visual Basic, JavaScript, XML, HTML, CSS ve F#, üçüncü taraflar için birçok başka dile eklenti Düzenleyicileri (ve derleyiciler) sunar.

 Tıklayarak tek tek dosyaları metin düzenleyicide düzenleyebilirsiniz **dosya &#124; açık &#124; dosya.** Açık bir proje dosyalarını düzenlemek için Çözüm Gezgini'ndeki dosya adını tıklayın. Kod renklendirilmiş ve Hızlı Başlat "Renk" yazarak renk düzenini kişiselleştirebilirsiniz. Aynı anda çok fazla metin düzenleyicisi sekmeli penceresi açık olabilir. Her pencere bağımsız olarak bölebilirsiniz. Metin Düzenleyici tam ekran modunda da çalıştırabilirsiniz.

 ![Kod düzenleyicisinde GreetingsConsoleApp.cpp](../ide/media/c-ide-editorlinenumberswordwrapon.png "C ++ IDE_EditorLineNumbersWordWrapOn")

 Metin düzenleyici, yüksek oranda (olmasını istiyorsanız) ile birçok üretkenlik yardımcı daha iyi daha hızlı kod yazmanızı etkileşimlidir. Dile göre farklı özellikler ve özelliklerini aç veya kapat için bunlardan (türü "Düzenleyicisinde" Hızlı Başlat) herhangi birini kullanmak zorunda değilsiniz: ortak üretkenlik özelliklerinden bazıları şunlardır:

1. [Yeniden düzenleme](../ide/refactoring-in-visual-studio.md) akıllı değişkenler taşıma, yeniden adlandırma kod satırlarını başka konumlara, redordering işlev parametrelerini ve daha fazla kod taşıma ayrı bir işleve seçildi. gibi işlemleri içerir.

2. *IntelliSense* bir genel bir doğrudan düzenleyicide kod türü bilgilerini görüntülemek ve bazı durumlarda, küçük kod parçalarını sizin için yazma popüler özellik kümesi için bir terimdir. Bu temel belgeleri satır içi ayrı Yardım penceresinde tür bilgileri aramak zorunda kalmaktan kurtarır düzenleyicisinde gibidir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic'e özel IntelliSense ](../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, iş yerinde bazı IntelliSense özelliklerini gösterir:

    ![Visual Studio üye listesi](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Dalgalı çizgiler** yazarken, hatalar veya gerçek zamanlı kodunuzdaki olası sorunlar için uyarı sağlayan hemen beklemenize gerek kalmadan çalıştırın veya derleme zamanı sırasında bulunmak hatayı düzeltmek. Dalgalı çizgi gelin, hatayla ilgili ek bilgileri görürsünüz. Bir ampul, önerileri nasıl hatayı düzeltmek sol kenar boşluğunda de görünebilir. Daha fazla bilgi için [ampullerle hızlı eylemler gerçekleştirme](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Ampul fare vurgulama ile](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Yer işaretleri](../ide/setting-bookmarks-in-code.md) etkin olarak üzerinde çalıştığınız dosyaları belirli satırları hızla gitmek sağlar.

5. [Çağrı hiyerarşisi](../ide/reference/call-hierarchy.md) penceresi çağırın ve göre adlandırılır yöntemleri göstermek için metin düzenleyici bağlam menüsünde çağrılacak ve giriş işaretindeki yöntemi.

6. **Code lens** ve değiştirir, kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testleri, düzenleyiciden çıkmadan tüm başvuruları Bul olanak sağlar. Daha fazla bilgi için [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).

7. **Özet tanım için** penceresi, geçerli Bağlamınızı uzağa gitmeden bir yöntem veya tür tanımı satır içi gösterir. Bu pencereyi şimdi XAML için çok çalışır.

8. **Tanıma** bağlam menüsü seçeneği, doğrudan bir işlevin veya nesnenin tanımlandığı yer alır. Başka gezinme komutları da Düzenleyicisi'nde sağ tıklayarak kullanılabilir.

9. İlgili bir aracı [Nesne Tarayıcısı](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)içeren görmek için .NET veya Windows çalışma zamanı derlemeleri sisteminize incelemek için türleri bunlar etkinleştirir ve yöntemleri ve özellikleri bu türler bulunur.

     ![Nesneyi gösteren Nesne Tarayıcısı](../ide/media/objectbrowser.png "ObjectBrowser")

   Düzen menüsü ve Görünüm menüsü öğelerin çoğu Kod Düzenleyicisi'nde şekilde ilgilidir. Düzenleyici hakkında daha fazla bilgi için bkz: [kod yazma](../ide/writing-code-in-the-code-and-text-editor.md) ve [kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Derleme ve kod oluşturma

Bir proje oluşturmak için kaynak kodu derleyin ve yürütülebilir dosyayı oluşturmak için gerekli tüm adımları gerçekleştirmek anlamına gelir. Farklı dillerde farklı bir derleme işlem var ve normal Web siteleri hiçbir derleme yok. Proje türü ne olursa olsun, da yapı menüsündeki şu komutları standart konumudur. Derleme ve tek bir tuş vuruşu ile kodunuzu çalıştırmak için F5 tuşuna basın. Her derleyici IDE ile tamamen yapılandırılabilirdir. Derleme araç mı programınızda, simgeler ve kesme noktaları ve tek hata ayıklayıcı veya bir yayın yapısı Adımlama, ne, sonuçta müşterilere sağlayacak olan desteklemek üzere etkinleştirilmiş ek hata denetimi ile hata ayıklama sürümünü oluşturmak belirtmenize olanak sağlar. Bir proje özelliği sayfasında daha fazla derleme ve diğer birçok ayarlarını yapılandırabilirsiniz. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve Özellikler'i seçin. Bu gibi durumlarda, yapılar da komut satırından çalıştırabilirsiniz.

Bir hata veya başarılı iletileri de dahil olmak üzere, yapı çıktısını görünür **çıkış** penceresi. **Hata listesi** derleme hataları hakkında ayrıntılı bilgileri gösterir.

## <a name="debugging-your-code"></a>Kodunuzun hatalarını ayıklama
 Visual Studio'nun durumu resim hata ayıklayıcı yerel projenizde, Android veya Windows Phone yönelik olanlar gibi bir öykünücü veya uzak bir cihazda çalışan kodda hata ayıklamak sağlar. Aynı anda bir deyim kod adım adım ve belirtilen bir koşul true olduğunda, yalnızca isabet kesme noktalarını ayarlayabilir, Git ve çok iş parçacıklı uygulamalar aracılığıyla geçebilirsiniz gibi değişkenleri denetleyin. Kodunuzun bağlamı bırakmak zorunda kalmazsınız tüm kod düzenleyicisinde kendisini yapılandırılabilir.

 ![Kesme noktası ayarları gözlem penceresi](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Hata ayıklayıcı kendisini görüntülemek ve yerel değişkenler, çağrı yığını ve diğer yönleri çalışma zamanı ortamı sağlayan birden çok windows sahiptir. Bu windows bulabilirsiniz **hata ayıklama** menüsü.

 [Komut penceresi](../ide/reference/immediate-window.md) bir ifade yazın ve sonucu hemen görmenize olanak sağlar.

 [IntelliTrace](http://msdn.microsoft.com/en-us/629e9660-c59a-446b-8c30-290059158f61) penceresi her yöntem çağrısının kaydeder ve bir çalışan .NET programı ve diğer olayları bir sorun kaynaklandığı hızla bulmanıza yardımcı olmak.

 Daha fazla bilgi için [Visual Studio'da hata ayıklama](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Kodunuzu test etme
 Visual Studio birim testi çerçevesi için yönetilen kodu (.NET) ve bir yerel C++ içerir. Testleri, birim oluşturmak için testlerinizi yazın ve ardından bunları Test Gezgini penceresinden çalıştırın sadece bir Test projesi çözümünüze ekleyin. Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md).

 ![Birim Test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Kod kalitesini ve performansını analiz etme
 Visual Studio statik ve çalışma zamanı analizi için güçlü araçlar içerir. Statik analiz araçları tasarımı, Genelleştirme, birlikte çalışabilirlik, performans, güvenlik ve diğer kategorilerden olası hataları belirlemenize yardımcı olur. Performans testi veya profil oluşturma, ölçme, programınızın nasıl çalıştığını içerir. Bu araçlardan erişim **Çözümle** menüsü. Daha fazla bilgi için [Visual Studio tanılama araçları ile kaliteyi geliştirme](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Bulut hizmetlerine ve veritabanlarına bağlanma
 [Sunucu Gezgini](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) Visual Studio'daki tüm hesapları kişiselleştirme hesabınız kapsamında (bir oturum ile), Azure, Salesforce.com, Office 365 gibi SQL Server örnekleri dahil olmak üzere yönetilen kaynaklar gösterilir ve Web siteleri.

 ![Sunucu Gezgini](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio içerir [Microsoft SQL Server veri Araçları](https://msdn.microsoft.com/data/tools.aspx) (SSDT), derleme, hata ayıklama, korumak ve veritabanlarını yeniden düzenleme olanak tanır. Bir veritabanı projesiyle veya doğrudan ile bir bağlı veritabanı örneği veya kapalı-şirket içinde çalışabilir.

 Visual Studio'da SQL Server Nesne Gezgini veritabanı nesnelerini SQL Server Management Studio'ya benzer bir görünümünü sunar. SQL Server Nesne Gezgini tablo verilerini düzenleme, Şema karşılaştırma ve doğru SQL Server Nesne Gezgini bağlam menülerini kullanarak sorgular yürütme light vergileri veritabanı yönetimi ve tasarım işler yapmasını sağlar. SSDT, ayrıca özel proje türleri ve SQL Server 2012 Analysis Services ve Reporting Services (önceki adıyla Business Intelligence Development Studio da bilinir) tümleştirme hizmetlerini iş zekası (BI) çözüm geliştirmeye yönelik araçlar içerir.

 ![SQL Server Nesne Gezgini](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma
 Uygulamanızı müşterilere dağıtmaya hazır olduğunda, Visual Studio için Windows Store, bir SharePoint sitesine veya InstallShield veya Windows Installer teknolojileriyle dağıtıyorsanız olup olmadığını, bunu yapmak için araçlar sağlar. Bu, tüm IDE erişilebilir. Daha fazla bilgi için [uygulamaları dağıtma, hizmetleri ve bileşenleri](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Mimari ve Modelleme Araçları (yalnızca Kurumsal)
 Tasarım ve uygulama modeli için Visual Studio mimari ve Modelleme Araçları'nı kullanabilirsiniz. Bu araçlar, kodun yapısını, davranış ve ilişkileri görselleştirmek için yardımcı olur. Geliştirme sürecinizin bir parçası olarak farklı uygulama yaşam döngüsü boyunca ayrıntı düzeylerinde modeller oluşturabilirsiniz. Gereksinimler, görevler, test çalışmalarını, hataları ve Team Foundation Server çalışma öğeleri ve geliştirme planınızı model öğelerini bağlantılandırarak Modellerinizi ile ilişkili diğer iş izleyebilirsiniz. Daha fazla bilgi için [tasarım ve uygulama modeli](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Visual Studio SDK ile Visual Studio'yu genişletme
 Visual Studio genişletilebilir bir platformdur. Visual Studio IDE ile tümleşen bir özel aracı uzantısıdır. Üçüncü taraf uzantıları ekleyin veya kendinizinkini oluşturun. Daha fazla bilgi için [Visual Studio uzantılarını geliştirme](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) temel bir başvuru herkes için yazma için Visual Studio uzantılarıdır. Yeni özelliğinizi olmanızı sağlayacak diğer etkileşim desenleri Visual Studio ile sorunsuz şekilde tümleştirin ve bu platforma özgü yönergeleri iletişim tasarımı, yazı tiplerini, renkleri, simgeler, ortak denetimleri hakkında bilgi içerir.

## <a name="in-this-guide"></a>Bu kılavuzda

|||
|-|-|
|[Kullanıcı Hesapları ve Güncelleştirmeler](../ide/user-accounts-and-updates.md)|[IDE’yi Kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)|
|[Nasıl Yapılır: IDE'de Gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Visual Studio ile Geliştirmeye Başlama](../ide/get-started-developing-with-visual-studio.md)|
|[Visual Studio Uzantıları’nı bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)|[Çözümler ve Projeler](../ide/solutions-and-projects-in-visual-studio.md)|
|[Kod Yazma](../ide/writing-code-in-the-code-and-text-editor.md)|[Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)|
|[Profil Araçları](../profiling/profiling-tools.md)|[Kod Kalitesini Geliştirme](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Kullanıcı Arabirimleri Tasarlama](../designers/designing-user-interfaces.md)|[Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)|
|[Derleme ve Oluşturma](../ide/compiling-and-building-in-visual-studio.md)|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](../deployment/deploying-applications-services-and-components.md)|
|[Visual Studio IDE 64 Bit Desteği](../ide/visual-studio-ide-64-bit-support.md)|[Güvenlik](../ide/security-in-visual-studio.md)|
|[Visual Studio Örnekleri](../ide/visual-studio-samples.md)|[Microsoft Yardım Görüntüleyicisi](../ide/microsoft-help-viewer.md)|
|[Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)|[Kullanıcı Arabirimi başvurusu](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio 2015'i yükleme](../install/install-visual-studio-2015.md)
- [Kodunuzu düzenleme](https://www.visualstudio.com/features/ide-vs)
- [Visual Studio 2015’teki Yenilikler](../what-s-new-in-visual-studio-2015.md)
- [Visual Studio Projelerini Taşıma, Geçirme ve Yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Bizimle İletişime Geçin](../ide/talk-to-us.md)