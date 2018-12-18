---
title: IDebugMemoryContext2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26ae199d1fee210559f599cdfe1393aeae5dd169
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115089"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Bu arabirim ayıklanacak program çalışan makinenin adres alanındaki bir konumu temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) bellekteki bir adresi temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) veya [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) bu arabirimini döndürür. Ayrıca, çağrılar [Ekle](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) ve [çıkarma](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) uygun aritmetik işlemin uygulandıktan sonra yeni kopya bu arabirimin döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugMemoryContext2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Bu bağlam için kullanıcı görüntülenebilir adını alır.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Bu bağlamda açıklayan bilgileri alır.|  
|[Ekleme](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Belirtilen değer, yeni bir bağlam oluşturmak için geçerli bağlamın adresine ekler.|  
|[Çıkarma](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Yeni bir bağlam oluşturmak için geçerli bağlamın adresi belirtilen değeri çıkarır.|  
|[Karşılaştırma](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Belirtildiği şekilde iki bağlamları karşılaştırır bayrakları karşılaştırın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio'nun **bellek** penceresi çağrıları [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) almak için `IDebugMemoryContext2` bellek adresi için kullanılan Değerlendirilmiş ifadeyi içeren arabirimi. Bu bağlamda sonra geçirilir [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) ve [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) okumak veya yazmak için adresini belirtmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)