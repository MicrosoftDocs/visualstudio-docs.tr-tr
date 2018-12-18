---
title: CommentMarkAtProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4eb29336b401b020df52d1ccaa743bb7240e1d2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854825"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile` Yöntemi, bir zaman damgası değeri, sayısal işareti ve bir açıklama dizesi olarak ekler. *Vsp* dosya. Zaman damgası değeri, dış olayları eşitlemek için kullanılabilir. CommentMarkAtProfile işlevi içeren bir iş parçacığı için profil oluşturma işareti ve yorum eklenecek için açık olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dnTimestamp`  
  
 Zaman damgası değeri temsil eden bir 64-bit tamsayı.  
  
 `lMarker`  
  
 Eklenecek sayısal işaretçisi. İşaretin değerinden büyük veya 0 (sıfır) eşit olmalıdır.  
  
 `szComment`  
  
 Metin dizesi eklemek için bir işaretçi. Dize NULL Sonlandırıcı dahil olmak üzere en fazla 256 karakter olmalıdır.  
  
## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri  
 İşlevi kullanarak başarısı veya başarısızlığı gösterir **PROFILE_COMMAND_STATUS** sabit listesi. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Parametresi veya 0'a eşit olan küçük. Bu değerler ayrılmıştır. Açıklama ve işareti kaydedilmez.|  
|MARK_ERROR_MODE_NEVER|HİÇ işlev çağrıldığında profil oluşturma modunda ayarlandı. Açıklama ve işareti kaydedilmez.|  
|MARK_ERROR_MODE_OFF|İşlev çağrıldığında, profil oluşturma modunda OFF olarak ayarlandı. Açıklama ve işareti kaydedilmez.|  
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işareti desteği yok. Açıklama ve işareti kaydedilmez.|  
|MARK_ERROR_OUTOFMEMORY|Bellek olayı kaydetmek kullanılabilir değildi. Açıklama ve işareti kaydedilmez.|  
|MARK_TEXTTOOLONG|Dize en fazla 256 karakter aşıyor. Açıklama dizesi kesilmiş ve işareti ve yorum kaydedilir.|  
|MARK_OK|MARK_OK tamamlandığını bildiren döndürülür.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşaretler ve açıklama işareti komutu veya API işlevleri (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) ile eklendiğinde işareti profili işlevi içeren iş parçacığı profil durumu olmalıdır. Profil işaretleri kapsam içinde geneldir. Örneğin, bir iş parçacığında eklenen bir profili işareti başlangıç veya bitiş .vsp dosyasının içinde herhangi bir iş parçacığı bir veri parçasının işaretlemek için kullanılabilir.  
  
> [!IMPORTANT]
>  CommentMarkAtProfile yöntemleri, yalnızca izleme ile kullanılmalıdır.  
  
## <a name="net-framework-equivalent"></a>.NET framework eşdeğeri  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>İşlev bilgisi  
  
|||  
|-|-|  
|**Üst bilgi**|Dahil *VSPerf.h*|  
|**Kitaplık**|Kullanım *VSPerf.lib*|  
|**Unicode**|(Unicode) CommentMarkAtProfileW ve CommentMarkAtProfileA (ANSI) uygulanır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod CommentMarkAtProfile genel işlev çağrısının kullanımını gösterir. Örneğin, Win32 dize makroların kullanılması ve ANSI kod çağrıları işlevi etkin olup olmadığını belirlemek ANSI derleyici ayarlarını varsayar.  
  
```cpp  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio Profiler API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)