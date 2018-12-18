---
title: JsDebugReadMemoryFlags listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796268"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags Listelemesi
Bellek okunduğu sıradaki davranışı belirten bayraklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="values"></a>Değerler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Arayan bellek parçası başarılı okuma yalnızca başarılı olması için okuma işlemi istediği gösterilir. Bu ayarlanırsa 'Adresi' geçersizse E_JsDEBUG_INVALID_MEMORY_ADDRESS hata yalnızca gerçekleştirilecektir. Bu bayrak boş olduğunda, istenen bellek herhangi bir kısmının okunamaz olduysa E_JsDEBUG_INVALID_MEMORY_ADDRESS hata gerçekleştirilecektir.|  
|`None`|Arayan ReadMemory için varsayılan davranış istediği gösterilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)