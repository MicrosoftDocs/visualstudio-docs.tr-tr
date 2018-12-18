---
title: C# Düzenleyicisi biçimlendirme seçenekleri
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 542d14e5913b1537d5e5e6aabb7264cd15add793
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220527"
---
# <a name="options-text-editor-c-code-style-formatting"></a>Seçenekler, metin düzenleyici, C#, kod stili, biçimlendirme

Kullanım **biçimlendirme** seçenekler sayfası, Kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için. Bu seçenekler sayfası erişmek için kendi seçtikleri **Araçları** > **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **metin düzenleyici** > **C#** > **kod stili**  >  **Biçimlendirme**.

## <a name="general-page"></a>Genel sayfası

### <a name="general-settings"></a>Genel ayarlar

Bu ayarlar etkiler *olduğunda* Kod düzenleyicisinde biçimlendirme seçeneklerini kod için geçerlidir.

|Etiketle|Açıklama|
|-----------|-----------------|
|**Yazarken Otomatik Biçimlendir**|Seçili olmadığında, **; deyimi biçimlendirme** ve **bloğu}** seçenekleri devre dışı bırakıldı.|
|**Biçim ifadesi üzerinde otomatik olarak;**|Seçili olduğunda, düzenleyici için seçili biçimlendirme seçeneklerine göre tamamlanma deyimleri biçimlendirir.|
|**Otomatik olarak bloğu}**|Bu onay kutusu seçildiğinde, biçimleri kod blokları için Düzenleyicisi kod bloğu tamamlar tamamlamaz seçili biçimlendirme seçeneklerine göre.|
|**Sonrasında Otomatik Biçimlendir**|Bu onay kutusu seçildiğinde, metin biçimleri, **Enter** düzenleyici için seçilen biçimlendirme seçenekleri uyacak şekilde basıldığında.|
|**Yapıştırıldığında otomatik olarak Biçimlendir**|Seçili olduğunda, düzenleyici için seçilen biçimlendirme seçenekleri uyacak şekilde düzenleyicisine yapıştırılan metin biçimlendirir.|

### <a name="format-document-settings"></a>Biçim belgesi ayarları

