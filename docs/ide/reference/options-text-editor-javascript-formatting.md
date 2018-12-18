---
title: Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa846a25e1383c0c164dfb4747899f5e86237d32
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671059"
---
# <a name="options-text-editor-javascript-formatting"></a>Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme
Kullanım **biçimlendirme** sayfasının **seçenekleri** Kod Düzenleyicisi'nde kod biçimlendirme seçeneklerini ayarlamak için iletişim kutusu. Menü çubuğunda, bu sayfaya erişmek için seçin **Araçları**, **seçenekleri**ve ardından **metin düzenleyici**, **JavaScript**ve **Biçimlendirme**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Otomatik Biçimlendirme
 Bu seçenekler biçimlendirme içinde oluştuğunda belirlemek **kaynak** görünümü.

### <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Enter üzerinde biçimlendirme tamamlandı satırı**|Bu seçenek belirlendiğinde, Enter tuşuna basın, Kod Düzenleyicisi'ni otomatik olarak bulunduğu satırı biçimlendirir.|
|**Üzerinde biçimlendirme tamamlandı deyimi;**|Bu seçenek belirlendiğinde, noktalı virgül anahtar seçtiğinizde, Kod Düzenleyicisi'ni otomatik olarak bulunduğu satırı biçimlendirir.|
|**{Blok açılan biçimi**|Bu seçenek belirlendiğinde, açılış seçtiğinizde Kod düzenleyicisinde otomatik olarak bulunduğu satırı biçimlendirir küme ayracı anahtarı.|
|**Tamamlanan bloğu Biçimlendir}**|Bu seçenek belirlendiğinde, kapatma seçeneğini belirlediğinizde Kod düzenleyicisinde otomatik olarak bulunduğu satırı biçimlendirir küme ayracı anahtarı.|
|**Yapıştırma sırasında Biçimlendir**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi kod düzenleyicisine yapıştırın, yeniden biçimlendirir. Düzenleyici, şu anda tanımlı biçimlendirme kurallarını kullanır. Bu seçenek seçilmezse Düzenleyicisi özgün yapıştırılan içinde kodun biçimi kullanır.|

## <a name="new-lines"></a>Yeni satırlar
 Bu seçenekler, Kod Düzenleyicisi, yeni bir satıra işlevleri ve denetim blokları için açık bir ayraç koyar olup olmadığını belirler.

### <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**İşlevler için yeni satıra açık ayraç yerleştirin**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi'ni yeni bir satır için bir işlev ile ilişkili açık ayraç taşır.|
|**Denetim blokları için yeni satıra açık ayraç yerleştirin**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi'ni bir denetim bloğu ile ilişkili açık ayraç taşır (örneğin, `if` ve `while` denetim blokları) için yeni bir satır.|

## <a name="spacing"></a>Aralığı
 Bu seçenekler alanları nasıl eklenir belirlemek **kaynak** görünümü.

### <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Virgül olan sınırlayıcıyı sonra boşluk Ekle**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi virgüller sonra bir boşluk ekler.|
|**'For' deyimleri noktalı virgülden sonra boşluk Ekle**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi olan ilk satırını her noktalı virgülden sonra bir boşluk ekler bir `for` döngü.|
|**İkili işleçlerden önce ve sonra boşluk Ekle**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi'ni bir alan ikili işleçlerden önce ve sonra ekler (örneğin, +, -, & &, &#124; &#124;).|
|**Denetim akış bildirimlerinde anahtar özcüklerden sonra boşluk Ekle**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi denetim akış deyimlerindeki anahtar sözcükleri JavaScript sonra bir boşluk ekler.|
|**Anonim işlevler için function anahtar sözcüğünü sonra boşluk Ekle**|Bu seçenek belirlendiğinde, Kod Düzenleyicisi'ni, sonra bir boşluk ekler. `function` anonim işlevler için anahtar sözcüğü.|
|**Açtıktan sonra ve boş ayraç kapatmadan önce boşluk Ekle**|Bu seçenek belirlendiğinde, parantez boş olmayan karakterler varsa Kod düzenleyicisinde bir boşluk açma parantezinden sonra ve kapatma parantezinden önce ekler.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)