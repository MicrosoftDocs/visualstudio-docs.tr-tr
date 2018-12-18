---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793286"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Bir kod yordamı ayrıştırır, altyapısı yazma komut dosyası için kod yordam metin ekler ve oluşturur bir `IScriptEntry` kodu yordama karşılık gelen nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [in] Ayrıştırılacak komut metni.  
  
 `pszFormalParams`  
 [in] Yordam için biçimsel parametresi adları adresi. Parametre adları, komut dosyası altyapısı yazma için uygun sınırlayıcılar tarafından ayrılmalıdır. Adlar parantez içine alınmamalıdır.  
  
 `pszProcedureName`  
 [in] Ayrıştırılacak yordam adı adresidir.  
  
 `pszItemName`  
 [in] Öğe adı içeren arabellek adresi ile ilişkili `IScriptEntry` nesnesi.  
  
 `pszDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresi. Zaman `pszCode` ayrıştırılır metin akışından konak genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti), komut dosyası bloğunun sonunu algılamak için kullanır. Komut dosyası bloğunun sonunu işaretlemek için sınırlayıcı ise bu parametre NULL olarak ayarlayın.  
  
 `dwCookie`  
 [in] Yeni ile ilişkilendirilmiş uygulama tanımlı bir değer `IScriptEntry` nesnesi.  
  
 `dwFlags`  
 [in] Kullanılmıyor.  
  
 `pdispFor`  
 [in] Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] altyapısı bu yöntem uygulamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthorprocedure arabirimi](../../winscript/reference/iactivescriptauthorprocedure-interface.md)