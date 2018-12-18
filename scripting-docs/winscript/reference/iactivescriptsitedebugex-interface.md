---
title: Iactivescriptsitedebugex arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793628"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx Arabirimi
İle birlikte bu arabirimi uygulayan `IActiveScriptSiteDebug` bir uygulamada bir çalıştırma hatası gösteren bir bildirim almak ve hata ayıklama için uygulamayı isteğe bağlı olarak eklemek için gereken bir ana bilgisayar yazıyorsanız arabirim. Hata ayıklama işlemi Yöneticisi üzerinden bildirim sağlar `IActiveScriptDebug` Just-ın-Time hata ayıklayıcı komut dosyası, bilgisayarda bulunamadı. Hiçbir sadece zamanında hata ayıklayıcı komut dosyası ise, bulunan PDM sağlar üzerinden bildirim `IActiveScriptDebugEx` yerine.  
  
 Bir çalıştırma hatası gösteren bir bildirim almak için ana bilgisayarınız işlemelidir [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). Bir kullanıcı eylemi bağlı olarak, daha sonra iç hata ayıklayıcı ve return ekleme ya da OnScriptErrorDebug hata ayıklayıcıda başlayarak döndürülecek karar verebilir `pfEnterDebugger` parametresi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Ana bilgisayar işlemi hata ayıklarken Yöneticisi bir komut dosyası çalışma zamanı hatası hakkında bir dış süre yalnızca hata ayıklayıcı bulamazsa bildirir.|