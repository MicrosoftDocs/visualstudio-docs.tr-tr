---
title: Xamarin ile mobil geliştirme hakkında bilgi edinin | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 329c684dcc09a15ec86f80493d9f084e486b7cfe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733178"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Xamarin ile mobil geliştirme hakkında bilgi edinin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu konuda, platformlar arası mobil uygulamaları geliştirmeye Xamarin ile anlamanıza yardımcı olan genel bakış malzeme için yönlendirir. Henüz Visual Studio ve Xamarin yüklü değilse, başlangıç [Kurulum ve yükleme](../cross-platform/setup-and-install.md) işlemi ilk olarak, daha sonra dönmek burada yükleyicileri çalışırken bu kaynak ile çalışmak için.  
  
> [!NOTE]
>  Aksi belirtilmediği sürece, başlangıçta yalnızca bu doğrudan bağlı burada sayfalarını ve değil paketinizle sayfaları okuma öneririz. Bu liste tamamladıktan sonra yükleme işlemi hala çalışıyor, geri dönün ve diğer konu başlıklarını keşfedin çekinmeyin.  
>   
>  Ayrıca, "Temel" olarak işaretlenmiş başlıklara çekinmeyin ve "Daha yakından bakın" konulara daha sonra tekrar deneyin.  
  
## <a name="essentials-introduction-to-xamarin"></a>Temel bileşenleri: Xamarin giriş  
 *10-20 dakika*  
  
