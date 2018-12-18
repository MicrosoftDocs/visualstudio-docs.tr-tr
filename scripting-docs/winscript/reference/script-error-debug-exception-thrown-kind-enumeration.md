---
title: Scrıpt_error_debug_exceptıon_thrown_kınd listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796400"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND Listelemesi
Oluşan özel durumun türünü gösterir. Bu numaralandırma tarafından kullanılan [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) yöntemi.  
  
> [!IMPORTANT]
>  Bu sabitler PDM sürüm 11.0 ve daha sonraki sürümleri tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Özel durum bir ilk şans özel durumudur.|  
|ETK_USER_UNHANDLED|0x00000001|Özel durum kullanıcı kodunda işlenmez.|  
|ETK_UNHANDLED|0x00000002|Özel durum kodda işlenmez.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescripterrordebug110 arabirimi](../../winscript/reference/iactivescripterrordebug110-interface.md)