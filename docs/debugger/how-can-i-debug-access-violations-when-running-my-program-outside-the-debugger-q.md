---
title: Uygulama hata ayıklayıcı dışında çalıştırırken erişim İhlallerinde hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42284de1195afb3b0926b15335c8e37bdcd5ec30
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048482"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?

## <a name="problem-description"></a>Sorun açıklaması  
 Kendi programımı Visual Studio ortamında düzgün çalışıyor, ancak bu tek başına Windows işletim sistemiyle birlikte çalıştırabilir, erişim ihlali üretir. Bu sorunu nasıl hata ayıklaması yapabilirsiniz?  
  
## <a name="solution"></a>Çözüm  
 Ayarlama [Just-ın-time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçenek ve erişim ihlali gerçekleşene kadar tek başına programınızı çalıştırın. Ardından **erişim ihlali** iletişim kutusu, tıklayabilirsiniz **iptal** hata ayıklayıcıyı başlatmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod hata ayıklaması SSS](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)