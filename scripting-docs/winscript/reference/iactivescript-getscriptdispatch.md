---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791951"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Alır `IDispatch` arabirim yöntemleri ve özellikleri şu anda çalışan komut dosyasıyla ilişkilidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrItemName`  
 [in] Kendisi için arayan ilişkili dağıtım nesnesi gerekiyor öğesinin adını içeren bir arabellek adresi. Bu parametre ise `NULL`, komut dosyası tarafından tanımlanan tüm genel yöntemleri ve özellikleri üye olarak dağıtım nesnesi içerir. Aracılığıyla `IDispatch` arabirimi ve ilişkili `ITypeInfo` arabirimi, konak betik yöntemleri ya da Görünüm çağırma ve komut dosyası değişkenleri değiştirin.  
  
 `ppdisp`  
 [out] Komut dosyanızın genel yöntemleri ve özellikleri ile ilişkili nesne için bir işaretçi alan değişkenin adresini. Komut dosyası altyapısı böyle bir nesnenin desteklemiyorsa `NULL` döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
|`S_FALSE`|Komut dosyası altyapısı, dağıtım nesnesi desteklemiyor; `ppdisp` parametresi NULL olarak ayarlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemleri ve özellikleri çağırarak eklenebilir olduğundan [Iactivescriptparse](../../winscript/reference/iactivescriptparse.md) arabirimi, `IDispatch` bu yöntem tarafından döndürülen arabirimi yeni yöntemleri ve özellikleri dinamik olarak destekleyebilir. Benzer şekilde, `IDispatch::GetTypeInfo` yöntemi döndürmelidir yeni, benzersiz `ITypeInfo` arabirim yöntemleri ve özellikleri eklendiğinde. Ancak, dil motorları değiştirmemelisiniz unutmayın `IDispatch` arabiriminde bir şekilde uyumlu herhangi bir önceki `ITypeInfo` döndürüldü arabirim. Bu, örneğin, DISPID değerleri hiçbir zaman yüklenmek anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)