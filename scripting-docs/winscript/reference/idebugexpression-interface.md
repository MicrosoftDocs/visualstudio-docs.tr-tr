---
title: Idebugexpression arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794492"
---
# <a name="idebugexpression-interface"></a>IDebugExpression Arabirimi
Zaman uyumsuz olarak değerlendirilen bir ifade temsil eder. Komut dosyası motorları, genellikle bu arabirimi uygular. Hata ayıklayıcı IDE genellikle bir hemen yürütme penceresi etkinleştirin veya Gözcü penceresi için bu arabirimini kullanır.  
  
> [!NOTE]
>  `IDebugExpression` Yalnızca yığın çerçevesinden arabirimi kullanılabilir.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugExpression` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|İfade değerlendirme başlar.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|İfade durdurur.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|İşlemi tam olup olmadığını belirler.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Dize ve işlemin dönüş değeri olarak ifade değerlendirme sonucunu döndürür.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Hata ayıklama özelliği ve işlemin dönüş değeri olarak ifade değerlendirme sonucunu döndürür.|