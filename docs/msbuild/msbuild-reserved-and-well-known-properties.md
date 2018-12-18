---
title: MSBuild ayrılmış ve tanınmış özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50bb5a21f93368533a6514cdaf19a7b88486eb06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894488"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild ayrılmış ve tanınmış özellikleri
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Proje dosyası hakkında bilgi depolayan önceden tanımlanmış özellikler kümesi sağlar ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ikili dosyaları. Bu özellikler diğer aynı şekilde değerlendirilir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] özellikleri. Örneğin, kullanılacak `MSBuildProjectFile` özelliği, yazdığınız `$(MSBuildProjectFile)`.  

 MSBuild ayrılmış ve iyi bilinen özelliklerin ön tanımlamasında aşağıdaki tabloda değerleri kullanır. Ayrılmış özellikler geçersiz kılınamaz, ancak iyi bilinen özellikler proje dosyasında aynı adlı ortam özellikleri, genel özellikleri veya, bildirilen özellikleri kullanarak geçersiz kılınabilir.

## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve tanınmış özellikleri  
 Aşağıdaki tabloda açıklanmıştır [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] özellikleri önceden tanımlanmış.  


| Özellik | Ayrılmış veya iyi bilinen | Açıklama |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Ayrılmış | Klasörün mutlak yolu burada [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] şu anda kullanılmakta olan ikili dosyaların bulunduğu (örneğin, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber >*). Dosyalara başvurmanız gerekiyorsa bu özellik yararlıdır [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dizin.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildExtensionsPath` | İyi bilinen | .NET Framework 4 ile geldi: varsayılan değerleri arasında fark yoktur `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`. Ortam değişkeni ayarlayabilirsiniz `MSBUILDLEGACYEXTENSIONSPATH` varsayılan değerinin davranışını etkinleştirmek için bir null olmayan değere `MSBuildExtensionsPath` önceki sürümlerinde.<br /><br /> .NET Framework 3.5 ve önceki sürümlerde varsayılan değerini `MSBuildExtensionsPath` altındaki MSBuild alt klasörünün yoluna işaret *\Program dosyaları\\*  veya *\Program dosyaları (x86)* klasörü Geçerli işlemin bit düzeyine bağlı olarak. Örneğin, bir 64-bit makinedeki 32-bit işlem için bu özelliği işaret *\Program dosyaları (x86)* klasör. Bu özellik bir 64-bit makinedeki 64-bit işlem için işaret *\Program dosyaları* klasör.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları yerleştirmek için kullanışlı bir yerdir. Örneğin hedef dosyalarınız, yüklenebilir *\Program Files\MSBuild\MyFiles\Northwind.targets* ve ardından bu XML kodu kullanılarak proje dosyalarının içeri aktarıldı:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | İyi bilinen | Yolu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altında alt *\Program dosyaları* veya *\Program dosyaları (x86)* klasör. Bu yol her zaman 32-bit işaret *\Program dosyaları* 32-bit makinedeki klasörü ve *\Program dosyaları (x86)* 64-bit makinedeki. Ayrıca bkz: `MSBuildExtensionsPath` ve `MSBuildExtensionsPath64`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildExtensionsPath64` | İyi bilinen | Yolu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altında alt *\Program dosyaları* klasör. Bir 64 bit makine için bu yol her zaman işaret *\Program dosyaları* klasör. Bir 32-bit makine için bu yol boştur. Ayrıca bkz: `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildLastTaskResult` | Ayrılmış | `true` önceki görev hatasız (uyarı durumunda bile), tamamladıysanız veya `false` önceki görev hatasız tamamlanırsa. Genellikle bir görevde bir hata oluştuğunda hata o projede gerçekleşen son şeydir oluşur. Bu nedenle, bu özelliğin değeri hiçbir zaman olan `false`, aşağıdaki senaryolar dışında:<br /><br /> - `ContinueOnError` Özniteliği [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md) ayarlanır `WarnAndContinue` (veya `true`) veya `ErrorAndContinue`.<br /><br /> - `Target` Sahip bir [OnError öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md) alt öğesi olarak. |
| `MSBuildNodeCount` | Ayrılmış | Oluştururken kullanılan eş zamanlı işlemlerin en fazla sayısı. Bu için belirttiğiniz değerdir **- maxcpucount** komut satırında. Belirttiyseniz **- maxcpucount** sonra bir değer belirtmeden `MSBuildNodeCount` bilgisayara işlemci sayısını belirtir. Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md) ve [paralel olarak birden çok proje derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Ayrılmış | 32 bit program klasörünün konumunu; Örneğin, *C:\Program Files (x86)*.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildProjectDefaultTargets` | Ayrılmış | Belirtilen hedeflerin tam listesi `DefaultTargets` özniteliği `Project` öğesi. Örneğin, aşağıdaki `Project` öğesinin bir `MSBuildDefaultTargets` özelliği değerinin `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Ayrılmış | Proje dosyasının bulunduğu, örneğin dizinin mutlak yolu *C:\MyCompany\MyProduct*.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildProjectDirectoryNoRoot` | Ayrılmış | Değerini `MSBuildProjectDirectory` kök sürücü hariç, özellik.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildProjectExtension` | Ayrılmış | Nokta dahil, proje dosyasının dosya adı uzantısı; Örneğin, *.proj*. |
| `MSBuildProjectFile` | Ayrılmış | Proje dosyasının dosya adı uzantısı dahil olmak üzere tam dosya adı; Örneğin, *MyApp.proj*. |
| `MSBuildProjectFullPath` | Ayrılmış | Mutlak yol ve dosya adı uzantısı dahil olmak üzere proje dosyasının tam dosya adı; Örneğin, *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Ayrılmış | Dosya adı uzantısı olmadan proje dosyasının dosya adı; Örneğin, *MyApp*. |
| `MSBuildRuntimeType` | Ayrılmış | Şu anda yürüten çalışma zamanının türü. MSBuild 15 ' kullanıma sunuldu. Değer (MSBuild 15) önce tanımlanmamış `Full` MSBuild Masaüstü .NET Framework üzerinde çalışan belirten `Core` MSBuild, .NET Core üzerinde çalıştığı belirten veya `Mono` MSBuild Mono üzerinde çalıştığı belirten. |
| `MSBuildStartupDirectory` | Ayrılmış | Klasörün mutlak yolu burada [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çağrılır. Bu özelliği kullanarak, bir proje ağacındaki belirli bir noktaya altındaki her şeyi oluşturmadan oluşturabileceğinizi  *\<dizin > .proj* her dizindeki dosyaları. Bunun yerine, yalnızca bir projeniz vardır; örneğin, *c:\traversal.proj*, burada gösterildiği gibi:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağaçtaki herhangi bir noktada oluşturmak için şunu yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin. |
| `MSBuildThisFile` | Ayrılmış | Dosya adı ve dosya uzantısı kısmı `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Ayrılmış | Öğesinin dizin bölümü `MSBuildThisFileFullPath`.<br /><br /> Yola son test eğik çizgi içerir. |
| `MSBuildThisFileDirectoryNoRoot` | Ayrılmış | Öğesinin dizin bölümü `MSBuildThisFileFullPath`, kök sürücü hariç.<br /><br /> Yola son test eğik çizgi içerir. |
| `MSBuildThisFileExtension` | Ayrılmış | Dosya adı uzantısı kısmı `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Ayrılmış | Çalışan hedefi içeren proje veya hedefler dosyasının mutlak yolu.<br /><br /> İpucu: Hedefler dosyası ve özgün proje dosyası değil göre olan hedefler dosyasındaki göreli bir yol belirtebilirsiniz. |
| `MSBuildThisFileName` | Ayrılmış | Dosya adı kısmı `MSBuildThisFileFullPath`, dosya adı uzantısı olmadan. |
| `MSBuildToolsPath` | Ayrılmış | Yükleme yolunun [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] değeriyle ilişkili sürümü `MSBuildToolsVersion`.<br /><br /> Yola son eğik çizgiyi dahil değildir.<br /><br /> Bu özellik geçersiz kılınamaz. |
| `MSBuildToolsVersion` | Ayrılmış | Sürümü [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Projeyi derlemek için kullanılan bir araç takımıdır.<br /><br /> Not: Bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevleri, hedefler ve bir uygulama oluşturmak için kullanılan araçları araçlardan oluşur. Araçlar gibi derleyicileri içerir *csc.exe* ve *vbc.exe*. Daha fazla bilgi için [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), ve [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md). |

## <a name="names-that-conflict-with-msbuild-elements"></a>MSBuild öğeleri ile çakışan adlara

Yukarıdakine ek olarak, kullanıcı tanımlı özellikler, öğe veya öğe meta verileri için Dil öğelerini kullanılamaz MSBuild karşılık gelen adları:

* VisualStudioProject
* Hedef
* PropertyGroup
* Çıkış
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* Importgroup
* Bunu seçin
* Ne zaman
* Aksi takdirde

## <a name="see-also"></a>Ayrıca bkz.  
[MSBuild başvurusu](../msbuild/msbuild-reference.md)

[MSBuild özellikleri](../msbuild/msbuild-properties.md)
