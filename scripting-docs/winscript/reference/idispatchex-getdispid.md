---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794870"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Ardından sonraki çağrılar kullanılabilir, karşılık gelen DISPID tek üye adı eşlendiği `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrName`  
 Eşlenecek adı geçirildi.  
  
 `grfdex`  
 Üye tanımlayıcısını alma seçenekleri belirler. Bu bir birleşimi aşağıdaki değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad arama büyük küçük harfe duyarlı bir biçimde yapılması istek sayısı. Büyük küçük harfe duyarlı arama desteklemiyor nesnesiyle yoksayılabilir.|  
|fdexNameEnsure|Zaten yoksa, üye oluşturulması ister. Yeni üye değeriyle oluşturulmalıdır `VT_EMPTY`.|  
|fdexNameImplicit|Çağrıyı yapan temel nesne açıkça belirtilmediğinde belirli bir ada sahip bir üye için nesneleri arıyor gösterir.|  
|fdexNameCaseInsensitive|Ad arama büyük küçük harf duyarsız bir biçimde yapılması istek sayısı. Büyük küçük harf duyarsız arama desteklemiyor nesnesiyle yoksayılabilir.|  
  
 `pid`  
 İşaretçi DISPID sonuç almak için bir konuma çağıran tarafından ayrılmış. Bir hata oluşursa, `pid` DISPID_UNKNOWN içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`DISP_E_UNKNOWNNAME`|Adı bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetDispID`yerine kullanılabilir `GetIDsOfNames` için belirtilen bir üyenin DISPID elde edilir.  
  
 Çünkü `IDispatchEx` ekleme ve silme üyelerinin DISPID değerleri kümesi durumda sabit bir nesne yaşam süresi için izin verir.  
  
 Kullanılmayan `riid` parametresinde `IDispatch::GetIDsOfNames` kaldırılmıştır.  
  
## <a name="example"></a>Örnek  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)