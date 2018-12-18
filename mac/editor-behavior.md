---
title: Kod biçimlendirme
description: Bu makale, Mac için Visual Studio Metin Düzenleyicisi davranışı değiştirmek için kullanılabilecek çeşitli seçenekleri açıklar
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 4a34076d06bfceb741b987377487a97291e8f726
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295520"
---
# <a name="editor-behavior"></a>Düzenleyici davranışı

Düzenleyici davranışları yazılmadan olarak biçimlendirilmesi için kod izin vermek için ayarlanabilir. Bu eylemler seçeneklerde ayarladığınız **Visual Studio > Tercihler > Metin Düzenleyicisi > davranışı**, ve daha yaygın olarak kullanılan işlevler bazıları aşağıda açıklanmıştır:

![Düzenleyici davranışı seçenekleri](media/source-editor-image9.png)

* Kapatma küme eşleşen otomatik olarak kodu yeni sınıflar, yöntemler ve Özellikler oluşturulurken eklenebilir. Bu seçenek belirlendiğinde, yazmaya `{` otomatik olarak ekler `}`.
* Üzerinde halindeyken kod biçimlendirme gibi noktalı virgül veya ayarlanan biçimlendirme tercihleri öykünecek küme ayraçları karakter basarsa tetiklenir.
* Dosyayı, istediğiniz gibi kod yazılmasını sağlar ve IDE mevcut Tercihler tarafından belirlenen kod biçimlendirme sorumlu bırakır kaydedilirken biçimlendirmek seçebilirsiniz.
* Girinti, yok, otomatik olarak ayarlanmış olması veya akıllı. Bunlar, aşağıdakileri yapın:
   * Sonraki satır başlangıcına kadar hiçbiri - ayarlar giriş işaretini
   * Auto - giriş işaretini bir sonraki satırında aynı sütuna ayarlar
   * Akıllı - girintileri koduna göre aşağıdaki satırda
* Sözcük bölme davranışı işletim sistemleri arasında farklılık gösterir ve gezinti amacıyla, metin düzenleyici burada sözcükler başlayamaz veya bitemez bilmek ister. Biçimlendirme UNIX ya da Windows için ayarlanabilir.

Ayrıca, XML, CSS, HTML ve JSON için biçimlendirme kurallarını da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod stili tercihleri (Windows için Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)