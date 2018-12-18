---
title: Atama kanca işlevleri | Microsoft Docs
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
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d201f22d461a04890899ac1cebc177cb1521555
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743347"
---
# <a name="allocation-hook-functions"></a>Atama Kanca İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanarak yüklü bir ayırma kanca işlevini [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), bellek tahsis, yeniden tahsis veya serbest her zaman çağrılır. Bu tür bir kanca birçok farklı amaçlarla kullanılabilir. Bunu nasıl bir uygulama yetersiz bellek durumları, örneğin, işleme test etmek için veya ayırma desenlerini incelenmesi veya daha sonraki analizler için ayırma bilgileri günlüğe kaydetmek için kullanın.  
  
> [!NOTE]
>  Kısıtlama C çalışma zamanı kitaplık işlevleri açıklandığı bir ayırma kanca işlevini kullanma hakkında bilmeniz [ayırma kancaları ve C çalışma zamanı bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Bir ayırma kanca işlevini aşağıdaki gibi bir prototipe sahip olmalıdır:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Geçirdiğiniz işaretçiyi [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) türünde **_CRT_ALLOC_HOOK**CRTDBG içinde tanımlanan gibi. Y:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Çalışma zamanı kitaplığı, kanca çağırdığında *nAllocType* bağımsız değişken belirtir hangi ayırma işlemidir hakkında gerçekleştirilecek (**_HOOK_ALLOC**, **_HOOK_REALLOC**, veya **_HOOK_FREE**). Ücretsiz veya bir reallocation söz konusu olduğunda `pvData` serbest bırakılacak bloğun kullanıcı konuya bir işaretçi içerir. Ancak bir ayırma söz konusu olduğunda ayırma değil henüz oluştuğundan Bu işaretçi null olabilir. Kalan bağımsız değişkenleri ayırmanın boyutu söz konusu, blok türü varsa ve bir işaretçi ayırma yapıldığı, dosya adı ve satır numarası ile ilişkili ardışık istek numarasını içerir. Hangi analizi kanca işlevini gerçekleştirir ve diğer görevler, yazar istediği sonra ya da döndürmelidir **TRUE**, ayırma işlemi devam edebilir, gösteren veya **FALSE**gösteren, işlem başarısız olmalıdır. Bu tür bir basit kanca şimdiye ayrılan bellek miktarını denetleyin ve dönüş **FALSE** bu kadar küçük bir sınır aşılırsa. Uygulama türü yalnızca kullanılabilir bellek düşük olduğunda, normalde oluşacak ayırma hatalarının ardından deneyimleyeceği. Daha karmaşık kancaları ayırma desenlerini izlemek, bellek kullanımını analiz etme veya özel durumlar oluştuğunda bildirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Atama kancaları ve C çalışma zamanı bellek ayırmaları](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Hata ayıklama kanca işlevi yazma](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 örnek](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



