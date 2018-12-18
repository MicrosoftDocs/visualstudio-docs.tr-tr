---
title: IEnumDebugThreads2 | Microsoft Docs
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
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b60d62846ce777897784e005457fe6cf2ca272a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754514"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Geçerli hata ayıklama oturumunda çalışan iş parçacıkları bu interfac numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE), bir programdaki iş parçacıklarının listesini temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) programlar bir işlemde çalışan tüm iş parçacıklarının listesini temsil eden bu arabirimi elde edilir. Çağrı [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) bir programda çalışan iş parçacıklarının listesini temsil eden bu arabirimi elde edilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IEnumDebugThreads2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Belirtilen bir numaralandırma sıralı iş parçacıklarının sayısını alır.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Bir numaralandırma sıralı iş parçacıklarında belirtilen sayıda atlar.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Bir numaralandırma sıralı başlangıç durumuna sıfırlar.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Geçerli planla aynı sıralaması durumu içeren bir numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|İş parçacığı sayısını bir numaralandırıcı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio genellikle güncelleştirmek için bu arabirimi alır **iş parçacıkları** çağırmak için ilk iş parçacığında listenin edinmeniz için de penceresi [yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [devam](../../../extensibility/debugger/reference/idebugprocess3-continue.md), ve [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

