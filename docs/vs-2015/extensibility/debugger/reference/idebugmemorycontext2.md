---
title: IDebugMemoryContext2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d19bad3f5ec4459c6aacf7b6456be9afb956043a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741176"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, hataları ayıklanan programa çalıştıran makinenin adres alanındaki bir konumu temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE), bellekte bir adresi temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bir çağrı [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) veya [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) bu arabirimi döndürür. Ayrıca, çağrılar [Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) ve [çıkarma](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) uygun aritmetik işlemi uygulandıktan sonra yeni kopyalarını bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugMemoryContext2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Bu bağlam için görüntülenebilir kullanıcı adını alır.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Bu bağlamı açıklayan bilgileri alır.|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Belirtilen değerin yeni bir bağlam oluşturma için geçerli bağlamın adresine ekler.|  
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresi belirtilen bir değeri çıkarır.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Belirtildiği şekilde iki bağlamları karşılaştırır bayrakları karşılaştırın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio'nun **bellek** penceresi çağrıları [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) edinme `IDebugMemoryContext2` bellek adresi için kullanılan Değerlendirilmiş ifadeyi içeren arabirimi. Bu bağlam için geçirilir [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) okumak veya yazmak için adresini belirtmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)

