---
title: Bir Android yerel etkinlik uygulaması oluşturma | Microsoft Docs
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
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6bc8d96c6207889f07ec6bf1257be3d620855fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731424"
---
# <a name="create-an-android-native-activity-app"></a>Android Yerel Etkinlik Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ platformlar arası mobil geliştirme seçeneği için yükleme sırasında Visual Studio 2015, tam olarak işlevsel Android yerel etkinlik uygulamaları oluşturmak için kullanılabilir. Android yerel Geliştirme Seti (NDK) çoğu saf bir C/C++ kod kullanarak Android uygulamanızı uygulama olanak tanıyan bir araç setidir. Bazı Java JNI kod ile Android'e etkileşim kurmak C/C++ kod izin vermek için bağlantılı görür. Android NDK ile Android API Düzey 9 yerel etkinlik uygulamaları oluşturma olanağı sundu. Yerel etkinlik kod Unreal Engine'i veya OpenGL kullanan oyunlar ve grafik kullanımı yoğun uygulamalar oluşturmak için yaygın olarak kullanılır. Bu konu OpenGL kullanan basit bir yerel etkinlik uygulaması oluşturulmasını adım yol gösterir. Ek konular, düzenleme, derleme, hata ayıklama ve yerel etkinlik kod dağıtma, geliştirici yaşam döngüsü ile yol.  
  
 [Gereksinimleri](#req)   
 [Yeni bir yerel etkinlik projesi oluşturma](#Create)   
 [Varsayılan Android yerel etkinlik uygulaması derleyebilir ve çalıştırabilirsiniz](#BuildHello)  
  
##  <a name="req"></a> Gereksinimleri  
 Android yerel etkinlik uygulaması oluşturmadan önce tüm sistem gereksinimleri karşılanıyor ve Visual Studio 2015'te Visual C++ mobil geliştirme seçeneği yüklü emin olmanız gerekir. Daha fazla bilgi için [platformlar arası Mobil Geliştirme için Visual C++ yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Gerekli üçüncü taraf araçları ve SDK'lar yüklemesine dahil ve Android için Microsoft Visual Studio öykünücü yüklendiğinden emin olun.  
  
##  <a name="Create"></a> Yeni bir yerel etkinlik projesi oluşturma  
 Bu öğreticide, önce yeni bir Android yerel etkinlik projesi oluşturma sonra oluşturun ve varsayılan uygulamasını Android için Visual Studio öykünücüsü'nün içinde çalıştırın.  
  
#### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Visual Studio'yu açın. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun **şablonları**, seçin **Visual C++**, **Çoklu Platform**ve ardından  **Native-Activity uygulaması (Android)** şablonu.  
  
3. Uygulama gibi bir ad verin `MyAndroidApp`ve ardından **Tamam**.  
  
    ![Yerel etkinlik proje oluşturma](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio, yeni bir çözüm oluşturur ve Çözüm Gezgini açılır.  
  
    ![Çözüm Gezgini'nde yerel etkinlik proje](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Yeni Android yerel etkinlik uygulaması çözümü iki proje içerir:  
  
-   **MyAndroidApp.NativeActivity** Birleştirici kodlar için uygulamanızı Android'de gibi yerel bir etkinlik çalışmasına ve başvurular içerir. Giriş noktaları tutkal kodun uygulamasını Main.cpp öğesi içinde var. Önceden derlenmiş üst bilgiler pch.h içinde var. Bu yerel etkinlik uygulaması projesi paketleme projesi tarafından devralındığında paylaşılan kitaplık bir .so dosyası derlenir.  
  
-   **MyAndroidApp.Packaging** .apk dosyası dağıtım için bir Android cihaz veya öykünücü üzerinde oluşturur. Bu, kaynakları ve bildirim özelliklerini ayarladığınız yerdir AndroidManifest.xml dosyası içerir. Ayrıca, Ant yapı işlemini denetleyen build.xml dosyası içerir. Dağıtılan ve doğrudan Visual Studio'dan çalıştırma varsayılan olarak, başlangıç projesi olarak ayarlanır.  
  
##  <a name="BuildHello"></a> Varsayılan Android yerel etkinlik uygulaması derleyebilir ve çalıştırabilirsiniz  
 Oluşturup yükleme ve Kurulum doğrulamak için şablon tarafından oluşturulan uygulamayı çalıştırın. Bu ilk test için Android için Visual Studio öykünücüsü'nün yüklü cihaz profilleri bir uygulamayı çalıştırın. Başka bir hedef uygulamanızı test etmek isterseniz, hedef öykünücü yükleyin veya cihazı bilgisayarınıza bağlayın.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Derleme ve varsayılan yerel etkinlik uygulaması çalıştırmak için  
  
1.  Zaten seçili değilse, seçin **x86** gelen **çözüm platformları** açılır liste.  
  
     ![Çözüm platformları x86 açılan liste seçimine](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Varsa **çözüm platformları** seçin, listeyi görüntülenmiyorsa **çözüm platformları** gelen **Ekle/Kaldır düğmeleri** listeleyin ve ardından platformunuzu seçin.  
  
2.  Menü çubuğunda, **derleme**, **Çözümü Derle**.  
  
     Çıkış penceresi çözümde iki proje için yapı işleminin çıkış görüntüler.  
  
3.  VS öykünücüsü Android telefon (x86) profilleri, dağıtım hedefi seçin.  
  
     Diğer öykünücü yüklü veya bir Android cihazına bağlı, dağıtım hedef açılan listeden seçebilirsiniz.  
  
4.  Hata ayıklamayı başlatmak için F5'e veya hata ayıklama olmadan Başlat için Shift + F5 tuşlarına basın.  
  
     Varsayılan Uygulama Visual Studio öykünücüsü'nde Android için nasıl göründüğüne aşağıda verilmiştir.  
  
     ![Öykünücü, uygulamanızı çalıştıran](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio öykünücü, yüklemek ve kodunuzu dağıtmak için birkaç saniye sürer başlatır. Uygulama başlatıldıktan sonra kesme noktaları ayarlayın ve hata ayıklayıcı kodunuz içinde adım adım, Yereller inceleyin ve izlemek için kullanın.  
  
5.  SHIFT + hata ayıklamayı durdurmak için F5 tuşuna basın.  
  
     Öykünücüyü çalıştırmak için devam eden ayrı bir işlemdir. Düzenleme, derleme ve kodunuzun birden çok kez aynı öykünücüye dağıtmak.

