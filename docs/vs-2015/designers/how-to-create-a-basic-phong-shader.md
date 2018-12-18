---
title: 'Nasıl yapılır: temel Phong gölgelendiricisi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ddb8f32cbf23184da140c3426e88c1f622dea1b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832686"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili (DGSL) Klasik Phong aydınlatma modeli uygulayan aydınlatma gölgelendirici oluşturmak için nasıl kullanılacağını gösterir.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Düğüm için bir gölgelendirici grafiği ekleme  
  
-   Düğüm bağlantısı kesiliyor  
  
-   Düğümleri bağlanma  
  
## <a name="the-phong-lighting-model"></a>Phong aydınlatma modeli  
 Phong aydınlatma modeli, yansıtıcı bir yüzeyi özellikleri benzetir Yansımalı vurgulama içerecek şekilde Lambert aydınlatma modeli genişletir. Lambert aydınlatma modeli kullandığınız aynı kaynaktan Yönlü ışık ek aydınlatma Yansımalı bileşen sağlar, ancak kendi son renk katkısı farklı şekilde işlenir. Yansımalı vurgulama her yüzeyi sahnedeki farklı görünüm yönünü, yönü ışık kaynağı yüzey yönü arasındaki ilişkiye bağlı etkiler. Yansımalı renk, yansımalı güç ve yönlendirmesini yüzeyi ve renk, şiddeti ve yönü ışık kaynaklarına bir üründür. Maksimum Yansımalı katkı Görüntüleyicisi, doğrudan ışık kaynağına yansıtacak yüzeylerini alır ve ışık kaynağına Sırtı Görüntüleyicisi yansıtacak yüzeylerini hiçbir katkı alırsınız. Phong aydınlatma modeli altında bir veya daha fazla Yansımalı bileşenleri her noktasında bir nesne için yansımalı vurgulamanın yoğunluğu ve renk belirlemek için birleştirilir ve ardından pikselin son rengini üretmek için Lambert aydınlatma modeli sonucuna eklenir .  
  
 Lambert aydınlatma modeli hakkında daha fazla bilgi için bkz: [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-phong-shader"></a>Phong gölgelendiricisi oluşturma  
  
1. Bölümünde anlatıldığı gibi bir Lambert gölgelendiricisi oluşturma [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).  
  
2. Bağlantı kesme **Lambert** düğümünden **son rengini** düğümü. Seçin **RGB** , terminal **Lambert** düğümünü seçip **Bağlantıları Kes**. Bu, sonraki adımda eklenen düğümü için yer sağlar.  
  
3. Ekle bir **Ekle** grafiğe düğüm. İçinde **araç kutusu**altında **matematik**seçin **Ekle** ve tasarım yüzeyine taşıyın.  
  
4. Ekleme bir **Specular** grafiğe düğüm. İçinde **araç kutusu**altında **yardımcı programı**seçin **Specular** ve tasarım yüzeyine taşıyın.  
  
5. Yansımalı katkı ekleyin. Taşıma **çıkış** , terminal **Specular** düğüme **X** , terminal **Ekle** düğümünü ve ardından taşıyın **çıkış**  , terminal **Lambert** düğüme **Y** , terminal **Ekle** düğümü. Bu bağlantılar piksel toplam dağıtma ve Yansımalı renk katkısını birleştirin.  
  
6. Hesaplanan renk değeri son rengi bağlanın. Taşıma **çıkış** , terminal **Ekle** düğüme **RGB** , terminal **son rengini** düğümü.  
  
   Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve çaydanlık modeline uygulanan gölgelendiricinin önizlemesini gösterir.  
  
> [!NOTE]
>  Bu çizimde gösterilen gölgelendirici etkisini daha iyi göstermek için turuncu renk kullanarak belirtilmiş **MaterialDiffuse** kullanarakgölgelendiricivemetalikgörünümlübirsonparametresibelirtilmedi**MaterialSpecular** ve **MaterialSpecularPower** parametreleri. Gölgelendiricileri Önizleme bölümünde malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
 ![Gölgelendirici grafiği ve etkisini önizlemesini](../designers/media/digit-lighting-graph.png "basamak aydınlatma grafiği")  
  
 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendiricileri Önizleme bölümünde gölgelendiricileri gölgelendirici Tasarımcısı'nda önizleme hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md)  
  
 Aşağıdaki çizim, 3B modeline uygulanan bu belgede açıklanan gölgelendirici gösterir. **MaterialSpecular** özelliği ayarlanmış (1.00, 0,50, 0,20, 0,00 için) ve onun **MaterialSpecularPower** 16'özelliği ayarlanmış.  
  
> [!NOTE]
>  **MaterialSpecular** özelliği yüzey malzeme görünen bitişi belirler. Cam veya plastik gibi bir parlak yüzeyinin beyaz parlak gölgeye olan Yansımalı renk sahip eğilimindedir. Metalik surface, yayınık renk yakın bir yansımalı renk sahip eğilimindedir. Saten bitiş surface, gri koyu bir gölge Yansımalı renk sahip eğilimindedir.  
>   
>  **MaterialSpecularPower** özelliği belirler nasıl yoğun olan Yansımalı vurgular. Yüksek Yansımalı powers düzeyi benzetimini yapmak, daha fazla yerelleştirilmiş vurgular. Çok düşük Yansımalı powers oversaturate ve tüm surface rengini gizlediklerinden güçlü, davrandığınızdan vurgular benzetimini yapar.  
  
 ![Bir modele uygulandı Phong aydınlatma](../designers/media/digit-lighting-model.png "basamak aydınlatma modeli")  
  
 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)   
 [Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)   
 [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)



