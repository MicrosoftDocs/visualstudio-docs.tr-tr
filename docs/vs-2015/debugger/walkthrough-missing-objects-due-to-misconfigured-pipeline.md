---
title: 'İzlenecek yol: Yanlış yapılandırılmış ardışık düzen nedeniyle nesnelerin eksikliği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd28886695e3234240de5675e5e2b19972b105fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782024"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>İzlenecek Yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda nasıl kullanılacağını gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nedeniyle bir unset piksel gölgelendiricisi eksik olan bir nesne incelemek için grafik tanılama araçları.  
  
 Bu örneklerde bu görevler gösterilir:  
  
-   Kullanarak **grafik olay listesi** olası sorun kaynaklarını bulmak için.  
  
-   Kullanarak **grafik ardışık düzen aşamaları** etkisini incelemek için penceresine `DrawIndexed` Direct3D API çağrısı.  
  
-   Gölgelendirici aşaması ayarlanmadı onaylamak için cihaz bağlamı inceleniyor.  
  
-   Kullanarak **grafik ardışık düzen aşamaları** penceresi ile birlikte **grafik olay çağrı yığını** unset piksel gölgelendiricisi kaynağını bulmaya yardımcı olacak.  
  
## <a name="scenario"></a>Senaryo  
 Bir nesneyi 3B bir uygulamada eksik olduğunda, nesne oluşturulmadan önce gölgelendirici aşamalarının biri ayarlanmadı bazen olmasıdır. Basit işleme gereksinimlerine sahip uygulamalar, bu hata genellikle bulunduğu yere nesnenin çizim çağrısı çağrı yığınında kaynağıdır. Ancak, bir iyileştirme gölgelendirici program, doku veya ortak en aza indirmek için diğer verileri bazı uygulamalar toplu birlikte nesneler durumu-ek yükü değişikliği. Bu uygulamalar, hatanın kaynağını toplu işlem sistemine kaçınma yerine çizim çağrısı çağrı yığınında bulunur. Basit işleme gereksinimlerine sahip bir uygulama bu kılavuzdaki senaryoyu göstermektedir ve bu nedenle hatanın kaynağının çağrı yığınında bulunabilir.  
  
 Bu senaryoda, test etmek için uygulamayı çalıştırdığınızda, arka plan beklendiği gibi işlenir ancak nesnelerinden birine görünmez. Böylece uygulamanın hatalarını ayıklayabilir miyim grafik tanılamayı kullanarak sorunu bir grafik günlüğüne yakalayın. Sorun, uygulamada şu şekilde görünür:  
  
 ![Nesne'ne görülemeyen](../debugger/media/gfx-diag-demo-misconfigured-pipeline-problem.png "gfx_diag_demo_misconfigured_pipeline_problem")  
  
## <a name="investigation"></a>Araştırma  
 Grafik tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük belgesi yükleyebilirsiniz.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eksik nesne sergiler çerçeveyi içeren grafik günlük belgesi yükleyin. Yeni bir grafik günlüğü sekmesi görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu sekmenin üst kısmında seçilen çerçevenin işleme hedefi çıktısı ' dir. Alt parçasıdır **çerçeve listesi**, bir küçük resim her yakalanan çerçeve görüntüler.  
  
2. İçinde **çerçeve listesi**, nesne görüntülenmez gösteren bir çerçeve seçin. İşleme hedefi, Seçilen çerçevenin yansıtacak şekilde güncelleştirilir. Bu senaryoda, grafik sekmesi şu şekilde görünür günlük:  
  
    ![Grafik belgesi Visual Studio'da oturum](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-1.png "gfx_diag_demo_misconfigured_pipeline_step_1")  
  
   Sorunu gösteren bir çerçeveyi seçtikten sonra kullanarak tanılamak başlayabilirsiniz **grafik olay listesi**. **Grafik olay listesi** etkin çerçeveye işlemek için yapılan her Direct3D API çağrısı içerir — örneğin, cihaz durumunu ayarlamak için oluşturun ve arabellek güncelleştirin ve çerçeve içinde görünen nesneler çizmek için. Pek çok çağrıları — Örneğin, çizim, gönderme, kopyalama veya açık çağrıları — olmadığı için genellikle (ama her zaman kullanılmaz) ilginç olan uygulamada beklendiği gibi çalışırken işleme hedefi karşılık gelen bir değişiklik. Çizim çağrıları özellikle ilgi çekici olduğu her bir uygulama oluşturulmasını geometri temsil eder.  
  
   İşleme hedefi içermiyor bildiğiniz eksik nesne de vardır değil gibi görünüyor, diğer hatalar, kullanabileceğiniz **grafik olay listesi** ile birlikte **grafik ardışık düzen aşamaları**, çizim çağrısı çıktılarının belirlemek için aracı için eksik nesne geometrisinin karşılık gelir. **Grafik ardışık düzen aşamaları** penceresi işleme hedefi üzerindeki etkisini bağımsız olarak her bir çizim çağrısına gönderildiği geometri gösterir. Çizim çağrıları arasında taşırken, ardışık düzen aşamaları her etkin bir aşama akan, her çağrısıyla ilişkili geometri gösterecek şekilde güncelleştirilir ve işleme hedefi çıktısı aramayı tamamladıktan sonra işleme hedefi durumunu göstermek için güncelleştirilir.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Çizim çağrısı için eksik geometri bulmak için  
  
1. Açık **grafik olay listesi** penceresi. Üzerinde **grafik tanılama** araç seçin **olay listesi**.  
  
2. Açık **grafik ardışık düzen aşamaları** penceresi. Üzerinde **grafik tanılama** araç seçin **ardışık düzen aşamaları**.  
  
3. Her geçerken çağrı çizin **grafik olay listesi** penceresi, watch **grafik ardışık düzen aşamaları** eksik nesnesinin penceresi. Bunu kolaylaştırmak için "Çiz" girin **arama** sağ üst köşesinde kutusunda **grafik olay listesi** penceresi. Bu, yalnızca başlıklarında "Çiz" olan olaylar içeren listenin filtreler.  
  
    İçinde **grafik ardışık düzen aşamaları** penceresinde **giriş Assembler** aşama, dönüştürülen önce nesne geometrisinin gösterir ve **köşe gölgelendiricisi** aşama aynı gösterir Bunu dönüştürüldükten sonra nesne. Bu senaryoda, dikkat **grafik ardışık düzen aşamaları** penceresi şunu gösterir **giriş Assembler** ve **köşe gölgelendiricisi** aşamaları ancak **piksel gölgelendiricisi**  aşaması için bir çizim çağrıları.  
  
   > [!NOTE]
   >  Diğer, ardışık düzen aşamaları — Örneğin, kabuk gölgelendiricisi, etki alanı gölgelendiricisi ve geometri gölgelendirici aşamalarının — nesneyi işlemek, sorunun nedenini herhangi biri olabilir. Genellikle, erken aşama sonucu görüntülenmez veya beklenmedik bir şekilde görüntülenir sorun ilgilidir.  
  
4. Eksik bir nesneye karşılık gelen bir çizim çağrısı ulaştığında durdurun. Bu senaryoda, **grafik ardışık düzen aşamaları** pencere geometri GPU'ya verildiğini gösterir (yokluğuyla **giriş Assembler** aşama) ve dönüştürülen ( tarafındanbelirtilir **Köşe gölgelendirici** aşama), bir etkin piksel gölgelendiricisi olması değil gözükmüyor olduğundan işleme hedefi görünmez, ancak (yokluğuyla **piksel gölgelendiricisi** aşama). Bu senaryoda, eksik nesnesinin siluet bile görebilirsiniz **çıkış Birleştiricisi** aşama:  
  
    ![DrawIndexed olay ve işlem hattı üzerindeki etkisini](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-2.png "gfx_diag_demo_misconfigured_pipeline_step_2")  
  
   Uygulamayı bir çizim çağrısı eksik nesne geometrisinin için verilen onaylayın ve piksel gölgelendirici aşaması etkin bulma sonra bulgularınızı onaylamak için cihaz durumunu inceleyebilirsiniz. Kullanabileceğiniz **Graphics Object Table** cihaz bağlamı ve diğer Direct3D nesne verilerini incelemek için.  
  
#### <a name="to-examine-device-context"></a>Cihaz bağlamı incelemek için  
  
1. Açık **d3d11 cihaz bağlamı**. İçinde **grafik ardışık düzen aşamaları** penceresinde seçin **ID3D11DeviceContext** parçası olan bağlantıyı `DrawIndexed` pencerenin üst kısmında görüntülenen çağrısı.  
  
2. Görüntülenen cihaz durumunu incelemek **d3d11 cihaz bağlamı** hiçbir piksel gölgelendiricisi çizim çağrısı sırasında etkin olduğunu onaylamak için sekmesinde. Bu senaryoda, **gölgelendirici genel bilgileri**— altında görüntülenen **piksel gölgelendirici durumu**— gölgelendirici olduğunu gösterir **NULL**:  
  
    ![Piksel gölgelendirici durumu 11 D3D cihaz bağlamı gösterir](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-4.png "gfx_diag_demo_misconfigured_pipeline_step_4")  
  
   Piksel gölgelendiricisinin ayarlandı olduğunu doğruladıktan sonra uygulamanız tarafından sonraki adım, uygulamanızın kaynak kodunda konumu bulmak için gölgelendirici ayarlandığı null. Kullanabileceğiniz **grafik olay listesi** ile birlikte **grafik olay çağrı yığını** bu konumu bulunamadı.  
  
#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Piksel gölgelendirici uygulamanızın kaynak kodunda belirlendiği bulmak için  
  
1. Bulma `PSSetShader` eksik nesnesine karşılık gelen çağrı. İçinde **grafik olay listesi** penceresinde "Çiz; girin "İçinde PSSetShader **arama** sağ üst köşesinde kutusunda **grafik olay listesi** penceresi. Bu, yalnızca "PSSetShader" olaylar ve kendi başlıklarında "Çiz" olan olaylar içeren listenin filtreler. İlk seçin `PSSetShader` eksik nesnesinin çizim çağrısından önce görüntülenen çağrısı.  
  
   > [!NOTE]
   >  `PSSetShader` görünmez **grafik olay listesi** penceresini bu çerçevesinde ayarlanmadı. Bu genellikle yalnızca tek bir piksel gölgelendiricisi tüm nesneleri için kullanılıyorsa veya gerçekleşir `PSSetShader` çağrısı sırasında bu çerçeve istemeden atlandı. Her iki durumda da, uygulamanın kaynak kodunu arama olan öneririz `PSSetShader` bu çağrılar davranışını incelemek için çağrıları ve geleneksel hata ayıklama teknikleri kullanın.  
  
2. Açık **grafik olay çağrı yığını** penceresi. Üzerinde **grafik tanılama** araç seçin **grafik olay çağrı yığını**.  
  
3. Çağrı yığınını bulmaya `PSSetShader` uygulamanızın kaynak kodunda çağırın. İçinde **grafik olay çağrı yığını** penceresinde en üst çağrı seçin ve piksel gölgelendiricisi ayarlanır değerini inceleyin. Piksel gölgelendirici ayarlanabilir, doğrudan boş veya null değeri, işlev veya başka bir duruma geçirilen bağımsız değişken nedeniyle oluşabilir. Doğrudan ayarlanmamışsa null değeri çağrı yığınını yere kaynağı bulacağından olabilir. Bu senaryoda, piksel gölgelendiricisi doğrudan kümesi olduğunu keşfedin `nullptr` en üstteki işlevinde olarak adlandırılmış `CubeRenderer::Render`:  
  
    ![Piksel gölgelendirici başlatmak olmayan kod](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-5.png "gfx_diag_demo_misconfigured_pipeline_step_5")  
  
   > [!NOTE]
   >  Çağrı yığını inceleyerek kaynağı null değerini bulamazsanız, üzerinde bir koşullu kesme noktası ayarlamanızı öneririz `PSSetShader` çağrı piksel gölgelendiricisi ayarladığınızda, programın yürütülmesini keser, null. Sonra uygulamayı hata ayıklama modunda yeniden başlatın ve null değer kaynağı bulmak için geleneksel hata ayıklama teknikleri kullanabilirsiniz.  
  
   Sorunu gidermek için ilk parametresini kullanarak doğru piksel gölgelendiricisi atama `ID3D11DeviceContext::PSSetShader` API çağrısı.  
  
   ![Düzeltilmiş C&#43; &#43; kaynak kodu](../debugger/media/gfx-diag-demo-misconfigured-pipeline-step-6.png "gfx_diag_demo_misconfigured_pipeline_step_6")  
  
   Kod düzelttikten sonra yeniden oluşturmak ve yeniden işleme sorunun çözüldüğünü doğrulamak için uygulamayı çalıştırın:  
  
   ![Nesne artık görüntülenen](../debugger/media/gfx-diag-demo-misconfigured-pipeline-resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")



