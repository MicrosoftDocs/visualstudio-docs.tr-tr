---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5e84180747a3e6a3b9e5a34e7694f4cd07867c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121563"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Bu arabirim bir kod konuma bağlamak hazır bir kesme noktası temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE), kesme noktaları desteğini bir parçası olarak bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) gelen bekleyen bir kesme noktası oluşturur bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) arabirimi. Çağrı [bağlamak](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) oluşturur bir `IDebugBreakpoint2` programa bağımlı bir kesme noktası temsil eden arabirim.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugPendingBreakpoint2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bu bekleyen kesme bir kod konuma bağlayabilirsiniz olup olmadığını belirler.|  
|[Bağlama](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bu bekleyen kesme bir veya daha fazla kod konumlara bağlar.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bu durum kesme noktası bekleyen alır.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bu bekleyen kesme noktası oluşturmak için kullanılan kesme isteğini alır.|  
|[Sanallaştırma](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Bu sanallaştırılmış kesme noktası bekleyen durumunu değiştirir.|  
|[Etkinleştir](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bu etkin kesme noktası bekleyen durumunu değiştirir.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Bu kesme noktası ilişkilendirilen koşulu değiştirir veya ayarlar.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Bu kesme noktası ilişkili geçişi sayısı değiştirir veya ayarlar.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Bu bekleyen kesme bağlı tüm kesme noktaları numaralandırır.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bu bekleyen kesme sonuçlandı tüm hata kesme noktaları numaralandırır.|  
|[Sil](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bu bekleyen kesme ve ondan bağlı tüm kesme noktalarını siler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDebugPendingBreakpoint2` bir veya daha çok programlar uygulanabilir kod bir kesme noktası bağlamak için gereken tüm gerekli bilgileri sağlayıcı olarak değerlendirilebilir.  
  
 Bekleyen bir kesme noktası büyük olasılıkla birden fazla bağımlı kesme noktası oluşturabilir. Örneğin, bir kesme noktası C++ stili şablondaki şablon benzersiz her örneği için ilişkili bir kesme noktası üretebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)