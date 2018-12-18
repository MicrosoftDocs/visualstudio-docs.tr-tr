---
title: IScriptEntry::GetSignature | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794951"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Döndürür tür bilgilerini için bir `IScriptEntry` işlev nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppti`  
 [out] Tür bilgilerini bu ile ilişkili `IScriptEntry` işlev nesnesi.  
  
 `piMethod`  
 [out] Yöntem dizinde `ITypeInfo` nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tür bilgileri kullanarak ayarlamak [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) veya [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Tür bilgilerini de iç işlev gösterimi göre giriş tarafından oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iscriptentry arabirimi](../../winscript/reference/iscriptentry-interface.md)