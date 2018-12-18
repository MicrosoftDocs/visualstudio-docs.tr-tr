---
title: 'Nasıl yapılır: geometri tabanlı gradyan gölgelendirici oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61dd80bb8d8ba4c272beff018d3ab65ffce41dc6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911882"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili geometri tabanlı gradyan gölgelendirici oluşturma için nasıl kullanılacağını gösterir. Her nokta, dünya alanındaki bir nesnenin yüksekliğini tarafından sabit bir RGB renk değeri bu gölgelendiriciyi olacak şekilde ölçeklendirir.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Düğüm için bir gölgelendirici grafiği ekleme  
  
-   Düğüm özelliklerini ayarlama  
  
-   Düğüm bağlantısı kesiliyor  
  
-   Düğümleri bağlanma  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma  
 Geometri tabanlı bir gölgelendirici pikselin konumu gölgelendiricinize ekleyerek uygulayabilirsiniz. Gölgelendirme dillerde bir piksel 2B ekranda yalnızca, rengini ve konumunu daha fazla bilgi içerir. Bir pikselin — olarak bilinen bir *parça* bazı sistemlerde — karşılık gelen bir piksel yüzeyine açıklayan değerleri oluşan bir koleksiyondur. Bu belgede açıklanan gölgelendirici, dünya alanındaki parça son çıktı rengini etkileyen bir 3B nesnenin her piksel yüksekliği kullanır.  
  
 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma  
  
1. Çalışmak için bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
2. Bağlantı kesme **nokta rengi** düğümünden **son rengini** düğümü. Seçin **RGB** , terminal **nokta rengi** düğümünü seçip **Bağlantıları Kes**. Bu, sonraki adımda eklenen düğümü için yer sağlar.  
  
3. Ekleme bir **Çarp** grafiğe düğüm. İçinde **araç kutusu**altında **matematik**seçin **Çarp** ve tasarım yüzeyine taşıyın.  
  
4. Ekleme bir **vektörü** grafiğe düğüm. İçinde **araç kutusu**altında **yardımcı programı**seçin **vektörü** ve tasarım yüzeyine taşıyın.  
  
5. Maskesi değerlerini belirtin **vektörü** düğümü. İçinde **seçin** modunu Seç **vektörü** düğümünü ve ardından **özellikleri** penceresinde **yeşil / Y** özelliğini**True**ve ardından **kırmızı / X**, **mavi / Z** ve **alfa / W** özelliklerine **False**. Bu örnekte, **kırmızı / X**, **yeşil / Y**, ve **mavi / Z** özellikleri karşılık gelen x, y ve z bileşenlerinin **dünya konumu** düğüm, ve **alfa / W** kullanılmıyor. Çünkü yalnızca **yeşil / Y** ayarlanır **True**, yalnızca giriş vektör y bileşeni, maskelenmiş sonra kalır.  
  
6. Ekleme bir **dünya konumu** grafiğe düğüm. İçinde **araç kutusu**altında **sabitleri**seçin **dünya konumu** ve tasarım yüzeyine taşıyın.  
  
7. Dünya alanı konumu parçanın maskeleyebilir. İçinde **seçin** modu, taşıma **çıkış** , terminal **dünya konumu** düğüme **vektör** , terminal **maskesi Vektör** düğümü. Bu bağlantı x ve z yok saymak için parça konumunu maskeleri bileşenleri.  
  
8. RGB renk sabiti maskelenmiş dünya alanı konumu ile çarpın. Taşıma **RGB** , terminal **nokta rengi** düğüme **Y** , terminal **Çarp** düğümünü ve ardından taşıyın  **Çıkış** , terminal **vektörü** düğüme **X** , terminal **Çarp** düğümü. Bu bağlantı, dünya alanındaki piksel yüksekliği tarafından renk değeri olacak şekilde ölçeklendirir.  
  
9. Ölçeklendirilmiş renk değeri son rengi bağlanın. Taşıma **çıkış** , terminal **Çarp** düğüme **RGB** , terminal **son rengini** düğümü.  
  
   Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve bir küre için uygulanan gölgelendiricinin önizlemesini gösterir.  
  
> [!NOTE]
>  Bu çizimde, daha iyi gölgelendirici etkisini göstermek için turuncu renk belirtildi, ancak Önizleme şekli, dünya alanındaki herhangi bir konum olduğundan, gölgelendirici tam gölgelendirici Tasarımcısı'nda önizlenemiyor. Gölgelendirici efekti tamamen göstermek için gerçek sahnede önizlemesi gerekir.  
  
 ![Gölgelendirici grafiği ve etkisini önizlemesini](../designers/media/digit-gradient-effect-graph.png "gradyan efekt grafik basamak")  
  
 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz: **gölgelendiricileri Önizleme** içinde [gölgelendirici Tasarımcısı](../designers/shader-designer.md)  
  
 Aşağıda gösterilmiştir 3B Sahne uygulanan bu belgede açıklanan gölgelendirici gösterilmektedir [nasıl yapılır: 3B Arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md). Renk ile dünyadaki noktası yüksekliğini yoğunluğuyla.  
  
 ![3'e uygulanan gradyan efekti&#45;D Arazi modeli](../designers/media/digit-gradient-effect-result.png "gradyan etkisi sonuç basamak")  
  
 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)   
 [Nasıl yapılır: 3B Arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md)   
 [Nasıl yapılır: gri tonlamalı doku gölgelendiricisi oluşturma](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)   
 [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)



