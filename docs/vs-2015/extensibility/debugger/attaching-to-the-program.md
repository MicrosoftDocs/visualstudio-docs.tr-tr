---
title: Programa ekleme | Microsoft Docs
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
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c16c13b4dec412fa44be5cbfbbdd8494b805545
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777948"
---
# <a name="attaching-to-the-program"></a>Programa Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Programlarınızın uygun bağlantı noktası ile kaydettikten sonra hata ayıklayıcı, hata ayıklamak istediğiniz program eklemeniz gerekir.  
  
## <a name="choosing-how-to-attach"></a>Nasıl ekleneceği seçme  
 Oturum hata ayıklama Yöneticisi (SDM) hata ayıklaması yapılan programa ekleme çalışır üç yolu vardır.  
  
1. Hata ayıklama altyapısı tarafından başlatılan program için [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) SDM yöntem (örneğin, yorumlanan dil tipik) edinir [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) gelen arabirimi [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) için iliştirilmekte programı ilişkili nesne. SDM elde `IDebugProgramNodeAttach2` SDM arabirimini, çağırır ve ardından [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi. `IDebugProgramNodeAttach2::OnAttach` Yöntemi döndürür `S_OK` programa eklemediniz ve denemeleri programa eklemek için yapılabilir.  
  
2. SDM elde [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) arabirim SDM çağrıları iliştirilmekte programdan [iliştirme](../../extensibility/debugger/reference/idebugprogramex2-attach.md) yöntemi. Bu yaklaşım, uzaktan bağlantı noktası sağlayıcısı tarafından başlatılan programlar tipik bir durumdur.  
  
3. Program aracılığıyla eklenemez, `IDebugProgramNodeAttach2::OnAttach` veya `IDebugProgramEx2::Attach` yöntemleri SDM yükler (henüz yüklü değilse) hata ayıklama altyapısı çağırarak `CoCreateInstance` işlevi ve ardından aramaları [iliştirme](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi. Bu yaklaşım, yerel olarak bağlantı noktası sağlayıcısı tarafından başlatılan programlar tipik bir durumdur.  
  
    Ayrıca çağırmak özel bağlantı noktası sağlayıcısı için olası `IDebugEngine2::Attach` yöntemi özel bir bağlantı noktası tedarikçi uygulamasında `IDebugProgramEx2::Attach` yöntemi. Genellikle bu durumda, özel bağlantı noktası sağlayıcısı uzak makinede hata ayıklama altyapısı başlatır.  
  
   Oturum hata ayıklama Yöneticisi (SDM) çağırdığında eki elde [iliştirme](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi.  
  
   Sizin DE ayıklanacak uygulamayla aynı işlemde çalıştırmak sonra aşağıdaki yöntemleri uygulamalıdır [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Sonra `IDebugEngine2::Attach` yöntemi çağrıldığında, uygulamanızda adımları `IDebugEngine2::Attach` yöntemi:  
  
1.  Gönderme bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM olay nesnesiyle. Daha fazla bilgi için [olayları gönderme](../../extensibility/debugger/sending-events.md).  
  
2.  Çağrı [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodunda [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) geçildi nesne `IDebugEngine2::Attach` yöntemi.  
  
     Bu döndürür bir `GUID` program tanımlamak için kullanılır. `GUID` Temsil yerel için DE program ve bunu ne zaman döndürülmelidir nesnede depolanan `IDebugProgram2::GetProgramId` yöntemi çağrıldığında `IDebugProgram2` arabirimi.  
  
    > [!NOTE]
    >  Uygularsanız `IDebugProgramNodeAttach2` arabirim, programın `GUID` geçirilir `IDebugProgramNodeAttach2::OnAttach` yöntemi. Bu `GUID` programın için kullanılan `GUID` tarafından döndürülen `IDebugProgram2::GetProgramId` yöntemi.  
  
3.  Gönder bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM bildirmek üzere olay nesnesi, yerel `IDebugProgram2` nesne program için DE göstermek için oluşturuldu. Ayrıntılar için bkz [olayları gönderme](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Bu aynı değil `IDebugProgram2` yöntemlere geçirilen nesne `IDebugEngine2::Attach` yöntemi. Daha önce geçirilen `IDebugProgram2` nesne yalnızca bağlantı noktası tarafından kabul edilir ve ayrı bir nesnedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlatma tabanlı ek](../../extensibility/debugger/launch-based-attachment.md)   
 [Olayları gönderme](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Ekleme](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

