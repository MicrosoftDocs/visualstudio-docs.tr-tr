---
title: CommentMarkAtProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b65b7067dee996f7b50cb98345c2777fc6224df3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805203"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`CommentMarkAtProfile` Yöntemi .vsp dosyasında bir zaman damgası değeri, sayısal işareti ve bir açıklama dizesi ekler. Zaman damgası değeri, dış olayları eşitlemek için kullanılabilir. CommentMarkAtProfile işlevi içeren bir iş parçacığı için profil oluşturma işareti ve yorum eklenecek için açık olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
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
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework Eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgisi  
  
|||  
|-|-|  
|**Üst bilgi**|VSPerf.h içerir|  
|**Kitaplık**|VSPerf.lib kullanın|  
|**Unicode**|(Unicode) CommentMarkAtProfileW ve CommentMarkAtProfileA (ANSI) uygulanır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod CommentMarkAtProfile genel işlev çağrısının kullanımını gösterir. Örneğin, Win32 dize makroların kullanılması ve ANSI kod çağrıları işlevi etkin olup olmadığını belirlemek ANSI derleyici ayarlarını varsayar.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Profil Oluşturucu API Başvurusu (Yerel)](../profiling/visual-studio-profiler-api-reference-native.md)



