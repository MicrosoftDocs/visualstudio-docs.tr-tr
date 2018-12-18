---
title: C çalışma zamanı kitaplığını kullanmadan çalışma zamanı kullanarak denetler | Microsoft Docs
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
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4929b569c8d40413e948a4b208e7800afb39acb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816781"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C Çalışma Zamanı Kitaplığını Kullanmadan Çalışma Zamanı Denetimlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınızın C çalışma zamanı kitaplığı olmadan kullanıyorsa **/nodefaultlıb**ve çalışma zamanı denetimlerini kullanmak istiyorsanız, RunTmChk.lib ile bağlanmanız gerekir.  
  
 `_RTC_Initialize` programınızın çalışma zamanı denetimleri başlatır. C çalışma zamanı kitaplığı ile bağlamazsanız, programınızın çalışma zamanı hata denetimleri çağırmadan önce ile derlenmiş olup olmadığını görmek için denetlemelisiniz `_RTC_Initialize`gibi:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 C çalışma zamanı kitaplığı ile bağlamazsanız, çağrılan işlev ayrıca tanımlamalısınız `_CRT_RTC_INITW`. `_CRT_RTC_INITW` Kullanıcı tanımlı işlevinizi varsayılan hata raporlama işlevi, şu şekilde yükler:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Varsayılan hata raporlama işlevi yükledikten sonra ek hata raporlama işlevleri ile yükleyebileceğiniz `_RTC_SetErrorFuncW`. Daha fazla bilgi için [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Yerel Çalışma Zamanı Denetimlerini Kullanma](../debugger/how-to-use-native-run-time-checks.md)





