---
title: Atama kancaları ve C çalışma zamanı bellek ayırmaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433112"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Atama Kancaları ve C Çalışma Zamanı Bellek Ayırmaları
Atama kanca işlevleri çok önemli bir kısıtlama bunlar açıkça yoksayması gereken olduğu `_CRT_BLOCK` engeller. Bu, iç bellek C çalışma zamanı kitaplık işlevleri yapılan her çağrı yaparsanız C çalışma zamanı kitaplığı işlevleri tarafından dahili olarak yapılan bellek ayırmaları taşlarıdır. Yoksayabilirsiniz `_CRT_BLOCK` , ayrılan başında eşlemelerinden kod ekleyerek blok kanca işlevini:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Varsa, atama kanca yoksaymaz `_CRT_BLOCK` , içindeki kanca adlı tüm C çalışma zamanı kitaplığı işlevi sonsuz bir döngünün program yakalayabilir sonra engeller. Örneğin, `printf` iç ayırma sağlar. Kanca kodunuzu çağırırsa `printf`, ortaya çıkan ayırma, kanca yeniden çağrılacak olan çağıracak neden olmaz **printf** yeniden, vb. kadar yığın taşıyor. Rapora ihtiyacınız varsa `_CRT_BLOCK` ayırma işlemleri, bu kısıtlama aşmak için bir yol olan biçimlendirmek için C çalışma zamanı işlevleri yerine Windows API işlevlerini kullanın ve çıkacağını. Windows API'ları C çalışma zamanı kitaplığı yığın kullanmayın çünkü, atama kanca sonsuz bir döngüde tuzak olmaz.  
  
 Çalışma zamanı kitaplığı kaynak dosyaları incelerseniz göreceğiniz işlevi, varsayılan ayırma kanca olduğunu **CrtDefaultAllocHook** (yalnızca döndüren **TRUE**), kendine ait, ayrı bir dosyada bulunan DBGHOOK. C. Bile, uygulamanızın önce yürütülen çalışma zamanı başlatma kodu tarafından yapılan ayırmaları çağrılmasına, atama kanca isteyip istemediğinizi **ana** işlevi, bir kendi yerine bu varsayılan işlev değiştirebilirsiniz kullanarak [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama kanca işlevi yazma](../debugger/debug-hook-function-writing.md)   
