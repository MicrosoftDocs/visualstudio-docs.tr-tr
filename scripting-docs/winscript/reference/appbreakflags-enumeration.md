---
title: APPBREAKFLAGS numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792029"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS Numaralandırması
Uygulamalar ve iş parçacıkları için geçerli hata ayıklama durumunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Dil altyapısı hemen tüm iş parçacıklarında BREAKREASON_DEBUGGER_BLOCK ile çalışmamasına neden.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Dil altyapısı hemen BREAKREASON_DEBUGGER_HALT ile kesme.|  
|APPBREAKFLAG_STEP|0x00010000|Dil altyapısı hemen BREAKREASON_STEP sürüm parçacığıyla bozan.|  
|APPBREAKFLAG_NESTED|0x00020000|Bir kesme noktası üzerindeki iç içe geçmiş yürütmesinde uygulamasıdır.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Hata ayıklayıcı kaynak düzeyinde atlama.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Hata ayıklayıcı bayt kodu düzeyinde atlama.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Hata ayıklayıcı makine düzeyinde atlama.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Adım türleri Finansman maske.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Bir kesme noktası devam ediyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı bayrakları diğer bayraklar hata ayıklayıcı sürüm modu belirtirken dil motorları sonraki fırsatta bölün belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON numaralandırması](../../winscript/reference/breakreason-enumeration.md)