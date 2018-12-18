---
title: IActiveScriptSite::OnScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793484"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Ana bilgisayara altyapı komut dosyası çalıştırılırken bir yürütme hatası oluştu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pase`  
 [in] Hata nesnesinin adresini [Iactivescripterror](../../winscript/reference/iactivescripterror.md) arabirimi. Bir konak, yürütme hatası hakkında bilgi edinmek için bu arabirimi kullanabilirsiniz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` hata doğru işlendiğini ya da bir OLE tanımlanan hata kodu Aksi takdirde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)