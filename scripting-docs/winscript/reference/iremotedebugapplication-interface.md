---
title: Iremotedebugapplication arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795035"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication Arabirimi
Çalışan bir uygulama temsil eder. Bir işletim sistemi işlemine karşılık gelecek şekilde gerekmez. Genellikle, bir hata ayıklayıcısı hata ayıklama için bir uygulama hedefler. Hata ayıklama işlem yöneticisi, genellikle uygulama nesnesi uygular.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IRemoteDebugApplication` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|İçinde bir kesme noktası şu anda bir uygulama devam eder.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Uygulamanın hata ayıklayıcı fırsatta içine çalışmamasına neden olur.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Bu uygulama için bir hata ayıklayıcısı bağlanır.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Geçerli hata ayıklayıcı uygulamadan bağlantısını keser.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Geçerli hata ayıklayıcı uygulamaya bağlı döndürür.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Hata ayıklayıcı IDE, çalışan giden işlem dışı uygulama işleminin nesneleri oluşturmak için bu uygulamaya için bir mekanizma sağlar.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Uygulamanın yanıt verebilir durumda olup olmadığını gösterir.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Uygulama ile ilişkili olduğu bilinen tüm iş parçacıklarının numaralandırır.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Bu uygulama düğümün adını döndürür.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Uygulama ile ilişkili tüm düğümleri altında eklendiği uygulama düğümü döndürür.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Bu uygulamayı çalıştıran tüm diller için genel ifade bağlamları numaralandırır.|