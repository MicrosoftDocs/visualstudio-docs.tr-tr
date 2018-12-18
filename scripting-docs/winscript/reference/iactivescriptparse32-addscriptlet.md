---
title: IActiveScriptParse32::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7b4ea62bf8afa4247fc7c4fdbea40c6b7c772661
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793451"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Kod Resimli komut dosyasına ekler. Bu yöntem, burada betik kalıcı durumunu konak belgeyle birbirine ve ana bilgisayar komut dosyasını geri yüklemek için sorumlu olduğu ortamlarda kullanılır yerine ile bir `IPersist*` arabirimi. Kod parçacıklarını iç olayları eklenecek HTML belgesinde katıştırılmış kod izin HTML komut dosyası dilleri birincil örnekler (örneğin, ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrDefaultName`  
 [in] Kod parçacığı ile ilişkilendirmek için varsayılan adı adresidir. Kod parçacığını (örnektekiyle ONCLICK yukarıdaki) adlandırma bilgileri içermiyorsa, bu ad Resimli tanımlamak için kullanılır. Bu parametre ise `NULL`, komut dosyası altyapısı, benzersiz bir ad gerekirse üreten.  
  
 `pstrCode`  
 [in] Adresi eklemek için kullanılan kod parçacığı metin. Bu dize yorumu komut dosyası dile bağlıdır.  
  
 `pstrItemName`  
 [in] Bu kod parçacığı ile ilişkili öğe adı içeren bir arabellek adresi. Ek olarak bu parametre, `pstrSubItemName`, kod parçacığını bir olay işleyicisi olduğu nesneyi tanımlar.  
  
 `pstrSubItemName`  
 [in] Adını içeren bir arabellek adresini bir `subobject` adlandırılmış öğesi, bu kod parçacığını ilişkilendirilen; bu ad adlandırılmış öğenin türü bilgilerinde bulunamadı. Kod parçacığı yerine adlandırılmış öğe ile ilişkili olması için bu parametre NULL ise bir `subitem`. Ek olarak bu parametre, `pstrItemName`, kod parçacığını bir olay işleyicisi olduğu belirli nesne tanımlar.  
  
 `pstrEventName`  
 [in] Kod parçacığını bir olay işleyicisi olduğu olay adını içeren bir arabellek adresi.  
  
 `pstrDelimiter`  
 [in] Resimli son sınırlayıcı adresidir. Zaman `pstrCode` parametresi metin akışından ayrıştırılır, gibi iki Resimli sonuna algılamak için tırnak işaretleri ("), tek konak genellikle bir sınırlayıcı kullanır. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgilerin kullanımı bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı sağlar. Konak Resimli sonuna işaretlemek için sınırlayıcı kullanmadıysanız, bu parametre NULL olarak ayarlayın.  
  
 `dwSourceContextCookie`  
 [in] Hata ayıklama amacıyla kullanılan uygulama tanımlı bir değer.  
  
 `ulStartingLineNumber`  
 [in] Ayrıştırma sırasında işlemini başlatacak hangi satır belirten sıfır tabanlı değeri.  
  
 `dwFlags`  
 [in] Kod parçacığı ile ilişkili bayraklar. Aşağıdaki değerlerden bir bileşimi olabilir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Betik metin görünür olması gerektiğini gösterir (ve bu nedenle, ada göre aranabilir) genel bir betik adı alanı yöntemi olarak.|  
|SCRIPTTEXT_ISPERSISTENT|Komut dosyası altyapısı kaydedilirse, bu çağrı sırasında eklenen kodu kaydedilmesi gerektiğini gösterir (örneğin, bir çağrıyla `IPersist*::Save`), veya komut dosyası altyapısı Başlatıldı durumuna geçiş yapmamanız sıfırlanır. Bu durumu hakkında daha fazla bilgi için komut dosyası altyapısı durumları bakın.|  
  
 `pbstrName` ,  
 [out] Kod parçacığı tanımlamak için kullanılan gerçek ad. Bu tercih sırasına göre olacak: kod parçacığı metinde açıkça belirtilen bir ad, varsayılan adı sağlanan `pstrDefaultName`, veya komut dosyası altyapısı tarafından oluşturulan benzersiz bir ad.  
  
 `pexcepinfo` ,  
 [out] Özel durum bilgilerini içeren bir yapı adresidir. DISP_E_EXCEPTION döndürülürse, bu yapıyı doldurulması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`DISP_E_EXCEPTION`|Kod parçacığı ayrıştırma bir özel durum oluştu. `pexcepinfo` Parametresi özel durum hakkında bilgiler içerir.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_NOTIMPL`|Bu yöntem desteklenmiyor; komut dosyası altyapısı olay indirme kod parçacıklarını eklemeyi desteklemez.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya) ve bu nedenle başarısız oldu.|  
|`OLESCRIPT_E_INVALIDNAME`|Bu komut dosyası dili ile sağlanan varsayılan adı geçersiz.|  
|`OLESCRIPT_E_SYNTAX`|Resimli belirtilmeyen sözdizimi hatası oluştu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)