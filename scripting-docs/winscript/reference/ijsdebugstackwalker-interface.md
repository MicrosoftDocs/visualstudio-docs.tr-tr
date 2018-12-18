---
title: Ijsdebugstackwalker arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794720"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker Arabirimi
Belirtilen iş parçacığı yığın walker temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[Ijsdebugstackwalker::GetNext yöntemi](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Sonraki Çerçeve alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın walkers, yalnızca hedef durdurulur ve hedef işlemin yeniden devam etti sonra geçersiz sırasında oluşturulabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)