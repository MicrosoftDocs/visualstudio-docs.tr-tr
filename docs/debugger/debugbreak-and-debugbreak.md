---
title: DebugBreak ve __debugbreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5eda428410733bf72174676f5a2303a7f625aa7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470479"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak ve __debugbreak
DebugBreak Win32 işlevi çağırabilir veya [__debugbreak](/cpp/intrinsics/debugbreak) kodunuzda herhangi bir noktada iç. `DebugBreak` ve `__debugbreak` bu konumda bir kesme noktası ayarlama aynı etkiye sahiptir.  
  
 Çünkü `DebugBreak` sistem hata ayıklama simgeleri yüklü, doğru çağrı yığını bilgileri sonra kesme görüntülendiğinden emin olmak için bir sistem işlevi çağrısı. Aksi takdirde, hata ayıklayıcı tarafından görüntülenen çağrı yığını bilgileri kapalı bir çerçeve tarafından olabilir. Kullanırsanız `__debugbreak`, simgeler gerekli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleyici iç bilgileri](/cpp/intrinsics/compiler-intrinsics)   
 [Hata ayıklama güvenliği](../debugger/debugger-security.md)   
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Simge (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)