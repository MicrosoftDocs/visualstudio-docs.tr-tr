---
title: Simülatörde UWP uygulamaları çalıştırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f8d1ae730947a70cac253866d0257aa4e0216626
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882775"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Simülatörde UWP uygulamaları çalıştırma
UWP uygulamaları için Visual Studio simulator, UWP uygulaması taklit eden bir masaüstü uygulamasıdır. Genellikle, yerel makine, bağlı bir cihaz veya uzak makinede hata ayıklama istersiniz. Ancak, bazı senaryolarda, farklı fiziksel ekran boyutunu ve çözüm benzetmek için Visual Studio simulator kullanmak isteyebilirsiniz. Ayrıca, ortak dokunma ve döndürme olaylarının benzetimini yapma ve ağ bağlantısı özellikleri benzetimi.
  
 Simülatör, hangi tasarlayabilir, geliştirme, hata ayıklama ve UWP uygulamalarını test etmek bir ortam sağlar. Ancak, Microsoft Store için uygulamanızı yayımlamadan önce uygulamanızın gerçek bir cihaz üzerinde test etmelisiniz.  
  
 UWP uygulamaları için Visual Studio simulator, yerel makinenizde yalıtılmış bir ortamda çalıştırmaz. Bu nedenle, tüm makine simulator'da, kurtarılamaz bir sistem genelinde hatası gibi hatalar da etkileyebilir.  
  
