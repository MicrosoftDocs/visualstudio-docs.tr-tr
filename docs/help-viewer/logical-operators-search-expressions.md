---
title: Mantıksal işleçler ve (Yardım Görüntüleyicisi) arama ifadelerindeki Gelişmiş operatörler
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5e9739ffe1e66186f62bb87ef5ffabdef27801a
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378127"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Arama ifadelerindeki mantıksal ve Gelişmiş işleçler

Yardım içerik, aramanızı daraltmak için mantıksal işleçler ve Gelişmiş arama işleçleri kullanabilirsiniz **Yardım Görüntüleyici**.

## <a name="logical-operators"></a>Mantıksal işleçler

Mantıksal işleçler, arama sorgusu birden çok arama terimlerini birleştirilmelidir belirtin. Aşağıdaki tabloda, mantıksal AND, OR işleçlerini gösterir değil ve NEREDEYSE.

|Aramak için|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Aynı makalede bulunan her iki terim|AND|DIB ve paleti|Hem "DIB" ve "palet" içeren konulardır.|
|Bir makalede her iki terim|VEYA|Izgara veya vektör|"Tarama" veya "vektör" içeren konulardır.|
|Aynı makalede bulunan ikinci terimi olmadan ilk terimi|DEĞİL|"işletim sistemi" DOS değil|"İşletim sistemi" ancak değil "DOS" içeren konulardır.|
|Birbirine yakın bir makaledeki her iki terim|YAKIN|Kullanıcı yakın çekirdek|Yakınlık "çekirdek" içinde "kullanıcı" içeren konuların kapatın.|

> [!IMPORTANT]
> Mantıksal işleçler tanıması arama motoru için tüm büyük harfler girmeniz gerekir.

## <a name="advanced-operators"></a>Gelişmiş operatörler

Gelişmiş arama işleçleri, ilişkin arama terimi aramak için bir makaledeki nerede belirterek içerik için aramanızı daraltın. Aşağıdaki tabloda dört kullanılabilir gelişmiş arama işleçleri açıklanmaktadır.

|Aramak için|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Bir terimi makalesinin başlığı|`title:`|`title:binaryreader`|Kendi başlıklarında "binaryreader" içeren konulardır.|
|Bir kod örneği bir terimi|`code:`|`code:readdouble`|Bir kod örneğinde "readdouble" içeren konulardır.|
|Bir terimi belirli bir programlama dili örneği|`code:vb:`|`code:vb:string`|Visual Basic kod örneğinde "dize" içeren konulardır.|
|Belirli bir dizin anahtar sözcüğüyle ilişkili olan bir makale|`keyword:`|`keyword:readbyte`|"Readbyte" dizin anahtar sözcüğü ile ilgili konular.|

> [!IMPORTANT]
> Son iki nokta üst üste ve arama motoru için iki noktadan önce boşluk olmaması Gelişmiş arama işleçleri tanıması için girmeniz gerekir.

### <a name="programming-languages-for-code-examples"></a>Kod örnekleri için programlama dilleri

Kullanabileceğiniz `code:` çeşitli programlama dillerini ilgili içeriği bulmak için işleci. Belirli bir programlama dili için örnekler döndürmek için programlama dili aşağıdaki değerlerden birini kullanın:

|Programlama dili|Arama işleci söz dizimi|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:` İşleci yalnızca genel kodu olarak işaretlenmiş içerik aksine bir programlama dili etiketi ile işaretlenmiş içeriği bulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Konu arayın](../help-viewer/find-topics.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
