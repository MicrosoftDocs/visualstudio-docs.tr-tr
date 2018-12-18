---
title: Visual C++ platformlar arası Mobil Geliştirme için yükleme | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dffe82511e75889ea588cb23b1f19490f991ab0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251913"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>C++ ile platformlar arası mobil geliştirme yükleyin

Android ve iOS için Windows Masaüstü uygulamaları, Evrensel Windows Platformu (UWP) uygulamaları, Linux uygulamaları ve artık, uygulamaları oluşturmak için Visual Studio'da C++ kullanabilirsiniz. **C++ ile Mobil Geliştirme** bileşenleri Visual Studio'da platformlar arası iOS, Android ve UWP için Visual Studio içeren yüklenebilir bir dizi iş yüküdür şablonları. Platformlar arası Araçlar ve SDK'lar bulun, indirmek ve bunları kendiniz yapılandırmak zorunda kalmadan hızla kullanmaya başlamak için ihtiyacınız yükler. Bu araçlar Visual Studio'da kullanmak kolayca oluşturma, düzenleme, hata ayıklama ve test, platformlar arası projeleri. Bu konuda, Araçlar ve üçüncü taraf yazılım kullanarak Visual Studio c++ platformlar arası uygulamalar geliştirmek için gereken yüklemeyi açıklar. Genel bakış için bkz. [Visual C++ platformlar arası mobil](https://go.microsoft.com/fwlink/p/?LinkId=536383)

## <a name="requirements"></a>Gereksinimler

- Yükleme gereksinimleri için bkz [Visual Studio ürün ailesi sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, Windows Masaüstü uygulamaları, Android yerel etkinlik uygulamaları ve kitaplıkları ve uygulamaları için kodu ve kod kitaplıkları için iOS ve Windows Phone değil veya UWP uygulamaları geliştirebilirsiniz.

Belirli cihaz platformları için uygulamalar oluşturmak için bazı ek gereksinimleri vardır:

- Windows Phone öykünücüleri ve Android için Microsoft Visual Studio öykünücüsü, Hyper-V çalıştıran bir bilgisayar gerektirir. Windows Hyper-V özelliği yükleyip öykünücü çalıştırması önce etkinleştirilmesi gerekir. Öykünücü'nın daha fazla bilgi için bkz. [sistem gereksinimleri](system-requirements-for-the-visual-studio-emulator-for-android.md).

- X86 Android SDK'sı ile gelen Android öykünücüleri Intel HAXM sürücüsü çalıştıran bilgisayarlarda en iyi şekilde çalışır. Bu sürücü bir Intel x64 işlemci ile birlikte VT-x ve devre dışı Bit yürütme desteği gerektirir. Daha fazla bilgi için [Intel® donanım hızlandırılmış yürütme Yöneticisi (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- İOS için kod oluşturma gerektiren bir Apple kimliği, bir iOS Developer Program hesap ve çalıştırabileceğiniz bir Mac bilgisayara [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) sürüm 6 veya daha sonra OS X Mavericks (sürüm 10.9) veya sonraki sürümler. Yükleme adımları bir bağlantı için bkz: [yüklemek için iOS Araçları](#install-tools-for-ios).

## <a name="get-the-tools"></a>Araçları edinin

C++ ile mobil geliştirme, Visual Studio Community, Professional ve Enterprise sürümlerinde kullanılabilir. Visual Studio almak için Git [Visual Studio indirmeleri](https://go.microsoft.com/fwlink/p/?linkid=517106) sayfası. Platformlar arası mobil geliştirme araçları, Visual Studio 2015 güncelleştirme 2 veya daha sonra başlayan kullanılabilir.

## <a name="install-the-tools"></a>Araçları yükleme

Visual Studio 2017 için Visual Studio Yükleyicisi'ni içeren bir **C++ ile Mobil Geliştirme** iş yükü C++ dil araçları, şablonları ve Visual Studio'da Android ve iOS geliştirme için gerekli bileşenleri yükler. GCC ve Clang araç takımları Android derleme ve hata ayıklama ve için iOS geliştirme için bir Mac ile iletişim kurmak için gereken bileşenleri yükler. Ayrıca, tüm iOS ve Android uygulaması geliştirme desteği için gerekli yazılım geliştirme setleri ve üçüncü taraf araçları yükler. Bu üçüncü taraf araçların çoğu Android platformu desteği için gerekli olan açık kaynaklı yazılımlardır.

- Android yerel Geliştirme Seti (NDK) Android platformunu hedefleyen C++ kod oluşturmak için gereklidir.

- Android SDK'sı, Apache Ant ve Java SE Development Kit Android yapı işlemi için gereklidir.

- Intel donanım hızlandırılmış yürütme Yöneticisi ve Google Android öykünücüsü isteğe bağlıdır, ancak önerilen bileşenleri. Geliştirme ve doğrudan bir Android cihazında hata ayıklama, ancak genellikle hata ayıklama için bir öykünücü masaüstünüzde kullanımı daha kolay olur. Microsoft, ayrı olarak yüklenebilir ve Android için bir Visual Studio öykünücüsü'nü de sağlar.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Visual Studio 2017'de C++ iş yükü ile Mobil Geliştirme yüklemek için

1. Çalıştırma **Visual Studio yükleyicisi** gelen **Başlat** menüsü.

1. Visual Studio'yu önceden yüklediyseniz, seçin **Değiştir** düğmesi için değiştirmek istediğiniz Visual Studio'nın yüklü sürümü. Aksi takdirde seçin **yükleme** Visual Studio'yu yüklemek için.

1. İle **iş yükleri** sekmesi seçili, aşağı kaydırın ve select **C++ ile Mobil Geliştirme** Visual Studio Yükleyicisi'nde iş yükü. Bu iş yükü seçildiğinde, C++ geliştirme için gereken diğer bileşenleri de seçilir. Ayrıca, diğer iş yükleri ve aynı anda yüklemek için tek tek bileşenleri de seçebilirsiniz. UWP hedefleyen platformlar arası kod oluşturmak için Seç **Evrensel Windows platformu geliştirme** iş yükü.

1. İçinde **Yükleme ayrıntıları** bölmesini genişletin **C++ ile Mobil Geliştirme**. İçinde **isteğe bağlı** bölümünde ek sürümleri NDK, Google Android öykünücüsü, Intel donanım hızlandırılmış yürütme Yöneticisi'ni seçebilirsiniz ve IncrediBuild derleme hızlandırma aracı.

1. Varsayılan olarak, bir veya daha fazla Android SDK Kurulumu bileşenleri iş yükü dahil edilir. Android SDK'sı ek sürümlerinde kullanılabilir. Yüklemenizi birine eklemek için **tek tek bileşenler** sekmesine ve ardından ekranı aşağı kaydırarak **SDK'lar, kitaplıklar ve çerçeveler** bölümü seçiminizi yapın.

1. Seçin **Değiştir** veya **yükleme** yüklemek için düğmesine **C++ ile Mobil Geliştirme** iş yükü ve diğer iş yükleri ve isteğe bağlı bileşenler seçildi.

   Yükleme tamamlandığında yükleyiciyi kapatın ve bilgisayarınızı yeniden başlatın. Bazı kurulum eylemleri üçüncü taraf bileşenleri için bilgisayar yeniden başlatılana kadar etkili olmaz.

   > [!IMPORTANT]
   > Her şeyin doğru şekilde yüklendiğinden emin olmak için yeniden başlatmanız gerekir.

1. Visual Studio'yu açın. Bu, Visual Studio'yu çalıştırdığınız ilk kez ise, yapılandırma ve oturum açma için biraz zaman alabilir. Visual Studio hazır olduğunda, tüm güncelleştirmeleri denetlemek ve bunları yükleyin.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Visual Studio 2015'te mobil geliştirme bileşeni ve üçüncü taraf araçları yüklemek için

Visual Studio 2015 kullanıyorsanız yükleyicisi Visual Studio 2015'te gerekli C++ dil araçları, şablonları ve bileşenleri yükler platformlar arası Mobil Geliştirme için Visual C++'ı yüklemek için bir seçenek içerir.

1. Visual Studio 2015 Yükleyicisi'ni çalıştırın. İsteğe bağlı bileşenleri yüklemek için seçin **özel** yükleme türü olarak. Seçin **sonraki** yüklemek için isteğe bağlı bileşenleri seçin.

1. İçinde **özellikleri seçin**, genişletme **platformlar arası mobil geliştirme** ve **Visual C++ mobil geliştirme**.

   ![Visual C seçin&#43; &#43; mobil geliştirme](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Seçtiğinizde varsayılan olarak **Visual C++ mobil geliştirme**, **programlama dilleri** yüklemek için seçeneği ayarlanır **Visual C++** ve **ortak Araçlar ve yazılım geliştirme setleri** seçenekleri gerekli üçüncü taraf bileşenleri yüklemek için ayarlanır. Eğer gerekiyorsa, ek bileşenleri seçebilirsiniz. Varsayılan olarak, **Android için Microsoft Visual Studio öykünücü** da seçilir. Zaten yüklü bileşenleri listesinde etkin olmayan görünür.

   Evrensel Windows uygulamaları oluşturun ve bunları ve Android ve iOS projeleri arasında kod içinde paylaşmak için **özellikleri seçin**, genişletme **Windows ve Web geliştirme** ve **Evrensel Windows uygulaması Geliştirme Araçları**. Evrensel Windows uygulamaları oluşturmak planlamıyorsanız, bu seçenek atlayabilirsiniz.

   Seçin **sonraki** devam etmek için.

1. Üçüncü taraf bileşenlerini, kendi lisans koşulları vardır. Lisans Koşulları'nı seçerek görüntüleyebilirsiniz **lisans koşulları** her bileşeninin yanındaki bağlantı. Seçin **yükleme** bileşenleri eklemek ve Visual Studio ve Visual C++ platformlar arası Mobil Geliştirme için yükleyin.

1. Yükleme tamamlandığında yükleyiciyi kapatın ve bilgisayarınızı yeniden başlatın. Bazı kurulum eylemleri üçüncü taraf bileşenleri için bilgisayar yeniden başlatılana kadar etkili olmaz.

   > [!IMPORTANT]
   > Her şeyin doğru şekilde yüklendiğinden emin olmak için yeniden başlatmanız gerekir.

   Android bileşen için Microsoft Visual Studio öykünücü yüklenemedi, bilgisayarınızda Hyper-V etkin olmayabilir. Kullanım **kapatma Windows özelliklerini aç veya Kapat** Denetim Masası uygulaması Hyper-V ve ardından Visual Studio yükleyicisini yeniden çalıştırın.

   > [!NOTE]
   > Bilgisayarınız veya Windows sürümünüzü Hyper-V desteklemiyorsa, Microsoft Visual Studio öykünücüsü Android bileşeni için kullanamazsınız. Home Edition'ın Windows Hyper-V desteği içermez.

1. Visual Studio'yu açın. Bu, Visual Studio'yu çalıştırdığınız ilk kez ise, yapılandırma ve oturum açma için biraz zaman alabilir. Visual Studio olduğunda hazır üzerinde **Araçları** menüsünde **Uzantılar ve güncelleştirmeler**, **güncelleştirmeleri**. Visual Studio için Visual C++ platformlar arası Mobil Geliştirme için veya Microsoft Visual Studio öykünücüsü Android için güncelleştirmesi vardır, bunları yükleyin.

## <a name="install-tools-for-ios"></a>İOS için araçları yükleme

Platformlar arası Mobil Geliştirme için Visual C++, düzenleme, hata ayıklama ve iOS Simulator'a veya bir iOS cihazının iOS kod dağıtmak için kullanabilirsiniz, ancak lisans kısıtlamaları nedeniyle, kodu uzaktan Mac üzerinde oluşturulmalıdır Yapı ve Visual Studio kullanarak iOS uygulamaları çalıştırmak için ayarlayabilir ve Mac'inizde uzak Aracısı'nı yapılandırma Ayrıntılı yükleme yönergeleri, Önkoşullar ve yapılandırma seçenekleri için bkz: [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md). İOS için oluştururken değil, bu adımı atlayabilirsiniz.

## <a name="install-or-update-dependencies-manually"></a>Yükleme veya bağımlılıkları el ile güncelleştirme

Bir yüklemeyi karar verirseniz veya yüklediğinizde Visual Studio Yükleyicisi'ni kullanarak daha fazla üçüncü taraf bağımlılıkları **C++ ile Mobil Geliştirme** iş yükü (veya Visual Studio 2015, Visual C++ mobil geliştirme seçeneği), bunları adımları kullanarak daha sonra yükleyebilirsiniz [Araçları'nı yükleme](#install-the-tools). Visual Studio Yükleyicisi'nin en son üçüncü taraf bileşenlerini yüklemek için düzenli olarak güncelleştirilir. Güncelleştirilmiş SDK'ları ve NDKs yüklemek için kullanabilirsiniz. Ayrıca, yükleme veya bunları bağımsız olarak Visual Studio güncelleştirme.

> [!CAUTION]
> Java dışındaki herhangi bir sırada bağımlılıklarını yükleyebilirsiniz. Yükleme ve Android SDK'yı yüklemeden önce JDK yapılandırmanız gerekir.

Aşağıdaki bilgileri okuyun ve bağımlılıkları el ile yüklemek için aşağıdaki bağlantıları kullanın.

- [Java SE Geliştirme Seti](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Varsayılan olarak, yükleyici Java araçları geçirir *C:\Program Files (x86) \Java*.

- [Android SDK'sı](https://developer.android.com/sdk/index.html#command-tools)

   Yükleme sırasında API'leri önerildiği şekilde güncelleştirin. En az olduğundan emin olun Android 5.0 Lollipop (API düzey 21) için SDK'sı yüklü. Varsayılan olarak, yükleyici Android SDK'sı geçirir *C:\Program Files (x86) \Android\android-sdk*.

   SDK Yöneticisi uygulama yeniden SDK'yi güncelleştirmek ve isteğe bağlı araçları ve ek API düzeylerini yüklemek için Android SDK dizininde çalıştırabilirsiniz. Güncelleştirmeleri kullanılmadıkça yükleme başarısız olabilir **yönetici olarak çalıştır** SDK Manager uygulamasını çalıştırmak için. Bir Android uygulaması oluşturma sorunları varsa, güncelleştirmeler, yüklü bir SDK'ları için SDK Yöneticisi'ni denetleyin.

   Android SDK'sı ile gelen Android öykünücüleri bazılarını kullanmak için isteğe bağlı Intel HAXM sürücüleri yüklemeniz gerekir. Hyper-V özelliği başarıyla Intel HAXM sürücüleri yüklemek için Windows kaldırmak zorunda kalabilirsiniz. Android için Windows Phone öykünücüleri ve Microsoft Visual Studio öykünücü kullanmak için Hyper-V özelliğini geri yüklemeniz gerekir. Daha fazla bilgi için [Android öykünücüsü donanım hızlandırma](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   Varsayılan olarak, yükleyici Android NDK geçirir *C:\ProgramData\Microsoft\AndroidNDK*. Android NDK yüklemenize güncelleştirmeyi yeniden NDK yükleyip.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Varsayılan olarak, yükleyici Apache Ant geçirir *C:\Program Files (x86) \Microsoft Visual Studio 14.0\Apps*.

- [Android için Microsoft Visual Studio öykünücüsü](https://aka.ms/vscomemudownload)

   Android için Microsoft Visual Studio öykünücüsü, test ve kod hatalarını ayıklamak için yararlı bir isteğe bağlı öykünücü ' dir. Sonra Android için sürüm Visual Studio öykünücüsü, Google Android öykünücüsünü güncelleştirdi Intel'in HAXM'si aracılığıyla donanım hızlandırmasını kullanmak için. Mümkün olduğunda, erişim için en son Android işletim sistemi görüntülerine ve Google Play hizmetleri sunar, hızlandırılmış Google'nın öykünücüsünü kullanmanızı öneririz.

Çoğu durumda, Visual Studio üçüncü taraf yazılım yükledikten ve iç ortam değişkenleri içindeki yükleme yolları tutar yapılandırmalarını algılayabilir. Platformlar arası geliştirme araçlarının Visual Studio IDE içindeki varsayılan yolları geçersiz kılabilirsiniz.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Üçüncü taraf araçları yollarını ayarlamak için

1. Visual Studio menü çubuğunda, seçin **Araçları** > **seçenekleri**.

1. İçinde **seçenekleri** iletişim kutusunda **Çoklu Platform** > **C++** > **Android**.

   ![Android aracı yolu seçeneklerinin](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Bir araç tarafından kullanılan yolu değiştirmek için yolun yanındaki onay kutusunu işaretleyin ve klasör yolu metin kutusuna düzenleyin. Gözat düğmesini de kullanabilirsiniz (**...** ) açmak için bir **konumu seçin** iletişim klasörünü seçin.

1. Seçin **Tamam** klasör konumlarını özel aracı kaydetmek için.

## <a name="see-also"></a>Ayrıca bkz.

- [Yükleme ve yapılandırma araçları kullanarak iOS oluşturmak için](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ platformlar arası mobil](https://go.microsoft.com/fwlink/p/?LinkId=536383)
