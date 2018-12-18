---
title: 'Nasıl Yapılır: Temel Doku Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 211da971bc7e4e275ef43b88531fe46a7fc0b4eb
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924072"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Nasıl yapılır: temel doku gölgelendiricisi oluşturma

Bu makalede, gölgelendirici Tasarımcısı ve yönlendirilmiş grafik gölgelendirici dili (DGSL) bir tek doku gölgelendiricisi oluşturmak için nasıl kullanılacağını gösterir. Bu gölgelendiriciyi RGB ve dokudan örneklenen alfa değerleri için doğrudan son rengini ayarlar.

## <a name="create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma

Temel, tek bir doku gölgelendirici doğrudan son çıkış rengi renk ve alfa değerleri bir doku örneğinin yazarak uygulayabilirsiniz.

Başlamadan önce emin **özellikleri** penceresi ve **araç kutusu** görüntülenir.

1.  Çalışmak için bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).

2.  Silme **nokta rengi** düğümü. İçinde **seçin** modunu Seç **nokta rengi** düğümünü ve ardından menü çubuğunda, **Düzenle** > **Sil**. Bu, sonraki adımda eklenen düğümü için yer sağlar.

3.  Ekleme bir **doku örneğinin** grafiğe düğüm. İçinde **araç kutusu**altında **doku**seçin **doku örneğinin** ve tasarım yüzeyine taşıyın.

4.  Ekleme bir **doku koordinatı** grafiğe düğüm. İçinde **araç kutusu**altında **doku**seçin **doku koordinatı** ve tasarım yüzeyine taşıyın.

5.  Bir doku uygulamak için seçin. İçinde **seçin** modunu seçin **doku örneğinin** düğümünü ve ardından **özellikleri** penceresinde kullanarak kullanmak istediğiniz dokuyu belirtin **dosya adı**  özelliği.

6.  Doku genel olarak erişilebilir hale getirir. Seçin **doku örneğinin** düğümünü ve ardından **özellikleri** penceresinde **erişim** özelliğini **genel**. Gibi başka bir aracı, doku ayarlayabilirsiniz artık **Model Düzenleyicisi**.

7.  Doku koordinatlarını doku örneğine bağlanın. İçinde **seçin** modu, taşıma **çıkış** , terminal **doku koordinatı** düğüme **UV** , terminal **doku Örnek** düğümü. Bu bağlantıyı belirtilen koordinatlarda dokuyu örnekler.

8.  Doku örneğinin son rengi bağlanın. Taşıma **RGB** , terminal **doku örneğinin** düğüme **RGB** , terminal **son rengini** düğümünü ve ardından taşıyın **Alfa** , terminal **doku örneğinin** düğüme **alfa** , terminal **son rengini** düğümü.

Aşağıdaki resimde tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendiricinin önizlemesini gösterir.

> [!NOTE]
> Bu çizimde, bir önizleme şeklinde kullanılır ve bir doku gölgelendirici etkisini daha iyi göstermek için belirtilen.

![Gölgelendirici grafiği ve etkisini önizlemesi](../designers/media/digit-texture-effect.png)

Belirli şekiller daha iyi önizlemeleri için bazı gölgelendiricileri sağlayabilir. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz. [gölgelendirici Tasarımcısı](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)