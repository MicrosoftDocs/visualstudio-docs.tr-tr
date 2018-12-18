---
title: Kurulum ve yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: f3a72c197963332ad433f88e6cb7fffde5a9a41b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730405"
---
# <a name="setup-and-install"></a>Kurulum ve yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yerel iOS, Android ve Windows oluşturmak için uygulamalardan genel C# / .NET kod tabanı kullanarak Xamarin, aşağıdakiler gerekir:  
  
- Windows ve Android uygulamaları ile çalışmak için: bir Windows geliştirme bilgisayarında Visual Studio 2015 ile ve (aşağıda Not Xamarin 4 yüklü bakın). (Visual Studio 2013 için yönergeleri takip ederek de kullanabilirsiniz [doğrudan Xamarin yükleme](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).)   
  
- İOS uygulamalarıyla çalışmak için: bir Mac OS X Yosemite (10.10.5) veya üstünde, XCode ve Xamarin yüklü.  
  
  Windows ve Mac bilgisayarları aynı anda ayarlayabilirsiniz ve bu yükleyiciler çalışırken geçtiğiniz [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md) okuyup gerekli arka plan bilgilerini izleyin.  
 
Bu kurulum ve yükleme yaptıktan sonra Xamarin kullanarak sorunları varsa, sorunuzu gönderin [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  31 Mart 2016 ' tüm Xamarin dahil ile gibi hiçbir ek Visual Studio'nun tüm sürümlerinde, maliyet ve ayrı bir lisans gerekmez. Mac için Xamarin Studio Community, ayrıca Öğrenciler, OSS geliştiricileri ve küçük takımlar için ücretsizdir. Not ile önceki Xamarin lisanslarını yapılandırılan mevcut yüklemelerinde Visual Studio'nun Xamarin 4.0.3.214 sürümüne güncelleştirmeniz gerekir ya da daha yüksek. Bunu yapmak için Git **Araçlar > Seçenekler > Xamarin > diğer**, tıklayın **şimdi denetle** bağlantı ve indirme 4.0.3.214 güncelleştirme. Visual Studio'yu yeniden başlatın, Git **Araçlar > Xamarin hesabı...**  güncel durumunu görmeniz gerekir.  
  
 **Bu konuda:**  
  
-   [Ön koşullar](#prereq)  
  
-   [Windows Kurulum (Visual Studio ve Xamarin)](#windows)  
  
-   [Mac kurulumu (Apple kimliği, Xcode ve Xamarin)](#mac)  
  
##  <a name="prereq"></a> Ön koşullar  
  
1.  Windows ve Android hedeflemek için:  
  
    1.  Önerilen: bir Android cihazınız yoksa hızlı kullanımına izin verir, Windows 8 veya sonraki sürümü çalıştıran fiziksel Windows bilgisayarı (VM değil) Hyper-V Visual Studio öykünücüsü için Android tabanlı. (Biz bir fiziksel bilgisayar ve bir VM gerekir söylemiş miydik?)  
  
    1.  Windows 7 veya önceki bir bilgisayarı kullanabilir, bu durumda Xamarin Player Android için öykünücüsü olarak kullanacaksınız. 
    
    1. Her iki yapılandırma için her zaman doğrudan bağlı fiziksel cihazlarda uygulamaları çalıştırabilirsiniz.  
  
1.  İOS hedeflemek için:  
  
    1.  Bir ağ Mac veya Mac OS X Yosemite 10.10.5 OS X çalıştıran mini veya üzeri (Xcode 7.1 için gereklidir).  
  
    1.  Visual Studio, bir Windows (7 +) bilgisayarda birincil geliştirme ortamı olarak kullanırken, bir ağ bağlantılı mac'e yalnızca derleyin ve iOS uygulamalarında hata ayıklama, iOS simülatörü veya tethered cihazları bağlayın ve Visual Studio için görsel taslak Tasarımcısı'nı kullanmak için gereklidir kullanıcı arabirimi tasarlama. Eski Mac modelleri tamamen ikincil bu rol için yeterlidir.  
  
##  <a name="windows"></a> Windows Kurulum (Visual Studio ve Xamarin)  
  
> [!TIP]
>  Bu yönergeler, Visual Studio 2015 için geçerlidir. Xamarin ile Visual Studio 2013 kullanmak için (güncelleştirme 2 gereklidir) yönergelerini izleyin [doğrudan Xamarin yükleme](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1. [İndirin ve herhangi bir sürümünü Visual Studio 2015 için yükleyiciyi başlatın](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) (Community, Professional veya Enterprise). Visual Studio 2015 Community ücretsiz bir sürümüdür; Professional ve Enterprise sürümleri 30 gün sonra bir lisans satın almanız gerekecektir deneme olarak kullanılabilir.  
  
   1.  Zaten Visual Studio yüklü değilse açın **Denetim Masası > Programlar ve Özellikler**, seçin **Visual Studio 2015** öğesi ekleyin ve tıklayın **değişiklik**. Yükleyici açıldığında tıklayın **Değiştir** ve aşağıdaki 3. adımına geçin.  
  
2. (Yalnızca yeni yükler) Yükleyici içinde seçin bir **özel** yükleyin:  
  
    ![Visual Studio Kurulumu içinde özel seçeneğini seçerken](../cross-platform/media/cross-plat-xamarin-setup-1.png "çapraz-Plat Xamarin Kurulum 1")  
  
3. Aşağıdaki kutuları işaretleyin:  
  
   1.  **Platformlar arası mobil geliştirme > C# / .NET (Xamarin)**. Bu, yaygın kullanılan araçlar ve yazılım geliştirme setleri altında çeşitli Android araçları da otomatik olarak seçer. Bu seçenek var olan bir Xamarin yüklemesini de güncelleştirmeniz gerekir.  
  
        ![Xamarin seçeneğini altında çapraz&#45;Platform mobil geliştirme](../cross-platform/media/cross-plat-xamarin-setup-2.png "çapraz-Plat Xamarin Kurulum 2")  
  
   2.  Windows 8 +: **platformlar arası mobil geliştirme > Android için Microsoft Visual Studio öykünücüsü**. Not: bir Windows 7 veya önceki bir bilgisayar kullanarak veya Windows çalıştıran bir Mac bilgisayarda, bu olduğundan emin olun *denetlenmeyen*. "Windows bilgisayarlarda öykünücüleri hakkında not" 5. adım sonra bakın. Yalnızca fiziksel Android cihazlarda hata ayıklamak istiyorsanız, siz de bu işaretlenmemiş olarak bırakabilirsiniz.  
  
   3.  (İsteğe bağlı) Windows cihazları hedefleyen üzerinde planlıyorsanız, ayrıca denetleyin **Windows ve Web geliştirme > Evrensel Windows uygulama geliştirme araçları** ve/veya **Windows 8.1 ve Windows Phone 8.0/8.1 Araçları**. Bu indirme daha uzun sürer öykünücü görüntüleri yükleme seçenekleri içerir. Ayrıca, daha sonra eklemek için Visual Studio yükleyicisi her zaman geri dönebilirsiniz.  
  
4. Yükle düğmesine tıklayın ve çalıştırma işlemi sağlar. Yeniden, bu süre içerisinde Mac kurulum yönergeleri ile devam edin ve Git tamamlanması biraz zaman alabilir [Xamarin ile mobil geliştirme hakkında bilgi edinin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Yükleme tamamlandıktan sonra Visual Studio ve Microsoft hesabınızla oturum istenirse başlatın (Windows ile kullandığınız hesapla aynıdır). Xamarin aracılığıyla güncelleştirmeleri daha sonra denetleyin **araçları > Seçenekler > Xamarin** veya **araçları > Seçenekler > Xamarin > diğer**, burada bulabilirsiniz bir **şimdi denetle** bağlantı:  
  
    ![Xamarin güncelleştirmeleri Visual Studio seçenekleri](../cross-platform/media/cross-plat-xamarin-setup-3.png "çapraz-Plat Xamarin Kurulum 3")  
  
   > [!NOTE]
   >  Daha önce belirtildiği gibi önceki Xamarin lisans sorunları önlemek için daha yüksek veya Xamarin 4.0.3.214 sürümüne güncelleştirmek emin olun.  

   Xamarin için bir seçenek görmüyorsanız **Araçlar > Seçenekler**yüklemenizi denetleyin veya Visual Studio'yu yeniden başlatmayı deneyin. Seçenekler iletişim kutusunda Xamarin için arama da yapabilirsiniz.
      
6. Mac'te önceki ya da çalışan Windows ve Windows 7 kullanan [Android SDK öykünücüsü](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) fiziksel cihazlar yoksa. Aşağıdaki nota bakın.  
  
   **Windows bilgisayarlarda öykünücüleri ilgili Not:** CPU aynı anda yalnızca bir sanallaştırma teknolojisi desteklediğinden, yalnızca biri kullanımda geliştirme bilgisayarında yüklü en iyisidir. Hyper-V (Android ve Windows Phone öykünücüsü için Visual Studio öykünücüsü tarafından kullanılan), Virtual Box (Genymotion tarafından kullanılır) ve (Android SDK öykünücüsü tarafından kullanılan) Intel HAXM teknolojilerdir üç ana virtualizations vardır. Hyper-V ve Virtual Box arasında çeşitli sorunları nedeniyle herhangi belirli bir bilgisayarda, bu nedenle, yalnızca bir öykünücü kullanmak için en iyi, Hyper-V, Windows 8 ve üzeri bilgisayarlar ve Windows 7 öykünücülerde Intel HAXM kullanmak için yukarıdaki ve ne zaman yanı sıra önceki öneriler yazın. Windows çalıştıran bir Mac üzerinde  
  
##  <a name="mac"></a> Mac kurulumu (Apple kimliği, Xcode ve Xamarin)  
  
1.  Ücretsiz bir Apple kimliği Oluştur [ https://appleid.apple.com ](https://appleid.apple.com/) zaten yoksa. Bu, yükleme ve Xcode ile imzalama gereklidir.  
  
2.  Xcode'dan yükleyip [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/), ve Apple Kimliğinizi üzerinde açıklandığı gibi ekleyin [hesabınızı eklemek için XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  İndirme ve yönergeleri izleyerek Xamarin yükleme [yükleme ve yapılandırma Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Xamarin hem Windows hem de Mac bilgisayarlara yükleme işlemini tamamladıktan sonra yönergeleri takip edin [Mac bilgisayara bağlayarak](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com) Windows bilgisayarda iOS ve Mac Visual Studio'dan ile çalışabilirsiniz.  
  
     Her iki bilgisayar aynı yerel ağda olması gerektiğini unutmayın.

