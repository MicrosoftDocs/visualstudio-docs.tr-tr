---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88fcbf0667c026cbbfc449936f92d440590e9a8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834272"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Program sona erer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Mümkünse, program sonlandırıldı ve işlemden kaldırıldı; Aksi takdirde, hata ayıklama altyapısı (DE) gerekli tüm temizleme işlemlerini gerçekleştirir.  
  
 Bu yöntem veya [sonlandırma](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) yöntemi IDE'de, genellikle tüm hata ayıklamayı durdurma kullanıcıya yanıt tarafından çağrılır. İdeal olarak, bu yöntemin uygulanmasını program süreci içinde sonlanmalıdır. Bu mümkün değilse DE program bu işlemde daha fazla engellemeniz (ve gerekli tüm temizleme işlemlerini yapın). Varsa `IDebugProcess2::Terminate` yöntemi, IDE tarafından çağrıldı, süre sonra tüm işlem sonlandırılacak `IDebugProgram2::Terminate` yöntemi çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)