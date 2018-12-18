---
title: Xamarin ortamınızı doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: fa7495673b1c063c210a86734811a34af8855740
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794354"
---
# <a name="verify-your-xamarin-environment"></a>Xamarin ortamınızı doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yükleyicileri tamamladıktan sonra (bkz [Kurulum ve yükleme](../cross-platform/setup-and-install.md)), her şeyi Xamarin geliştirme deneyimi hazır olduğunu doğrulamak için birkaç dakikanızı ayırın.  
  
 Bu doğrulamaları tamamladıktan sonra aşağıdaki izlenecek her ikisi de ya da yapabilirsiniz:  
  
-   [Visual Studio'da Xamarin.Forms ile uygulama oluşturmaya yönelik temel bilgileri öğrenin](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
-   [Visual Studio’da Xamarin kullanarak yerel kullanıcı arabirimi ile uygulama oluşturma](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Tüm platformlar  
 İlk olarak, seçin **Araçlar > Seçenekler**, genişletin **Xamarin > diğer**, tıklatıp **şimdi denetle** güncelleştirmeleri için bağlantı. Xamarin 4.0.3.214 kullanılmasını veya önceki lisans sorunlarını önlemek için daha sonra ihtiyacınız var.  
  
 Visual Studio kullanarak yeni bir Xamarin çözüm oluşturup **Dosya > Yeni proje**, sonra da iletişim kutusunda'i genişletin **şablonları > Diğer diller > Visual C# > platformlar arası**seçin  **Boş uygulama (yerel taşınabilir)**, Tamam'ı tıklatın. Bu çözüm bir paylaşılan taşınabilir sınıf kitaplığı projesi ve tek tek projeler ile Android, iOS ve Windows için oluşturur:  
  
 ![Boş uygulamadan yeni proje oluşturma sonuçlarını &#40;yerel taşınabilir&#41; şablon](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin doğrula 1")  
  
> [!NOTE]
>  Şablonları olan değil, görürseniz [eksik Xamarin projesi şablonlar? Bu deneyin](#missing) bu sayfanın alt kısmındaki.  
  
## <a name="android"></a>Android  
  
1. En son Android SDK araçlarının giderek yüklü olup olmadığını denetleyin **Araçlar > Android > Android SDK Yöneticisi** ve en yeni Android SDK Tools sürümü yükleme Android SDK platformunuzun Araçlar ve Android SDK derleme araçları bileşenleri. Her zaman en son Android API düzeyi yüklemek için gerekli olmadığını göz önünde bulundurun; ihtiyaç duyduğunuz API'yi hedeflemek istediğiniz platformu düzeyine bağlıdır. Genel olarak, Xamarin yüklendiğinde, platform düzeyi gerektiriyor yüklenir.  

2.  Android designer doğrula: Çözüm Gezgini'nde Android projeyi **Kaynakları > Düzen > Main.axml** dosya. (Bu dosya, doğrudan için Çözüm Gezgini'nde; aramayı deneyin görmüyorsanız, yalnızca Android projesi ve iOS projesinde bulunmaktadır.)  
  
    - "Android SDK yüklü olduğu çok eski" belirten bir hata alırsanız, tıklayın **açık Android SDK** bu iletiyi seçin ve en yeni SDK sürümü kullanılabilen araçlar olarak yüklemek için yukarıdaki 1. adımda. 
  
3.  Derleme ve öykünücü (veya cihaz) hata ayıklama doğrulama:  
  
    -   Çözüm Gezgini'nde Android projesine sağ tıklayıp **başlangıç projesi olarak ayarla**.  
  
         ![Başlangıç projesi seçeneği olarak ayarlanan Visual Studio](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin doğrula 2")  
  
    -   Hedef Android sürümü üzerinde temel bir uygun öykünücüyü seçin. bilgisayarınıza bağlı bir Android geliştirme cihazınız varsa, öykünücüleri burada listelenen de görürsünüz:  
  
        -   Windows 8 +: seçmek bir **VS Öykünücüsünden** tuşuna basarak hata ayıklayıcıyı başlatın ve aşağıda gösterildiği gibi Visual Studio'nun hata ayıklama açılır listede hedef **F5**. Daha fazla ayrıntı için [Karşınızda Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Visual Studio ALM blogu). Çalışmak için bkz öykünücü sorun karşılaşmanız halinde [Android için Visual Studio öykünücü sorun giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Seçerek ve öykünücüsü için yeni cihaz profilleri oluşturabilirsiniz **Araçlar > Android için Visual Studio öykünücüsü...** .  
  
             ![Hata ayıklama hedefi olarak Android için Visual Studio öykünücüsü'nü seçerek](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin doğrulayın 3")  
  
             Not: görmüyorsanız, **Araçlar > Android için Visual Studio öykünücüsü...**  menü seçeneğini öykünücü kendisini yüklü değil sahip olabilir. Git **Denetim Masası > Programlar ve Özellikler**seçin **Microsoft Visual Studio**, tıklatıp **değişiklik** için yükleyiciyi yeniden çalıştırın. Tıklayın **Değiştir** Yükleyicisi'nde kutusunu işaretlemeniz **platformlar arası mobil geliştirme > Android için Microsoft Visual Studio öykünücü**, tıklatıp **güncelleştirme**.  
  
        -   Windows 7 ve önceki sürümleri: açılan menü Android için Xamarin Player yerine seçin ve çalıştırmak için F5 tuşuna basın. Xamarin Player hakkında ayrıntılı bilgi için Aygıt Yöneticisi'ni ve sorun giderme ipuçları, okuma [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com).  
  
> [!NOTE]
>  Visual Studio'da Android öykünücü Yöneticisi'ni (AVD) düğmesini özellikle Google Android öykünücüsü'nü yapılandırmak için kullanılan Aygıt Yöneticisi'ni açar (show aşağıdaki), araç çubuğundaki varlığını fark edebilirsiniz.  Bu üzerinde Visual Studio öykünücüsü Android veya Xamarin Player profillerini yapılandırmak için her biri kendi Aygıt Yöneticisi'ni sahip, bir etkisi yoktur.  Bkz: [Karşınızda Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Visual Studio ALM blogu) ve [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com) Ayrıntılar için.  
> ![CrossPlat Xamarin doğrulayın 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin 7 doğrulayın")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1.  Windows Phone Tasarımcı doğrula: Windows Phone Çözüm Gezgini'nde projeyi **MainPage.xaml** dosya.  
  
2.  Derleme ve öykünücüsü veya bir cihazda hata ayıklama doğrulamak (Not: Bu adım veya bir internet paylaşımlı cihaz için Visual Studio Kurulumu ile yüklenen Windows Phone öykünücüsü sahip olması gerekir):  
  
    -   Çözüm Gezgini'nde Windows Phone projesine sağ tıklayıp **başlangıç projesi olarak ayarla**.  
  
    -   Seçin bir **öykünücüsü 8.1** hedefi ya da aşağıda gösterildiği gibi açılan hata ayıklama ve F5 tuşuna basarak hata ayıklayıcıyı başlatın eklenen bir cihazı Visual Studio'nun içinde.  
  
         ![Hata ayıklama hedefi olarak bir Windows Phone öykünücüsü'nü seçerek](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin 4 doğrulayın")  
  
    -   Sorun çalışma, okuma için öykünücü karşılaşmanız halinde [Windows Phone 8 öykünücüsü'nü sorun giderme](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1.  Ağ üzerinde kullanılabilir ve üzerinde açıklandığı gibi Visual Studio ile eşleştirilmiş Mac'inizde olduğundan emin olun [Mac bilgisayara bağlayarak](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com).  
  
2.  Görsel taslak Tasarımcı doğrula: iOS Çözüm Gezgini'nde projeyi **Main.storyboard** dosya. Visual Studio Mac üzerinde çalışan uzaktan Tasarımcı burada barındırma  
  
3.  Derleme ve hata ayıklama doğrulama:  
  
    1.  Çözüm Gezgini'nde iOS projesine sağ tıklayıp **başlangıç projesi olarak ayarla**.  
  
    2.  Seçin **iPhoneSimulator** hedefleyen Visual Studio'nun derleme açılan listeden, aşağıda gösterildiği gibi veya **iPhone** internet paylaşımlı cihaz varsa hedefleyin. Mac bilgisayarınızda, select Xcode hiçbir simülatörleri listede yoksa, başlatma **Xcode -> Tercihler**, tıklatıp **indirin**. Altında **bileşenleri** indirilebilir simülatör sürümleri görmeniz gerekir. Hata ayıklama için ek yönergeler için Xamarin'in üzerinde [hata ayıklama](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) sayfa (xamarin.com).  
  
         ![Hedef derleme iPhoneSimulator seçerek](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin 5 doğrulayın")  
  
    3.  Aşağıda gösterildiği gibi Visual Studio'nun hata ayıklama açılır listeden bir iPhone hedefini seçin ve F5 tuşuna basarak hata ayıklayıcıyı başlatın. Bu, simülatör burada Visual Studio'da hata ayıklama işlem sırasında uygulamayla etkileşim kuracağınızı Mac üzerinde çalıştırır. Bir fiziksel iPhone veya iPad Mac bilgisayara bağlı varsa, burada görünür ve bunun yerine seçebilirsiniz. Mac bağlantısı herhangi bir cihaz veya simülatör listelenen görmüyorsanız, yukarıdaki 1. adımda bağlantılı konu inceleyerek veya giderek kontrol **Araçları** >**iOS**  > **Xamarin Mac aracı**  
  
         ![Bir iPhone hata ayıklama hedefi seçme](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin 6 doğrulayın")  
  
    4.  Mac bilgisayara bağlayarak sorunlarla karşılaşırsanız, okuma [bağlantı sorunlarını giderme](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) (xamarin.com).  
  
    5.  Bir hata bildiren görürseniz "yüklü hiçbir sağlama profili yüklü iOS imzalama anahtarı aynı, aşağıdakileri yapın:  
  
        -   Apple kimliği hesabınızı Xcode Mac üzerinde açıklandığı eklendiğini denetlemek [hesabınızı eklemek için Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Hesabınızı ekledikten sonra hem Visual Studio hem de Xcode yeniden emin olun.  
  
             ![CrossPlat Xamarin doğrulayın 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin 8 doğrulayın")  
  
        -   İçinde iOS imzalama sekmesine iOS proje özelliklerinde paket, özel yetkilendirme alan etkin hata ayıklama yapılandırması boş olduğunu doğrulayın.  Not: yalnızca yukarıdaki hata iletisi karşılaştığınız varsa bu ayarı kaldırma denemeniz gerekir.  
  
##  <a name="missing"></a> Xamarin proje şablonları eksik olabilir mi? Bu deneyin  
 Doğrudan Xamarin Web sitesinden Xamarin'i yükleyin ve Visual Studio 2013'e sahipseniz ve yan yana Visual Studio 2015 yüklü değilse, şablonları eksik olabilir. Ancak düzeltmek kolaydır: etkinleştirmeniz yeterlidir **Xamarin için Visual Studio 2015** Xamarin Kurulum programı özelliği.  
  
1.  Denetim Masası'nda açın **programlar ve Özellikler**, seçin **Xamarin** öğesi ekleyin ve tıklayın **değişiklik**.  
  
2.  Görüntülenen Xamarin için Kurulum sihirbazındaki tıklayın **sonraki** ardından **değişiklik**.  
  
3.  Yüklemek için isteğe bağlı özelliklerin listesinde genişletin **Xamarin için Visual Studio 2015**, seçin **yerel sürücünüze yüklenecek**, tıklatıp **sonraki** eklemeye devam etme özelliği.

