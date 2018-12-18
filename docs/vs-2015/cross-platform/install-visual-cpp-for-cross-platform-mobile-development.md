---
title: Visual C++ platformlar arası Mobil Geliştirme için yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c8cbe8992a1035e2fb4a26feb9a77b5546bfa56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786021"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Çoklu Platform Mobil Uygulama Geliştirme için Visual C++’ı yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ platformlar arası Mobil Geliştirme için] (http://go.microsoft.com/fwlink/p/?LinkId=536383) Visual Studio 2015'in yüklenebilir bileşendir. Platformlar arası Visual Studio şablonları içerir ve platformlar arası Araçlar ve SDK'lar bulun, indirmek ve bunları kendiniz yapılandırmak zorunda kalmadan hızla kullanmaya başlamak için yükler. Kolayca oluşturma, düzenleme, hata ayıklama ve test platformlar arası projeleri için Visual Studio'da bu araçları kullanabilirsiniz. Bu konuda Araçlar ve üçüncü taraf yazılım Visual Studio kullanarak platformlar arası uygulamalar geliştirmek için gereken nasıl yükleneceğini açıklar. Bileşen genel bakış için bkz. [Visual C++ platformlar arası mobil](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Gereksinimleri](#Requirements)   
 [Araçları edinin](#GetTheTools)   
 [Araçları yükleme](#InstallTheTools)   
 [İOS için araçları yükleme](#InstallForiOS)   
 [Yükleme veya bağımlılıkları el ile güncelleştirme](#ThirdParty)  
  
##  <a name="Requirements"></a> Gereksinimleri  
  
- Yükleme gereksinimleri için bkz [Visual Studio 2015 sistem gereksinimleri](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  >  Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, Klasik Windows uygulamaları, Android yerel etkinlik uygulamaları ve kitaplıkları ve uygulamaları için kodu ve kod kitaplıkları için iOS ve Windows Store veya evrensel Windows uygulamaları geliştirebilirsiniz.  
  
  Belirli cihaz platformları için uygulamalar oluşturmak için bazı ek gereksinimleri vardır:  
  
- Windows Phone öykünücüleri ve Android için Microsoft Visual Studio öykünücüsü, Hyper-V çalıştıran bir bilgisayar gerektirir. Windows Hyper-V özelliği yükleyip öykünücü çalıştırması önce etkinleştirilmesi gerekir. Öykünücü'nın daha fazla bilgi için bkz. [sistem gereksinimleri](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf).  
  
- X86 Android SDK'sı ile gelen Android öykünücüleri Intel HAXM sürücüsü çalıştıran bilgisayarlarda en iyi şekilde çalışır. Bu sürücü bir Intel x64 işlemci ile birlikte VT-x ve devre dışı Bit yürütme desteği gerektirir. Daha fazla bilgi için [yükleme yönergeleri için Intel® donanım hızlandırılmış yürütme Yöneticisi - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
- İOS için kod oluşturma gerektiren bir Apple kimliği, bir iOS Developer Program hesap ve çalıştırabileceğiniz bir Mac bilgisayara [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) veya daha sonra OS X Mavericks veya sonraki sürümler. Basit yükleme adımları için bkz: [yüklemek için iOS Araçları](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Araçları edinin  
 Platformlar arası Mobil Geliştirme için Visual C++, Visual Studio Community, Professional ve Enterprise sürümlerinde bulunan bir yüklenebilir bileşendir. Visual Studio almak için Git [Visual Studio 2015 indirmeleri](http://go.microsoft.com/fwlink/p/?linkid=517106) sayfasında ve Visual Studio 2015 güncelleştirme 2 veya üzeri indirin.  
  
##  <a name="InstallTheTools"></a> Araçları yükleme  
 Visual Studio 2015 için yükleyici Visual C++ platformlar arası Mobil Geliştirme için yüklemek için bir seçenek içerir. Bu, gerekli C++ dil araçları, şablonları ve Android derleme ve hata ayıklama ve bileşenleri için iOS geliştirme için bir Mac ile iletişim kurmak için gereken Visual Studio, GCC ve Clang araç takımları için bileşenleri yükler. Ayrıca, tüm iOS ve Android uygulaması geliştirme desteği için gerekli yazılım geliştirme setleri ve üçüncü taraf araçları yükler. Bu üçüncü taraf araçların çoğu Android platformu desteği için gerekli olan açık kaynaklı yazılımlardır.  
  
-   Android yerel Geliştirme Seti (NDK) Android platformunu hedefleyen C++ kod oluşturmak için gereklidir.  
  
-   Android SDK'sı, Apache Ant ve Java SE Development Kit Android yapı işlemi için gereklidir.  
  
-   Android için Microsoft Visual Studio öykünücüsü, test ve kod hatalarını ayıklamak için yararlı bir isteğe bağlı yüksek performanslı öykünücü ' dir.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Visual C++ platformlar arası mobil geliştirme ve üçüncü taraf araçları yüklemek için  
  
1.  Aşağıdaki bağlantıyı indirdiğiniz Visual Studio 2015 Yükleyicisi'ni çalıştırın [araçları edinin](#GetTheTools). İsteğe bağlı bileşenleri yüklemek için seçin **özel** yükleme türü olarak. Seçin **sonraki** yüklemek için isteğe bağlı bileşenleri seçin.  
  
2.  Özellikleri seçin alanında, genişletme **platformlar arası mobil geliştirme** ve **Visual C++ mobil geliştirme**.  
  
     ![Visual C seçin&#43; &#43; mobil geliştirme](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Seçtiğinizde varsayılan olarak **Visual C++ mobil geliştirme**, **programlama dilleri** yüklemek için seçeneği ayarlanır **Visual C++** ve **ortak Araçlar ve yazılım geliştirme setleri** seçenekleri gerekli üçüncü taraf bileşenleri yüklemek için ayarlanır. Eğer gerekiyorsa, ek bileşenleri seçebilirsiniz. Varsayılan olarak, **Android için Microsoft Visual Studio öykünücü** da seçilir. Zaten yüklü bileşenleri listesinde etkin olmayan görünür.  
  
     Evrensel Windows uygulamaları oluşturun ve bunları ve Android ve iOS projeleri arasında kod içinde paylaşmak için **özellikleri seçin**, genişletme **Windows ve Web geliştirme** ve **Evrensel Windows uygulaması Geliştirme Araçları**. Evrensel Windows uygulamaları oluşturmak planlamıyorsanız, bu seçenek atlayabilirsiniz.  
  
     Seçin **sonraki** devam etmek için.  
  
3.  Üçüncü taraf bileşenlerini, kendi lisans koşulları vardır. Lisans Koşulları'nı seçerek görüntüleyebilirsiniz **lisans koşulları** her bileşeninin yanındaki bağlantı. Seçin **yükleme** bileşenleri eklemek ve Visual Studio ve Visual C++ platformlar arası Mobil Geliştirme için yükleyin.  
  
4.  Yükleme tamamlandığında yükleyiciyi kapatın ve bilgisayarınızı yeniden başlatın. Bazı kurulum eylemleri üçüncü taraf bileşenleri için bilgisayar yeniden başlatılana kadar etkili olmaz.  
  
    > [!IMPORTANT]
    >  Her şeyin doğru şekilde yüklendiğinden emin olmak için yeniden başlatmanız gerekir.  
  
     Android bileşen için Microsoft Visual Studio öykünücü yüklenemedi, bilgisayarınızda Hyper-V etkin olmayabilir. Kullanım **kapatma Windows özelliklerini aç veya Kapat** Denetim Masası uygulaması Hyper-V ve ardından Visual Studio yükleyicisini yeniden çalıştırın.  
  
    > [!NOTE]
    >  Bilgisayarınız veya Windows sürümünüzü Hyper-V desteklemiyorsa, Microsoft Visual Studio öykünücüsü Android bileşeni için kullanamazsınız. Home Edition'ın Windows Hyper-V desteği içermez.  
  
5.  Visual Studio'yu açın. Bu, Visual Studio'yu çalıştırdığınız ilk kez ise, yapılandırma ve oturum açma için biraz zaman alabilir. Visual Studio olduğunda hazır üzerinde **Araçları** menüsünde **Uzantılar ve güncelleştirmeler**, **güncelleştirmeleri**. Visual Studio için Visual C++ platformlar arası Mobil Geliştirme için veya Microsoft Visual Studio öykünücüsü Android için güncelleştirmesi vardır, bunları yükleyin.  
  
##  <a name="InstallForiOS"></a> İOS için araçları yükleme  
 Platformlar arası Mobil Geliştirme için Visual C++, düzenleme, hata ayıklama ve iOS Simulator'a veya bir iOS cihazının iOS kod dağıtmak için kullanabilirsiniz, ancak lisans kısıtlamaları nedeniyle, kodu uzaktan Mac üzerinde oluşturulmalıdır Yapı ve Visual Studio kullanarak iOS uygulamaları çalıştırmak için ayarlayabilir ve Mac'inizde uzak Aracısı'nı yapılandırma Ayrıntılı yükleme yönergeleri, Önkoşullar ve yapılandırma seçenekleri için bkz: [yükleme ve yapılandırma araçları iOS kullanarak derlemeye](../cross-platform/install-and-configure-tools-to-build-using-ios.md). İOS için oluştururken değil, bu adımı atlayabilirsiniz.  
  
##  <a name="ThirdParty"></a> Yükleme veya bağımlılıkları el ile güncelleştirme  
 Bir yüklememeye karar veya daha fazla üçüncü taraf bağımlılıkları, Visual C++ mobil geliştirme seçeneği yüklediğinizde Visual Studio Yükleyicisi'ni kullanarak bunları daha sonra adımları kullanarak yükleyebileceğiniz [Araçları'nı yükleme](#InstallTheTools). Ayrıca, yükleme veya bunları bağımsız olarak Visual Studio güncelleştirme.  
  
> [!CAUTION]
>  Java dışındaki herhangi bir sırada bağımlılıklarını yükleyebilirsiniz. Yükleme ve Android SDK'yı yüklemeden önce JDK yapılandırmanız gerekir.  
  
 Aşağıdaki bilgileri okuyun ve bağımlılıkları el ile yüklemek için aşağıdaki bağlantıları kullanın.  
  
- [Java SE Geliştirme Seti](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Varsayılan olarak, yükleyici C:\Program Files (x86) \Java içinde Java araçları geçirir.  
  
- [Android SDK'sı](https://developer.android.com/sdk/index.html#Other)  
  
   Yükleme sırasında API'leri önerildiği şekilde güncelleştirin. En az olduğundan emin olun Android 5.0 Lollipop (API düzey 21) için SDK'sı yüklü. Varsayılan olarak, yükleyici Android SDK'sı C:\Program Files (x86) \Android\android SDK'da geçirir.  
  
   SDK Yöneticisi uygulama yeniden SDK'yi güncelleştirmek ve isteğe bağlı araçları ve ek API düzeylerini yüklemek için Android SDK dizininde çalıştırabilirsiniz. Güncelleştirmeleri kullanılmadıkça yükleme başarısız olabilir **yönetici olarak çalıştır** SDK Manager uygulamasını çalıştırmak için. Bir Android uygulaması oluşturma sorunları varsa, güncelleştirmeler, yüklü bir SDK'ları için SDK Yöneticisi'ni denetleyin.  
  
   Android SDK'sı ile gelen Android öykünücüleri bazılarını kullanmak için isteğe bağlı Intel HAXM sürücüleri yüklemeniz gerekir. Hyper-V özelliği başarıyla Intel HAXM sürücüleri yüklemek için Windows kaldırmak zorunda kalabilirsiniz. Android için Windows Phone öykünücüleri ve Microsoft Visual Studio öykünücü kullanmak için Hyper-V özelliğini geri yüklemeniz gerekir.  
  
- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Varsayılan olarak, yükleyici C:\ProgramData\Microsoft\AndroidNDK içinde Android NDK geçirir. Android NDK yüklemenize güncelleştirmeyi yeniden NDK yükleyip.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Varsayılan olarak, yükleyici C:\Program Files (x86) \Microsoft Visual Studio 14.0\Apps Apache Ant geçirir.  
  
- [Android için Microsoft Visual Studio öykünücüsü](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
   Yükleyebilir ve Visual Studio Galerisi Android için Microsoft Visual Studio öykünücü güncelleştirin.  
  
  Çoğu durumda, Visual Studio üçüncü taraf yazılım yükledikten ve iç ortam değişkenleri içindeki yükleme yolları tutar yapılandırmalarını algılayabilir. Platformlar arası geliştirme araçlarının Visual Studio IDE içindeki varsayılan yolları geçersiz kılabilirsiniz.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Üçüncü taraf araçları yollarını ayarlamak için  
  
1.  Visual Studio menü çubuğunda, seçin **Araçları**, **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusunda **Çoklu Platform**, **C++** seçip **Android**.  
  
     ![Android aracı yolu seçeneklerinin](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3.  Bir araç tarafından kullanılan yolu değiştirmek için yolun yanındaki onay kutusunu işaretleyin ve klasör yolu metin kutusuna düzenleyin. Gözat düğmesini de kullanabilirsiniz (**...** ) açmak için bir **konumu seçin** iletişim klasörünü seçin.  
  
4.  Seçin **Tamam** klasör konumlarını özel aracı kaydetmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İOS kullanarak derlemeye yönelik ve Yapılandırma Araçları'nı yükleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ platformlar arası mobil](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)

