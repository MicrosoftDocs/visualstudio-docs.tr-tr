---
title: Visual Studio 2015'teki yenilikler | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1d2b37a988f0078149228cce808397f9fb915d1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062444"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Hangi&#39;Visual Studio 2015'te yeni s
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Visual Studio 2015, tümleşik bir geliştirici üretkenliği araçları, bulut Hizmetleri ve size ve ekibinize harika uygulamalar ve web için Windows Store, masaüstü, Android ve iOS için oyunlar oluşturmaya olanak tanıyan uzantılar paketidir Hoş Geldiniz.

Bu sayfada Visual Studio 2013'ün ilk olarak sunulan özelliklerini Visual Studio 2013 güncelleştirmelerden biri dahil olmak üzere RTM,'den beri yenidir en önemli özelliklerinden bazıları vurgular. Visual Studio 2015'te Yenilikler tam listesi için bkz. [sürüm notları](https://www.visualstudio.com/news/vs2015-vs).

Birçok geliştirme ve Visual Studio ALM yeni özellikler hakkında daha fazla bilgi için bkz: [TFS 2015 için Yenilikler](/tfs/server/whats-new?view=vsts#tfs-2015-rtm).

## <a name="a-new-setup-experience"></a>Yeni bir kurulum deneyimi
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Yalnızca gereksinim duyduğunuz bölümleri'ni yüklemeniz gerekir, böylece Visual Studio 2015 kurulum deneyimini bileşenlerden. Bu yükleme .NET ya da Web geliştirme ile ilgili birçok yaygın senaryo için daha hızlı hale getirir. Geliştirme, platformlar arası mobil geliştirme gibi diğer tür yapın veya C++'da iş veya F#, seçin **özel** Yükleme bileşenleri ve ihtiyacınız olan isteğe bağlı üçüncü taraf SDK'yı seçin. Ayrıca özel bileşenleri daha sonra yükleyebilirsiniz. Örneğin, temel Yükleme'yi seçin ve ardından yeni bir C++ projesi oluşturma girişimi, C++ geliştirme araçlarını indirin istenir.

 ![Visual Studio 2015 Kurulum iletişim](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Birden fazla hesabında oturum açın
 Visual Studio 2015 ile yeni kolaylaştırılmış oturum açma deneyimi, birden fazla Visual Studio hesabı olsa bile, çevrimiçi kaynaklara erişiminizi önemli ölçüde kolaylaştırmak için tasarlanmıştır. Visual Studio'ya oturum sonra otomatik olarak Visual Studio 2015 ve Blend tüm örnekleri için makinenizde oturum açtınız. Otomatik olarak oturum açarken ayarlarınızı, dolaşım başlatır. Visual Studio 2015'te hesabınızı özellikleri arasında paylaşılan iyi bir belirteç olduğu sürece, bu nedenle, Visual Studio Team Services hesaplarınızı erişebilirsiniz **Takım Gezgini**, Microsoft Azure Web sitelerinden ve kaynakların Sunucu Gezgini'nde abonelik. Azure kaynaklarınızı yeni proje iletişim kutusunda Application Insights projeleri için de görürsünüz ve Azure depolama, Azure mobil görürsünüz [Microsoft Office 365](http://msdn.microsoft.com/office/aa905340.aspx) ve [Saleforce.com Geliştirici](https://developer.salesforce.com/) Yeni hesapları **bir bağlı hizmet eklemek** iletişim.

 Kullandıkça ekleyerek bunları veya yeni hesap Yöneticisi aracılığıyla Visual Studio'da birden fazla kullanıcı hesaplarıyla çalışabilir. Ardından, bağlanma Hizmetleri çalıştırıldığında anında veya çevrimiçi kaynaklara erişen hesaplar arasında geçiş yapabilirsiniz. Visual Studio, Visual Studio veya Blend herhangi bir örneğinden kullanabilmesi için eklediğiniz hesaplara hatırlar. (Biz değerli kimlik bilgilerinizi götürülmeyeceğini rağmen) hızlı bir şekilde başka bir cihazda bu hesapların biriyle çalışmaya başlayabilir için visual Studio da hesaplarının listesi, kişiselleştirme hesabınızla dolaşır. Elbette, hesap ayarları iletişim kutusundan hesapları dilediğiniz zaman kaldırabilirsiniz. Başlamak için bkz: [birden çok kullanıcı hesabıyla çalışma](./ide/work-with-multiple-user-accounts.md).

 ![Hesap Yöneticisi](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Hedef platformları seçin
 Visual Studio 2015, platformlar arası mobil cihaz için geliştirmeyi destekler. Uygulamalar ve iOS, Android ve Windows platformlarını ve bir ortak kod Visual Studio IDE içinden temeli, tüm gelen paylaşan oyunlar yazabilirsiniz. Tüm bu yeni proje türleri dosyasında, yeni proje iletişim kutusu görürsünüz.

 Ve — Elbette — geliştirmeleri dilleri, kitaplıklar ve araçlar için çok sayıda ile hiç olmadığı kadar daha iyi Klasik Masaüstü uygulamaları için destek.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>C# ile Visual Studio için Xamarin platformlar arası mobil uygulamalar
 Xamarin iOS için yerel olarak bağlayan #c ve Android API'leri kod yazmanızı sağlayan Mobil bir çerçevedir. Microsoft, kendi paylaşılan kod ile tek bir çözümde, Android, iOS ve Windows Phone için geliştirin olanak tanıyan uzantı Visual Studio için Xamarin sürümü üzerinde Xamarin ile yakından kurdu. Xamarin ile bir dil ve bir kod tabanı ile platformlar arasında çok az deltaları kullanacaksınız.  Visual Studio için Xamarin, Visual Studio 2010 ve sonraki sürümlerde desteklenir. Xamarin başlangıç sürümü Visual Studio 2015'te eklenmiştir. Başlamak için bkz: [Visual Studio'daki Xamarin yerel UI ile uygulamalar oluşturun](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Apache Cordova ile HTML/JavaScript içinde platformlar arası mobil uygulamalar
 Apache Cordova için Visual Studio Araçları Microsoft ve açık kaynaklı Apache Cordova topluluk arasında Kapat işbirliği sonucudur. HTML, CSS ve JavaScript (veya Typescript) kullanarak platformlar arası Mobil Geliştirme Araçları'nı etkinleştirin. Android, iOS ve Windows ile tek bir kod tabanının hedef ve JavaScript IntelliSense, DOM Gezgini, JavaScript konsolu, kesme noktaları, Gözcü, yerel öğeler, yalnızca kendi kodum ve daha da dahil olmak üzere Visual Studio IDE zenginliğine keyfini çıkarın.  Apache Cordova için Visual Studio Araçları ile uygulamalarınızı tüm platformlarda ortak bir JavaScript API'si eklentileri üzerinden yerel cihaz özelliklerine erişimine olanak sahip. Başlamak için bkz: [Apache Cordova için Visual Studio Araçları ile çalışmaya başlama](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Unity ile C# platformlar arası mobil oyunlar
 Unity çok platformlu 2B ve 3B Oyun Geliştirme için yaygın olarak kullanılan bir platformdur. Oyununuzu C# dilinde yazabilir ve BT yerel Android, iOS, Windows Phone ve diğer birçok platformda. Unity için Visual Studio Araçları Unity Visual Studio IDE ile tümleşen bir uzantısıdır. Bu uzantı, Visual Studio IDE ve hata ayıklayıcı, Unity geliştiricileri için tasarlanmış üretkenliği özelliklerine ek olarak tüm özelliklerini alın. Unity 2.0 Preview 2 ekler visual Studio Araçları Visual Studio 2015 için ek olarak yeni özellikler, Yereller ve izleme nesneleri için daha iyi görselleştirme gibi çeşitli windows desteği. Microsoft, Unity için Visual Studio Araçları'nın en son geliştiren SyntaxTree şirketini aldı. Unity 2.0 Preview 2 ve Unity için Visual Studio Araçları hakkında daha fazla bilgi için Visual Studio Araçları indirmek için bkz [Unity 2.0 için Visual Studio Araçları](http://Aka.ms/vstu).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Platformlar arası uygulamalar ve yerel C++ kitaplıkları
 C++ kullanılabilir yerel olarak çoğu mobil cihazlarda dildir. Birden çok mobil platform hedefleri için yapılandırılabilecek platformlar arası paylaşılan kod kitaplıkları yazmak için kullanabilirsiniz. C++'ta bile tüm mobil uygulamalar oluşturabilirsiniz. Visual C++ düzenlemek, oluşturmak, dağıtmak ve platformlar arası kod hata ayıklama için Araçlar verir. Windows uygulamaları için şablonlara ek olarak, Android yerel etkinlik uygulamaları, iOS uygulamalarını veya Xamarin karma uygulamaları içeren birden çok platform için paylaşılan kod kitaplık projeleri için şablonlardan projeler oluşturabilirsiniz. Platforma özel IntelliSense'i API'leri keşfetmek ve Android, iOS veya Windows hedefleri için doğru kodu oluşturmasını sağlar. Yapınızı x86 veya ARM yerel platformları için yapılandırın ve kodunuzu iOS simülatörü veya doğrudan bağlı Android cihazlarında, ağa bağlı bir Mac üzerinde iOS cihazlarına dağıtmak veya test etmek için Microsoft Visual Studio öykünücü yüksek performanslı Android için kullanın. Kesme noktaları ayarlayın, değişkenleri izleyin, yığını görüntüleyin ve Visual Studio hata ayıklayıcının C++ kodunda adım adım. Birden fazla uygulama platformunda tüm platforma özgü kod paylaşın ve bunlar için tüm bir çözümü Visual Studio ile derleme.

 Platformlar arası C++ kullanmaya başlamak için bkz: [Visual C++ ile platformlar arası mobil uygulamalar oluşturun](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Tüm Windows 10 cihazlar için evrensel Windows uygulamaları
 Evrensel Windows platformu ve bizim bir Windows çekirdek ile aynı uygulama tüm Windows 10 cihazlarda phone'lardan masaüstlerine çalıştırabilirsiniz. Visual Studio 2015 ile Evrensel Windows uygulaması geliştirme araçları bu evrensel Windows uygulamaları oluşturun.

 ![Evrensel Windows platformu](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uygulamanızı Windows 10 telefonda, Windows 10 Masaüstü veya Xbox üzerinde çalıştırın. Bu, aynı uygulama paketi kullanılır! Windows 10 tek, birleştirilmiş çekirdek sunulmasıyla birlikte, tüm platformlardaki bir uygulama paketini çalıştırabilecek. Çeşitli platformları platform belirli davranışlardan faydalanmak için uygulamanızı ekleyebileceğiniz olan uzantı Sdk'lerine vardır. Örneğin, mobil cihazlar için bir uzantı SDK'sı, Windows phone'da basıldığında geri düğmesini işler. Projenizde bir uzantı SDK'sına başvuran, yalnızca, SDK bu platform üzerinde kullanılabilir olup olmadığını test etmek için çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketi nasıl sahip olmasıdır!

 Bunlar oluşturmak için C#, Visual Basic, C++ veya JavaScript kullanın [Evrensel Windows uygulamaları](http://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>Web
 ASP.NET 5 önemli bir güncelleştirme için MVC, Webapı ve SignalR ve Windows, Mac ve Linux üzerinde çalıştırır.  ASP.NET 5 baştan ayarlama, yalın ve birleştirilebilir bir .NET ile modern bulut tabanlı uygulamalar oluşturmak için yığın sağlamak için tasarlanmıştır. Visual Studio 2015 araçları daha yakından Bower ve Grunt gibi popüler web geliştirme araçları ile tümleşiktir. Başlamak için üzerinde çok sayıda blog gönderilerini görün [NET Web geliştirme ve Araçlar Blogumuza](http://blogs.msdn.com/b/webdev/).

### <a name="classic-desktop-and-windows-store"></a>Klasik Masaüstü ve Windows Store
 Visual Studio 2015, Klasik Masaüstü ve Windows Store geliştirme desteklemeye devam eder. Windows geliştikçe ile birlikte Visual Studio evrilir.  Visual Studio 2015'te kitaplıkları ve diller C++ yanı sıra .NET için tüm Windows sürümleri için geçerli olan önemli geliştirmeleri yapıldı.

#### <a name="the-net-framework"></a>.NET Framework
 Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] hakkında yeni 150 API'ler ve 50 güncelleştirilmiş daha fazla senaryoları etkinleştirmek için API'ler sunar. Örneğin, koleksiyonlar hemen uygulayın <xref:System.Collections.Generic.IReadOnlyCollection%601> bunları kullanmayı daha kolay hale getirir. Ayrıca, ASP.NET 5, daha önce bahsedilen modern bulut tabanlı uygulamaları derlemeye yönelik yalın bir .NET platformu sunar.

 .NET Framework'ü hedefleyen C# dilinde yazılmış Windows Store apps artık yararlanabilir .NET hangi uygulamaları IL yerine yerel kod derlenir, yerel ve [!INCLUDE[net_v46](./includes/net-v46-md.md)] Ryujıt, 64 bit tam zamanında (JIT) derleyici de ekler.

 Yeni C# ve VB derleyicileri ("Roslyn"), önemli ölçüde derleme sürelerini hızlandırmak ve kapsamlı bir kod analizi API'leri sağlar. Visual Studio 2015 satır içi dahil olmak üzere daha fazla yeniden düzenlemeleri yeniden adlandır sağlamak için Roslyn Çözümleyicileri ve hızlı düzeltmeler yararlanır.

 C# ve Visual Basic dil, çok sayıda smallish geliştirmeler çekirdek dil ve IDE desteği içerir. Tüm bu geliştirmeler, .NET kodlama deneyimi daha sezgisel, kolay ve üretken olmak için ortaya koyuyor.

 Daha fazla bilgi için [yenilikler](http://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) ve [.NET Blog](http://blogs.msdn.com/b/dotnet/).

#### <a name="c"></a>C++
 Visual C++, C ++ 11/14 dil uyumluluğu, platformlar arası mobil cihaz geliştirme desteği için önemli gelişmeler await (C ++ 17'de Standartlaştırma için planlanan şu anda) ve sürdürülebilir işlevleri destekler ve geliştirmeleri ve hata düzeltmeleri C sağlar Çalışma zamanı kitaplığı (CRT) ve C++ Standart Kitaplığı (STL) uygulamaları resizeable iletişim kutularında MFC, yeni derleyici iyileştirmeleri, daha iyi performans ve tanılama özellikleri yeni kod düzenleyicisinde yeni üretkenlik araçlarını oluşturun.

 Daha fazla bilgi için [Visual C++ için Yenilikler](http://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) ve [Visual C++ blogu](http://blogs.msdn.com/b/vcblog/).

## <a name="device-preview-menu-bar"></a>Cihaz Önizleme menü çubuğu
 Evrensel Windows platformu projelerinde, cihaz Önizleme menü çubuğunda, XAML tabanlı UI çeşitli ekran boyutlarını nasıl işlenir görmenizi sağlar.

 ![Cihaz Önizleme menüsü](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
 Visual Studio 2013'ten beri Visual Studio grafik tanılama çerçeve analizi, Windows Phone desteği, gölgelendirici düzenleme dahil olmak üzere birçok yeni özellik eklemiştir ve Uygula ve komut satırı araçları yakalar. Ayrıca, DirectX12 uygulamalarında hata ayıklamaya yönelik destek de eklemiştir. Daha fazla bilgi için [Visual Studio grafik tanılama](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Hizmetlere bağlanma
 Visual Studio 2015, uygulamanızla hizmetler için hiç bağlantı için daha kolay getirir.  Yeni bağlı hizmet Ekle Sihirbazı projenizi yapılandırır, gerekli kimlik doğrulama desteği ekler ve hizmetinizi karşı hızla ve kolayca kodlamaya başlamanıza yardımcı olmak için gerekli NuGet paketlerini indirir. Bağlı hizmet Ekle Sihirbazı'nı, ayrıca yeni hesabı birden çok kullanıcı hesaplarını ve abonelikleri ile çalışmak kolay hale getirmek için Yöneticisi ile tümleştirilir. Şu hizmetler sağlanır (hesabınız olduğunu varsayarak) kullanıma hazır Visual Studio 2015'te desteği:

1. Azure mobil hizmetler

2. Azure Depolama

3. Office 365 (posta, kişiler, takvimler, dosyalar, kullanıcılar ve gruplar)

4. Salesforce

   Sürekli olarak yeni hizmet eklenir ve bu "Bul yeni hizmetler bağlantıyı tıklatarak" Sihirbazı'nda bulabilir.

   ![Bağlı hizmetler iletişim kutusunu eklemek](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Kullanıcı Arabirimi tasarlama
 XAML kullanıcı arabirimleri tasarlama için Blend deneyimini önemli ölçüde geliştirilmiştir. Blend tamamen daha sezgisel bir kullanıcı Arabirimi, IntelliSense ve Visual Studio ile daha iyi tümleştirme dahil olmak üzere, daha güçlü XAML düzenleme özellikleri sağlamak üzere tasarlanmıştır. Daha fazla bilgi için [Visual Studio ve Visual Studio için Blend, XAML tasarlama](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Platformlar arası hata ayıklama desteği
 Visual Studio, oluşturmak ve Windows, iOS ve Android cihazlarda çalışan yerel mobil uygulamalar hata ayıklamak için kullanabilirsiniz. Kullanım [Android için Visual Studio öykünücü](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx), veya bir cihazı bağlayın ve kodunuzu doğrudan Visual Studio'da hata ayıklama.

-   **JavaScript / Cordova**. Kullanım [Apache Cordova için Visual Studio Araçları](http://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) Windows, iOS ve Android JavaScript ile yerel uygulamalar oluşturun.

     [Uygulamanızı hata ayıklama](http://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) hata ayıklama desteği Cordova için Visual Studio ayrıntılı bilgi MSDN Kitaplığı'nda olduğu.

-   **C# / Xamarin**. Kullanım [Xamarin](http://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) Windows, iOS ve Android Visual Studio'da C# ile yerel uygulamalar oluşturun.

     [Hata ayıklama](http://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/) (iOS) ve [cihazda hata ayıklama](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debugging_with_xamarin_android/) içinde [Xamarin Geliştirici kılavuzlarındaki](http://developer.xamarin.com/guides) hata ayıklama deneyimini açıklar.

-   **C++ / Android**. Kullanım [platformlar arası Mobil Geliştirme için Visual C++](http://msdnstage.redmond.corp.microsoft.com/library/dn872463\(v=vs.140\).aspx) üçüncü taraf araçlarla birlikte şablonları ister [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) Windows ve Android için yerel uygulamalar oluşturmak için.

## <a name="debugging-and-diagnostics"></a>Hata Ayıklama ve Tanılama
 Hata ayıklamaya yenilikler hakkında daha fazla bilgi için bkz: [Visual Studio 2015 hata ayıklayıcısındaki yenilikler](./debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md).

 Tanılama'da yenilikler hakkında daha fazla bilgi için bkz: [profil oluşturma araçlarındaki yenilikler](./profiling/what-s-new-in-profiling-tools.md).

 Aşağıdaki yeni veya geliştirilmiş kodunuz üzerinde farklı türde tanılama ve analiz gerçekleştiren araçlar:

### <a name="perftips"></a>PerfTips
 PerfTips yöntemleri yürütme süresini hata ayıklama sırasında hızlı bir şekilde profil oluşturucu çağırmak zorunda kalmadan performans sorunlarını saptayın olanak tanıyarak görüntüler. Başlamak için bkz: [PerfTips: performans bilgilerini bir bakışta Visual Studio ile hata ayıklama sırasında](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)

### <a name="error-list"></a>Hata Listesi
 Hata listesi, artık herhangi bir sütunu filtrelemeyi destekler. Yazdığınız sırada bir kod değişikliği binlerce uyarılar üretir zaman bile tüm C# veya Visual Basic çözümünüz arasında ayrıca hatalar, uyarılar ve Kod Analizi canlı bir görünümünü gösterir. Yeni hata listesi geriye dönük olarak uyumludur mevcut kullanım ile. Daha fazla bilgi için [Hata Listesi penceresi](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>GPU kullanımı aracı
 GPU kullanımı aracı, toplamak ve DirectX uygulamaları ve oyunları GPU kullanım verilerini çözümleme ve CPU veya GPU'nun performans sorunlarını kaynaklanan olup olmadığını sorun giderme yardımcı olur. Aracı ile çalışmaya başlamak için bkz. [Visual C++ team blog gönderisi](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx).

## <a name="live-code-analysis-light-bulbs"></a>Canlı kod analizi (ampuller)
 C# ve Visual Basic yeni Roslyn derleyici, yalnızca daha hızlı derleme sürelerini sağlar; ayrıca Canlı kod analizi gibi siz yazarken sağlayan zengin ve özelleştirilebilir bir geri bildirim ve öneriler doğrudan kod düzenleyicisi içinde tamamen yeni senaryolara olanak tanır. Visual Studio 2015'te ampuller sol kenar boşluğu (klavye kullanırken) veya bir araç ipucu (hata fare ile üzerine gelindiğinde) görüntüler. Ampul (büyük olasılıkla bir özel kural kümesi kullanarak) derleyici, kodunuzda bir sorun algıladı ve sorunun nasıl çözüleceğini yönelik bir öneri de sahip gerçek zamanlı olarak bildirir. Bir ampul gördüğünüzde, eyleme dönüştürülebilir öneriler için tıklayın.

 ![Ampuller Visual Studio Kod Düzenleyicisi'nde](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Bu ek IDE geliştirmeleri keyfini çıkarın

### <a name="synchronized-settings-roaming-settings"></a>Eşitlenmiş ayarlar (Dolaşım ayarları)
 Visual Studio 2013'ün, metin düzenleyici, tuş bağlamaları, tema & yazı tipi & renkler, başlangıç ve ortam diğer adları gibi en sık yapılandırılan ayarlardan bazıları için eşitlenmiş ayarlar kullanıma sunuldu.  Visual Studio 2015, ayarlarınızı daha fazla eşitleme ve Visual Studio Professional, Enterprise, Express SKU'ları ve Blend gibi uygulamaları ailesi üzerinden ayarları eşitleme bu deneyimini geliştirir. Visual Studio 2013'te kullanılan, Visual Studio 2015 aynı hesapla ilk kez oturum açtığınızda Visual Studio 2013'ten uygulanan eşitlenen ayarlarınız görürsünüz. Ayarlarınızı "eşitleme" yazarak erişebilirsiniz **hızlı başlatma**, veya gezinme **Araçlar > Seçenekler > ortam > eşitlenmiş ayarlar**.

### <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri
 Artık Visual Studio Galerisi üzerinde yeni bir sürümü kullanılabilir olduğunda bu, yüklü Visual Studio uzantıları otomatik olarak güncelleştirilir. Bkz: [bulma ve Visual Studio uzantılarını kullanarak](./ide/finding-and-using-visual-studio-extensions.md) otomatik uzantı güncelleştirmeleri nasıl özelleştirebileceğiniz hakkında bilgi.

### <a name="title-case-menus"></a>Başlık büyük/küçük harf menüleri
 Uç yaptık. Visual Studio menülerinin yine başlık varsayılan örneği. TÜMÜ büyük harf stili ister seçerseniz, Başlat menüsünde ayarlayabilirsiniz ancak ya da **Araçlar > Seçenekler > Genel** özellik sayfası:

 ![Visual Studio 2015 başlık çalışması ana menü komutları](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Yüksek çözünürlüklü görüntüleri ve dokunma desteği
 Visual Studio IDE true yüksek çözünürlüklü görüntülerden (menüler, bağlam menüleri, araç penceresini komut çubukları gibi alanlarda ve bazı projeler Çözüm Gezgini'nde) daha yoğun ekranlarda artık sahiptir. Ve dokunma ve tutun, sıkıştırma, vb. dokunun yakınlaştırma, kaydırma, metni seçin ve bağlam menüleri çağırır gibi bir touch-ekranında Visual Studio kod düzenleyicisi penceresi, şimdi hareketleri kullan.

 ![Dokunma desteği düzenleyicisinde](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Özel düzenler
 Depo oluşturabilir ve özel pencere düzenlerini dolaşıma girer. Örneğin, bir dizüstü bilgisayar veya küçük ekran cihazda kullanım için farklı bir düzene yanı sıra Masaüstü makinenizde kullanmak için tercih edilen bir düzen tanımlayabilirsiniz. Veya, bir kullanıcı Arabirimi proje için bir düzen ve başka bir veritabanı projesi için tercih edebilirsiniz. Tuş bağlamaları düzenleri arasında hızla geçiş yapmanızı sağlar. Oturumunuz zaman herhangi bir Visual Studio örneğinde bu düzenleri kullanılabilir. Daha fazla bilgi için [özel pencere düzenlerini oluşturma](./misc/create-custom-window-layouts.md).

 ![Visual Studio özel düzen menü öğesi](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Bildirim hub'ı
 Bildirim hub'ı için kullanıcı Arabirimi hızlı tarama kolaylaştırmak üzere basitleştirilmiştir. Performans sorunlarını, işleme sorunlarını ve kilitlenmeleri de dahil olmak üzere ek bildirim türlerini eklenmiştir ve gösteren bir bildirimini durdurmak için Visual Studio artık söyleyebilirsiniz. Daha fazla bilgi için [Visual Studio bildirimleri](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: kodunuzu (yalnızca Enterprise ve Professional sürümleri) ne olduğunu Bul
 Düzenleyiciden çıkmadan kodunuz hakkında - bilgi bulma sırasında çalışmasına odaklı kalmak. Değişiklikleri ve diğer geçmişi iş öğelerini, hataları, vb. Visual Studio Team Services (VSTS), ya da Team Foundation Server (TFS) içinde depolanan kod için kod gözden geçirmeleri, gözden geçirebilirsiniz.

 Visual Studio Enterprise ve Visual Studio Professional, artık şunları yapabilirsiniz:

- Visual Studio düzenleyicisinde bir bütün kod dosyanın geçmişini Al.

   ![CodeLens: kod dosyası ayrıntılarınıza](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Kodunuzu değiştiren kişi gösteren bir grafik görürsünüz. Bu, takımınızın değişiklikleri kalıpları bulmasına ve etkilerini değerlendirmenize yardımcı olabilir.

   ![CodeLens: Bkz: kod değişikliklerini geçmişi grafik olarak](./ide/media/codelens.png "CodeLens")

- Kodunuzu son değiştirildiği bir kolayca görebilir.

- Değişiklikleri kodunuzu etkileyen diğer dalları bulun.

  Bkz: [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Tasarım ve modelleme araçlarını (yalnızca Enterprise edition)
 **Kod haritaları ve bağımlılık grafikleri**

 Kodunuzdaki belirli bağımlılıkları anlamak istediğinizde, Visual Studio Enterprise kod haritaları oluşturarak bunları görselleştirin. Ardından, kodunuzun yanında görüntülenen haritayı kullanarak bu ilişkilere gidebilirsiniz. Kod haritaları de yardımcı olabilir, kod içindeki yerinizi çalışmak veya kodunuzun tasarımı hakkında daha fazla bilgi edinirken daha az kod okumanız için kodu, hata ayıklama sırasında izler.

 Bu sürümde, kod öğeleri ve bağlantılarına yönelik kısayol menülerini çok daha kolay seçme, düzenleme, grupları yönetme ve Grup içeriklerinin düzenini değiştirmek için ilgili bölümlere komutları gruplandırma tarafından kullanılacak yaptık. Ayrıca test projelerinin diğer projelerden farklı bir stilde görüntülendiğini ve haritadaki öğelere yönelik simgeleri daha uygun sürümlere güncelleştirdik, dikkat edin.

 ![Seçili öğeleri yeni bir kod haritasında Göster](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Diğer iyileştirmeler şunlardır:

- **Gelişmiş yukarıdan aşağıya diyagramlar**. Orta ve büyük ölçekli Visual Studio çözümleri, daha kullanışlı bir kod eşlemeleri, çözümünüz için almak için artık basitleştirilmiş bir mimari menüsü kullanabilirsiniz. Böylece bunları bağlam içinde görebilir ve, çözümü yapılandırırken yaptığınız çalışmadan yararlanarak çözümünüzün derlemeleri çözüm klasörleri tarafından gruplanır. Proje ve bütünleştirilmiş kod başvuruları ve bağlantı türleri görüntülenir hemen görürsünüz. Ayrıca, çözümünüze dışında bulunan derlemeler daha kompakt şekilde gruplanır.

- **Test projeleri farklı stillere sahip olabilir ve filtrelenebilir**. Farklı stillere çünkü haritasında test projelerini daha kolay ve hızlı bir şekilde artık tanımlayabilirsiniz. Uygulamanın çalışma koduna odaklanabilmeniz için bunlar da filtrelenebilen.

- **Basitleştirilmiş dış bağımlılık bağlantıları**. Bağımlılık bağlantıları artık System.Object, System.ValueType, System.Enum ve kod haritanızda dış bağımlılıkların görmeyi kolaylaştırır ve System.Delegate öğesinden devralmayı temsil eder.

- **' Ayrıntıya-bağımlılık bağlantılarının ' işleminde filtreler dikkate**. Bağımlılık bağlantısına yapılan katkıları anlamak için genişletirken, kullanışlı bir NET diyagram alırsınız. Diyagram daha az dağınıktır ve bağlantı filtreleme seçeneklerini seçmiş olduğunuz hesaba katar ' dir.

- **Kod öğeleri, bağlamları ile birlikte bir kod haritasına eklenir**. Diyagramları artık bağlamları (gerektiğinde filtreleyebileceğiniz, derleme ve çözüm klasörüne kadar) ile birlikte sürükleyip kod öğelerini Çözüm Gezgini, sınıf görünümü, Nesne Tarayıcısı daha kullanışlı diyagramlar elde filtreleyebileceğiniz; veya, Çözüm Gezgini'nde öğeleri ve seçerek kod haritasında göster.

- **Reaktif kod haritalarını daha hızlı alma**. Sürükleyip bırakma işlemleri anında sonuç verir ve düğümler arasındaki bağlantılar, düğümü genişletme veya daha fazla düğüm isteme gibi sonraki kullanıcı tarafından başlatılan işlemleri etkilemeden çok daha hızlı bir şekilde oluşturulur. Tüm olağandışı durumlar çözümü oluşturmadan kod haritaları oluşturduğunuzda — zaman derlemeleri oluşturulmadı gibi — şimdi işlenir.

- **Çözümünüzü yeniden oluşturmayı atlama.** Diyagram oluştururken veya düzenlerken daha iyi performans sağlar.

- **Kod öğesi düğümlerini ve gruplarını filtreleme**. Hızlı bir şekilde, gösterme veya gizleme kod öğelerini kategorilerine veya kod öğelerini çözüm klasörleri, derlemeler, ad alanları, proje klasörleri ve türleri tarafından gruplandırma etsek düzelten.

- **Diyagramların okunmasını kolaylaştırmak için ilişkileri filtreleme**. Bağlantı filtrelemesi artık filtre penceresiyle çalışılmasını daha az sezgisel önceki sürümlere kıyasla getiren, çapraz grup bağlantıları için de geçerlidir.

- **Sınıf Görünümü ve Nesne Tarayıcısı'ndan diyagramlar oluşturma**. Sürükleyip dosyaları ve yeni veya mevcut bir haritayı derlemeleri sınıf görünümü ve Nesne Tarayıcısı windows.

  Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](./modeling/map-dependencies-across-your-solutions.md).

  **Bu sürümdeki diğer tasarım ve modelleme değişiklikleri:**

- **Katman diyagramları**. Sınıf Görünümü ve Nesne Tarayıcısı'nı kullanarak bu diyagramları güncelleştirin. Yazılım tasarımı gerekliliklerini yerine getirmek için yazılımınız için istenen bağımlılıkları açıklamak için katman diyagramları kullanın. Kodun bu tasarım ile tutarlı bu sınırlamaları karşılamayan kodu bularak ve sonraki kodu bu temele göre doğrulayarak tutun.

- **UML diyagramları**. Artık koddan UML sınıf diyagramları ve sıra diyagramları oluşturamazsınız. Ancak yine de yeni UML öğelerini kullanarak bu diyagramları oluşturur.

- **Mimari Gezgini**. Mimari Gezgini artık diyagramları oluşturmak için de kullanabilirsiniz. Ancak Çözüm Gezgini'ni kullanmaya devam edebilirsiniz.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio genişletilebilirlik araçları
 Artık oldukları gibi Visual Studio genişletilebilirlik Araçları (VS SDK ve şablonlar) yüklemek daha kolay olmamıştı Kurulum sırasında isteğe bağlı bir bileşen dahil.  Genişletilebilirlik araçları, özelleştirmek ve özellikler eklemek için Visual Studio için uzantıları yazmak geliştiricilerinin imkan tanır. Visual Studio genişletilebilirlik hakkında daha fazla bilgi için bkz: [Visual Studio SDK'sı](./extensibility/visual-studio-sdk.md)

 Genişletilebilirlik araçları, özel yükleme işleminize dahil etmek isterseniz, bunları altında bulabilirsiniz **özellikleri / ortak araçlar / Visual Studio genişletilebilirlik Araçları**.  Açarak daha sonraki bir zamanda genişletilebilirlik araçları yükleyebilirsiniz **yeni proje** iletişim ve seçerek **yükleme Visual Studio genişletilebilirlik Araçları** altında madde **Visual C# / Genişletilebilirlik**.

## <a name="please-give-feedback"></a>Lütfen geri bildirimde bulunun
 Neden Visual Studio ekibine geri bildirim gönderilsin mi? Size müşteri geri bildirimi ciddiye olduğundan. Aslında, her parça geri bildirim sistemimiz gelen geri bildirimler inceleyin. Geri bildiriminiz bizim çok fazla beraberinde getirir.

### <a name="send-a-smile"></a>Gülümseme Gönder
 Bize söyleyerek ne gibi bize yardımcı olur, biz karşıladığında veya beklentilerinizi anlama. Biz tasarlama ve uygulama yeni özellikler, müşterilerimize tasarım kararlarına yardımcı olmak için istediğiniz özellikler hakkında daha fazla veri kullanırız. Visual Studio özelliği istiyorsanız, bu nedenle, iyileştirebileceğimize ilişkin. Kolay bir işlemdir ve doğrudan IDE içinde yapabilirsiniz.

 Yalnızca başlık çubuğunda sarı gülen yüz tıklayın, ardından beğenmediğinizi bize **gülümseme Gönder** düğmesi.

 İşte bu kadar! Biz burada bunlar kendilerini arkasında pat sonra hızlıca bile daha memnun edecek şekilde düşünmeye başlamak doğru ekibe geri bildirim rota.

### <a name="send-a-frown"></a>Kaş çatma Gönder
 Burada üründe geliştirmeler yapmak için ihtiyacımız duymak bizim biriktirme ilk müşterilerimize en önemli olan şeyleri odaklanarak yönetmek için yardımcı olur. Varsa, bugging bir şey kullanarak iyileştirebileceğimize ilişkin **kaş çatma Gönder** doğrudan IDE içinde özellik öğesinden. Bu son derece basit bir işlem çok yaptık:

 Başlık çubuğunda sarı gülen yüz'ı tıklatın **kaş çatma Gönder**. Bize ne kaş çatma düğme Gönder'i hoşunuza giden değil. Daha fazla bilgi için [konuşmak bize](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Rapor kilitlenmeler, askıda kalır ve performans konuları
 Bazı durumlarda, hızlı Not kaş çatma içinde yalnızca tam etkisi yok gibi bir şey iletmek için yeterli değildir. Bir yanıt vermemesine, kilitlenme veya performans sorunu olduğunda saatlere, kolayca yineleme adımları ve kilitlenme bilgi dökümleri izleme dosyaları kaş çatma Gönder sonra görüntülenen iletişim kutusunu kullanarak paylaşabilirsiniz.

 İlk olarak, yukarıda açıklanan şekilde kaş çatma Gönder. Açılan iletişim kutusunda, geri bildirim etiketi varsayılan etiket birini veya kendi etiket oluştur. Etiketler bize geri bildirim yönlendirmek için uygun özellik takımı yardımcı olur. İçinde **bir kategori seçin** açılan listesinde, raporlama olduğunuz sonra sorunu yeniden oluşturmak için adımları sorunu temsil eden seçeneğini belirleyin. Visual Studio geri bildirim raporu kullanma hakkında ayrıntılı adımlar de mevcuttur. Daha fazla bilgi için [Visual Studio bir Gülümseyin yönergeleri gönderin](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Ayrıca Bkz.

* [Apache Cordova ile platformlar arası uygulamalar oluşturma](http://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Visual C++ ile platformlar arası mobil uygulamalar oluşturun](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Intellitest ile kodunuz için birim testleri oluşturma](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Birden çok kullanıcı hesabıyla çalışma](./ide/work-with-multiple-user-accounts.md)
* [Özel pencere düzenlerini oluşturma](./misc/create-custom-window-layouts.md)
* [Ampullerle hızlı eylemler gerçekleştirme](./ide/perform-quick-actions-with-light-bulbs.md)
* [Visual Studio 2017'deki yenilikler](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)