---
title: Grafik bilgilerini yakalama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: 44
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a099254acd572b3fcbb437f8933c81f3d6bd45b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799840"
---
# <a name="capturing-graphics-information"></a>Grafik Bilgilerini Yakalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşleme sorunlarını ve performans sorunlarını tanılamak için Visual Studio grafik Çözümleyicisi kullanabilirsiniz, böylece Direct3D uygulamanızdan grafik bilgilerini yakalama.  
  
## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Graf bilgilerini yakalama iki adımlı bir işlemdir. Önce uygulamanızı Grafik Tanılama altında çalıştırın ve sonra ayrıntılı bilgilerini yakalamak üzere bir veya daha fazla kare belirtin.  
  
#### <a name="to-run-your-app-under-graphics-diagnostics"></a>Uygulamanızı Grafik Tanılama altında çalıştırmak için  
  
- Menü çubuğunda, **hata ayıklama**, **grafik**, **tanılamayı Başlat**. (Klavye: Alt+F5 tuşlarına basın)  
  
- Üzerinde **grafik** araç seçin **tanılamayı Başlat** düğmesi.  
  
  Bir uygulama Grafik Tanılama altında çalışırken, belirli grafik bilgisi türleri sürekli olarak yakalanır; bunlar cihaz kurulumu, takas zincirinin oluşturulması, grafik nesnelerinin ve kaynakların oluşturulması ve birden fazla kareyi etkileyen diğer önemli olayları içerir. Aynı zamanda, belirli kareler hakkında ayrıntılı bilgiler yakalayabilirsiniz; Direct3D nesneleri ve bunları destekleyen kaynaklar ile birlikte çizim çağrıları ve hesaplayıcı-gölgelendirici sevkleri buna dahildir.  
  
#### <a name="to-capture-a-frame"></a>Bir kareyi yakalamak için  
  
- Visual Studio'da üzerinde **grafik** araç seçin **kare Yakala** düğmesi![grafik yakalama düğmesinin simgesi](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
- Klavyede Print Screen tuşuna basın.  
  
  > [!NOTE]
  >  Bir uygulama altında çalışırken **grafik tanılama**, Print Screen tuşu yalnızca grafik bilgisi karesi yakalamak için kullanılabilir; normal işlevini gerçekleştirmez. Başka bir uygulama odakta olsa bile, grafik bilgilerini yakalamayı durduruncaya kadar (genellikle hata ayıklamayı durdurarak veya uygulamadan normal yolla çıkarak) bu durum devam eder.  
  
- Visual Studio yakalama arabiriminde seçtiğiniz **kare Yakala** düğmesi bulunan yukarıda **Tanılama oturumu** zaman çizelgesi veya büyük seçin **kare Yakala** düğmesi Aşağıda bulunan **Saniyedeki** yüzme kulvarı ve daha önce yakalanan çerçeve sağındaki. Her iki düğme, aşağıdaki resimde vurgulanmıştır.  
  
   ![GPU kullanımı aracı kullanarak çerçevelerini yakalayın. ](../debugger/media/pix-gpu-usage-tool-capture-frame.png "pix_gpu_usage_tool_capture_frame")  
  
   Çerçeveleri incelemek hazır olduğunuzda, yakalanan, başlangıç **Visual Studio grafik Çözümleyicisi** izleyerek **çerçeve...** Görüntü küçük resimleri üstüne ya da küçük resim çift tıklayarak bağlayın.  
  
  Yalnızca tam kareler yakalanabilir; bu nedenle bir yakalama başlattığınızda, kaydedilen aslında bir sonraki karenin grafik bilgileridir. Kayıt, yakalama işlemini başlattığınız kare sunulduktan hemen sonra başlar ve yakalanan kare sunulduğunda sona erer. Uygulama Grafik Tanılama altında çalışırken istediğiniz sayıda kare yakalayabilirsiniz. Hiçbir kare yakalamazsanız, grafik günlüğü atılır.  
  
  Çerçeve yakalama sırasında Visual Studio Tanılama oturumu (.diagsession) penceresinde görüntüler. Bu pencereyi kapatın, hata ayıklamayı durdurmak veya uygulamayı kapatmak, bu günlüğe başka kareler yakalayamazsınız. Daha fazla grafik bilgisi yakalamak için uygulamayı yeni bir tanılama oturumu yeniden başlatmak için grafik tanılama altında çalıştırmak sahip.  
  
### <a name="graphics-diagnostics-capture-options"></a>Grafik tanılama yakalama seçenekleri  
 Tüm grafik olaylarını veya sınırlı bir alt kümesi için çağrı yığınlarını Topla, baş üstü, yakalama devre dışı bırakma ve etkinleştirme veya devre dışı yakalama uyumluluk modu yakalama özelliğini yapılandırabilirsiniz.  
  
##### <a name="to-configure-graphics-diagnostics-capture-options"></a>Grafik tanılama yakalama seçeneklerini yapılandırmak için  
  
1.  Menü çubuğunda, Araçlar, Seçenekler'i seçin. Seçenekler iletişim kutusu görünür.  
  
