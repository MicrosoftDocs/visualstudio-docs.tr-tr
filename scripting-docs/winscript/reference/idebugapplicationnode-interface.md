---
title: Idebugapplicationnode arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793955"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode Arabirimi
`IDebugApplicationNode` Arabirimi işlevselliğini genişleten `IDebugDocumentProvider` proje ağacı bağlamında sağlayarak arabirimi.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IDebugDocumentProvider`, `IDebugApplicationNode` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Bu uygulama düğümün alt öğelerinin numaralandırır.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Bu uygulama düğümün üst düğümü döndürür.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Bu uygulama düğümü için belge sağlayıcıyı ayarlar.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Tüm başvurularını serbest bırakın ve etkin olmayan bir duruma girmek bu uygulamayı neden olur.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Bu uygulama düğümü belirtilen proje ağacına ekler.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Bu uygulama düğümü proje ağacından kaldırır.|