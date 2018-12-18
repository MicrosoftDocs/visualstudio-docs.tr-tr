---
title: IDispatchEx::GetMemberProperties | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795053"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Bir üyenin özellikleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. Kullanan `GetDispID` veya `GetNextDispID` gönderme tanımlayıcısı alınamadı.  
  
 `grfdexFetch`  
 Almak için hangi özellikleri belirler. Bu altında listelenen değerleri bir bileşimi olabilir `pgrfdex` ve/veya bir birleşimi aşağıdaki değerlerden biri:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|grfdexPropCanAll|FdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct ve fdexPropCanSourceEvents birleştirir.|  
|grfdexPropCannotAll|FdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct ve fdexPropCannotSourceEvents birleştirir.|  
|grfdexPropExtraAll|FdexPropNoSideEffects ve fdexPropDynamicType birleştirir.|  
|grfdexPropAll|GrfdexPropCanAll, grfdexPropCannotAll ve grfdexPropExtraAll birleştirir.|  
  
 `pgrfdex`  
 Adres bir `DWORD` istenen özellikleri alır. Bu bir birleşimi aşağıdaki değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexPropCanGet|Üye DISPATCH_PROPERTYGET kullanılarak edinilebilir.|  
|fdexPropCannotGet|Üye DISPATCH_PROPERTYGET kullanarak elde edilemiyor.|  
|fdexPropCanPut|Üye DISPATCH_PROPERTYPUT kullanarak ayarlayabilirsiniz.|  
|fdexPropCannotPut|Üye DISPATCH_PROPERTYPUT kullanarak ayarlanamaz.|  
|fdexPropCanPutRef|Üye DISPATCH_PROPERTYPUTREF kullanarak ayarlayabilirsiniz.|  
|fdexPropCannotPutRef|Üye DISPATCH_PROPERTYPUTREF kullanarak ayarlanamaz.|  
|fdexPropNoSideEffects|Üye herhangi yan etkileri yok. Örneğin, güvenli bir şekilde get/set/çağrısı bir hata ayıklayıcısı verebilir ayıklanacak betik durumunu değiştirmeden bu üye.|  
|fdexPropDynamicType|Üye dinamiktir ve nesnesinin ömrü boyunca değiştirebilirsiniz.|  
|fdexPropCanCall|Üye DISPATCH_METHOD kullanarak bir yöntem olarak çağrılabilir.|  
|fdexPropCannotCall|Üye DISPATCH_METHOD kullanarak bir yöntem olarak çağrılamaz.|  
|fdexPropCanConstruct|Üye DISPATCH_CONSTRUCT kullanarak bir oluşturucu çağrılabilir.|  
|fdexPropCannotConstruct|Üye DISPATCH_CONSTRUCT kullanarak bir oluşturucu çağrılamaz.|  
|fdexPropCanSourceEvents|Üye olayları tetikleyebilir.|  
|fdexPropCannotSourceEvents|Üye olayları harekete olamaz.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`DISP_E_UNKNOWNNAME`|Adı bilinmiyor.|  
  
## <a name="example"></a>Örnek  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)