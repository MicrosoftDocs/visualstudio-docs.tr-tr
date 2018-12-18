---
title: Araç Kutusu, HTML Sekmesi
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90dfae7e891c805a785db8bba00d3c75d2a84bf3
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384168"
---
# <a name="toolbox-html-tab"></a>Araç kutusu, HTML sekmesi

**HTML** araç kutusu sekmesi web sayfalarını ve web forms yararlı olan bileşenleri sağlar. Bu sekme görüntülemek için ilk HTML Tasarımcısı'nda düzenlemek için bir belgeyi açın. Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**ve ardından **HTML** araç kutusu sekmesi.

 Bir aracı örneği oluşturmak için **HTML** sekmesinde ya da çift aracı belgenize geçerli ekleme noktasına ekleyin veya aracı seçin ve düzenleme yüzeyi üzerinde istenen konuma sürükleyin.

## <a name="ui-elements"></a>Kullanıcı Arabirimi öğeleri

Aşağıdaki araçlar, HTML sekmesi varsayılan olarak kullanılabilir.

**İşaretçi**

![ASP.NET Mobil Tasarımcısı HTMLpage işaretçi](../../ide/reference/media/vxpointer.gif)

Bu araç, herhangi bir araç kutusu sekmeyi açıldığında, varsayılan olarak seçilidir. Silinemiyor. İşaretçiyi, nesneler görünümü tasarım yüzeyine sürükleyin, yeniden boyutlandırabilir ve sayfa veya form üzerinde yeniden konumlandırmak sağlar. Daha fazla bilgi için [araç kutusu](../../ide/reference/toolbox.md).

**Giriş (düğme)**

![HTML web sayfası düğmesi](../../ide/reference/media/vxbutton.gif)

Ekler bir `input` öğesinin `type="button"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Button1"` ilk düğme için eklenen `id="Button2"` saniye vb. için.

Sürüklediğinizde **giriş (düğme)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Giriş (Sıfırla)**

![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif)

Ekler bir `input` öğesinin `type="reset"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Reset1"` Sıfırla düğmesi, ilk için eklenen `id="Reset2"` saniye vb. için.

Sürüklediğinizde **giriş (Sıfırla)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Giriş (Gönder)**

![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif)

Ekler bir `input` öğesinin `type="submit"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Submit1"` ilk Gönder düğmesini için eklenen `id="Submit2"` saniye vb. için.

Sürüklediğinizde **giriş (Gönder)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Girişi (metin)**

![HTMLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif)

Ekler bir `input` öğesinin `type="text"` belgenizdeki. Görüntülenen varsayılan metni değiştirmek için Düzenle `value` özniteliği. Varsayılan olarak, `id="Text1"` ilk metin alanı için eklenen `id="Text2"` saniye vb. için.

Sürüklediğinizde **girişi (metin)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [ASP.NET Web sayfaları (Razor) sitelerinde kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (dosya)**

![HTML sayfası dosya alanı](../../ide/reference/media/vxfilefield.gif)

Ekler bir `input` öğesinin `type="file"` belgenizdeki. Varsayılan olarak, `id="File1"` ilk dosya alanı için eklenen `id="File2"` saniye vb. için.

Sürüklediğinizde **giriş (dosya)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [ASP.NET Web sayfaları (Razor) sitelerinde kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (parola)**

![Visual Studio parola alanı](../../ide/reference/media/vxpassword.gif)

Ekler bir `input` öğesinin `type="password"`. Varsayılan olarak, `id="Password1"` ilk parola alanına eklenen `id="Password2"` saniye vb. için.

Sürüklediğinizde **giriş (parola)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Uygulamanızın kullanıcı adları ve parolalar gönderiyorsa, sitenizi iletim şifrelemek için Güvenli Yuva Katmanı (SSL) kullanmak için yapılandırmanız gerekir. Daha fazla bilgi için [bağlantıların güvenliğini sağlama](/previous-versions/tn-archive/bb418917(v=technet.10)). Ayrıca, tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [ASP.NET Web sayfaları (Razor) sitelerinde kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (onay kutusu)**

![HTML Web sayfası araç onay kutusu seçeneği](../../ide/reference/media/vxcheckbox.gif)

Ekler bir `input` öğesinin `type="checkbox"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Checkbox1"` ilk onay kutusunu, eklenen `id="Checkbox2"` saniye vb. için.

Sürüklediğinizde **giriş (onay kutusu)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Giriş (radyo)**

![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif)

Ekler bir `input` öğesinin `type="radio"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Radio1"` ilk radyo düğmesi için eklenen `id="Radio2"` saniye vb. için.

Sürüklediğinizde **giriş (radyo)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Giriş (gizli)**

![HTML sayfası gizli öğesi](../../ide/reference/media/vxhidden.gif)

Ekler bir `input` öğesinin `type="hidden"`. Varsayılan olarak, `id="Hidden1"` ilk gizli alan için eklenen `id="Hidden2"` saniye vb. için.

Sürüklediğinizde **giriş (gizli)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**TextArea**

![HTMLpage araç metin alanı](../../ide/reference/media/vxtextarea.gif)

Ekler bir `textarea` öğesi. Metin alanının yeniden boyutlandırmak veya kendi görüntüleme alanı genişletir metin görüntülemek için kaydırma çubuklarını kullanın. Görüntülenen varsayılan metni değiştirmek için Düzenle `value` özniteliği. Varsayılan olarak, `id="textarea1"` olan ilk metin alanında, eklenen `id=" textarea 2"` saniye vb. için.

Sürüklediğinizde **Textarea** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [ASP.NET Web sayfaları (Razor) sitelerinde kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tablo**

![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif)

Ekler bir `table` öğesi.

Sürüklediğinizde **tablo** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Görüntü**

![HTML sayfası görüntü öğesi](../../ide/reference/media/vximage.gif)

Ekler bir `img` öğesi. Belirtmek için bu öğeyi düzenleyin, `src` ve kendi `alt` metin.

Sürüklediğinizde **görüntü** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<img alt="" src="">
```

**Seçin**

![Araç kutusu açılır HTML sayfası](../../ide/reference/media/vxdropdown.gif)

Bir açılan ekler `select` öğesi (olmadan bir `size` özniteliği). Varsayılan olarak, `id="select1"` ilk liste kutusu için eklenen `id="select2"` saniye vb. için.

Sürüklediğinizde **seçin** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Çok satırlı oluşturabilirsiniz `select` boyut özelliğinin değerini artırarak öğesi.

**Yatay cetvel**

![Yatay cetvel öğesi HTML sayfası](../../ide/reference/media/vxhorizontal.gif)

Ekler bir `hr` öğesi. Çizgi kalınlığı artırmak için Düzenle `size` özniteliği.

Sürüklediğinizde **yatay cetvel** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<hr width="100%" size=1>
```

**div**

![HTML sayfası etiketi](../../ide/reference/media/vxlabel.gif)

Ekler bir `div` içeren öğesi bir `ms_positioning="FlowLayout"` özniteliği. Genişlik ve yükseklik dışında bu öğeyi bir akış düzeni paneline aynıdır. İçinde yer alan metni biçimlendirmek için `div` öğe, Ekle bir `class="stylename"` özniteliği için açılış etiketi.

Sürüklediğinizde **Div** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
