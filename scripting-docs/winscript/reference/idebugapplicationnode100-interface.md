---
title: Idebugapplicationnode100 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793898"
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 Arabirimi
`IDebugApplicationNode100` Arabirimi işlevselliğini genişleten [Idebugapplicationnode arabirimi](../../winscript/reference/idebugapplicationnode-interface.md). Bu arabirim örneği uygulaması üzerinde QueryInterface çağırarak alabilirsiniz [Idebugapplicationnode arabirimi](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Bu arabirim PDM v10.0 ve büyük uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 `IDebugApplicationNode100` Arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Belirtilen filtre tarafından gizlenen metin belgeleri alır.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Belirtilen belge bu düğümün alt öğelerinin birine ait olup olmadığını belirler.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Belirli bir filtre ayarlar [Idebugapplicationnodeevents arabirimi](../../winscript/reference/idebugapplicationnodeevents-interface.md) uygulaması. Böylece PDM artık düğümlerin oluşturulduğunda veya kaldırılan olayları gönderecek alt derleyici tarafından üretilen uygulama düğümleri filtrelemek komut dosyası hata ayıklayıcıları sağlar. Varsayılan olarak, tüm düğümlere gönderilir.|