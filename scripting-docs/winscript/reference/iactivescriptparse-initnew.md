---
title: IActiveScriptParse::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793406"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Komut dosyası altyapısını başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_FAIL` başlatma sırasında bir hata ortaya çıktıysa.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı kullanılabilmesi için aşağıdaki yöntemlerden birini çağrılmalıdır: `IPersist*::Load`, `IPersist*::InitNew`, veya `IActiveScriptParse::InitNew`. Bu yöntem semantiği özdeş `IPersistStreamInit::InitNew`, bu yöntem kendisine başlatmak için komut dosyası altyapısı söyler. Her ikisi de çağırmak için geçerli olmadığını göz önünde bulundurun `IPersist*::InitNew` veya `IActiveScriptParse::InitNew` ve `IPersist*::Load`, veya çağırmak için geçerli değil `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, veya `IPersist*::Load` birden çok kez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptparse](../../winscript/reference/iactivescriptparse.md)