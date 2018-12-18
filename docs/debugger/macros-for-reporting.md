---
title: Raporlama makroları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056608"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
Hata ayıklama için kullanabilirsiniz **_RPTn** ve **_RPTFn** CRTDBG içinde tanımlı makrolar. Kullanımını değiştirmek için H `printf` deyimleri. Bunları inclose gerekmez **#ifdef**s, bunlar otomatik olarak, yayın kaybolur çünkü ne zaman yapı **_DEBUG** tanımlı değil.  
  
|Makrosu|Açıklama|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Bir ileti dizesi ve sıfır dört bağımsız olarak çıkarır. _RPT1 için **_RPT4**, printf stili biçimlendirme dizesi bağımsız değişkenler için ileti dizesi görür.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Aynı **_RPTn**, ancak bu makroları ayrıca makrosu bulunduğu dosya adı ve satır numarası çıktı.|  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Bu kod değerlerini çıkarır `someVar` ve `otherVar` için **stdout**. Aşağıdaki çağrıyı kullanabilirsiniz `_RPTF2` aynı bu değerleri ve ayrıca, dosya adı ve satır numarası bildirmek için:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Belirli bir uygulama C çalışma zamanı kitaplığı ile sağlanan makroları sağlıyor mu Raporlama hata ayıklama gerektiğini fark edebilirsiniz. Bu durumlarda, özellikle kendi gereksinimlerinizi karşılayacak şekilde tasarlanmış bir makro yazabilirsiniz. Üstbilgi dosyaları her birinde Örneğin, size adlı bir makro tanımlamak için aşağıdaki gibi kod içerebilir **ALERT_IF2**:  
  
```cpp
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Yapılan bir çağrı **ALERT_IF2** tüm işlevlerini yapabilirsiniz **printf** kod:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Daha az veya farklı hedeflere bilgileri raporlamak için özel bir makro kolayca değiştirebilirsiniz. Hata ayıklama gereksinimlerinizi geliştikçe bu yaklaşım özellikle yararlı olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)
