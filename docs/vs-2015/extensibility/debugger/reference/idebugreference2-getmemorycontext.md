---
title: 'IDebugReference2:: GetMemoryContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d9f3aa8ef59997a326eeae54df1216d96508207
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202503"
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir başvurunun bellek bağlamını alır. Daha sonraki kullanımlar için ayrılmıştır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```csharp  
int GetMemoryContext (   
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppMemory`  
 dışı Başvurunun değeriyle ilişkili belleği temsil eden [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Her zaman `E_NOTIMPL` döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
