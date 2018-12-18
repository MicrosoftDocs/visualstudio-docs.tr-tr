---
title: Android ve iOS üzerinde OpenGL ES uygulaması derleme | Microsoft Docs
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
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4978c8196553dba5566ec63fbfcd133d06b6dd6f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733401"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Android ve iOS Üzerinde OpenGL ES Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ platformlar arası mobil geliştirme seçeneği için yükleme sırasında Visual Studio çözümleri ve iOS uygulamaları ve ortak kod paylaşma Android uygulamaları için projeler oluşturabilirsiniz. Bu konuda, bir basit bir iOS uygulamasının hem Android yerel etkinlik uygulaması oluşturan bir çözüm şablonu aracılığıyla size yol gösterir. C++ kodu, uygulamalar her platformda aynı animasyonlu döndürme küpünü görüntülemek için OpenGL ES kullanan ortak sahiptir. OpenGL ES (Embedded Systems veya GLES için OpenGL) bir 2D ve 3D grafikler mobil cihazlarda desteklenen API ' dir.  
  
 [Gereksinimleri](#req)   
 [Yeni bir OpenGLES uygulaması projesi oluşturma](#Create)   
 [Android uygulaması derleyebilir ve çalıştırabilirsiniz](#BuildAndroid)   
 [İOS uygulaması derleyebilir ve çalıştırabilirsiniz](#BuildIOS)   
 [Uygulamalarınızı özelleştirin](#Customize)  
  
##  <a name="req"></a> Gereksinimleri  
 İOS ve Android için OpenGL ES uygulama oluşturabilmeniz için önce tüm sistem gereksinimlerini karşılamanızın emin olmanız gerekir. Visual Studio 2015'te Visual C++ platformlar arası mobil geliştirme seçeneği için yüklemeniz gerekir. Gerekli üçüncü taraf araçları ve SDK'lar yüklemesine dahil ve Android için Visual Studio öykünücü yüklendiğinden emin olun. Daha fazla bilgi ve ayrıntılı yönergeler için bkz. [platformlar arası Mobil Geliştirme için Visual C++ yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Yapı ve test iOS uygulaması için bir Mac ihtiyaç duyarsınız bilgisayar, yükleme yönergelerine göre ayarlayın. İOS geliştirme için ayarlama hakkında daha fazla bilgi için bkz: [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a> Yeni bir OpenGLES uygulaması projesi oluşturma  
 Bu öğreticide, ardından oluşturabilir ve varsayılan uygulamasını Android için Visual Studio öykünücüsü'nün içinde çalıştırmak önce yeni bir OpenGL ES uygulaması projesi oluşturun. Ardından iOS için uygulama oluşturun ve uygulamayı iOS Simulator'da çalıştırmak.  
  
#### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Visual Studio'yu açın. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun **şablonları**, seçin **Visual C++**, **Çoklu Platform**ve ardından  **OpenGLES uygulaması (Android, iOS)** şablonu.  
  
3. Uygulama gibi bir ad verin `MyOpenGLESApp`ve ardından **Tamam**.  
  
    ![Yeni bir OpenGLES uygulaması projesi](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio, yeni bir çözüm oluşturur ve Çözüm Gezgini açılır.  
  
    ![Çözüm Gezgini'nde MyOpenGLESApp](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Yeni bir OpenGL ES uygulaması çözümü, üç kitaplık projeleri ve iki uygulama projeleri içerir. Kitaplık klasörüne bir paylaşılan kod projesi ve Paylaşılan koda başvuran iki platforma özgü projeler içerir:  
  
- **MyOpenGLESApp.Android.NativeActivity** uygulamanızı android'de yerel bir etkinlik olarak uygulayan basitleştirin ve başvurular içerir. Giriş noktalarının tutkal kodun uygulama içinde MyOpenGLESApp.Shared ortak paylaşılan kodu içeren Main.cpp öğesi alanlarındadır. Önceden derlenmiş üst bilgiler pch.h içinde var. Bu yerel etkinlik uygulaması projesi MyOpenGLESApp.Android.Packaging proje tarafından devralındığında bir paylaşılan kitaplık (.so) dosyasına derlenir.  
  
- **MyOpenGLESApp.iOS.StaticLibrary** MyOpenGLESApp.Shared paylaşılan kodu içeren bir iOS statik kitaplık (.a) dosyası oluşturur. MyOpenGLESApp.iOS.Application proje tarafından oluşturulan uygulamaya bağlıdır.  
  
- **MyOpenGLESApp.Shared** platformlar arasında çalışır paylaşılan kodu içerir. Önişlemci makroları platforma özgü kod koşullu derleme için kullanır. Paylaşılan kod proje başvurusu MyOpenGLESApp.Android.NativeActivity hem de MyOpenGLESApp.iOS.StaticLibrary tarafından seçilir.  
  
  Çözüm, Android ve iOS platformlara yönelik uygulamalar oluşturmak için iki proje vardır:  
  
- **MyOpenGLESApp.Android.Packaging** .apk dosyası dağıtım için bir Android cihaz veya öykünücü üzerinde oluşturur. Bu, kaynakları ve bildirim özelliklerini ayarladığınız yerdir AndroidManifest.xml dosyası içerir. Ayrıca, Ant yapı işlemini denetleyen build.xml dosyası içerir. Dağıtılan ve doğrudan Visual Studio'dan çalıştırma varsayılan olarak, başlangıç projesi olarak ayarlanır.  
  
- **MyOpenGLESApp.iOS.Application** kaynakları ve bir iOS uygulaması içinde MyOpenGLESApp.iOS.StaticLibrary bağlanan C++ statik kitaplık kodu oluşturmak için Objective-C Birleştirici kodlar içerir. Bu proje, Mac için Visual Studio ve uzak aracı tarafından aktarılan bir derleme paketi oluşturur. Bu proje oluşturduğunuzda, Visual Studio Mac uygulamanızı oluşturup komutları ve dosya gönderir.  
  
##  <a name="BuildAndroid"></a> Android uygulaması derleyebilir ve çalıştırabilirsiniz  
 Şablon tarafından oluşturulan çözüm Android uygulamasını varsayılan proje olarak ayarlar.  Derleme ve yükleme ve Kurulum doğrulamak için bu uygulamayı çalıştırın. İlk test için Android için Visual Studio öykünücüsü'nün yüklü cihaz profilleri bir uygulamayı çalıştırın. Başka bir hedef uygulamanızı test etmek isterseniz, hedef öykünücü yükleyin veya cihazı bilgisayarınıza bağlayın.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Derleme ve Android yerel etkinlik uygulaması çalıştırmak için  
  
1. Zaten seçili değilse, seçin **x86** gelen **çözüm platformları** aşağı açılan listesi.  
  
    ![Çözüm Platformu ayarlamak için x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    X86 için Android öykünücüsü Windows hedeflemek için kullanın. Bir cihaz hedefliyorsanız, cihaz işlemciye göre çözüm platformunu seçin. Varsa **çözüm platformları** seçin, listeyi görüntülenmiyorsa **çözüm platformları** gelen **Ekle/Kaldır düğmeleri** listeleyin ve ardından platformunuzu seçin.  
  
2. İçinde **Çözüm Gezgini**, MyOpenGLESApp.Android.Packaging projesi için kısayol menüsünü açın ve ardından **yapı**.  
  
    ![Android paketleme projesi derleme](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    Android kitaplığı ve Android uygulamasını paylaşılan için çıkış penceresine yapı işleminin çıkış görüntüler.  
  
    ![Android projeleri için derleme çıkışı](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. VS öykünücüsü Android telefon (x86) profilleri, dağıtım hedefi seçin.  
  
    ![Dağıtım hedefini seçin](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Diğer öykünücü yüklü veya bir Android cihazına bağlı, dağıtım hedef açılan listeden seçebilirsiniz. Uygulamayı çalıştırmak için yerleşik Çözüm Platformu hedef cihaz platformunu eşleşmesi gerekir.  
  
4. Hata ayıklamayı başlatmak için F5'e veya hata ayıklama olmadan Başlat için Shift + F5 tuşlarına basın.  
  
    Visual Studio öykünücü, yüklemek ve kodunuzu dağıtmak için birkaç saniye sürer başlatır. Android için Visual Studio öykünücüsü uygulamayı'nasıl göründüğü aşağıda gösterilmiştir.  
  
    ![Android öykünücüsünde çalışan uygulama](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Uygulama başlatıldıktan sonra kesme noktaları ayarlayın ve hata ayıklayıcı kodunuz içinde adım adım, Yereller inceleyin ve izlemek için kullanın.  
  
5. SHIFT + hata ayıklamayı durdurmak için F5 tuşuna basın.  
  
    Öykünücüyü çalıştırmak için devam eden ayrı bir işlemdir. Düzenleme, derleme ve kodunuzun birden çok kez aynı öykünücüye dağıtmak. Uygulamanızı öykünücü uygulama Koleksiyonu'na görünür ve bunu doğrudan buradan başlatılabilir.  
  
   C++ put oluşturulan Android yerel etkinlik uygulaması ve kitaplık projeleri Android platformu ile arabirim oluşturmak için "Yapıştırıcı" kod içeren bir dinamik kitaplık kodu paylaşılan. Bu, çoğu uygulama kodu kitaplıkta ve bildirimi, kaynaklar ve derleme yönergeleri paketleme projesi içerisine anlamına gelir. Paylaşılan kodun NativeActivity projedeki Main.cpp olarak çağrılır. Android NDK Geliştirici programına Android yerel etkinlik hakkında daha fazla bilgi için bkz [kavramları](https://developer.android.com/ndk/guides/concepts.html) sayfası.  
  
   Visual Studio Android platform araç takımını Clang kullanan NDK, kullanarak Android yerel etkinlik projeleri derler. Visual Studio için komut satırı anahtarları NativeActivity proje özelliklerinde eşleştirir ve derlemek için kullanılan seçenekler bağlantı ve hedef platformda hata ayıklama. Ayrıntılar için açık **özellik sayfaları** MyOpenGLESApp.Android.NativeActivity proje için iletişim kutusu. Komut satırı anahtarları hakkında daha fazla bilgi için bkz. [Clang derleyici kullanıcının el ile](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a> İOS uygulaması derleyebilir ve çalıştırabilirsiniz  
 İOS uygulama projesi oluşturulur ve Visual Studio'da düzenlenemez, ancak lisans kısıtlamaları nedeniyle, oluşturulan ve gerekir bir Mac'ten dağıtılan Visual Studio, proje dosyaları aktarmak ve derleme, dağıtım ve hata ayıklama komutları yürütmek için Mac bilgisayarda çalışan uzak bir aracı ile iletişim kurar. Ayarlayın ve Visual Studio ve Mac kullanarak iOS uygulaması oluşturmadan önce iletişim kurmak için yapılandırmanız gerekir. Ayrıntılı yönergeler için bkz. [yükleme ve yapılandırma araçları iOS kullanarak derlemeye](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Uzak aracı çalıştırmak ve Visual Studio Mac ile eşleştirildi sonra oluşturun ve yükleme ve Kurulum doğrulamak üzere iOS uygulamasını çalıştırın.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Derleme ve iOS uygulamasını çalıştırmak için  
  
1. Mac'inizde uzak Aracısı çalışıyor ve Visual Studio için Uzak Aracı eşleştirilir doğrulayın. Uzak Aracı başlatmak için bir Terminal uygulamasını penceresi açın ve girin `vcremote`. Daha fazla bilgi için [Visual Studio'da uzak aracı yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Vcremote çalıştıran Mac Terminal penceresi](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Zaten seçili değilse, seçin **x86** gelen **çözüm platformları** aşağı açılan listesi.  
  
    ![Çözüm Platformu ayarlamak için x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    X86 iOS simülatörü hedeflemek için kullanın. Bir iOS cihazı hedefliyorsanız, cihaz üzerinde (genellikle bir ARM işlemci) işlemciyi temel çözüm platformunu seçin. Varsa **çözüm platformları** seçin, listeyi görüntülenmiyorsa **çözüm platformları** gelen **Ekle/Kaldır düğmeleri** listeleyin ve ardından platformunuzu seçin.  
  
3. Çözüm Gezgini'nde MyOpenGLESApp.iOS.Application proje için kısayol menüsünü açın ve seçin **yapı**.  
  
    ![İOS uygulaması projesi oluşturmak](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    Çıkış penceresi iOS statik kitaplık ve iOS uygulaması için yapı işleminin çıkış görüntüler. Mac bilgisayarlarda, uzak aracı gösterir çalıştıran Terminal penceresinde, komut ve dosya etkinlik aktarın.  
  
    Mac bilgisayarınızda istenebilir, bir kod imzalama isteğini kabul edin. Devam etmek için izin ver'ı seçin.  
  
4. Seçin **iOS simülatörü** uygulamayı Mac üzerinde iOS Simulator'da çalıştırmak için araç çubuğunda Bu, simülatör başlatılması biraz sürebilir. Simülatörü çıktısını görmek için Mac'inizde öne getirmek zorunda kalabilirsiniz.  
  
    ![İOS simülatörü'üzerinde çalışan uygulama](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Uygulama başlatıldıktan sonra kesme noktaları ayarlayın ve Visual Studio hata ayıklayıcısını Yereller inceleyin, çağrı yığını görmek ve izlemek için kullanın.  
  
    ![İOS uygulama içinde kesme noktasında hata ayıklayıcı](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. SHIFT + hata ayıklamayı durdurmak için F5 tuşuna basın.  
  
    İOS Simulator Mac üzerinde çalışmaya devam eden ayrı bir işlemdir Düzenleme, derleme ve kodunuzun birden çok kez aynı iOS Simulator örneğine dağıtma. Dağıtıldıktan sonra kodunuzu doğrudan simülatörde çalıştırabilirsiniz.  
  
   Oluşturulan bir iOS uygulaması ve kitaplık projeleri yalnızca paylaşılan kod uygulayan bir statik kitaplıkta C++ kodu yerleştirin. Çoğu uygulama kodu, uygulama projesinde olur. Bu şablon projede paylaşılan kitaplık kodu çağrıları GameViewController.m dosyasında yapılır. İOS uygulamanızı oluşturmak için Visual Studio ile bir Mac üzerinde çalışan bir uzak istemci iletişimi gerektiren Xcode platform araç takımını kullanır  
  
   Visual Studio proje dosyalarını aktarır ve komutları Xcode kullanarak uygulamayı oluşturmak için uzak istemciye gönderir. Uzak istemci gönderir yapı durumu bilgileri Visual Studio dönün. Uygulama başarıyla oluşturdu, çalıştırın ve uygulamanın hatalarını ayıklamak için komutları göndermek için Visual Studio kullanabilirsiniz. Visual Studio hata ayıklayıcının iOS simülatörü çalışır mac'inizde veya bağlı bir iOS cihazında çalışan uygulama denetler. Visual Studio için komut satırı anahtarları StaticLibrary proje özelliklerinde eşleştirir ve oluşturmak için kullanılan seçenekler bağlantı ve hedef iOS platformunda hata ayıklama. Derleyici komut satırı seçeneği ayrıntılarını açın **özellik sayfaları** MyOpenGLESApp.iOS.StaticLibrary proje için iletişim kutusu.  
  
##  <a name="Customize"></a> Uygulamalarınızı özelleştirin  
 Paylaşılan C++ koduna eklemek veya ortak işlevselliği değiştirmek için değiştirebilirsiniz. Paylaşılan kod MyOpenGLESApp.Android.NativeActivity ve MyOpenGLESApp.iOS.Application projelerinde çağrıları eşleşecek şekilde değiştirmeniz gerekir. Önişlemci makroları, platforma özgü bölümler ortak kodunuzda belirtmek için kullanabilirsiniz. Önişlemci makrosu `__ANDROID__` Android için oluşturduğunuzda önceden tanımlanmış. Önişlemci makrosu `__APPLE__` iOS için oluşturduğunuzda önceden tanımlanmış.  
  
 Belirli proje platformu için IntelliSense görmek için bağlam değiştiricisi açılan Düzenleyicisi penceresinin üst gezinti çubuğunda projeyi seçin.  
  
 ![Proje bağlamı değiştiricisi açılan kutusunda Düzenleyicisi](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 IntelliSense sorunlarını geçerli projede kırmızı dalgalı çizgi ile işaretlenir. Diğer projelerde sorunları mor dalgalı çizgi ile işaretlenir. Varsayılan olarak, Visual Studio kod renklendirme veya IntelliSense için Java veya Objective-C dosyaları desteklemez. Ancak, yine de kaynak dosyaları değiştirebilir ve uygulama adınız, simge ve diğer uygulama ayrıntılarını ayarlamak için kaynakları değiştirin.

