---
title: IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793250"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Bir betik bloğu metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCode`  
 [içinde size_is (`cch`)] komut dosyası bloğunun metin. Bu dize sonlandırıldı null olması gerekmez.  
  
 `cch`  
 [in] Kullanılan boyut `pszCode` ve `pattr` parametreleri.  
  
 `pszDelimiter`  
 [in] Komut son sınırlayıcısı adresi. Zaman `pszCode` ayrıştırılır metin akışından konak genellikle bir sınırlayıcı (örneğin, iki tek tırnak işareti) Resimli sonuna algılamak için kullanır. Komut dosyası bloğunun sonunu tanımlamak için sınırlayıcı ise bu parametre NULL olarak ayarlayın.  
  
 `dwFlags`  
 [in] Betik bloğu metin özniteliklerle ilişkili bayraklar. Aşağıdaki değerlerden bir bileşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|SOURCETEXT_ATTR_IDENTIFIER özniteliğine sahip tanımlayıcıları tanımlamak ve SOURCETEXT_ATTR_MEMBERLOOKUP özniteliğine sahip nokta işleçleri tanımlayın.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS özniteliğine sahip geçerli nesne tanımlayın.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT özniteliğine sahip dizesi içerik ve açıklama metni tanımlayın.|  
  
 `pattr`  
 [out içinde size_is (`cch`)] betik bloğu kodu için renk bilgileri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)