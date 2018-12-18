---
title: CSC görevi | Microsoft Docs
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
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 657535e73294508ac59330cd379c1c6bd192a0b2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237386"
---
# <a name="csc-task"></a>Csc Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
CSC.exe sarmalar ve yürütülebilir dosyalar (.exe dosyaları), dinamik bağlantı kitaplığı (.dll dosyaları) veya modülleri (.netmodule dosyaları) üretir. CSC.exe hakkında daha fazla bilgi için bkz: [C# Derleyici Seçenekleri](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `Csc` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalLibPaths`|İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için [/lib (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|İsteğe bağlı `String` parametresi.<br /><br /> Derlemenin bir parçası olarak bir veya daha fazla modül belirtir. Daha fazla bilgi için [/addmodule (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, kullanan kodu derler [güvenli](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) anahtar sözcüğü. Daha fazla bilgi için [/ unsafe (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|İsteğe bağlı `String` parametresi.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir.|  
|`BaseAddress`|İsteğe bağlı `String` parametresi.<br /><br /> Bir DLL yüklemek için tercih edilen temel adresini belirtir. Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı. Daha fazla bilgi için [/baseaddress (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Tamsayı veri türü sınırları taşıyor, aritmetik çalışma zamanında bir özel durum neden olup olmayacağını belirtir. Daha fazla bilgi için [/ checked (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için [/codepage (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` olabilir `full` veya `pdbonly`. Varsayılan `full`, bir hata ayıklayıcı çalışan bir programa eklenmesi sağlar. Belirtme `pdbonly` etkinleştirir kaynak hata ayıklama kodu programın Hata Ayıklayıcısı'nda başlatılır, ancak çalışan programa hata ayıklayıcıya bağlı olduğu assembler yalnızca görüntüler.<br /><br /> Bu parametre geçersiz kılar `EmitDebugInformation` parametresi.<br /><br /> Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|İsteğe bağlı `String` parametresi.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için [/ define (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tam olarak imzalı bir derleme istediğinizi belirtir. Varsa `false`, yalnızca derleme içinde ortak anahtar yerleştirmek istediğinizi belirtir.<br /><br /> Bu parametre ile birlikte kullanılmadığı sürece hiçbir etkisi olmaz `KeyFile` veya `KeyContainer` parametresi.<br /><br /> Daha fazla bilgi için [/delaysign (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|İsteğe bağlı `String` parametresi.<br /><br /> Devre dışı bırakılması uyarıların bir listesini belirtir. Daha fazla bilgi için [/nowarn (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|İsteğe bağlı `String` parametresi.<br /><br /> Belge yorumlarını bir XML dosyasına işler. Daha fazla bilgi için [/doc (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, görev, hata ayıklama bilgisi üretir ve bir program veritabanı (.pdb) dosyasına yerleştirir. Varsa `false`, hiçbir hata ayıklama bilgisi görev yayar. Varsayılan değer `false`. Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|İsteğe bağlı `String` parametresi.<br /><br /> Bir C# iç hata Microsoft'a bildirmek için kullanışlı bir yol sağlar. Bu parametre değerini alabilir `prompt`, `send`, veya `none`. Parametre ayarlanırsa `prompt`, derleyici iç hatası oluştuğunda bir ileti alacaksınız. Bir hata raporu elektronik olarak Microsoft'a istemi sağlar. Parametre ayarlanırsa `send`, bir hata raporu otomatik olarak gönderilir. Parametre ayarlanırsa `none`, yalnızca derleyicinin metin çıktısı hata bildirilir. Varsayılan değer `none`. Daha fazla bilgi için [/errorreport (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|İsteğe bağlı `Int32` parametresi.<br /><br /> Bölüm boyutu, çıkış dosyasında belirtir. Daha fazla bilgi için [/filealign (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici çıktısında dosyanın mutlak yolunu belirtir. Varsa `false`, dosyasının adını belirtir. Varsayılan değer `false`. Daha fazla bilgi için [/fullpaths (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtar kapsayıcısı adını belirtir. Daha fazla bilgi için [/keycontainer (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için [/keyfile (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için [/langversion (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir bağlantı oluşturur bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] kaynak çıkış dosyasına; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametrede aktarılan öğeleri adlı isteğe bağlı meta veri girdileri olabilir `LogicalName` ve `Access`. `LogicalName` karşılık gelen `identifier` parametresinin `/linkresource` geçiş, ve `Access` karşılık gelen `accessibility-modifier` parametresi. Daha fazla bilgi için [/linkresource (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|İsteğe bağlı `String` parametresi.<br /><br /> Konumunu belirtir `Main` yöntemi. Daha fazla bilgi için [/Main (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|İsteğe bağlı `String` parametresi.<br /><br /> Bu modül bir parçası olacağı derlemenin adını belirtir.|  
|`NoConfig`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyiciye ile csc.rsp dosyasını derleme değil. Daha fazla bilgi için [/noconfig (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, derleyici başlık bilgilerinin görüntülenmesini bastırır. Daha fazla bilgi için [/nologo (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm sistem ad alanını tanımlayan mscorlib.dll alma engeller. Tanımlayın veya kendi sistem ad alanı ve nesneler oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için [/nostdlib (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, varsayılan Win32 bildirimini içermez.|  
|`Optimize`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, iyileştirmeler sağlar. Varsa `false`, iyileştirmeleri devre dışı bırakır. Daha fazla bilgi için [/ optimize (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Daha fazla bilgi için [/out (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama bilgi dosyası adını belirtir. .Pdb uzantısına sahip çıkış dosyası adı varsayılan addır.|  
|`Platform`|İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformu belirtir. Bu parametre değerini alabilir `x86`, `x64`, veya `anycpu`. Varsayılan değer `anycpu`. Daha fazla bilgi için [/Platform (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Geçerli projenin içine belirtilen öğelerden genel tür bilgileri aktarmak görev neden olur. Daha fazla bilgi için [/Reference (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Belirtebileceğiniz bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] başvuru diğer adı içinde bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] meta veriler ekleyerek dosya `Aliases` özgün "Başvuru" öğe. Örneğin, diğer ad aşağıdaki CSC komut satırında "LS1" ayarlamak için şunu yazın:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> kullanın:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Katıştıran bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] çıkış dosyasına kaynak.<br /><br /> Bu parametrede aktarılan öğeleri adlı isteğe bağlı meta veri girdileri olabilir `LogicalName` ve `Access`. `LogicalName` karşılık gelen `identifier` parametresinin `/resource` geçiş, ve `Access` karşılık gelen `accessibility-modifier` parametresi. Daha fazla bilgi için [/Resource (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için komutları içeren bir yanıt dosyası belirtir. Daha fazla bilgi için [@ (yanıt dosyası belirtme)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir veya daha fazla belirtir [!INCLUDE[csprcs](../includes/csprcs-md.md)] kaynak dosyaları.|  
|`TargetType`|İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir. Bu parametre değerini alabilir `library`, bir kod kitaplığı oluşturur `exe`, bir konsol uygulaması oluşturan `module`, bir modül oluşturur veya `winexe`, bir Windows programı oluşturur. Varsayılan değer `library` şeklindedir. Daha fazla bilgi için [/target (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, tüm uyarıları hata olarak değerlendirir. Daha fazla bilgi için [/warnaserror (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|İsteğe bağlı `Boolean` parametresi.<br /><br /> İşlem içi derleyici nesnesini kullanmasına görev varsa bildirir. Yalnızca kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Daha fazla bilgi için [/utf8output (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|İsteğe bağlı `Int32` parametresi.<br /><br /> Görüntülenecek derleyici uyarı düzeyini belirtir. Daha fazla bilgi için [/ warn (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilecek uyarıların bir listesini belirtir. Daha fazla bilgi için [/warnaserror (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Bu parametre geçersiz kılar `TreatWarningsAsErrors` parametresi.|  
|`WarningsNotAsErrors`|İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak görülmeyen uyarıların bir listesini belirtir. Daha fazla bilgi için [/warnaserror (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Bu parametre yalnızca yararlıdır, `TreatWarningsAsErrors` parametrenin ayarlanmış `true`.|  
|`Win32Icon`|İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasına dosya Gezgini'nde istenen görünümü verir derlemede bir .ico simge dosyası ekler. Daha fazla bilgi için [/win32icon (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|İsteğe bağlı `String` parametresi.<br /><br /> Dahil edilecek Win32 bildirimi belirtir.|  
|`Win32Resource`|İsteğe bağlı `String` parametresi.<br /><br /> Bir Win32 kaynağı (.res) dosyası çıkış dosyasına ekler. Daha fazla bilgi için [/win32res (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan `Microsoft.Build.Tasks.ManagedCompiler` öğesinden devralan sınıf <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Csc` bir çalıştırılabilir dosyadan kaynak dosyalarında derlemek için görev `Compile` öğe koleksiyonu.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)



