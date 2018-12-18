---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793583"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Etkinleştirmek veya devre dışı kendi ana penceresi yanı sıra tüm kalıcı olmayan iletişim kutuları için ana neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fEnable`  
 [in] Varsa, bayrak `TRUE`, ana pencereyi ve kalıcı olmayan iletişim kutuları sağlar veya `FALSE`, bunları devre dışı bırakır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_FAIL` durumunda bir hata oluştu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem aynıdır `IOleInPlaceFrame::EnableModeless` yöntemi.  
  
 Bu yönteme çağrıları iç içe.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsitewindow](../../winscript/reference/iactivescriptsitewindow.md)