Bu ayarları yapılandırmak **belgeyi Biçimlendir** bir dosyada ek kod temizleme işlemini gerçekleştirmek için komutu. Bu ayarları nasıl uygulanacağı hakkında daha fazla bilgi için bkz. [belgeyi Biçimlendir komut](../code-styles-and-quick-actions.md#format-document-command).

|Etiketle|Açıklama|Karşılık gelen EditorConfig ve Araçlar > Seçenekler kuralları|
|-----------|-----------------|-----------------|-----------------|
|**Tüm biçimlendirme kuralları (Girinti, sarmalama, aralık) #c Uygula**|**Belgeyi Biçimlendir** her zaman biçimlendirme sorunları giderir komutu. Bu ayar değiştirilemez.| [Çekirdek EditorConfig seçeneği](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig biçimlendirme seçenekleri](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici**  >  **C#**  >   **Biçimlendirme** > [**girinti** veya **yeni satırlar** veya **aralığı** veya **sarmalama**]|
|**Biçimlendirme sırasında ekleme kodu temizleme gerçekleştirin**|Bu onay kutusu seçildiğinde, düzeltmeler aşağıda belirtilen kuralları geçerlidir **Edit.FormatDocument** komutu.| Yok |
|**Gereksiz kullanımları Kaldır**|Seçili olduğunda, gereksiz kaldırır `using` yönergeleri olduğunda **Edit.FormatDocument** tetiklenir.| Yok |
|**Kullanımları sıralama**|Bu onay kutusu seçildiğinde, sıralar `using` yönergeleri olduğunda **Edit.FormatDocument** tetiklenir.| dotnet_sort_system_directives_first<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **Gelişmiş**   >  **Yer 'System' yönergelerini ilk kullanımları sıralarken** |
|**Küme ayraçları için tek satır denetim ifadeleri Ekle/Kaldır**|Bu onay kutusu seçildiğinde, ekler veya küme ayraçları tek satır denetimi deyimlerini kaldırır, **Edit.FormatDocument** tetiklenir.| csharp_prefer_braces<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **Kod bloğu tercihleri** > **küme ayraçlarını tercih et** |
|**Erişilebilirlik değiştiricileri Ekle**|Bu onay kutusu seçildiğinde, eksik erişilebilirlik değiştiricileri ekler, **Edit.FormatDocument** tetiklenir.| dotnet_style_require_accessibility_modifiers |
|**Erişilebilirlik değiştiricileri Sırala**|Bu onay kutusu seçildiğinde, erişilebilirlik değiştiricileri sıralar, **Edit.FormatDocument** tetiklenir.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**İfade veya engelleme gövdesi tercihleri Uygula**|İfade gövdeli üyeler gövdeleri engellemek için bu onay kutusu seçildiğinde, dönüştürür ya da tam tersi zaman **Edit.FormatDocument** tetiklenir.| [İfade gövdeli üye EditorConfig seçeneği](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **İfade tercihleri** > **yöntemleri, Oluşturucular, vb. için ifade gövdesi kullan.** |
|**Örtük/açık tür tercihleri Uygula**|Bu onay kutusu seçildiğinde, dönüştürür `var` açık tür veya tam tersi zaman **Edit.FormatDocument** tetiklenir.| [Açık tür EditorConfig seçeneği](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **'var' tercihleri** |
|**Satır içi 'out' değişken tercihleri Uygula**|Seçili olduğunda, satır içleri `out` değişkenleri burada mümkün olduğunda **Edit.FormatDocument** tetiklenir.| csharp_style_inlined_variable_declaration<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **Değişken tercihleri** > **satır içi değişken bildirimini tercih et** |
|**Dil/framework tür tercihleri Uygula**|Seçildiğinde, language türleri dönüştürür framework türleri veya tam tersi zaman **Edit.FormatDocument** tetiklenir.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **önceden tanımlanmış tür tercihleri** |
|**Nesne/toplama başlatma tercihleri Uygula**|Bu onay kutusu seçildiğinde, mümkün olduğunda nesne ve koleksiyon başlatıcıları kullanır, **Edit.FormatDocument** tetiklenir.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **İfade tercihleri** > **nesne başlatıcısını tercih et** veya **koleksiyon başlatıcısını tercih et** |
|**'This.' niteliği tercihleri Uygula**|Seçili olduğunda geçerlidir `this.` tercihleri olduğunda **Edit.FormatDocument** tetiklenir.| [Bu. Nitelik EditorConfig seçeneği](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **'this.' tercihleri** |
|**Mümkün olduğunda özel alanları salt okunur yapın**|Seçili olduğunda, özel alanlar yapar `readonly` burada mümkün olduğunda **Edit.FormatDocument** tetiklenir.| dotnet_style_readonly_field<br/><br/>**Araçlar** > **seçenekleri** > **metin düzenleyici** > **C#** > **kod stili**   >  **Alan tercihleri** > **salt okunur tercih et** |
|**Gereksiz atamaları Kaldır**|Bu onay kutusu seçildiğinde, mümkün olduğunda gereksiz atamalar kaldırır, **Edit.FormatDocument** tetiklenir.| Yok |
|**Kullanılmayan değişkenler Kaldır**|Bu onay kutusu seçildiğinde, ne zaman kullanılmayan değişkenler kaldırır **Edit.FormatDocument** tetiklenir.| Yok |

![Visual Studio'da C# kod temizleme ayarları](media/format-document-settings.png)

## <a name="preview-windows"></a>Windows Preview

**Girinti**, **yeni satırlar**, **aralığı**, ve **sarmalama** alt her alt kısmında Önizleme penceresini görüntüleyin. Önizleme penceresini her seçeneği etkisini gösterir. Önizleme penceresini kullanmak için biçimlendirme seçeneği seçin. Önizleme penceresini seçeneği örneği gösterilmektedir. Bir ayar radyo düğmesinin veya onay kutusunu, yeni ayar etkisini göstermek için önizleme penceresi güncelleştirmeleri seçerek değiştirdiğinizde.

## <a name="indentation-remarks"></a>Girinti açıklamalar

Girinti seçenekleri üzerinde **sekmeleri** her bir dilin sayfaları yalnızca belirlemek bastığınızda Kod düzenleyicisinde imleci burada yerleştirir **Enter** bir satırın sonunda. Girinti seçenekleri altında **biçimlendirme** dosyaya kod yapıştırdığınızda kod otomatik olarak, örneğin, biçimlendirildiğinde uygulamak **otomatik olarak, yapıştırma sırasında Biçimlendir** seçildiğinde ve ne zaman bloğu biçimlendirilen el ile yazılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)