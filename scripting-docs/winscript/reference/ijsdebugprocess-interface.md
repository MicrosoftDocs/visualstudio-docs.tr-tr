---
title: Ijsdebugprocess arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794726"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess Arabirimi
İnceleme ve hedef işlem denetleme için yordamlar sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[Ijsdebugprocess::createbreakpoint yöntemi](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Kesme noktası belirtilen belge konumuna ayarlar.|  
|[Ijsdebugprocess::createstackwalker yöntemi](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Yığın walker için Üreteç yöntemi.|  
|[Ijsdebugprocess::performasyncbreak yöntemi](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Sonraki komut dosyası yönerge ayırmak için bunu neden kesme modunda betik altyapısı koyar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)