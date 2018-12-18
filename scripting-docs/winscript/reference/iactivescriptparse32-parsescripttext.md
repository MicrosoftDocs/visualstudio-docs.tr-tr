---
title: IActiveScriptParse32::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793547"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Ad alanı içine bildirimleri ekleme ve uygun şekilde kodu değerlendirme verilen kodu Resimli ayrıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|||  
|-|-|  
|`pstrCode`|[in] Değerlendirmek için kullanılan kod parçacığı metin adresidir. Bu dize yorumu komut dosyası dile bağlıdır.|  
|`pstrItemName`|[in] Kod parçacığı değerlendirilecek olduğu bağlamı sağlar öğe adı adresidir. Bu parametre NULL ise, kod komut dosyası altyapısının genel bağlamda değerlendirilir.|  
|`punkContext`|[in] Context nesnesi adresidir. Bu nesne, bu tür bir bağlam etkin bir çalışma zamanı bağlamı temsil etmek için hata ayıklayıcı tarafından sağlanabilir burada bir hata ayıklama ortamında kullanım için ayrılmıştır. Bu parametre NULL ise, altyapısı kullanır `pstrItemName` bağlamı belirlemek için.|  
|`pstrDelimiter`|[in] Resimli son sınırlayıcı adresidir. Zaman `pstrCode` ayrıştırılır gibi iki Resimli sonuna algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgilerin kullanımı bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı sağlar. Bu parametre kümesine `NULL` konak Resimli sonuna işaretlemek için sınırlayıcı kullanmadıysanız.|  
|`dwSourceContextCookie`|[in] Hata ayıklama amacıyla kullanılan tanımlama bilgisi.|  
|`ulStartingLineNumber`|[in] Ayrıştırma sırasında işlemini başlatacak hangi satır belirten sıfır tabanlı değeri.|  
|`dwFlags`|[in] Kod parçacığı ile ilişkili bayraklar. Bu değerleri bir bileşimi olabilir:|  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Hesaplama ifadesi ve bir deyim arasında ayrım önemli ancak komut dosyası dili sözdizimsel olarak belirsiz ise, bu bayrak Resimli bir deyim veya deyimleri listesi olarak değil, bir ifade olarak yorumlanır olduğunu belirtir. Kod parçacığı metin sözdiziminden, doğru seçimi belirlenebilir sürece varsayılan olarak, deyimleri varsayılır.|  
|SCRIPTTEXT_ISPERSISTENT|Komut dosyası altyapısı kaydedilirse, bu çağrı sırasında eklenen kodu kaydedilmesi gerektiğini gösterir (örneğin, bir çağrıyla `IPersist*::Save`), veya komut dosyası altyapısı Başlatıldı durumuna geçiş yapmamanız sıfırlanır.|  
|SCRIPTTEXT_ISVISIBLE|Betik metin görünür olması gerektiğini gösterir (ve bu nedenle, ada göre aranabilir) genel bir betik adı alanı yöntemi olarak.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Kod parçacığı işlemenin sonuçlarını alır bir arabellek adresini veya `NULL` çağıran sonuç görüyorsa (diğer bir deyişle, SCRIPTTEXT_ISEXPRESSION değeri ayarlanmamış).|  
|`pexcepinfo`|[out] Özel durum bilgilerini alır bir yapı adresidir. Bu yapı, girilir `IActiveScriptParse::ParseScriptText` DISP_E_EXCEPTION döndürür.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`DISP_E_EXCEPTION`|Kod parçacığı işlenirken bir özel durum oluştu. `pexcepinfo` Parametresi özel durum hakkında bilgiler içerir.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor. Komut dosyası altyapısı çalıştırma değerlendirme ifadeler veya deyimleri desteklemiyor.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı başlatılmamış veya kapalı durumda veya SCRIPTTEXT_ISEXPRESSION bayrağı ayarlandı ve komut dosyası altyapısı başlatılmış durumda).|  
|`OLESCRIPT_E_SYNTAX`|Resimli belirtilmeyen sözdizimi hatası oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut dosyası altyapısı başlatılmış durumda ise, kod aslında bu çağrı sırasında değerlendirilecek; Bunun yerine, bu tür kodu sıraya ve komut dosyası altyapısı içinde (veya yoluyla) geçirildiğinde yürütülen başlangıç durumu. Yürütme başlatılmış durumda izin verilmediğinden SCRIPTTEXT_ISEXPRESSION bayrağıyla başlatılmış bir durumda olduğunda bu yöntemi çağırmak için bir hata var.  
  
 Kod parçacığını bir ifade listesini deyimlerinin veya komut dosyası dili tarafından izin verilen herhangi bir şey olabilir. Örneğin, bu yöntem HTML hesaplanmasında kullanılan \<komut dosyası > etiketi yerine yalnızca bunları derleme betik durumuna HTML sayfası oluşturulmuyor olarak yürütülecek deyimlerine izin verir.  
  
 Bu yönteme geçirilen kod kodunun geçerli, tam bir bölümü olmalıdır. Örneğin, VBScript içinde bu yöntemle kez alt Function(x) ve ardından ikinci bir kez ile çağırmak için geçersiz `End Sub`. Ayrıştırıcının alt yordama tamamlamak ikinci çağrı için bekleme gerekir, ancak bir ayrıştırma hatası yerine bir alt yordama bildirimi başlatıldı ancak tamamlanmamış olduğundan oluşturmanız gerekir.  
  
 Komut dosyası durumları hakkında daha fazla bilgi için komut dosyası altyapısı durumları bölümüne bakın [Windows komut dosyası motorları](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)