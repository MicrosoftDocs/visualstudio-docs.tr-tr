---
title: Simulator'da çalıştırma Windows Store apps | Microsoft Docs
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 504a63d0f99a1a96d1192a1666d45dafde037253
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775114"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Simülatörde Windows Store uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Store uygulamaları için Visual Studio simulator, Windows Store app taklit eden bir masaüstü uygulamasıdır. Uygulamaları çalıştırabilir ve ortak dokunma ve döndürme olaylarının geliştirme bilgisayarınızda benzetimini yapma. Ayrıca, fiziksel ekran boyutunu ve öykünme ve ağ bağlantısı özellikleri benzetimini yapmak istediğiniz çözümü seçebilirsiniz.  
  
 Simülatör, hangi tasarlayabilir, geliştirme, hata ayıklama ve Windows Store uygulamalarını test etmek bir ortam sağlar. Ancak, Windows Store için uygulamanızı yayımlamadan önce uygulamanızın gerçek bir cihaz üzerinde test etmelisiniz.  
  
 Windows Store uygulamaları için Visual Studio simulator, yerel makinenizde yalıtılmış bir ortamda çalıştırmaz. Bu nedenle, tüm makine simulator'da, kurtarılamaz bir sistem genelinde hatası gibi hatalar da etkileyebilir.  
  
 Bkz: [öykünücüsünde çalıştırın, Windows Phone uygulamaları](../debugger/run-windows-phone-apps-in-the-emulator.md) Windows Phone bilgi.  
  
