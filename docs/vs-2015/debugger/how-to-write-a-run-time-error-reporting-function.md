---
title: 'Nasıl yapılır: bir çalışma zamanı hata raporlama işlevi yazma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5d7c9e3d87f7b73ccfad822ef0e7800baaa5b44
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771511"
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>Nasıl Yapılır: Çalışma Zamanı Hata Raporlama İşlevi Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel raporlama işlevi için çalışma zamanı hataları olarak aynı bildirimde olmalıdır `_CrtDbgReportW`. Hata ayıklayıcısı için 1 değerini döndürmesi gerekir.  
  
 Aşağıdaki örnek, bir özel raporlama fonksiyon tanımlayın gösterilmektedir.  
  
## <a name="example"></a>Örnek  
  
```  
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, daha karmaşık özel raporlama işlevini gösterir. Bu örnekte, switch deyimi çeşitli hata türleri tarafından tanımlandığı gibi işler `reportType` parametresinin `_CrtDbgReportW`. Değiştirdiğiniz çünkü `_CrtDbgReportW`, kullanamazsınız `_CrtSetReportMode`. İşlevinizi çıkış işlemesi gerekir. Bu işlevdeki ilk değişken bağımsız değişken bir çalışma zamanı hata numarasını alır. Daha fazla bilgi için [_RTC_SetErrorType](http://msdn.microsoft.com/library/f5f99be7-d357-4b11-b8f5-ddd3428f2b06).  
  
```  
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## <a name="example"></a>Örnek  
 Kullanım `_RTC_SetErrorFuncW` özel işlevinizi yerine yüklemek için `_CrtDbgReportW`. Daha fazla bilgi için [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a). `_RTC_SetErrorFuncW` Dönüş değeri, kaydedebilir ve gerekirse geri önceki raporlama işlevi.  
  
```  
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Çalışma Zamanı Denetimlerini Özelleştirme](../debugger/native-run-time-checks-customization.md)





