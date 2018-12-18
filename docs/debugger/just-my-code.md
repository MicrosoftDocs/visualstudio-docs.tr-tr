---
title: Kullanıcı kodunda yalnızca kendi kodum ile hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01e36c528b71bb49b29265890ca6c48863f01be9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389033"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Yalnızca kullanıcı kodunu yalnızca kendi kodum ile hata ayıklama 

*Yalnızca kendi kodum* bir Visual Studio hata ayıklama otomatik olarak adımları sistemi, çerçeve ve diğer kullanıcı olmayan kod çağrıları üzerinden özelliğidir. İçinde **çağrı yığını** pencere, yalnızca kendi kodum içinde bu çağrıları daraltır **[harici kod]** çerçeveler. 

Yalnızca kendi kodum, .NET Framework, C++ ve JavaScript projelerinde farklı şekilde çalışır.

##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Etkinleştirmek veya devre dışı yalnızca kendi kodum  

Çoğu programlama dili için yalnızca kendi kodum, varsayılan olarak etkindir. 

- Etkinleştirme veya altında Visual Studio'da, Just My Code'u devre dışı **Araçları** > **seçenekleri** (veya **hata ayıklama** > **seçenekleri**) > **Hata ayıklama** > **genel**seçin veya seçimini **yalnızca benim kodumu etkinleştir**.
  
 ![Seçenekler iletişim kutusundaki Just My Code'u etkinleştirmek](../debugger/media/dbg_justmycode_options.png "yalnızca benim kodumu etkinleştir")  
  
> [!NOTE]
> **Sadece benim kodumu etkinleştir** tüm Visual Studio projelerine tüm dillerde uygulanan genel bir ayardır.  
  
##  <a name="just-my-code-debugging"></a>Yalnızca Kendi Kodumda hata ayıklama

Bir hata ayıklama oturumu sırasında **modülleri** , hata ayıklayıcı kodum (kullanıcı kodu) değerlendirmesini modülleri durumu yüklenirken, sembol birlikte kod penceresini gösterir. Daha fazla bilgi için [Hata Ayıklayıcı'nın uygulamanıza nasıl ekleyen daha iyi tanımak](../debugger/debugger-tips-and-tricks.md#modules_window).

 ![Modüller penceresini kullanıcı kodunda](../debugger/media/dbg_justmycode_module.png "modüller penceresini kullanıcı kodunda")
  
İçinde **çağrı yığını** veya **görevleri** pencere, yalnızca kendi kodum daraltır kullanıcı olmayan kod olarak etiketlenmiş grileştirilmiş açıklamalı kod çerçeveye `[External Code]`.

 ![Dış kod çerçeve çağrı yığını penceresinde](../debugger/media/dbg_justmycode_externalcode.png "dış kod çerçevesi")
  
>[!TIP]
>Açmak için **modülleri**, **çağrı yığını**, **görevleri**, veya çoğu diğer hata ayıklama windows, hata ayıklama oturumunda olması gerekir. Hata ayıklarken, altında **hata ayıklama** > **Windows**, açmak istediğiniz windows seçin. 

<a name="BKMK_Override_call_stack_filtering"></a> Daraltılmış bir kodu görmek için **[harici kod]** çerçeve, sağ **çağrı yığını** veya **görev** penceresi ve select **harici kodu Göster**bağlam menüsünden. Genişletilmiş bir dış kod satırlarını değiştirin **[harici kod**] çerçeve. 

 ![Çağrı yığını penceresinde dış Kodu Göster](../debugger/media/dbg_justmycode_showexternalcode.png "harici kodu göster")
  
> [!NOTE]
> **Dış Kodu Göster** tüm dillerdeki kullanıcı tarafından açılan tüm projelere ayarı geçerli bir kullanıcı profil oluşturucu uygular.

Bir genişletilmiş dış kod satırında çift **çağrı yığını** penceresi, kaynak kodunda yeşil çağıran kod satırı vurgular. DLL veya bulunamadı veya yüklü diğer modüller için sembol veya kaynak sayfası açılabilir bulunamadı.

##  <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET framework yalnızca kendi kodum 

.NET Framework projelerinde, yalnızca kendi kodum sembol kullanır (*.pdb*) dosya ve program iyileştirmeleri, kullanıcı ve kullanıcı olmayan kod sınıflandırmak için. .NET Framework hata ayıklayıcı değerlendirir yüklü olmayan ve ikili dosyaları en iyi duruma getirilmiş *.pdb* kullanıcı olmayan kod dosyaları.
  
.NET hata ayıklayıcı kullanıcı kodu dikkate üç derleyici öznitelikleri de etkiler:  

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> için uygulanan kod kullanıcı kodu olmayan hata ayıklayıcıya bildirir.  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Yalnızca kendi kodum kapalı olsa bile hata ayıklayıcıyı kodu gizler.  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> hata ayıklayıcının, kod içine Adımlama yerine uygulandığı kod adım adım anlatır.  

.NET Framework hata ayıklayıcı kullanıcı kodu tüm kod olarak değerlendirir.  

.NET Framework'te hata ayıklama sırasında:

- **Hata ayıklama** > **içine adımla** (veya **F11**) kullanıcı kodunun sonraki satıra kod üzerinde kullanıcı olmayan kod adımlar. 
- **Hata ayıklama** > **Step Out** (veya **Shift**+**F11**) kullanıcı olmayan kod üzerinde çalışan kullanıcı kodu sonraki satırına. 

Daha fazla kullanıcı kodu yoksa sona erer, başka bir kesme noktasına denk gelir veya bir hata atar kadar hata ayıklama devam eder. 

<a name="BKMK_NET_Breakpoint_behavior"></a> Hata ayıklayıcı kullanıcı olmayan kodu keserse (örneğin, kullandığınız **hata ayıklama** > **tümünü Kes** ve kullanıcı olmayan kod duraklatma), **kaynak** penceresi görüntülenir. Daha sonra kullanabileceğiniz bir **hata ayıklama** > **adım** kullanıcı kodunun sonraki satıra Git komutu.

Kullanıcı olmayan kod içinde işlenmeyen bir özel durum meydana gelirse, hata ayıklayıcı özel durum burada oluşturulan kullanıcı kod satırında keser.  
  
İlk fırsat özel durum için etkinse, kaynak kodundaki yeşil çağıran kullanıcı kod satırı vurgulanır. **Çağrı yığını** etiketli açıklamalı çerçeve penceresi görüntüler **[harici kod]**.  

##  <a name="BKMK_C___Just_My_Code"></a> C++ yalnızca kendi kodum  
  
C++'da, yalnızca kendi kodum etkinleştirme kullanarak aynıdır [(yalnızca benim kodum hata ayıklayıcı) /JMC](/cpp/build/reference/jmc) derleyici anahtarı.

<a name="BKMK_CPP_User_and_non_user_code"></a> Yalnızca kendi kodum olduğundan farklı .NET Framework ve JavaScript, c++ atlama davranışı için ayrı ayrı kullanıcı olmayan dosyaları belirtebilirsiniz ve **çağrı yığını** penceresi. 

C++'ta yalnızca benim kodum kullanıcı olmayan kod olacak şekilde bu işlevler yalnızca göz önünde bulundurur:

- İçin **çağrı yığını** penceresi: 

  - İşlevler, semboller dosyası kesilmiş kaynak bilgileri.  
  - İşlevler, yığın çerçevesi için karşılık gelen kaynak dosya yok sembol dosyaları burada belirtin.  
  - Belirtilen işlevleri  *\*.natjmc* dosyalar *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* klasör.  
  
- Davranış atlamak için:
  
  - Belirtilen işlevleri  *\*.natstepfilter* dosyalar *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* klasör.  
  
Oluşturabileceğiniz *.natstepfilter* ve *.natjmc* yalnızca kendi kodum atlama davranışını özelleştirmek için dosyaları ve **çağrı yığını** penceresi. Bkz: [özelleştirme C++ atlama davranışını](#BKMK_CPP_Customize_stepping_behavior) ve [özelleştirme C++ çağrı yığını davranışı](#BKMK_CPP_Customize_call_stack_behavior). 

<a name="BKMK_CPP_Stepping_behavior"></a> C++ hata ayıklama sırasında:

- **Hata ayıklama** > **içine adımla** (veya **F11**) kullanıcı kodunun sonraki satıra kod üzerinde kullanıcı olmayan kod adımlar. 
- **Hata ayıklama** > **Step Out** (veya **Shift**+**F11**) kullanıcı olmayan kod üzerinde çalışan kullanıcı kodu sonraki satırına. 

Daha fazla kullanıcı kodu yoksa sona erer, başka bir kesme noktasına denk gelir veya bir hata atar kadar hata ayıklama devam eder. 

Hata ayıklayıcı kullanıcı olmayan kodu keserse (örneğin, kullandığınız **hata ayıklama** > **tümünü Kes** ve duraklatma kullanıcı olmayan kod), Adımlama kullanıcı dışındaki kodda devam eder.

Hata ayıklayıcısı özel bir durum olursa, kullanıcı veya kullanıcı olmayan kod olup olmadığını özel durum durdurur. **Kullanıcı-işlenmemiş** seçeneklerini **özel durum ayarları** iletişim kutusunu yok sayılır.  

###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> C++ atlama davranışını özelleştirme  

 C++ projelerinde, İşlevler kullanıcı olmayan kod olarak listelenerek tarafından devralınırsa adım belirtebilirsiniz  *\*.natstepfilter* dosyaları.  
  
- Tüm yerel Visual Studio kullanıcılar için kullanıcı olmayan kod belirtmek için *.natstepfilter* dosyasını *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* klasör.  
- Bir kullanıcı için kullanıcı olmayan kod belirtmek için *.natstepfilter* dosyasını *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers* klasör.  
  
A *.natstepfilter* dosyasıdır bu söz dizimi olan bir XML dosyası:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Function`|Gerekli. Bir veya daha fazla işlevleri kullanıcı olmayan işlevler olarak belirtir.|  
|`Name`|Gerekli. ECMA 262 eşleşmesi için tam işlev adını belirterek normal ifade biçimlendirilmiş. Örneğin:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> hata ayıklayıcı, bildiren tüm yöntemler `MyNS::MyClass` kullanıcı olmayan kod kabul edilip. Eşleşme büyük/küçük harf duyarlıdır.|  
|`Module`|İsteğe bağlı. ECMA 262 işlevi içeren modül tam yolunu belirtmeyi normal ifade biçimlendirilmiş. Eşleşme büyük/küçük harf duyarlıdır.|  
|`Action`|Gerekli. Büyük/küçük harfe şu değerlerden biri:<br /><br /> `NoStepInto`  -işlevin adımlamak için hata ayıklayıcıya bildirir.<br /> `StepInto`  -işleve, hata ayıklayıcının söyleyen diğer geçersiz kılma `NoStepInto` eşleşen işlevi.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> C++ çağrı yığını davranışını özelleştirme  

C++ projeleri için modüller, kaynak dosyaları ve işlevleri belirtebilirsiniz **çağrı yığını** penceresi, bunları belirterek kullanıcı olmayan kod olarak değerlendirir  *\*.natjmc* dosyaları.  
  
-   Kullanıcı dışı kod için Visual Studio makinenin tüm kullanıcıları belirtmek için *.natjmc* dosyasını *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* klasör.  
-   Bir kullanıcı için kullanıcı olmayan kod belirtmek için *.natjmc* dosyasını *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers* klasör.  

A *.natjmc* dosyasıdır bu söz dizimi olan bir XML dosyası:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Modül öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Modül veya modülleri tam yolu. Windows joker karakterler kullanabilirsiniz `?` (sıfır veya bir karakter) ve `*` (sıfır veya daha fazla karakter). Örneğin,<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> Tüm modüllerdeki değerlendirilecek hata ayıklayıcıya bildirir *\3rdParty\UtilLibs* harici kod olarak herhangi bir sürücüdeki.|  
|`Company`|İsteğe bağlı. Yürütülebilir dosyada gömülü modülü yayımlayan şirketin adı. Modüller belirsizliğini ortadan kaldırmak için bu özniteliği kullanabilirsiniz.|  
  
 **Dosya öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Kaynak dosya veya dosyalar harici kod olarak değerlendirilecek tam yolu. Windows joker karakterler kullanabilirsiniz `?` ve `*` yolunu belirtmek için.|  
  
 **İşlev öğesi öznitelikleri**  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Harici kod olarak değerlendirilecek işlevin tam adı.|  
|`Module`|İsteğe bağlı. İşlevi içeren modül tam yolu ve adı. Aynı ada sahip işlevler belirsizliğini ortadan kaldırmak için bu özniteliği kullanabilirsiniz.|  
|`ExceptionImplementation`|Ayarlandığında `true`, özel durum oluşturdu işlevi yerine bu işlev çağrı yığınını görüntüler.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript yalnızca kendi kodum  

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript yalnızca kendi kodum, bu sınıflandırmaları birinde kod gruplayarak adımlama ve çağrı yığını görüntü denetimleri:  

|||  
|-|-|  
|**MyCode**|Sahibi olduğunuz ve denetlediğiniz kullanıcı kodu.|  
|**LibraryCode**|Doğru şekilde (örneğin WinJS veya jQuery) çalışması için kullanıcı dışı kod düzenli olarak kullandığınız kitaplıklar ve uygulamanıza kullanır.|  
|**UnrelatedCode**|Sahip olmadığınız uygulamanızı ve uygulamanızın kullanıcı olmayan kod üzerinde doğru çalışması için içermez. Örneğin, bir reklam görüntüler reklam SDK'sı UnrelatedCode olabilir. UWP projelerinde, HTTP veya HTTPS URI uygulamanızdan yüklenen herhangi bir kod da UnrelatedCode kabul edilir.|  

JavaScript hata ayıklayıcı, kodu kullanıcı veya kullanıcı olmayan bu sırayla olarak sınıflandırır:  
  
1. Varsayılan sınıflandırmalar.  
   -   Ana bilgisayar tarafından sağlanan için bir dize geçirerek yürütülen betik `eval` işlevi **MyCode**.  
   -   Bir dizeye geçirerek yürütülen betik `Function` oluşturucudur **LibraryCode**.  
   -   WinJS ya da Azure SDK'sı gibi framework başvurusu betiğidir **LibraryCode**.  
   -   Bir dizeye geçirerek yürütülen betik `setTimeout`, `setImmediate`, veya `setInterval` işlevleri, **UnrelatedCode**.  
   
2. Tüm Visual Studio JavaScript projeleri için belirtilen sınıflandırmalar *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* dosya.  
   
3. Sınıflandırmaları *mycode.json* geçerli projenin dosya.  
  
Her sınıflandırma adım, önceki adımlarda geçersiz kılar. 

Diğer tüm kod olarak sınıflandırılır **MyCode**.  

Varsayılan sınıflandırmalar değiştirmek ve belirli dosyaları ve URL'leri ekleyerek kullanıcı veya kullanıcı olmayan kod olarak sınıflandırmak bir *.json* adlı dosya *mycode.json* JavaScript projesinin kök klasörüne. Bkz: [JavaScript yalnızca kendi kodum özelleştirme](#BKMK_JS_Customize_Just_My_Code). 

<a name="BKMK_JS_Stepping_behavior"></a> JavaScript hata ayıklama sırasında: 

- Kullanıcı olmayan kod, bir işlev ise **hata ayıklama** > **içine adımla** (veya **F11**) gibi davranır **hata ayıklama**  >  **Üzerinden adımla** (veya **F10**).  
- Bir adım kullanıcı olmayan başlıyorsa (**LibraryCode** veya **UnrelatedCode**) kod, geçici olarak atlama davranışını alacağı yalnızca kendi kodum etkin değil. Kullanıcı koda geri, yalnızca kendi kodum geçtiğinizde Adımlama tekrar etkinleştirilecektir.  
- Geçerli yürütme bağlamı bırakarak içinde kullanıcı kodu adım sonuçları hata ayıklayıcı sonraki yürütülen kullanıcı kod satırına durdurur. Örneğin, bir geri çağırmayı yürütür, **LibraryCode** kodun, hata ayıklayıcı devam kadar kullanıcı kod sonraki satırı yürütür.
- **Step Out** (veya **Shift**+**F11**) kullanıcı kodun sonraki satırında durdurur. 

Daha fazla kullanıcı kodu yoksa sona erer, başka bir kesme noktasına denk gelir veya bir hata atar kadar hata ayıklama devam eder. 

Her zaman kod içinde ayarlanan kesme noktaları isabet ancak kod sınıflandırılır.  

- Varsa `debugger` anahtar sözcüğü oluşuyor **LibraryCode**, hata ayıklayıcı her zaman keser.  
- Varsa `debugger` anahtar sözcüğü oluşuyor **UnrelatedCode**, hata ayıklayıcı bitmez.  
  
<a name="BKMK_JS_Exception_behavior"></a> İşlenmeyen bir özel durum oluşursa **MyCode** veya **LibraryCode** kod, hata ayıklayıcı her zaman keser.  

İşlenmeyen bir özel durum oluşursa **UnrelatedCode**, ve **MyCode** veya **LibraryCode** hata ayıklayıcı kesmesi çağrı yığını.  
  
İlk fırsat özel durum için etkin ve özel durum meydana **LibraryCode** veya **UnrelatedCode**:  
  
-   Özel durumun işlenip, hata ayıklayıcı sonu gelmez.  
-   Özel durum işlenmezse hata ayıklayıcı keser.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> JavaScript yalnızca kendi kodum özelleştirme  

Kullanıcı ve kullanıcı dışı kod için tek bir JavaScript proje sınıflandırmak için ekleyebileceğiniz bir *.json* adlı dosya *mycode.json* projesinin kök klasörüne.  
  
Bu dosyadaki belirtimleri geçersiz varsayılan sınıflandırmalar ve *mycode.default.wwa.json* dosya. *Mycode.json* dosya tüm anahtar-değer çiftlerinin listelemek ihtiyacı yoktur. **MyCode**, **kitaplıkları**, ve **Unrelated** değerler, boş bir dizi olabilir.  
  
*Mycode.JSON* dosyaları, bu sözdizimini kullanın:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Değerlendirme, işlevi hem de ScriptBlock**  
  
 **Eval**, **işlevi**, ve **ScriptBlock** anahtar-değer çiftlerinin belirlemek nasıl dinamik olarak oluşturulan kod sınıflandırılmış:  
  
|||  
|-|-|  
|**Değerlendirme**|Ana bilgisayar tarafından sağlanan için bir dize geçirerek yürütülen betik `eval` işlevi. Varsayılan olarak, Eval betik olarak sınıflandırılır **MyCode**.|  
|**İşlevi**|Bir dizeye geçirerek yürütülen betik `Function` Oluşturucusu. Varsayılan olarak, işlev betik olarak sınıflandırılır **LibraryCode**.|  
|**ScriptBlock**|Bir dizeye geçirerek yürütülen betik `setTimeout`, `setImmediate`, veya `setInterval` işlevleri. Varsayılan olarak, ScriptBlock betik olarak sınıflandırılır **UnrelatedCode**.|  
  
 Bu anahtar sözcüklerden biri için değer değiştirebilirsiniz:  
  
-   `MyCode`  betik olarak sınıflandırır **MyCode**.  
-   `Library`  betik olarak sınıflandırır **LibraryCode**.  
-   `Unrelated`  betik olarak sınıflandırır **UnrelatedCode**.  
  
  **MyCode, kitaplıklar ve ilgisiz**  
  
 **MyCode**, **kitaplıkları**, ve **Unrelated** anahtar-değer çiftlerinin bir sınıflandırma dahil etmek istediğiniz dosyaları ve URL'leri belirtin:  
  
|||  
|-|-|  
|**MyCode**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **MyCode**.|  
|**Kitaplıkları**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **LibraryCode**.|  
|**İlişkisiz**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **UnrelatedCode**.|  
  
 Bir veya daha fazla URL veya dosya dize olabilir `*` karakter sıfır veya daha fazla karakterini eşleştirin. `*` Normal ifade aynı `.*`.
