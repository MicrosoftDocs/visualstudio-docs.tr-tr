---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793331"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Komut dosyası altyapısını başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_FAIL` başlatma sırasında bir hata ortaya çıktıysa.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı kullanılabilmesi için aşağıdaki yöntemlerden birini çağrılmalıdır: `IPersist*::Load`, `IPersist*::InitNew`, veya `IActiveScriptParse32::InitNew`. Bu yöntem semantiği özdeş `IPersistStreamInit::InitNew`, bu yöntem kendisine başlatmak için komut dosyası altyapısı söyler. Her ikisi de çağırmak için geçerli olmadığını göz önünde bulundurun `IPersist*::InitNew` veya `IActiveScriptParse32::InitNew` ve `IPersist*::Load`, veya çağırmak için geçerli değil `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, veya `IPersist*::Load` birden çok kez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)