---
title: MSBuild görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4d7a296902695007541e4c21c661f659fbbaab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861611"
---
# <a name="msbuild-task"></a>MSBuild görevi
Yapılar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] başka projelerden [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje.  

## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `MSBuild` görev.  


| Parametre | Açıklama |
|-----------------------------------| - |
| `BuildInParallel` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, belirtilen proje `Projects` mümkünse parametresi paralel olarak oluşturulur. Varsayılan değer `false`. |
| `Projects` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Derleme için proje dosyalarını belirtir. |
| `Properties` | İsteğe bağlı `String` parametresi.<br /><br /> Alt projenin genel özellikler olarak uygulamak için özellik ad/değer çiftleri noktalı virgülle ayrılmış listesi. Bu parametreyi belirttiğinizde, işlevsel olarak eşdeğer olan özellikleri ayarlamak **-özellik** ile oluşturduğunuzda geçiş [ *MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Örneğin:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Özellikleri aracılığıyla projenin gönderdiğinizde `Properties` parametresi [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası zaten yüklü olsa bile, projeye yeni bir örneğini oluşturur. Projeye yeni bir örneğini oluştururken [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] farklı genel özellikleri olan ve diğer proje örnekleri ile paralel oluşturulabilir farklı bir proje olarak değerlendirir. Örneğin, bir yayın yapılandırması hata ayıklama yapılandırması ile aynı anda oluşturabilirsiniz. |
| `RebaseOutputs` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, oluşturulmuş projelerdeki öğelere sahip yollarına göre arama projesi olarak ayarlanmış olan göreli yolları hedef çıktı. Varsayılan değer `false`. |
| `RemoveProperties` | İsteğe bağlı `String` parametresi.<br /><br /> Kaldırmak için genel özellikler kümesini belirtir. |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevini çağırır geçirilen listesindeki her bir hedef [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] teker teker yerine aynı anda. Bu parametre ayarını `true` önceden çağrılan hedefleri başarısız olsa bile, sonraki hedefler çağrılan garanti eder. Aksi takdirde, bir yapı hatası tüm sonraki hedefleri çağrılmasını durdurur. Varsayılan değer `false`. |
| `SkipNonexistentProjects` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, disk üzerinde mevcut proje dosyaları atlanacak. Aksi takdirde, bu gibi projeler hataya neden olur. |
| `StopOnFirstFailure` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, bir proje oluşturmak, başarısız olduğunda daha fazla proje oluşturulacaktır. Şu anda bu (ile birden çok işlemci) paralel derlerken desteklenmez. |
| `TargetAndPropertyListSeparators` | İsteğe bağlı `String[]` parametresi.<br /><br /> Hedefleri ve özellikleri olarak listesini belirtir `Project` öğe meta verileri). Ayırıcılar önce işleme kaçılmamış olacaktır. Örneğin % 3B (Atlanan ';') bir kaçılmamış gibi kabul edilir;'. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıkış parametresi.<br /><br /> Oluşturulan hedeflerin çıkışları tüm proje dosyaları döndürür. Yalnızca belirtilen hedef çıkışları döndürüldüğü, hedeflerin bağımlı hedeflerde mevcut olmayan herhangi bir çıkış.<br /><br /> `TargetOutputs` Parametresi, aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Çıkışları ayarlanan hedefi içeren proje dosyası.<br />-   `MSBuildSourceTargetName`: Hedef çıkışları ayarlayın. **Not:** her proje dosyası çıkışları tanımlamak veya ayrı olarak hedef, çalıştırmak istediğiniz varsa `MSBuild` her bir proje dosyası veya hedef için ayrı ayrı görev. Çalıştırırsanız `MSBuild` yalnızca tüm proje dosyaları oluşturmak için hedef çıkışları bir diziye toplandıktan sonra görev. |
| `Targets` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef veya hedefleri, proje dosyalarını oluşturmak için belirtir. Hedef adlarının bir listesini ayırmak için noktalı virgül kullanın. Hiçbir hedef belirtilirse `MSBuild` görev, proje dosyalarında belirtilen varsayılan hedefler oluşturulur. **Not:** hedefleri tüm proje dosyaları içinde gerçekleşmelidir. Aksi takdirde, bir derleme hatası oluşur. |
| `ToolsVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtir `ToolsVersion` bu göreve geçirilen projeler oluşturma sırasında kullanılacak.<br /><br /> Sağlayan bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] farklı bir sürümünü hedefleyen bir proje oluşturmak için görev [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] projede belirtilenden. Geçerli değerler `2.0`, `3.0` ve `3.5`. Varsayılan değer `3.5`. |
| `UnloadProjectsOnCompletion` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, işlem tamamlandıktan sonra projenin yüklemesi kaldırılır. |
| `UseResultsCache` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, önbelleğe alınan sonuç, varsa, döndürülür.<br /><br />  MSBuild görevi çalıştırırsanız, sonuç bir kapsamda konumlandırılmalıdır. <br /><br /> (ProjectFileName GlobalProperties) [TargetNames]<br /><br /> Yapı öğeleri listesi olarak |

## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  

 Kullanarak aksine [Exec görevi](../msbuild/exec-task.md) başlatmak için *MSBuild.exe*, bu görevi ndedir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] alt projeleri oluşturmak için işlem. Atlanabilir zaten oluşturulmuş hedefleri listesinde, üst ve alt yapı arasında paylaşılır. Bu görevi de olduğundan daha hızlıdır yeni [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] işlem oluşturulur.  

 Bu görevi yalnızca proje dosyalarını aynı zamanda çözüm dosyalarını işleyebilir.  

 Gerekli herhangi bir yapılandırma [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri aynı zamanda, yapılandırmayı uzak oluşsa da etkinleştirmek için (örneğin, bağlantı noktaları, protokolleri, zaman aşımı, yeniden denemeler vb.), altyapıyı kullanarak yapılandırılabilir yapılmalıdır bir yapılandırma dosyası. Mümkün olduğunda, yapılandırma öğeleri görev parametreleri üzerinde belirtilmesi erişebiliyor olmalısınız `MSBuild` görev.  

 Başlayarak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, çözüm projeleri artık surface TargetOutputs tüm yapıların alt projeleri.  

## <a name="pass-properties-to-projects"></a>Projelere özellikleri geçirme  
 Sürümlerinde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] öncesinde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] farklı geçirme 3.5, listelenen farklı projelere özelliklerini ayarlar [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] öğesi zor. Özellikleri öznitelik kullandıysanız [MSBuild görevi](../msbuild/msbuild-task.md), ayarına, toplu sürece oluşturulan projeleri tümüne uygulanan sonra [MSBuild görevi](../msbuild/msbuild-task.md) ve koşullu olarak farklı sağlanan öğe listesi her proje için özellikleri.  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, Bununla birlikte, iki yeni meta veri öğeleri, Özellikler ayrılmış ve farklı özellikleri farklı geçirmek için esnek bir şekilde sağladığınız AdditionalProperties projeleri durdurulmasını sağlar kullanılarak oluşturulan [MSBuild görevi](../msbuild/msbuild-task.md).  

> [!NOTE]
>  Bu yeni meta veri öğeleri projeleri özniteliğinde geçirilen öğelere uygulanabilir [MSBuild görevi](../msbuild/msbuild-task.md).  

## <a name="multi-processor-build-benefits"></a>Birden çok işlemcili derlemenin avantajları  
 Çok işlemcili bir sistemde projelerinizi paralel oluşturduğunuzda bu yeni meta veriler kullanmanın en önemli avantajlarından biri gerçekleşir. Meta veriler, tüm projeleri bir tek birleştirmenize olanak tanır [MSBuild görevi](../msbuild/msbuild-task.md) arama herhangi toplu işleme yapmak zorunda veya koşul olmadan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevleri. Ve yalnızca tek bir çağırdığınızda [MSBuild görevi](../msbuild/msbuild-task.md), tüm projeleri öznitelikte listelenen projeleri paralel olarak derlenir. (Ancak, yalnızca, `BuildInParallel=true` özniteliği mevcut [MSBuild görevi](../msbuild/msbuild-task.md).) Daha fazla bilgi için [paralel olarak birden çok proje derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  

## <a name="properties-metadata"></a>Özellikler meta verisi  
 Kullanarak birden çok çözüm dosyalarını oluştururken sık karşılaşılan bir senaryodur [MSBuild görevi](../msbuild/msbuild-task.md), yalnızca farklı derleme yapılandırmalarında kullanarak. Çözüm a1 oluşturmak isteyebilir hata ayıklama yapılandırması ve çözüm a2 kullanarak sürüm yapılandırmasını kullanarak. İçinde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, bu proje dosyasını aşağıdaki gibi görünür:  

> [!NOTE]
>  Aşağıdaki örnekte, "..." ek çözüm dosyalarını temsil eder.  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  

 Özellikler meta verileri kullanarak, ancak, tek bir kullanmak için bunu basitleştirebilirsiniz [MSBuild görevi](../msbuild/msbuild-task.md)aşağıdaki gösterildiği gibi:  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  

 \- veya -  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln..."/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  

## <a name="additionalproperties-metadata"></a>AdditionalProperties meta verisi  
 Burada oluşturduğunuz iki çözüm dosyalarını kullanarak aşağıdaki senaryoyu göz önünde bulundurun [MSBuild görevi](../msbuild/msbuild-task.md), her iki sürüm yapılandırmasını kullanarak, ancak bir x86 kullanarak mimarisi ve diğer IA64 mimari kullanarak. İçinde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, birden çok örneğini oluşturma gerekir [MSBuild görevi](../msbuild/msbuild-task.md): ile x86 sürüm yapılandırmasını kullanarak Projeyi derlemek için bir mimari, diğer sürüm yapılandırmasını IA64 ile kullanma Mimari. Proje dosyanız aşağıdaki gibi görünür:  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  

 AdditionalProperties meta verileri kullanarak, tek bir kullanmak için bunu basitleştirebilirsiniz [MSBuild görevi](../msbuild/msbuild-task.md) aşağıdakileri kullanarak:  

### <a name="aproj"></a>a.proj  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `MSBuild` tarafından belirtilen projeleri oluşturmak için görev `ProjectReferences` öğe koleksiyonu. Sonuçta elde edilen hedef çıkışları depolanır `AssembliesBuiltByChildProjects` öğe koleksiyonu.  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  

    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  

</Project>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)