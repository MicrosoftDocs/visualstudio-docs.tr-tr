---
title: IDebugDocumentTextEvents2 | Microsoft Docs
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
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d7fb3c64c1cdbd0e52753b6cd7ec4da197d22f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797292"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, Visual Studio hata ayıklama altyapısı tarafından sağlanan kaynak belgedeki değişiklikler bildirmek için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bu arabirim, kaynak kodu değişiklikleri desteklemek için DE uygular. Bu arabirimi uygulayan aynı nesne üzerinde uygulanan genellikle [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Bu arabirim yapılan bir çağrıyla alır <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> yöntemi. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Arabirimi elde çağrısından <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> yöntemi. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Arabirimi çağırarak elde [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) metodunda bir [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugDocumentTextEvents2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Tüm belgeyi yok edildi gösterir.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Hata ayıklama paketi metin belgeye eklenmiş bildirir.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Hata ayıklama paketi metin belgesinden kaldırıldığını size bildirir.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Hata ayıklama paketi metin belgesinde değiştirilmiştir bildirir.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Hata ayıklama paketi metin özniteliklerini belgede güncelleştirildiğini bildirir.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Olay alıcısı belge öznitelikleri güncelleştirildiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca kendi belgeleri tedarik hata ayıklama motorlarını avantajlarından götürecek `IDebugDocumentTextEvent2` arabirimi. Buna örnek olarak bir komut dosyası hata ayıklama altyapısı olacaktır. Betik yorumlama sürecinde, yeni kaynak kodu herhangi bir disk dosyasında mevcut değil ve yalnızca DE olarak bilinen oluşturulabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

