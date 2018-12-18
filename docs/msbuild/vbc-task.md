---
title: Vbc görevi | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf2ab82b16d3cdaf493afc15f506dc237e6a91d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937882"
---
# <a name="vbc-task"></a>Vbc görevi
Sarmalar *vbc.exe*, yürütülebilir dosyalar oluşturur (*.exe*), dinamik bağlantı kitaplıklarını (*.dll*), veya kod modüllerini (*.netmodule*). Daha fazla bilgi için *vbc.exe*, bkz: [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index).  

## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `Vbc` görev.  


| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuruları özniteliğinde belirtilen derlemeleri aramak, ek klasörleri belirtir. |
| `AddModules` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın. Bu parametre için karşılık gelen [- addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) geçiş *vbc.exe* derleyici. |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> DLL temel adresini belirtir. Bu parametre için karşılık gelen [- baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) geçiş *vbc.exe* derleyici. |
| `CodePage` | İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre için karşılık gelen [- kod sayfası](/dotnet/visual-basic/reference/command-line-compiler/codepage) geçiş *vbc.exe* derleyici. |
| `DebugType` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin hata ayıklama bilgisi oluşturmasına neden olur. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer `full`, çalışan programa hata ayıklayıcı ekleme sağlar. Değerini `pdbonly` programın Hata Ayıklayıcısı'nda başlatılır, ancak yalnızca çalışan programa hata ayıklayıcıya iliştirildiğinde derleme dil kodu görüntüler kaynak kodda hata ayıklama sağlar. Daha fazla bilgi için [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | İsteğe bağlı `String[]` parametresi.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgüllerle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Bu parametre için karşılık gelen [-tanımlama](/dotnet/visual-basic/reference/command-line-compiler/define) geçiş *vbc.exe* derleyici. |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev derlemede ortak anahtarı yerleştirir. Varsa `false`, görev derleme tam olarak imzalar. Varsayılan değer `false`. Bu parametre ile birlikte kullanılmadığı sürece hiçbir etkisi olmaz `KeyFile` parametresi veya `KeyContainer` parametresi. Bu parametre için karşılık gelen [- delaysıgn](/dotnet/visual-basic/reference/command-line-compiler/delaysign) geçiş *vbc.exe* derleyici. |
| `Deterministic` | İsteğe bağlı `Boolean` parametresi.<br/><br/> Varsa `true`, derleyicinin ikili içeriği aynı derlemeler arasında girişleri aynıysa bir derleme çıktı.<br/><br/>Daha fazla bilgi için [-belirleyici](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtilen Uyarıları bastırır. Uyarı tanımlayıcısının sayısal parçası belirtmeniz yeterlidir. Çoklu uyarılar noktalı virgül ile ayrılır. Bu parametre için karşılık gelen [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) geçiş *vbc.exe* derleyici. |
| `DocumentationFile` | İsteğe bağlı `String` parametresi.<br /><br /> Belge yorumlarını belirtilen XML dosyasına işler. Bu parametre geçersiz kılar `GenerateDocumentation` özniteliği. Daha fazla bilgi için [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev, hata ayıklama bilgisi üretir ve yerleştirir bir *.pdb* dosya. Daha fazla bilgi için [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | İsteğe bağlı `String` parametresi.<br /><br /> Görev iç derleyici hatalarını nasıl raporlayacağını belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Varsa `prompt` belirtilir ve derleyici iç hatası oluşur, bir seçenek olup Microsoft'a hata verileri göndermek ile kullanıcı istenir.<br /><br /> Varsa `send` belirtilir ve derleyici iç hatası oluşur, görev hata verilerini Microsoft'a gönderir.<br /><br /> Varsayılan değer `none`, yalnızca çıkış metin hataları bildirir.<br /><br /> Bu parametre için karşılık gelen [- errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) geçiş *vbc.exe* derleyici. |
| `FileAlignment` | İsteğe bağlı `Int32` parametresi.<br /><br /> , Çıktı dosyasının bölümlerinin hizalanacağı yeri bayt cinsinden belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre için karşılık gelen [- filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) geçiş *vbc.exe* derleyici. |
| `GenerateDocumentation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, belgelendirme bilgilerini üretir ve yürütülebilir dosya veya görev oluşturulurken kitaplık adıyla bir XML dosyasına yerleştirir. Daha fazla bilgi için [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Belirtilen öğe koleksiyonlardan ad alanlarını alır. Bu parametre için karşılık gelen [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) geçiş *vbc.exe* derleyici. |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtar kapsayıcısı adını belirtir. Bu parametre için karşılık gelen [- keycontaıner](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) geçiş *vbc.exe* derleyici. |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için [- keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> "9" veya "10", dil sürümünü belirtir. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur. kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre için karşılık gelen [- linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) geçiş *vbc.exe* derleyici. |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> Sınıf veya içeren modül belirtir `Sub Main` yordamı. Bu parametre için karşılık gelen [-ana](/dotnet/visual-basic/reference/command-line-compiler/main) geçiş *vbc.exe* derleyici. |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Bu modül bir parçası olan derlemeyi belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici kullanmamalısınız belirtir *nezahrnovat* dosya. Bu parametre için karşılık gelen [- noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametresinin *vbc.exe* derleyici. |
| `NoLogo` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici başlık bilgilerinin görüntülenmesini bastırır. Bu parametre için karşılık gelen [- nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) geçiş *vbc.exe* derleyici. |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Standart kitaplıkları başvuruda bulunmamaya derleyici neden olur. Bu parametre için karşılık gelen [- nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) geçiş *vbc.exe* derleyici. |
| `NoVBRuntimeReference` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Yalnızca iç kullanım. TRUE ise otomatik referansı engeller *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev tüm uyarıları bastırır. Daha fazla bilgi için [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici iyileştirmelerini sağlar. Bu parametre için karşılık gelen [-en iyi duruma getirme](/dotnet/visual-basic/reference/command-line-compiler/optimize) geçiş *vbc.exe* derleyici. |
| `OptionCompare` | İsteğe bağlı `String` parametresi.<br /><br /> Dize karşılaştırmaları nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer `binary` görev ikili dize karşılaştırmaları kullandığını belirtir. Değer `text` görevi metin dize karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary`. Bu parametre için karşılık gelen [- optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) geçiş *vbc.exe* derleyici. |
| `OptionExplicit` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, değişkenleri açık bildirimini gereklidir. Bu parametre için karşılık gelen [- optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) geçiş *vbc.exe* derleyici. |
| `OptionInfer` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, değişkenlerin tür çıkarımı sağlar. |
| `OptionStrict` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, kesin türü anlamları örtük tür dönüştürmelerini sınırlamak için görev zorlar. Bu parametre için karşılık gelen [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) geçiş *vbc.exe* derleyici. |
| `OptionStrictType` | İsteğe bağlı `String` parametresi.<br /><br /> Hangi katı türü anlamları bir uyarı üretir belirtir. Şu anda yalnızca "özel" desteklenir. Bu parametre için karşılık gelen [- optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) geçiş *vbc.exe* derleyici. |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Bu parametre için karşılık gelen [-out](/dotnet/visual-basic/reference/command-line-compiler/out) geçiş *vbc.exe* derleyici. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformu belirtir. Bu parametre değerini alabilir `x86`, `x64`, `Itanium`, veya `anycpu`. Varsayılan değer `anycpu`. Bu parametre için karşılık gelen [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) geçiş *vbc.exe* derleyici. |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Geçerli projenin içine belirtilen öğelerden genel tür bilgileri aktarmak görev neden olur. Bu parametre için karşılık gelen [-başvuru](/dotnet/visual-basic/reference/command-line-compiler/reference) geçiş *vbc.exe* derleyici. |
| `RemoveIntegerChecks` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tamsayı taşma hatası denetimlerini devre dışı bırakır. Varsayılan değer `false` şeklindedir. Bu parametre için karşılık gelen [- removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) geçiş *vbc.exe* derleyici. |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> .NET Framework kaynak çıkış dosyasına katıştırır. Bu parametre için karşılık gelen [-kaynak](/dotnet/visual-basic/reference/command-line-compiler/resource) geçiş *vbc.exe* derleyici. |
| `ResponseFiles` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bu görev için komutları içeren bir yanıt dosyası belirtir. Bu parametre için karşılık gelen [@ (yanıt dosyası belirtme)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) seçeneği *vbc.exe* derleyici. |
| `RootNamespace` | İsteğe bağlı `String` parametresi.<br /><br /> Tür bildirimleri tüm kök ad alanını belirtir. Bu parametre için karşılık gelen [- rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) geçiş *vbc.exe* derleyici. |
| `SdkPath` | İsteğe bağlı `String` parametresi.<br /><br /> Konumunu belirtir *mscorlib.dll* ve *microsoft.visualbasic.dll*. Bu parametre için karşılık gelen [- sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) geçiş *vbc.exe* derleyici. |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir veya daha fazla Visual Basic kaynak dosyaları belirtir. |
| `TargetCompactFramework` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev hedefleri [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Bu anahtara karşılık gelen [- netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) geçiş *vbc.exe* derleyici. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir. Bu parametre değerini alabilir `library`, bir kod kitaplığı oluşturur `exe`, bir konsol uygulaması oluşturan `module`, bir modül oluşturur veya `winexe`, bir Windows programı oluşturur. Varsayılan değer `library`. Bu parametre için karşılık gelen [-hedef](/dotnet/visual-basic/reference/command-line-compiler/target) geçiş *vbc.exe* derleyici. |
| `Timeout` | İsteğe bağlı `Int32` parametresi.<br /><br /> Sonra yürütülebilir görev sonlandırıldığından, milisaniye cinsinden süre miktarını belirtir. Varsayılan değer `Int.MaxValue`, hiçbir zaman aşımı süresi olduğunu gösterir. |
| `ToolPath` | İsteğe bağlı `String` parametresi.<br /><br /> Temel alınan yürütülebilir dosya görev burada yükleyecek konumu belirtir (*vbc.exe*). Bu parametre belirtilmezse görev çalışıyor framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm uyarıları hata olarak kabul edilir. Daha fazla bilgi için [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametresi.<br /><br /> İşlem içi derleyici nesnesini kullanmasına görev varsa bildirir. Yalnızca kullanılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre için karşılık gelen [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) geçiş *vbc.exe* derleyici. |
| `Verbosity` | İsteğe bağlı `String` parametresi.<br /><br /> Derleyicisinin çıktısının ayrıntı düzeyini belirtir. Ayrıntı olabilir `Quiet`, `Normal` (varsayılan) veya `Verbose`. |
| `WarningsAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilecek uyarıların bir listesini belirtir. Daha fazla bilgi için [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre geçersiz kılar `TreatWarningsAsErrors` parametresi. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak görülmeyen uyarıların bir listesini belirtir. Daha fazla bilgi için [- warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre yalnızca yararlıdır, `TreatWarningsAsErrors` parametrenin ayarlanmış `true`. |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> Ekler bir *.ico* çıkış dosyası istenen görünümü verir, bütünleştirilmiş kod dosyasında **dosya Gezgini**. Bu parametre için karşılık gelen [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) geçiş *vbc.exe* derleyici. |
| `Win32Resources` | İsteğe bağlı `String` parametresi.<br /><br /> Bir Win32 kaynağı ekler (*.res*) çıktı dosyasına dosya. Bu parametre için karşılık gelen [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) geçiş *vbc.exe* derleyici. |

## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir Visual Basic projesi derler.  

```xml  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
