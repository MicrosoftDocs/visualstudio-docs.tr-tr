---
title: 'Nasıl yapılır: temel renk gölgelendiricisi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bcbbb8ede9f30ed1c0340098ffb358cf5715487
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813225"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili (DGSL) bir düz renk gölgelendiricisi oluşturma için nasıl kullanılacağını gösterir. Bu gölgelendirici için sabit bir RGB renk değeri son rengini ayarlar.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Bir grafikten düğümleri kaldırma  
  
-   Grafiğe düğüm ekleme  
  
-   Düğüm özelliklerini ayarlama  
  
-   Düğümleri bağlanma  
  
## <a name="creating-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma  
 Son çıkış rengi bir RGB renk sabiti renk değerini yazarak düz renk gölgelendiricisi uygulayabilirsiniz.  
  
 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma  
  
1. Çalışmak için bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
2. Silme **nokta rengi** düğümü. Kullanım **seçin** seçme aracı **nokta rengi** düğümünü ve ardından menü çubuğunda, **Düzenle**, **Sil**.  
  
3. Ekleme bir **renk sabit** grafiğe düğüm. İçinde **araç kutusu**altında **sabitleri**seçin **renk sabit** ve tasarım yüzeyine taşıyın.  
  
4. Renk için bir değer belirtmeniz **renk sabit** düğümü. Kullanım **seçin** seçme aracı **Color sabit** düğümünü ve ardından **özellikleri** penceresi, **çıkış** özelliği belirtin bir renk değeri. Turuncu için (1.0, 0,5, 0.2, 1.0) değerini belirtin.  
  
5. Renk sabiti için son rengini bağlanın. Bağlantılar oluşturmak için taşıma **RGB** , terminal **renk sabit** düğüme **RGB** , terminal **son rengini** düğümünü ve ettirin **alfa** , terminal **renk sabit** düğüme **alfa** , terminal **son rengini** düğümü. Bu bağlantılar, önceki adımda tanımlanan renk sabiti için son rengini ayarlayın.  
  
   Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendiricinin önizlemesini gösterir.  
  
> [!NOTE]
>  Çizimde, daha iyi gölgelendirici etkisini göstermek için turuncu renk belirtildi.  
  
 ![Gölgelendirici grafiği ve sonucu 3&#45;D modeli](../designers/media/digit-flat-color-effect.png "basamak düz renk etkisi")  
  
 Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz: [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)   
 [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)



