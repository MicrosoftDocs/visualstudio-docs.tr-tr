---
title: IActiveScript::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791999"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Geçerli iş parçacığının hiçbir sitede sahip yüklenen bir komut dosyası altyapısı döndürme geçerli komut dosyası altyapısı (tüm geçerli yürütme durumu), eksi klonlar. Bu yeni bir komut dosyası motoru özelliklerini özgün komut dosyası altyapısı olarak da geçti varsa Başlatıldı durumuna geri olacaktır özellikler için aynı olacaktır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppscript`  
 [out] Bir işaretçi alan değişkenin adresini [IActiveScript](../../winscript/reference/iactivescript.md) kopyalanan komut dosyası altyapısı arabirimi. Ana site ve çağrı oluşturmalısınız [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) başlatılmış durumda olacaktır önce yeni komut dosyası altyapısı yöntemi ve bu nedenle, kullanılabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
  
## <a name="remarks"></a>Açıklamalar  
 `IActiveScript::Clone` Yöntemdir bir en iyi duruma getirilmesi `IPersist*::Save`, `CoCreateInstance`, ve `IPersist*::Load`, özgün komut dosyası motoru durumu kaydedildi ve yeni bir komut dosyası motoru yüklenmiş gibi yeni bir komut dosyası motoru durumu aynı olmalıdır. Adlandırılmış öğe kopyalanan komut dosyası altyapısında çoğaltıldığından, ancak her öğe için belirli nesne işaretçileri unutmuş ve ile elde edilen [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemi. Bu, kullanılacak iş parçacığı başına giriş noktaları (apartman modeli) ile aynı nesne modeli sağlar.  
  
 Bu yöntem, birden çok örneğini aynı komut dosyasını çalıştırabilirsiniz birden çok iş parçacıklı server konakları için kullanılır. Komut dosyası altyapısı döndürebilir `E_NOTIMPL`, bu durumda ana bilgisayar aynı sonucu durumunu sürekli çoğaltma ve komut dosyası altyapısı ile yeni bir örneğini oluşturarak elde edebilirsiniz bir `IPersist*` arabirimi.  
  
 Bu yöntem bir temel olmayan belirtme çizgisi içinde ana bilgisayar nesneleri veya çok sonuçlanmadan temel olmayan iş parçacığı tarafından çağrılabilir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)