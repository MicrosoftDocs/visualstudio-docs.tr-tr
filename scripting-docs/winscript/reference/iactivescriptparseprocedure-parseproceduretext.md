---
title: IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793535"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Verilen kodu yordamı ayrıştırır ve ad alanı yordamı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 [in] Değerlendirilecek yordamı metin adresidir. Bu dize yorumu komut dosyası dile bağlıdır.  
  
 `pstrFormalParams`  
 [in] Yordam için biçimsel parametresi adları adresidir. Parametre adları, komut dosyası altyapısı için uygun sınırlayıcılar ile ayrılmalıdır. Adlar parantez içine alınmamalıdır.  
  
 `pstrProcedureName`  
 [in] Ayrıştırılacak yordam adı adresidir.  
  
 `pstrItemName`  
 [in] Değerlendirilecek yordamı olduğu bağlamı sağlar öğe adı adresidir. Bu parametre ise `NULL`, kod komut dosyası altyapısının genel bağlamda değerlendirilir.  
  
 `punkContext`  
 [in] Context nesnesi adresidir. Bu nesne, bu tür bir bağlam etkin bir çalışma zamanı bağlamı temsil etmek için hata ayıklayıcı tarafından sağlanabilir burada bir hata ayıklama ortamında kullanım için ayrılmıştır. Bu parametre ise `NULL`, altyapısını kullanan `pstrItemName` bağlamı belirlemek için.  
  
 `pstrDelimiter`  
 [in] Yordam son sınırlayıcı adresidir. Zaman `pstrCode` ayrıştırılır gibi iki yordamı sonuna algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgilerin kullanımı bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı sağlar. Bu parametre kümesine `NULL` konak yordamı sonuna işaretlemek için sınırlayıcı kullanmadıysanız.  
  
 `dwSourceContextCookie`  
 [in] Hata ayıklama amacıyla kullanılan uygulama tanımlı bir değer.  
  
 `ulStartingLineNumber`  
 [in] Ayrıştırma sırasında işlemini başlatacak hangi satır belirten sıfır tabanlı değeri.  
  
 `dwFlags`  
 [in] Yordam ile ilişkili bayraklar. Bu değerleri bir bileşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Belirten kodda `pstrCode` yordamı dönüş değerini temsil eden bir ifade değil. Varsayılan olarak, bir ifade, deyimleri listesini ya da başka bir yordamda komut dosyası dili tarafından izin verilen herhangi bir şey kodu içerebilir.|  
|SCRIPTPROC_IMPLICIT_THIS|Belirten `this` işaretçi yordamı kapsamında yer almaktadır.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Belirten üst öğelerini `this` işaretçi yordamı kapsamında dahil edilir.|  
  
 `ppdisp`  
 [out] Komut dosyanızın genel yöntemleri ve özellikleri içeren nesneyi işaretçi adresi. Komut dosyası altyapısı böyle bir nesnenin desteklemiyorsa `NULL` döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Komut dosyası altyapısı çalışma zamanı yordamları ad alanı için eklenmesini desteklemez.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda).|  
|`OLESCRIPT_E_SYNTAX`|Yordamda belirtilmeyen sözdizimi hatası oluştu.|  
|`S_FALSE`|Komut dosyası altyapısı, dağıtım nesnesi desteklemiyor; `ppdisp` parametrenin ayarlanmış `NULL`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Betik kodu, bu çağrı sırasında değerlendirilir; Bunun yerine, yordam Burada, komut dosyası tarafından daha sonra çağrılabilir betik durumuna derlenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptparseprocedure](../../winscript/reference/iactivescriptparseprocedure.md)