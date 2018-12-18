---
title: Scrıptprop_hostkeepalıve özelliği | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796397"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE Özelliği
Komut dosyası altyapısı bekleyen başvurular varsa tam olarak işlevsel tutulmalıdır olup olmadığını belirtmek için kullanılır.  
  
 Kullanım [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) bu özelliği ayarlamak için `true`. Bu özellik ayarlanmışsa `true`, komut dosyası altyapısı veya için en az bir bekleyen başvuru var olduğu sürece komut dosyası altyapısı tam olarak işlevsel tutulur bir `IDispatch` komut dosyası kullanılarak oluşturulan bir JavaScript nesne işaretçisi altyapısı. Bu özellik ayarlandığında `true`, açıkça kapattığınızda veya komut dosyası altyapısını kullanarak sıfırlamak [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) veya [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) yöntemleri. Bir komut dosyası nesnesi son referansı sürümü betik altyapısı kapanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Bu özellik yalnızca ile yüklenen activscp.idl sürümü görünür [!INCLUDE[win8](../../javascript/includes/win8-md.md)], Internet Explorer 8 KB 2707082 ile [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], veya Internet Explorer 9'e yönelik KB 2722913 ile [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] veya [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].