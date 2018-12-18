---
title: İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ca585ca547d342daa5ed19776a7cd5d8f8363e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721336"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun açıklaması  
 Kendi programımı belirli bir işlev çağrısı başarısız `CnvtV`. Bu başarısız olmadan önce programı büyük olasılıkla bu işlev birkaç yüzlerce kez çağırır. Ben bir konum kesme noktası ayarlarsanız, `CnvtV`, söz konusu işleve yapılan her çağrıda programı durdurur ve bu istemiyorum. Koşullu kesme noktası olarak ayarlanamıyor için hangi koşullar çağrının başarısız olmasına neden bilmiyorum. Ne yapabilirim?  
  
## <a name="solution"></a>Çözüm  
 İşlevi ile bir kesme noktası ayarlayabilirsiniz **Hit Count** , hiçbir zaman ulaşılacak kadar yüksek bir değer alanı. Bu durumda, işlev düşünüyorsanız çünkü `CnvtV` birkaç çağrılır, yüzlerce kez ayarlayabilirsiniz **isabet sayısı** 1000 veya daha fazla. Ardından programı çalıştırın ve başarısız çağrının tamamlanmasını bekleyin. Bu başarısız olduğunda, kesme noktaları penceresi açın ve kesme noktalarının listesine bakın. Üzerinde ayarladığınız kesme noktası `CnvtV` görünür, ardından isabet sayısı ve kalan yineleme sayısı:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 İşlev 101st çağrıda başarısız olduğunu biliyorsunuz. Kesme noktası isabet sayısını 101 ile sıfırlama ve programı yeniden çalıştırın, program çağrısı durakları `CnvtV` , başarısız olmasına neden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod hata ayıklaması SSS](../debugger/debugging-native-code-faqs.md)   
 [Kesme noktaları ayarlama](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)



