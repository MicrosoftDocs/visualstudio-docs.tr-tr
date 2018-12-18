---
title: Geri durdurulduysa MFC'yi çağıran işleve geri dönme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c746fc287435ea6219e0f6052bc9372fc2ae5d25
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048574"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Nasıl Yapılır: Durdurulduysa MFC'yi Çağıran İşleve Geri Dönme

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [ayarlarına](../ide/environment-settings.md#reset-settings).

Kullandıysanız **sonu** komutunu **hata ayıklama** programı durdurmak için menü MFC'de sonuçlandı ve sorunu kodunuzda olduğundan eminseniz işlevinize geri gitmek için çağrı yığını penceresini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: çağrı yığını penceresinde kullanmak](../debugger/how-to-use-the-call-stack-window.md).

Bazen, kodunuzun içinde ileti pompası kesilebilir. Bu durumda, çağrı yığınındaki kullanıcı kodu yok. Bu sorunu önlemek için kesme noktaları (büyük olasılıkla ile koşullar ve isabet sayıları) yerine kullanabileceğiniz **sonu** komutu. Daha fazla bilgi için [kesme noktaları ve izleme noktaları](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC çağrıldı işleve gidin

-   Kullanım **çağrı yığını** penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)