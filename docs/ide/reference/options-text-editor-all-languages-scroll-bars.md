---
title: Seçenekler, metin düzenleyici tüm diller, kaydırma çubukları
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Scroll_Bars
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdff9d71055ff1357bff82d27fa8df5916e0a699
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220570"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Seçenekler, metin düzenleyici tüm diller, kaydırma çubukları
Bu iletişim kutusu Kod Düzenleyicisi kaydırma çubuğunun varsayılan davranışını değiştirmenizi sağlar. Bu seçenekleri görüntülemek için seçin **seçenekleri** gelen **Araçları** menüsü. İçinde **metin düzenleyici** klasörünü genişletin **tüm diller** alt ve ardından **kaydırma çubukları**.

> [!CAUTION]
> Bu sayfa, tüm geliştirme diller için varsayılan seçenekleri ayarlar. Bu iletişim kutusunda bir seçenek sıfırlama hangi seçenekler burada seçilen için tüm diller kaydırma çubukları seçeneklerinde sıfırlar. Yalnızca bir dilin metin düzenleyici seçenekleri değiştirmek için bu dil için alt klasörü genişletin ve seçeneği sayfalarını seçin.

## <a name="show-horizontal-scroll-bar"></a>Yatay kaydırma çubuğunu göster

Seçili olduğunda, düzenleyici görüntüleme alanı dışında kalan view öğeleri yan yana kaydırmak izin veren bir yatay kaydırma çubuğu, görüntüler. Yatay kaydırma çubukları kullanılamıyorsa, kaydırmak için imleç tuşlarını kullanabilirsiniz.

## <a name="show-vertical-scroll-bar"></a>Dikey kaydırma çubuğunu göster

Seçili olduğunda, düzenleyici görüntüleme alanı dışında kalan view öğeleri yukarı ve aşağı kaydırarak olanak tanıyan dikey bir scrollbar görüntüler. Dikey kaydırma çubuklarının kullanılamaz, Page Up, Page Down ve imleç anahtarları kaydırmak için kullanabilirsiniz.

## <a name="display"></a>Ekran

### <a name="show-annotations-over-vertical-scroll-bar"></a>Dikey kaydırma çubuğunun üzerinde ek açıklamalarını göster

Dikey kaydırma çubuğunun şu ek açıklamaları gösterip göstermediği seçin:

- değişiklikler
- işaretler
- hatalar
- şapka

> [!TIP]
> **İşaretleri Göster** seçeneği, kesme noktaları ve yer imlerini içerir.

Büyük kod bir dosyası açarak ve metin dosyasında çeşitli yerlerde meydana değiştirerek deneyin. Kaydırma çubuğu bir şey kaydetmemeniz değiştirirse, değişikliklerinizi yedekleyebilirsiniz bu nedenle değişiklik etkisini gösterir.

## <a name="behavior"></a>Davranış

Kaydırma çubuğu iki modu vardır: çubuk modu ile eşleme modu.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğunun çubuk modunu kullan

*Çubuk modunu* ek açıklama göstergeleri kaydırma çubuğundaki görüntüler. Kaydırma çubuğundaki sayfa yukarı veya aşağı kaydır ancak dosyayı bu konuma geçmez.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Dikey kaydırma çubuğu için eşleme modunu kullan

İçinde *eşleme modu*, kaydırma çubuğu, imleç atlar yerine yalnızca bir sayfa aşağı veya yukarı kaydırma dosyanın bu konumda bir konuma tıklayın. Kod satırlarını, kaydırma çubuğundaki küçük gösterilir. Ne kadar geniş sütun eşleme olan bir değer seçerek seçebilirsiniz **kaynak genel bakış**. Harita üzerinde işaretçiyi getirdiğinizde, kodun daha büyük bir önizlemesini etkinleştirmek için seçin **önizleme araç ipucunu göster** seçeneği. Daraltılmış bölgeleri farklı şekilde gölgeli ve bunları çift tıkladığınızda genişletin.

> [!TIP]
> Küçük kod görünümü eşleme modunda ayarlayarak kapatabilirsiniz **kaynak genel bakış** için **kapalı**. Varsa **önizleme araç ipucunu göster** olan seçildiğinde kodunun bu konumunda bir önizleme kaydırma çubuğundaki işaretçinizi üzerine gelin ve tıkladığınızda imleç hala dosyanın bu konumda atlar görmeye.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: kaydırma çubuğunu özelleştirme](../how-to-track-your-code-by-customizing-the-scrollbar.md)