---
title: Grafik ardışık düzen aşamaları | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da74af0f77586e518365fa669c84309e7751b319
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941568"
---
# <a name="graphics-pipeline-stages"></a>Grafik Ardışık Düzen Aşamaları
Grafik ardışık düzen Aşamaları penceresinde bir bağımsız çizim çağrısı Direct3D grafik Ardışık düzenin her aşaması tarafından nasıl dönüştürdüğünü anlamanıza yardımcı olur.  
  
 Bu ardışık düzen Aşamaları penceresinde.  
  
 ![Bir 3B nesneyi ardışık düzen aşamaları gider.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Grafik ardışık düzen Aşamaları penceresinde anlama  
 Ardışık Düzen Aşamaları penceresinde grafik ardışık düzeninin her aşamasında sonucu, her bir çizim çağrısı için ayrı ayrı görselleştirir. Normalde, bir işleme sorunuyla başlatıldığı bildirmek zorlaştıran ortasında ardışık düzen aşamaları sonuçlarını gizlidir. Her aşama ayrı olarak görselleştirerek ardışık düzen Aşamaları penceresinde sorunun başladığı görmeyi kolaylaştırır — Örneğin, kolayca köşe gölgelendirici aşaması beklenmedik bir şekilde off-screen çizilecek nesneyi sebep olduğunda görebilirsiniz.  
  
 Sorunun oluştuğu aşama tanımladıktan sonra verileri nasıl yorumlandığını veya dönüştürülmüş incelemek için bir grafik Çözümleyicisi araçları kullanabilirsiniz. Ardışık Düzen aşamaları görünen işleme sorunlarını çoğunlukla ilgili yanlış köşe biçim tanımlayıcıları, çalışmalarında gölgelendirici program veya yanlış yapılandırılmış durum olur.  
  
### <a name="links-to-related-graphics-objects"></a>İlişkili grafik nesneleri bağlantılar  
 Neden bir çizim çağrısı belirli bir şekilde grafik ardışık düzen ile etkileşime giren belirlemek için bazen ek bağlam gerekir. Bu ek bağlam bulmayı kolaylaştırmak için grafik işlem hattında neler grafik ardışık düzen Aşamaları penceresinde bağlantılar ek bağlam sağlamak veya daha fazla nesne ilişkili.  
  
- Direct3D 12'deki bu nesne, genellikle komut listesi alır.  
  
- Direct3D 11'de bu nesne, genellikle bir grafik cihaz bağlamı olur.  
  
  Bu bağlantıların grafik ardışık düzen aşamaları penceresinin sol alt köşesinde bulunan geçerli grafik olay imzası bir parçasıdır. Herhangi bir nesne hakkında daha ayrıntılı incelemek için bu bağlantıları izleyin.  
  
### <a name="viewing-and-debugging-shader-code"></a>Görüntüleme ve gölgelendirici kodunda hata ayıklama  
 İnceleyin ve ardışık düzen Aşamaları penceresinde ilgili kendi aşamaları alttaki denetimleri kullanarak köşe, kabuk, etki alanı, geometri ve piksel gölgelendiricilerini kod hata ayıklama.  
  
#### <a name="to-view-a-shaders-source-code"></a>Gölgelendiricinin kaynak kodunu görüntülemek için  
  
-   İçinde **grafik ardışık düzen aşamaları** penceresinde gölgelendirici için karşılık gelen gölgelendirici aşamasını bulun incelemeniz gerekebilir. Daha sonra Önizleme görüntüsünü gölgelendirici aşaması odkaz na nadpis izleyin — Örneğin, bağlantıyı izleyerek **köşe gölgelendiricisi obj:30** köşe gölgelendirici kaynak kodunu görüntülemek için.  
  
    > [!TIP]
    >  Nesne sayısı **obj:30**, olduğu gibi nesne tablosu ve piksel geçmişini penceresi gibi grafik Çözümleyicisi arabirimi içinde bu gölgelendiriciyi tanımlar.  
  
#### <a name="to-debug-a-shader"></a>Gölgelendirici hata ayıklamak için  
  
-   İçinde **grafik ardışık düzen aşamaları** penceresinde gölgelendirici için karşılık gelen gölgelendirici aşamasını bulun, hata ayıklamak istediğiniz. Önizleme görüntüsü seçin **hata ayıklamayı Başlat**. Bu giriş noktasına karşılık gelen aşamanın gölgelendirici ilk çağrıya HLSL hata ayıklayıcısı varsayılanlara — diğer bir deyişle, ilk piksel, Tepe veya temel nesne bu çizim çağrısı sırasında gölgelendirici tarafından işlenir. Bu belirli piksel veya köşe gölgelendiricisi çağrıları üzerinden erişilebilir **grafik piksel geçmişi**.  
  
### <a name="the-pipeline-stages"></a>Ardışık Düzen aşamaları  
 Ardışık Düzen Aşamaları penceresinde yalnızca çizim çağrısı sırasında etkin ardışık düzen aşamaları görselleştirir. Grafik ardışık düzeninin her aşamasında, önceki aşamaya girişten dönüştürür ve sonuç sonraki aşamaya geçer. İlk aşama — giriş derleyici — dizin ve köşe verileri uygulamanızdan; giriş olarak alır son aşama — çıkış Birleştiricisi — yeni piksel framebuffer geçerli içerikle birlikte çizilir veya işleme hedefi çıktısı, ekranda gördüğünüz son görüntü üretmek için olarak birleştirir.  
  
> [!NOTE]
>  Hesaplayıcı gölgelendiricilerde desteklenmez **grafik ardışık düzen aşamaları** penceresi.  
  
 **Giriş Birleştiricisi**  
 Giriş derleyicisi, uygulamanız tarafından belirtilen dizin ve köşe verileri okur ve için grafik donanımının birleştirir.  
  
 Ardışık Düzen Aşamaları penceresinde giriş Assembler çıkışı Tel Çerçeve model olarak görselleştirilir. Sonuç birine daha yakından bakalım için seçin **giriş Assembler** içinde **grafik ardışık düzen aşamaları** tam 3B Model Düzenleyicisi'ni kullanarak içinde birleştirilmiş köşeleri görüntülemek üzere penceresi.  
  
> [!NOTE]
>  Varsa `POSITION` anlam giriş derleyici çıktısında mevcut değil ve hiçbir şey görüntülenen **giriş derleyici** aşaması.  
  
 **Köşe gölgelendirici**  
 Köşe gölgelendirici aşaması skinning ve ışık dönüşüm gibi işlemleri genellikle köşeleri işler. Köşe gölgelendirici oluşturmak, alan köşeler aynı sayıda girdi olarak.  
  
 Ardışık Düzen Aşamaları penceresinde, köşe gölgelendiricisi çıkışı bir Tel Çerçeve ızgara görüntüsü olarak görselleştirilir. Sonuç birine daha yakından bakalım için seçin **köşe gölgelendiricisi** içinde **grafik ardışık düzen aşamaları** Resim Düzenleyicisi'nde işlenen köşeleri görüntülemek üzere windows.  
  
> [!NOTE]
>  Varsa `POSITION` veya `SV_POSITION` köşe gölgelendiricisi çıkışı semantiği bulunmaz ve hiçbir şey görüntülenen **köşe gölgelendiricisi** aşaması.  
  
 **Kabuk gölgelendirici** (Direct3D 11 ve Direct3D 12 yalnızca)  
 Kabuk gölgelendirici aşamalı süreçleri tanımlayan bir satır, üçgen veya dört gibi düşük düzey yüzey noktalarını denetler. Çıktı olarak daha yüksek sıralı geometri düzeltme eki ve düzeltme eki sabitleri, sabit işlevi Mozaik döşeme aşaması için geçirilen oluşturur.  
  
 Kabuk gölgelendirici aşaması ardışık düzen Aşamaları penceresinde görünür değil.  
  
 **Tessellator aşama** (Direct3D 11 ve Direct3D 12 yalnızca)  
 Kabuk gölgelendiricisi çıkışı tarafından temsil edilen etki alanı önceden işler sabit işlev (programlanabilir olmayan) bir donanım birim tessellator aşamadır. Çıktı olarak bir etki alanının örnekleme desen ve daha küçük ilkel bir dizi oluşturur — noktaları, satırlar, üçgen — bu örnekleri bağlanın.  
  
 Tessellator aşaması ardışık düzen Aşamaları penceresinde görünür değil.  
  
 **Etki alanı gölgelendiricisi** (Direct3D 11 ve Direct3D 12 yalnızca)  
 Etki alanı gölgelendirici aşaması birlikte Mozaik faktörler hesaplanabilir Mozaik döşeme aşaması'dan daha yüksek sıralı geometri düzeltme ekleri Hull gölgelendiricisi, gelen işler. Mozaik faktörler olabilir tessellator giriş faktörü dahil yanı sıra Etkenler çıktı. Çıktı olarak bir noktadaki tessellator faktörlere göre çıkış düzeltme eki köşe konumunu hesaplar.  
  
 Etki alanı gölgelendirici aşaması ardışık düzen Aşamaları penceresinde görünür değil.  
  
 **Geometri gölgelendiricisi**  
 Geometri gölgelendirici aşaması tüm temelleri işler — noktaları, çizgiler veya üçgenler — edge bitişik temelleri için isteğe bağlı köşe verileriyle birlikte. Köşe gölgelendiricileri aksine geometri gölgelendirici daha oluşturabilir veya olarak aldıkları daha az temelleri giriş.  
  
 Ardışık Düzen Aşamaları penceresinde geometri gölgelendiricisi çıkışı bir Tel Çerçeve ızgara görüntüsü olarak görselleştirilir. Sonuç birine daha yakından bakalım için seçin **geometri gölgelendiricisi** içinde **grafik ardışık düzen aşamaları** işlenen temelleri Resim Düzenleyicisi'nde görüntülemek için pencere.  
  
 **Stream çıkış aşaması**  
 Akış çıkış aşama, dönüştürülen temelleri tarama önce ıntercept ve bellek yazmak; buradan veri önceki grafik ardışık düzen aşamaları giriş olarak recirculated veya CPU tarafından okunur.  
  
 Akış çıkış aşaması ardışık düzen Aşamaları penceresinde görselleştirilir değil.  
  
 **Tarayıcısını aşaması**  
 Vektör temelleri dönüştürür bir sabit işlev (programlanabilir olmayan) bir donanım birim tarayıcısını aşamadır — noktaları, satırlar, üçgen — satır içi tarama dönüştürme gerçekleştirerek bir ızgara görüntüsü. Tarama sırasında köşeler homojen küçük-alanı dönüştürülür ve kırpılır. Çıktı olarak piksel gölgelendiricileri eşlenir ve her köşe öznitelikleri arasında temel ilişkilendirilmiş ve piksel gölgelendiricisi için hazır hale getirdik.  
  
 Tarayıcısını aşaması ardışık düzen Aşamaları penceresinde görselleştirilir değil.  
  
 **Piksel gölgelendirici**  
 Piksel başına oluşturulacak piksel gölgelendirici aşaması işlemleri taranmış temelleri birlikte ilişkilendirilmiş köşe verileri, renk ve derinlik gibi değerler.  
  
 Ardışık Düzen Aşamaları penceresinde piksel gölgelendirici çıkış rengi tam tarama görüntü olarak görselleştirilir. Sonuç birine daha yakından bakalım için seçin **piksel gölgelendiricisi** içinde **grafik ardışık düzen aşamaları** işlenen temelleri Resim Düzenleyicisi'nde görüntülemek için pencere.  
  
 **Çıkış Birleştiricisi**  
 Yeni oluşturulan piksel karşılık gelen arabelleklerini mevcut içeriğini birlikte etkisini çıkış birleşme aşama birleştirir; renk ve derinlik kalıbı — bu arabellekleri yeni değerler oluşturmak için.  
  
 Ardışık Düzen Aşamaları penceresinde çıkış birleşme çıkış rengi tam tarama görüntü olarak görselleştirilir. Sonuçları birine daha yakından bakalım için seçin **çıkış Birleştiricisi** içinde **grafik ardışık düzen aşamaları** birleştirilmiş framebuffer görüntülemek için pencere.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Köşe ve geometri gölgelendiricisi Önizleme  
 Köşe veya geometri gölgelendiricisi aşamasında seçtiğinizde **ardışık düzen aşamaları** penceresinde görüntüleyebilirsiniz girişleri ve çıkışları gölgelendirici altındaki panel içinde.  Burada, bunlar tarafından giriş derleyici aşamasının birleştirilmiş sonra gölgelendiriciler için sağlanan köşe listesi hakkındaki ayrıntıları bulabilirsiniz.  

 ![Köşe gölgelendirici aşaması giriş arabelleği Görüntüleyicisi](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Köşe gölgelendirici aşamasının sonucu görüntülemek için Kafes sonra biri tam boyutlu, bir taranmış Tel Çerçeve görüntülemek için köşe gölgelendirici aşaması küçük resim seçin, edilmiş köşe gölgelendiricisi tarafından dönüştürülür.  
  
 ![Köşe gölgelendirici aşaması sonuç önizlemesi](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Köşe gölgeleme nedeniyle nesnelerin eksikliği](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)