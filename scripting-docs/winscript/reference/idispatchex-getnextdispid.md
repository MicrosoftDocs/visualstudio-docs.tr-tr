---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794711"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Nesne üyeleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `grfdex`  
 Hangi öğeleri kümesidir sıralanması belirler. Bu bir birleşimi aşağıdaki değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexEnumDefault|İstekleri nesne varsayılan öğeleri numaralandırır. Nesne herhangi bir grup öğeyi listeleme izin verilmez.|  
|fdexEnumAll|İstekleri nesne tüm öğeleri numaralandırır. Nesne herhangi bir grup öğeyi listeleme izin verilmez.|  
  
 `id`  
 Geçerli üye tanımlar. Getnextdispıd bunu sonra listedeki öğe alır. Bu tanımlayıcı elde etmek için Getdispıd veya önceki bir Getnextdispıd çağrısı kullanır. İlk öğesinin ilk tanımlayıcısını elde etmek için DISPID_STARTENUM değeri kullanır.  
  
 `pid`  
 Numaralandırmada sonraki öğe tanımlayıcı alan DISPID değişkenin adresini.  
  
 Bir üyesi tarafından silinirse `DeleteMemberByName` veya `DeleteMemberByDispID`, `DISPID` için geçerli kalır gerekiyor `GetNextDispID`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`S_FALSE`|Numaralandırma yapılır.|  
  
## <a name="example"></a>Örnek  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)