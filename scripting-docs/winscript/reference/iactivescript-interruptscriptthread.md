---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792083"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Bir çalışan betik iş parçacığı (bir olay iç havuz, hemen bir yürütme veya makrosu çağırma) çalışmasını kesintiye uğratır. Bu yöntem (örneğin, sonsuz bir döngüde) takılmış bir komut dosyası sonlandırmak için kullanılır. Temel olmayan iş parçacıklarından onu çağrılabilir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `stidThread`  
 [in] İş parçacığı kesme ya da aşağıdaki özel iş parçacığı tanımlayıcısı değerlerden biri tanıtıcısı:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tüm iş parçacıklarının. Kesme, devam eden tüm betik yöntemlerine uygulanır. Çağıran komut bağlantısının kesilmesi istedi sürece, sonraki komut dosyalı olay çağırarak yeniden çalıştırmak bir kod neden olduğunu unutmayın [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_DISCONNECTED yöntemiyle veya SCRIPTSTATE_INITIALIZED bayrağını ayarlayın.|  
|SCRIPTTHREADID_BASE|Temel iş parçacığı; diğer bir deyişle, komut dosyası altyapısını iş parçacığı örneğinin başlatılmasından.|  
|SCRIPTTHREADID_CURRENT|Şu anda yürütülen iş parçacığı.|  
  
 `pexcepinfo`  
 [in] Adres bir `EXCEPINFO` durdurulan komut dosyasına bildirilen hata bilgilerini içeren yapısı.  
  
 `dwFlags`  
 [in] Kesinti ile ilişkili bayraklar seçeneği. Şu değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Destekliyorsa, komut dosyası altyapısı hata ayıklayıcı, geçerli bir komut dosyası yürütme noktada girin.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Komut dosyası altyapısı dil tarafından destekleniyorsa, özel durum işleme komut dosyası sağlar. Aksi takdirde, komut dosyası yöntemi iptal edilir ve çağırana döndürülen hata kodu; diğer bir deyişle, olay kaynağı veya makrosu çağırıcı.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)