---
title: Idispatchex arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22ccc54dee335fd8c81343557d2f32c48eb30560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837925"
---
# <a name="idispatchex-interface"></a>IDispatchEx Arabirimi
`IDispatchEx`, uzantısı `IDispatch` arabirimi özellikleri uygun komut dosyası dilleri gibi dinamik dilleri için. Bu bölümde açıklanmaktadır `IDispatchEx` kendisini arasındaki farklar arabirim `IDispatch` ve `IDispatchEx`ve uzantıları için stratejinin. Okuyucular aşina olduğunuzu beklenmektedir `IDispatch` ve erişimi `IDispatch` belgeleri.  
  
## <a name="remarks"></a>Açıklamalar  
 `IDispatch` Microsoft Visual Basic için temel olarak geliştirilmiştir. Birincil SORUMLULUĞUN `IDispatch` olan nesneleri statik olduğunu varsayar. Nesneler, çalışma zamanı sırasında değiştirmeyin olduğundan, diğer bir deyişle, tür bilgilerini tam olarak bunları derleme zamanında tanımlayabilirsiniz. Visual Basic Scripting Edition (VBScript) gibi komut dosyası dilleri içinde bulunan dinamik çalışma zamanı modelleri ve [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ve nesne modellerini daha esnek bir arabirim gibi dinamik HTML gerektirir.  
  
 `IDispatchEx` tüm hizmetleri sağlamak üzere geliştirilmiştir `IDispatch` komut dosyası dilleri gibi daha dinamik geç bağlanan diller için uygun olan bazı uzantılar yanı sıra. Ek özellikleri `IDispatchEx` tarafından sağlananlar dışında `IDispatch` şunlardır:  
  
- Bir nesneye ("expando") yeni üyeler eklemek — kullanın `GetDispID` ile `fdexNameEnsure` bayrağı.  
  
- Bir nesnenin üyelerine Sil — kullanın `DeleteMemberByName` veya `DeleteMemberByDispID`.  
  
- Büyük/küçük harfe dağıtma işlemleri — kullanın `fdexNameCaseSensitive` veya `fdexNameCaseInsensitive`.  
  
- Örtük ada sahip üye için arama — kullanın `fdexNameImplicit`.  
  
- Bir nesnenin DISPID değeri listeleme — kullanın `GetNextDispID`.  
  
- DISPID haritasına öğe adı — kullanın `GetMemberName`.  
  
- Nesne üyeleri özelliklerini alın — kullanın `GetMemberProperties`.  
  
- Yöntem çağırma ile `this` işaretçi — kullanın `InvokeEx` DISPATCH_METHOD ile.  
  
- Bir nesnenin adı alanı üst elde etmek için ad alanları kavramını destekleyen tarayıcılar izin — kullanın `GetNameSpaceParent`.  
  
  Nesneleri destekleyen `IDispatchEx` de destekleyebilir `IDispatch` geriye dönük uyumluluk için. Destek nesneleri dinamik doğasını `IDispatchEx` birkaç şifrelemelerini `IDispatch` söz konusu nesnelerin arabirimi. Örneğin, `IDispatch` aşağıdaki varsayım yapmaz:  
  
- DISPID değeri parametresi ve üye nesne ömrü boyunca sabit kalması gerekir. Bu, bir istemcinin DISPID değeri bir kez elde ve daha sonra kullanmak üzere önbelleğe sağlar.  
  
  Bu yana `IDispatchEx` eklenmesini ve üyelerinin geçerli DISPID değeri kümesini silme değil kalan sabit sağlar. Ancak, `IDispatchEx` DISPID ve üye adına arasındaki eşlemeyi sabit kalmasını gerektirir. Üye silinirse anlamına gelir:  
  
- Aynı ada sahip bir üye oluşturulana kadar DISPID kullanılamayacak.  
  
- DISPID için geçerli kalmalıdır `GetNextDispID`.  
  
- DISPID düzgün biçimde herhangi biri tarafından kabul edilmesi gereken `IDispatch` veya `IDispatchEx` yöntemleri — üye silindi olarak tanınması ve uygun hata kodunu (genellikle DISP_E_MEMBERNOTFOUND veya S_FALSE) döndürür.  
  
## <a name="examples"></a>Örnekler  
 Bu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] işlevi test() kodda şunları yapar:  
  
- Çağırarak yeni bir nesne oluşturur `Object` oluşturucusu ve değişken Obj. yeni nesneye bir işaretçi atar  
  
- Nesnesinde Elem adlı yeni bir öğe oluşturur ve bu öğeye bir işaretçi işlevi cat atar.  
  
- Bu işlevi çağırır. Bir yöntem çağrılan beri `this` işaretçi Obj. nesnesine başvurur İşlev yeni bir öğe ekler çubuğuna nesnesinin.  
  
  Tam HTML kodu verilmiştir:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Bu aynı Web sayfasına yerleştirilen bir denetim, tarayıcıda betik altyapısına gönderme işaretçi elde edebilir. Denetimin ardından işlevi test() uygulayabilir:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Kod denetiminden, test, aynı şeyi yapar [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] işlevi `test()`. Bu gönderme çağrıları içine çalışması yapıldığını unutmayın [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] altyapısı ve altyapının durumunu değiştirin:  
  
- Cat işlevi kullanarak gönderme işaretçi `GetDispID()`.  
  
- Nesne işlevi kullanarak gönderme işaretçi `GetDispID()`.  
  
- Bir nesne nesne işlevini çağırarak oluşturur `InvokeEx()` ve yeni oluşturulmuş nesne için bir gönderme işaretçi alır.  
  
- Nesnesini kullanarak Elem, yeni bir öğe oluşturur `GetDispID()` ile `fdexNameEnsure` bayrağı.  
  
- Öğesini kullanarak cat için gönderme işaretçi koyar `InvokeEx()`.  
  
- Çağırarak cat gönderme işaretçisi bir yöntem çağırır `InvokeEx()` ve gönderme işaretçiyi yapılandırılmış nesne olarak geçirerek `this` işaretçi.  
  
- Cat yöntemi yeni bir öğe oluşturur çubuğunda geçerli `this` nesne.  
  
- Doğrular yeni bir öğe, çubuk, oluşturulan nesneyi kullanarak öğeleri numaralandırarak oluşturulduğu `GetNextDispID()`.  
  
  Test denetimi için kod:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Yöntemler  
 [IDispatchEx Metotları](../../winscript/reference/idispatchex-methods.md)