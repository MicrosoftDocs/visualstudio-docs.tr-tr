---
title: NameProfile | Microsoft Docs
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
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e56788c36e8c77ec134ed24a7636475c54da664
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733837"
---
# <a name="nameprofile"></a>NameProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`NameProfile` İşlevi belirtilen işlem veya iş parçacığı bir dize atar.  
  
 NameProfile API, yalnızca izleme profil oluşturmak için kullanılabilir. NameProfile API örnekleme profil için desteklenmiyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszName`  
  
 Profil oluşturma öğesinin adı. Bir ad (NameProfileA dönüş NAME_ERROR_INVALID_NAME içinde elde edilen) geçersiz ise:  
  
- NameProfileA geçirilen işaretçi NULL bir değerdir  
  
- PszName dize verilerini bir sayı ile başlatılır.  
  
- Bir alanı pszName dize verilerini içeriyor  
  
- Dize verilerini pszName aşağıdaki karakterlerden herhangi birini içeren:,. ' ~! @# $% ^ & * () = []{}&#124;\\? / <>  
  
  `Level`  
  
  Hangi performans veri toplama uygulanabilir profili düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** değerleri için hangi performans veri toplama uygulanabilir üç düzeylerinden birini belirtmek için kullanılabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Genel düzeyi ayarı tüm işlemleri ve profil oluşturma, iş parçacıklarını etkiler.|  
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı belirtilen işlemin bir parçası olan tüm iş parçacıklarını etkiler.|  
|PROFILE_THREADLEVEL|İş parçacığı düzeyi ayarı profil oluşturma, belirtilen iş parçacığı etkiler.|  
  
 `dwId`  
  
 Profil oluşturma düzeyi tanımlayıcısı. İşlemi kullanın veya iş parçacığı sistem tarafından oluşturulan tanımlayıcısı.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 İşlevi kullanarak başarısı veya başarısızlığı gösterir **PROFILE_COMMAND_STATUS** sabit listesi. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Numaralandırıcı|Açıklama|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|Belirtilen profil oluşturma öğesi yok.|  
|NAME_ERROR_INVALID_NAME|Ad geçersiz.|  
|NAME_ERROR_LEVEL_NOEXIST|Belirtilen düzeyi profili yok.|  
|NAME_ERROR_NO_SUPPORT|Belirtilen işlem desteklenmiyor.|  
|NAME_ERROR_OUTOFMEMORY|Bellek olayı kaydetmek kullanılabilir değildi.|  
|NAME_ERROR_REDEFINITION|Bir ad zaten profil öğesine atandı. Bu işlev adı göz ardı edilir.|  
|NAME_ERROR_TEXTTRUNCATED|Ad metin null karakteri de dahil olmak üzere 32 karakter aştı ve bu nedenle kesildi.|  
|NAME_OK|Adı başarıyla kaydedildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca bir ad, her bir işlem veya iş parçacığı atanabilir. Profil oluşturma bir öğesinin adlı sonra yapılan sonraki çağrılar NameProfile o öğe için göz ardı edilir.  
  
 Farklı iş parçacıkları veya işlemlerdeki için aynı adı belirtilmezse, rapor verilerini bu ada sahip o düzeydeki tüm öğeleri içerir.  
  
 Bir işlem veya iş parçacığı geçerli dışında belirtirseniz, başlatılır ve bunu önce çalışmaya başladığı emin emin olmanız gerekir. Aksi takdirde NameProfile yöntemi başarısız olur.  
  
> [!IMPORTANT]
>  İş parçacığı önce CreateProcess() ve CreateThread() API işlevleri döndürebilir veya işlem başlatılır.  
  
## <a name="net-framework-equivalent"></a>.NET Framework Eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgisi  
  
|||  
|-|-|  
|**Üst bilgi**|VSPerf.h içerir|  
|**Kitaplık**|VSPerf.lib kullanın|  
|**Unicode**|Olarak uygulanan `NameProfileW` (Unicode) ve `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod NameProfile işlev çağrısı göstermektedir. Örneğin, Win32 dize makroların kullanılması ve ANSI kod çağrıları işlevi etkin olup olmadığını belirlemek ANSI derleyici ayarlarını varsayar.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Profil Oluşturucu API Başvurusu (Yerel)](../profiling/visual-studio-profiler-api-reference-native.md)



