---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793301"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Bir kod parçacığı metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [içinde size_is (`cch`)] Resimli metin. Bu dize sonlandırıldı null olması gerekmez.  
  
 `cch`  
 [in] Kullanılan boyut `pszCode` ve `pattr` parametreleri.  
  
 `pszDelimiter`  
 [in] Resimli son sınırlayıcı adresi. Zaman `pszCode` ayrıştırılır metin akışından konak genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) Resimli sonuna algılamak için kullanır. Sınırlayıcı Resimli sonuna tanımlamak için kullanılır, bu parametre NULL olarak ayarlayın.  
  
 `dwFlags`  
 [in] Kod parçacığı metin özniteliklerle ilişkili bayraklar. Aşağıdaki değerlerden bir bileşimi olabilir.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|SOURCETEXT_ATTR_IDENTIFIER özniteliğine sahip tanımlayıcıları tanımlamak ve SOURCETEXT_ATTR_MEMBERLOOKUP özniteliğine sahip nokta işleçleri tanımlayın.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS özniteliğine sahip geçerli nesne tanımlayın.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT özniteliğine sahip dizesi içerik ve açıklama metni tanımlayın.|  
  
 `pattr`  
 [out içinde size_is (`cch`)] Resimli kodu için renk bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)