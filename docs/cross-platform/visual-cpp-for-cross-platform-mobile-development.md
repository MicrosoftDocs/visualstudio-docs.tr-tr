---
title: Platformlar arası Mobil Geliştirme için Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dfa353c1ae49e938c74e6d209cc2957dff2352d
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251643"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Platformlar arası Mobil Geliştirme için Visual C++
Yerel C++ uygulamaları oluşturabileceğinizi iOS, Android ve Windows cihazları ve iOS, Android ve Windows için oluşturulan kitaplıklarda ortak kod paylaşın, kullanarak Visual C++ platformlar arası Mobil Geliştirme için. Yerel uygulamalar ile paylaşılan kitaplıklar ve platformlar arası geliştirme için ihtiyaç duyduğunuz araçları ve SDK'larını yükleyen Visual Studio 2015'te kullanılabilecek bir seçenek budur. Yüklendiğinde, iOS ve Android cihazlar ve platformlar, yanı sıra Windows, Windows Phone ve Xbox üzerinde çalışan kod oluşturmak için Visual C++ kullanabilirsiniz.  
  
 Birden çok platform için kod yazma can sıkıcı olabilir. Birincil geliştirme dillerini ve iOS, Android ve Windows için Araçlar, her platformda farklıdır. Ancak, tüm platformlar kod yazma, C++'da destekler. Platformlar arasında yeniden çekirdek kodu kullanılmasını sağlamak için kullanabileceğiniz ortak paydası budur. C++ programında yazılan yerel kod, iki daha fazla performansa sahip olabilir ve dayanıklı tersine mühendislik. Kod yeniden kullanımını, birden çok platform için uygulamalar oluştururken zaman ve çaba kaydedebilirsiniz.  
  
 Platformlar arası Mobil Geliştirme için Visual C++ kullanarak geliştirme, çeşitli avantajları vardır:  
  
1.  **Kolay yükleme.** Visual Studio yükleyicisi, edinme ve Android ve iOS için uygulama veya kitaplık oluşturmak için ihtiyacınız olan SDK'lar ve gerekli üçüncü taraf araçları yükler. Yapılandırma ve Kurulum, basit ve çoğunlukla otomatik.  
  
2.  **Bir güçlü ve bilindik yapı ortamı.** Kolayca paylaşılabilir platformlar arası çözümler ve projeler Visual Studio şablonları ile oluşturun. Tek bir ortak arabirim kullanarak tüm projelerde özelliklerini yönetin. Tüm kodunuzu Visual Studio düzenleyicisinde düzenleyin ve kod tamamlama ve hata vurgulama için yerleşik platformlar arası Intellisense'ten yararlanın.  
  
3.  **Birleştirilmiş bir hata ayıklama deneyimi.** Birinci sınıf hata ayıklama araçları, Visual Studio'da izleyin ve C++ kodu adımlayın Android cihazlar ve Öykünücüler, iOS simülatörleri ve cihazları ve Windows veya Windows Phone cihazları ve öykünücüleri dahil olmak üzere tüm platformlarda kullanın.  
  
