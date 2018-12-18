---
title: Idebugproperty arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794273"
---
# <a name="idebugproperty-interface"></a>IDebugProperty Arabirimi
Adı, türü ve değeri içeren hiyerarşik özelliğini ayıklanacak varlık açıklamak için kullanılır. En yaygın olarak, `IDebugProperty` ifade değerlendirme, deyimi değerlendirme veya kayıt değerlendirme sonucu açıklamak için kullanılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki tabloda yöntemlerini gösterilmektedir `IDebugProperty` arabirimi.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Alma `DebugPropertyInfo` bu açıklar`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Bir özelliğe genişletilmiş bilgilerini alır.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Bir dizeden bir özelliğin değerini ayarlar.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Bir özellik üyeleri numaralandırır.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Bir özelliğin üst alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: dbgprop.h