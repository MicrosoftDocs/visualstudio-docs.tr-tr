---
title: IDebugStackFrame2 | Microsoft Docs
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
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc6a6ea1b1d864c3f14158b9687181e6bdb6bc4a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816677"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, belirli bir iş parçacığında bir çağrı yığınındaki bir tek yığın çerçevesini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE), bir yığın çerçevesini temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) almak için bir [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabirimi. Çağrı [sonraki](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) almak için bir [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) içeren yapısı `IDebugStackFrame2` arabirimi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugStackFrame2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Bu yığın çerçevesi için kod bağlamı alır.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Bu yığın çerçevesi için belge bağlamını alır.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Yığın çerçevesinin adını alır.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Yığın çerçevesinin açıklamasını alır.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Bir yığın çerçevesiyle ilgili olan fiziksel adres aralığını makine bağımlı bir gösterimini alır.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Bir yığın çerçevesi ve iş parçacığı geçerli bağlam içinde ifade değerlendirmesi yapmak için bir değerlendirme bağlamı alır.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Bir yığın çerçevesiyle ilgili dilini alır.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Bir yığın çerçevesiyle ilgili özellikleri açıklamasını alır.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Çerçeve Özellikleri yığın için bir numaralandırıcı oluşturur.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Bir yığın çerçevesiyle ilgili iş parçacığı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, yalnızca hata ayıklanan programa (ya da bir kullanıcı kümesi kesme noktası veya bir özel durum nedeniyle) bir kesme noktasında durduruldu olduğunda elde edilir. Bu arabirimden, ifadeler değerlendirilecek bir ifade bağlamı elde edilebilir, kayıtların listesini döndürülebilir veya çağrı yığını elde ve incelenir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)

