---
title: 'İzlenecek yol: Cihaz durumu nedeniyle nesnelerin eksikliği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c0ad6017dd6ff660dfbd47977e1a53346cf6c55
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773736"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda nasıl kullanılacağını gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nedeni eksik bir nesne incelemek için grafik Tanılama, cihaz durumu yanlış.  
  
 Bu izlenecek yol gösterir nasıl yapılır:  
  
-   Kullanım **grafik olay listesi** olası sorun kaynaklarını bulmak için.  
  
-   Kullanım **grafik ardışık düzen aşamaları** etkisini denetlemek için pencere `DrawIndexed` Direct3D API'sini çağırır.  
  
-   Kullanım **grafik piksel geçmişi** sorunu daha ayrıntılı belirtmek gerekirse bulunacak penceresi.  
  
-   Olası sorunları veya yanlış yapılandırmalar için cihaz durumunu inceleyin.  
  
## <a name="scenario"></a>Senaryo  
 Nedenlerden biri dolayısıyla nesneler, 3B bir uygulamada nereye beklenen görünmeyebilir olduğundan işleme çıkarılacak nesneleri neden olur grafik cihazlarının yanlış yapılandırma — Örneğin, Sarım düzeni sebep olduğunda hata culled üçgen , veya Derinlik test işlevi sebep olduğunda tüm piksel nesneyi reddedilir.  
  
 Bu kılavuzda açıklanan senaryoda, yalnızca ilk aşama 3-b uygulama geliştirmede ulaştınız ve ilk kez test etmeye hazırsınız. Bununla birlikte, uygulamayı çalıştırdığınızda, yalnızca kullanıcı arabirimi ekranı işlenir. Böylece uygulamanın hatalarını ayıklayabilir miyim grafik tanılamayı kullanarak sorunu bir grafik günlük dosyasına yakalayın. Sorun, uygulamada şu şekilde görünür:  
  
 ![Sorun çözülmezse önce uygulamayı](../debugger/media/vsg-walkthru1-firstview.png "vsg_walkthru1_firstview")  
  
 Grafik sorunlarını grafik günlüğünde yakalama hakkında daha fazla bilgi için bkz: [Capturing Graphics Information](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Araştırma  
 Grafik tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük dosyasını yükleyebilirsiniz.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eksik model sergiler çerçeveyi içeren grafik günlüğünü yükleyin. Yeni bir grafik Tanılama sekmesi görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu sekmenin üst kısmında seçilen çerçevenin işleme hedefi çıktısı ' dir. Alt parçasıdır **çerçeve listesi**, bir küçük resim her yakalanan çerçeve görüntüler.  
  
2. İçinde **çerçeve listesi**, model görüntülenmez gösteren bir çerçeve seçin. İşleme hedefi, Seçilen çerçevenin yansıtacak şekilde güncelleştirilir. Bu senaryoda, grafik sekmesi şu şekilde görünür günlük:  
  
    ![.Vsglog sekme framebuffer Önizleme ve çerçeve listesi](../debugger/media/vsg-walkthru1-experiment.png "vsg_walkthru1_experiment")  
  
   Sorunu gösteren bir çerçeveyi seçtikten sonra kullanabileceğiniz **grafik olay listesi** tanılamak için. **Grafik olay listesi** etkin çerçeve için işlemek için yapılan her Direct3D API çağrısı cihaz durumunu ayarlamak için oluşturun ve arabellek güncelleştirin ve çerçeve içinde görünen nesneler çizmek için API çağrısı içerir. Olduğundan çağrılarının pek çok ilgi çekici genellikle (ama her zaman kullanılmaz) karşılık gelen bir uygulamada beklendiği gibi çalışırken işleme hedefi değişiklik örneğin çizme, gönderme, kopyalama veya açık çağrıları. Her bir uygulama oluşturulmasını geometri temsil ettiğinden çizim çağrıları özellikle ilgi çekici (gönderme çağrılar da de geometri oluşturma).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Bu çizim çağrıları yapılan emin olmak için  
  
1. Açık **grafik olay listesi** penceresi. Üzerinde **grafik tanılama** araç seçin **olay listesi**.  
  
2. İnceleme **grafik olay listesi** çizim çağrıları. Bunu kolaylaştırmak için "Çiz" girin **arama** sağ üst köşesinde kutusunda **grafik olay listesi** penceresi. Bu, yalnızca başlıklarında "Çiz" olan olaylar içeren listenin filtreler. Bu senaryoda birkaç çizim çağrıları yapılan keşfedin:  
  
    ![Yakalanan olaylar gösteren grafik olay listesi](../debugger/media/vsg-walkthru1.png "vsg_walkthru1_")  
  
   Bu çizim çağrıları yapılan onayladıktan sonra hangisinin eksik geometriye karşılık gelen belirleyebilirsiniz. Eksik geometri işleme hedefine (Bu örnekte) olması nedeniyle dikkatin değil olduğunu bildiğiniz olduğundan, kullanabileceğiniz **grafik ardışık düzen aşamaları** penceresi, çizim çağrısı çıktılarının belirlemek için eksik geometriye karşılık gelir. **Grafik ardışık düzen aşamaları** penceresi işleme hedefi üzerindeki etkisini bağımsız olarak her bir çizim çağrısına gönderildiği geometri gösterir. Çizim çağrıları arasında taşırken, ardışık düzen aşamaları bu çağrıyla ilişkili geometri gösterecek şekilde güncelleştirilir ve işleme hedefi çıktısı çağrı tamamlandıktan sonra işleme hedefi durumunu göstermek için güncelleştirilir.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Çizim çağrısı için eksik geometri bulmak için  
  
1. Açık **grafik ardışık düzen aşamaları** penceresi. Üzerinde **grafik tanılama** araç seçin **ardışık düzen aşamaları**.  
  
2. İzleme sırasında her bir çizim çağrısı aracılığıyla Taşı **grafik ardışık düzen aşamaları** eksik model penceresi. **Giriş Assembler** aşaması ham model verileri gösterir. **Köşe gölgelendiricisi** aşama dönüştürülmüş model verileri gösterir. **Piksel gölgelendiricisi** aşaması piksel gölgelendirici çıkışı gösterir. **Çıkış Birleştiricisi** aşama Bu çizim çağrısı ve tüm önceki çizim çağrıları birleştirilmiş işleme hedefi gösterir.  
  
3. Eksik modeline karşılık gelen bir çizim çağrısı ulaştınız durdur. Bu senaryoda, **grafik ardışık düzen aşamaları** geometri işlenir ancak işleme hedef görünmedi pencere gösterir:  
  
    ![Ardışık Düzen Görüntüleyicisi eksik nesneyi gösteren](../debugger/media/vsg-walkthru1-pipeline.png "vsg_walkthru1_pipeline")  
  
   Eksik geometri uygulama oluşturulmasını ve karşılık gelen bir çizim çağrısı bulun onayladıktan sonra bir kısmı eksik geometri gösterin ve ardından işleme hedefi çıktısı seçebileceğiniz **grafik piksel geçmişi** piksel neden dışlanan bulmak için pencere. Piksel geçmişi, belirli bir piksel üzerinde bir etkisi yapmış olabileceği her bir çizim çağrısı bir listesini içerir. Her bir çizim çağrısı **grafik piksel geçmişi** penceresi da görüntülenen bir sayı tarafından tanımlanan **grafik olay listesi** penceresi. Bu, piksel eksik geometri görüntülenmelidir doğrulamanıza yardımcı olur ve piksel neden dışlandı bulmak için  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Neden için piksel dışarıda bırakıldı belirlemek için  
  
1. Açık **grafik piksel geçmişi** penceresi. Üzerinde **grafik tanılama** araç seçin **piksel geçmişi**.  
  
2. Temel **piksel gölgelendiricisi** bir kısmı eksik geometri içermesi gereken bir pikselin framebuffer çıktı küçük resim seçin. Bu senaryoda, çoğu işleme hedefinin piksel gölgelendirici çıkışı kapsamalıdır; bir pikselin seçildikten sonra **grafik piksel geçmişi** penceresi şu şekilde görünür:  
  
    ![Piksel Geçmişi penceresini ilgili gösteren çizim çağrıları](../debugger/media/vsg-walkthru1-hist1.png "vsg_walkthru1_hist1")  
  
3. Seçili işleme hedef piksel inceleyerek çizim çağrısı sayısını eşleştirerek geometri değerinin bir bölümü yer aldığını onaylayın (gelen **grafik olay listesi** pencere) bir çizim çağrıları **grafik Piksel geçmişi** penceresi. Çağrılarında hiçbiri **grafik piksel geçmişi** penceresi eşleşme, inceleyerek, çizim çağrısı (dışında 1. adım) bu adımları yineleyin bir eşleşme bulana kadar. Bu senaryoda, eşleşen çizim çağrısı şöyle görünür:  
  
    ![Piksel Geçmişi penceresini gösteren parça bilgileri](../debugger/media/vsg-walkthru1-hist2.png "vsg_walkthru1_hist2")  
  
4. Bir eşleşme bulduğunuzda, eşleşen çizim çağrısını genişletin **grafik piksel geçmişi** penceresi ve piksel dışarıda bırakıldı onaylayın. Her bir çizim çağrısı **grafik piksel geçmişi** penceresi, karşılık gelen nesnenin geometrisini sonucunda bu piksel kesiştiğinden bir veya daha fazla geometrik temelleri (noktaları, çizgiler veya üçgenler) karşılık gelir. Her tür kesişimi pikselin son rengini için katkıda bulunabilir. Derinlik testinde başarısız oldu çünkü hariç temel soldan sağa doğru aşağı slopes okun üzerine Harf Z gösteren bir simge ile temsil edilir.  
  
5. Duruma çıkarılmasına neden daha ayrıntılı incelemek için hariç tutulan bir temel öğeyi genişletin. İçinde **çıkış Birleştiricisi** grubunda, işaretçiyi **sonucu**. Temel neden dışlandı bir araç ipucu belirtir. Bu senaryoda, derinlik testinde başarısız oldu ve bu nedenle pikselin son rengini için katkıda bulundu mu değil çünkü temel dışlandı İnceleme ortaya çıkarır.  
  
   Geometri, ilkel derinlik testinde başarısız olduğundan görünmüyor belirledikten sonra bu sorunun yapılandırılmış cihaz durumuna ilgili olup olmadığını düşündüğünüz. Cihaz durumu ve diğer Direct3D nesnesini kullanarak veri incelenebilir **Graphics Object Table**.  
  
#### <a name="to-examine-device-state"></a>Cihaz durumunu incelemek için  
  
1. Açık **Graphics Object Table** penceresi. Üzerinde **grafik tanılama** araç seçin **nesne tablosu**.  
  
2. Bulun **D3D10 cihazı** nesnesine **Graphics Object Table**ve ardından açın **D3D10 cihazı** nesne. Yeni bir **d3d10 cihazı** sekmesi açılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bunu kolaylaştırmak için sıralayabilirsiniz **Graphics Object Table** tarafından **türü**:  
  
    ![Grafik nesne tablosu ve ilgili cihaz durumu](../debugger/media/vsg-walkthru1-objtable.png "vsg_walkthru1_objtable")  
  
3. Görüntülenen cihaz durumunu incelemek **d3d10 cihazı** olası sorunlar için sekmesinde. Geometri, ilkel derinlik testinde başarısız olduğundan görünmez olduğundan derinlik testinde etkileyen derinlik kalıbı gibi cihaz durumu odaklanabilirsiniz. Bu senaryoda, **derinlik kalıbı açıklaması** (altında **çıkış birleşme durumu**) için genel olmayan bir değer içeriyor **derinliği işlevi** üyesi `D3D10_COMPARISON_GREATER`:  
  
    ![Derinlik kalıbı bilgilerini gösteren D3D10 cihazı penceresi](../debugger/media/vsg-walkthru1-devicestate.png "vsg_walkthru1_devicestate")  
  
   İşleme sorunun nedenini yapılandırılmış derinliği işlevi olabilir belirledikten sonra burada derinliği işlevi yanlış ayarlanmış bulmak için kod bilginizi birlikte bu bilgileri kullanın ve ardından sorunu gidermek. Kodla alışkın değilseniz, sorun için hata ayıkladığınız sırada topladığınız ipuçları kullanarak arayabilir — Örneğin, temel **derinlik kalıbı açıklaması** Bu senaryoda, kod sözcükleri arayabilir. "ayrıntılı" veya "Daha büyük" gibi. Kod giderdikten sonra yeniden oluşturmak ve uygulamayı yeniden işleme sorunun çözüldüğünü bulmak için çalıştırın:  
  
   ![Sorun düzeltildikten sonra uygulama](../debugger/media/vsg-walkthru1-finalview.png "vsg_walkthru1_finalview")



