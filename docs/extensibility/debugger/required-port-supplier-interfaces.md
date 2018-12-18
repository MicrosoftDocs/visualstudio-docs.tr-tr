---
title: Bağlantı noktası sağlayıcısı arabirimleri gerekli | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c727cb39b480d72a3e0aa2083ca795bb65ac0ff
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252420"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli bağlantı noktası sağlayıcısı arabirimleri
Bağlantı noktası sağlayıcısı uygulamalıdır [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Bağlantı noktası sağlayıcısı bağlantı noktası sağlar ve bunları uygular. Bu nedenle, aşağıdaki arabirimlerinden çalıştırmanız gerekir:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Bağlantı noktası açıklar ve bağlantı noktası üzerinde çalışan tüm işlemler numaralandırır.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Başlatma ve bağlantı noktası işlemleri sonlandırma için sağlar.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Bu program düğüm oluşturma ve yok etme bildirmek için bu bağlantı noktasının bağlamı içinde çalışan programlar için bir mekanizma sağlar. Daha fazla bilgi için [programda düğümler](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Bir bağlantı noktası sağlar [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Bağlantı noktası tedarikçi işlemi  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) havuz, işlem bildirimleri alır ve programlar oluşturulur ve bir bağlantı noktası yok. Bir bağlantı noktası göndermek için gereken [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) işlem oluşturulduğunda ve [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) ne zaman bir işlem yok edildiğinde bağlantı noktası üzerinde. Bir bağlantı noktası da göndermek için gereken [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) bir program oluşturulduğunda ve [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) ne zaman bir program yok edildiğinde bağlantı noktası üzerinde çalışan bir işlemin içinde.  
  
 Bir bağlantı noktası genellikle gönderir program oluşturma ve olayları yanıt olarak yok et [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemleri, sırasıyla.  
  
 Bir bağlantı noktası başlatın ve fiziksel işlemleri hem mantıksal programları sonlandırmak için aşağıdaki arabirimlerinden hata ayıklama altyapısı tarafından da uygulanması gerekir:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Fiziksel işlemi açıklanmaktadır. En az aşağıdaki yöntemlerden uygulanması gerekir:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [Getprocessıd](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     SDM eklemek ve kendisini bir işlemden ayırmak bir yol sağlar.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Mantıksal program açıklar. En az aşağıdaki yöntemlerden uygulanması gerekir:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     SDM bu programa eklemek bir yol sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bir bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)