---
title: CommentMarkProfile | Microsoft Docs
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
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d1722cd09bfb76e2ca8c72c6948923b0713100
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802947"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`CommentMarkProfile` İşlevi .vsp dosyasında bir sayısal işareti ve bir metin dizesi ekler. Eklenecek, açıklama ve işareti için içeren iş parçacığı profil oluşturma `CommentMarkProfile` işlevi açık olması gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `lMarker`  
  
 Eklenecek sayısal işaretçisi. İşaretin değerinden büyük veya 0 (sıfır) eşit olmalıdır.  
  
 `szComment`  
  
 Eklenecek metin dizeye yönelik işaretçi. Dize NULL Sonlandırıcı dahil olmak üzere en fazla 256 karakter olmalıdır.  
  
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
 İşaretler ve açıklamaları Vsınstr işareti komutu veya işlevleri (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) ile eklendiğinde işareti profili işlevi içeren iş parçacığı profil durumu olmalıdır.  
  
 Profil işaretleri kapsam içinde geneldir. Örneğin, bir iş parçacığında eklenen bir profili işareti başlangıç veya bitiş .vsp dosyasının içinde herhangi bir iş parçacığı bir veri parçasının işaretlemek için kullanılabilir.  
  
> [!IMPORTANT]
>  CommentMarkProfile yöntemi yalnızca izleme ile kullanılabilir.  
  
## <a name="net-framework-equivalent"></a>.NET Framework Eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgisi  
  
|||  
|-|-|  
|**Üst bilgi**|VSPerf.h içerir|  
|**Kitaplık**|VSPerf.lib kullanın|  
|**Unicode**|Olarak uygulanan `CommentMarkProfileW` (Unicode) ve `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod CommentMarkProfile işlev çağrısı göstermektedir. Win32 dize makroları ve Unicode derleyici ayarları kodu çağıran olup olmadığını belirlemek için örnek varsayar [!INCLUDE[vcpransi](../includes/vcpransi-md.md)] işlev çağrısı.  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Profil Oluşturucu API Başvurusu (Yerel)](../profiling/visual-studio-profiler-api-reference-native.md)



