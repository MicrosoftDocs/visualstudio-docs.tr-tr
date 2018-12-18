---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1c0b636c88c2c2e23efcc01b01eec1e421317e0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831106"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Hata ayıklama altyapısı adres alanında yönetilen nesnesinin bir kopyasını oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppObject`  
 [out] Döndürür bir [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) yeni oluşturulan yönetilen nesneyi temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılıysa S_OK döndürür; Aksi takdirde bir hata kodu döndürür. Bu E_FAIL döndürür [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) yönetilen değeri sınıfı örneğini temsil etmiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesne gerekir temsil eden bir yönetilen değeri sınıf örneği gibi bir `System.Decimal` örneği. Yerel bir kopya arama getirdiği ek yüke sahip [değerlendir](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)