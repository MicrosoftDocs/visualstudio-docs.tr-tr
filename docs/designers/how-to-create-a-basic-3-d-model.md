---
title: 'Nasıl yapılır: temel 3B Model oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6242b80c1dcefe0e1a3a35561337a75e6098d25d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913455"
---
# <a name="how-to-create-a-basic-3d-model"></a>Nasıl yapılır: temel 3B model oluşturma

Bu makalede, Model Düzenleyicisi temel 3B model oluşturma için nasıl kullanılacağını gösterir. Aşağıdaki eylemler ele alınmaktadır:

-   Nesneler bir Sahne ekleme

-   Yüzleri ve kenar seçme

-   Seçimleri çevirme

-   Kullanarak **yüzü alt bölümlere ayırır** ve **yüzü kalıptan geçirir** araçları

-   Kullanarak **üçgenlere** komutu

## <a name="create-a-basic-3d-model"></a>Temel 3B model oluşturma
 3B modeller ve oyunlarda veya uygulamalarda için sahneler oluşturmak ve değiştirmek için Model Düzenleyicisi'ni kullanabilirsiniz. Aşağıdaki adımlar, Model Düzenleyicisi evin basitleştirilmiş bir 3B model oluşturmak için nasıl kullanılacağını gösterir. Basitleştirilmiş bir model bir stand-in yine de, çakışma algılaması için ağ veya temsil ettiği nesneyi daha ayrıntılı işleme yararlanmak için çok uzakta olduğunda kullanılacak düşük ayrıntı model olarak oluşturulmakta olan son resim varlıkları için kullanılabilir.

 İşlemi tamamladığınızda, model şu şekilde görünmelidir:

 ![Basitleştirilmiş evi tamamlanmış modelini](../designers/media/gfx_model_demo_house_final.png)

 Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Evin basitleştirilmiş bir 3B model oluşturma

1. Bir 3B modeli ile çalışmak için oluşturun. Başlarken bölümünde projenize bir model ekleme hakkında daha fazla bilgi için bkz. [Model Düzenleyicisi](../designers/model-editor.md).

2. Bir küp sahneye ekleyin. İçinde **araç kutusu** penceresinin altında **şekiller**seçin **küp** ve ardından tasarım yüzeyine taşıyın.

3. Yüz seçimi geçin. Model Düzenleyicisi araç çubuğunda **seçin yüz**.

4. Küp en alt bölümlere ayırır. Yüz seçimi modunda, küpün kez seçimi için etkinleştirmek için seçin ve en üst yüz seçmek için küp seçin. Model Düzenleyicisi araç çubuğunda **yüzü alt bölümlere ayırır**. Bu dört eşit boyutlu bölümlere bölme küp üstüne yeni köşeler ekler.

    ![Küp en alt bölümlere](../designers/media/gfx_model_demo_house_subdiv.png)

5. Küp bitişik iki tarafının Yükselt — Örneğin, ön ve küp sağ tarafında. Yüz seçimi modunda, küp seçimi etkinleştirin ve sonra bir küp tarafı kez seçin. Basılı **Ctrl** anahtar, başka bir tarafında, seçtiğiniz ilk yan bitişik olan küp seçin ve ardından Model Düzenleyicisi araç çubuğunda **yüzü kalıptan geçirir**.

    ![Küp tarafının yükseltilmiş](../designers/media/gfx_model_demo_house_extrude.png)

6. Extrusions birini genişletin. Yeni yüzler birini yükseltilmiş seçin ve ardından, Model Düzenleyicisi araç çubuğunda **çevir** aracı ve kalıp ile aynı yönde çeviri işleyici taşıyın.

    ![Bir küp tarafı daha fazla yükseltilmiş.](../designers/media/gfx_model_demo_house_extend.png)

7. Model üçgenlere bölmek. Model Düzenleyicisi araç çubuğunda **Gelişmiş** > **Araçları** > **üçgenlere**.

8. Evi çatıyı oluşturun. Kenar seçme moduna geçiş seçerek **seçin Edge** Model Düzenleyicisi araç çubuğunda etkinleştirmek için küp seçin. Basılı **Ctrl** anahtar burada gösterilen kenarlar seçin:

    ![Tavan değerinin en yüksek oluşturacak kenarlar](../designers/media/gfx_model_demo_house_edges.png)

    Kenarlar, Model Düzenleyicisi araç çubuğunda seçildiğinde seçin **çevir** aracı ve ardından yukarı evi çatıyı oluşturmak için çeviri işleyici taşıyın.

   Basitleştirilmiş merkezi modeli tamamlanmıştır. İşte son modelin yeniden uygulanan düz gölgelendirme ile:

   ![Basitleştirilmiş evi tamamlanmış modelini](../designers/media/gfx_model_demo_house_final.png)

   Sonraki adım olarak, bu 3B modele gölgelendirici uygulayabilirsiniz. Bilgi için [nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: 3B arazi modeli oluşturma](../designers/how-to-model-3-d-terrain.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
