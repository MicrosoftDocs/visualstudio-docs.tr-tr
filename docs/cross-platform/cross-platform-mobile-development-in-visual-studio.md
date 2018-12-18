---
title: Visual Studio'da platformlar arası Mobil Geliştirme | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: c28dcf247a9e0faaec13ddc4b3006cf6a93fda90
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496148"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Visual Studio'da platformlar arası Mobil Geliştirme

Visual Studio kullanarak Android, iOS ve Windows cihazlar için uygulamalar oluşturabilirsiniz.  Uygulamanızı tasarlarken, araçları Visual Studio'da bağlı hizmetler Application ınsights'ı Office 365 ve Azure App Service gibi kolayca eklemek için kullanın.

C# ve .NET Framework, HTML ve JavaScript veya C++ kullanarak uygulamalarınızı oluşturun. Kod, dizeler, resimleri paylaşın ve kullanıcı arabiriminin bazı durumlarda bile.

Oyun veya derinlikli bir grafik uygulaması oluşturmak istiyorsanız, Unity için Visual Studio Araçları'nı yükleyin ve tüm Visual Studio ile Unity uygulamaları için popüler platformlar arası oyun/grafik altyapısı ve geliştirme ortamı, güçlü üretkenlik özellikleri keyfini çıkarın, iOS, Android, Windows ve diğer platformlarda çalıştırın.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Android, iOS ve Windows (.NET Framework) için uygulama oluşturma

![Cihazları](../cross-platform/media/homedevices.png "HomeDevices")

