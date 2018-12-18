---
title: XAML Tasarımcısı'de denetimler ekleme ve bunların davranışlarını değiştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 739c43b0ed6665684f0a38b35dfd6eccdf8f5b2c
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977818"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>XAML Tasarımcısı'de denetimler ekleme ve bunların davranışlarını değiştirme

Denetimler, kullanıcıların uygulamanızla etkileşim kurmasına olanak sağlar. Bunları gerçekleştirmek için de bilgi toplamak için kullanabileceğiniz eylemler gibi bir nesneye animasyon ekleme veya bir veri kaynağı sorgu.

## <a name="add-controls-to-the-artboard"></a>Çalışma yüzeyine denetimler ekleme

Denetimlerden sürükleyebilirsiniz **varlıklar** üzerine panelinde **çalışma yüzeyine**ve bunları değiştirmek **özellikleri** penceresi.

![Blend varlıklar sekme denetimleri](../designers/media/blend_assetsflipview_xaml.png)

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Bir denetimi dışında bir resmi, şekli veya yol olun

Herhangi bir nesneyi bir denetime yapabilirsiniz.

![Blend denetim haline Dönüştür iletişim kutusu](../designers/media/blend_makeintocontrol_xaml.png)

Örneğin, bir sayfanın ortasında bir televizyon resmini düşünün. Denetimleri televizyon düğmeler gibi görünen küçük resimler yetersiz duruma gelir. Ardından, kullanıcıların kanalı değiştirmek için bu düğmeleri tıklayabilirsiniz.

Düğme denetimleri artık olduğundan, bu mümkündür. Denetimleri sayesinde, Kullanıcı etkileşimlerine karşılık vermelerini; Bu durumda kullanıcı bir düğmeyi tıkladığında.

Bir denetim yapmak için bir nesne seçin. Ardından **Araçları** menüsünde tıklatın **olun denetim**.

## <a name="make-controls-do-things"></a>Denetimleri şeyler yap

Kullanıcılar bunlarla etkileşim kurduğunuzda denetimleri eylemleri gerçekleştirebilirsiniz. Örneğin, bunlar bir animasyonu başlatmak, bir veri kaynağını güncelleştirebilir veya bir videoyu oynatın.

Kullanım *Tetikleyicileri*, *davranışları*, ve *olayları* şeyler denetimleri yapma.

### <a name="triggers"></a>Tetikleyiciler

A *tetikleyici* bir özelliğini değiştirir veya yanıt olarak bir olay ya da başka bir özellik değişikliği bir görevi gerçekleştirir. Örneğin, kullanıcılar üzerine geldiğinizde, bir düğme rengini değiştirebilirsiniz.

![Tetikleyiciler paneli](../designers/media/custom_button_blend_propertytriggerinfo.png)

### <a name="behaviors"></a>Davranışlar

A *davranışı* kod yeniden kullanılabilir bir pakettir. Bunu biraz yapmak birden fazla özelliklerini değiştirin. Bu sorgu veri hizmeti gibi eylemleri gerçekleştirebilirsiniz. Blend ile küçük bir koleksiyon davranışların birlikte sunulur, ancak daha ekleyebilirsiniz. Bir davranış herhangi bir nesne, çalışma yüzeyine sürükleyin ve sonra davranış özelliklerini ayarlayarak özelleştirin.

![Özellikler bölmesinde FluidMoveBehavior](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

**Bir video izleyin:** ![oynatma simgesine](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Blend ipuçları: 1. Bölüm davranışları kullanarak giriş](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Olaylar

Ultimate esneklik için tanıtıcı bir *olay*. Bazı kod yazmak zorunda kalırsınız.