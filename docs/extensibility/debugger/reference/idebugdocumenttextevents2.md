---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107676"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Bu arabirim, Visual Studio hata ayıklama altyapısı tarafından sağlanan kaynak belge değişiklikleri bildirmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 DE kaynak kodunu değişiklikleri desteklemek için bu arabirimi uygular. Bu arabirimi uygulayan aynı nesne üzerinde genel uygulanır [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Bu arabirim çağrısıyla edinir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> yöntemi. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Arabirimi çağrısından elde edilir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> yöntemi. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Arabirimi çağırarak elde edilir [QueryInterface](/cpp/atl/queryinterface) yöntemi bir [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugDocumentTextEvents2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Tüm belgeyi yok olduğunu gösterir.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Hata ayıklama paket metin belgesine eklenmiş olduğunu bildirir.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Hata ayıklama paket metin belgeden kaldırıldı bildirir.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Hata ayıklama paket metin belgede değiştirildiğini bildirir.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Hata ayıklama paket metin özniteliklerini belgede güncelleştirildiğini bildirir.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Olay alıcısı belge nitelikleri güncelleştirildi bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kendi belgelerinin tedarik hata ayıklama motorları yararlanmak yalnızca `IDebugDocumentTextEvent2` arabirimi. Buna örnek olarak bir komut dosyası hata ayıklama altyapısı olacaktır. Komut dosyaları yorumlama sürecinde yeni kaynak kodunu herhangi bir disk dosyada mevcut değil ve yalnızca DE bilinen oluşturulabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)