---
title: Vbc görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ed9563f4149b550e123cf74a09f19245514fe97
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281868"
---
# <a name="vbc-task"></a>Vbc Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yürütülebilir dosyalar (.exe), dinamik bağlantı kitaplığı (.dll) veya modülleri (.netmodule) oluşturan vbc.exe sarmalar. Vbc.exe hakkında daha fazla bilgi için bkz. [Visual Basic komut satırı derleyicisi](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `Vbc` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalLibPaths`|İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuruları özniteliğinde belirtilen derlemeleri aramak, ek klasörleri belirtir.|  
|`AddModules`|İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın. Bu parametre için karşılık gelen [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) vbc.exe derleyicisinin anahtar.|  
|`BaseAddress`|İsteğe bağlı `String` parametresi.<br /><br /> DLL temel adresini belirtir. Bu parametre için karşılık gelen [/baseaddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) vbc.exe derleyicisinin anahtar.|  
|`CodePage`|İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre için karşılık gelen [/CODEPAGE](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) vbc.exe derleyicisinin anahtar.|  
|`DebugType`|İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin hata ayıklama bilgisi oluşturmasına neden olur. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer `full`, çalışan programa hata ayıklayıcı ekleme sağlar. Değerini `pdbonly` programın Hata Ayıklayıcısı'nda başlatılır, ancak yalnızca çalışan programa hata ayıklayıcıya iliştirildiğinde derleme dil kodu görüntüler kaynak kodda hata ayıklama sağlar. Daha fazla bilgi için [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|İsteğe bağlı `String[]` parametresi.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgüllerle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Bu parametre için karşılık gelen [/ define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) vbc.exe derleyicisinin anahtar.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev derlemede ortak anahtarı yerleştirir. Varsa `false`, görev derleme tam olarak imzalar. Varsayılan değer `false`. Bu parametre ile birlikte kullanılmadığı sürece hiçbir etkisi olmaz `KeyFile` parametresi veya `KeyContainer` parametresi. Bu parametre için karşılık gelen [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) vbc.exe derleyicisinin anahtar.|  
|`DisabledWarnings`|İsteğe bağlı `String` parametresi.<br /><br /> Belirtilen Uyarıları bastırır. Uyarı tanımlayıcısının sayısal parçası belirtmeniz yeterlidir. Çoklu uyarılar noktalı virgül ile ayrılır. Bu parametre için karşılık gelen [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) vbc.exe derleyicisinin anahtar.|  
|`DocumentationFile`|İsteğe bağlı `String` parametresi.<br /><br /> Belge yorumlarını belirtilen XML dosyasına işler. Bu parametre geçersiz kılar `GenerateDocumentation` özniteliği. Daha fazla bilgi için [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev, hata ayıklama bilgisi üretir ve bir .pdb dosyasına yerleştirir. Daha fazla bilgi için [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|İsteğe bağlı `String` parametresi.<br /><br /> Görev iç derleyici hatalarını nasıl raporlayacağını belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Varsa `prompt` belirtilir ve derleyici iç hatası oluşur, kullanıcı hata verileri Microsoft'a göndermeyi wheter seçeneği ile istenir.<br /><br /> Varsa `send` belirtilir ve derleyici iç hatası oluşur, görev hata verilerini Microsoft'a gönderir.<br /><br /> Varsayılan değer `none`, yalnızca çıkış metin hataları bildirir.<br /><br /> Bu parametre için karşılık gelen [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) vbc.exe derleyicisinin anahtar.|  
|`FileAlignment`|İsteğe bağlı `Int32` parametresi.<br /><br /> , Çıktı dosyasının bölümlerinin hizalanacağı yeri bayt cinsinden belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre için karşılık gelen [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) vbc.exe derleyicisinin anahtar.|  
|`GenerateDocumentation`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, belgelendirme bilgilerini üretir ve yürütülebilir dosya veya görev oluşturulurken kitaplık adıyla bir XML dosyasına yerleştirir. Daha fazla bilgi için [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Belirtilen öğe koleksiyonlardan ad alanlarını alır. Bu parametre için karşılık gelen [/Imports](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) vbc.exe derleyicisinin anahtar.|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtar kapsayıcısı adını belirtir. Bu parametre corresonds için [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) vbc.exe derleyicisinin anahtar.|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|İsteğe bağlı [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametre.<br /><br /> "9" veya "10", dil sürümünü belirtir.|  
|`LinkResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur. kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre için karşılık gelen [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) vbc.exe derleyicisinin anahtar.|  
|`MainEntryPoint`|İsteğe bağlı `String` parametresi.<br /><br /> Sınıf veya içeren modül belirtir `Sub Main` yordamı. Bu parametre corresonds için [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) vbc.exe derleyicisinin anahtar.|  
|`ModuleAssemblyName`|İsteğe bağlı `String` parametresi.<br /><br /> Bu modül bir parçası olan derlemeyi belirtir.|  
|`NoConfig`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici nezahrnovat dosya kullanmamalıdır belirtir. Bu parametre için karşılık gelen [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) parametre vbc.exe derleyicisinin.|  
|`NoLogo`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici başlık bilgilerinin görüntülenmesini bastırır. Bu parametre için karşılık gelen [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) vbc.exe derleyicisinin anahtar.|  
|`NoStandardLib`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Standart kitaplıkları başvuruda bulunmamaya derleyici neden olur. Bu parametre için karşılık gelen [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) vbc.exe derleyicisinin anahtar.|  
|`NoVBRuntimeReference`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Yalnızca iç kullanım. TRUE ise Microsoft.VisualBasic.dll otomatik başvurusunu engeller...|  
|`NoWarnings`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev tüm uyarıları bastırır. Daha fazla bilgi için [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici iyileştirmelerini sağlar. Bu parametre için karşılık gelen [/ optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) vbc.exe derleyicisinin anahtar.|  
|`OptionCompare`|İsteğe bağlı `String` parametresi.<br /><br /> Dize karşılaştırmaları nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer `binary` görev ikili dize karşılaştırmaları kullandığını belirtir. Değer `text` görevi metin dize karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary`. Bu parametre için karşılık gelen [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) vbc.exe derleyicisinin anahtar.|  
|`OptionExplicit`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, değişkenleri açık bildirimini gereklidir. Bu parametre için karşılık gelen [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) vbc.exe derleyicisinin anahtar.|  
|`OptionInfer`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, değişkenlerin tür çıkarımı sağlar.|  
|`OptionStrict`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, kesin türü anlamları örtük tür dönüştürmelerini sınırlamak için görev zorlar. Bu parametre için karşılık gelen [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) vbc.exe derleyicisinin anahtar.|  
|`OptionStrictType`|İsteğe bağlı `String` parametresi.<br /><br /> Hangi katı türü anlamları bir uyarı üretir belirtir. Şu anda yalnızca "özel" desteklenir. Bu parametre için karşılık gelen [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) vbc.exe derleyicisinin anahtar.|  
|`OutputAssembly`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Bu parametre için karşılık gelen [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) vbc.exe derleyicisinin anahtar.|  
|`Platform`|İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformu belirtir. Bu parametre değerini alabilir `x86`, `x64`, `Itanium`, veya `anycpu`. Varsayılan değer `anycpu`. Bu parametre için karşılık gelen [/Platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) vbc.exe derleyicisinin anahtar.|  
|`References`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Geçerli projenin içine belirtilen öğelerden genel tür bilgileri aktarmak görev neden olur. Bu parametre için karşılık gelen [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) vbc.exe derleyicisinin anahtar.|  
|`RemoveIntegerChecks`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tamsayı taşma hatası denetimlerini devre dışı bırakır. Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) vbc.exe derleyicisinin anahtar.|  
|`Resources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> .NET Framework kaynak çıkış dosyasına katıştırır. Bu parametre için karşılık gelen [/Resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) vbc.exe derleyicisinin anahtar.|  
|`ResponseFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bu görev için komutları içeren bir yanıt dosyası belirtir. Bu parametre için karşılık gelen [@ (yanıt dosyası belirtme)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) vbc.exe derleyicisinin seçeneği.|  
|`RootNamespace`|İsteğe bağlı `String` parametresi.<br /><br /> Tür bildirimleri tüm kök ad alanını belirtir. Bu parametre için karşılık gelen [/RootNamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) vbc.exe derleyicisinin anahtar.|  
|`SdkPath`|İsteğe bağlı `String` parametresi.<br /><br /> Mscorlib.dll'nin ve Microsoft.VisualBasic.dll'nin konumunu belirtir. Bu parametre için karşılık gelen [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) vbc.exe derleyicisinin anahtar.|  
|`Sources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir veya daha fazla belirtir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kaynak dosyaları.|  
|`TargetCompactFramework`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev hedefleri [!INCLUDE[Compact](../includes/compact-md.md)]. Bu anahtara karşılık gelen [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) vbc.exe derleyicisinin anahtar.|  
|`TargetType`|İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir. Bu parametre değerini alabilir `library`, bir kod kitaplığı oluşturur `exe`, bir konsol uygulaması oluşturan `module`, bir modül oluşturur veya `winexe`, bir Windows programı oluşturur. Varsayılan değer `library`. Bu parametre için karşılık gelen [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) vbc.exe derleyicisinin anahtar.|  
|`Timeout`|İsteğe bağlı `Int32` parametresi.<br /><br /> Sonra yürütülebilir görev sonlandırıldığından, milisaniye cinsinden süre miktarını belirtir. Varsayılan değer `Int.MaxValue`, hiçbir zaman aşımı süresi olduğunu gösterir.|  
|`ToolPath`|İsteğe bağlı `String` parametresi.<br /><br /> Görev temel yürütülebilir dosya (vbc.exe) burada yükleyecek konumu belirtir. Bu parametre belirtilmezse görev çalışıyor framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm uyarıları hata olarak kabul edilir. Daha fazla bilgi için [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|İsteğe bağlı `Boolean` parametresi.<br /><br /> İşlem içi derleyici nesnesini kullanmasına görev varsa bildirir. Yalnızca kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre için karşılık gelen [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) vbc.exe derleyicisinin anahtar.|  
|`Verbosity`|İsteğe bağlı `String` parametresi.<br /><br /> Derleyicisinin çıktısının ayrıntı düzeyini belirtir. Ayrıntı olabilir `Quiet`, `Normal` (varsayılan) veya `Verbose`.|  
|`WarningsAsErrors`|İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilecek uyarıların bir listesini belirtir. Daha fazla bilgi için [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Bu parametre geçersiz kılar `TreatWarningsAsErrors` parametresi.|  
|`WarningsNotAsErrors`|İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak görülmeyen uyarıların bir listesini belirtir. Daha fazla bilgi için [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Bu parametre yalnızca yararlıdır, `TreatWarningsAsErrors` parametrenin ayarlanmış `true`.|  
|`Win32Icon`|İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasına dosya Gezgini'nde istenen görünümü verir derlemede bir .ico simge dosyası ekler. Bu parametre için karşılık gelen [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) vbc.exe derleyicisinin anahtar.|  
|`Win32Resources`|İsteğe bağlı `String` parametresi.<br /><br /> Bir Win32 kaynağı (.res) dosyası çıkış dosyasına ekler. Bu parametre için karşılık gelen [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) vbc.exe derleyicisinin anahtar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek derleyen bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] proje.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



