---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793247"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Betik metin ayrıştırır, altyapısı yazma komut metni ekler ve oluşturur bir `IScriptEntry` betik bloğu karşılık gelen nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [in] Ayrıştırılacak komut metni.  
  
 `pszItemName`  
 [in] Betik bloğu ile ilişkili öğe adı içeren arabellek adresi.  
  
 `pszDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresi. Zaman `pszCode` ayrıştırılır metin akışından konak genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti), komut dosyası bloğunun sonunu algılamak için kullanır. Komut dosyası bloğunun sonunu tanımlamak için sınırlayıcı ise bu parametre NULL olarak ayarlayın.  
  
 `dwCookie`  
 [in] Yeni ile ilişkilendirilmiş uygulama tanımlı bir değer `IScriptEntry` nesnesi.  
  
 `dwFlags`  
 [in] Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)