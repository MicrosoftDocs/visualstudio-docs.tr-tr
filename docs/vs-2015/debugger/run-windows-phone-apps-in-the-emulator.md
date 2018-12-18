---
title: Öykünücüde Windows Phone uygulamaları çalıştırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7035e4a77b67fb5207f878c8e0650236afda7c6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739979"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Öykünücüde Windows Phone uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Phone öykünücü hata ayıklama ve fiziksel bir cihaz olmadan bilgisayarınızdaki Windows Phone uygulamalarını test etmek için sanallaştırılmış bir ortam sağlar. Ortak dokunma ve döndürme olaylarının benzetimini yapma ve fiziksel ekran boyutunu ve taklit etmek istediğiniz çözümü seçin. Ayrıca, konum, ağ, bildirimler, sensörlerden, ivme ölçer ve isteğe bağlı bir SD kart gibi birçok yaygın olarak kullanılan özellik test edebilirsiniz.  
  
 Öykünücüde test etme özellikleri hakkında daha fazla bilgi için bkz. [uygulama özelliklerini Windows Phone öykünücüsü'nde Test](http://msdn.microsoft.com/en-us/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Visual Studio ile birlikte öykünücü içinde tasarlayabilir, geliştirme, hata ayıklama ve Windows Phone uygulamalarını test etmek için eksiksiz bir ortam sağlar.  
  
##  <a name="BKMK_run"></a> Bir Windows Phone uygulaması öykünücüde çalıştırma  
 Windows Phone Uygulama geliştirirken olsa da, Windows Phone öykünücüsü dağıtın ve uygulamanızı hızlı bir şekilde test etmek için kullanabilirsiniz. Windows Phone Store uygulamanızı yayımlamadan önce uygulamanızın gerçek bir Windows Phone cihazında ancak sınamanızı öneririz. Bu, kullanıcıların bu deneyimi gibi uygulama deneyimi sağlar.  
  
 Bir Windows Phone uygulaması Windows Phone öykünücüsü ilk kez çalıştırdığınızda, aşağıdaki olaylar gerçekleşir:  
  
1. Öykünücü başlatılır.  
  
2. Öykünücüyü Windows Phone işletim sistemi yükler.  
  
3. Öykünücüyü Windows Phone başlangıç ekranı görüntüler.  
  
4. Uygulamanızı öykünücüde dağıtılır.  
  
5. Uygulamanızı öykünücü üzerinde çalışır.  
  
   Seçilen öykünücü zaten çalışıyorsa, uygulamanızı dağıtılan ve çalışan öykünücüde başlatıldı. Her öykünücü yalnızca bir örneği aynı anda çalıştırabilirsiniz.  
  
> [!TIP]
>  Emulator'da uygulamanızı test ederken öykünücü açık olarak bırakın ve yeniden hızlı bir şekilde uygulamanızı çalıştırabilmeniz için hata ayıklama oturumları arasında.  
  
###  <a name="BKMK_vs"></a> Uygulamayı Visual Studio'dan çalıştırma  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Dağıtma ve uygulamayı Visual Studio'dan çalıştırma  
  
1.  Visual Studio'da bir Windows Phone projesini açın.  
  
2.  Üzerinde **standart** araç öykünücü seçeneklerden birini belirleyin.  
  
     ![Windows Phone öykünücü görüntüleri](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3.  Dağıtma ve hata ayıklama ile uygulamanız üzerinde çalıştırma **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat**, veya F5 tuşuna basın.  
  
     Dağıtma ve hata ayıklama olmadan uygulamanız üzerinde çalıştırmak için **hata ayıklama** menüsünde tıklatın **hata ayıklama olmadan Başlat**, ya da Ctrl + F5 tuşlarına basın.  
  
     Uygulamanız dağıtıldıktan ve başlatıldı.  
  
     Üzerinde çalıştırmadan uygulamanızı dağıtmak için **derleme** menüsünde tıklatın **çözüm dağıtma**.  
  
##### <a name="to-stop-a-running-app"></a>Çalışan uygulamayı durdurmak için  
  
- Çalışan uygulamayı durdurmak için aşağıdakilerden birini yapın:  
  
  - Visual Studio'da üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Durdur**, veya Shift + F5 tuşlarına basın.  
  
  - Öykünücüde basın **geri** uygulamadan çıkmak için düğme. Uygulamanın etkin sayfa uygulama başlangıç sayfası başarısız olduysa, basmanız gerekebilir **geri** birden çok kez düğmesi.  
  
    Uygulama çıkışından ve başlangıç ekranı açılır. Bu, geçerli hata ayıklama oturumu sona erer.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Hata ayıklama olmadan bir uygulamayı yeniden başlatmanız  
  
1.  Öykünücüde, başlangıç ekranında uygulama listesini görüntülemek için geçirme kalmadı.  
  
2.  Uygulama listesi, uygulama simgesine dokunun. Uygulamayı hata ayıklama olmadan yeniden başlatır.  
  
##### <a name="to-deactivate-a-running-app"></a>Çalışan bir uygulamanın devre dışı bırakmak için  
  
1.  Uygulamanızı çalıştırmadan önce Visual Studio'daki Çözüm Gezgini'nde projeye sağ tıklayın ve ardından **özellikleri** açmak için **Proje Tasarımcısı**.  
  
2.  İçinde **Proje Tasarımcısı**, **hata ayıklama** sayfasında **silinmiş öğe işareti devre dışı bırakma, hata ayıklama sırasında üzerine** bir etkinliği olmayan gitmek için bir uygulama istiyorsanız denetlenmeyen kutuyu durumuna devre dışı bırakıldı. Uygulamayı devre dışı olduğunda kaldırıldı olmasını istiyorsanız onay kutusunu işaretleyin.  
  
3.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**, veya uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Öykünücüde basın **Başlat** düğmesi. Başlangıç ekranı görünür ve uygulama devre dışı bırakılır. Uygulama ya da bir etkinliği olmayan durumuna geçtiğinde veya ayarına bağlı olarak kaldırıldı **silinmiş öğe işareti devre dışı bırakma, hata ayıklama sırasında üzerine** onay kutusu.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Bir etkinliği olmayan veya kaldırıldı uygulaması yeniden etkinleştirmek için  
  
-   Öykünücüde basın **geri** uygulamaya döndürülecek düğmesi. Diğer sayfalara çıkıldığında veya başka bir uygulama açılır, basmanız gerekebilir **geri** uygulamayı yeniden etkinleştirmek için birden çok kez düğmesi.  
  
     Hata ayıklama oturumu devam ettirir. Hata ayıklayıcı uygulamadan ayrılmış, hata ayıklama oturumu sürdürmek için F5'e olabilir.  
  
###  <a name="BKMK_depltool"></a> Uygulama dağıtımı aracı ile uygulamayı çalıştırma  
 Windows Phone uygulama dağıtımı aracı da kullanabilirsiniz (**AppDeploy.exe**) uygulamanızı öykünücüde çalıştırma için. Bu araç, Windows Phone geliştirme araçları yüklediğinizde, yüklü olduğu tek başına bir uygulamadır.  
  
 Daha fazla bilgi için bkz. [dağıtma Windows Phone 8.1 uygulamaları ile uygulama dağıtımı aracı](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a> Öykünücü araç ile Windows Phone öykünücüsü'nü yapılandırma  
 Bu tabloda öykünücü araç çubuğunda kullanılabilir yapılandırma düğmeleri gösterilir.  
  
|Araç çubuğu düğmeleri|Yapılandırma seçenekleri|  
|---------------------|---------------------------|  
|![Windows Phone öykünücüsü araç çubuğundaki seçenekleri giriş](../debugger/media/wp-emulator.png "WP_Emulator_")|**Tek noktası veya çok noktası erişimini yapılandırma**<br /><br /> Giriş çok nokta etkinleştirdiğinizde, dokunma ekran dokunmadan taşımak için sağ tıklayabilirsiniz. Ardından, aynı anda hem dokunma taşımak için sol.|  
|![Windows Phone öykünücüsü araç çubuğu üzerinde yön](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Öykünücü yönlendirmesini yapılandırma**<br /><br /> Windows Phone öykünücüsü yönde üç yönleri birini değiştirebilirsiniz: dikey, yatay sol veya sağ yatay. Öykünücü boyutunu, yönünü değiştirdiğinizde değiştirmez.<br /><br /> Verilerin yönünü değiştirmek için tıklayın **Sola Döndür** düğmesini veya **Sağa Döndür** düğmesi.|  
|![Windows Phone öykünücüsü araç çubuğundaki seçenekleri boyut](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Öykünücü boyutunu yapılandırma**<br /><br /> Ana bilgisayar ekranında öykünücü boyutunu değiştirebilirsiniz. Nokta / inç (DPI) öykünücüsü yakınlaştırma değerinden bağımsız olarak konak İzleyicisi DPI dayanır.<br /><br /> -Öykünücü ekrana sığacak şekilde tıklayın **ekrana Sığdır** düğmesi.<br />-Yakınlaştırma ayarını değiştirmek için tıklayın **yakınlaştırma** düğmesi. **Yakınlaştırma** iletişim kutusu açılır. İçinde **yakınlaştırma** iletişim kutusunda, 33 ile 100 arasında bir yakınlaştırma değeri girin.|  
  
##  <a name="BKMK_buttons"></a> Öykünücü üzerinde sanal donanım düğmeleri kullanın  
 Bir telefonun donanım düğmelerinin kullanımını öykünücü ekranın sağ tarafında sanal donanım düğmeleri kullanarak benzetimini yapar.  
  
- Tıklayın **güç** görünen açılıp kapatılması benzetimini yapmak için düğme. ' A tıklayın ve telefon kapatma benzetimini yapmak için basılı tutun.  
  
- Tıklayın **birim yukarı** veya **birim aşağı** telefon aramaları ve bildirimler için telefonun Konuşmacı hacmi değiştirme benzetimini yapmak için düğme.  
  
- **Kamera** düğme kamera uygulamayı başlatır. Bir fotoğraf veya bir video kamera uygulamada denetimler kullanılarak alma benzetimini yapabilirsiniz.  
  
  Aşağıdaki ekran görüntüsünde sanal donanım düğmeleri gösterilir.  
  
1. Sol resmi öykünücü üzerinde başlangıç ekranı görüntüler.  
  
2. Ortadaki görüntü dokunma sonra öykünücüyü görüntüler **güç** ekranı kapatmak için düğme.  
  
3. Doğru görüntüye dokunma sonra öykünücü ekranında görüntüler **birim yukarı** birim artırmak için düğme.  
  
   ![Windows Phone öykünücüsü düğmelerini](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Öykünücü ile bilgisayar klavyeyi kullanma  
 Öykünücü, geliştirme bilgisayarınızda bir Windows Phone klavyede donanım klavye eşleme destekler. Anahtarları davranışını bir Windows Phone cihazında aynıdır.  
  
 Varsayılan olarak, donanım klavye etkin değil. Bu uygulama, kullanabilmeniz için önce dağıtılmış olması gereken bir kayan klavye eşdeğerdir. Donanım klavye etkinleştirmeden önce öykünücünün anahtar girişini yalnızca denetim anahtarları kabul eder.  
  
 Klavyedeki Windows geliştirme bilgisayarında yerelleştirilmiş bir sürümünü, özel karakterler öykünücüsü tarafından desteklenmez. Yerelleştirilmiş klavyede bulunan özel karakterleri girmek için yazılım giriş paneli (SIP) kullanın.  
  
 Öykünücüde bilgisayarınızın klavyeyi kullanmak için PAGE UP veya PAUSE/BREAK tuşuna (Windows 8/8.1 öykünücünüzde) ya da F4 tuşuna basın (Windows 10 öykünücü).  
  
 Öykünücüde, bilgisayarın Klavyesi kullanılmadan durdurmak için PAGE DOWN veya PAUSE/BREAK tuşuna (Windows 8/8.1 öykünücünüzde) ya da F4 tuşuna basın (Windows 10 öykünücü).  
  
 Aşağıdaki tabloda, tuşlarını düğmeleri benzetmek için kullanabileceğiniz bir donanım ve Windows Phone diğer denetimler listeler.  
  
|Bilgisayar donanım anahtarı|Windows Phone donanım düğmesi|Notlar|  
|---------------------------|-----------------------------------|-----------|  
|F1|GERİ|Uzun basma işlemlerine beklendiği gibi çalışmayabilir.|  
|F2|BAŞLANGIÇ|Uzun basma işlemlerine beklendiği gibi çalışmayabilir.|  
|F3|ARAMA||  
|F4|Windows 10 öykünücüsünde yerel bilgisayarın Klavyesi kullanılmadan değil ve yerel bilgisayarın Klavyesi kullanılmadan arasında geçiş yapar.|Windows 8/8.1 öykünücüsü geçerli değildir.|  
|F5|Yok.||  
|F6|KAMERA YARI|Olan sürenin yarısına ulaşıldığında basıldığında adanmış kamera düğme.|  
|F7|KAMERA TAM|Adanmış kamera düğme.|  
|F8|Yok.||  
|F9|BİRİMİ||  
|F10|BİRİM AŞAĞI||  
|F11|Yok.||  
|F12|GÜÇ|Kilit ekranında iki kez etkinleştirmek için F12 tuşuna basın.<br /><br /> Uzun basma işlemlerine beklendiği gibi çalışmayabilir.|  
|ESC|GERİ|Uzun basma işlemlerine beklendiği gibi çalışmayabilir.|  
|PAUSE/BREAK|İki durumlu klavye (yalnızca windows 8/8.1 öykünücüsü).|Windows 10 öykünücüsü için geçerli değildir.|  
|AYARLAMA SAYFASI|Donanım klavye (yalnızca Windows 8/8.1 öykünücünüzde) sağlar.|Windows 10 öykünücüsü için geçerli değildir.|  
|SAYFA AŞAĞI|Donanım klavye (yalnızca Windows 8/8.1 öykünücünüzde) devre dışı bırakır.|Windows 10 öykünücüsü için geçerli değildir.|  
  
##  <a name="BKMK_checkpoints"></a> Kaydetme ve özel kontrol noktaları yükleme  
 Öykünücü'nın durumunun bir anlık görüntüsünü kullanarak kaydedin **kontrol noktaları** öykünücü'nın sekmesinde **ek araçlar**. Bu özellik, sık sık aynı verileri ve ayarları ile uygulamanızı test yararlıdır.  
  
 Örneğin, uygulamanızı birkaç kişi gerektiriyorsa, kişi kayıtlarını bir kez oluşturun ve bir anlık görüntüsünü öykünücüsü. Aksi takdirde öykünücü her başlattığınızda kişi kayıtlarını yeniden oluşturmanız gerekir.  
  
- Tıklayın **yeni bir kontrol noktası** öykünücü ile verileri ve uygulamanızı daha sonra yeniden test etmek için gereken ayarları durumunun yeni bir anlık görüntü yakalamak için. Yeni bir kontrol noktası eklenen **kontrol noktaları** listesi.  
  
   Öykünücüde hata ayıklayıcı bağlıyken bir denetim noktası yakalama gerçekleştiremez.  
  
- Bir denetim noktasında seçin **kontrol noktaları** denetim noktası hakkında bilgileri görüntülemek için liste.  
  
- Radyo düğmesini işaretleyin **varsayılan** kaydedilmiş bir denetim noktası etkin ve öykünücüsü için varsayılan denetim noktası yapmak için sütun.  
  
- Tıklayın **geri** öykünücüyü Windows Phone işletim sisteminde yeniden başlatmak ve seçili anlık görüntü yüklemek için.  
  
- Tıklayın **Sil** artık ihtiyacınız olmayan bir anlık görüntü silinemedi.  
  
  Özgün öykünücü görüntüsü, listedeki ilk öğe olarak her zaman görünür **kontrol noktaları** listelemek ve silinmiş veya değiştirilemez. Ancak, başka bir anlık görüntü varsayılan öykünücü görüntüsü seçebilirsiniz.  
  
  ![Windows Phone öykünücüsü'nü kontrol noktaları sekmesinde](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Ekran görüntüleri öykünücüsünde yakalama  
 Windows Phone uygulamalarınızın ekran görüntülerini ek araçlar penceresinden ekran aracını kullanarak oluşturabilirsiniz. Aracı, çalışan öykünücüsü çözümleme eşleşen PNG dosyaları oluşturur.  
  
 ![Ekran görüntüleri Windows Phone öykünücüsü](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Yerleşik öykünücü ekran aracını kullanarak bir uygulama ekran görüntüsü oluşturmak için  
  
1. Ekran görüntüleri kalitesini iyileştirmek için öykünücü yakınlaştırma seviyesini yüzde 100 olarak ayarlayın. Daha yüksek ekran kalitesini iyi yakınlaştırma düzeyini ayarlayın.  
  
2. Uygulamanızı öykünücüde başlatın.  
  
3. Öykünücü araç çubuğunda açmak için genişletme düğmesini **ek araçlar** penceresi.  
  
4. Tıklayın **ekran** sekmesi.  
  
5. Uygulama hazır olduğunda tıklayın **yakalama** düğmesi.  
  
    Ekran çalışma alanında görüntülenir.  
  
6. Tıklayın **Kaydet** açmak için düğmeyi **Kaydet** iletişim kutusu.  
  
7. Konum seçin ve **dosya adı** ve ardından **Kaydet**.  
  
8. İsteğe bağlı olarak, uygulamanızda diğer sayfalara gidin ve ek ekran görüntüleri yakalama.  
  
9. Farklı ekran çözünürlüğü farklı bir çözüm aynı ekran yakalamak için bir öykünücü başlatın. Uygulamanızı hata ayıklama ile çalıştırdıysanız, başka bir öykünücü üzerinde yeniden çalıştırmadan önce hata ayıklamayı durdurmak zorunda.  
  
   Ekran görüntüleri için Windows Phone Store gönderilecek yakalamadan önce öykünücü ekranında kare oranı sayaçları devre dışı bırakın.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Kare hızı sayaçları öykünücüsünde ekran görüntüleri yakalamayı önce devre dışı bırakmak için  
  
-   Visual Studio'da bir yayın yapısı belirtmek. Yayın derlemesi belirttikten sonra uygulamanızı seçerek başlatın. **Dağıt _[uygulama adı]_**  bağlantısını **derleme** menüsü.  
  
-   Alternatif olarak, değerini ayarlar app.xaml.cs veya app.xaml.vb dosyasında kod satırı yorum yapabilecek `EnableFrameRateCounter` için `true`.



