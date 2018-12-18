---
title: Platformlar arası Mobil Geliştirme
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 4f98b51be027240cf6acee57ec6f8dc8f149a8e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056606"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio’da Platformlar Arası Mobil Geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio kullanarak Android, iOS ve Windows cihazlar için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, araçları Visual Studio'da bağlı hizmetler Application ınsights'ı Office 365 ve Azure App Service gibi kolayca eklemek için kullanın.

 C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dizeler, resimleri paylaşın ve kullanıcı arabiriminin bazı durumlarda bile.

 Oyun veya derinlikli bir grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları'nı yükleyin ve tüm Visual Studio ile Unity uygulamaları için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı, güçlü üretkenlik özellikleri keyfini çıkarın, iOS, Android, Windows ve diğer platformlarda çalıştırın.

 **Bu makalede:**

-   [Android, iOS ve Windows (.NET Framework) için uygulama oluşturma](#NET)

    -   [Android, iOS ve Windows, bir tek kod tabanından hedef](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

    -   [Windows 10 cihazlarını hedefleyin](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

-   [Android, iOS ve Windows (HTML/JavaScript) için uygulama oluşturma](#HTML)

-   [Android ve Windows (C++) için uygulama oluşturma](#CPP)

-   [Unity için Visual Studio araçları kullanarak Android, iOS ve Windows için platformlar arası oyun oluşturun](#Unity)

##  <a name="NET"></a> Android, iOS ve Windows (.NET Framework) için uygulama oluşturma
 ![Cihazları](../cross-platform/media/homedevices.png "HomeDevices")

 Xamarin ile kod ve hatta kullanıcı Arabirimi paylaşımı aynı çözüm içinde Android, iOS ve Windows hedefleyebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio yükleme](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Visual Studio'da Xamarin hakkında bilgi edinin](http://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com)|
|[Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md) (MSDN Kitaplığı)|
|[Xamarin uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM)](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (MSDN Kitaplığı)|
|[Visual Studio'da Evrensel Windows uygulamaları hakkında bilgi edinin](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# arasındaki benzerlikleri hakkında bilgi edinin](http://aka.ms/scposter) (download.microsoft.com)|
|[Android için Visual Studio öykünücüsü öğrenin](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

###  <a name="AndroidHTML"></a> Android, iOS ve Windows, bir tek kod tabanından hedef
 Kullanarak Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz C# veya F# (Visual Basic şu anda desteklenmiyor).  Başlamak için Visual Studio 2015'i yükleyin, seçin **özel** seçeneği yükleyicide ve seçeneğinin altındaki kutuyu **platformlar arası mobil geliştirme > C# / .NET (Xamarin)**. İle başlayabilirsiniz [Xamarin yükleyici](https://www.xamarin.com/download), Xamarin için Visual Studio 2013 yüklemek için gereklidir.

 Visual Studio 2015'i zaten varsa, yükleyici'den çalıştırın **Denetim Masası > Programlar ve Özellikler** ve aynı **özel** Xamarin için bir seçenek olarak yukarıdaki.

 İşiniz bittiğinde, proje şablonları görünür **yeni proje** iletişim kutusu. "Xamarin" üzerinde yalnızca aramak için Xamarin şablonları bulmanın en kolay yolu olan

 Xamarin yerel Android, iOS ve Windows işlevselliğini .NET nesneleri olarak kullanıma sunar. Bu nedenle, uygulamalarınızı yerel API'lere ve yerel kullanıcı denetimleri tam erişime sahiptir ve bunlar yalnızca, yerel platform dillerde yazılan uygulamaları olarak duyarlı.

 Bir proje oluşturduğunuzda, tüm Visual Studio üretkenlik özelliklerinden faydalanabilirsiniz. Örneğin, sayfa oluşturmak için bir tasarımcı kullanır ve yerel API'lere mobil platformlarda keşfetmek için IntelliSense kullanın. Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android veya Android SDK öykünücüsü için Visual Studio öykünücüsü'nü kullanın, Windows uygulamaları yerel olarak çalıştırma veya Windows uygulamalarını Windows Phone öykünücü üzerinde çalıştırın. Tethered Android ve Windows cihazları doğrudan da kullanabilirsiniz. İOS projeleri için bir mac'e bağlanın ve Visual Studio'dan Mac öykünücüyü başlatın veya tethered bir cihaza bağlayın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Bir Xamarin.Forms kullanarak tüm cihazlarda oluşturan sayfalar kümesini tasarlama
 Uygulama tasarımınızı karmaşıklığına bağlı olarak, kullanarak oluşturmayı düşünebilirsiniz *Xamarin.Forms* şablonlarında **Mobile Apps** grup proje şablonları. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabilirsiniz tek bir arabirim oluşturmanıza imkan tanıyan bir UI araç takımıdır.  Xamarin.Forms çözümü derlediğinizde, bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması elde edersiniz. Daha fazla ayrıntı için [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

####  <a name="ShareHTML"></a> Android, iOS ve Windows uygulamaları arasında kod paylaşma
 Xamarin.Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamak seçerseniz, çoğu kullanıcı Arabirimi olmayan kodunuzun platformu projelerinde (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, iş mantığı, bulut tümleştirme, veritabanı erişimi veya .NET Framework'ü hedefleyen herhangi bir kod içerir. Paylaşamazsınız yalnızca kodu belirli bir platformu hedefleyen kodudur.

 ![Windows, iOs ve Android kullanıcı Arabiriminin arasında kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, taşınabilir sınıf kitaplığı projesi veya her ikisini de kullanarak kodunuzu paylaşabilir. Daha fazla iyi bir paylaşılan projede veya bazı kod yapar bazı kod uygun bir taşınabilir sınıf kitaplığı projesi içinde anlamlıdır bulabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|Paylaşılan projeler, taşınabilir sınıf kitaplığı projeleri veya her ikisini de kullanarak kodunuzu paylaşmak isteyip istemediğinizi seçin.<br /><br /> [Platformlar arasında kod paylaşımını](http://blogs.msdn.com/b/dotnet/archive/2014/04/21/sharing-code-across-platforms.aspx) (.NET Framework blogu)<br /><br /> [Paylaşım kod seçeneklerini](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Xamarin)<br /><br /> [Kod paylaşma seçenekleri .NET Framework ile](http://msdn.microsoft.com/library/dn720832.aspx) (MSDN Kitaplığı)|

###  <a name="WindowsHTML"></a> Windows 10 cihazlarını hedefleyin
 ![Windows cihazları](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Windows 10 cihazları olan tüm tekliflerden hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir evrensel Windows uygulaması oluşturun. Tek bir proje kullanarak uygulama tasarlayın ve hangi cihaz ne olursa olsun, bunları görüntülemek için kullanılır, sayfalar düzgün bir şekilde işlenir.

 Evrensel Windows uygulaması proje şablonu ile başlayın. Sayfalarınızı görsel olarak tasarlamanıza ve bunları çeşitli cihaz türleri için görünme görmek için bir önizleme penceresini açın. Nasıl bir cihazda bir sayfa görünür kullanmak istemiyorsanız, sayfanın ekran boyutu, çözüm ya da yatay veya dikey modu gibi çeşitli yönleriyle daha iyi uyacak şekilde en iyi duruma getirebilirsiniz. Tüm bu, Visual Studio'da sezgisel araç pencereleri ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Kodunuz uygulama ve adım çalıştırmaya hazır olduğunuzda, tüm aygıt benzetmeleri ve simülatörleri farklı cihaz türleri için birlikte bulunan bir açılan listedeki bulabilirsiniz **standart** araç çubuğu.

 Windows 10 oldukça yeni olduğundan Windows 8.1 hedefleyen proje şablonları da bulabilirsiniz. İstediğiniz ve uygulamanızı Windows 10 telefonlar, tabletler ve bilgisayarlar üzerinde çalışır, bu proje şablonları kullanabilirsiniz. Ancak, Windows 8.1 çalıştıran tüm cihazlara otomatik alırsınız Windows 10 yükseltme, bu nedenle özel nedenlerin neden yerine hedef Windows 8.1 olmadığı sürece, Windows 10'u hedefleyen proje şablonları kullanmanızı öneririz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows uygulamaları hakkında bilgi edinin](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Geliştirici Merkezi)|
|[İlk uygulamanızı bir derleme](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Geliştirici Merkezi)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Evrensel Windows Platformu (UWP) uygulamaları geçirme](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

##  <a name="HTML"></a> Android, iOS ve Windows (HTML/JavaScript) için uygulama oluşturma
 ![Cihazları](../cross-platform/media/homedevices.png "HomeDevices")

 Bir web geliştiricisi olduğunuzu ve HTML ve JavaScript ile ilgili bilgi sahibi olduğunuz, Apache Cordova için Visual Studio araçları kullanarak Windows, Android ve iOS hedefleyebilirsiniz. Bu uygulamalar, tüm üç platformlar hedefleyebilir ve bunları en alışık olduğunuz işlemleri ve becerileri kullanarak oluşturun.

 Apache Cordova eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, tüm üç platformları (Android, iOS ve Windows), yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si sağlar.

 Bu API'ler, platformlar arası olduğundan, tüm üç platformlar arasında yazma çoğu paylaşabilirsiniz. Bu, geliştirme ve Bakım maliyetlerinizi azaltır. Ayrıca, baştan başlatmaya gerek yoktur. Web uygulamalarının diğer türleri oluşturduysanız, herhangi bir şekilde yeniden tasarlayıp tasarlayamayacağınızı veya değiştirmek zorunda kalmadan, bu dosyaları ile Cordova uygulamanızı paylaşabilirsiniz.

 ![Çoklu&#45;Cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Başlamak için Visual Studio 2015'i yükleyin ve seçin **HTML/JavaScript (Apache Cordova)** Kurulum sırasında özellik. Visual Studio 2013 kullanıyorsanız, Apache Cordova uzantısı için Visual Studio Araçları yükleyin. Her iki durumda da, Cordova araçları, çok platformlu uygulamanızı oluşturmak için gerekli tüm üçüncü taraf yazılımlarını otomatik olarak yükler.

 Uzantıyı yükledikten sonra Visual Studio'yu açın ve oluşturma bir **boş uygulama (Apache Cordova)** proje. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Uygulamanızı genişletmek için eklentilerini da ekleyebilir ve kod yazarken IntelliSense içinde eklentiler API'lerinden görünür.

 Kodunuz uygulama ve adım çalıştırmaya hazır olduğunuzda, Apache Ripple öykünücü, Visual Studio öykünücü (Android veya Windows Phone), bir tarayıcı veya bilgisayarınıza doğrudan bağlı bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Bir Windows bilgisayarda uygulama geliştiriyorsanız, hatta üzerinde çalıştırabilirsiniz. Bu seçeneklerin tümü Visual Studio Araçları'nın bir parçası olarak Visual Studio ile Apache Cordova için oluşturulur.

 Evrensel Windows uygulamaları oluşturma Visual Studio'da hala kullanılabilir proje şablonları bu nedenle yalnızca Windows cihazları hedefleyen planlıyorsanız, bunları kullanan çekinmeyin. Daha sonra Android ve iOS platformlarını karar verirseniz, her zaman bir Cordova projesi için kod bağlantı noktası. Bu API kullanan herhangi bir kod yeniden kullanabilmesi WinJS API'leri, açık kaynak sürümü vardır. Bu, gelecekte diğer platformları hedefleyen planlıyorsanız, Apache Cordova için Visual Studio Araçları ile başlamanızı öneririz belirtti.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio yükleme](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Apache Cordova için Visual Studio Araçları ile çalışmaya başlama](http://taco.visualstudio.com/en-us/docs/get-started-vs-tools-apache-cordova/) (taco.visualstudio.com)|
|[Android için Visual Studio öykünücüsü öğrenin](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

##  <a name="CPP"></a> Android ve Windows (C++) için uygulama oluşturma
 ![Kullanım C&#43; &#43; Android, iOS ve Windows için oluşturulacak](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak Visual Studio 2015 ve Visual C++ platformlar arası mobil geliştirme araçlarını yükleyin. Ardından, Android veya Windows hedefleyen bir uygulama için bir yerel etkinlik uygulaması oluşturabilirsiniz. İOS hedefleyen C++ şablonları henüz kullanıma sunulmamıştır. Ve ardından bunları bir platformlar arası statik veya dinamik paylaşılan kitaplık kullanarak arasında kod paylaşma, Android ve Windows aynı çözüm içinde hedefleyebilirsiniz.

 Gelişmiş grafik işleme, oyun gibi her türlü gerektiren Android için bir uygulama oluşturmak ihtiyacınız varsa yapmak için C++ kullanabilirsiniz. İle başlayan **Native-Activity uygulaması (Android)** proje. Bu proje, Clang araç zinciri için tam destek sunar.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat-cpp-native.png "arası Plat_CPP_Native")

 Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android için Visual Studio öykünücüsü'nü kullanın. Bu hızlı, güvenilir ve kolay yükleme ve yapılandırma.

 Ayrıca, C++ ve evrensel Windows uygulaması proje şablonunu kullanarak Windows 10 cihazları olan tüm tekliflerden hedefleyen bir uygulama oluşturabilirsiniz. Bu konuda hakkında daha fazla bilgiyi [hedef Windows 10 cihazları](#WindowsHTML) bu konuda daha önce görünen bölümü.

 Bir statik veya dinamik paylaşılan kitaplık oluşturarak, Android ve Windows arasında C++ kod paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Bir Windows veya Android projesi, daha önce bu bölümde açıklanan olanlar gibi bu kitaplığı kullanabilir. Ayrıca, bir uygulamada, Xamarin, Java veya yönetilmeyen DLL işlevlerini çağırma olanak sağlayan herhangi bir dil kullanarak yapı raporlarını kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarını yerel API'leri keşfetmek için IntelliSense'i kullanabilirsiniz. Kesme noktaları, kodu adımlama ve bulabilir ve tüm hata ayıklayıcı'nın Gelişmiş özelliklerine kullanarak sorunları düzeltmek için bu kitaplık projeleri, Visual Studio hata ayıklayıcıyla tamamen tümleştirilmiştir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio'yu indirin.](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Visual C++ platformlar arası mobil geliştirme araçlarını yükleyin.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[C++ birden çok platformu hedefleyecek şekilde kullanma hakkında daha fazla bilgi edinin.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Neleri gerekir ve ardından Android için bir yerel etkinlik uygulaması oluşturma yükleme](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (MSDN Kitaplığı)|
|[Android için Visual Studio öykünücüsü öğrenin](http://www.visualstudio.com/explore/msft-android-emulator-vs) (VisualStudio.com)|
|[C++ kodu ile Android ve Windows uygulamaları paylaşma hakkında daha fazla bilgi edinin](http://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx) (VisualStudio.com)|
|[C++ platformlar arası mobil geliştirme örnekleri](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Kitaplığı)|
|[C++ için ek platformlar arası mobil geliştirme örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

##  <a name="Unity"></a> Unity için Visual Studio araçları kullanarak Android, iOS ve Windows için platformlar arası oyun oluşturun
 Unity için Visual Studio Araçları, Visual Studio'nun güçlü kod düzenleme, üretkenlik ve hata ayıklama araçları ile tümleştirilir. Visual Studio için ücretsiz bir uzantı *Unity*, popüler platformlar arası oyun/grafik altyapısı ve Windows, iOS, Android ve web dahil olmak üzere diğer platformları hedefleyen modern uygulamalar için geliştirme ortamı.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz. VSTU en son sürümünü Unity 5 için destek getirir ve Unity'nın ShaderLab gölgelendirici dili için söz dizimi renklendirme, daha iyi eşitlemesi Unity, daha zengin hata ayıklama ve geliştirilmiş kod oluşturma için MonoBehavior Sihirbazı'nı içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.

 Oyununuzu Unity ve Unity için Visual Studio Araçları ile oluşturmaya hemen başlayın.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Unity Visual Studio ile oyun oluşturma hakkında daha fazla bilgi edinin](https://www.visualstudio.com/en-us/features/unitytools-vs.aspx)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgiyi](../cross-platform/visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Unity için Visual Studio Araçları kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (MSDN Kitaplığı)|
|[Son geliştirmeler hakkında Unity 2.0 önizlemesi için Visual Studio Araçları okuma](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (Visual Studio blogu)|
|[Unity 2.0 önizlemesi için Visual Studio Araçları için bir tanıtım izleyin](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Unity hakkında bilgi edinin](http://unity3d.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio projesi için Office 365 API ekleme](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure mobil hizmetler](http://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)