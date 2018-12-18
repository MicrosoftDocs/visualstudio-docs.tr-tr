---
title: CONTEXT_COMPARE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a17d0b422b65093721a55d4bf8d632aba271a55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950816"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
İki bellek bağlamları karşılaştırma ölçütü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Üyeler  
 CONTEXT_EQUAL  
 Hedef bellek bağlamına eşit olan listesinde ilk bellek içeriği bulur.  
  
 CONTEXT_LESS_THAN  
 Hedef bellek bağlam'dan küçük listedeki ilk bellek bağlam bulun.  
  
 CONTEXT_GREATER_THAN  
 Hedef bellek bağlamını anlamaktan büyük listesinde ilk bellek içeriği bulur.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Hedef bellek bağlam eşit veya daha az olan listesinde ilk bellek içeriği bulur.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Büyüktür veya eşittir hedef bellek bağlam listedeki ilk bellek bağlam bulun.  
  
 CONTEXT_SAME_SCOPE  
 Hedef bellek bağlamı ile aynı kapsamda olan listesinde ilk bellek içeriği bulur.  
  
 CONTEXT_SAME_FUNCTION  
 Hedef bellek kapsamla aynı işlevde listesinde ilk bellek içeriği bulabilirsiniz.  
  
 CONTEXT_SAME_MODULE  
 Hedef bellek içerik olarak aynı modülde listesinde ilk bellek içeriği bulabilirsiniz.  
  
 CONTEXT_SAME_PROCESS  
 Hedef bellek içerik olarak aynı işlemde olan listesinde ilk bellek içeriği bulur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bağımsız değişken olarak geçirilen [karşılaştırma](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) yöntemi.  
  
 Bu değerler, belirtilen karşılaştırma ölçütleri karşılayan bir listedeki ilk bellek içeriği bulmak için kullanılır. Bir bellek bağlamı kendisine karşı karşılaştırmak için bellek içerikleri bir listesi verilir `IDebugMemoryContext2::Compare` yöntemi. Karşılaştırma işleci olan listede ilk bellek bağlam `true` sonra döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)