---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1369f33e047ed2340ce8f3b181e581512f9bd233
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932123"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Bu yöntem, bir oturum işlemi artık hata ayıklıyor işlem bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSession`  
 [in] Bu işlemden ayırmak için oturum benzersiz olarak tanımlayan bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Arabirim geçirilen `pSession` oturum hata ayıklama Yöneticisi, başlangıçta benzersiz olarak tanımlayan bir değer yalnızca bir tanımlama bilgisi değerlendirilmesi için bu işleme bağlı; sağlanan arabirim yöntemleri hiçbiri işlevsel değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)