Xamarin için Visual Studio Araçları ile kod ve hatta kullanıcı Arabirimi paylaşımı aynı çözüm içinde Android, iOS ve Windows hedefleyebilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio yükleme](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Visual Studio'da Xamarin hakkında bilgi edinin](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Xamarin mobil uygulama geliştirme belgeleri](/xamarin/) |
|[Xamarin uygulamaları ile DevOps](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) |
|[Visual Studio'da Evrensel Windows uygulamaları hakkında bilgi edinin](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Swift ve C# arasındaki benzerlikleri hakkında bilgi edinin](http://aka.ms/scposter) (download.microsoft.com)|

###  <a name="AndroidHTML"></a> Android, iOS ve Windows, bir tek kod tabanından hedef

 C# veya F # (Visual Basic şu anda desteklenmiyor) kullanarak, Android, iOS ve Windows için yerel uygulamalar oluşturabilirsiniz.  Başlamak için Visual Studio 2017'yi, seçin **.NET ile Mobil Geliştirme** yükleyici seçeneği.

 Visual Studio 2017 zaten varsa, yeniden çalıştırma **Visual Studio yükleyicisi** ve aynı **.NET ile Mobil Geliştirme** Xamarin seçeneğini (yukarıdaki gibi).

 İşiniz bittiğinde, proje şablonları görünür **yeni proje** iletişim kutusu. "Xamarin" üzerinde yalnızca aramak için Xamarin şablonları bulmanın en kolay yolu olan

 Xamarin yerel Android, iOS ve Windows işlevselliğini .NET sınıflar ve yöntemler olarak kullanıma sunar. Bu, uygulamalarınızın yerel API'lere ve yerel denetimleri tam erişime sahiptir ve bunlar yalnızca, yerel platform dillerde yazılan uygulamaları olarak duyarlı anlamına gelir.

 Bir proje oluşturduğunuzda, tüm Visual Studio üretkenlik özelliklerinden faydalanabilirsiniz. Örneğin, sayfa oluşturmak için bir tasarımcı kullanır ve yerel API'lere mobil platformlarda keşfetmek için IntelliSense kullanın. Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android SDK öykünücüsü'nü kullanın ve Windows uygulamalarını yerel olarak çalıştırın. Tethered Android ve Windows cihazları doğrudan da kullanabilirsiniz. İOS projeleri için bir mac'e bağlanın ve Visual Studio'dan iOS öykünücüyü başlatın veya tethered bir cihaza bağlayın.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Bir Xamarin.Forms kullanarak tüm cihazlarda oluşturan sayfalar kümesini tasarlama

 Uygulama tasarımınızı karmaşıklığına bağlı olarak, kullanarak oluşturmayı düşünebilirsiniz *Xamarin.Forms* şablonlarında **Mobile Apps** grup proje şablonları. Xamarin.Forms, Android, iOS ve Windows arasında paylaşabilirsiniz tek bir arabirim oluşturmanıza imkan tanıyan bir UI araç takımıdır.  Xamarin.Forms çözümü derlediğinizde, bir Android uygulaması, bir iOS uygulaması ve bir Windows uygulaması elde edersiniz. Daha fazla ayrıntı için [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md) ve [Xamarin.Forms belgeleri](/xamarin/xamarin-forms/).

####  <a name="ShareHTML"></a> Android, iOS ve Windows uygulamaları arasında kod paylaşma

 Xamarin.Forms kullanmıyorsanız ve her platform için ayrı ayrı tasarlamak seçerseniz, çoğu kullanıcı Arabirimi olmayan kodunuzun platformu projelerinde (Android, iOS ve Windows) arasında paylaşabilirsiniz. Bu, iş mantığı, bulut tümleştirme, veritabanı erişimi veya .NET Framework'ü hedefleyen herhangi bir kod içerir. Paylaşamazsınız yalnızca kodu belirli bir platformu hedefleyen kodudur.

 ![Windows, iOs ve Android kullanıcı Arabiriminin arasında kod paylaşma](../cross-platform/media/sharecode.png "ShareCode")

 Paylaşılan bir proje, taşınabilir sınıf kitaplığı projesi veya her ikisini de kullanarak kodunuzu paylaşabilir. Daha fazla iyi bir paylaşılan projede veya bazı kod yapar bazı kod uygun bir taşınabilir sınıf kitaplığı projesi içinde anlamlıdır bulabilirsiniz.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Paylaşım kod seçeneklerini](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Kod paylaşma seçenekleri ile .NET](/dotnet/standard/cross-platform/) |

###  <a name="WindowsHTML"></a> Windows 10 cihazlarını hedefleyin

 ![Windows cihazları](../cross-platform/media/windowsdevices.png "Windows cihazları")

 Windows 10 cihazları olan tüm tekliflerden hedefleyen tek bir uygulama oluşturmak istiyorsanız, bir evrensel Windows uygulaması oluşturun. Tek bir proje kullanarak uygulama tasarlayın ve hangi cihaz ne olursa olsun, bunları görüntülemek için kullanılır, sayfalar düzgün bir şekilde işlenir.

 Evrensel Windows Platformu (UWP) uygulaması proje şablonu ile başlayın. Sayfalarınızı görsel olarak tasarlamanıza ve bunları çeşitli cihaz türleri için görünme görmek için bir önizleme penceresini açın. Nasıl bir cihazda bir sayfa görünür kullanmak istemiyorsanız, sayfanın ekran boyutu, çözüm ya da yatay veya dikey modu gibi çeşitli yönleriyle daha iyi uyacak şekilde en iyi duruma getirebilirsiniz. Tüm bu, Visual Studio'da sezgisel araç pencereleri ve kolayca erişilebilen menü seçeneklerini kullanarak yapabilirsiniz. Kodunuz uygulama ve adım çalıştırmaya hazır olduğunuzda, tüm aygıt benzetmeleri ve simülatörleri farklı cihaz türleri için birlikte bulunan bir açılan listedeki bulabilirsiniz **standart** araç çubuğu.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Evrensel Windows platformu giriş](/windows/uwp/get-started/universal-application-platform-guide)|
|[İlk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app)|
|[Evrensel Windows Platformu (UWP) için uygulama geliştirme](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Evrensel Windows Platformu (UWP) uygulamaları geçirme](https://msdn.microsoft.com/library/mt148501.aspx)|

##  <a name="HTML"></a> Android, iOS ve Windows (HTML/JavaScript) için uygulama oluşturma

 ![Windows, iOS ve Android cihazlarda](../cross-platform/media/homedevices.png "Windows, iOS ve Android cihazlar")

 Bir web geliştiricisi olduğunuzu ve HTML ve JavaScript ile ilgili bilgi sahibi olduğunuz, Apache Cordova için Visual Studio araçları kullanarak Windows, Android ve iOS hedefleyebilirsiniz. Bu uygulamalar, tüm üç platformlar hedefleyebilir ve bunları en alışık olduğunuz işlemleri ve becerileri kullanarak oluşturun.

 Apache Cordova eklenti modeli içeren bir çerçevedir. Bu eklenti modeli, tüm üç platformları (Android, iOS ve Windows), yerel cihaz özelliklerine erişmek için kullanabileceğiniz tek bir JavaScript API'si sağlar.

 Bu API'ler, platformlar arası olduğundan, tüm üç platformlar arasında yazma çoğu paylaşabilirsiniz. Bu, geliştirme ve Bakım maliyetlerinizi azaltır. Ayrıca, baştan başlatmaya gerek yoktur. Web uygulamalarının diğer türleri oluşturduysanız, herhangi bir şekilde yeniden tasarlayıp tasarlayamayacağınızı veya değiştirmek zorunda kalmadan, bu dosyaları ile Cordova uygulamanızı paylaşabilirsiniz.

 ![Javascript ile çok cihazlı karma uygulamalar](../cross-platform/media/multidevicehybridapps.png "Javascript ile çok cihazlı karma uygulamalar")

 Başlamak için Visual Studio 2017'yi yükleyin ve seçin **Javascript ile Mobil Geliştirme** Kurulum sırasında özellik. Cordova araçları, çok platformlu uygulamanızı oluşturmak için gerekli tüm üçüncü taraf yazılımlarını otomatik olarak yükler.

 Uzantıyı yükledikten sonra Visual Studio'yu açın ve oluşturma bir **boş uygulama (Apache Cordova)** proje. Ardından, JavaScript veya Typescript kullanarak uygulamanızı geliştirebilirsiniz. Uygulamanızı genişletmek için eklentilerini da ekleyebilir ve kod yazarken IntelliSense içinde eklentiler API'lerinden görünür.

 Kodunuz uygulama ve adım çalıştırmaya hazır olduğunuzda, Apache Ripple öykünücüsünü veya Android öykünücüsü, bir tarayıcı veya bilgisayarınıza doğrudan bağlı bir cihaz gibi bir öykünücü seçin. Ardından, uygulamanızı başlatın. Bir Windows bilgisayarda uygulama geliştiriyorsanız, hatta üzerinde çalıştırabilirsiniz. Bu seçeneklerin tümü Visual Studio Araçları'nın bir parçası olarak Visual Studio ile Apache Cordova için oluşturulur.

 Evrensel Windows Platformu (UWP) uygulamaları oluşturma Visual Studio'da hala kullanılabilir proje şablonları bu nedenle yalnızca Windows cihazları hedefleyen planlıyorsanız, bunları kullanmak çekinmeyin. Daha sonra Android ve iOS platformlarını karar verirseniz, her zaman bir Cordova projesi için kod bağlantı noktası.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio yükleme](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Apache Cordova için Visual Studio Araçları ile çalışmaya başlama](/visualstudio/cross-platform/tools-for-cordova/)|
|[Android için Visual Studio öykünücüsü öğrenin](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

<a name="CPP"></a>

## <a name="build-an-app-for-android-and-windows-c"></a>Android ve Windows (C++) için uygulama oluşturma
 ![Kullanım C&#43; &#43; Android, iOS ve Windows için oluşturulacak](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 İlk olarak, Visual Studio 2017'yi yükleyin ve **C++ ile Mobil Geliştirme** iş yükü. Ardından, Android veya Windows hedefleyen bir uygulama için bir yerel etkinlik uygulaması oluşturabilirsiniz. İOS hedefleyen C++ şablonları henüz kullanıma sunulmamıştır. Ve ardından bunları bir platformlar arası statik veya dinamik paylaşılan kitaplık kullanarak arasında kod paylaşma, Android ve Windows aynı çözüm içinde hedefleyebilirsiniz.

 Gelişmiş grafik işleme, oyun gibi her türlü gerektiren Android için bir uygulama oluşturmak ihtiyacınız varsa yapmak için C++ kullanabilirsiniz. İle başlayan **Native-Activity uygulaması (Android)** proje. Bu proje, Clang araç zinciri için tam destek sunar.

 ![Yerel etkinlik proje şablonu](../cross-platform/media/cross-plat_cpp_native.png "yerel etkinlik proje şablonu")

 Uygulamanızı çalıştırın ve nasıl göründüğüne bakmak hazır olduğunuzda, Android öykünücüsü'nü kullanın. Bu hızlı, güvenilir ve kolay yükleme ve yapılandırma.

 Ayrıca, C++ ve Uiversal Windows Platformu (UWP) uygulaması proje şablonunu kullanarak Windows 10 cihazları olan tüm tekliflerden hedefleyen bir uygulama oluşturabilirsiniz. Bu konuda hakkında daha fazla bilgiyi [hedef Windows 10 cihazları](#WindowsHTML) bu konuda daha önce görünen bölümü.

 Bir statik veya dinamik paylaşılan kitaplık oluşturarak, Android ve Windows arasında C++ kod paylaşabilirsiniz.

 ![Statik ve dinamik paylaşılan kitaplıklar](../cross-platform/media/cross_plat_cpp_libraries.png "statik ve dinamik paylaşılan kitaplıklar")

 Bir Windows veya Android projesi, daha önce bu bölümde açıklanan olanlar gibi bu kitaplığı kullanabilir. Ayrıca, bir uygulamada, Xamarin, Java veya yönetilmeyen DLL işlevlerini çağırma olanak sağlayan herhangi bir dil kullanarak yapı raporlarını kullanabilirsiniz.

 Bu kitaplıklara kod yazarken, Android ve Windows platformlarını yerel API'leri keşfetmek için IntelliSense'i kullanabilirsiniz. Kesme noktaları, kodu adımlama ve bulabilir ve tüm hata ayıklayıcı'nın Gelişmiş özelliklerine kullanarak sorunları düzeltmek için bu kitaplık projeleri, Visual Studio hata ayıklayıcıyla tamamen tümleştirilmiştir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Visual Studio'yu indirin.](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Visual C++ platformlar arası mobil geliştirme araçlarını yükleyin.](https://msdn.microsoft.com/library/dn707591.aspx) (MSDN Kitaplığı)|
|[C++ birden çok platformu hedefleyecek şekilde kullanma hakkında daha fazla bilgi edinin.](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Neleri gerekir ve ardından Android için bir yerel etkinlik uygulaması oluşturma yükleme](https://msdn.microsoft.com/library/dn707595.aspx) (MSDN Kitaplığı)|
|[C++ kodu ile Android ve Windows uygulamaları paylaşma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[C++ platformlar arası mobil geliştirme örnekleri](https://msdn.microsoft.com/library/dn707596.aspx) (MSDN Kitaplığı)|
|[C++ için ek platformlar arası mobil geliştirme örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Unity için Visual Studio araçları kullanarak Android, iOS ve Windows için platformlar arası oyun oluşturun

 Unity için Visual Studio Araçları, Visual Studio'nun güçlü kod düzenleme, üretkenlik ve hata ayıklama araçları ile tümleştirilir. Visual Studio için ücretsiz bir uzantı *Unity*, popüler platformlar arası oyun/grafik altyapısı ve Windows, iOS, Android ve web dahil olmak üzere diğer platformları hedefleyen modern uygulamalar için geliştirme ortamı.

 ![VSTU geliştirme ortamı](../cross-platform/media/vstu_overview.png "Unity genel bakış için Visual Studio Araçları")

 Visual Studio Araçları ile Unity (VSTU), oyun ve düzenleyici betikleri C# dilinde yazın ve ardından, güçlü bir hata ayıklayıcı hataları bulma ve düzeltme için Visual Studio kullanabilirsiniz. VSTU en son sürümünü Unity 2018.1 için destek getirir ve Unity'nın ShaderLab gölgelendirici dili için söz dizimi renklendirme, daha iyi eşitlemesi Unity, daha zengin hata ayıklama ve geliştirilmiş kod oluşturma için MonoBehavior Sihirbazı'nı içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.

|**Daha fazla bilgi edinin**|
|--------------------|
|[Unity Visual Studio ile oyun oluşturma hakkında daha fazla bilgi edinin](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Unity için Visual Studio Araçları hakkında daha fazla bilgi](../cross-platform/visual-studio-tools-for-unity.md) |
|[Unity için Visual Studio Araçları kullanmaya başlayın](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Son geliştirmeler hakkında Unity 2.0 önizlemesi için Visual Studio Araçları okuma](https://blogs.msdn.microsoft.com/visualstudio/2014/12/03/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blogu)|
|[Unity 2.0 önizlemesi için Visual Studio Araçları için bir tanıtım izleyin](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Unity hakkında bilgi edinin](http://unity3d.com/) (Unity Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Office 365 API'lerini bir Visual Studio projesine ekleme](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [Azure uygulama hizmetleri - mobil uygulamalar](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)