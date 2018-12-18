---
title: Hata ayıklayıcıyı başlatma | Microsoft Docs
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
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bcb73a46f6055d1c8637fe1d5375ba9be0fc8652
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774880"
---
# <a name="launching-the-debugger"></a>Hata Ayıklayıcıyı Başlatma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcıyı başlatma, yöntemlerini ve olaylarını uygun öznitelikleriyle birlikte doğru sırasını gönderilmesi gerekir.  
  
## <a name="sequences-of-methods-and-events"></a>Dizileri yöntemler ve olaylar  
  
1.  Oturum hata ayıklama Yöneticisi (SDM) seçerek çağrılır **hata ayıklama** menüsüne ve ardından **Başlat**. Bkz: [Program başlatma](../../extensibility/debugger/launching-a-program.md) daha fazla bilgi için.  
  
2.  SDM çağrıları [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi.  
  
3.  Hata ayıklama altyapısı (DE) işlem modelini temel alan `IDebugProgramNodeAttach2::OnAttach` yöntemi ne olacağını belirler aşağıdaki yöntemlerden birini döndürür.  
  
     Varsa `S_FALSE` döndürülür, hata ayıklama altyapısı (DE) sanal makine aşamasındayız yüklenecek.  
  
     veya  
  
     Varsa `S_OK` döndürülür, DE yüklenecek işlemdeki SDM biri. SDM sonra aşağıdaki görevleri gerçekleştirir:  
  
    1.  Çağrıları [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) altyapısı DE almak için.  
  
    2.  Birlikte DE oluşturur.  
  
    3.  Çağrıları [ekleme](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  DE gönderen bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) ile SDM için bir `EVENT_SYNC` özniteliği.  
  
5.  DE gönderen bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ile SDM için bir `EVENT_SYNC` özniteliği.  
  
6.  DE gönderen bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) ile SDM için bir `EVENT_SYNC` özniteliği.  
  
7.  DE gönderen bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ile SDM için bir `EVENT_SYNC` özniteliği.  
  
8.  DE gönderen bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) ile SDM için bir `EVENT_SYNC` özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)   
 [Program Başlatma](../../extensibility/debugger/launching-a-program.md)