> [!IMPORTANT]
>  Visual Studio 2015 simülatör coğrafi konum düğmesi içermez. Bu durum, Windows 10 simülatör coğrafi konum simülasyonu içermez çünkü.
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Simülatör hedef olarak ayarlanmış.  
 Simülatörde UWP uygulamanızı çalıştırmak için seçin **simülatör** listesinde yanındaki açılan listeden **hata ayıklamayı Başlat** hata ayıklayıcı düğmesinde **standart** araç çubuğu. Bu seçenek yalnızca kullanılabilir değilse, uygulamanızın **hedef Platform Min. Sürüm** geliştirme yaptığınız makinedeki işletim sistemi küçük veya ona eşit. 
  
 ![Simülatörde çalıştırılan](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Etkileşim modu seçin  
 Aşağıdaki etkileşim modları seçebilirsiniz.  
  
-   ![Fare Modu düğmesini](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") fare modu: fare hareketlerini etkileşim modu ayarlar. Fare hareketlerini içerir: tıklama, çift tıkladığında ve etkileyen.  
  
-   ![Başlangıç dokunma öykünmesi düğmesi](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") başlangıç dokunma öykünmesi: tek bir parmağınızı hareket dokunması etkileşim modu ayarlar. Tek-parmak olayları dokunarak sürükleme ve çekerek içerir.  
  
     ![Simülatör tek bir parmak hedef](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") tek hedef simge simülatör içerisindeki konumunu belirtir. Fare işaretçisini konumlandırmak için kullanın.  
  
     ![Tek bir parmak touch hedef](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") dokunma modunu etkinleştirmek için farenin sol düğmesine basın. Örneğin, bir dokunun benzetimini yapmak veya doğru kaydırın veya sürüklerken düğmesini basılı için düğmeye tıklayın.  
  
## <a name="pinch-and-zoom"></a>Sıkıştırma ve yakınlaştırma  
 Sıkıştırma ve iki parmağınızı hareket yakınlaştırmak için etkileşim modu ayarlar.  
  
-   ![İki Siimulator parmak hedef](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     Çift hedef simge cihaz ekranında iki parmağınızı konumunu belirtir.  
  
    -   Cihaz ekranında nesnenin üzerine simgeleri konumlandırmak için fareyi hareket ettirin.  
  
    -   Fare tekerleği geriye veya İleri sıkıştırma veya yakınlaştırma önce iki parmağınızı sanal uzaklığı değiştirmek için döndürün.  
  
-   -   ![Sıkıştırarak yakınlaştırma ve döndürme hedefleri](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
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
>  Bit eşlem resimleri ölçeklendirilmiş sürümlerini uygulamanızda kaydedebilir ve Windows geçerli ölçek için doğru görüntüyü yükler. Daha fazla bilgi için [tasarım ve UI giriş](/windows/uwp/layout/design-and-ui-intro). Ancak, bu Windows farklı bir görüntü çözünürlüğünü uyacak şekilde seçer için simülatör çözümleme değiştirirseniz, yeni resmi görmek için hata ayıklama oturumunuzu yeniden başlatın ve durdurun gerekir.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Uygulamanızı göndermek üzere Microsoft Store görüntüsü yakalama  
 Bir uygulama için Microsoft Store gönderdiğinizde, uygulama ekran görüntüleri eklemeniz gerekir.  
  
> [!NOTE]
>  Ekran görüntüsü, simülatör geçerli çözünürlükte kaydedilir. Çözünürlüğünü değiştirmek için seçin **değiştirme çözümleme** düğmesi.  
  
-   Simülatör uygulama ekran görüntüleri oluşturmak için seçin **panoya ekran yakalama** düğmesi.  
  
-   Ekran görüntüleri yerleştirildiği konum koymak için **ekran görüntüsü ayarları** düğmesine tıklayın ve kısayol menüsünden konumu seçin.  
  
     ![Ekran görüntüsü ayarları bağlam menüsü](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Ağ bağlantısı özellikleri benzetimi  
 Uygulamanızın kullanıcılarına tarifeli ağ bağlantılarında maliyetini ağ bağlantı maliyeti veya veri planı durumu değişiklikleri bilincini korumak ve yinelenen Dolaşım veya aşan ek maliyetler oluşmasını önlemek için bu bilgileri kullanmak için uygulamanızı etkinleştirme yönetmesine yardımcı olabilecek bir Belirtilen veri aktarımı sınırı. [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) API'leri sayesinde yanıt [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) ve [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) oturum olayları. Bkz: [hızlı başlangıç: tarifeli ağ yönetme maliyet kısıtlamaları](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Hata ayıklama veya ağ maliyet uyumlu kodunuzu test etmek için simülatör üzerinden sunulan bir ağın özellikleri taklit [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) tarafından döndürülen nesne [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Ağ özellikleri benzetimini yapmak için:  
  
1. Simülatör araç çubuğunda **ağ özelliklerini değiştirme** düğmesi.  
  
2. Üzerinde **ağ özelliklerini ayarla** iletişim kutusunda **kullanım sanal ağ özellikleri**.  
  
    Benzetim kaldırın ve şu anda bağlı arabirimi için ağ özellikleri döndürmek için bu onay kutusunu temizleyin.  
  
3. Girin bir **profil adı** sanal ağ için. Benzetim tanımlamak için kullanabileceğiniz bir benzersiz ad kullanmanızı öneririz [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) özelliği [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) nesne.  
  
4. Seçin [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) profilinden değeri **ağ maliyet türü** listesi.  
  
5. Gelen **veri sınırı durum bayrağı** liste, ayarlayabilirsiniz [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) özelliği veya [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) özelliği true olarak veya tercih edebilirsiniz  **Veri sınırının altında** her iki değeri false olarak ayarlanacak.  
  
6. Gelen **gezici durumu** listesinde, ayarlamak [gezici](/uwp/api/windows.networking.connectivity.connectioncost) özelliği.  
  
7. Seçin **özelliklerini ayarla** ağ özelliklerinin, ön plan tetikleyerek benzetimini yapmak için [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) olay ve arka plan [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) türü **NetworkStateChange**.  
  
   **Ağ Bağlantıları yönetme hakkında daha fazla bilgi**  
  
   [Hızlı Başlangıç: Tarifeli ağ maliyet kısıtlamalarını yönetme](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ağ bilgi örnek](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Enerji kullanımını çözümleme](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
   [Nasıl sistem arka plan görevleri ile olaylara yanıt verme](/previous-versions/windows/apps/hh977058(v=win.10))  
  
   [UWP uygulamalarında askıya alma, sürdürme ve arka plan olayları tetikleme](/visualstudio/debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Simülatör klavye ile gezinme  
 Simülatör araç çubuğu tuşlarına basarak gezinebilirsiniz **CTRL + ALT + YUKARI OK** odak simülatör araç çubuğuna simülatör penceresinde geçiş yapmak için. Kullanım **yukarı ok** ve **aşağı ok** araç çubuğu düğmeleri arasında taşımak için.  
  
 Simülatör tuşlarına basarak kapatabilirsiniz **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)