> [!IMPORTANT]
>  Visual Studio 2015 simülatör coğrafi konum düğmesi içermez. Bu durum, Windows 10 simülatör coğrafi konum simülasyonu içermez çünkü. Bu tür bir simülasyon yapmanız gerekiyorsa, Windows 8.1 veya önceki işletim sistemlerinde Visual Studio 2013 simülatör kullanabilirsiniz.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Simülatör hedef olarak ayarlanmış.  
 Windows Store uygulamanızı simulator'da çalıştırmak için seçin **simülatör** listesinde yanındaki açılan listeden **hata ayıklamayı Başlat** hata ayıklayıcı düğmesinde **standart** araç çubuğu.  
  
 ![Simülatörde çalıştırılan](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Etkileşim modu seçin  
 Aşağıdaki etkileşim modları seçebilirsiniz.  
  
-   ![Fare Modu düğmesini](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") fare modu: fare hareketlerini etkileşim modu ayarlar. Fare hareketlerini içerir: tıklama, çift tıkladığında ve etkileyen.  
  
-   ![Başlangıç dokunma öykünmesi düğmesi](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") başlangıç dokunma öykünmesi: tek bir parmağınızı hareket dokunması etkileşim modu ayarlar. Tek-parmak olayları dokunarak sürükleme ve çekerek içerir.  
  
     ![Simülatör tek bir parmak hedef](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") tek hedef simge simülatör içerisindeki konumunu belirtir. Fare işaretçisini konumlandırmak için kullanın.  
  
     ![Tek bir parmak touch hedef](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") dokunma modunu etkinleştirmek için farenin sol düğmesine basın. Örneğin, bir dokunun benzetimini yapmak veya doğru kaydırın veya sürüklerken düğmesini basılı için düğmeye tıklayın.  
  
## <a name="pinch-and-zoom"></a>Sıkıştırma ve yakınlaştırma  
 Sıkıştırma ve iki parmağınızı hareket yakınlaştırmak için etkileşim modu ayarlar.  
  
-   ![İki Siimulator parmak hedef](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  
  
     Çift hedef simge cihaz ekranında iki parmağınızı konumunu belirtir.  
  
    -   Cihaz ekranında nesnenin üzerine simgeleri konumlandırmak için fareyi hareket ettirin.  
  
    -   Fare tekerleği geriye veya İleri sıkıştırma veya yakınlaştırma önce iki parmağınızı sanal uzaklığı değiştirmek için döndürün.  
  
-   -   ![Sıkıştırarak yakınlaştırma ve döndürme hedefleri](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Sol düğmesine basın ve (tabletinizde) yakınlaştırmak için (,) geriye dönük tekerleğini döndürün.  
  
    -   Sol düğmesine basın ve (uzaklaştırma) yakınlaştırma için fare tekerleğinin (İleri) döndürün.  
  
## <a name="object-rotation"></a>Nesne döndürme  
 **Dokunma öykünmesi döndürme** düğmesini kullanarak iki parmağınızı döndürme hareketlerine etkileşim modu ayarlar.  
  
-   -   Cihaz ekranında nesnenin üzerine simgeleri konumlandırmak için fareyi hareket ettirin.  
  
    -   Fare tekerleği geriye veya İleri nesneyi önce iki parmağınızı sanal yönünü değiştirmek için döndürün.  
  
-   -   Sol düğmesine basın ve yönünün nesneyi döndürmek için (,) geriye dönük tekerleğini döndürün. Fare tekerleğini döndürün gibi iki hedef simgelerden birini diğer döndürme göre boyutunu göstermek için döndürür.  
  
    -   Sol düğmesine basın ve saat yönünde nesneyi döndürmek için fare tekerleğini (İleri) döndürün.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Etkinleştirmek veya her zaman üst modunu devre dışı  
 Her zaman diğer windows en üstünde olacak şekilde simülatörü penceresini ayarlayabilirsiniz. **Üstteki pencere geçişi** düğmesini etkinleştirir veya devre dışı bırakır **her zaman üstte** simülatörü penceresini modu.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Cihaz yönlendirmesini değiştirme  
 90 derece herhangi bir yönde simülatör döndürerek cihaz yönü dikey ve yatay arasında geçiş yapabilirsiniz.  
  
> [!NOTE]
>  Simülatör saygı [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) projenin özellik. Örneğin, projeniz yönlendirmesini ayarlar `Landscape`ve ardından dikey yönlendirme simülatöre döndürme, simülatör'ü görünen görüntünün ayrıca döndürülmüş ve yeniden boyutlandırıldı. Bu ayarlar gerçek bir cihaz üzerinde test edin.  
  
> [!NOTE]
>  Simülatör bir kenarında görüntülendiği ekran daha büyük olması simülatör döndürürseniz, simülatör içinde ekrana sığacak şekilde otomatik olarak boyutlandırılır. Simülatör özgün boyutuna boyutlandırılır yeniden döndürürseniz değil.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Benzetimli ekran boyutunu ve çözümleme değiştirme  
 Benzetimli ekran boyutunu ve çözümleme değiştirmek için seçin **değiştirme çözümleme** paletinde düğmesini ve listeden yeni boyutu ve çözümü seçin.  
  
 Ekran boyutunu ve çözüm olarak listelenen *ekran genişliği inç, piksel genişlik X piksel yüksekliği*. Not ekran boyutunu ve çözümleme benzetimi yapılır. Simülatör üzerinde ortak ordinates konum, seçili cihaz boyutu ve çözümleme için ortak ordinates çevrilir.  
  
> [!NOTE]
>  Bit eşlem resimleri ölçeklendirilmiş sürümlerini uygulamanızda kaydedebilir ve Windows geçerli ölçek için doğru görüntüyü yükler. Daha fazla bilgi için [duyarlı tasarım 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Ancak, bu Windows farklı bir görüntü çözünürlüğünü uyacak şekilde seçer için simülatör çözümleme değiştirirseniz, yeni resmi görmek için hata ayıklama oturumunuzu yeniden başlatın ve durdurun gerekir.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Uygulamanızı göndermek üzere Windows Store görüntüsü yakalama  
 Bir uygulamayı Windows app Store'a gönderdiğinizde, uygulama ekran görüntüleri eklemeniz gerekir.  
  
> [!NOTE]
>  Ekran görüntüsü, simülatör geçerli çözünürlükte kaydedilir. Çözünürlüğünü değiştirmek için seçin **değiştirme çözümleme** düğmesi.  
  
-   Simülatör uygulama ekran görüntüleri oluşturmak için seçin **panoya ekran yakalama** düğmesi.  
  
-   Ekran görüntüleri yerleştirildiği konum koymak için **ekran görüntüsü ayarları** düğmesine tıklayın ve kısayol menüsünden konumu seçin.  
  
     ![Ekran görüntüsü ayarları bağlam menüsü](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Ağ bağlantısı özellikleri benzetimi  
 Uygulamanızın kullanıcılarına tarifeli ağ bağlantılarında maliyetini ağ bağlantı maliyeti veya veri planı durumu değişiklikleri bilincini korumak ve yinelenen Dolaşım veya aşan ek maliyetler oluşmasını önlemek için bu bilgileri kullanmak için uygulamanızı etkinleştirme yönetmesine yardımcı olabilecek bir Belirtilen veri aktarımı sınırı. [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) API'leri sayesinde yanıt [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) ve [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) oturum olayları. Bkz: [hızlı başlangıç: tarifeli ağ yönetme maliyet kısıtlamaları](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Hata ayıklama veya ağ maliyet uyumlu kodunuzu test etmek için simülatör üzerinden sunulan bir ağın özellikleri taklit [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) tarafından döndürülen nesne [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)...  
  
 Ağ özellikleri benzetimini yapmak için:  
  
1. Simülatör araç çubuğunda **ağ özelliklerini değiştirme** düğmesi.  
  
2. Üzerinde **ağ özelliklerini ayarla** iletişim kutusunda **kullanım sanal ağ özellikleri**.  
  
    Benzetim kaldırın ve şu anda bağlı arabirimi için ağ özellikleri döndürmek için bu onay kutusunu temizleyin.  
  
3. Girin bir **profil adı** sanal ağ için. Benzetim tanımlamak için kullanabileceğiniz bir benzersiz ad kullanmanızı öneririz [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) özelliği [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) nesne.  
  
4. Seçin [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) profilinden değeri **ağ maliyet türü** listesi.  
  
5. Gelen **veri sınırı durum bayrağı** liste, ayarlayabilirsiniz [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) özelliği veya [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)özelliği true olarak veya tercih edebilirsiniz  **Veri sınırının altında** her iki değeri false olarak ayarlanacak.  
  
6. Gelen **gezici durumu** listesinde, ayarlamak [gezici](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) özelliği.  
  
7. Seçin **özelliklerini ayarla** ağ özelliklerinin, ön plan tetikleyerek benzetimini yapmak için [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) olay ve arka plan [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) türü **NetworkStateChange**.  
  
   **Ağ Bağlantıları yönetme hakkında daha fazla bilgi**  
  
   [Hızlı Başlangıç: Tarifeli ağ maliyet kısıtlamalarını yönetme](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ağ bilgi örnek](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Enerji kullanımını çözümleme](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Nasıl sistem arka plan görevleri ile olaylara yanıt verme](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Nasıl tetikleyeceğinizi askıya alma, sürdürme ve arka plan olaylarını Windows Store uygulamalarında](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Simülatör klavye ile gezinme  
 Simülatör araç çubuğu tuşlarına basarak gezinebilirsiniz **CTRL + ALT + YUKARI OK** odak simülatör araç çubuğuna simülatör penceresinde geçiş yapmak için. Kullanım **yukarı ok** ve **aşağı ok** araç çubuğu düğmeleri arasında taşımak için.  
  
 Simülatör tuşlarına basarak kapatabilirsiniz **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)



