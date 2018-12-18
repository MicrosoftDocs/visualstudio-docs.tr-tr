---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791774"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Komut dosyası için ad alanı için bir tür kitaplığı ekler. Bu benzer `#include` C/c++ yönergesi. Sınıf tanımları gibi önceden tanımlanmış öğeleri kümesi sağlar `typedefs`ve komut dosyası çalışma zamanı ortamı eklenecek sabitleri adlı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `guidTypeLib`  
 [in] Eklenecek CLSID tür kitaplığı.  
  
 `dwMaj`  
 [in] Ana sürüm numarası.  
  
 `dwMin`  
 [in] İkincil sürüm numarası.  
  
 `dwFlags`  
 [in] Bayrakları seçeneği. Aşağıdakiler olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Tür kitaplığını ana bilgisayar tarafından kullanılan bir ActiveX denetimini açıklar.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
|`TYPE_E_CANTLOADLIBRARY`|Belirtilen tür kitaplığı yüklenemedi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)