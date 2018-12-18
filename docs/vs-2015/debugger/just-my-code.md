---
title: Yalnızca kendi kodum | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b016c8565b3c501c5cc41802512f02b1c10d615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798657"
---
# <a name="just-my-code"></a>Yalnızca Kendi Kodum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework dillerinde kullanan geliştiriciler, çağrı yığını windows sistemi, çerçeve ve diğer kullanıcı olmayan çağrılardan adımlar ve bunları daraltır hata ayıklayıcı özelliği çağırır kodum aşinasınız. Yalnızca kendi kodum, C++ ve JavaScript diller için genişletilmiştir. Bu konu, yalnızca kendi kodum .NET Framework, yerel C++ ve JavaScript kullanarak özellikleri açıklar. projeleri.  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Etkinleştirmek veya devre dışı yalnızca kendi kodum  
 Just My Code'u devre dışı bırakmak veya etkinleştirmek için seçin **seçenekler ve ayarlar** üzerinde **hata ayıklama** menüsü. İçinde **hata ayıklama** / **genel** düğümünü seçin veya temizleyin **yalnızca benim kodumu etkinleştir**.  
  
 ![Seçenekler iletişim kutusundaki Just My Code'u etkinleştirmek](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **Yalnızca benim kodumu etkinleştir** tüm Visual Studio projelerine tüm dillerde uygulanan genel bir ayar bir ayardır.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Çağrı yığını filtreleme geçersiz kıl  
 Yalnızca kendi kodum, çağrı yığını ve görevler windows gibi çağrı yığını gösterimlerinde etiketli bir açıklamalı çerçeve kullanıcı olmayan kod daraltır `[External Code]`. Daraltılmış çerçeveleri görüntülemek için seçin **harici kodu Göster** çağrı yığınının bağlam menüsünü görüntüleyin.  
  
> [!NOTE]
>  **Harici kodu Göster** ayarı için geçerli kullanıcının profil oluşturucu kaydedildi. Tüm dillerdeki kullanıcı tarafından açılan tüm projelere uygulanır.  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> .NET framework yalnızca kendi kodum  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Kullanıcı ve kullanıcı olmayan kod  
 Yalnızca kendi kodum kullanıcı kodu olmayan kullanıcı kodundan ayırt etmek için Sembol (.pdb) dosyalarını ve program iyileştirmeleri arar. Hata ayıklayıcı kod ikili iyileştirilmişse veya .pdb dosyası mevcut olmadığında kullanıcı olmayan kod olarak değerlendirir.  
  
 Hata ayıklayıcı kodum olmasını dikkate üç özniteliği de etkiler:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> için uygulanan kod benim kodum değil hata ayıklayıcıya bildirir.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Yalnızca kendi kodum kapalı olsa bile hata ayıklayıcıyı kodu gizler.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> hata ayıklayıcının, kod içine Adımlama yerine uygulandığı kod adım adım anlatır.  
  
  Diğer tüm kod, kullanıcı kodu olarak kabul edilir.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Atlama davranışını  
 Olduğunda, **içine adımla** (klavye kısayolu: F11) kullanıcı olmayan kod, sonraki kullanıcı deyimi için kod üzerinde hata ayıklama adımlarında. Olduğunda, **Step Out** (klavye: Shift + F11), hata ayıklayıcı sonraki satıra kullanıcı kodu çalıştırır. Hiç kullanıcı kodu karşılaşıldıktan sonra yürütülmeye kadar uygulama çıkar, bir kesme noktasına isabet ya da bir özel durum oluşur.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Kesme noktası davranışı  
 Yalnızca kendi kodum etkinleştirildiğinde, seçebileceğiniz **tümünü Kes** (klavye: Ctrl + Alt + Break) ve yürütmeyi durdur görüntülenecek hiç kullanıcı kodu olduğu. Bu durumda, kaynak penceresinde görüntülenir. Ardından bir adım komutu seçerseniz, hata ayıklayıcı kullanıcı kodunun sonraki satıra götürür.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Özel durum davranışını  
 Kullanıcı olmayan kod içinde işlenmeyen bir özel durum meydana gelirse, hata ayıklayıcı özel durum burada oluşturulan kullanıcı kodunda satırında keser.  
  
 İlk fırsat özel durum için etkinse, kullanıcı kodu satır yeşil renkte vurgulanır. Etiketli bir açıklamalı çerçeve çağrı yığınını görüntüler **[harici kod]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> C++ yalnızca kendi kodum  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Kullanıcı ve kullanıcı olmayan kod  
 Atlama davranışını çağrı yığını davranışını bağımsız olduğundan C++ Yalnızca benim kodum .NET Framework ve JavaScript Just My Code'u farklıdır.  
  
 **Çağrı yığınları**  
  
 Varsayılan olarak, bu işlevler, çağrı yığını Windows kullanıcı olmayan kod için hata ayıklayıcı göz önünde bulundurur:  
  
- İşlevler, semboller dosyası kesilmiş kaynak bilgileri.  
  
- İşlevler, yığın çerçevesi için karşılık gelen kaynak dosya yok sembol dosyaları burada belirtin.  
  
- Belirtilen işlevleri `*.natjmc` dosyalar `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasör.  
  
  **Adımlama**  
  
  Varsayılan olarak, yalnızca işlevler belirtilen `*.natstepfilter` dosyalar `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasör kullanıcı olmayan kod olarak kabul edilir.  
  
  Kendi oluşturabilirsiniz `.natstepfilter` ve `.natjmc` Adımlama özelleştirip çağrı yığını penceresi davranışı `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Atlama davranışını  
 Olduğunda, **içine adımla** (klavye kısayolu: F11) kullanıcı kodundan kullanıcı olmayan kod, kod üzerinde hata ayıklama adımlarında kullanıcı kodu sonraki satırına. Olduğunda, **Step Out** (klavye: Shift + F11), hata ayıklayıcı sonraki satıra kullanıcı kodu çalıştırır. Hiç kullanıcı kodu karşılaşıldıktan sonra yürütülmeye kadar uygulama çıkar, bir kesme noktasına isabet ya da bir özel durum oluşur.  
  
 Hata ayıklayıcı kullanıcı olmayan kodu keserse (örneğin tümünü Kes komutu kullanıcı dışındaki kodda durdurursa), Adımlama kullanıcı dışındaki kodda devam eder.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Özel durum davranışını  
 Hata ayıklayıcı bir özel durum ulaştığında, kullanıcı veya kullanıcı olmayan kod olmasına bakılmaksızın özel durumda durdurur. **Kullanıcı-işlenmemiş** seçeneklerini **özel durumları** iletişim kutusunu yok sayılır.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Atlama davranışını özelleştirme  
 Kullanıcı olmayan kod olarak listelenerek tarafından devralınırsa adım için işlevleri belirtebilirsiniz `*.natstepfilter` dosyaları.  
  
- Kullanıcı dışı kod için Visual Studio makinenin tüm kullanıcıları belirtmek için .natstepfilter dosyaya ekleyin `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasör.  
  
- Bir kullanıcı için kullanıcı olmayan kod belirtmek için .natstepfilter dosyaya ekleyin `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` klasör.  
  
  Bu sözdizimi ile xml dosyaları .natstepfilter dosyalar şunlardır:  
  
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
|İşlev|Gerekli. Bir veya daha fazla işlevleri kullanıcı olmayan işlevler olarak belirtir.|  
|`Name`|Gerekli. ECMA 262 eşleşmesi için tam işlev adını belirterek normal ifade biçimlendirilmiş. Örneğin:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> hata ayıklayıcı, bildiren tüm yöntemler `MyNS::MyClass` kullanıcı olmayan kod kabul edilip. Eşleşme büyük/küçük harf duyarlıdır.|  
|`Module`|İsteğe bağlı. ECMA 262 işlevi içeren modül tam yolunu belirtmeyi normal ifade biçimlendirilmiş. Eşleşme büyük/küçük harf duyarlıdır.|  
|`Action`|Gerekli. Büyük/küçük harfe şu değerlerden biri:<br /><br /> -   `NoStepInto`  – eşleşen işlevin adımlamak için hata ayıklayıcıya bildirir.<br />-   `StepInto`  – eşleşen işlevleri adımlamak için hata ayıklayıcıya bildirir diğer geçersiz kılma `NoStepInto` eşleşen işlevleri için.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Çağrı yığını davranışını özelleştirme  
 Modüller, kaynak dosyaları ve bunları belirterek, çağrı yığınlarını kullanıcı olmayan kod olarak değerlendirilecek işlevleri belirtebilirsiniz `*.natjmc` dosyaları.  
  
- Kullanıcı dışı kod için Visual Studio makinenin tüm kullanıcıları belirtmek için .natjmc dosyaya ekleyin `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` klasör.  
  
- Bir kullanıcı için kullanıcı olmayan kod belirtmek için .natjmc dosyaya ekleyin `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` klasör.  
  
  Bu sözdizimi ile xml dosyaları .natjmc dosyalar şunlardır:  
  
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
|`Name`|Gerekli. Modül veya modülleri tam yolu. Windows joker karakterler kullanabilirsiniz `?` (sıfır veya bir karakter) ve `*` (sıfır veya daha fazla karakter). Örneğin,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> Tüm modüllerdeki değerlendirilecek hata ayıklayıcıya bildirir `\3rdParty\UtilLibs` harici kod olarak herhangi bir sürücüdeki.|  
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
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Kullanıcı ve kullanıcı olmayan kod  
 **Kod sınıflandırmaları**  
  
 JavaScript yalnızca kendi kodum, bu sınıflandırmaları birinde kod gruplayarak adımlama ve çağrı yığını görüntü denetimleri:  
  
|||  
|-|-|  
|**MyCode**|Sahibi olduğunuz ve denetlediğiniz kullanıcı kodu.|  
|**LibraryCode**|Kullanıcı olmayan kod düzenli olarak kullandığınız kitaplıklar ve uygulamanızın doğru şekilde (örneğin WinJS veya jQuery) çalışması için kullanır.|  
|**UnrelatedCode**|Yoksa uygulamanız ancak, çalışıyor olabilir, kullanıcı dışı kod sahibi ve uygulamanızın doğru şekilde (örneğin, reklam görüntüleyen bir reklam SDK) çalışabilmesi için şirket doğrudan içermez. Windows Store projeleri, HTTP veya HTTPS URI uygulamanızdan yüklenen herhangi bir kod da UnrelatedCode kabul edilir.|  
  
 JavaScript hata ayıklayıcı, aşağıdaki kod türleri otomatik olarak sınıflandırır:  
  
- Ana bilgisayar tarafından sağlanan için bir dize geçirerek yürütülen betik `eval` işlevi olarak sınıflandırılmış **MyCode**.  
  
- Bir dizeye geçirerek yürütülen betik `Function` Oluşturucu olarak sınıflandırılmış **LibraryCode**.  
  
- WinJS ya da Azure SDK'sı gibi bir çerçeve başvurusu yer alan komut dosyası olarak sınıflandırılmış **LibraryCode**.  
  
- Bir dizeye geçirerek yürütülen betik `setTimeout`, `setImmediate`, veya `setInterval` işlevleri olarak sınıflandırılmış **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Diğer tüm Visual Studio JavaScript projeleri için kullanıcı ve kullanıcı olmayan kod belirtir.  
  
  Varsayılan sınıflandırmalar değiştirmek ve belirli dosyaları sınıflandırabilir ve URL'leri ile adlı bir .json dosyası eklemek `mycode.json` bir projesinin kök klasörüne.  
  
  Diğer tüm kod olarak sınıflandırılır **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Atlama davranışını  
  
-   Bir işlev kullanıcı değilse (**MyCode**) kodu **içine adımla** (klavye kısayolu: F11) gibi davranır **Step Over** (klavye: F10).  
  
-   Bir adım kullanıcı olmayan başlıyorsa (**LibraryCode** veya **UnrelatedCode**) kod geçici olarak Adımlamayı yalnızca kendi kodum etkin değilse gibi davranır. Kullanıcı koda geri, yalnızca kendi kodum adım hemen sonra Adımlama tekrar etkinleştirilecektir.  
  
-   Bir adım olduğunda (örneğin, bir olay işleyicisi son satırının bir adımda yapılması) geçerli yürütme bağlamı bırakarak kullanıcı kodu sonuçları hata ayıklayıcı kullanıcı kodunun yürütülen sonraki satıra durdurur. Örneğin, bir geri çağırmayı yürütür, **LibraryCode** kodu hata ayıklayıcının kullanıcı kodun sonraki satırına yürütülene kadar devam eder.  
  
-   **Step Out** (klavye: Shift + F11) kullanıcı kodun sonraki satırında durdurur. Hiç kullanıcı kodu karşılaşıldıktan sonra yürütülmeye kadar uygulama çıkar, bir kesme noktasına isabet ya da bir özel durum oluşur.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Kesme noktası davranışı  
  
-   Herhangi bir kod ayarlanan kesme noktaları kod sınıflandırmasını bağımsız olarak her zaman erişilecektir  
  
-   Varsa `debugger` anahtar sözcüğü karşılaştı:  
  
    -   **LibraryCode** kod, hata ayıklayıcı her zaman keser.  
  
    -   **UnrelatedCode** olmayan kod, hata ayıklayıcıyı durdurun.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Özel durum davranışını  
 İşlenmeyen bir özel durum oluşması halinde:  
  
- **MyCode** veya **LibraryCode** kod, hata ayıklayıcı her zaman keser.  
  
- **UnrelatedCode** kodunu ve **MyCode** veya **LibraryCode** çağrı yığını, hata ayıklayıcı kesmesi kodudur.  
  
  İlk fırsat özel durumlar, özel durum iletişim kutusunda özel durum için etkinleştirilir ve özel durumun **LibraryCode** veya **UnrelatedCode** kod:  
  
- Özel durumun işlenip, hata ayıklayıcı sonu gelmez.  
  
- Özel durum işlenmezse hata ayıklayıcı keser.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Yalnızca kendi kodum özelleştirme  
 Kullanıcı ve kullanıcı dışı kod için tek bir Visual Studio Proje sınıflandırmak için adlandırılmış bir .json dosyası eklemek `mycode.json` projesinin kök klasörüne.  
  
 Sınıflandırmalar, bu sırada gerçekleştirilir:  
  
1. Varsayılan sınıflandırmalar  
  
2. Sınıflandırmaları `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` dosyası  
  
3. Sınıflandırmaları `mycode. json` geçerli projenin dosya.  
  
   Her sınıflandırma adım, önceki adımlarda geçersiz kılar. Bir .json dosyası tüm anahtar-değer çiftlerinin listesinde gerekmez ve **MyCode**, **kitaplıkları**, ve **Unrelated** değerler, boş bir dizi olabilir.  
  
   My Code .json dosyaları, bu sözdizimini kullanın:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Değerlendirme, işlevi hem de ScriptBlock**  
  
 **Eval**, **işlevi**, ve **ScriptBlock** anahtar-değer çiftlerinin belirlemek nasıl dinamik olarak oluşturulan kod sınıflandırılmış.  
  
|||  
|-|-|  
|**Değerlendirme**|Ana bilgisayar tarafından sağlanan için bir dize geçirerek yürütülen betik `eval` işlevi. Varsayılan olarak, Eval betik olarak sınıflandırılır **MyCode**.|  
|**İşlevi**|Bir dizeye geçirerek yürütülen betik `Function` Oluşturucusu. Varsayılan olarak, işlev betik olarak sınıflandırılır **LibraryCode**.|  
|**ScriptBlock**|Bir dizeye geçirerek yürütülen betik `setTimeout`, `setImmediate`, veya `setInterval` işlevleri. Varsayılan olarak, ScriptBlock betik olarak sınıflandırılır **UnrelatedCode**.|  
  
 Bu anahtar sözcüklerden biri için değer değiştirebilirsiniz:  
  
- `MyCode`  betik olarak sınıflandırır **MyCode**.  
  
- `Library`  betik olarak sınıflandırır **LibraryCode**.  
  
- `Unrelated`  betik olarak sınıflandırır **UnrelatedCode**.  
  
  **MyCode, kitaplıklar ve ilgisiz**  
  
  **MyCode**, **kitaplıkları**, ve **Unrelated** anahtar-değer çiftlerinin bir sınıflandırma dahil etmek istediğiniz dosyaları ve URL'leri belirtin:  
  
|||  
|-|-|  
|**MyCode**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **MyCode**.|  
|**Kitaplıkları**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **LibraryCode**.|  
|**İlişkisiz**|Bir dizi olarak sınıflandırılan dosyalar veya URL'ler **UnrelatedCode**.|  
  
 Url veya dosya dizesi, bir veya daha fazla içerebilir `*` karakter sıfır veya daha fazla karakterini eşleştirin. `*` normal ifadenin eşdeğeri `.*`.





