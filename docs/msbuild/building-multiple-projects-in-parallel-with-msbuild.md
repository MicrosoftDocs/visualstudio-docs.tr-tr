---
title: MSBuild ile paralel olarak birden çok proje oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c375f9af63f1622df995ca28315048f682c1ca4
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879011"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile paralel olarak birden çok proje derleme
Paralel çalıştırarak daha hızlı olan birden çok projeleri derlemek için MSBuild'ı kullanabilirsiniz. Derlemeleri paralel olarak çalıştırmak için çok çekirdekli veya birden çok işlemci bilgisayarda aşağıdaki ayarları kullanın:  
  
-   `-maxcpucount` Geçiş komut isteminde.  
  
-   <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> Bir MSBuild görevi görev parametresi.  
  
> [!NOTE]
>  **-Ayrıntı** (**- v**) bir komut satırı anahtarı da yapı performansını etkiler. Derleme günlüğü bilgilerinizin ayrıntı ayrıntılı kümesi veya sorun giderme için kullanılan tanılama ise, derleme performansı düşebilir. Daha fazla bilgi için [elde derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="-maxcpucount-switch"></a>-maxcpucount anahtarı  
 Kullanırsanız `-maxcpucount` geçiş, veya `-m` kısa için belirtilen sayıda MSBuild oluşturabilirsiniz *MSBuild.exe* paralel olarak çalışan işlemler. Bu işlemler "çalışan işlemleri" olarak da bilinen olan Diğer kullanılabilir işlemci diğer projeler oluşturmak olarak aynı anda bir proje oluşturmak kullanılabilir olduğunda her çalışan işlemi ayrı bir çekirdek veya işlemci kullanır. Örneğin, "4" değeri için bu anahtarı ayarı, projeyi derlemek için dört çalışan işlemler oluşturmak MSBuild neden olur.  
  
 Eklerseniz `-maxcpucount` MSBuild bir değer belirtmeden anahtar için kullanacağı bilgisayarın işlemci sayısı.  
  
 MSBuild 3. 5'kullanıma sunulan bu anahtar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki örnek, üç alt işlemlerin kullanılacak MSBuild bildirir. Bu yapılandırmayı kullanıyorsanız, MSBuild aynı anda üç projeleri oluşturabilirsiniz.  
  
```cmd  
msbuild.exe myproj.proj -maxcpucount:3   
```  

## <a name="buildinparallel-task-parameter"></a>Buildınparallel görev parametresi  
 `BuildInParallel` İsteğe bağlı bir boolean parametre açıktır bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görev. Zaman `BuildInParallel` ayarlanır `true` (varsayılan değeri `false`), aynı anda mümkün olduğunca çok projeleri derlemek için birden çok çalışan işlemi oluşturulur. Bunun düzgün çalışması `-maxcpucount` anahtar ayarlanmalıdır bir değer 1'den büyük ve sistemin en az çift çekirdekli veya iki veya daha fazla işlemciye sahip olmanız gerekir.  
  
 Alınan, bir örneği verilmiştir *microsoft.common.targets*, nasıl ayarlanacağı konusunda `BuildInParallel` parametresi.  
  
```xml  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Projeleri derlemek için birden çok işlemci kullanma](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Birden çok işlemciye duyarlı günlükçüler yazma](../msbuild/writing-multi-processor-aware-loggers.md)   
 [C++ yapı paralellik blog ayarlama](http://go.microsoft.com/fwlink/?LinkId=251457)
