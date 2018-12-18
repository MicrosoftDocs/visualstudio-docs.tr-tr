---
title: SCRIPTSTATE numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796466"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE Numaralandırması
Bir komut dosyası motoru durumunu belirtir. Bu numaralandırma tarafından kullanılan [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , ve [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Numaralandırma değerleri  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Komut dosyası, yeni oluşturduğunuz ancak henüz kullanarak başlatılmamış bir `IPersist*` arabirimi ve [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Komut dosyası başlatıldı, ancak (diğer nesnelere bağlanma veya olayları indirme) çalışmıyor veya herhangi bir kod yürütme. Kod sorgulanan yürütme için çağırarak [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) yöntemi.|  
|SCRIPTSTATE_STARTED|Betik kodu, yürütebilir tarafından eklenen nesneleri olayları henüz indirme değil ancak [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) yöntemi.|  
|SCRIPTSTATE_CONNECTED|Komut dosyası yüklenir ve olayları indirme için bağlı.|  
|SCRIPTSTATE_DISCONNECTED|Komut dosyası yüklenir ve bir çalışma zamanı yürütme durumuna sahip, ancak geçici olarak olayları indirme bağlantısı kesildi.|  
|SCRIPTSTATE_CLOSED|Komut dosyası kapatıldı. Komut dosyası altyapısı artık çalışır ve çoğu yöntemleri için hatalar döndürür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası sabitleri, numaralandırmaları ve hata kodları](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)