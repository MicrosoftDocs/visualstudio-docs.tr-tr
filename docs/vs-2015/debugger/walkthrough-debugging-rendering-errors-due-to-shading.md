---
title: 'İzlenecek yol: Gölgeleme nedeniyle çıkan oluşturma hatalarını ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d65c3d2525533e5881b4626941e43fb302ce2aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733190"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda nasıl kullanılacağını gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gölgelendirici hata nedeniyle yanlış renklendirilmiştir nesneyi incelemek için grafik tanılama.  
  
 Bu izlenecek yol gösterir nasıl yapılır:  
  
-   Sorunu gösteren piksel tanımlamak için grafik günlük belgesi inceleyin.  
  
-   Kullanım **grafik piksel geçmişi** penceresini piksel durumu daha yakından inceleyin.  
  
-   Kullanım **HLSL hata ayıklayıcısı** piksel ve köşe gölgelendiricileri incelemek için.  
  
## <a name="scenario"></a>Senaryo  
 Yaygın olarak yanlış renklendirme nesneler üzerinde bir köşe gölgelendiricisi piksel geçtiğinde gerçekleşir gölgelendirici yanlış veya tamamlanmamış bilgiler.  
  
 Bu senaryoda, kısa süre önce bir nesne yanı sıra yeni köşe ve piksel gölgelendiricileri benzersiz bir görünüm sunar ve nesneyi dönüştürmek için uygulamanıza eklediğiniz. Test sırasında uygulamayı çalıştırdığınızda, nesne düz bir siyah olarak işlenir. Böylece uygulamanın hatalarını ayıklayabilir miyim grafik tanılamayı kullanarak sorunu bir grafik günlüğüne yakalayın. Sorun, uygulamada şu şekilde görünür:  
  
 ![Nesne yanlış renk ile işlenir. ](../debugger/media/gfx-diag-demo-render-error-shader-problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Araştırma  
 Grafik tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük belgesi yükleyebilirsiniz.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eksik model sergiler çerçeveyi içeren grafik günlüğünü yükleyin. Yeni bir grafik günlüğü belge penceresi görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu pencerenin üst kısmında seçilen çerçevenin işleme hedefi çıktısı ' dir. Alt parçasıdır **çerçeve listesi**, bir küçük resim her yakalanan çerçeve görüntüler.  
  
2. İçinde **çerçeve listesi**, hangi nesne yok doğru görünümünü bir çerçeve seçin. İşleme hedefi, Seçilen çerçevenin yansıtacak şekilde güncelleştirilir. Bu senaryoda, grafik belge penceresi şöyle günlük:  
  
    ![Grafik belgesi Visual Studio'da oturum açın. ](../debugger/media/gfx-diag-demo-render-error-shader-step-1.png "gfx_diag_demo_render_error_shader_step_1")  
  
   Sorunu gösteren bir çerçeveyi seçtikten sonra kullanabileceğiniz **grafik piksel geçmişi** tanılamak için penceresi. **Grafik piksel geçmişi** penceresinde belirli bir piksel, kendi gölgelendiricileri ne etkilerini işleme hedef, kronolojik olarak başlatılmalı ve üzerinde bir etkisi olan temelleri gösterilir.  
  
#### <a name="to-examine-a-pixel"></a>Bir pikselin incelemek için  
  
1. Açık **grafik piksel geçmişi** penceresi. Üzerinde **grafik tanılama** araç seçin **piksel geçmişi**.  
  
2. İncelemek için bir piksel seçin. Grafik günlüğü belge penceresinde yanlış renkli nesne üzerinde piksel birini seçin:  
  
    ![Bir pikselin seçerek, buna ait geçmişi hakkında bilgi görüntüler. ](../debugger/media/gfx-diag-demo-render-error-shader-step-2.png "gfx_diag_demo_render_error_shader_step_2")  
  
    **Grafik piksel geçmişi** penceresinde, seçilen piksel yansıtacak şekilde güncelleştirilir. Bu senaryoda, **grafik piksel geçmişi** penceresi şu şekilde görünür:  
  
    ![Piksel geçmişi bir DrawIndexed olay gösterir. ](../debugger/media/gfx-diag-demo-render-error-shader-step-3.png "gfx_diag_demo_render_error_shader_step_3")  
  
    Piksel gölgelendiricinin sonucu tamamen opak siyah (0, 0, 0, 1) ve fark **çıkış Birleştiricisi** bu birleşik **önceki** şekilde piksel rengi, **sonucu** tamamen opak siyahtır.  
  
   Yanlış renkli bir pikseli inceleyebilir ve piksel gölgelendirici çıkış rengi beklenen olmadığını fark sonra piksel gölgelendiricisi incelemek ve nesnenin rengini neler olduğunu öğrenmek için HLSL Hata Ayıklayıcısı'nı kullanabilirsiniz. HLSL hata ayıklayıcısı, HLSL kodu adımlayın yürütme sırasında HLSL değişkenleri durumunu incelemek için kullanın ve sorunu tanılamanıza yardımcı olmak için kesme noktaları ayarlayın.  
  
#### <a name="to-examine-the-pixel-shader"></a>Piksel gölgelendirici incelemek için  
  
1. Piksel gölgelendirici hatalarını ayıklamaya başlayın. İçinde **grafik piksel geçmişi** penceresinde nesnenin ilkel yanındaki **piksel gölgelendiricisi**, seçin **hata ayıklamayı Başlat** düğmesi.  
  
2. Piksel gölgelendirici rengi üzerinden köşe gölgelendiricisi, yalnızca geçirir. Bu senaryoda, piksel gölgelendiricisi sorunun kaynağına değil gözlemlemek kolay olmasıdır.  
  
3. Üzerinde işaretçiyi `input.color`. Değeri tam olarak donuk siyah (0, 0, 0, 1) olduğuna dikkat edin.  
  
    !["Rengi", "Giriş" siyah üyesidir. ](../debugger/media/gfx-diag-demo-render-error-shader-step-5.png "gfx_diag_demo_render_error_shader_step_5")  
  
    Bu senaryoda, inceleme, yanlış renk büyük olasılıkla üzerinde çalışılacak piksel gölgelendiricisinin doğru renk bilgilerini sağlamayan bir köşe gölgelendiricisi sonucu olduğunu gösterir.  
  
   Köşe gölgelendirici doğru bilgileri piksel gölgelendiricisi için sağladığını büyük olasılıkla saptadıktan sonra sonraki adıma köşe gölgelendiricisi incelemektir.  
  
#### <a name="to-examine-the-vertex-shader"></a>Köşe gölgelendirici incelemek için  
  
1. Köşe gölgelendirici hatalarını ayıklamaya başlayın. İçinde **grafik piksel geçmişi** penceresinde nesnenin ilkel yanındaki **köşe gölgelendiricisi**, seçin **hata ayıklamayı Başlat** düğmesi.  
  
2. Köşe gölgelendiricinin çıktı yapısını bulun — piksel gölgelendirici için giriş budur. Bu senaryoda, bu yapı adıdır `output`. Köşe gölgelendirici kodu inceleyerek dikkat `color` üyesi `output` yapısı açıkça tam olarak donuk siyah olarak ayarlandı, belki de sonucunda birisi çalışmalarını hata ayıklıyor.  
  
3. Renk üye giriş yapısında hiçbir zaman kopyalandığını onaylayın. Çünkü değerini `output.color` tamamen opak siyah olarak hemen önce ayarlanır `output` yapısı döndürülür, emin olmak için iyi bir fikirdir değerini `output` düzgün bir şekilde bir önceki satırdaki başlatıldığından değildi. Ayarlayan satırdan ulaşana kadar köşe gölgelendirici kodu adımlayın `output.color` değerini izlerken siyaha `output.color`. Dikkat değerini `output.color` siyah olarak ayarlamadığınız başlatılmadı. Bu kod satırının ayarlar onaylar `output.color` için siyah değiştiren yerine silindi.  
  
    !["Output.color" siyah değeridir. ](../debugger/media/gfx-diag-demo-render-error-shader-step-7.png "gfx_diag_demo_render_error_shader_step_7")  
  
   İşleme sorunun nedenini köşe gölgelendiricisi için piksel gölgelendiricisinin doğru renk değeri sağlamaz olduğunu belirledikten sonra sorunu gidermek için bu bilgileri kullanabilirsiniz. Bu senaryoda, köşe gölgelendiricisi aşağıdaki kodda değiştirerek düzeltebilirsiniz  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 to  
  
```hlsl  
output.color = input.color;  
```  
  
 Bu kod, köşe rengi üzerinden yalnızca üzerinde değişiklik yapılmadan nesnenin köşesinden geçirir. — daha karmaşık köşe gölgelendiricileri değiştirme rengi aracılığıyla iletmeden önce. Düzeltilmiş köşe gölgelendirici kodu şuna benzemelidir:  
  
 ![Düzeltilmiş köşe gölgelendirici kodu. ](../debugger/media/gfx-diag-demo-render-error-shader-step-8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Kod giderdikten sonra onu yeniden oluşturun ve yeniden işleme sorunun çözüldüğünü bulmak için uygulamayı çalıştırın.  
  
 ![Nesne doğru renklerle işlenir. ](../debugger/media/gfx-diag-demo-render-error-shader-resolution.png "gfx_diag_demo_render_error_shader_resolution")



