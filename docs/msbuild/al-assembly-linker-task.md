---
title: AL (derleme bağlayıcı) görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a9c2a362a27c24daf1802482ed7a52d9f1d0f2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824394"
---
# <a name="al-assembly-linker-task"></a>AL (derleme bağlayıcı) görevi
AL görevi sarmalar *AL.exe*, ile dağıtılmış bir aracı [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Bu derleme bağlayıcı aracı, bir modül olan bir veya daha fazla veya kaynak dosyalar bildiriminden bir derleme oluşturmak için kullanılır. Bu görevi doğrudan kullanmak için gerekli değildir, dolayısıyla derleyicileri ve geliştirme ortamlarını zaten bu özellikleri sağlayabilir. Assembly Linker, karma dil geliştirme üretilen gibi birden çok bileşen dosyalarından tek bir derleme oluşturmak gereken geliştiriciler için yararlıdır. Bu görev, bir tek derleme dosyasına modülleri birleştirmek değil; tek tek modüllerinin hala dağıtılmış ve doğru bir şekilde yüklemek oluşturulan derleme için kullanılabilir olmalıdır. Daha fazla bilgi için *AL.exe*, bkz: [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).  

## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `AL` görev.  


| Parametre | Açıklama |
|---------------------| - |
| `AlgorithmID` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme bildirimini içeren dosya hariç, çok dosyalı bir derlemede tüm dosyaları karma yapmak için bir algoritma belirtir. Daha fazla bilgi için belgelerine bakın `/algid` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> Çalışma zamanında kullanıcının bilgisayarına DLL yüklenecek adresi belirtir. İşlem alanında DLL'lerin yerini işletim sistemi izin vermek yerine DLL'lerin temel adresini belirtirseniz, uygulamaları daha hızlı yüklenir. Bu parametre için / Base karşılık gelen[adresi](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Company` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/comp[any]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Configuration` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/config[uration]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Copyright` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/copy[right]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme ile ilişkilendirilecek için kültür dizeyini belirtir. Daha fazla bilgi için belgelerine bakın `/c[ulture]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true` derlemeye yalnızca ortak anahtar yerleştirmek için; `false` derlemeyi tam imzalamak için. Daha fazla bilgi için belgelerine bakın `/delay[sign]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Description` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/descr[iption]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Belirtilen kaynaklar derleme bildirimini içeren görüntüde katıştırır. Bu görevi, görüntüye kaynak dosyasının içeriğini kopyalar. Bu parametreye geçirilen öğe bağlı adlı isteğe bağlı meta verilerine de sahip `LogicalName` ve `Access`. `LogicalName` Meta veri kaynağı için iç tanımlayıcı belirtmek için kullanılır.  `Access` Meta verileri ayarlanabilir `private` kaynağın diğer derlemeler tarafından görülmemesini sağlamak için. Daha fazla bilgi için belgelerine bakın `/embed[resource]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtilen dosya, kaynak adını taşıyan derlemesine katıştırır `Security.Evidence`.<br /><br /> Kullanamazsınız `Security.Evidence` normal kaynaklar için. Bu parametre için karşılık gelen `/e[vidence]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | İsteğe bağlı `Int32` çıkış parametresi salt okunur.<br /><br /> Yürütülen komutun tarafından sağlanan çıkış kodu belirtir. |
| `FileVersion` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `File Version` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/fileversion` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir değer belirtir `Flags` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/flags` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Görev bir hata iletisinde bildirilen dosyalar için mutlak yolu kullanmak neden olur. Bu parametre için karşılık gelen `/fullpaths` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar (ona tanımlayıcı ad verir). Görev, ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için belgelerine bakın `/keyn[ame]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Bir derlemeyi imzalamak için bir anahtar çifti veya yalnızca ortak anahtar içeren bir dosyayı belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için belgelerine bakın `/keyf[ile]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Belirtilen kaynak dosyalarını bir derlemeye bağlar. Kaynak derlemenin parçası haline gelir, ancak dosya kopyalanmaz. Bu parametreye geçirilen öğe bağlı adlı isteğe bağlı meta verilerine de sahip `LogicalName`, `Target`, ve `Access`. `LogicalName` Meta veri kaynağı için iç tanımlayıcı belirtmek için kullanılır. `Target` Meta verileri, görev kopyalar sonra derlendiğinden bu yeni dosyayı bir derlemeye dosyanın dosya adı ve yolunu belirtebilirsiniz. `Access` Meta verileri ayarlanabilir `private` kaynağın diğer derlemeler tarafından görülmemesini sağlamak için. Daha fazla bilgi için belgelerine bakın `/link[resource]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> Tam nitelikli adını belirtir (*sınıf.yöntem biçimindeki*) yönteminin bir modülü çalıştırılabilir bir dosyaya dönüştürürken giriş noktası olarak kullanın. Bu parametre için karşılık gelen `/main` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dosya adını belirtir. Bu parametre için karşılık gelen `/out` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Bu kodu çalıştırmak hangi platformu sınırlar; biri olmalıdır `x86`, `Itanium`, `x64`, veya `anycpu`. Varsayılan, `anycpu` değeridir. Bu parametre için karşılık gelen `/platform` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Product` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/prod[uct]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `ProductVersion` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/productv[ersion]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | İsteğe bağlı `String[]` parametresi.<br /><br /> Assembly Linker için geçişine yönelik ek seçenekler içeren yanıt dosyaları belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametresi.<br /><br /> Resgen.exe gibi SDK Araçları yolunu belirtir. |
| `SourceModules` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bir bütünleştirilmiş kod içine derlenmiş için bir veya daha fazla modül. Modüller, elde edilen derlemeyi bildiriminde listelenen ve dağıtılmış ve kullanılabilir durumda derlemeyi yüklenmeye gerekir. Bu parametrede aktarılan öğeleri olarak adlandırılan ek meta verilerine de sahip `Target`, görev kopyalar sonra derlendiğinden bu yeni dosyayı bir derlemeye dosyanın dosya adı ve yolunu belirtir. Daha fazla bilgi için belgelerine bakın [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Bu parametre yöntemlere geçirilen modüller listesinde karşılık gelen *Al.exe* belirli bir anahtar olmadan. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir: `library` (kod kitaplığı) `exe` (konsol uygulaması), veya `win` (Windows tabanlı uygulama). Varsayılan, `library` değeridir. Bu parametre için karşılık gelen `/t[arget]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | İsteğe bağlı `String` parametresi.<br /><br /> Kültür alanı dışında tüm derleme meta devralmak derleme belirtir. Belirtilen derleme tanımlayıcı bir ada sahip olmalıdır.<br /><br /> İle oluşturduğunuz derleme `TemplateFile` parametresi, bir uydu derleme olacaktır. Bu parametre için karşılık gelen `/template` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | İsteğe bağlı `Int32` parametresi.<br /><br /> Sonra yürütülebilir görev sonlandırıldığından, milisaniye cinsinden süre miktarını belirtir. Varsayılan değer `Int.MaxValue`, hiçbir zaman aşımı süresi olduğunu gösterir. |
| `Title` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Title` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/title` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | İsteğe bağlı `String` parametresi.<br /><br /> Görev temel yürütülebilir dosya (Al.exe) burada yükleyecek konumu belirtir. Bu parametre belirtilmezse görev çalışıyor framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | İsteğe bağlı `String` parametresi.<br /><br /> İçin bir dize belirtir `Trademark` derlemesi içindeki alan. Daha fazla bilgi için belgelerine bakın `/trade[mark]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | İsteğe bağlı `String` parametresi.<br /><br /> Bu derlemenin sürüm bilgilerini belirtir. Dize biçimi *major.minor.build.revision*. Varsayılan değer 0’dır. Daha fazla bilgi için belgelerine bakın `/v[ersion]` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> Ekler bir *.ico* derlemesindeki dosya. *.İco* dosya çıktı dosyasına dosya Gezgini'nde istenen görünümü verir. Bu parametre için karşılık gelen `/win32icon` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | İsteğe bağlı `String` parametresi.<br /><br /> Bir Win32 kaynağı ekler (*.res* dosya) çıkış dosyasına. Daha fazla bilgi için belgelerine bakın `/win32res` seçeneğini [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.ToolTask> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [ToolTaskExtension taban sınıfı](../msbuild/tooltaskextension-base-class.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirtilen seçeneklerle bir derleme oluşturur.  

```xml  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  

    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  

    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)