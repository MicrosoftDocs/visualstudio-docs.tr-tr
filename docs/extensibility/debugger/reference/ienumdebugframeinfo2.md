---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123924"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Bu arabirim numaralandırır [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapıları.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Hata ayıklama altyapısı (DE) geçerli çağrı yığını açıklayan yapıları listesi sağlamak için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Visual Studio çağrıları [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) bir kesme noktası olduğunda bu arabirimi sağlamak için özel durum ya da durdurmak ayıklanacak bir programda oluşur.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IEnumDebugFrameInfo2`.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Belirtilen sayıda alır [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) numaralandırma dizisi yapılarda.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Belirtilen sayıda atlar [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) numaralandırma dizisi yapılarda.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Bir numaralandırma sırasını başlangıç durumuna sıfırlar.|  
|[kopya](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Geçerli Numaralandırıcı aynı numaralandırma duruma içeren bir numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Sayısını alır [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarını bir numaralandırıcı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio bu arabirimi bir kesme noktası, özel durum ya da kullanıcı tarafından oluşturulan Duraklat ayıklanacak programı'nda işleme için ilk adım olarak alır. Listesini [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapıları temsil eden geçerli çağrı yığını, liste ve eski işlevi başındaki geçerli işlev çağrısı ile listesinin sonuna çağırın. Her `FRAMEINFO` yığın çerçevesi, ifadeler değerlendirilmesi ve yerel değişkenler arama sırasında bir bağlamı temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)