1.  [Visual Studio'da Xamarin ile Mobile Apps](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) birincil Xamarin özelliklerini çok kısa bir özetini sağlar.  
  
2.  [C# ve Visual Studio kullanılarak yapı platformlar arası mobil uygulamalar](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9 15m16s) ile Xamarin destekçisi, James Montemagno. İlk üç dakika kod tanıtımlar tarafından izlenen bir Xamarin genel bakış ' dir.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Hakkında temel bilgiler: Visual Studio ve Xamarin ortamı genel bakış  
 *5-15 dakika*  
  
- Visual Studio ve Xamarin ile Windows bilgisayarı iş çoğunu burada gerçekleştirirsiniz ' dir. Bu bilgisayar, doğrudan Windows ve Android uygulamaları geliştirin ve çalıştırın ve bir cihaz veya öykünücü üzerinde hata ayıklayın. Uzaktan da oluşturun, çalıştırın ve Mac aracılığıyla iOS uygulamalarının hatalarını ayıklama Visual Studio Windows bilgisayarda ayrıca iOS görsel taslak Tasarımcısı ve iOS simülatörü bağlanabilirsiniz.  
  
- Xcode ve Xamarin ile bir Mac derleme/imzalama olarak hizmet veren iOS uygulamaları için konak ve çalışma zamanı ortamı. Derlemeler için Visual Studio içinden iOS Windows bilgisayarda, bu Mac bilgisayara verilmiş; bir iOS uygulamasını Visual Studio'dan hata ayıklama sırasında iOS simülatöründe Mac veya doğrudan bağlı Mac için bir internet paylaşımlı cihaz üzerinde çalıştığı Bu durumda üzerinde veya yakınında Mac uygulaması ile etkileşim kurmak ve Visual Studio'da hata ayıklama deneyiminizi olması.  
  
  Bu ilişkileri aşağıda gösterilmiştir ve daha fazla bilgi edinebilirsiniz üzerinde iOS uygulamalarıyla çalışma hakkında [Visual Studio için Xamarin.ios'a giriş](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) (xamarin.com).  
  
  ![Xamarin ortamınızdaki Windows ve Mac'te geliştirme bilgisayarlar arasındaki ilişki](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin 1 öğrenin")  
  
## <a name="essentials-how-projects-are-structured"></a>Temel bileşenleri: Projeleri nasıl yapılanmıştır.  
 *10-30 dakika*  
  
1.  [Paylaşım kod seçeneklerini](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com). Taşınabilir sınıf kitaplıkları seçeneği en iyi kullanmadan yalnızca bu .NET tüm hedef platformlar arasında desteklenen API'lerini kullanarak destekleyen öneririz. Çoğu iş mantığı kod veritabanları, REST API çağrıları ve taşınabilir Xamarin bileşenleri çağrıları dahil olmak üzere, PCL kalır (bkz [daha yakından bakın: Xamarin bileşenleri](#components) sonunda, bu konuda). Xamarin.Forms ile yazılmış ortak UI kodunu da bir PCL'de bulunabilir.  
  
2.  (İsteğe bağlı) [Örnek olay incelemesi: Tasky](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/case_study-tasky/) (xamarin.com), tasarım ve tam özellikli bir uygulama verileri, veri erişimi ve iş katmanları ayıran paylaşılan kod için bir PCL projeyle yapılandırılması gibi yapısı için bazı en iyi uygulamaları açıklar.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Temel bileşenleri: yerel ve Xamarin.Forms UI katmanları  
 *10-40 dakika*  
  
 Xamarin yerel harika uygulamalar oluşturmak için iki yol sağlar: Xamarin yerel ve Xamarin.Forms.  
  
 Xamarin yerel her hedef platformu için ayrı bir kullanıcı Arabirimi kod yazma: iOS, Android ve Windows.  Bu yaklaşımda, doğrudan erişim sağlayan özelleştirilmiş bir kullanıcı Arabirimi deneyimi platform başına platforma özgü API var.  De yerel Tasarımcısı ve her platform için denetimleri ile ilgili kullanıcı arabirimini oluşturmaya yardımcı olmak için tam erişim var.  
  
 Xamarin.Forms, genelleştirilmiş bir taşınabilir sınıf kitaplığında tüm platformlar için paylaşılan kullanıcı Arabirimi katman yazmanızı sağlayan API kümesi sağlar.  Yerel bir görünüm sağlamak için her hedef platformda yerel denetimlere Xamarin.Forms işler.  Xamarin.Forms ile bir tasarımcı kullanmak yerine, C# ve XAML kullanarak kullanıcı Arabirimi oluşturun.  
  
 Önden almak için hangi yaklaşımın karar gerekmez; uygulamalar hem Xamarin.Forms, hem de Xamarin yerel bir birleşimini kullanarak uygulanabilir:  
  
- Oturum açma bilgileri gibi platformlarda benzer kullanıcı Arabirimi ve özellikleri sağlayan genel amaçlı ekranlar oluşturmak için Xamarin.Forms kullanın forms başvurun ve arama sonuçları.  
  
- Çeşitli özelleştirme özelliklerini Xamarin.Forms UI platform başına temelinde ayarlamak için kullanın. Bunlar, hem koddan kullanılabilir OnPlatform API ve özel görünüm oluşturma, var olan bir oluşturucu genişletme ve özel Oluşturucu Oluşturma XAML içerir.  
  
- Gerekirse, örneğin her platformun benzersiz kullanıcı Arabirimi özelliklerini kullanan ekranlar, yerel kamera yakalama ve görüntü işleme kullanan bir ekran oluşturmak için Xamarin yerel kullanın.  
  
  Platformlar arasında paylaşma ve platforma özgü düzenlemeler için özelleştirme özelliklerini kullanarak kullanıcı Arabirimi kodu ayarlamak için Xamarin.Forms çözümü her zaman başlamanızı öneririz. Tamamen platforma özgü ekranlar ihtiyacınız varsa, bunları ayrı ayrı Xamarin yerel kullanarak ekleyebilirsiniz.  
  
  Daha fazla bilgi için:  
  
1.  [Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/) (xamarin.com), kısa bir genel bakış ve avantajları ve dezavantajları Xamarin.Forms ve yerel UI katmanları (diğer bir deyişle, Xamarin.iOS ve Xamarin.Android) sağlar.  
  
2.  İlk üç dakika James Montemagno'nın video [Xamarin.Forms: yerel iOS, Android ve Windows uygulamaları C# ve XAML ile](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9 13m3s) başka bir genel bakış sağlar ve Tanıtımlar izlemeye devam edebilirsiniz.  
  
3.  (İsteğe bağlı) [Xamarin.Forms'a giriş](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/introduction-to-xamarin-forms/) (xamarin.com)  
  
4.  (İsteğe bağlı) Özelleştirme için OnPlatform kullanma örnekleri görmek [cihaz sınıfı](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) belgeleri (xamarin.com)  
  
5.  (İsteğe bağlı) [Çoklu Platform - mobil platformlar arasında paylaşım kullanıcı Arabirimi kod Xamarin.Forms ile](https://msdn.microsoft.com/magazine/dn904669.aspx) Jason Smith (MSDN dergisi) anahatları Xamarin.Forms, kendisi için ayrıntıları ele alınmıştır şirket içinde farklı özelleştirme seçenekleri tarafından [ Her platformda denetimleri özelleştirme](http://developer.xamarin.com/guides/xamarin-forms/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Derin Dalış: Emulator'lar ile hata ayıklama  
 *10-15 dakika*  
  
 Platformlar arası uygulamalarınızı fiziksel bir cihaz kullanmak zorunda kalmadan hata ayıklamak için aşağıdaki kullanmanız gerekir:  
  
1.  **Android öykünücüsü.** Kullandığınız Windows sürümüne bağlı olarak, ya da Microsoft Visual Studio öykünücüsü Android veya Xamarin ikisi için de hızlı performans sunar ve cihaz özellikleri çeşitli destek Player öneririz:  
  
    -   **Windows 8 + makineleri:** Microsoft'un kullanarak önerilir [Android için Visual Studio öykünücü](https://www.visualstudio.com/en-us/features/msft-android-emulator-vs.aspx), Visual Studio ile yüklenir.  [Android için Visual Studio öykünücü](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) video (Channel9, 5m55s), bir genel bakış ve tanıtım sunmaktadır.  
  
    -   **Windows 7 veya önceki/Mac OS X üzerinde çalışan Windows**: kullanın [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player) (xamarin.com).  
  
2.  **Apple iOS simülatörü.** Daha fazla bilgi edinmek için [iOS simülatörü ile çalışmaya başlama](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3.  **Microsoft'un Windows Phone öykünücüsü.** Daha fazla bilgi edinmek için [Windows Phone 8 için Windows Phone öykünücüsü](https://msdn.microsoft.com/library/dn632391.aspx).  
  
##  <a name="components"></a> Derin Dalış: Xamarin bileşenleri  
 *10 dakika*  
  
 Çok sayıda genişletilmiş özellikler, Xamarin bileşenleri ile Xamarin uygulamaları için kullanılabilir. Ücretsiz olarak kullanılabilir tam katalog bulabilirsiniz [ http://components.xamarin.com/ ](http://components.xamarin.com/), bileşenler için ek kullanıcı Arabirimi denetimleri, kimlik doğrulaması, Microsoft Azure gibi bulut hizmetlerini ve daha fazlasını içerir.

