---
title: 'İzlenecek yol: Köşe gölgeleme nedeniyle nesnelerin eksikliği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ecff22d99eb995f0dbe70e93783460f4343d74f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745933"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>İzlenecek Yol: Köşe Gölgeleme Nedeniyle Nesnelerin Eksikliği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda nasıl kullanılacağını gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] köşe gölgelendirici aşaması sırasında oluşan bir hata nedeniyle eksik bir nesne incelemek için grafik tanılama araçları.  
  
 Bu örneklerde bu görevler gösterilir:  
  
-   Kullanarak **grafik olay listesi** olası sorun kaynaklarını bulmak için.  
  
-   Kullanarak **grafik ardışık düzen aşamaları** etkisini denetlemek için pencere `DrawIndexed` Direct3D API'sini çağırır.  
  
-   Kullanarak **HLSL hata ayıklayıcısı** köşe gölgelendiricisi incelemek için.  
  
-   Kullanarak **grafik olay çağrı yığını** yanlış bir HLSL sabiti kaynağını bulmaya yardımcı olacak.  
  
## <a name="scenario"></a>Senaryo  
 Eksik bir nesnenin bir 3B uygulamada sık karşılaşılan nedenlerinden oluşur köşe gölgelendiricisi nesnenin köşe hatalı veya beklenmedik bir şekilde dönüştürür — Örneğin, nesne çok küçük bir boyuta ölçeklendirilir veya kamera göründüğü şekilde dönüştürülmüş , yerine önündeki.  
  
 Bu senaryoda, test etmek için uygulamayı çalıştırdığınızda, arka plan beklendiği gibi işlenir ancak nesnelerinden birine görünmez. Böylece uygulamanın hatalarını ayıklayabilir miyim grafik tanılamayı kullanarak sorunu bir grafik günlüğüne yakalayın. Sorun, uygulamada şu şekilde görünür:  
  
 ![Nesne görülebilir değildir. ](../debugger/media/gfx-diag-demo-missing-object-shader-problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Araştırma  
 Grafik tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük dosyasını yükleyebilirsiniz.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eksik nesne sergiler çerçeveyi içeren grafik günlüğünü yükleyin. Yeni bir grafik günlüğü sekmesi görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu sekmenin üst kısmında seçilen çerçevenin işleme hedefi çıktısı ' dir. Alt parçasıdır **çerçeve listesi**, bir küçük resim her yakalanan çerçeve görüntüler.  
  
2. İçinde **çerçeve listesi**, nesne görüntülenmez gösteren bir çerçeve seçin. İşleme hedefi, Seçilen çerçevenin yansıtacak şekilde güncelleştirilir. Bu senaryoda, grafik sekmesi şu şekilde görünür günlük:  
  
    ![Grafik belgesi Visual Studio'da oturum](../debugger/media/gfx-diag-demo-missing-object-shader-step-1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
   Sorunu gösteren bir çerçeveyi seçtikten sonra kullanarak tanılamak başlayabilirsiniz **grafik olay listesi**. **Grafik olay listesi** etkin çerçeve için işlemek için yapılan her Direct3D API çağrısı cihaz durumunu ayarlamak için oluşturun ve arabellek güncelleştirin ve çerçeve içinde görünen nesneler çizmek için API çağrısı içerir. Olduğundan çağrılarının pek çok ilgi çekici genellikle (ama her zaman kullanılmaz) karşılık gelen bir uygulamada beklendiği gibi çalışırken işleme hedefi değişiklik örneğin çizme, gönderme, kopyalama veya açık çağrıları. Her bir uygulama oluşturulmasını geometri temsil ettiğinden çizim çağrıları özellikle ilgi çekici (gönderme çağrılar da de geometri oluşturma).  
  
   Eksik nesne işleme hedefine (Bu örnekte) olması nedeniyle dikkatin değil olduğunu bildiğiniz — Sahne geri kalanı, beklendiği gibi çizilir. ancak bu — kullanabileceğiniz **grafik olay listesi** ile birlikte **grafik ardışık düzen Aşamalar** , çizim çağrısı çıktılarının belirlemek için aracı için eksik nesne geometrisinin karşılık gelir. **Grafik ardışık düzen aşamaları** penceresi işleme hedefi üzerindeki etkisini bağımsız olarak her bir çizim çağrısına gönderildiği geometri gösterir. Çizim çağrıları arasında taşırken, ardışık düzen aşamaları bu çağrıyla ilişkili geometri gösterecek şekilde güncelleştirilir ve işleme hedefi çıktısı çağrı tamamlandıktan sonra işleme hedefi durumunu göstermek için güncelleştirilir.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Çizim çağrısı için eksik geometri bulmak için  
  
1. Açık **grafik olay listesi** penceresi. Üzerinde **grafik tanılama** araç seçin **olay listesi**.  
  
2. Açık **grafik ardışık düzen aşamaları** penceresi. Üzerinde **grafik tanılama** araç seçin **ardışık düzen aşamaları**.  
  
3. Her geçerken çağrı çizin **grafik olay listesi** penceresi, watch **grafik ardışık düzen aşamaları** eksik nesnesinin penceresi. Bunu kolaylaştırmak için "Çiz" girin **arama** sağ üst köşesinde kutusunda **grafik olay listesi** penceresi. Bu, yalnızca başlıklarında "Çiz" olan olaylar içeren listenin filtreler.  
  
    İçinde **grafik ardışık düzen aşamaları** penceresinde **giriş Assembler** aşaması nesne geometrisinin, dönüştürülen önce gösterir ve **köşe gölgelendiricisi** aşama aynı gösterir Bunu dönüştürüldükten sonra nesne. Bu senaryoda, görüntülendiğinde eksik nesne buldunuz bilmeniz **giriş Assembler** aşama ve hiçbir şey görüntülenir **köşe gölgelendiricisi** aşaması.  
  
   > [!NOTE]
   >  Varsa diğer geometri aşamaları — Örneğin, kabuk gölgelendiricisi, etki alanı gölgelendiricisi ve geometri gölgelendirici aşamaları — nesneyi işlemek, sorunun nedenini olması olabilir. Genellikle, erken aşama sonucu görüntülenmez veya beklenmedik bir şekilde görüntülenir sorun ilgilidir.  
  
4. Eksik bir nesneye karşılık gelen bir çizim çağrısı ulaştığında durdurun. Bu senaryoda, **grafik ardışık düzen aşamaları** penceresi geometri (giriş Assembler küçük resim gösterilir) GPU verildiğini gösterir, ancak yanlış sırasında bir sorun nedeniyle işleme hedefi görünmüyor Köşe gölgelendirici aşaması (köşe gölgelendiricisi küçük resim gösterilir):  
  
    ![DrawIndexed olay ve işlem hattı üzerindeki etkisini](../debugger/media/gfx-diag-demo-missing-object-shader-step-2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
   Sonra uygulamayı bir çizim çağrısı eksik nesne geometrisinin için verilen onaylayın ve Bul köşe gölgelendirici aşaması sırasında sorun ortaya, HLSL hata ayıklayıcısı, köşe gölgelendiricisi incelemek ve nesne geometrisinin neler olduğunu öğrenmek için kullanabilirsiniz. HLSL hata ayıklayıcısı, HLSL kodu adımlayın yürütme sırasında HLSL değişkenleri durumunu incelemek için kullanın ve sorunu tanılamanıza yardımcı olmak için kesme noktaları ayarlayın.  
  
#### <a name="to-examine-the-vertex-shader"></a>Köşe gölgelendirici incelemek için  
  
1. Köşe gölgelendirici aşaması hatalarını ayıklamaya başlayın. İçinde **grafik ardışık düzen aşamaları** penceresi altında **köşe gölgelendiricisi** aşama öğesini **hata ayıklamayı Başlat** düğmesi.  
  
2. Çünkü **giriş Assembler** aşama görünür iyi verileri köşe gölgelendiricisine sağlamak ve **köşe gölgelendiricisi** aşama görünür hiçbir çıktı oluşturmak için köşe gölgelendiricisi çıkışı incelemek istediğiniz yapısı, `output`. HLSL kodunuz içinde adım adım olarak, bir daha yakın olması ne zaman Ara `output` değiştirilir.  
  
3. İlk kez `output` değiştirildiğinde, üye `worldPos` yazılır.  
  
    !["Output.worldPos" değerini makul görünür](../debugger/media/gfx-diag-demo-missing-object-shader-step-4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
    Değerini makul gibi göründüğünden, değiştiren sonraki satıra kadar kod içerisinde ilerlemeye devam `output`.  
  
4. Bir sonraki `output` değiştirildiğinde, üye `pos` yazılır.  
  
    !["Output.pos" değerini çıkış zeroed](../debugger/media/gfx-diag-demo-missing-object-shader-step-5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
    Bu süre, değerini `pos` üye — sıfırlardan — şüpheli görünüyor. Ardından, belirlemek istediğiniz nasıl `output.pos` gelen sıfır değerine sahip.  
  
5. Olduğunu fark edersiniz `output.pos` adlı bir değişken değerini alan `temp`. Önceki satırında gördüğünüz değerini `temp` önceki değerine adlı bir sabit ile çarpılmasıyla elde edilen sonucu olan `projection`. Bu şüpheli `temp`ait şüpheli değerdir bu Çarpım sonucunu. Üzerinde işaretçiyi getirdiğinizde `projection`, değeri de sıfırlardan olduğuna dikkat edin.  
  
    ![Projeksiyon matris hatalı bir dönüşüm içeren](../debugger/media/gfx-diag-demo-missing-object-shader-step-6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
    Bu senaryoda, inceleme, ortaya çıkarır `temp`ait şüpheli değer büyük olasılıkla kendi çarpım kaynaklanan `projection`ve çünkü `projection` bir projeksiyon matris içerecek şekilde hazırlanmıştır sabittir olmaması gerektiği olduğunu bildiğiniz Tüm sıfırları içerir.  
  
   Karar verdikten sonra HLSL sabiti `projection`— gölgelendirici uygulamanız tarafından geçirilen — olası kaynak sorununu, sonraki adım, uygulamanızın kaynak kodunda konumu bulmak için nereye sabit arabelleğini girilir. Kullanabileceğiniz **grafik olay çağrı yığını** bu konumu bulunamadı.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Uygulamanızın kaynak kodunda sabiti ayarlandığı bulmak için  
  
1. Açık **grafik olay çağrı yığını** penceresi. Üzerinde **grafik tanılama** araç seçin **grafik olay çağrı yığını**.  
  
2. Uygulamanızın kaynak koda çağrı yığınında yukarı gidin. İçinde **grafik olay çağrı yığını** penceresinde sabit arabelleğini var. dolu olmadığını görmek için en üstteki arama seçin. Yüklü değilse, burada da girilir bulana kadar çağrı yığınının devam edin. Bu senaryoda, sabit arabelleğini doldurulmuş olduğunu keşfedin; kullanarak `UpdateSubresource` Direct3D API — daha fazla, adlı bir işlev çağrı yığınında yukarı `MarbleMaze::Render`, ve adlı bir sabit arabellek nesneden değeri gelen `m_marbleConstantBufferData` :  
  
    ![Nesnenin sabit arabelleğini ayarlayan kodu](../debugger/media/gfx-diag-demo-missing-object-shader-step-7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
   > [!TIP]
   >  Uygulamanız aynı anda hata ayıklaması yapıyorsanız bu konumda bir kesme noktası ayarlayabilirsiniz ve sonraki kare işlendiğinde ulaşılır. Ardından üyelerini inceleyebilirsiniz `m_marbleConstantBufferData` onaylamak için değerini `projection` üyesi sabit arabelleğini dolduğunda tümü sıfır olarak ayarlayın.  
  
   Burada sabit arabelleğini doldurulur konum bulun ve değerleri değişkeninden geldiğini bulmak sonra `m_marbleConstantBufferData`, sonraki adıma nereden bulmaktır `m_marbleConstantBufferData.projection` üye tümü sıfır olarak ayarlanır. Kullanabileceğiniz **tüm başvuruları Bul** hızla değerini değiştirir kodunu tarama `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Yansıtma üyesi, uygulamanızın kaynak kodunda belirlendiği bulmak için  
  
1. Başvuruları Bul `m_marbleConstantBufferData.projection`. Değişken için kısayol menüsünü açın `m_marbleConstantBufferData`ve ardından **tüm başvuruları Bul**.  
  
2. Uygulamanızın kaynak kodundaki satır konumuna gitmek için burada `projection` üye değiştirilmişse, bu satırda seçin **sembol sonuçları Bul** penceresi. Yansıtma üyesi değiştiren ilk sonucu sorunun nedeni olabileceğinden, uygulamanızın kaynak kodunun çeşitli alanları incelemek olabilir.  
  
   Konumun bulduktan sonra nerede `m_marbleConstantBufferData.projection` , yanlış bir değer kökenini belirlemek için çevreleyen kaynak kodu inceleyebilirsiniz ayarlanmış. Bu senaryoda olduğunu fark değerini `m_marbleConstantBufferData.projection` adlı yerel bir değişken `projection` kod tarafından verilen bir değere başlatılmadan önce `m_camera->GetProjection(&projection);` sonraki satıra.  
  
   ![Marble projeksiyon başlatma önce ayarlanır](../debugger/media/gfx-diag-demo-missing-object-shader-step-9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
   Sorunu gidermek için değerini ayarlar kod satırına Taşı `m_marbleConstantBufferData.projection` yerel değişkenin değerini başlatır satırdan `projection`.  
  
   ![Düzeltilmiş C&#43; &#43; kaynak kodu](../debugger/media/gfx-diag-demo-missing-object-shader-step-10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
   Kod düzelttikten sonra yeniden oluşturmak ve yeniden işleme sorunun çözüldüğünü bulmak için uygulamayı çalıştırın:  
  
   ![Şimdi nesnesinde görüntülenir. ](../debugger/media/gfx-diag-demo-missing-object-shader-resolution.png "gfx_diag_demo_missing_object_shader_resolution")



