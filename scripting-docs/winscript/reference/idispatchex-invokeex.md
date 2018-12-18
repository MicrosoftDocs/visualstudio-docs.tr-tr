---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795179"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Özellikleri ve yöntemleri tarafından sunulan erişim sağlayan bir `IDispatchEx` nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. Kullanan `GetDispID` veya `GetNextDispID` gönderme tanımlayıcısı alınamadı.  
  
 `lcid`  
 Bağımsız değişkenlerin yorumlanacağı yerel ayar bağlamı. `lcid` Geçirilir `InvokeEx` değişkenlerinin bir yerel belirli yorumlamak nesne izin vermek için.  
  
 `wFlags`  
 Yasal değerleri `wFlags` şunlardır:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Bağlamında açıklayan bayrakları `InvokeEx` çağırın:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|DISPATCH_METHOD|Üye bir yöntem olarak çağrılır. Bir özellik aynı ada sahipse, bu hem DISPATCH_PROPERTYGET bayrağı ayarlanmış olabilir (tarafından tanımlanan `IDispatch`).|  
|DISPATCH_PROPERTYGET|Üye özelliği veya veri üyesi olarak alınır (tarafından tanımlanan `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Üye özelliği veya veri üyesi olarak değiştirildiğinde (tarafından tanımlanan `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Üye bir değer atamaya yerine bir başvuru ataması tarafından değiştirildi. Bu bayrak, yalnızca bir nesneye başvuru özelliği kabul ettiğinde geçerlidir (tarafından tanımlanan `IDispatch`).|  
|DISPATCH_CONSTRUCT|Üye Oluşturucusu kullanılır. (Bu tarafından tanımlanan yeni bir değer olan `IDispatchEx`). Yasal değerleri `wFlags` şunlardır:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Bir dizi bağımsız değişkeni içeren bir yapıya yönelik işaretçi, adlandırılmış bağımsız değişkenler için bir dizi bağımsız değişken DISPID değeri ve dizilerdeki öğelerin sayısına ilişkin sayımlar. Bkz: `IDispatch` DISPPARAMS yapısı ilgili tam açıklama için belgeleri.  
  
 `pVarRes`  
 Sonuç saklı veya çağıranın sonuç görüyorsa Null olduğu konuma işaretçi. DISPATCH_PROPERTYPUT veya DISPATCH_PROPERTYPUTREF belirtilmişse, bu bağımsız değişken göz ardı edilir.  
  
 `pei`  
 Özel durum bilgisi içeren bir yapıya yönelik işaretçi. Bu yapı IF doldurulması `DISP_E_EXCEPTION` döndürülür. Null olabilir. Bkz: `IDispatch` ilgili tam açıklama için belgeleri `EXCEPINFO` yapısı.  
  
 `pspCaller`  
 Çağrıyı yapandan Hizmetleri almak nesne sağlar çağıran tarafından sağlanan bir hizmet sağlayıcısı nesnesi işaretçi. Null olabilir.  
  
 `IDispatchEx::InvokeEx`Tüm aynı özellikleri sağlayan `IDispatch::Invoke` ve birkaç uzantıları ekler:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Öğe bir oluşturucu kullanılmakta olduğunu gösterir.|  
|`pspCaller`|`pspCaller` Çağıran tarafından sağlanan hizmetlerin nesne erişmesini sağlar. Belirli hizmetleri çağıran tarafından işlenen veya daha fazla çağrı zincirine yukarı çağıranlar için temsilci. Örneğin, bir komut dosyası altyapısı içinde bir tarayıcı yapar bir `InvokeEx` dış nesne, nesne çağrısı izleyin `pspCaller` zinciri betik altyapısı ya da tarayıcı Hizmetleri elde edilir. (Çağrı zincirine oluşturma zinciri ile aynı değildir — kapsayıcı zinciri veya site zinciri olarak da bilinir. Oluşturma zinciri gibi başka bir mekanizma aracılığıyla kullanılabilir olan `IObjectWithSite`.)|  
|`this`İşaretçi|DISPATCH_METHOD ayarlandığında `wFlags`, "Bu" değeri "adlandırılmış parametre" olabilir. DISPID DISPID_THIS olacak ve ilk adlandırılmış parametre olması gerekir.|  
  
 Kullanılmayan `riid` parametresinde `IDispatch::Invoke` kaldırılmıştır.  
  
 `puArgArr` Parametresinde `IDispatch::Invoke` kaldırılmıştır.  
  
 Bkz: `IDispatch::Invoke` aşağıdaki örneklerde belgelerine:  
  
 "Bağımsız değişken içermeyen bir yöntemi çağırmak"  
  
 "Alma ve özelliklerini ayarlama"  
  
 "Parametreleri geçirme"  
  
 "Dizinli Özellikler"  
  
 "Yükseltme sırasında özel durumlar Invoke"  
  
 "Hataları döndürüyor"  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS için sağlanan öğe sayısı, yöntemi veya özelliği tarafından kabul bağımsız değişken sayısı farklıdır.|  
|DISP_E_BADVARTYPE|Bağımsız değişkenler birini `rgvarg` geçerli bir değişken türü değil.|  
|DISP_E_EXCEPTION|Bir özel durum yükseltmek uygulamanın gerekir. Yapı bu durumda, geçirilen `pei` dolu olması gerekir.|  
|DISP_E_MEMBERNOTFOUND|İstenen üye yok, ya da çağrısı `InvokeEx` salt okunur bir özellik değerinin ayarlanmaya çalışıldı.|  
|DISP_E_NONAMEDARGS|Bu uygulaması, `IDispatch` adlandırılmış değişkenleri desteklemez.|  
|DISP_E_OVERFLOW|Bağımsız değişkenler birini `rgvarg` belirtilen türe zorlanamadı.|  
|DISP_E_PARAMNOTFOUND|Bir parametre DISPID değerleri yöntemine bir parametre için karşılık gelmiyor.|  
|DISP_E_TYPEMISMATCH|Bir veya daha fazla bağımsız değişken zorlanamadı.|  
|DISP_E_UNKNOWNLCID|Çağrılan üye dize bağımsız değişkenleri LCID göre yorumlar ve LCID tanınmıyor. LCID bağımsız değişkenleri yorumlamak için gerekli değildir, bu hata döndürülmemesi gereken.|  
|DISP_E_PARAMNOTOPTIONAL|Gerekli parametre atlandı.|  
  
## <a name="example"></a>Örnek  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idispatchex arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)