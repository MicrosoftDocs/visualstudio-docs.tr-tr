---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793268"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Belirtilen öznitelikleri Resimli döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdisp`  
 [in] `IDispatch` Karşılık gelen nesne `NamedItem` Resimli ekli olduğu için.  
  
 `pszItem`  
 [in] Ana bilgisayar tam Resimli adlarında en üst düzey tanıtıcısı arabellek adresi.  
  
 `pszSubItem`  
 [in] Ana bilgisayar tam Resimli adlarında ikinci düzey tanıtıcısı arabellek adresi. Ad yalnızca bir düzey varsa NULL olarak ayarlayın.  
  
 `pszEvent`  
 [in] Olay adı içeren bir arabellek adresi. Kod parçacığı, bu olay için olay işleyicisidir.  
  
 `ppse`  
 [out] Bir işaretçi alan değişkenin adresini `IScriptEntry` belirtilen öznitelikleri Resimli arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Iscriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)