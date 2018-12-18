---
title: Yürütme denetimi | Microsoft Docs
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
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4fe5259d49424fa1d46ea1ef33c0808dfc7b7be
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776375"
---
# <a name="control-of-execution"></a>Yürütme Denetimi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE) genellikle aşağıdaki olaylardan biri son başlatma olayı gönderir:  
  
- Yeni başlatılan programa ekleme, giriş noktası olayı  
  
- Zaten çalışan bir programa ekleme, yük complete olayı  
  
  Hem bu olayları DE kullanıcıdan yanıt IDE yoluyla bekler, yani olan Durma olaylarıdır. Daha fazla bilgi için [çalışma modları](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Olay durduruluyor  
 Durdurma olay hata ayıklama oturumu için gönderildiğinde:  
  
1. Dosyadaki geçerli yönerge işaretçisini içeren iş parçacığı ve program olay arabiriminden elde edilebilir.  
  
2. IDE geçerli kaynak kodu dosyası ve görüntüler düzenleyicide vurgulanır konumunu belirler.  
  
3. Genellikle hata ayıklama oturumu programın çağırarak bu ilk durdurma olaya yanıt **devam** yöntemi.  
  
4. İçinde ve çalışması DE bir kesme noktası olayının hata ayıklama oturumu için gönderir, bir kesme noktasına ulaşma gibi bir durdurma koşul karşılaşana kadar program sonra çalışır. Kesme noktası olayı durdurma bir olaydır ve DE yeniden kullanıcı yanıt bekler.  
  
5. Üzerinde Adımlama kullanıcı seçer veya bir işlevden, IDE program çağırmak için hata ayıklama oturumu ister `Step` (yönergesi, deyim veya satır) bir adım adım türü ve birim geçirerek yöntemini — diğer bir deyişle, üzerinde Adımlama verilip verilmeyeceğini , veya işlev dışında. Bu adım tamamlandıktan sonra DE durdurma olay hata ayıklama oturumu için adım tam bir olay gönderir.  
  
    veya  
  
    Kullanıcı, dosyadaki geçerli yönerge işaretçisini çalıştırmaya devam etmeyi seçerse, IDE program çağırmak için hata ayıklama oturumunun ister **yürütme** yöntemi. Sonraki durdurma koşul karşılaşana kadar program yürütme devam eder.  
  
    veya  
  
    Hata ayıklama oturumunun belirli durdurma olay yok saymak için ise, programın hata ayıklama oturumu çağırır **devam** yöntemi. Ardından durdurma koşul karşılaştığında program içine, üzerine veya bir işlev dışına Adımlama, adımı devam eder.  
  
   Programlı olarak bunu gönderir gibi durdurma olaylar DE durdurma koşul karşılaştığında [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) yoluyla oturum hata ayıklama Yöneticisi (SDM) için bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi. DE geçişleri [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ve [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) program ve dosyadaki geçerli yönerge işaretçisini içeren iş parçacığını temsil eden arabirim. SDM çağrıları [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) üst yığın çerçevesi ve çağrılarını almak için [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) geçerli yönergenin ile ilişkili belge bağlamı almak için İşaretçi. Bu belge genellikle bir kaynak kod dosya adı, satır ve sütun numarası bağlamıdır. IDE bu dosyadaki geçerli yönerge işaretçisini içeren kaynak kodu vurgulamak için kullanır.  
  
   Genellikle SDM çağırarak bu ilk durdurma olaya yanıt [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). İçinde DE çalışması gönderir, bir kesme noktasına ulaşma gibi bir durdurma koşul karşılaşana kadar program sonra çalışan bir [IDebugBreakpointEvent2 arabirimi](../../extensibility/debugger/reference/idebugbreakpointevent2.md) SDM için. Kesme noktası olayı durdurma bir olaydır ve DE yeniden kullanıcı yanıt bekler.  
  
   Kullanıcı, üzerinde Adımlama seçer veya bir işlevden, IDE çağrılacak SDM ister [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), iletmeden [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (yönergesi, deyim veya çizgi) ve [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), diğer bir deyişle, içine, üzerine veya işlev dışında adım verilip verilmeyeceğini. Bu adım tamamlandıktan sonra DE gönderir. bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) durdurma olayı SDM arabirimi.  
  
   Kullanıcı, dosyadaki geçerli yönerge işaretçisini çalıştırmaya devam etmeyi seçerse, IDE çağrılacak SDM ister [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Sonraki durdurma koşul karşılaşana kadar program yürütme devam eder.  
  
   Hata ayıklama paketi belirli durdurma olay yok saymak için ise, hata ayıklama paketi çağırır SDM çağırır [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Ardından durdurma koşul karşılaştığında program içine, üzerine veya bir işlev dışına Adımlama, adımı devam eder. Devam etmek nasıl bilir, böylece programın bir atlama durumu korur gelir.  
  
   SDM yapar için çağrıları `Step`, **yürütme**, ve **devam** SDM hızlı bir şekilde geri dönmek için çağrı bekliyor yani olan zaman uyumsuz. DE SDM durdurma olay önce aynı iş parçacığında gönderirse `Step`, **yürütme**, veya **devam** döndürür SDM yanıt vermemeye başlıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)

