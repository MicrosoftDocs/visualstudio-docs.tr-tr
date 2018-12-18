---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793607"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Çalışma zamanı hataların nasıl işleneceğini belirlemek bir akıllı ana bilgisayar sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 [in] Oluştu çalışma zamanı hatası  
  
 `pfEnterDebugger`  
 [out] JIT hata ayıklama yapmak için hata ayıklayıcı hata geçirmek tutulmayacağını gösteren bayrak.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Çağrılıp çağrılmayacağını belirten bayrak `IActiveScriptSite::OnScriptError` zaman kullanıcı karar hata ayıklama yapmadan devam etmek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler dahil, ancak aşağıdaki tabloda değerine sınırlı değildir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir akıllı ana bilgisayar, çalışma zamanı hataların nasıl işleneceğini belirlemek için bu yöntemi kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsitedebug arabirimi](../../winscript/reference/iactivescriptsitedebug-interface.md)