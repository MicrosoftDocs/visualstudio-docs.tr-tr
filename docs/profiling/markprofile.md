---
title: MarkProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98530a790963d1c7fc60742dda4bb16e14a28ab4
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238166"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile` Yöntemi bir profil işareti ekler. *Vsp* dosya. İş parçacığı içeren için profil oluşturma `MarkProfile` işlevi eklenecek işareti açık olması gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `lMarker`  
  
 Eklenecek işaretçisi. İşaretin 0 (sıfır) değerine eşit veya daha büyük olmalıdır.  
  
## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri  
 Kullanarak işlevi başarısını veya başarısızlığını gösterir **PROFILE_COMMAND_STATUS** numaralandırması. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Parametre, küçük veya 0 değerine eşit değil. Bu değerler ayrılmıştır. Açıklama ve işareti kaydedilmedi.|  
|MARK_ERROR_MODE_NEVER|Hiçbir zaman işlevi çağrıldığında profil oluşturma modu ayarlandı. Açıklama ve işareti kaydedilmedi.|  
|MARK_ERROR_MODE_OFF|İşlevi çağrıldığında profil oluşturma modu OFF olarak ayarlandı. Açıklama ve işareti kaydedilmedi.|  
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işareti desteği yok. Açıklama ve işareti kaydedilmedi.|  
|MARK_ERROR_OUTOFMEMORY|Olay kaydetmek bellek yoktu. Açıklama ve işareti kaydedilmedi.|  
|MARK_TEXTTOOLONG|Dize en fazla 256 karakter aşıyor. Açıklama dizesi kesilir ve yorum ve işareti kaydedilir.|  
|MARK_OK|MARK_OK başarılı olduğunu belirtmek için döndürülür.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşareti değeri eklenir. *vsp* dosya kodu MarkProfile işlevi içeren iş parçacığı profili, her çalıştığında. Birden çok kez MarkProfile çağırabilirsiniz.  
  
 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığında eklenen bir profili işareti başlangıç ya da herhangi bir iş parçacığı veri segmentinin sonunu işaretlemek için kullanılabilir. *vsp* dosya.  
  
 İşaretleri ve yorumları API işlevleri (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) veya işareti komutu ile yerleştirildiğinde işareti profili işlevi içeren iş parçacığı için profil oluşturma durumu olmalıdır.  
  
> [!IMPORTANT]
>  MarkProfile yöntemi araçları yalnızca profil oluşturma ile kullanılması gerekir.  
  
## <a name="net-framework-equivalent"></a>.NET framework eşdeğeri  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>İşlev bilgisi  
 Başlık: bildirilen *VSPerf.h*  
  
 İçeri aktarma kitaplığı: *VSPerf.lib*  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod MarkProfile işlev gösterir.  
  
```cpp  
void ExerciseMarkProfile()  
{  
    // Declare and initialize variables to pass to   
    // MarkProfile.  The values of these parameters   
    // are assigned based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variables are assigned arbitrary values.  
    int markId = 03;  
  
    // Declare enumeration to hold return value of   
    // call to MarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    markResult = MarkProfile(markId);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("MarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio profil oluşturucu API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)