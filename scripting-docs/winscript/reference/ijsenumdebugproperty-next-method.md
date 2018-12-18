---
title: Ijsenumdebugproperty::Next yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794801"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next Yöntemi
Bu nesne için özellikler okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `count`  
 [in] Okunacak özellikleri sayısı.  
  
 `ppDebugProperty`  
 [out] Özellik tarayıcısı temsil eden nesne.  
  
 `pActualCount`  
 [out] Nesnenin özelliklerini gerçek sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsenumdebugproperty arabirimi](../../winscript/reference/ijsenumdebugproperty-interface.md)