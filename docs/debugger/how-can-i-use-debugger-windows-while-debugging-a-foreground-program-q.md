---
title: Ön plan uygulamasında hata ayıklarken hata ayıklayıcı pencerelerini kullanma | Microsoft Docs
description: Ön planda kalması gereken bir programda hata ayıklaması yapıyorsanız, arka planda yerleştirmekten kaçınmak için uzaktan hata ayıklamayı kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fce51a1a28a8e03692faeee3ed723627864f4031
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386832"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Ön Plan Programında Hata Ayıklarken Hata Ayıklayıcı Penceresini Nasıl Kullanabilirim?
## <a name="problem-description"></a>Sorun Açıklaması
 Bir ekran boyama sorununa hata ayıklamaya çalışıyorum. Bu sorunu gözlemlemek için, programımı ön planda tutdum, yani hata ayıklama pencerelerini erişimim yok. Ne yapabilirim?

## <a name="solution"></a>Çözüm
 İkinci bir bilgisayarınız varsa, uzaktan hata ayıklamayı kullanabilirsiniz. İki bilgisayarlı bir kurulumla, ana bilgisayarda hata ayıklayıcıyı çalıştırırken uzak bilgisayar üzerinde ekran boyamayı izleyebilirsiniz. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
