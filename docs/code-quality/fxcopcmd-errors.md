---
title: FxCopCmd hataları
ms.date: 10/19/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 657e650f9244fb97d4990e04a60b9e1f93794af4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924267"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd aracı hataları

FxCopCmd önemli olması için tüm hataların dikkate almaz. FxCopCmd kısmi analiz gerçekleştirmek için yeterli bilgiye sahip oluştu analiz ve raporları hataları gerçekleştirir. Bir 32 bit tamsayı ise, hata kodu hataları karşılık gelen sayısal değerlerin Bitsel bir birleşimi içerir.

Aşağıdaki tabloda FxCopCmd tarafından döndürülen hata kodları açıklanmaktadır:

|Hata|Sayısal değer|
|-----------|-------------------|
|Hiçbir hata|0x0|
|Çözümleme hatası|0x1|
|Kural özel durumları|0x2|
|Proje yükleme hatası|0x4|
|Derleme yükleme hatası|0x8|
|Kural kitaplığı yükleme hatası|0x10|
|İçeri aktarma rapor yükleme hatası|0x20|
|Çıkış hatası|0x40|
|Komut satırı anahtarı hatası|0x80|
|Başlatma hatası|0x100|
|Derleme başvuruları hata|0x200|
|BuildBreakingMessage|0x400|
|Bilinmeyen hata|0x1000000|

**Çözümleme hatası** önemli hataları döndürülür. Analiz tamamlanamadı belirtir. Uygun olduğunda, hata kodu önemli hatanın temel nedenini de içerir. Aşağıdaki koşullar önemli hatalar oluşturur:

- Analiz yetersiz giriş nedeniyle gerçekleştirilemedi.

- Analiz FxCopCmd tarafından işlenmemiş bir özel durum oluşturdu.

- Belirtilen proje dosyası bulunamadı veya bozuk olabilir.

- Output seçeneği belirtilmedi veya dosya yazılmadı.

> [!NOTE]
> FxCopCmd dönüş kodu **bütünleştirilmiş koduna başvuruyor hata** kendisi tarafından 0x200 olan bir hata yerine bir uyarı. FxCopCmd bunları kaldırabilir, ancak bu dönüş kodu dolaylı başvurular var. eksik gösterir. Uyarı, bazı çözümleme sonuçlarını geçirildiğini olduğunu olasılığı anlamına gelir. İşle **bütünleştirilmiş koduna başvuruyor hata** diğer dönüş kodu ile birlikte kullanıldığında bir hata olarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Çözümleme Uygulama Hataları](../code-quality/code-analysis-application-errors.md)