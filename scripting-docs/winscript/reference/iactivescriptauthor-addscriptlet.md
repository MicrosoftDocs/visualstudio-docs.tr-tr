---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793292"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Kök düzeyinde alt sitesi olarak kod Resimli ekler `IScriptNode` nesnesi. Ana bilgisayar Resimli tam adı, yalnızca iki düzeylerine sahip izin verilmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszDefaultName`  
 [in] Kod parçacığı ile ilişkilendirmek için varsayılan adı adresidir.  
  
 `pszCode`  
 [in] Kod parçacığı metin adresi.  
  
 `pszItemName`  
 [in] Ana bilgisayar tam Resimli adlarında en üst düzey tanıtıcısı arabellek adresi.  
  
 `pszSubItemName`  
 [in] Ana bilgisayar tam Resimli adlarında ikinci düzey tanıtıcısı arabellek adresi. Ad yalnızca bir düzey varsa NULL olarak ayarlayın.  
  
 `pszEventName`  
 [in] Kod parçacığını bir olay işleyicisi olduğu olay adını içeren bir arabellek adresi.  
  
 `pszDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresi. Zaman `pszCode` ayrıştırılır metin akışından konak genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti), komut dosyası bloğunun sonunu algılamak için kullanır. Bir sınırlayıcı komut dosyası bloğunun sonunu işaretler değil, bu parametre NULL olarak ayarlayın.  
  
 `dwCookie`  
 [in] Kod parçacığını bir ana bilgisayar nesnesi ile ilişkilendirmek için kullanılan bir uygulama tanımlı bir değer.  
  
 `dwFlags`  
 [in] Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)