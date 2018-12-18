---
title: Raporlama makroları | Microsoft Docs
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
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc2a5226b3d6f512d2c2f89d9fef2a80eef34340
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758452"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz **_RPTn**, ve **_RPTFn** CRTDBG içinde tanımlı makrolar,. Kullanımını değiştirmek için H `printf` hata ayıklama için deyimleri. Bu makrolar, sürümde otomatik olarak kaybolur ne zaman yapı **_DEBUG** içine alınmaları gerekmez. Bu nedenle, tanımlanmamış **#ifdef**s.  
  
|Makrosu|Açıklama|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Bir ileti dizesi ve sıfır dört bağımsız değişken olarak çıkarır. _RPT1 için **_RPT4**, printf stili bir biçimlendirme dizesi bağımsız değişkenler için ileti dizesi görür.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Aynı **_RPTn** , fakat bu makrolar da makro bulunduğu dosyanın adı ve satır numarası çıktı.|  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Bu kodu değerini çıkarır `someVar` ve `otherVar` için **stdout**. Aşağıdaki çağrısını kullanabilirsiniz `_RPTF2` bildirme aynı değerler ve ayrıca, dosya adı ve satır numarası:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Belirli bir uygulama, C çalışma zamanı kitaplığı ile sağlanan makroları sağlamadığı bildirme hatalarını ayıklama gerektiğini fark ederseniz, özellikle kendi gereksinimlerinizi karşılayacak şekilde tasarlanmış bir makro yazabilirsiniz. Üstbilgi dosyalarınızın her birinde Örneğin, adında bir makro tanımlamak için aşağıdaki gibi kod içerebilir **ALERT_IF2**:  
  
```  
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
  
 Çağrı **ALERT_IF2** tüm işlevlerini gerçekleştirebilir **printf** bu konunun başındaki kod:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Özel bir makro daha az veya farklı hedeflere (ne daha uygun olduğuna bağlı olarak) rapor için kolayca değiştirilebilir çünkü hata ayıklama gereksinimleriniz değiştikçe bu yaklaşım özellikle yararlı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)



