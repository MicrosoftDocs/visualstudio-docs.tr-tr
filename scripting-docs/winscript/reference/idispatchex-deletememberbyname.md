---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794594"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Üye adına göre siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrName`  
 Silinecek üyenin adı.  
  
 `grfdex`  
 Üye adı büyük küçük harfe duyarlı olup olmadığını belirler. Bu aşağıdaki değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad arama büyük küçük harfe duyarlı bir biçimde yapılması istek sayısı. Büyük küçük harfe duyarlı arama desteklemeyen nesnesi tarafından göz ardı edilebilir.|  
|fdexNameCaseInsensitive|Ad arama büyük küçük harf duyarsız bir biçimde yapılması istek sayısı. Büyük küçük harf duyarsız arama desteklemeyen nesnesi tarafından göz ardı edilebilir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`S_FALSE`|Üye var, ancak silinemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye silinirse, DISPID için geçerli kalır gerekiyor `GetNextDispID`.  
  
 Verilen ada sahip bir üye silinir ve aynı ada sahip bir üye daha sonra yeniden DISPID aynı olmalıdır. (Yalnızca örneğe göre farklılık üyeleri "aynı" olup olmadığını nesne bağlıdır.)  
  
## <a name="example"></a>Örnek  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)