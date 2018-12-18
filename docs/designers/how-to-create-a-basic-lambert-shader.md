---
title: 'Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d71a59e0173be60779675f838fad20943eabc85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913260"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma

Bu makalede, gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili (DGSL) Klasik Lambert aydınlatma modeli uygulayan aydınlatma gölgelendirici oluşturmak için nasıl kullanılacağını gösterir.

## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli

Lambert aydınlatma modeli, çevresel ve tek yönlü ışık 3B görünümde gölge nesnelere içerir. Ortam bileşenleri ışıklar 3B Sahne olarak temel düzeyde sağlar. Yönlü ışık (uzaktaki) kaynaklardan ek aydınlatma yönlü bileşenleri sağlar. Ortam aydınlatma sahnedeki tüm yüzeyleri eşit, bağımsız olarak kendi yönlendirmesini etkiler. Belirli bir yüzeyi için çevresel renk yüzeyi ve renk ve ortam aydınlatması sahnedeki yoğunluğunu bir üründür. Tek yönlü ışık yönü ışık kaynağına göre yüzey yönü göre her yüzeyi sahnedeki farklı etkiler. Bu bir ürün yayınık renk ve surface ve rengini, şiddeti ve yönü ışık kaynaklarına yönünü olur. En büyük katkı doğrudan ışık kaynağına doğru yüzeyleri almak ve doğrudan yerine yüz tanıma yüzey hiçbir katkı alabilirsiniz. Lambert aydınlatma modeli altında nesne üzerinde her nokta için toplam yayınık renk katkısı belirlemek için çevresel bileşeni ve bir veya daha çok yönlü bileşenleri birleştirilir.

Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.

1. Birlikte çalışmak bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).

2. Bağlantı kesme **nokta rengi** düğümünden **son rengini** düğümü. Seçin **RGB** , terminal **nokta rengi** düğümünü seçip **Bağlantıları Kes**. Bırakın **alfa** terminal bağlı.

3. Ekleme bir **Lambert** grafiğe düğüm. İçinde **araç kutusu**altında **yardımcı programı**seçin **Lambert** ve tasarım yüzeyine taşıyın. Lambert düğümü çevresel ve yayınık aydınlatma parametrelere bağlı olarak piksel toplam yayınık renk katkısını hesaplar.

4. Connect **nokta rengi** düğüme **Lambert** düğümü. İçinde **seçin** modu, taşıma **RGB** , terminal **nokta rengi** düğüme **Yayınık renk** , terminal **Lambert**  düğümü. Bu bağlantı lambert düğümle ilişkilendirilmiş pikselin yayınık rengine sağlar.

5. Hesaplanan renk değeri son rengi bağlanın. Taşıma **çıkış** , terminal **Lambert** düğüme **RGB** , terminal **son rengini** düğümü.

   Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve çaydanlık modeline uygulanan gölgelendiricinin önizlemesini gösterir.

> [!NOTE]
> Bu çizimde gösterilen gölgelendirici etkisini daha iyi göstermek için turuncu renk kullanarak belirtilmiş **MaterialDiffuse** Gölgelendirici parametresi. Oyunlarda veya uygulamalarda bu parametre, her nesne için bir benzersiz renk değeri sağlamak için kullanabilirsiniz. Gölgelendiricileri Önizleme bölümünde malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md).

 ![Gölgelendirici grafiğinin ve etkisini önizlemesidir.](../designers/media/digit-lambert-effect-graph.png)

 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendiricileri Önizleme bölümünde gölgelendiricileri gölgelendirici Tasarımcısı'nda önizleme hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md).

 Aşağıdaki çizim, 3B modeline uygulanan bu belgede açıklanan gölgelendirici gösterir.

 ![Lambert aydınlatma bir modele uygulandı.](../designers/media/digit-lambert-effect-result.png)

 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma](../designers/how-to-create-a-basic-phong-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)