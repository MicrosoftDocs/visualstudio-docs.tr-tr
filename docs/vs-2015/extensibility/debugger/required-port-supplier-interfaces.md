---
title: Bağlantı noktası sağlayıcısı arabirimleri gerekli | Microsoft Docs
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
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 485c295e7258f09aaf4114d5945f8136057447e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782810"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli Bağlantı Noktası Sağlayıcısı Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bağlantı noktası sağlayıcısı uygulamalıdır [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Bağlantı noktası sağlayıcısı bağlantı noktası sağlayan olduğundan, ayrıca bunları uygulamalıdır. Bu nedenle, aşağıdaki arabirimlerinden uygulamanız gerekir:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Bağlantı noktası açıklar ve bağlantı noktası üzerinde çalışan tüm işlemler sıralayabilirsiniz.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Başlatma ve bağlantı noktası işlemleri sonlandırma için sağlar.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Bu program düğüm oluşturma ve yok etme bildirmek için bu bağlantı noktasının bağlamı içinde çalışan programlar için bir mekanizma sağlar. Daha fazla bilgi için [Program düğümleri](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Bir bağlantı noktası sağlar [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Bağlantı noktası tedarikçi işlemi  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) havuz, işlem bildirimleri alır ve programlar oluşturulur ve bir bağlantı noktası yok. Bir bağlantı noktası göndermek için gereken [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) işlem oluşturulduğunda ve [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) ne zaman bir işlem yok edildiğinde bağlantı noktası üzerinde. Bir bağlantı noktası da göndermek için gereken [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) bir program oluşturulduğunda ve [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) ne zaman bir program yok edildiğinde bağlantı noktası üzerinde çalışan bir işlemin içinde.  
  
 Bir bağlantı noktası genellikle gönderir program oluşturma ve olayları yanıt olarak yok et [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemleri, sırasıyla.  
  
 Bir bağlantı noktası başlatın ve fiziksel işlemleri hem mantıksal programları sonlandırmak için bu arabirimler hata ayıklama altyapısı tarafından da uygulanması gerekir:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Fiziksel işlemi açıklanmaktadır. En az aşağıdaki yöntemlerden uygulanması gerekir:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Noktası Sağlayıcısı Uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)

