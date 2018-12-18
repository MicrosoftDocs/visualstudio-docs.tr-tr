---
title: Blend'de nesnlerin stilini değiştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ae494a82e92086cfa0e8e2a69b7f7eee022807a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917208"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Blend'de nesnlerin stilini değiştirme

Özelliklerini ayarlamak için bir nesne özelleştirmek için en kolay yolu olan **özellikleri** bölmesi.

Yeniden kullanma ayarları veya ayar gruplarını istiyorsanız, yeniden kullanılabilir bir kaynak oluşturun. Bunun bir *stili*, *şablonu*, ya da özel bir renk gibi basit bir şey. Bir denetim durumu üzerinde farklı bağlı olarak görüntülenirler de yapabilirsiniz. Örneğin, kullanıcı tıklattığında bir düğme yeşil etkinleştirir.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Fırçalar: bir nesne görünümünü değiştirme

Görünümünü değiştirmek istiyorsanız fırça nesneye uygulanır.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Yinelenen bir resim veya desen bir nesne üzerinde boyama

Yinelenen bir resim veya desen bir nesne üzerinde kullanarak boyamak bir *döşeme fırça*.

Döşeme Fırça oluşturma için oluşturarak başlayın bir *görüntü fırça*, *fırça çizim*, veya *visual fırça* kaynak.

Resim fırçası görüntü kullanarak oluşturun. Aşağıdaki çizimler görüntü fırça, döşeli görüntü fırça ve çevrilmiş görüntü fırça gösterir.

![Görüntü fırça](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![döşenir mage fırça](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Çevrilmiş görüntü fırça](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Çizim Fırçası gibi bir yol veya şekil çizme vektör kullanarak oluşturun. Aşağıdaki çizimler çizim Fırçası, döşeli çizim Fırçası ve çevrilmiş çizim Fırçası gösterir.

![Çizim fırça](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Döşenir fırça çizme](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Fırça çizim çevrilmiş](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Denetimindeki bir düğme gibi visual Fırça oluşturma. Aşağıdaki çizimler visual fırça ve döşenir visual fırça göstermektedir.

![Görsel fırça](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Döşenir visual fırça](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Stilleri ve şablonları: denetimleri arasında tutarlı bir görünüm oluşturma

Bir kez Tasarım görünümünü ve davranışını ve böylece tek tek korumak yok Bu tasarımı diğer denetimleri uygulayın.

**Stil kullanmalısınız?** : Varsayılan özelliklerini (örneğin, bir düğme rengi) ayarlamak istiyorsanız kullanın bir *stili*. Hatta, stil için uyguladığınız sonra bir denetim değiştirebilirsiniz.

**Bir şablon kullanmalısınız?** : Bir denetim yapısını değiştirmek istiyorsanız, kullanmak bir *şablon*. Grafik veya logo bir düğmeye dönüştürme düşünün. Bir şablon uyguladığınız sonra bir denetim değiştiremezsiniz.

### <a name="create-a-template-or-style"></a>Bir şablonu veya stil oluşturma

Bir şablon oluşturmak için iki yol demektir. Bir denetime, yüzeyinde herhangi bir nesne dönüştürebilir veya varolan bir denetimi şablonunuzu temel alabilir.

Herhangi bir nesne için bir denetim şablonu dönüştürmek için nesneyi seçin ve ardından **Araçları** menüsünde seçin **olun içine denetim**.

Şablonunuzu var olan bir denetim temel almasını istiyorsanız, bir nesne seçin. Ardından, çalışma yüzeyi üst kısmında, içerik haritası düğmesini seçin, seçin **Şablonu Düzenle**ve ardından **bir kopyasını düzenlemek** veya **oluşturma boş**.

![Düzen şablonu menüsü](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Bir stil oluşturmak için nesneyi seçin ve ardından **nesne** menüsünde seçin **stili Düzenle**ve ardından **bir kopyasını düzenlemek** veya **boş oluştur**.

- Seçin **bir kopyasını düzenlemek** varsayılan stil veya şablon denetimi ile başlatmak için.

- Seçin **boş oluştur** baştan başlamak için.

**Düzenle geçerli** seçeneği, yalnızca bir stil veya önceden oluşturduğunuz şablonu düzenlerseniz görünür. Bir denetim için varsayılan Sistem şablonu kullanmaya devam görünmeyecektir.

İçinde **stil kaynağı oluştur** iletişim kutusu, ya da adını stil veya şablon daha sonra kullanmak ya da bu türdeki tüm denetimler için stil veya şablon uygulayabilirsiniz.

![Stil kaynak Oluştur iletişim kutusu](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Stilleri veya her tür denetimi için şablonlar oluşturulamıyor. Bir denetim bunları desteklemiyorsa, içerik haritası düğmesi çalışma yüzeyi gösterilmez.
> Ana belgenizi düzenleme kapsamına dönmek için tıklatın **dönmek için kapsam** ![kapsam simge durumuna döndürmek](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Stil veya şablon için bir denetim Uygula

Bir nesneye sağ [nesneleri ve zaman çizelgesi](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel) paneli, seçin **Şablonu Düzenle**ve ardından **geçerli kaynak**.

![Uygula kaynak menüsü](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Varsayılan stil veya şablon bir denetimin geri yükleme

Denetimi seçin ve [özellikleri](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel) paneli, bulun **stili** veya **şablonu** özelliği. Seçin **Gelişmiş Seçenekler**ve ardından **sıfırlama** kısayol menüsünde.

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>Görsel durumlar: kendi durumuna bağlı denetiminin görünümünü değiştirme

Denetimlerin Kullanıcı etkileşimlerine dayalı farklı görsel görünümler olabilir. Örneğin, bir kullanıcı bağlantıya tıkladığında veya animasyonun çalıştırabilirsiniz yeşile bir düğme yapabilirsiniz. Kısaltın veya geçişleri kullanarak görsel durumlarını arasındaki süreyi uzatın.

![Durum fare](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Kısa bir video izlemek:** ![Oynat düğmesini](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF denetimleri durumunu yöneten](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Kaynaklar: renk, stil ve şablonları oluşturmak ve bunları daha sonra yeniden

Bir kaynağa projenizdeki herhangi bir şeyi dönüştürebilirsiniz. Farklı yerlerde uygulamanızda yeniden bir nesne bir kaynaktır. Örneğin, bir kez bir renk oluşturmak, bir kaynak olun ve sonra o renk birkaç nesneler üzerinde kullanın. Tüm bu nesneleri rengini değiştirmek için yalnızca renk kaynağı değiştirin.

![Renk kaynak düğmeye Dönüştür](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Renk kaynak Oluştur iletişim kutusu](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)