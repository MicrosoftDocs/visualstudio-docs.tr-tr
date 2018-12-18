---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793658"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Ana bilgisayar işlemi hata ayıklarken Yöneticisi bir komut dosyası çalışma zamanı hatası hakkında bir süre yalnızca komut dosyası hata ayıklayıcısı bulamazsa bildirir.  
  
 Bir hata ayıklayıcısı ana bilgisayarınız uygulamak için işlemelidir [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Bir kullanıcı eylemi bağlı olarak, konak ya da hata ayıklayıcı ekleyebileceğini ve dönün veya OnScriptErrorDebug hata ayıklayıcıda başlangıç dönmek `pfEnterDebugger` parametresi. Ayrıca işlem hata ayıklama Yöneticisi tarafından yorumlanabilen dış hiçbir hata ayıklayıcıları olsa bile çalışma zamanı hata hakkında bildirim almak için bu arabirimi uygulamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 [in] Çalışma zamanı hata oluştu.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Çağrılıp çağrılmayacağını [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) hata ayıklama yapmadan devam etmek kullanıcı karar verirse.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayrıca bir bildirim almak için bu arabirimi uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsitedebugex arabirimi](../../winscript/reference/iactivescriptsitedebugex-interface.md)