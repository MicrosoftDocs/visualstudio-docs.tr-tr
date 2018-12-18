---
title: Biçimlendirme seçenekler, metin düzenleyici, XAML, | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
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
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c86c7d2913b5fe112181bec2e9dc1bec12273b5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824459"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]


Kullanım **biçimlendirme** öğeler ve öznitelikler XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için özellik sayfası. Açmak için **seçenekleri** iletişim kutusu, tıklayın **Araçları** menüsünü seçin ve ardından **seçenekleri**. Erişim için **biçimlendirme** özellik sayfasında **metin düzenleyici**, **XAML**, **biçimlendirme** düğümü.  

> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  

## <a name="auto-formatting-events"></a>Otomatik biçimlendirme olayları  
 Otomatik biçimlendirme oluşabilir, aşağıdaki olaylardan herhangi biri algılandı.  

- Bir bitiş etiketi ya da basit etiket tamamlama.  

- Bir başlangıç etiketi tamamlandığında.  

- Panodan yapıştırarak.  

- Klavye komutlarını biçimlendirme.  

  Otomatik biçimlendirme olayları neden belirtebilirsiniz.  

|||  
|-|-|  
|**Bitiş etiketi ya da basit etiket tamamlandığında**|Otomatik biçimlendirme bir bitiş etiketi ya da basit etiket yazmayı bitirdikten sonra gerçekleşir. Basit bir etiket öznitelikleri, örneğin yok `<Button />`.|  
|**Başlangıç etiketi tamamlandığında**|Otomatik biçimlendirme, bir başlangıç etiketi yazmayı bitirdikten sonra gerçekleşir.|  
|**Pano'dan üzerinde Yapıştır**|XAML görünümü panodan XAML yapıştırın otomatik biçimlendirme gerçekleşir.|  

## <a name="quotation-mark-style"></a>Tırnak işareti stili  
 Bu ayar, öznitelik değerleri tek veya çift tırnak içine alınmış olup olmadığını gösterir. Otomatik-biçimlendirici ve IntelliSense otomatik tamamlama, bu ayarı kullanın.  

 Bu seçeneği belirlediğinizde, yalnızca öznitelikler, daha sonra Tasarımcı kullanılarak eklenen veya el ile XAML görünümünde etkilenir.  

|||  
|-|-|  
|**Çift tırnak (")**|Öznitelik değerleri çift tırnak işareti içine alınır.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Tek tırnak (')**|Öznitelik değerleri tek tırnak işaretleri içine alınır.<br /><br /> `<Button Name='button1'>Hello</Button>`|  

## <a name="tag-wrapping"></a>Etiket kaydırma  
 Etiket sarmalama için bir satır uzunluğu belirtebilirsiniz. Etiket kaydırma etkin olduğunda, tüm XAML Tasarımcısı'nı kullanarak daha sonradan eklenen uygun şekilde sarmalanır.  

|||  
|-|-|  
|**Belirtilen uzunluğu geçen etiketleri Kaydır**|Tarafından belirtilen satır uzunluğu'konumundaki satırları sarmalanmış olup olmadığını belirtir **uzunluğu**.|  
|**Uzunluğu**|Bir satırın karakter içerebilir. Gerekirse, bazı XAML satırları belirtilen satır uzunluğu aşabilir.|  

## <a name="attribute-spacing"></a>Öznitelik aralığı  
 XAML belgenizde öznitelikleri nasıl düzenlenir denetlemek için bu ayarı kullanın.  

|||  
|-|-|  
|**Satır başı ve öznitelikleri arasındaki boşlukları koru**|Yeni satırlar ve öznitelikler arasında boşluk tarafından otomatik olarak biçimlendirme etkilenmez.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Öznitelikler arasına tek boşluk Ekle**|Öznitelikleri bir boşluk ile ayırarak bitişik öznitelikleri bir satır kaplayabilir. Etiket sarmalama ayarları uygulanır.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Her özniteliği ayrı bir satıra Yerleştir**|Her öznitelik kendi satırına kaplar. Fazla öznitelik mevcut olduğunda bu kullanışlıdır.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Konum ilk özniteliği başlangıç etiketiyle aynı satıra**|Bu onay kutusu işaretlendiğinde, öğenin başlangıç etiketi ile aynı satırda ilk öznitelik görünür.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  

## <a name="element-spacing"></a>Öğe aralığı  
 XAML belgenizde öğeleri nasıl düzenlenir denetlemek için bu ayarı kullanın.  


|                                                               |                                                                                                                                                                                              |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               **İçeriği yeni satırları koru**               | Öğe içeriği boş satırları kaldırılmaz.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>\` |
| **İçerikte birden çok boş satırlar için tek bir satırı Daralt** | Öğe içeriği boş satırları tek bir satıra daraltılır.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`  |
|               **İçerikteki boş satırları Kaldır**               |                        Öğesi içerik tüm boş satırlar kaldırıldı.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                        |

## <a name="auto-insert"></a>Otomatik Ekle  
 Etiketleri ve teklifler ne zaman otomatik olarak oluşturulan denetlemek için bu ayarı kullanın.  

|||  
|-|-|  
|**Kapanış etiketleri**|Büyüktür (>) karakteri ile açılış etiketinde'ı kapattığınızda, bir öğenin kapatma etiketi otomatik olarak oluşturulup oluşturulmayacağını belirtir.|  
|**Öznitelik tırnak işaretleri**|Deyim tamamlama açılır listeden bir öznitelik değeri seçildiğinde çevreleyen tırnak oluşturulup oluşturulmadığını belirtir.|  
|**Küme ayraçları Markupextension'lar için kapanış**|Açılış yazdığınızda, bir biçimlendirme uzantının kapanış ayracından (}) otomatik olarak oluşturulup oluşturulmayacağını belirtir ayracı karakteri ({}).|  
|**MarkupExtension parametrelerini ayıran ayırmak için virgül**|Birden fazla parametre bir işaretleme uzantısı'nda yazarken virgül oluşturulup oluşturulmadığını belirtir.|  

## <a name="default-view"></a>Varsayılan Görünüm  
 Tasarım görünümü XAML belgeleri yüklendiğinde görünür olup olmadığını denetlemek için bu ayarı kullanın.  

|||  
|-|-|  
|**Tam XAML görünümünde her zaman açık belgeler**|XAML belgeleri yalnızca Tasarım görünümü olmadan XAML Görünümü'nde görüntülenip görüntülenmeyeceğini belirtir. Büyük belgelerin yüklenmesi için yararlıdır.|  

## <a name="toolbox"></a>Araç Kutusu  
 Kullanıcı denetimleri ve özel denetimler araç kutusunda gösterilip gösterilmeyeceğini belirtmek için bu ayarı kullanın.  

|||  
|-|-|  
|**Araç kutusu öğeleri otomatik olarak doldurur.**|Kullanıcı denetimleri ve geçerli çözüme özel denetimleri araç kutusunda otomatik olarak gösterilip gösterilmeyeceğini belirtir.|  

## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de XAML](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Nasıl yapılır: XAML Görünümü Ayarları Değiştir](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [XAML ve kod gözden geçirmeleri](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)



