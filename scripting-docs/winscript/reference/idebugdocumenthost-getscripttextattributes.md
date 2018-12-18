---
title: IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517b228bb46594d19ba6d2fdf41a68e22ac03c75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794714"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Bir belge metin bloğunu metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 [in] Betik bloğu metin. Bu dize sonlandırıldı null olması gerekmez.  
  
 `uNumCodeChars`  
 [in] Betik bloğu metinde karakterlerin sayısı.  
  
 `pstrDelimiter`  
 [in] Son olarak betik bloğu ayırıcısı adresidir. Zaman `pstrCode` ayrıştırılır gibi iki komut dosyası bloğunun sonunu algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgileri bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı kullanır. Ana komut dosyası bloğunun sonunu işaretlemek üzere bir sınırlayıcı kullanmadıysanız, bu parametre NULL olarak ayarlayın.  
  
 `dwFlags`  
 [in] Betik bloğu ile ilişkili bayraklar. Bu değerleri bir bileşimi olabilir:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|Tanımlayıcılar ve nokta işleçleri, SOURCETEXT_ATTR_IDENTIFIER ve SOURCETEXT_ATTR_MEMBERLOOKUP bayraklarıyla'nin sırasıyla tanımlanan gösterir.|  
|GETATTRFLAG_THIS|0x0100|Geçerli nesne tanımlayıcısı SOURCETEXT_ATTR_THIS bayrağıyla tanımlanması gerektiğini gösterir.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Dize içeriği ve açıklama metni SOURCETEXT_ATTR_HUMANTEXT bayrağıyla tanımlanması gerektiğini gösterir.|  
  
 `pattr`  
 [içinde out] Döndürülen öznitelikleri içeren arabelleği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Ana bilgisayar yalnızca varsayılan özniteliklerini kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, rasgele bir belge metin bloğunda metin özniteliklerini döndürür. Döndürülecek ana bilgisayarlar için kabul edilebilir `E_NOTIMPL`, bu durumda varsayılan öznitelikler kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenthost arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)