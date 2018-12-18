---
title: FxCopCmd hataları
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71e2a39b792dcc5a01eb28611664736f6620bb1f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688880"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd araç hataları

FxCopCmd önemli olması için tüm hataları dikkate almaz. FxCopCmd kısmi analiz gerçekleştirmek için yeterli bilgi varsa, oluşan analiz ve raporları hatalar gerçekleştirir. Bir 32 bitlik tamsayıdır, hata kodu karşılaştırmaya hataları karşılık gelen sayısal değerleri içerir.

Aşağıdaki tabloda FxCopCmd tarafından döndürülen hata kodları açıklanmaktadır:

|Hata|Sayısal değer|
|-----------|-------------------|
|Hata yok|0x0|
|Analiz hatası|0x1|
|Kuralın özel durumları|0x2|
|Proje yükleme hatası|0x4|
|Derleme yükleme hatası|0x8|
|Kural kitaplık yükleme hatası|0x10|
|İçeri aktarma rapor yükleme hatası|0x20|
|Çıkış hatası|0x40|
|Komut satırı geçiş hatası|0x80|
|Başlatma hatası|0x100|
|Derleme başvuruları hatası|0x200|
|BuildBreakingMessage|0x400|
|Bilinmeyen hata|0x1000000|

**Analiz hatası** için önemli hatalar döndürülür. Analiz tamamlanamadı gösterir. Uygun olduğunda hata kodu önemli hata temel nedenini de içerir. Aşağıdaki koşullar önemli hatalar oluşturur:

- Analiz yetersiz girişi nedeniyle gerçekleştirilemedi.

- Analiz FxCopCmd tarafından işlenmemiş özel durum oluşturdu.

- Belirtilen proje dosyası bulunamadı veya bozuk olabilir.

- Output seçeneği belirtilmedi veya dosya yazılmadı.

> [!NOTE]
> FxCopCmd dönüş kodu **derlemeye başvuran hata** 0x200 tek başına bir hata yerine bir uyarı olduğunu. FxCopCmd bunları işleyebilmesi olduğunu dolaylı başvuruları eksik, bu dönüş kodu gösterir. Uyarı, bazı analiz sonuçları gizliliği bozulmuş olabilecek, olasılığı anlamına gelir. İşle **derlemeye başvuran hata** diğer dönüş kodu ile birleştirildiğinde hata olarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Çözümleme Uygulama Hataları](../code-quality/code-analysis-application-errors.md)