---
title: MSBuild ayrılmış ve tanınmış özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f121701ff5d463c852f386f012fe22a7a46d43e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225413"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild Ayrılmış ve Tanınmış Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası hakkında bilgi depolayan önceden tanımlanmış özellikler kümesi sağlar ve [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ikili dosyaları. Bu özellikler diğer aynı şekilde değerlendirilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özellikleri. Örneğin, kullanılacak `MSBuildProjectFile` özelliği, yazdığınız `$(MSBuildProjectFile)`.  
  
 MSBuild ayrılmış ve iyi bilinen özelliklerin ön tanımlamasında aşağıdaki tabloda değerleri kullanır. Ayrılmış özellikler geçersiz kılınamaz, ancak iyi bilinen özellikler proje dosyasında aynı adlı ortam özellikleri, genel özellikleri veya, bildirilen özellikleri kullanarak geçersiz kılınabilir.  
  
## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve Tanınmış Özellikler  
 Aşağıdaki tabloda açıklanmıştır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özellikleri önceden tanımlanmış.  
  
|Özellik|Açıklama|Ayrılmış veya iyi bilinen|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Klasörün mutlak yolu burada [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] şu anda kullanılmakta olan ikili dosyaların bulunduğu (örneğin, C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Dosyalara başvurmanız gerekiyorsa bu özellik yararlıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dizin.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|Ayrılmış|  
|`MSBuildExtensionsPath`|.NET Framework 4 ile geldi: varsayılan değerleri arasında fark yoktur `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`. Ortam değişkeni ayarlayabilirsiniz `MSBUILDLEGACYEXTENSIONSPATH` varsayılan değerinin davranışını etkinleştirmek için bir null olmayan değere `MSBuildExtensionsPath` önceki sürümlerinde.<br /><br /> .NET Framework 3.5 ve önceki sürümlerde varsayılan değerini `MSBuildExtensionsPath` Files\ veya \Program Files (x86) klasörü, geçerli işlemin bit düzeyine bağlı olarak altındaki MSBuild alt klasörünün yoluna işaret eder. Örneğin, bir 64-bit makinedeki 32-bit işlem için bu özellik \Program dosyaları (x86) klasörünü işaret eder. Bir 64-bit makinedeki 64-bit işlem için bu özellik \Program dosyaları klasörünü işaret eder.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları yerleştirmek için kullanışlı bir yerdir. Örneğin hedef dosyalarınız \Program Files\MSBuild\MyFiles\Northwind.targets yüklenebilir ve ardından bu XML kodu kullanılarak proje dosyalarında alınan:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|İyi bilinen|  
|`MSBuildExtensionsPath32`|Yolu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] \Program Files veya \Program Files (x86) klasörü altında alt. Bu yol her zaman \Program ve 32-bit makinedeki 32-bit \Program Files klasöründeki bir 64-bit makinedeki dosyaları (x86) gösteriyor. Ayrıca bkz: `MSBuildExtensionsPath` ve `MSBuildExtensionsPath64`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|İyi bilinen|  
`MSBuildExtensionsPath64`|Yolu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] \Program Files klasörü altındaki alt. Bir 64 bit makine için bu yol her zaman \Program dosyaları klasörünü işaret eder. Bir 32-bit makine için bu yol boştur. Ayrıca bkz: `MSBuildExtensionsPath` ve `MSBuildExtensionsPath32`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|İyi bilinen|  
|`MSBuildLastTaskResult`|`true` önceki görev hatasız (uyarı durumunda bile), tamamladıysanız veya `false` önceki görev hatasız tamamlanırsa. Genellikle bir görevde bir hata oluştuğunda hata o projede gerçekleşen son şeydir oluşur. Bu nedenle, bu özelliğin değeri hiçbir zaman olan `false`, aşağıdaki senaryolar dışında:<br /><br /> - `ContinueOnError` Özniteliği [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md) ayarlanır `WarnAndContinue` (veya `true`) veya `ErrorAndContinue`.<br /><br /> - `Target` Sahip bir [OnError öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md) alt öğesi olarak.|Ayrılmış|  
|`MSBuildNodeCount`|Oluştururken kullanılan eş zamanlı işlemlerin en fazla sayısı. Bu için belirttiğiniz değerdir **/maxcpucount** komut satırında. Belirttiyseniz **/maxcpucount** sonra bir değer belirtmeden `MSBuildNodeCount` bilgisayara işlemci sayısını belirtir. Daha fazla bilgi için [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md) ve [paralel birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Ayrılmış|  
|`MSBuildProgramFiles32`|32 bit program klasörünün konumunu; Örneğin, `C:\Program Files (x86)`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|Ayrılmış|  
|`MSBuildProjectDefaultTargets`|Belirtilen hedeflerin tam listesi `DefaultTargets` özniteliği `Project` öğesi. Örneğin, aşağıdaki `Project` öğesinin bir `MSBuildDefaultTargets` özelliği değerinin `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Ayrılmış|  
|`MSBuildProjectDirectory`|Proje dosyasının bulunduğu, örneğin dizinin mutlak yolu `C:\MyCompany\MyProduct`.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|Ayrılmış|  
|`MSBuildProjectDirectoryNoRoot`|Değerini `MSBuildProjectDirectory` kök sürücü hariç, özellik.<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|Ayrılmış|  
|`MSBuildProjectExtension`|Nokta dahil, proje dosyasının dosya adı uzantısı; Örneğin, .proj.|Ayrılmış|  
|`MSBuildProjectFile`|Proje dosyasının dosya adı uzantısı dahil olmak üzere tam dosya adı; Örneğin, MyApp.proj.|Ayrılmış|  
|`MSBuildProjectFullPath`|Mutlak yol ve dosya adı uzantısı dahil olmak üzere proje dosyasının tam dosya adı; Örneğin, C:\MyCompany\MyProduct\MyApp.proj.|Ayrılmış|  
|`MSBuildProjectName`|Dosya adı uzantısı olmadan proje dosyasının dosya adı; Örneğin, MyApp.|Ayrılmış|  
|`MSBuildStartupDirectory`|Klasörün mutlak yolu burada [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çağrılır. Bu özelliği kullanarak, bir proje ağacındaki belirli bir noktaya altındaki her şey her dizinde dirs.proj dosyaları oluşturmadan oluşturabilirsiniz. Bunun yerine, yalnızca bir projeniz vardır; burada gösterildiği gibi örneğin c:\traversal.proj:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağaçtaki herhangi bir noktada oluşturmak için şunu yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özellikte son test eğik çizgiyi eklemeyin.|Ayrılmış|  
|`MSBuildThisFile`|Dosya adı ve dosya uzantısı kısmı `MSBuildThisFileFullPath`.|Ayrılmış|  
|`MSBuildThisFileDirectory`|Öğesinin dizin bölümü `MSBuildThisFileFullPath`.<br /><br /> Yola son test eğik çizgi içerir.|Ayrılmış|  
|`MSBuildThisFileDirectoryNoRoot`|Öğesinin dizin bölümü `MSBuildThisFileFullPath`, kök sürücü hariç.<br /><br /> Yola son test eğik çizgi içerir.|Ayrılmış|  
|`MSBuildThisFileExtension`|Dosya adı uzantısı kısmı `MSBuildThisFileFullPath`.|Ayrılmış|  
|`MSBuildThisFileFullPath`|Çalışan hedefi içeren proje veya hedefler dosyasının mutlak yolu.<br /><br /> İpucu: Hedefler dosyası ve özgün proje dosyası değil göre olan hedefler dosyasındaki göreli bir yol belirtebilirsiniz.|Ayrılmış|  
|`MSBuildThisFileName`|Dosya adı kısmı `MSBuildThisFileFullPath`, dosya adı uzantısı olmadan.|Ayrılmış|  
|`MSBuildToolsPath`|Yükleme yolunun [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] değeriyle ilişkili sürümü `MSBuildToolsVersion`.<br /><br /> Yola son eğik çizgiyi dahil değildir.<br /><br /> Bu özellik geçersiz kılınamaz.|Ayrılmış|  
|`MSBuildToolsVersion`|Sürümü [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Projeyi derlemek için kullanılan bir araç takımıdır.<br /><br /> Not: Bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevleri, hedefler ve bir uygulama oluşturmak için kullanılan araçları araçlardan oluşur. Araçlar csc.exe ve vbc.exe gibi derleyicileri içerir. Daha fazla bilgi için [araç takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), ve [standart ve özel araç takımı yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md).|Ayrılmış|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md) [MSBuild özellikleri](msbuild-properties1.md)



