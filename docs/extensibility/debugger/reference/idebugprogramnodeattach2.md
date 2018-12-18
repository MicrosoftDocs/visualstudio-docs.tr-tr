---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120695"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Program düğümün ilişkili programın bağlama girişimi bildirilmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirimi uygulayan aynı sınıfa uygulanan [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi ekleme işlemi bildirim almak için ve ekleme işlemini iptal etmek için bir fırsat sağlamaktır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim çağırarak elde `QueryInterface` yönteminde bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi çağrılır, önce [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) program düğüm ekleme işlemi durdurmak için bir şansı vermek yöntemi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki yöntem bu arabirimi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|İlişkili programı ekler veya ekleme işlemi için erteler [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirimin tercih edilen kullanım dışı alternatifidir [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) yöntemi. Tüm hata ayıklama motorları her zaman ile yüklenen `CoCreateInstance` işlev, ayıklanacak program adres alanı dışında başka bir deyişle, örneği.  
  
 Önceki bir uygulaması, `IDebugProgramNode2::Attach_V7` yöntemi yalnızca ayarı `GUID` , ardından yalnızca ayıklanacak programının [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi uygulanması gerekiyor.  
  
 Önceki bir uygulaması, `IDebugProgramNode2::Attach_V7` sağlanan geri çağırma arabirimi kullanılan yöntem, sonra bu işlevselliği uygulaması için taşınması gerekiyor [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi ve `IDebugProgramNodeAttach2` arabirimi yok uygulanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)