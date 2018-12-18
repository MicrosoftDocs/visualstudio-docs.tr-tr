---
title: IActiveScriptProperty::SetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 186608bc56cf8b3649f5beeb1e3a301580ce44bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279290"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Parametresiyle belirtilen özelliği ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetProperty(  
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
 Ayarlanacak özellik değeri.  
  
 `pvarIndex`  
 Kullanılmadı.  
  
 `pvarValue`  
 Özelliğin değeri.  
  
 İçin izin verilen değerler `dwProperty` aşağıdaki tabloda açıklanmıştır.  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Kayan nokta modu yerine tamsayı modunda bölmek için komut dosyası altyapısı zorlar. Varsayılan değer `False` şeklindedir.|  
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
 Etkinleştirmek ya da tamsayı bölme devre dışı bırakmak için çağırma `SetProperty` ve dönüştürme bir `Boolean` için bir `Object`. Varsayılan olarak, özellik değeri olan `False`. Ayarlarsanız `True`, bölme işlemlerini yalnızca tamsayı döndürür.  
  
 Etkinleştirmek veya devre dışı özel dize karşılaştırması için çağırma `SetProperty` ve geçirin bir `Object` değeri. Geçirdiğiniz nesne arabirimi uygulamalıdır [Iactivescriptstringcompare arabirimi](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) yöntemi [Iactivescriptstringcompare arabirimi](../../winscript/reference/iactivescriptstringcompare-interface.md) arabirimi, bir dize karşılaştırma işlevi yürütülen her zaman çağrılır.  
  
 Ne zaman desteklenecek dil özellikleri kümesi seçmek için [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı başlatılır, çağırma `SetProperty` SCRIPTPROP_INVOKEVERSIONING için etkinleştirilmesi için dil özelliği için karşılık gelen bir değer geçirirsiniz. Bu özellik (SCRIPTLANGUAGEVERSION_5_7) 1 olarak ayarlarsanız, kullanılabilir dil özellikleri sürümünü 5.7 görünen aynıdır [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı. 2 (SCRIPTLANGUAGEVERSION_5_8)'ye ayarlanmışsa kullanılabilir dil özellikleri 5.7 Sürüm 5.8 sürümünde eklenen yeni özellikler ek olarak görünen olanlardır. Varsayılan olarak, bu özellik, konak farklı varsayılan davranışını desteklemediği sürece, 5.7 sürümünde görünen dil özellik kümesine eşdeğer olan (SCRIPTLANGUAGEVERSION_DEFAULT) 0 olarak ayarlanır. Örneğin, Internet Explorer 8 olarak kabul eder [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 sürümü tarafından desteklenen dil özellikleri [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Internet Explorer 8 varsayılan belge modu "Internet Explorer 8 standartları" modunda olduğunda varsayılan komut dosyası altyapısı. Internet Explorer 8 belge modu, Internet Explorer 7 standartları için veya süslemeler moduna geçiş sıfırlar [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.7 sürümde var olan dil özellik kümesini desteklemek için komut dosyası altyapısı [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı.  
  
> [!NOTE]
>  Yalnızca SCRIPTPROP_INVOKEVERSIONING ayarlanmalıdır [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] komut dosyası altyapısı başlatılan.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Tamsayı bölme kullanmak için komut dosyası altyapısı zorlanması ve karşılaştırma işlev aşırı yüklemesi kullanmasının nasıl sağlanacağını gösterir.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Belge uyumluluğunu tanımlama](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty](../../winscript/reference/iactivescriptproperty.md)   
 [Sürüm Bilgileri](../../javascript/reference/javascript-version-information.md)