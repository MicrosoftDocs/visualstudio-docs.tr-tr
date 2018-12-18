---
title: Kaydırma çubuğu eşleme modu ve çubuğu modu
ms.date: 09/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f60d7f573ed275ff4d827e0a4209f21444ee64c
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219958"
---
# <a name="how-to-customize-the-scroll-bar"></a>Nasıl yapılır: kaydırma çubuğunu özelleştirme

Uzun kod dosyaları ile çalışırken, her şeyi dosyasında olduğu, izlenmesi zor olabilir. Kodunuzda olup bitenleri genel bir resmini vermek için Kod Düzenleyicisi, kaydırma çubuğu özelleştirebilirsiniz.

## <a name="annotations"></a>Ek Açıklamalar

Kaydırma çubuğu ek açıklamaları gibi kod değişiklikleri, kesme noktaları, yer işaretleri, hataları ve şapka gösterip göstermediği seçebilirsiniz.

   1. Açık **kaydırma çubukları** seçerek seçenekler sayfası **Araçları** > **seçenekleri** > **metin düzenleyici**  >  **Tüm diller** > **kaydırma çubukları**.

   2. Seçin **dikey kaydırma çubuğunun üzerinde ek açıklamalarını göster**, görmek istediğiniz ek açıklamaları'ı seçin. Kullanılabilir ek açıklamalar şunlardır:

      - değişiklikler
      - işaretler
      - hatalar
      - şapka

      > [!TIP]
      > **İşaretleri Göster** seçeneği, kesme noktaları ve yer imlerini içerir.

Büyük kod bir dosyası açarak ve metin dosyasında çeşitli yerlerde meydana değiştirerek deneyin. Kaydırma çubuğu bir şey kaydetmemeniz değiştirirse, değişikliklerinizi yedekleyebilirsiniz bu nedenle değişiklik etkisini gösterir.

İşte nasıl bir dize için arama yaptıktan sonra kaydırma çubuğu görünür. Dizesinin tüm örnekleri kaydırma çubuğunda görüntülendiğine dikkat edin.

![Bir dize için arama sonra visual Studio kaydırma çubuğu](../ide/media/enhancedscrollbarsearch.png)

Dizesinin tüm örnekleri değiştirildikten sonra kaydırma çubuğu aşağıdadır. Metin değişimi hataları Burada sunulan kaydırma çubuğunu göster kırmızı işaretler.

![Visual Studio kaydırma çubuğuna hatalarla bir dize değiştirdikten sonra](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Görüntü modları

Kaydırma çubuğu iki modu vardır: çubuk modu ile eşleme modu.

### <a name="bar-mode"></a>Çubuğu modu

*Çubuk modunu* ek açıklama göstergeleri kaydırma çubuğundaki görüntüler. Kaydırma çubuğundaki sayfa yukarı veya aşağı kaydır ancak dosyayı bu konuma geçmez.

### <a name="map-mode"></a>Eşleme modu

İçinde *eşleme modu*, kaydırma çubuğu, imleç atlar yerine yalnızca bir sayfa aşağı veya yukarı kaydırma dosyanın bu konumda bir konuma tıklayın. Kod satırlarını, kaydırma çubuğundaki küçük gösterilir. Ne kadar geniş sütun eşleme olan bir değer seçerek seçebilirsiniz **kaynak genel bakış**. Harita üzerinde işaretçiyi getirdiğinizde, kodun daha büyük bir önizlemesini etkinleştirmek için seçin **önizleme araç ipucunu göster** seçeneği. Daraltılmış bölgeleri farklı şekilde gölgeli ve bunları çift tıkladığınızda genişletin.

> [!TIP]
> Küçük kod görünümü eşleme modunda ayarlayarak kapatabilirsiniz **kaynak genel bakış** için **kapalı**. Varsa **önizleme araç ipucunu göster** olan seçildiğinde kodunun bu konumunda bir önizleme kaydırma çubuğundaki işaretçinizi üzerine gelin ve tıkladığınızda imleç hala dosyanın bu konumda atlar görmeye.

Eşleme modu etkin ve genişliğini ayarlamak aşağıdaki görüntüde arama örnek gösterilmektedir **orta**:

![Visual Studio kaydırma çubuğu eşleme modunda](../ide/media/enhancedscrollbar.png)

Aşağıdaki görüntüde **önizleme araç ipucunu göster** seçeneği:

![Visual Studio kaydırma çubuğu içeren bir araç ipucu](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)