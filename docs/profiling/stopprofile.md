---
title: StopProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e03abc331d59504b1b08136c8c81fe12c8ba2af
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264201"
---
# <a name="stopprofile"></a>StopProfile
`StopProfile` İşlevi için belirtilen profil düzeyi 0 (Kapalı) sayaç ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Level`  
  
 Hangi performans veri toplama uygulanabilir profili düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** numaralandırmalar, hangi performans veri toplama uygulanabilir üç düzeylerinden birini belirtmek için kullanılabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Genel düzeyi ayarı, tüm işlemler ve Çalıştır profil oluşturma iş parçacıkları etkiler.|  
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı belirtilen işleminin bir parçası olan tüm iş parçacıklarının etkiler.|  
|PROFILE_THREADLEVEL|İş parçacığı düzeyi ayarı profil belirtilen iş parçacığı etkiler.|  
  
 `dwId`  
  
 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.  
  
## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri  
 Kullanarak işlevi başarısını veya başarısızlığını gösterir **PROFILE_COMMAND_STATUS** numaralandırması. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Profil oluşturma öğesi kimliği yok.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Düzey belirtilen profil yok.|  
|PROFILE_ERROR_MODE_NEVER|Hiçbir zaman işlevi çağrıldığında profil oluşturma modu ayarlandı.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profil oluşturma işlev çağrısı, profil düzeyinde veya arama ve düzeyi birleşimi henüz uygulanmadı.|  
|PROFILE_OK|Çağrı başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 StartProfile ve StopProfile profil düzeyi Başlat/Durdur durumunu denetler. Başlat/Durdur varsayılan değeri 1'dir. Başlangıç değeri kayıt defterinde değiştirilebilir. Her çağrı StartProfile Başlat/Durdur 1 olarak ayarlar; her çağrı StopProfile 0 olarak ayarlanır.  
  
 Başlat/Durdur 0'dan büyük Başlat/Durdur durumu düzeyi için açık olur. Küçük veya 0 değerine eşit olduğunda Başlat/Durdur durumu Kapalı'dır.  
  
 Başlat/Durdur durumu ve askıya alma/sürdürme durumu hem de açık olduğunda, profil düzeyi için açık bir durumda. İş parçacığı olması için genel işlem profili ve iş parçacığı için iş parçacığı düzeyi durumları açık olması gerekir.  
  
## <a name="net-framework-equivalent"></a>.NET framework eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgisi  
 Başlık: VSPerf.h içinde bildirilen  
  
 İçeri aktarma kitaplığı: VSPerf.lib  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek StopProfile yöntemi gösterilmektedir. Örnek StartProfile yöntemine bir çağrı aynı iş parçacığı veya tarafından tanımlanan işlemi için yapılan varsayar [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```cpp  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio profil oluşturucu API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)