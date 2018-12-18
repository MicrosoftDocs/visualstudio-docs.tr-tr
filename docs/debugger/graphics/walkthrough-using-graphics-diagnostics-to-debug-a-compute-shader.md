---
title: 'İzlenecek yol: Hesaplayıcı Gölgelendiricisinde hata ayıklamak için grafik tanılamayı kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62c92a8b24dd3d932eedfcb122b4da9294dd3418
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949883"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>İzlenecek Yol: Hesaplayıcı Gölgelendiricisinde Hata Ayıklamak İçin Grafik Tanılamayı Kullanma
Bu izlenecek yol, Visual Studio grafik tanılama araçları hatalı sonuçlar üreten bir compute gölgelendiriciyi incelemek için nasıl kullanılacağını gösterir.  
  
 Bu örneklerde bu görevler gösterilir:  
  
-   Kullanarak **grafik olay listesi** olası sorun kaynaklarını bulmak için.  
  
-   Kullanarak **grafik olay çağrı yığını** hangi compute gölgelendiricisinin yürütüleceğini tarafından DirectCompute belirlemek için `Dispatch` olay.  
  
-   Kullanarak **grafik ardışık düzen aşamaları** penceresini ve HLSL hata ayıklayıcısı sorunun kaynağı olan compute gölgelendiriciyi incelemek için.  
  
