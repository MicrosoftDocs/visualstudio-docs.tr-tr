---
title: Isimpleconnectionpoint arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796328"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint Arabirimi
Açıklayan ve belirli bağlantı noktasında tetiklenen olayları numaralandırma için basit bir yol sağlar. Bu arabirim de takma kolaylaştırır bir `IDispatch` olaylar nesne. Bu arabirim, işlem hata ayıklama Yöneticisi (PDM) tarafından uygulanan ve komut dosyası motorları tarafından tüketilen.  
  
 Bu arabirim kullanılabilir `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `ISimpleConnectionPoint` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Basit bağlantı noktası nesnesi ve istemcinin havuz arasında bir bağlantı kurar.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Her olay için ad ve DISPID olayların belirtilen aralıkta döndürür.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Bu arabirimde kullanıma sunulan olayların sayısını döndürür.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Üzerinden daha önce oluşturulmuş bir danışma bağlantıyı sonlandırır `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)