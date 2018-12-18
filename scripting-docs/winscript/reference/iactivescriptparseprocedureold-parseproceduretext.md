---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793610"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Verilen kodu yordamı ayrıştırır ve ad alanı için anonim bir yordam ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 [in] Değerlendirilecek yordamı metin. Bu dize yorumu komut dosyası dile bağlıdır.  
  
 `pstrFormalParams`  
 [in] Yordam için biçimsel parametresi adları. Parametre adları, komut dosyası altyapısı için uygun sınırlayıcılar ile ayrılmalıdır. Adlar parantez içine alınmamalıdır.  
  
 `pstrItemName`  
 [in] Değerlendirilecek yordamı olduğu bağlamı sağlar adlandırılmış öğesinin adı. Bu parametre ise `NULL`, kod komut dosyası altyapısının genel bağlamda değerlendirilir.  
  
 `punkContext`  
 [in] Bağlam nesnesi. Bu nesne, bu tür bir bağlam etkin bir çalışma zamanı bağlamı temsil etmek için hata ayıklayıcı tarafından sağlanabilir burada bir hata ayıklama ortamında kullanım için ayrılmıştır. Bu parametre ise `NULL`, altyapısını kullanan `pstrItemName` bağlamı belirlemek için.  
  
 `pstrDelimiter`  
 [in] Yordam son sınırlayıcısı. Zaman `pstrCode` ayrıştırılır gibi iki yordamı sonuna algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, bir ayırıcısı olarak kullanmak için iki tek tırnak işareti tek tırnak işareti ['] yerine) ilkel ön işleme. Tam olarak nasıl (ve ise) bu bilgileri bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı kullanır. Bu parametre kümesine `NULL` konak yordamı sonuna işaretlemek için sınırlayıcı kullanmadıysanız.  
  
 `dwSourceContextCookie`  
 [in] Hata ayıklama amacıyla kullanılan uygulama tanımlı bir değer.  
  
 `ulStartingLineNumber`  
 [in] Hangi satırında ayrıştırma başlayacak belirten sıfır tabanlı değeri.  
  
 `dwFlags`  
 [in] Yordam ile ilişkili bayraklar. Bu değerleri bir bileşimi olabilir.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Belirten kodda `pstrCode` yordamı dönüş değerini temsil eden bir ifade değil.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Belirten `this` işaretçi yordamı kapsamında yer almaktadır.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Belirten üst öğelerini `this` işaretçi yordamı kapsamında dahil edilir.|  
  
 `ppdisp`  
 [out] Gönderme sarmalayıcı varsayılan yöntemi bu yöntem tarafından ayrıştırılan yordamı olduğu döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Komut dosyası altyapısı çalışma zamanı yordamları ad alanı için eklenmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda).|  
|`OLESCRIPT_E_SYNTAX`|Yordamda belirtilmeyen sözdizimi hatası oluştu.|  
|`S_FALSE`|Komut dosyası altyapısı, dağıtım nesnesi desteklemiyor; `ppdisp`parametrenin ayarlanmış `NULL`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Betik kodu, bu çağrı sırasında değerlendirilir; Bunun yerine, yordam bir yönteme üzerinde derlenmiş `ppdisp` burada da çağrılabilir komut dosyası tarafından daha sonra.  
  
 Şunun için bu arabirimi kullanım `IActiveScriptParseProcedure` arabirimi. `IActiveScriptParseProcedure::ParseProcedureText` Yöntemi bu yönteme benzer, ancak yordam adı belirtilmesine izin verir. Tüm durumlarda, `IActiveScriptParseProcedure::ParseProcedureText` kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptparseprocedureold arabirimi](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)