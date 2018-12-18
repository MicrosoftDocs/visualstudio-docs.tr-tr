---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
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
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cec22985451386b88662818a15f60a90e93e6ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780613"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

KULLANIM DIŞI. KULLANMAYIN.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMDMProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) eklemek için program temsil eden arabirim.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM için hata ayıklama olayları göndermek için kullanılan arabirim.  
  
 `dwReason`  
 [in] Bir değer [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) ekleme nedenini belirten sabit listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir uygulama her zaman döndürmelidir `E_NOTIMPL`.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!WARNING]
>  Sürümünden itibaren [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], bu yöntem artık kullanılmamaktadır ve her zaman döndürmelidir `E_NOTIMPL`. Bkz: [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) program düğümü, iliştirilemez için göstermek gerekiyorsa veya program düğümü yalnızca program ayarlıyorsanız alternatif bir yaklaşım için arabirim `GUID`. Aksi takdirde uygulama [iliştirme](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi.  
  
## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005'ten önce  
 Bu yöntem yalnızca DE ayıklanan programa Adres alanında çalıştırıyorsa uygulanması gerekiyor. Aksi takdirde, bu yöntem döndürmelidir `S_FALSE`.  
  
 Bu yöntem çağrıldığında DE göndermelisiniz [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesne, zaten bu örneği için gönderilmedi, [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimi yanı sıra [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ve [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesneleri. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi, ardından gönderilen `dwReason` parametresi `ATTACH_REASON_LAUNCH`.  
  
 DE çağırmalı [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodunda [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) tarafından sağlanan nesne [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesne ve bu programın GUID depolamanız gerekir Örnek verileri `IDebugProgram2` DE tarafından uygulanan bir nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)

