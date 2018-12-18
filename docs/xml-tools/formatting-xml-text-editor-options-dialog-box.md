---
title: Biçimlendirme, XML, metin düzenleyici, Seçenekler iletişim kutusu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f92ced5ca5ac007969a06cec7f253617ee293e3
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548797"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Biçimlendirme, XML, metin düzenleyici, Seçenekler iletişim kutusu

Bu iletişim kutusu için XML Düzenleyicisi biçimlendirme ayarları belirtmenize olanak sağlar. Erişebileceğiniz **seçenekleri** iletişim kutusundan **Araçları** menüsü.

> [!NOTE]
> Öğesini seçtiğinizde bu ayarlar kullanılabilir **metin düzenleyici** klasörü, **XML** klasörünü ve ardından **biçimlendirme** gelen seçeneği **seçenekleri** iletişim kutusu.

## <a name="attributes"></a>Öznitelikler
 **El ile öznitelik biçimlendirmeyi koru**

 Öznitelikleri yeniden biçimlendirilen değil. Bu varsayılandır.

> [!NOTE]
> Öznitelikleri birden çok satırda varsa, her satırın üst öğenin girinti eşleştirilecek özniteliklerin Düzenleyicisi girintileri.

 **Öznitelikleri her kendi satırında hizalayın**

 Dikey olarak ilk öznitelik girinti eşleştirmek için ikinci ve sonraki öznitelikleri hizalar. Aşağıdaki XML metni nasıl öznitelikleri hizalı bir örnektir.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Otomatik yeniden biçimlendirme
 **Pano'dan üzerinde Yapıştır**

 Panodan yapıştırılan XML metni yeniden biçimlendirir.

 **Bitiş etiketi tamamlama hakkında**

 Bitiş etiketi tamamlandığında, öğeyi yeniden biçimlendirir.

## <a name="mixed-content"></a>Karışık içerik
 **Varsayılan olarak karışık içerik koruma**

 Düzenleyici karışık içerik yeniden biçimlendirir olup olmadığını belirler. Varsayılan olarak, içeriği ne zaman bulunur dışında karışık içerik yeniden biçimlendirmek Düzenleyicisi çalışır bir `xml:space="preserve"` kapsam.

 Bir öğenin metin ve biçimlendirme bir karışımını içeriyorsa, içeriği içerik karışık kabul edilir. Bir öğenin karışık içerikli bir örnek verilmiştir.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge özellikleri, özellik penceresi](../xml-tools/xml-document-properties-properties-window.md)
- [XML Düzenleyicisi bileşenleri](../xml-tools/xml-editor-components.md)