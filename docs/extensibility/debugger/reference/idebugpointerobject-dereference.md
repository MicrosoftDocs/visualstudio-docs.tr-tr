---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b173394aba18c47a18a7a683db0f35d474bb4eeb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833856"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Belirtilen nesnenin alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwIndex`  
 [in] İşaret nesne başlangıcı basit bayt uzaklığı.  
  
 `ppObject`  
 [out] Döndürür bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesini temsil eden işaret yanı sıra uzaklığı, varsa nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılıysa S_OK döndürür; Aksi takdirde bir hata kodu döndürür. Bu nesne başka bir nesneye işaret etmiyorsa E_FAIL döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 İşaret edilen nesnenin, basit bir tür veya bir sınıf veya yapı gibi daha karmaşık bir tür olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)