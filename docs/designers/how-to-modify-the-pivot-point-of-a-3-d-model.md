---
title: 'Nasıl yapılır: 3B modelin Pivot noktasını değiştirme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 352685e6b31aa688ff51f9564f141fa800c348d8
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977825"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Nasıl yapılır: 3B modelin pivot noktasını değiştirme

Bu makalede değiştirmek için Model Düzenleyicisi'ni kullanmayı gösteren *pivot noktası* 3B modeli. Pivot noktası matematik nesnenin döndürme ve ölçeklendirme merkezini tanımlayan alanında noktasıdır.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>3B modelin pivot noktasını değiştirme

Kaynak 3B modelin pivot noktası değiştirerek tanımlayabilirsiniz.

Emin olun **özellikleri** penceresi ve **araç kutusu** görüntülenir.

1.  Başlangıç makalesinde bir gibi mevcut bir 3B model ile [nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md).

2.  Pivot modu girin. Üzerinde **Model Düzenleyicisi modu** araç seçin **Pivot modu** pivot modunu etkinleştirmek için düğme. Bir kutu çevresinde görünen **Pivot modu** Model Düzenleyicisi artık pivot modunda olduğunu belirtmek için düğme. Pivot modu, dünya alanındaki nesne yapısını yerine nesnenin pivot noktası çeviri gibi işlemleri etkiler.

3.  Nesnenin pivot noktasını değiştirme. İçinde **seçin** modu, nesneyi seçin ve ardından **Model Görüntüleyici** araç seçin **çevir** aracı. Pivot noktasını temsil eden bir kutu tasarım yüzeyinde görünür. Nesnenin pivot noktasını değiştirme için kutusunu taşıyın.

     Kutunun taşıyarak, tüm üç farklı boyutta pivot noktasını taşıyabilirsiniz. Pivot noktası bir ekseni çevirmek için bu eksen için karşılık gelen oku taşıyın. Çeviri tarafından etkilenen eksen göstermek üzere bir sarı renk kutusu ve oklar değiştirin.

     Pivot noktası kullanarak da belirtebilirsiniz **Özet çeviri** özelliğinde **özellikleri** penceresi.

    > [!TIP]
    > Yeni pivot noktası etkisini nesnesi döndürerek görüntüleyebilirsiniz. Döndürmek için kullanın **Döndür** aracı veya değiştirme **döndürme** özelliği.

Değiştirilen pivot noktası olan bir model şu şekildedir:

![Değiştirilen pivot noktası olan bir ev modeli](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Model düzenleyicisi](../designers/model-editor.md)