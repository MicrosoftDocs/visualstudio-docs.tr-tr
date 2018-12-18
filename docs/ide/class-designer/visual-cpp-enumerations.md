---
title: Sınıf Tasarımcısında Visual C++ Numaralandırmaları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a42dfb65cc70704bbed662e35b2e2eb0e9c237c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922026"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Sınıf tasarımcısında Visual C++ numaralandırmaları

**Sınıf Tasarımcısı** C++ destekler `enum` ve kapsamlı `enum class` türleri. Aşağıda bir örnek verilmiştir:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Sınıf diyagramında C++ numaralandırması Şekil arar ve çalıştığını yapısı şekli gibi etiketi okur dışında **Enum** veya **Enum sınıfı**, mavi yerine pembe ve üst ve sol renkli kenarlık vardır Kenar boşlukları. Numaralandırma şekiller ve yapısı şekiller kare köşeleri vardır.

Kullanma hakkında daha fazla bilgi için `enum` yazın, bkz: [numaralandırmalar](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sabit Listeleri](/cpp/cpp/enumerations-cpp)