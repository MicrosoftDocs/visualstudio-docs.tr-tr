---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794927"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Belirtilen metni için bir hata ayıklama ifadesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrCode`  
 [in] İfade veya deyim metnin sağlar.  
  
 `nRadix`  
 [in] Kullanılacak sayı tabanını.  
  
 `pstrDelimiter`  
 [in] Son olarak betik bloğu sınırlayıcısı. Zaman `pstrCode` ayrıştırılır gibi iki komut dosyası bloğunun sonunu algılamak için tırnak işaretleri ("), tek bir metin akışından ana bilgisayar bir sınırlayıcı genellikle kullanır.. Bu parametre bazı koşullu ilkel ön işleme sağlamak komut dosyası altyapısı izin vererek ana kullanılan sınırlayıcı belirtir (örneğin, tek tırnak işareti ['] ayırıcı olarak kullanmak için iki tek tırnak işareti yerine). Tam olarak nasıl (ve ise) bu bilgileri bağlıdır komut dosyası altyapısı üzerinde komut dosyası altyapısı kullanır. Bu parametre kümesine `NULL` ana komut dosyası bloğunun sonunu işaretlemek üzere bir sınırlayıcı kullanmadıysanız.  
  
 `dwFlags`  
 [in] Aşağıdaki hata ayıklama metin bayrak birleşimi:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Metin bir deyim aksine bir ifade olduğunu gösterir. Bu bayrak metin bazı diller tarafından ayrıştırılır şekilde etkileyebilir.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Dönüş değeri kullanılabilir ise, çağıran tarafından kullanılır.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Yan etkiler izin vermez. İfade değerlendirme, bu bayrağı ayarlarsanız, çalışma zamanı durumu değiştirmeniz gerekir.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Kesme noktaları metin değerlendirme sırasında sağlar. Bu bayrak ayarlanmazsa kesme noktaları metin değerlendirme sırasında dikkate alınmaz.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Hata raporlarını metin değerlendirme sırasında sağlar. Ardından bu bayrağı ayarlanmamışsa hataları konağa değerlendirmesi sırasında raporlanmaz.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|İfade çalıştırmak yerine ifade kod bağlamına değerlendirilecek gösterir|  
  
 `ppe`  
 [out] Belirtilen metni için hata ayıklama ifadesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen metni için bir hata ayıklama ifadesi oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugexpressioncontext arabirimi](../../winscript/reference/idebugexpressioncontext-interface.md)