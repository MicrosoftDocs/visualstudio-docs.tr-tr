---
title: Iactivescriptsitewindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793664"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Bu arabirim aynı nesne üzerinde bir kullanıcı arabirimi desteği konaklar tarafından uygulanır [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) . Uygulamaz sunucuları gibi bir kullanıcı arabirimi desteklemeyen Konaklar `IActiveScriptSiteWindow` arabirimi. Komut dosyası altyapısı bu arabirimi çağırarak erişen `QueryInterface` gelen `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Komut dosyası altyapısı görüntülemelidir bir açılır pencere sahibi olarak davranıp pencere tanıtıcısını alır.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Etkinleştirmek veya devre dışı kendi ana penceresi yanı sıra tüm kalıcı olmayan iletişim kutuları için ana neden olur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası arabirimleri](../../winscript/reference/active-script-interfaces.md)