2.  Sol taraftaki seçenekleri Kategori listesinden, grafik Tanılama'yı seçin ve sonra istediğiniz grafik tanılama seçenekleri yapılandırın.  
  
     **Yakalama sırasında çağrı yığınlarını TOPLA (yakalamayı yavaşlatır)**  
     Çağrı yığınlarını Topla için bu kutuyu işaretleyin. Varsayılan olarak, çağrı yığını toplanmadı. Çağrı yığınlarını yakalamak için emin **toplama çağrı yığınları yakalama sırasında (yakalamayı yavaşlatır** toplamayı etkinleştirin ve ardından ya da ayarlamak için onay kutusuna olarak **çizim,gönderme,mevcutveperformansişaretleyicileriiçin**yalnızca en önemli çağrı yığınlarını, toplanacak (varsayılan) seçeneğini veya **her şeyi** seçeneği tüm çağrı yığınlarını topla. Çağrı yığınlarını sonraki toplamayı durdurmak için temizleyin **toplama çağrı yığınları yakalama sırasında (yakalamayı yavaşlatır** onay kutusu.  
  
     **Yakalama sırasında oyun içi HUD'yi devre dışı bırak**  
     Baş üstü devre dışı bırakmak için bu kutuyu, bir uygulama grafik tanılama altında genellikle görüntüler çalışmaya kaplama denetleyin. Baş üstü katmana görüntülemek için onay işaretini kaldırın.  
  
     **Uyumluluk modunda yakalayın**  
     Uyumluluk modunda grafik bilgilerini yakalamak için bu kutuyu işaretleyin. Uyumluluk modunda yakalama varsayılandır. Uyumluluk modunda, Direct3D GPU ötesinde bir temel özellik düzeyinde tanımlanan diğer ek özellikleri desteklediğini rapor olmaz. Bu uygulama üzerinde GPU, yakalanan donanıma özgü uzantıları kullanılarak yakalanan engeller ve grafik günlüğü geri aynı veya daha yüksek özellik düzeyini destekleyen herhangi bir GPU kullanılarak çalınabilir sağlar. Uyumluluk modunu devre dışı bırakmak için bu kutunun işaretini kaldırın; Uyumluluk modu devre dışı yakalanan günlükleri, yakalama sırasında uygulama tarafından kullanılan aynı ek özellikleri desteklemeyen herhangi bir GPU üzerinde yürütme işlemi başarısız olur.  
  
     **SDK katmanı hatası bulunursa Yakalamayı Durdur**  
     Bir hatayla karşılaşılmazsa yakalama hemen durdurmak için bu kutuyu işaretleyin.  
  
## <a name="capturing-graphics-information-remotely"></a>Graf bilgilerini uzaktan yakalama  
 Grafik bilgileri, yerel makinede ya da uzak bir makine veya cihazda çalışan bir uygulamadan yakalanabilir. Uzaktan yakalama için desteklenen [!INCLUDE[winblue_client_2](../includes/winblue-client-2-md.md)] makineler ve [!INCLUDE[winblue_winrt_2](../includes/winblue-winrt-2-md.md)] cihazlar. Uzakta çalışan bir uygulamadan grafik bilgilerini yakalamak için, projenizi uzaktan hata ayıklama için yapılandırın ve sonra uygulamanızı, daha önce açıklandığı gibi, Grafik Tanılama altında çalıştırın. Uygulama uzak makinede çalışır ve yakalanan grafik bilgileri geliştirme makinenizde kaydedilir.  
  
 Projenizi uzaktan hata ayıklama için yapılandırma şekliniz, geliştirmekte olduğunuz uygulamanın türüne ve kullandığınız programlama diline göre değişir. Bir Windows Store uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında daha fazla bilgi için bkz: [uzak bir makinede çalıştırma Windows Store apps](../debugger/run-windows-store-apps-on-a-remote-machine.md). Bir Windows masaüstü uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında daha fazla bilgi için bkz: [kümesi oluşturan uzaktan hata ayıklama için Visual Studio projesi](http://msdn.microsoft.com/library/ec332dc4-400a-498b-a0e6-c8dcf10fef8a).  
  
 Daha sonra, bilgilerin yakalandığı yerden bağımsız olarak, grafik bilgilerini kayıttan yürütmek için bir uzak makine veya cihaz kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Komut satırından grafik bilgilerini yakalama  
 Bir komut satırı aracını kullanarak bir uygulamadan grafik bilgilerini yakalanabilir. Bu araç, DXCap.exe, hızlı bir şekilde yakalayın ve Visual Studio ya da programlı yakalama kullanmadan grafik bilgilerini kayıttan yürütme. Özellikle, otomasyon için veya bir test ortamında DXCap.exe kullanabilirsiniz. DXCap.exe hakkında daha fazla bilgi için bkz: [komut satırı Yakalama aracı](../debugger/command-line-capture-tool.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: Grafik Bilgilerini Yakalama](../debugger/walkthrough-capturing-graphics-information.md)



