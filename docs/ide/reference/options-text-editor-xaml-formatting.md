---
title: Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4686760625062fea7984cdc05386284f8f98c4ee
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388994"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme

Kullanım **biçimlendirme** öğeler ve öznitelikler XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için özellik sayfası. Açmak için **seçenekleri** iletişim kutusu, tıklayın **Araçları** menüsünü seçin ve ardından **seçenekleri**. Erişim için **biçimlendirme** özellik sayfasında **metin düzenleyici** > **XAML** > **biçimlendirme** düğüm.

## <a name="auto-formatting-events"></a>Otomatik biçimlendirme olayları

Biçimlendirme oluşabilir, aşağıdaki olaylardan herhangi biri algılandı.

-   Bir bitiş etiketi ya da basit etiket tamamlama.

-   Bir başlangıç etiketi tamamlandığında.

-   Panodan yapıştırarak.

-   Klavye komutlarını biçimlendirme.

Otomatik biçimlendirme olayları neden belirtebilirsiniz.

**Bitiş etiketi ya da basit etiket tamamlandığında**

Biçimlendirme bir bitiş etiketi ya da basit etiket yazmayı bitirdikten sonra gerçekleşir. Basit bir etiket öznitelikleri, örneğin yok `<Button />`.

**Başlangıç etiketi tamamlandığında**

Biçimlendirme bir başlangıç etiketi yazmayı bitirdikten sonra gerçekleşir.

**Pano'dan üzerinde Yapıştır**

XAML görünümü panodan XAML yapıştırın biçimlendirme gerçekleşir.

## <a name="quotation-mark-style"></a>Tırnak işareti stili

Bu ayar, öznitelik değerleri tek veya çift tırnak içine alınmış olup olmadığını gösterir. Otomatik biçimlendirici ve IntelliSense otomatik tamamlama, bu ayarı kullanın.

Bu seçeneği belirlediğinizde, yalnızca öznitelikler, daha sonra Tasarımcı kullanılarak eklenen veya el ile XAML görünümünde etkilenir.

**Çift tırnak (")**

Öznitelik değerleri çift tırnak işareti içine alınır.
`<Button Name="button1">Hello</Button>`

**Tek tırnak (')**

Öznitelik değerleri tek tırnak işaretleri içine alınır.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Etiket kaydırma

Etiket sarmalama için bir satır uzunluğu belirtebilirsiniz. Etiket kaydırma etkin olduğunda, tüm XAML Tasarımcısı'nı kullanarak daha sonradan eklenen uygun şekilde sarmalanır.

**Belirtilen uzunluğu geçen etiketleri Kaydır**

Tarafından belirtilen satır uzunluğu'konumundaki satırları sarmalanmış olup olmadığını belirtir **uzunluğu**.

**Uzunluğu**

Bir satırın karakter içerebilir. Gerekirse, bazı XAML satırları belirtilen satır uzunluğu aşabilir.

## <a name="attribute-spacing"></a>Öznitelik aralığı

XAML belgenizde öznitelikleri nasıl düzenlenir denetlemek için bu ayarı kullanın.

**Satır başı ve öznitelikleri arasındaki boşlukları koru**

Yeni satırları ve boşlukları öznitelikleri arasındaki biçimlendirme tarafından etkilenmez.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Öznitelikler arasına tek boşluk Ekle**

Öznitelikleri bir boşluk ile ayırarak bitişik öznitelikleri bir satır kaplayabilir. Etiket sarmalama ayarları uygulanır.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Her özniteliği ayrı bir satıra Yerleştir**

Her öznitelik fazla öznitelik mevcut olduğunda, kullanışlı olan kendi satırına kaplar.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Konum ilk özniteliği başlangıç etiketiyle aynı satıra**

Bu onay kutusu işaretlendiğinde, öğenin başlangıç etiketi ile aynı satırda ilk öznitelik görünür.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Öğe aralığı

XAML belgenizde öğeleri nasıl düzenlenir denetlemek için bu ayarı kullanın.

**İçeriği yeni satırları koru**

Öğe içeriği boş satırları kaldırılmaz.

```xml
<Grid>


<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikte birden çok boş satırlar için tek bir satırı Daralt**

Öğe içeriği boş satırları tek bir satıra daraltılır.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikteki boş satırları Kaldır**

Öğesi içerik tüm boş satırlar kaldırıldı.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)