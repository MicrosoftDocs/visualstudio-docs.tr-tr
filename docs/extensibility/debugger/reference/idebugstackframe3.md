---
title: IDebugStackFrame3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 635b53bf63eb83cc868e4bf9b7d5fbb31fe5aa08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120628"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Bu arabirim genişletir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) ilerlemesinden özel durumları işleme.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) bu arabirimi uygulayan aynı nesne üzerinde uygulayan [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) ilerlemesinden özel durumlar desteklemek için arabirim.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [QueryInterface](/cpp/atl/queryinterface) üzerinde bir `IDebugStackFrame2` bu arabirimi sağlamak için arabirim.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Kaynağından devralındı yöntemleri yanı sıra [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` aşağıdaki yöntemlerini gösterir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Interceptcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Geçerli yığın çerçevesini önce tüm normal özel durum işleme için bir özel durum işleme.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Yığın bırakma oluşmasına olsaydı bir kod bağlamını döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ele geçirilen bir özel durum normal özel durum işleme rutinleri çalışma zamanı tarafından çağrılmadan önce bir hata ayıklayıcısı bir özel durum işleyebileceği anlamına gelir. Bir özel durum temelde kesintiye uğratan bile olmadığında mevcut bir özel durum işleyici olduğunu içeriğini çalıştırma yapmadan anlamına gelir.  
  
 [Interceptcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) sırasında tüm normal özel durum geri çağırma olayları olarak adlandırılır (tek özel durum (yönetilen ve yönetilmeyen kodu), karma mod kodu; bu durumda özel olamaz ele sırasında ayıkladığınız durumunda olduğu son fırsat geri çağırma). DE uygulamazsa `IDebugStackFrame3`, veya DE IDebugStackFrame3 bir hata döndürür::`InterceptCurrentException` (gibi `E_NOTIMPL`), sonra da hata ayıklayıcısını özel normal olarak işleyecek.  
  
 Bir özel durum uğratarak hata ayıklayıcı ayıklanacak programın durumunu değişiklikler yapmak ve burada özel durum oluştu noktada yürütme devam etmek kullanıcı izin verebilirsiniz.  
  
> [!NOTE]
>  İlerlemesinden özel durumlar yalnızca yönetilen kodda, diğer bir deyişle, ortak dil çalışma zamanı (CLR) altında çalışan bir programı izin verilir.  
  
 Hata ayıklama altyapısı "metricExceptions" ayarlayarak kesintiye uğratan özel durumlar desteklediğini değeri 1 için çalışma zamanında kullanarak gösterir `SetMetric` işlevi. Daha fazla bilgi için bkz: [hata ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Hata Ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)