---
title: Kesme noktasıyla ilgili metotlar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7e823c5fef66077ba03d4cb9eec4367b79038db
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152153"
---
# <a name="breakpoint-related-methods"></a>Kesme noktasıyla ilgili metotlar
Hata ayıklama altyapısı (DE), kesme noktaları ayarını desteklemesi gerekir. Visual Studio hata ayıklama kesme noktaları aşağıdaki türlerini destekler:  
  
-   bağlı  
  
     Kullanıcı Arabirimi aracılığıyla istenen ve başarılı bir şekilde bir kod belirtilen konuma bağlı  
  
-   Bekleniyor  
  
     UI ancak gerçek henüz bağlı yönergeleri istendi  
  
## <a name="discussion"></a>Tartışma  
 Bekleyen kesme noktası gibi yönergeleri henüz yüklenmedi oluşur. Ne zaman kod, kod belirtilen konumda, diğer bir deyişle bağlamak için kod içinde kesme yönergeleri eklemek için kesme noktaları deneyin bekleyen yüklenir. Olayları, başarılı bir bağlama belirtin veya bağlama hatalar bildirmek için oturum hata ayıklama Yöneticisi (SDM) gönderilir.  
  
 Bir bekleyen kesme noktasının da kendi iç karşılık gelen bağlı kesme noktaları listesini yönetir. Bir kesme noktası bekleyen çok sayıda kesme noktaları ekleme kodu neden olabilir. Visual Studio kullanıcı Arabirimi hata ayıklama bekleyen kesme noktalarını ağaç görünümünü gösterir ve bunlara karşılık gelen bağlı kesme noktaları.  
  
 Oluşturma ve bekleyen kesme noktalarını kullanımını gerektiren uygulaması [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) yöntemi ve bunun yanı sıra aşağıdaki yöntemleri [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimleri.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Belirtilen bir olup olmadığını belirleyen bir kod konuma kesme noktası bağlayabilirsiniz.|  
|[bağlama](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Belirtilen bir kesme noktası için bir veya daha fazla kod konumlarını bağlar.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Bir bekleyen kesme noktasının durumunu alır.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Bekleyen kesme noktası oluşturmak için kullanılan kesme noktası istek alır.|  
|[Etkinleştirme](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bir bekleyen kesme noktasının etkinleştirilen durumunu değiştirir.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Tüm kesme noktalarını bir bekleyen kesme noktasından bağlı numaralandırır.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Bir bekleyen kesme noktasından neden tüm hata kesme noktalarını numaralandırır.|  
|[DELETE](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Bir bekleyen kesme noktasının ve ondan bağlı tüm kesme noktalarını siler.|  
  
 Hata kesme noktaları ve bağlı kesme noktaları numaralandırmak için tüm yöntemleri uygulamalıdır [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) ve [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Bir konum gerektirme aşağıdaki uygulaması bekleyen bir kodunu bağlamak kesme noktaları [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) yöntemleri.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Bir kesme noktasını içeren bekleyen kesme noktasının alır.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Bağlı bir kesme noktasının durumunu alır.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Bir kesme noktası açıklayan bir kesme noktası çözünürlüğü alır.|  
|[Etkinleştirme](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Etkinleştirir ya da bir kesme noktası devre dışı bırakır.|  
|[DELETE](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|İlişkili bir kesme noktasını siler.|  
  
 Çözüm ve bilgi gerektiren aşağıdaki uygulaması istek [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) yöntemleri.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Bir çözüm tarafından temsil edilen kesme noktası türünü alır.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktası açıklayan kesme noktası çözünürlüğü bilgileri alır.|  
  
 Bağlama sırasında oluşabilecek hatalar çözümlemesini gerektirir aşağıdaki uygulaması [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) yöntemleri.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Bir hata kesme noktasını içeren bekleyen kesme noktasının alır.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Bir hata kesme noktası açıklayan kesme noktası hata çözünürlüğü alır.|  
  
 Bağlama sırasında oluşabilecek hatalar çözümlenmesi aşağıdaki yöntemleri de gerektirir [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Bir kesme noktası türünü alır.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Bir kesme noktası çözümleme bilgilerini alır.|  
  
 Bir kesme noktasında kaynak kodunu görüntüleme gerektirir yöntemlerini uygulamak [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve/veya yöntemlerini [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)