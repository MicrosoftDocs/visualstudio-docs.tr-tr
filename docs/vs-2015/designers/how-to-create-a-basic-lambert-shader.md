---
title: 'Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4fbf209e970367ded8e019087287d429bad8fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929731"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili (DGSL) Klasik Lambert aydınlatma modeli uygulayan aydınlatma gölgelendirici oluşturmak için nasıl kullanılacağını gösterir.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Düğüm için bir gölgelendirici grafiği ekleme  
  
-   Düğüm bağlantısı kesiliyor  
  
-   Düğümleri bağlanma  
  
## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli  
 Lambert aydınlatma modeli, çevresel ve tek yönlü ışık 3B görünümde gölge nesnelere içerir. Ortam bileşenleri ışıklar 3B Sahne olarak temel düzeyde sağlar. Yönlü ışık (uzaktaki) kaynaklardan ek aydınlatma yönlü bileşenleri sağlar. Ortam aydınlatma sahnedeki tüm yüzeyleri eşit, bağımsız olarak kendi yönlendirmesini etkiler. Belirli bir yüzeyi için çevresel renk yüzeyi ve renk ve ortam aydınlatması sahnedeki yoğunluğunu bir üründür. Tek yönlü ışık yönü ışık kaynağına göre yüzey yönü göre her yüzeyi sahnedeki farklı etkiler. Bu bir ürün yayınık renk ve surface ve rengini, şiddeti ve yönü ışık kaynaklarına yönünü olur. En büyük katkı doğrudan ışık kaynağına doğru yüzeyleri almak ve doğrudan yerine yüz tanıma yüzey hiçbir katkı alabilirsiniz. Lambert aydınlatma modeli altında nesne üzerinde her nokta için toplam yayınık renk katkısı belirlemek için çevresel bileşeni ve bir veya daha çok yönlü bileşenleri birleştirilir.  
  
 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-lambert-shader"></a>Lambert gölgelendiricisi oluşturma  
  
1. Çalışmak için bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
2. Bağlantı kesme **nokta rengi** düğümünden **son rengini** düğümü. Seçin **RGB** , terminal **nokta rengi** düğümünü seçip **Bağlantıları Kes**. Bırakın **alfa** terminal bağlı.  
  
3. Ekleme bir **Lambert** grafiğe düğüm. İçinde **araç kutusu**altında **yardımcı programı**seçin **Lambert** ve tasarım yüzeyine taşıyın. Lambert düğümü çevresel ve yayınık aydınlatma parametrelere bağlı olarak piksel toplam yayınık renk katkısını hesaplar.  
  
4. Connect **nokta rengi** düğüme **Lambert** düğümü. İçinde **seçin** modu, taşıma **RGB** , terminal **nokta rengi** düğüme **Yayınık renk** , terminal **Lambert**  düğümü. Bu bağlantı lambert düğümle ilişkilendirilmiş pikselin yayınık rengine sağlar.  
  
5. Hesaplanan renk değeri son rengi bağlanın. Taşıma **çıkış** , terminal **Lambert** düğüme **RGB** , terminal **son rengini** düğümü.  
  
   Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve çaydanlık modeline uygulanan gölgelendiricinin önizlemesini gösterir.  
  
> [!NOTE]
>  Bu çizimde gösterilen gölgelendirici etkisini daha iyi göstermek için turuncu renk kullanarak belirtilmiş **MaterialDiffuse** Gölgelendirici parametresi. Oyunlarda veya uygulamalarda bu parametre, her nesne için bir benzersiz renk değeri sağlamak için kullanabilirsiniz. Gölgelendiricileri Önizleme bölümünde malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
 ![Gölgelendirici grafiğinin ve etkisini önizlemesidir. ](../designers/media/digit-lambert-effect-graph.png "Lambert efekt grafik basamak")  
  
 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendiricileri Önizleme bölümünde gölgelendiricileri gölgelendirici Tasarımcısı'nda önizleme hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
 Aşağıdaki çizim, 3B modeline uygulanan bu belgede açıklanan gölgelendirici gösterir.  
  
 ![Lambert aydınlatma bir modele uygulandı. ](../designers/media/digit-lambert-effect-result.png "Lambert etkisi sonuç basamak")  
  
 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)   
 [Nasıl yapılır: temel Phong gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-phong-shader.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)   
 [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)



