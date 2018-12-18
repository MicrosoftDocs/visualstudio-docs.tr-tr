---
title: 'Nasıl yapılır: temel 3B Model oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83d4069135adf37156457321b8ce15a254c9c27b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825498"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Nasıl Yapılır: Temel 3B Model Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, temel 3B model oluşturmak için Model Düzenleyicisi nasıl yapılacağı açıklanır.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Nesneler bir Sahne ekleme  
  
-   Yüzleri ve kenar seçme  
  
-   Seçimleri çevirme  
  
-   Kullanarak **yüzü alt bölümlere ayırır** ve **yüzü kalıptan geçirir** araçları  
  
-   Kullanarak **üçgenlere** komutu  
  
## <a name="creating-a-basic-3-d-model"></a>Temel 3B model oluşturma  
 3B modeller ve oyunlarda veya uygulamalarda için sahneler oluşturmak ve değiştirmek için Model Düzenleyicisi'ni kullanabilirsiniz. Aşağıdaki adımlar, Model Düzenleyicisi evin basitleştirilmiş bir 3B model oluşturma için nasıl kullanılacağını gösterir. Basitleştirilmiş bir model bir stand-in yine de, çakışma algılaması için ağ veya temsil ettiği nesneyi daha ayrıntılı işleme yararlanmak için çok uzakta olduğunda kullanılacak düşük ayrıntı model olarak oluşturulmakta olan son resim varlıkları için kullanılabilir.  
  
 İşlemi tamamladığınızda, model şu şekilde görünmelidir:  
  
 ![Basitleştirilmiş evi tamamlanmış modelini](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Evin basitleştirilmiş bir 3B model oluşturma  
  
1. Çalışmak için bir 3B modeli oluşturun. Başlarken bölümünde projenize bir model ekleme hakkında daha fazla bilgi için bkz. [Model Düzenleyicisi](../designers/model-editor.md).  
  
2. Bir küp sahneye ekleyin. İçinde **araç kutusu** penceresinin altında **şekiller**seçin **küp** ve ardından tasarım yüzeyine taşıyın.  
  
3. Yüz seçimi geçin. Model Düzenleyicisi araç çubuğunda **seçin yüz**.  
  
4. Küp en alt bölümlere ayırır. Yüz seçimi modunda, küpün kez seçimi için etkinleştirmek için seçin ve en üst yüz seçmek için küp seçin. Model Düzenleyicisi araç çubuğunda **yüzü alt bölümlere ayırır**. Bu dört eşit boyutlu bölümlere bölme küp üstüne yeni köşeler ekler.  
  
    ![Küp en alt bölümlere](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5. Küp bitişik iki tarafının Yükselt — Örneğin, ön ve küp sağ tarafında. Yüz seçimi modunda, küp seçimi etkinleştirin ve sonra bir küp tarafı kez seçin. Tuşuna basın ve CTRL tuşunu basılı tutun, başka bir tarafında, seçtiğiniz ilk yan bitişik olan küp seçin ve ardından Model Düzenleyicisi araç çubuğunda **yüzü kalıptan geçirir**.  
  
    ![Küp tarafının yükseltilmiş](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6. Extrusions birini genişletin. Yeni yüzler birini yükseltilmiş seçin ve ardından, Model Düzenleyicisi araç çubuğunda **çevir** aracı ve kalıp ile aynı yönde çeviri işleyici taşıyın.  
  
    ![Bir küp tarafı daha fazla yükseltilmiş. ](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7. Model üçgenlere bölmek. Model Düzenleyicisi araç çubuğunda **Gelişmiş**, **Araçları**, **üçgenlere**.  
  
8. Evi çatıyı oluşturun. Kenar seçme moduna geçiş seçerek **seçin Edge** Model Düzenleyicisi araç çubuğunda etkinleştirmek için küp seçin. Tuşuna basın ve burada gösterilen kenarlar seçerken CTRL tuşunu basılı tutun:  
  
    ![Tavan değerinin en yüksek oluşturacak kenarları](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
    Kenarlar, Model Düzenleyicisi araç çubuğunda seçildiğinde seçin **çevir** aracı ve ardından yukarı evi çatıyı oluşturmak için çeviri işleyici taşıyın.  
  
   Basitleştirilmiş merkezi modeli tamamlanmıştır. İşte son modelin yeniden uygulanan düz gölgelendirme ile:  
  
   ![Basitleştirilmiş evi tamamlanmış modelini](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
   Sonraki adım olarak, bu 3B modele gölgelendirici uygulayabilirsiniz. Bilgi için [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: 3B Arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md)   
 [Model Düzenleyicisi](../designers/model-editor.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)



