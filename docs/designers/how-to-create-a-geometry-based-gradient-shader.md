---
title: 'Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfdf75c058d1786febda71b05d424b1032254754
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37923913"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl yapılır: geometri tabanlı gradyan gölgelendirici oluşturma

Bu makalede gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili geometri tabanlı gradyan gölgelendirici oluşturma için nasıl kullanılacağını gösterir. Her nokta, dünya alanındaki bir nesnenin yüksekliğini tarafından sabit bir RGB renk değeri bu gölgelendiriciyi olacak şekilde ölçeklendirir.

## <a name="create-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma

Geometri tabanlı bir gölgelendirici pikselin konumu gölgelendiricinize ekleyerek uygulayabilirsiniz. Gölgelendirme dillerde bir piksel 2B bir ekranda yalnızca, rengini ve konumunu daha fazla bilgi içerir. Bir pikselin — olarak bilinen bir *parça* bazı sistemlerde — karşılık gelen bir piksel yüzeyine açıklayan değerleri oluşan bir koleksiyondur. Bu belgede açıklanan gölgelendirici, dünya alanındaki parça son çıktı rengini etkileyen bir 3B nesnenin her piksel yüksekliği kullanır.

Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.

1.  Birlikte çalışmak bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).

2.  Bağlantı kesme **nokta rengi** düğümünden **son rengini** düğümü. Seçin **RGB** , terminal **nokta rengi** düğümünü seçip **Bağlantıları Kes**. Bu, sonraki adımda eklenen düğümü için yer sağlar.

3.  Ekleme bir **Çarp** grafiğe düğüm. İçinde **araç kutusu**altında **matematik**seçin **Çarp** ve tasarım yüzeyine taşıyın.

4.  Ekleme bir **vektörü** grafiğe düğüm. İçinde **araç kutusu**altında **yardımcı programı**seçin **vektörü** ve tasarım yüzeyine taşıyın.

5.  Maskesi değerlerini belirtin **vektörü** düğümü. İçinde **seçin** modunu Seç **vektörü** düğümünü ve ardından **özellikleri** penceresinde **yeşil / Y** özelliğini**True**ve ardından **kırmızı / X**, **mavi / Z** ve **alfa / W** özelliklerine **False**. Bu örnekte, **kırmızı / X**, **yeşil / Y**, ve **mavi / Z** özellikleri karşılık gelen x, y ve z bileşenlerinin **dünya konumu** düğüm, ve **alfa / W** kullanılmıyor. Çünkü yalnızca **yeşil / Y** ayarlanır **True**, yalnızca giriş vektör y bileşeni, maskelenmiş sonra kalır.

6.  Ekleme bir **dünya konumu** grafiğe düğüm. İçinde **araç kutusu**altında **sabitleri**seçin **dünya konumu** ve tasarım yüzeyine taşıyın.

7.  Dünya alanı konumu parçanın maskeleyebilir. İçinde **seçin** modu, taşıma **çıkış** , terminal **dünya konumu** düğüme **vektör** , terminal **maskesi Vektör** düğümü. Bu bağlantı x ve z yok saymak için parça konumunu maskeleri bileşenleri.

8.  RGB renk sabiti maskelenmiş dünya alanı konumu ile çarpın. Taşıma **RGB** , terminal **nokta rengi** düğüme **Y** , terminal **Çarp** düğümünü ve ardından taşıyın  **Çıkış** , terminal **vektörü** düğüme **X** , terminal **Çarp** düğümü. Bu bağlantı, dünya alanındaki piksel yüksekliği tarafından renk değeri olacak şekilde ölçeklendirir.

9. Ölçeklendirilmiş renk değeri son rengi bağlanın. Taşıma **çıkış** , terminal **Çarp** düğüme **RGB** , terminal **son rengini** düğümü.

Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve bir küre için uygulanan gölgelendiricinin önizlemesini gösterir.

> [!NOTE]
> Bu çizimde, daha iyi gölgelendirici etkisini göstermek için turuncu renk belirtildi, ancak Önizleme şekli, dünya alanındaki herhangi bir konum olduğundan, gölgelendirici tam gölgelendirici Tasarımcısı'nda önizlenemiyor. Gölgelendirici efekti tamamen göstermek için gerçek sahnede önizlemesi gerekir.

 ![Gölgelendirici grafiği ve etkisini önizlemesi](../designers/media/digit-gradient-effect-graph.png)

 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz: **gölgelendiricileri Önizleme** içinde [gölgelendirici Tasarımcısı](../designers/shader-designer.md)

 Aşağıdaki çizim, bu belgedeki örneklerde gösterildiği 3B Sahne uygulanan açıklanan gölgelendirici gösterir. [nasıl yapılır: 3B Arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md). Renk ile dünyadaki noktası yüksekliğini yoğunluğuyla.

 ![3'e uygulanan gradyan efekti&#45;D Arazi modeli](../designers/media/digit-gradient-effect-result.png)

 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılır: 3B arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md)
- [Nasıl yapılır: Gri tonlamalı doku gölgelendiricisi oluşturma](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)