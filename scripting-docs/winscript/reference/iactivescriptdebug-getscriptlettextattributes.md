---
title: IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793391"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Rastgele bir kod parçacığı metin özniteliklerini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 [in] Kod parçacığı metin. Bu dize sonlandırıldı null olması gerekmez.  
  
 `uNumCodeChars`  
 [in] Kod parçacığı metinde karakterlerin sayısı.  
  
 `pstrDelimiter`  
 [in] Resimli son sınırlayıcı adresidir. Zaman `pstrCode` ayrıştırılır gibi iki Resimli sonuna algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgileri bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı kullanır. Konak Resimli sonuna işaretlemek için sınırlayıcı kullanmadıysanız, bu parametre NULL olarak ayarlayın.  
  
 `dwFlags`  
 [in] Kod parçacığı ile ilişkili bayraklar. Bu değerleri bir bileşimi olabilir:  
  
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
  
## <a name="remarks"></a>Açıklamalar  
 Arabirimini uygulayan bir akıllı ana bilgisayar `IDebugDocumentText` arabirimi çağrıları temsilci seçmek için bu yöntemi kullanabilirsiniz `IDebugDocumentText::GetText` yöntemi.  
  
 Kod parçacıklarını ifadeleri olma eğilimindedir ve bir betik bloğu daha farklı bir sözdizimi olabilir çünkü bu çağrıyı sağlanır. Bunlar aynı sözdizimini varsa, bu yöntemin kullanımı uygulanması için aynı `GetScriptTextAttributes` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptdebug arabirimi](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Idebugdocumenttext arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)