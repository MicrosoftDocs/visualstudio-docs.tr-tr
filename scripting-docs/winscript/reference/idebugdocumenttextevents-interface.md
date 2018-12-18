---
title: Idebugdocumenttextevents arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794555"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents Arabirimi
İlişkili metin belgesi değişiklikleri belirten olaylar sağlar.  
  
> [!NOTE]
>  Bu olaylar yangın arabirim zaman belge metni değiştirir. Olay işleyicileri almak kullanarak yeni metin `IDebugDocumentText` arabirimi.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugDocumentTextEvents` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Temel alınan belge yok edildi ve artık geçerli değil gösterir|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Yeni metin belgesine eklenmiş olduğunu gösterir|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Metin belgeden kaldırıldı gösterir.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Metin değiştirildiğini gösterir.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Temel alınan karakteri konumu aralığı ile ilişkili metin özniteliklerini değiştiğini gösterir.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Belge nitelikleri değiştiğini gösterir.|