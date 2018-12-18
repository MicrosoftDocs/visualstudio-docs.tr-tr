---
title: Ijsdebugdatatarget::readnullterminatedstring yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795005"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString Yöntemi
Hedef belirtilen sayıda karakteri okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] Okunacak adresi.  
  
 `characterSize`  
 boyutu her karakterinin dize]  
  
 `maxCharacters`  
 [in] Okunacak karakter sayısı. maxCharacters makul olmalıdır. 128 MB'tan fazla bellek için herhangi bir istek başarısız olur.  Dize maxCharacters büyükse, sonuç dizesini maxCharacters sonra kesilir.  
  
 `pString`  
 [out] BSTR hedef okuyun.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Kesirli kısmı S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)