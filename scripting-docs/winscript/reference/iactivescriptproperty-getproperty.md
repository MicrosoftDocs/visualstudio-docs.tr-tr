---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cd5c7ac948a9001688de69f9db9ee31624ca33d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284152"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Parametresiyle belirtilen özelliği alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwProperty`  
 Almak için özellik değeri.  
  
 `pvarIndex`  
 Kullanılmadı.  
  
 `pvarValue`  
 Özelliğin değeri.  
  
 İçin izin verilen değerler `dwProperty` aşağıdaki tabloda açıklanmıştır.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Kayan nokta modu yerine tamsayı modunda bölmek için komut dosyası altyapısı zorlar.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Komut dosyası altyapısı değiştirilecek dize karşılaştırma işlevine izin verir.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Küresel nesneye katkıda bulunmak için herhangi bir komut dosyası motorları mevcut komut dosyası altyapısı bildirir.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Zorlar [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dil özelliklerinin desteklenmesi için bir grubu seçmek için komut dosyası altyapısı. Tarafından desteklenen dil özellikleri varsayılan kümesini [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sürümünü 5.7 görünen dil özelliği ayarlamak için komut dosyası altyapısı eşdeğerdir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçerli değil.|  
|`E_UNEXPECTED`|Çağrı beklenmiyordu (örneğin, komut dosyası altyapısı henüz yüklenen başlatıldı veya).|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, başka bir komut dosyası motorları küresel nesneye katkıda bulunmak için mevcut bir komut dosyası altyapısı bildirmek için SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION özelliğini kullanabilirsiniz. Örneğin, Internet Explorer bilgilendirebilir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] oluşturulmakta olan sayfaya yalnızca içeren altyapısı [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] betikler. Bu nedenle, yalnızca [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] altyapısı, yeni özellikleri genel nesne penceresine ekleyebilir ve aynı yapmak için hiçbir Visual Basic Scripting Edition (VBScript) altyapısı yoktur. Altyapısı bu bayrağı yoksayın veya genel nesnesine eklenen yeni üyeler yönetimini iyileştirmek için kullanabilirsiniz.  
  
 Konak kümesi olarak dil özellikleri seçmek için SCRIPTPROP_INVOKEVERSIONING özelliğini kullanabilirsiniz ne zaman desteklenen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı başlatılır. Bu özellik (SCRIPTLANGUAGEVERSION_5_7) 1 olarak ayarlarsanız, kullanılabilir dil özellikleri sürümünü 5.7 görünen aynıdır [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı. 2 (SCRIPTLANGUAGEVERSION_5_8)'ye ayarlanmışsa kullanılabilir dil özellikleri 5.7 Sürüm 5.8 sürümünde eklenen özellikler ek olarak görünen olanlardır. Varsayılan olarak, bu özellik, konak farklı varsayılan davranışını desteklemediği sürece, 5.7 sürümünde görünen dil özellik kümesine eşdeğer olan (SCRIPTLANGUAGEVERSION_DEFAULT) 0 olarak ayarlanır. Örneğin, Internet Explorer 8 olarak kabul eder [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 sürümü tarafından desteklenen dil özellikleri [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Internet Explorer 8 belge modu "Internet Explorer 8 standartları" modunda olduğunda varsayılan komut dosyası altyapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Belge uyumluluğunu tanımlama](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty](../../winscript/reference/iactivescriptproperty.md)   
 [Sürüm Bilgileri](../../javascript/reference/javascript-version-information.md)