## <a name="get-the-tools"></a>Araçları edinin  
 Visual C++ platformlar arası Mobil Geliştirme için Visual Studio 2015 ile birlikte gelen yüklenebilir bir seçenektir. Önkoşullar ve yükleme yönergeleri için bkz: [platformlar arası Mobil Geliştirme için Visual C++ yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). İOS için kod oluşturmak için ayrıca bir Mac bilgisayara ve Apple iOS Geliştirici hesabı gerekir. Daha fazla bilgi için bkz. [yükleme ve yapılandırma araçları kullanarak iOS derleme](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Kısa sürede gelir  
 Android veya iOS geliştirme kullanıma sunulacak, başlama konusunda bazı harika malzeme sahibiz. Visual Studio bir ifadesel ve özellikli bir geliştirme ortamıdır. Nasıl kullanılacağını öğrenmek için deneyin [Android geliştiricileri için Başlarken](/previous-versions/windows/apps/dn275875\(v=win.10\)) veya [iOS geliştiricileri için Başlarken](/previous-versions/windows/apps/jj657966\(v=win.10\)). Bu konular, Visual Studio ve Windows ve Windows Phone için platformlar arası uygulamalar geliştirmek ihtiyacınız olan kavramlar başlatacaktır. İOS ve Android için platformlar arası ilk uygulamanızı yazmaya başlamak için bkz: [Android ve iOS üzerinde OpenGL ES uygulaması derleme](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Platformlar arası Mobil Geliştirme için Visual C++ uygulamalarınızı başlamanıza yardımcı olmak için birkaç şablon içerir:  
  
-   OpenGLES 2 uygulaması (Android, iOS, Windows Evrensel)  
  
     Android yerel etkinlik uygulaması, bir iOS uygulaması ve paylaşılan bir C++ kod kitaplığı ile birlikte bir evrensel Windows uygulaması projeleri kümesi içeren bir çözüm oluşturur. Bu uygulamalar, platforma özgü kitaplıklar her uygulamada aynı dönen küp çizmek için ortak C++ OpenGL ES kod kullanılarak oluşturulan kullanın. Bu şablonun kullanılabilmesi için Visual Studio yüklediğinizde Evrensel Windows uygulama geliştirme araçları seçeneğini eklemeniz gerekir.  
  
-   Native-Activity uygulaması (Android)  
  
     Bir Android yerel etkinlik projesi olarak bir tam C++ OpenGL uygulaması oluşturur.  
  
-   OpenGLES uygulaması (Android, iOS)  
  
     Çözüm projeleri Android yerel etkinlik uygulaması hem bir iOS uygulaması oluşturmak için bir dizi oluşturur. Bu uygulamalar, platforma özgü kitaplıklar her uygulamada aynı dönen küp çizmek için ortak C++ OpenGL ES kod kullanılarak oluşturulan kullanın.  
  
-   Paylaşılan kitaplık (Android, iOS)  
  
     Paylaşılan projede ortak C++ kod kullanarak bir Android dinamik kitaplık (.so) dosyası ve bir iOS statik kitaplık (.a) dosyası oluşturmak için projeleri içeren bir çözüm oluşturur.  
  
-   Temel uygulama (Android, Ant)  
  
     Bir Android oluşturur Java kaynak kodu ve Ant yapı sistemi yalnızca kullanır "Hello, World" uygulaması projesi.  
  
-   Temel uygulama (Android, Gradle)  
  
     Bir Android oluşturur sistem Java kaynak kodu ve Gradle derleme yalnızca kullanır "Hello, World" uygulaması projesi.  
  
-   Temel kitaplık (Android, Ant)  
  
     Bir Android oluşturur Java kaynak kodu ve Ant yapı sistemi yalnızca kullanan "Hello, World" kitaplığı projesi.  
  
-   Temel kitaplık (Android, Gradle)  
  
     Bir Android oluşturur sistem Java kaynak kodu ve Gradle derleme yalnızca kullanan "Hello, World" kitaplığı projesi.  
  
-   Dinamik paylaşılan kitaplık (Android)  
  
     C++ kod kullanarak bir Android dinamik kitaplık (.so) dosyası oluşturur.  
  
-   OpenGLES 2 uygulaması (iOS)  
  
     Çözüm projeleri OpenGL ES 2 iOS uygulaması oluşturmak için bir dizi oluşturur. Uygulama, bir iOS uygulama dönen küp çizmek için C++ OpenGL ES kod içeren bir kitaplık kullanır. Bu uygulama, iOS uygulamanız C++ kitaplıkları içeri aktarma görmek için iyi bir başlangıç noktası olabilir.  
  
-   Statik kitaplık (Android)  
  
     Android için bir statik kitaplık oluşturmak için bir proje oluşturur. Yalnızca bir dinamik kitaplık bir Android uygulaması kullanabilirsiniz, ancak herhangi bir sayıda statik kitaplıklar bağlayabilirsiniz.  
  
-   Statik kitaplık (iOS)  
  
     İOS için bir statik kitaplık oluşturmak için bir proje oluşturur.  
  
-   Derleme görevleri dosyası projesi (Android)  
  
     Kendi Android derleme görevleri dosyası projeleri için proje sarmalayıcı oluşturur.  
  
## <a name="try-out-sample-code"></a>Kod örneğini deneyin  
 Windows, Android ve iOS uygulamaları kullanabileceğiniz ortak kod kitaplıkları oluşturma ve Android için eksiksiz bir yerel etkinlik uygulamaları oluşturma işlemini gösteren örnekleri indirin. Başlamak için bkz: [platformlar arası mobil geliştirme örnekleri](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
1.  [Platformlar arası Mobil Geliştirme için Visual C++'ı yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Yükleme ve yapılandırma araçları kullanarak iOS oluşturmak için](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Bir Android yerel etkinlik uygulaması oluşturma](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Android ve iOS üzerinde OpenGL ES uygulaması oluşturma](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Platformlar arası mobil geliştirme örnekleri](../cross-platform/cross-platform-mobile-development-examples.md)