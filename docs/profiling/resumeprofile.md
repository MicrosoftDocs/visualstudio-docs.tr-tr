---
title: ResumeProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b15c57766c2deadc65e0d2d7d2b41baa50bf50e5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677271"
---
# <a name="resumeprofile"></a>ResumeProfile
`ResumeProfile` Yöntemi azaltır askıya alma/sürdürme sayaç için belirtilen profil oluşturma düzeyi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Level`  
  
 Hangi performans veri toplama uygulanabilir profili düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** numaralandırıcılar, hangi performans veri toplama uygulanabilir üç düzeylerinden birini belirtmek için kullanılabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Genel düzeyi ayarı tüm işlemleri ve profil oluşturma, iş parçacıklarını etkiler.|  
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı belirtilen işlemin bir parçası olan tüm iş parçacıklarını etkiler.|  
|PROFILE_THREADLEVEL|İş parçacığı düzeyi ayarı profil oluşturma, belirtilen iş parçacığı etkiler.|  
  
 `dwId`  
  
 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.  
  
## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri  
 İşlevi kullanarak başarısı veya başarısızlığı gösterir **PROFILE_COMMAND_STATUS** sabit listesi. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Profil oluşturma öğesi kimliği yok.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Düzey belirtilen profil yok.|  
|PROFILE_ERROR_MODE_NEVER|HİÇ işlev çağrıldığında profil oluşturma modunda ayarlandı.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profil oluşturma işlev çağrısı, profil oluşturma düzeyinde veya çağrı ve düzey henüz uygulanmadı.|  
|PROFILE_OK|Çağrı başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Askıya alma/sürdürme sayacın başlangıç değeri 0'dır. SuspendProfile yapılan her çağrı için askıya alma/sürdürme sayısı 1 ekler; her çağrı ResumeProfile 1 çıkarır.  
  
 Askıya alma/sürdürme sayısı 0'dan büyük olduğunda düzeyi için askıya alma/sürdürme durumu Kapalı'dır. Sayı 0'a eşit veya daha az olduğunda, askıya alma/sürdürme durumu açıktır.  
  
 Başlat/Durdur durumunda ve askıya alma/sürdürme durumu hem de açık olduğunda, profil oluşturma durumu düzeyi için açıktır. İş parçacığı olacak şekilde, genel işlem profili ve iş parçacığı düzeyi durumlar iş parçacığı için tüm açık.  
  
## <a name="net-framework-equivalent"></a>.NET framework eşdeğeri  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>İşlev bilgisi  
 Başlık: bildirilen *VSPerf.h*  
  
 İçeri aktarma kitaplığı: *VSPerf.lib*  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ResumeProfile işlevi gösterir. Örnekte, aynı iş parçacığı veya işlem tarafından tanımlanan SuspendProfile yönteme bir çağrı yapıldı varsayılır [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```cpp  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio profil oluşturucu API Başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)