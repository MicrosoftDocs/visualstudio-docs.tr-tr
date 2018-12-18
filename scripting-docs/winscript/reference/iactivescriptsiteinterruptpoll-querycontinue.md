---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793679"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Bir komut dosyası sonlanmalıdır belirtmek bir konak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Çağrı başarılı oldu ve ana bilgisayar betik çalıştırmaya devam etmesine izin verir.|  
|`S_FALSE`|Başarılı arama ve betiği konak istekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Barındırılan betik sürece sonlanmalıdır dönüş değerini `QueryContinue` yöntemi `S_OK`. Dönüş değeri `S_FALSE` betik sonlandırmak konak açıkça istekleri gösterir.  
  
 Birden çok iş parçacıklı bir ana bilgisayar kullanabilir `IActiveScript::InterruptScriptThread` bir betiği sonlanmaya yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsiteınterruptpoll arabirimi](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)