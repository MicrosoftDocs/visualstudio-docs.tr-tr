---
title: IDebugPortNotify2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1874b46e702af49bf8f0a738b9e764f2fa11014
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115183"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Bu arabirim kaydeder veya üzerinde çalıştırıldığı bağlantı noktası ile hata ayıklaması yapılabilir bir program kaydını siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Özel bir bağlantı noktası tedarikçi ekleme ve kaldırma bağlantı noktasından desteklemek için bu arabirimi uygular. Genellikle uygulayan aynı nesne üzerinde uygulanan [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Çağrı [QueryInterface](/cpp/atl/queryinterface) üzerinde `IDebugPort2` arabirimi bu arabirimi döndürür. Ayrıca, bir çağrı [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) bu arabirimini döndürür. Hata ayıklama altyapısı parametre olarak bu arabirim görebilirsiniz [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugPortNotify2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Hata ayıklaması yapılabilir bir programın üzerinde çalıştırıldığı bağlantı noktası ile kaydeder.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Üzerinde çalıştırıldığı bağlantı noktasından hata ayıklaması yapılabilir bir program kaydını siler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama bağlantı noktası programları ne zaman yüklendi veya kaldırıldığında bilmenin bir yolu olmadığı sürece, özel bir bağlantı noktası tedarikçi bu arabirimi uygulamalıdır. Belirli bir bağlantı noktası üzerinden hata ayıklama için yüklenen tüm programlar bu arabirimi kullanarak izlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)