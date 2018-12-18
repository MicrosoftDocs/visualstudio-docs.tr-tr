---
title: DOCUMENTNAMETYPE listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791684"
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE Listelemesi
Bir belge için hangi türün alınacağını açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Uygulama ağacında görünen adını alır.|  
|DOCUMENTNAMETYPE_TITLE|Görüntüleyici başlık çubuğunda görünen adını alır.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Bir yol olmadan dosya adını alır.|  
|DOCUMENTNAMETYPE_URL|Belge URL'sini alır.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Tanımlama için numaralandırma eklenen başlığını alır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)