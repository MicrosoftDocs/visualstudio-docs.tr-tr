---
title: Android için Visual Studio öykünücüsü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: af3dd595b786c57983e44982fa2eb8b9afa2959a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300775"
---
# <a name="visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Android için Visual Studio öykünücüsü, Android cihazına öykünen bir masaüstü uygulamasıdır. Fiziksel bir cihaz olmadan Android uygulamalarında hata ayıklamanıza ve test yapabilmeniz için sanallaştırılmış bir ortam sağlar. Ayrıca, uygulama prototiplerinizi için yalıtılmış bir ortam sağlar.  
  
 Android için Visual Studio öykünücüsü, gerçek bir cihaza benzer bir performans sağlamak üzere tasarlanmıştır. Ancak uygulamanızı yayımlamadan önce, uygulamanızı fiziksel bir cihazda sınamanızı öneririz.  
  
 Uygulamanızı, Android için Visual Studio öykünücüsü tarafından desteklenen Android platformları, ekran çözünürlükleri ve diğer donanım özellikleri için benzersiz bir cihaz profilinde test edebilirsiniz.  
  
 Bu konuda aşağıdaki bölümler yer almaktadır.  
  
- [Yükleme ve kaldırma](#Installing)  
  
- [Sistem gereksinimleri ve geri uyumluluk](#Requirements)  
  
- [Android için Visual Studio öykünücüsü 'nde ağ oluşturma](#Networking)  
  
- [Android için Visual Studio öykünücüsü 'nü yapılandırma](#Configuring)  
  
- [Öykünücüde test edebilirsiniz özellikleri](#FeaturesTest)  
  
- [Öykünücüde test etemiyorum Özellikler](#FeaturesNonTest)  
  
- [Destek kaynakları](#Support)  
  
## <a name="installing-and-uninstalling"></a><a name="Installing"></a> Yükleme ve kaldırma  
 Yükleme  
  
 Android için Visual Studio öykünücüsü, Visual Studio 'da bulunan platformlar arası araçların bir bileşenidir ve platformlar arası mobil geliştirme, ortak araçlar ve yazılım geliştirme setleri ' ni ve ardından Android için Visual Studio öykünücüsü ' nü seçtiğinizde özel bir Visual Studio Kurulumu sırasında yüklenecektir.  
  
 Kaldırıyor  
  
 Denetim Masası 'ndaki Program Ekle/Kaldır 'ı kullanarak Android için Visual Studio öykünücüsü ' nü kaldırabilirsiniz.  
  
> [!NOTE]
> Visual Studio 'Yu kaldırmak, öykünücüyü kaldırmaz. Öykünücüyü ayrı olarak kaldırmanız gerekir.  
  
 Android için Visual Studio öykünücüsü 'nü kaldırdığınızda, öykünücü için oluşturulan Hyper-V sanal Ethernet bağdaştırıcıları otomatik olarak kaldırılmaz. Hyper-V Yöneticisi 'Ni açıp öykünücü VHD görüntülerinden birini seçerek, ağ sekmesini seçerek ve bu sekmede görünen anahtarların her biri için **Kaldır** ' ı seçerek bu sanal bağdaştırıcıları (kullanımda değilse) el ile kaldırabilirsiniz.  
  
## <a name="system-requirements-and-backward-compatibility"></a><a name="Requirements"></a> Sistem gereksinimleri ve geri uyumluluk  
 Android için Visual Studio öykünücüsü donanım, yazılım ve yapılandırma gereksinimleriyle ilgili önemli bilgiler için aşağıdaki konuya bakın.  
  
- [Android için Visual Studio Öykünücüsü Sistem Gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Android için Visual Studio öykünücüsü, Visual Studio 2015 gerektirir; Visual Studio 'nun önceki sürümleriyle geriye dönük olarak uyumlu değildir.  
  
  Öykünücünün yeni sürümleri eski sürümlerin üzerine yüklenir (ve bazı durumlarda eski görüntülerin yerini alarak, bu görüntülerde yüklü ayarları, uygulamaları ve dosyaları atarak).  
  
## <a name="networking-in-the-visual-studio-emulator-for-android"></a><a name="Networking"></a> Android için Visual Studio öykünücüsü 'nde ağ oluşturma  
 Android için Visual Studio öykünücüsü ağ bağlantısı, bu özelliklerle bir masaüstü bilgisayar bağlantısı gibi davranır:  
  
- Öykünücü ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür.  
  
- Öykünücü ile henüz yüklenmemiş ek bir ağ yazılımı gerektirmez.  
  
- Bir Windows etki alanına katılmadı.  
  
  Öykünücü ağ bağlantısının yeteneklerini anlamak için, Android telefonunuzdaki bir Wi-Fi bağlantısına aynı ağa benzer şekilde göz önünde bulundurun. Telefonunuzdaki çalışan bir uygulama, Wi-Fi bağlantısı üzerinden bir ağ kaynağına erişebildi, öykünücü üzerinde çalışan bir uygulama aynı ağ kaynağına da erişebilir.  
  
  Ağ gereksinimleriyle ilgili daha fazla bilgi için bkz [. Android Için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Ağ sorunlarını giderme hakkında bilgi için bkz. [Android Için Visual Studio öykünücüsü sorunlarını giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
## <a name="configure-the-visual-studio-emulator-for-android"></a><a name="Configuring"></a> Android için Visual Studio öykünücüsü 'nü yapılandırma  
 Android uygulamanızı kademelendirme çok sayıda Android donanımında uyumluluk için test etmek zor olabilir. Pazardaki Android telefonlar ve tabletler, çok çeşitli sürüm ve ekran boyutlarına sahiptir ve birçok farklı donanım yapılandırmasında (RAM, CPU, mimari, vb.) gelir. Android için Visual Studio öykünücüsü, cihaz profillerini kullanarak bunu basitleştirir. Cihaz profillerimiz, Samsung, Motorola, Sony, LG ve daha fazlasına ait cihazlar dahil olmak üzere pazardaki en popüler donanımı temsil etmektedir.  
  
 Visual Studio 2015 ' de, öykünücü yöneticisi 'Ni kullanarak cihaz profillerini yükleyebilir, kaldırabilir ve başlatabilirsiniz. **Araçlar**' ı ve ardından **Android Için Visual Studio öykünücüsü**' nü seçerek öykünücü yöneticisine erişin.  
  
 ![Android için Visual Studio öykünücüsü yöneticisi](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 Varsayılan olarak, beyaz metin ve simgelerle gösterildiği gibi önceden yüklenmiş dört cihaz profili (KitKat ve Lollipop telefonu/5 "ve tablet/7" yapılandırması) vardır. **Profil yükleme** düğmesini seçinceye ve yükleme tamamlanıncaya kadar listedeki diğer profiller gri görünür. Listeyi API düzeyine göre filtreleyebilir ve tam yapılandırma ayrıntılarını görüntülemek için bir profilin sağ alt tarafındaki Ayrıntılar okuna tıklayabilirsiniz.  
  
 Hedeflemek istediğiniz profil kümesini yükledikten sonra, yeşil **yürütme** düğmesine basarak bu yeni profilleri doğrudan yöneticisinden başlatabilirsiniz. Ayrıca, Visual Studio platformlar arası mobil proje türündeki hata ayıklama hedefi açılan menüsünde de görüntülenir.  
  
## <a name="features-that-you-can-test-in-the-emulator"></a><a name="FeaturesTest"></a> Öykünücüde test edebilirsiniz özellikleri  
 Öykünücüde test edebilirsiniz özellikleri hakkında ayrıntılı bilgi için bu [belgelere](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)bakın.  
  
## <a name="features-that-you-cant-test-in-the-emulator"></a><a name="FeaturesNonTest"></a> Öykünücüde test etemiyorum Özellikler  
 Aşağıdaki liste, öykünücü içinde test **etemen** Android platformunun özelliklerini açıklar. Bu özellikleri fiziksel bir cihazda test etmeniz gerekir.  
  
- Pusula  
  
- Jiroskop  
  
- Titreşim denetleyicisi  
  
- Parlaklığı. Öykünücünün parlaklık düzeyini değiştirmek, cihazın ekranınızda görünme biçimini görsel olarak etkilemez.  
  
## <a name="support-resources"></a><a name="Support"></a> Destek kaynakları  
 Ana bilgisayarınız sistem gereksinimlerini karşılıyorsa ve bu sorun giderme kılavuzunda kapsanmayan bir sorunla karşılaşırsanız:  
  
- [Android-Emulator](https://stackoverflow.com/questions/tagged/android-emulator) ve Visual-Studio etiketini kullanarak StackOverflow 'de soru sorun.  
  
- Visual Studio 'da veya öykünücü yöneticisinde gülümseme Gönder aracını kullanarak bir sorun bildirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Android için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Android için Visual Studio Öykünücüsü’nde Sorun Giderme](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
