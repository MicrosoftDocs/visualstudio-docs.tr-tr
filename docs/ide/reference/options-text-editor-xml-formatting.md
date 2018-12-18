---
title: Biçimlendirme seçenekler, metin düzenleyici, XML,
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 652d9ff3b2178089b4ef35838a4181408aef7f09
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388305"
---
# <a name="options-text-editor-xml-formatting"></a>Biçimlendirme seçenekler, metin düzenleyici, XML,

Kullanım **biçimlendirme** öğeler ve öznitelikler XML belgelerinizde nasıl biçimlendirileceğini belirtmek için özellik sayfası. Açmak için **seçenekleri** iletişim kutusu, tıklayın **Araçları** menüsünü seçin ve ardından **seçenekleri**. Erişim için **biçimlendirme** özellik sayfasında **metin düzenleyici** > **XML** > **biçimlendirme** düğümü .

## <a name="attributes"></a>Öznitelikler

**El ile öznitelik biçimlendirmeyi koru**

Öznitelikleri biçimlendirmez. Bu varsayılan ayardır.

> [!NOTE]
> Öznitelikler üzerinde birden fazla satır varsa, düzenleyici üst öğenin girintisini eşleştirilecek özniteliklerin her satırı girintiler.

**Öznitelikleri her ayrı satıra Hizala**

Dikey olarak ilk öznitelik girintisini eşleştirmek için ikinci ve sonraki öznitelikleri Hizala. Aşağıdaki XML nasıl öznitelikleri hizalanmış bir örnek metindir.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Otomatik yeniden Biçimlendir

**Pano'dan üzerinde Yapıştır**

Panodan yapıştırılan XML metin biçimlendirmesi.

**Bitiş etiketi tamamlandığında**

Öğe bitiş etiketi tamamlandığında yeniden biçimlendirin.

## <a name="mixed-content"></a>Karışık içerik

**Varsayılan olarak karışık içeriği biçimlendirin.**

Zaman içinde içerik bulunana dışında karışık içerik, yeniden biçimlendirme girişiminde bir `xml:space="preserve"` kapsam. Bu varsayılan ayardır.

Bir öğe metni ve biçimlendirmeyi bir karışımını içeriyorsa, içeriği içerik karışık kabul edilir. Karışık içerikli bir öğenin bir örneği verilmiştir.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML belgeleri (Visual Basic) oluşturma](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Kod oluşturma](../code-generation-in-visual-studio.md)