## <a name="scenario"></a>Senaryo  
 Bu senaryoda, benzetim güncelleştirmesinin hesaplama açısından en yoğun bölümlerini gerçekleştirmek için DirectCompute kullanan bir Akışkan dinamiği benzetimi yazdınız. Uygulamayı çalıştırdığınızda, veri kümesi ve UI işlenmesi doğru görünür, ancak benzetim beklendiği gibi davranmaz. Grafik tanılamayı kullanarak sorunu bir grafik günlüğüne böylece uygulamanın hatalarını ayıklayabilir miyim yakalayabilirsiniz. Sorun, uygulamada şu şekilde görünür:  
  
 ![Benzetimli sıvı yanlış şekilde davranır. ](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Grafik sorunlarını grafik günlüğünde yakalama hakkında daha fazla bilgi için bkz: [Capturing Graphics Information](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Araştırma  
 Grafik tanılama araçları, yakalanan kareleri inceleyebilmeniz için grafik günlük dosyasını yüklemek için kullanabilirsiniz.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için  
  
1. Visual Studio'da, yanlış benzetim sonuçlarının gösterildiği çerçeveyi içeren grafik günlüğünü yükleyin. Yeni bir grafik Tanılama sekmesi Visual Studio'da görünür. Bu sekmenin üst kısmında seçilen çerçevenin işleme hedefi çıktısı ' dir. Alt parçasıdır **çerçeve listesi**, bir küçük resim her yakalanan çerçeve görüntüler.  
  
2. İçinde **çerçeve listesi**, yanlış benzetim davranışını gösteren bir çerçeve seçin. Hata benzetimi kod ve işleme kodu değil gibi görünüyor olsa da, yine de DirectCompute olayları, Direct3D olaylarıyla birlikte çerçeve çerçeve olarak yakalandığından bir çerçeve seçmeniz gerekir. Bu senaryoda, grafik sekmesi şu şekilde görünür günlük:  
  
    ![Grafik belgesi Visual Studio'da oturum açın. ](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
   Sorunu gösteren bir çerçeveyi seçtikten sonra kullanabileceğiniz **grafik olay listesi** tanılamak için. **Grafik olay listesi** her DirectCompute çağrısı ve etkin çerçeve sırasında yapılan her Direct3D API çağrısı için bir olay içerir — örneğin, GPU üzerinde hesaplama çalıştırmak için veya veri kümesi veya Arabirimi işlemek için API çağrısı. Bu durumda, ilgileniriz `Dispatch` GPU'da çalışan Benzetimin parçalarını temsil eden olayları.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Benzetimi güncelleştirmesine ilişkin dağıtma olayını bulmak için  
  
1. Üzerinde **grafik tanılama** araç seçin **olay listesi** açmak için **grafik olay listesi** penceresi.  
  
2. İnceleme **grafik olay listesi** veri kümesini oluşturan çizim olayı için. Bunu kolaylaştırmak için girin `Draw` içinde **arama** sağ üst köşesinde kutusunda **grafik olay listesi** penceresi. Bu, yalnızca başlıklarında "Çiz" olan olaylar içeren listenin filtreler. Bu senaryoda, bunların olaylarının gerçekleştiğini keşfedersiniz oluştu:  
  
    ![Olay listesi &#40;EL&#41; çizmek olayları gösterir. ](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3. Grafik günlük belgesi sekmesindeki oluşturma hedef izlerken her çizim olayının üzerinden geçin.  
  
4. İşleme hedefi işlenmiş dataseti ilk kez görüntülediğinde durdurun. Bu senaryoda, ilk çizim olayında veri kümesi oluşturulur. Benzetimdeki hata gösterilmiştir:  
  
    ![Bu benzetimi veri kümesi olay işleme çizin. ](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5. Şimdi **grafik olay listesi** için `Dispatch` benzetimi güncelleştiren bir olay. Benzetim oluşturulmadan önce güncelleştirildiğinden emin olma olasılığı yüksektir çünkü, ilk hakkında yoğunlaşabilirsiniz `Dispatch` sonuçlarını işleyen çizim olayından önce oluşan olaylar. Bunu kolaylaştırmak için değiştirme **arama** kutusun `Draw;Dispatch;CSSetShader(`. Hem de içeren bu liste filtreler `Dispatch` ve `CSSetShader` çizim olaylarına ek olarak olaylar. Bu senaryoda olduğunu fark birkaç `Dispatch` Olaylar oluştuysa çizim olayından önce:  
  
    ![Çizim EL gösterir, gönderme ve CSSetShader olayları](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
   Artık, büyük olasılıkla pek çok az sayıda bildiğinize göre `Dispatch` olayların soruna karşılık gelen, daha ayrıntılı olarak inceleyebilirsiniz.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Hangi dağıtım çağrısına gölgelendirici yürüttüğünü belirlemek için  
  
1. Üzerinde **grafik tanılama** araç seçin **olay çağrı yığını** açmak için **grafik olay çağrı yığını** penceresi.  
  
2. Benzetim sonuçlarını işleyen çizim olayından başlayarak her geriye önceki `CSSetShader` olay. Ardından **grafik olay çağrı yığını** penceresinde çağrı sitesine gitmek için en üstteki işlevi seçin. İlk parametresini kullanabilirsiniz çağıran sitede [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) işlev çağrısı hangi compute gölgelendiricisinin yürütüleceğini tarafından sonraki belirlemek için `Dispatch` olay.  
  
   Bu senaryoda, üç çift vardır `CSSetShader` ve `Dispatch` her çerçevede olayları. Geriye doğru tümleştirme adımını (burada sıvı Parçacıklar gerçekten taşınır) üçüncü çifti temsil çalışırken, ikinci çift hesaplamayı zorla adımını (burada her parçacığı etkileyen güçleri hesaplanır) temsil eder ve ilk çift temsil eder Yoğunluk hesaplama adımını.  
  
#### <a name="to-debug-the-compute-shader"></a>Bilgisayar gölgelendiricide hata ayıklamak için  
  
1. Üzerinde **grafik tanılama** araç seçin **ardışık düzen aşamaları** açmak için **grafik ardışık düzen aşamaları** penceresi.  
  
2. Üçüncü seçin `Dispatch` olay (çizim olayından hemen önce gelen bir) ve ardından **grafik ardışık düzen aşamaları** penceresi altında **hesaplayıcı gölgelendiricisi** aşama öğesini  **Hata Ayıklamayı Başlat**.  
  
    ![Üçüncü dağıtma olayını seçme içinde EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
    HLSL hata ayıklayıcı tümleştirme adımını gerçekleştiren gölgelendiricide başlatılır.  
  
3. Hatanın kaynağını aramak için tümleştirme adımının compute gölgelendirici kaynak kodunu inceleyin. HLSL compute-gölgelendirici kodunda hata ayıklamak için grafik tanılama kullandığınızda, kod içinde gezinebilmek ve izleme pencereleri gibi diğer bilinen hata giderme araçlarını kullanın. Bu senaryoda, yok görünüyor, tümleştirme adımını gerçekleştiren hesaplayıcı gölgelendiricisinde hata olarak belirleyin.  
  
    ![IntegrateCS compute gölgelendirici hata ayıklaması. ](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4. Bilgisayar gölgelendiricide hata ayıklamayı durdurmak için **hata ayıklama** araç seçin **hata ayıklamayı Durdur** (klavye: Shift + F5).  
  
5. Ardından, ikinci seçin `Dispatch` olay ve önceki adımda yaptığınız gibi compute gölgelendirici hata ayıklamayı Başlat.  
  
    ![İkinci dağıtma olayını seçme içinde EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
    HLSL hata ayıklayıcısı, her sıvı parçacık üzerinde etkin olan kuvvetleri hesaplayan bir gölgelendirici sırasında başlatılır.  
  
6. Zorla hesaplama adımı için compute gölgelendirici kaynak kodunu inceleyin. Bu senaryoda hatanın kaynağının burada olduğunu belirlersiniz.  
  
    ![Hata ayıklama ForceCS&#95;basit gölgelendirici işlem. ](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
   Hatanın konumunu belirledikten sonra hata ayıklamayı durdurmak ve etkileşim kuran Parçacıklar arasındaki mesafeyi doğru hesaplamak için compute gölgelendirici kaynak kodunu değiştirin. Bu senaryoda, yalnızca satırın değiştirdiğiniz `float2 diff = N_position + P_position;` için `float2 diff = N_position - P_position;`:  
  
   ![Düzeltilmiş işlem&#45;gölgelendirici kodu. ](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
   Hesaplayıcı gölgelendiricileri çalışma zamanında derlendiğinden nasıl bunların benzetim üzerindeki etkisini gözlemlemek için değişiklikler yaptıktan sonra bu senaryoda, yalnızca uygulamayı yeniden başlatabilirsiniz. Uygulamayı yeniden oluşturmanız gerekmez. Uygulamayı çalıştırdığınızda, şimdi Benzetimin doğru olduğunu keşfedin.  
  
   ![Benzetimli sıvı doğru şekilde davranır. ](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")