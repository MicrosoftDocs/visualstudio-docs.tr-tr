---
title: CSC görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd360a34c70d3208211b861dae064bd4c5a01595
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832373"
---
# <a name="csc-task"></a>Csc görevi
Sarmalar *csc.exe*, yürütülebilir dosyalar oluşturur (*.exe* dosyaları), dinamik bağlantı kitaplıklarını (*.dll* dosyaları), veya kod modüllerini (*.netmodule* dosyaları). Hakkında daha fazla bilgi için *csc.exe*, bkz: [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index).  

## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `Csc` görev.  


| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için [-lib (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemenin bir parçası olarak bir veya daha fazla modül belirtir. Daha fazla bilgi için [- addmodule (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, kullanan kodu derler [güvenli](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğü. Daha fazla bilgi için [-unsafe (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> Bir DLL yüklemek için tercih edilen temel adresini belirtir. Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ortak dil çalışma zamanı. Daha fazla bilgi için [- baseaddress (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Tamsayı veri türü sınırları taşıyor, aritmetik çalışma zamanında bir özel durum neden olup olmayacağını belirtir. Daha fazla bilgi için [-checked (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için [- codepage (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` olabilir `full` veya `pdbonly`. Varsayılan `full`, bir hata ayıklayıcı çalışan bir programa eklenmesi sağlar. Belirtme `pdbonly` etkinleştirir kaynak hata ayıklama kodu programın Hata Ayıklayıcısı'nda başlatılır, ancak çalışan programa hata ayıklayıcıya bağlı olduğu assembler yalnızca görüntüler.<br /><br /> Bu parametre geçersiz kılar `EmitDebugInformation` parametresi.<br /><br /> Daha fazla bilgi için [-hata ayıklama (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe bağlı `String` parametresi.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için [-tanımlama (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tam olarak imzalı bir derleme istediğinizi belirtir. Varsa `false`, yalnızca derleme içinde ortak anahtar yerleştirmek istediğinizi belirtir.<br /><br /> Bu parametre ile birlikte kullanılmadığı sürece hiçbir etkisi olmaz `KeyFile` veya `KeyContainer` parametresi.<br /><br /> Daha fazla bilgi için [- delaysıgn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe bağlı `Boolean` parametresi.<br/><br/> Varsa `true`, derleyicinin ikili içeriği aynı derlemeler arasında girişleri aynıysa bir derleme çıktı.<br/><br/>Daha fazla bilgi için [-belirleyici (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe bağlı `String` parametresi.<br /><br /> Devre dışı bırakılması uyarıların bir listesini belirtir. Daha fazla bilgi için [- nowarn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe bağlı `String` parametresi.<br /><br /> Belge yorumlarını bir XML dosyasına işler. Daha fazla bilgi için [-doc (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev, hata ayıklama bilgisi üretir ve bir program veritabanı (.pdb) dosyasına yerleştirir. Varsa `false`, hiçbir hata ayıklama bilgisi görev yayar. Varsayılan değer `false`. Daha fazla bilgi için [-hata ayıklama (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe bağlı `String` parametresi.<br /><br /> Bir C# iç hata Microsoft'a bildirmek için kullanışlı bir yol sağlar. Bu parametre değerini alabilir `prompt`, `send`, veya `none`. Parametre ayarlanırsa `prompt`, derleyici iç hatası oluştuğunda bir ileti alacaksınız. Bir hata raporu elektronik olarak Microsoft'a istemi sağlar. Parametre ayarlanırsa `send`, bir hata raporu otomatik olarak gönderilir. Parametre ayarlanırsa `none`, yalnızca derleyicinin metin çıktısı hata bildirilir. Varsayılan değer `none`. Daha fazla bilgi için [- errorreport (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe bağlı `Int32` parametresi.<br /><br /> Bölüm boyutu, çıkış dosyasında belirtir. Daha fazla bilgi için [- filealign (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici çıktısında dosyanın mutlak yolunu belirtir. Varsa `false`, dosyasının adını belirtir. Varsayılan değer `false`. Daha fazla bilgi için [- fullpaths (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtar kapsayıcısı adını belirtir. Daha fazla bilgi için [- keycontaıner (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için [- keyfile (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için [- langversion (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir bağlantı oluşturur bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] kaynak çıkış dosyasına; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametrede aktarılan öğeleri adlı isteğe bağlı meta veri girdileri olabilir `LogicalName` ve `Access`. `LogicalName` karşılık gelen `identifier` parametresinin `/linkresource` geçiş, ve `Access` karşılık gelen `accessibility-modifier` parametresi. Daha fazla bilgi için [- linkresource (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> Konumunu belirtir `Main` yöntemi. Daha fazla bilgi için [-main (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Bu modül bir parçası olacağı derlemenin adını belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyiciye derleme değil *csc.rsp* dosya. Daha fazla bilgi için [- noconfig (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici başlık bilgilerinin görüntülenmesini bastırır. Daha fazla bilgi için [- nologo (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, içe engeller *mscorlib.dll*, tüm sistem ad alanı tanımlar. Tanımlayın veya kendi sistem ad alanı ve nesneler oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için [- nostdlib (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, varsayılan Win32 bildirimini içermez. |
| `Optimize` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, iyileştirmeler sağlar. Varsa `false`, iyileştirmeleri devre dışı bırakır. Daha fazla bilgi için [-(C# Derleyici Seçenekleri) en iyi duruma getirme](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Daha fazla bilgi için [-out (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için [- refonly (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama bilgi dosyası adını belirtir. Çıkış dosya adından varsayılan addır bir *.pdb* uzantısı. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformu belirtir. Bu parametre değerini alabilir `x86`, `x64`, veya `anycpu`. Varsayılan değer `anycpu`. Daha fazla bilgi için [-platform (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Geçerli projenin içine belirtilen öğelerden genel tür bilgileri aktarmak görev neden olur. Daha fazla bilgi için [-başvurusu (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Belirtebileceğiniz bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] başvuru diğer adı içinde bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] meta veriler ekleyerek dosya `Aliases` özgün "Başvuru" öğe. Örneğin, diğer ad aşağıdaki Csc komut satırında "LS1" ayarlamak için şunu yazın:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> kullanın:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Katıştıran bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] çıkış dosyasına kaynak.<br /><br /> Bu parametrede aktarılan öğeleri adlı isteğe bağlı meta veri girdileri olabilir `LogicalName` ve `Access`. `LogicalName` karşılık gelen `identifier` parametresinin `/resource` geçiş, ve `Access` karşılık gelen `accessibility-modifier` parametresi. Daha fazla bilgi için [-kaynak (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için komutları içeren bir yanıt dosyası belirtir. Daha fazla bilgi için [@ (yanıt dosyası belirtme)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir veya daha fazla belirtir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kaynak dosyaları. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir. Bu parametre değerini alabilir `library`, bir kod kitaplığı oluşturur `exe`, bir konsol uygulaması oluşturan `module`, bir modül oluşturur veya `winexe`, bir Windows programı oluşturur. Varsayılan değer `library` şeklindedir. Daha fazla bilgi için [-target (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm uyarıları hata olarak değerlendirir. Daha fazla bilgi için [- warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametresi.<br /><br /> İşlem içi derleyici nesnesini kullanmasına görev varsa bildirir. Yalnızca kullanılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Daha fazla bilgi için [-utf8output (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe bağlı `Int32` parametresi.<br /><br /> Görüntülenecek derleyici uyarı düzeyini belirtir. Daha fazla bilgi için [-warn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilecek uyarıların bir listesini belirtir. Daha fazla bilgi için [- warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre geçersiz kılar `TreatWarningsAsErrors` parametresi. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak görülmeyen uyarıların bir listesini belirtir. Daha fazla bilgi için [- warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca yararlıdır, `TreatWarningsAsErrors` parametrenin ayarlanmış `true`. |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> Ekler bir *.ico* çıkış dosyası istenen görünümü verir, bütünleştirilmiş kod dosyasında **dosya Gezgini**. Daha fazla bilgi için [-win32icon (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | İsteğe bağlı `String` parametresi.<br /><br /> Dahil edilecek Win32 bildirimi belirtir. |
| `Win32Resource` | İsteğe bağlı `String` parametresi.<br /><br /> Bir Win32 kaynağı ekler (*.res*) çıktı dosyasına dosya. Daha fazla bilgi için [-win32res (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan `Microsoft.Build.Tasks.ManagedCompiler` öğesinden devralan sınıf <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Csc` bir çalıştırılabilir dosyadan kaynak dosyalarında derlemek için görev `Compile` öğe koleksiyonu.  

```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
