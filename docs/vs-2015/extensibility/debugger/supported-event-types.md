---
title: Desteklenen olay türleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd6f8f5b7c2782bb908538426cb531db216b72fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781471"
---
# <a name="supported-event-types"></a>Desteklenen Olay Türleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio hata ayıklama, şu anda aşağıdaki olay türlerini destekler:  
  
- Zaman uyumsuz olay  
  
   Oturum hata ayıklama Yöneticisi (SDM) bildirmek ve ayıklanan uygulamayı durumunu değiştirme IDE. Bu olaylar SDM ve IDE zamanınızda işlenir. Olayı işlendikten sonra yanıt hata ayıklama Altyapısı'na (DE) gönderilir. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) ve [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) arabirimleri, zaman uyumsuz olay örnekleri verilmiştir.  
  
- Zaman uyumlu olayları  
  
   SDM ve ayıklanan uygulamayı durumunu değiştirme IDE bildirin. Bu olaylar ve zaman uyumsuz olaylar arasındaki tek fark yanıt yoluyla gönderileceğini olan [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) yöntemi.  
  
   Zaman uyumlu bir olayı gönderirken, IDE alır ve olayı işleyen sonra işleme devam etmek için DE gerektiğinde kullanışlıdır.  
  
- Zaman uyumlu olayları durdurma veya olayları durduruluyor  
  
   Bildirim SDM ve IDE ayıklanan uygulamayı kod yürütme durduruldu. Durdurma olay yöntemiyle gönderdiğinizde [olay](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametresi gereklidir. Aşağıdaki yöntemlerden birini yapılan bir çağrıyla durdurma olayları ettirilen:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Arabirimler [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) durdurma olayları örnekleridir.  
  
  > [!NOTE]
  >  Zaman uyumsuz durdurma olayları desteklenmez. Bu zaman uyumsuz durdurma olay göndermek için bir hatadır.  
  
## <a name="discussion"></a>Tartışma  
 Olayların kullanımınız, sizin DE tasarımına bağlıdır. Gönderilen her olay türünü DE tasarlarken hangi ayarlanan kendi özniteliklere göre belirlenir. Örneğin, bir DE gönderebiliriz bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olarak zaman uyumsuz olay sırasında başka bir durdurma olay olarak gönderebilir.  
  
 Aşağıdaki tabloda, hangi olayları, ek olarak olay türleri hangi program ve iş parçacığı parametreler gereklidir belirtir. Herhangi bir olay, zaman uyumlu olabilir. Hiçbir olay, zaman uyumlu olması gerekiyor.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) arabirimi tüm olaylar için gereklidir.  
  
|Olay|IDebugProgram2|IDebugThread2|Olayları durduruluyor|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Gerekli|Gerekli|Hayır|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|İzin verilmiyor|İzin verilmiyor|Hayır|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|İzin verilmiyor|İzin verilmiyor|Hayır|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Olabilir|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Olabilir|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Olabilir|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Gerekli|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Gerekli|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Gerekli|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Gerekli|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Gerekli|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|IDebugStopCompleteEvent2|Gerekli|Gerekli|Evet|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Gerekli|Gerekli|Evet|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Gerekli|Gerekli|Hayır|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Gerekli|Gerekli|Hayır|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|İzin verilen, ancak gerekli değil|İzin verilen, ancak gerekli değil|Hayır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları Gönderme](../../extensibility/debugger/sending-events.md)

