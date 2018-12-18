---
title: IDebugMessageEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116181"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Bu arabirim, kullanıcıdan bir yanıt gerektirir Visual Studio bir ileti göndermek için hata ayıklama altyapısı (DE) tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE Visual Studio için kullanıcı yanıt isteyen bir ileti göndermek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi uygulanan, bu arabirimle aynı nesne üzerinde. SDM kullanan [QueryInterface](/cpp/atl/queryinterface) erişimi `IDebugEvent2` arabirimi.  
  
 Bu arabirim uygulaması Visual Studio'nun çağrısı iletişim kurması gereken [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) DE için. Örneğin, bu iş parçacığı işleme DE'ın iletiye gönderilen bir ileti ile yapılabilir veya bu arabirimi uygulayan nesne DE başvuru tutun ve geri içine geçirilen yanıt için DE arama `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 DE oluşturur ve yanıt gerektirir kullanıcıya bir ileti görüntülemek için bu olay nesnesi gönderir. Olay kullanılarak gönderilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) ayıklanacak programın eklendiğinde, SDM tarafından sağlanan geri çağırma işlevi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugMessageEvent2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Görüntülenecek iletiyi alır.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Yanıt iletisi kutusundan varsa ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir iletiyi kullanıcıdan belirli bir yanıt gerektiriyorsa DE bu arabirimini kullanır. Uzaktan bir programa bağlama girişimi sonra bir "Erişim engellendi" iletisi DE alır, örneğin, DE bu belirli ileti Visual Studio'da gönderir bir `IDebugMessageEvent2` ileti kutusu stili olayla `MB_RETRYCANCEL`. Bu, kullanıcının yeniden deneyin veya attach işlemi iptal olanak sağlar.  
  
 DE nasıl bu iletiyi Win32 işlevi kurallarına tarafından işleneceğini belirtir `MessageBox` (bkz [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) Ayrıntılar için).  
  
 Kullanım [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) kullanıcıdan bir yanıt gerektirmeyen Visual Studio iletileri göndermek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)