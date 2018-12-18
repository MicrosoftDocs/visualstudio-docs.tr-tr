---
title: Derleme işlemini genişletme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 380933a07636cddd2bc32fb45f14f9b2a65830df
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058278"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl yapılır: Visual Studio derleme işlemini genişletme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yapı işlemi bir dizi tarafından tanımlanan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *.targets* proje dosyanıza aktarmış dosyaları. Dosyaları, bunlardan alınan *Microsoft.Common.targets*, yapı işleminde bazı noktalarda özel görevleri çalıştırmanıza olanak tanır şekilde genişletilebilir. Bu makalede genişletmek için kullanabileceğiniz iki yöntem anlatılmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derleme işlemi:  
  
-   Tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma *Microsoft.Common.targets*.  
  
-   Tanımlanan "DependsOn" özelliklerini geçersiz kılma *Microsoft.Common.targets*.  
  
## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma  
 *Microsoft.Common.targets* dosyası önce ve sonra yapı işleminin ana hedeflerin bazıları çağrılan bir dizi önceden tanımlanmış boş hedef içeriyor. Örneğin, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çağrıları `BeforeBuild` ana önce hedef `CoreBuild` hedef ve `AfterBuild` sonra hedef `CoreBuild` hedef. Varsayılan olarak, boş hedef *Microsoft.Common.targets* hiçbir şey yapma, ancak içe aktaran bir proje dosyasında istediğiniz hedefler tanımlayarak kendi varsayılan davranışı geçersiz kılabilirsiniz *Microsoft.Common.targets*. Kullanabileceğiniz önceden tanımlanmış hedefleri geçersiz kılma [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] yapı işlemi hakkında daha fazla denetime size görevleri.  
  
#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için  
  
1.  Önceden tanımlanmış bir hedef belirleyin *Microsoft.Common.targets* geçersiz kılmak istediğiniz. Güvenli bir şekilde geçersiz kılabilirsiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.  
  
2.  Hemen önce hedef veya hedefleri, proje dosyasının sonunda tanımlamak `</Project>` etiketi. Örneğin:  
  
    ```xml  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Proje dosyası oluşturun.  

Aşağıdaki tabloda tüm hedeflerin gösterir *Microsoft.Common.targets* , güvenli bir şekilde geçersiz kılabilirsiniz.  
  
|Hedef adı|Açıklama|  
|-----------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Bu hedefler birinde eklenen görevler önce veya çekirdek derleme tamamlandıktan sonra çalışır. Çoğu özelleştirmeleri, bu iki hedefi birinde gerçekleştirilir.|  
|`BeforeBuild`, `AfterBuild`|Bu hedefler birinde eklenen görevler önce veya sonra yapı diğer her şey çalışır. **Not:** `BeforeBuild` ve `AfterBuild` hedefleri sonunda öncesi ve derleme sonrası olayları proje dosyanıza kolayca eklemenize olanak sağlayan, çoğu proje dosyaları, açıklamalar içinde zaten tanımlanmıştır.|  
|`BeforeRebuild`, `AfterRebuild`|Bu hedefler önce çalıştırması biriyle eklenen veya çekirdek sonra işlevi yeniden görevleri çağrılır. Hedef yürütme sırası *Microsoft.Common.targets* olduğu: `BeforeRebuild`, `Clean`, `Build`, ardından `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Önce bu hedefler birinde eklenen görevleri çalıştırmak veya çekirdek sonra temiz işlevi çağrılır.|  
|`BeforePublish`, `AfterPublish`|Bu hedefler önce çalıştırması biriyle eklenen veya sonra çekirdek işlevselliğini yayımlama görevleri çağrılır.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Bu hedefler birinde eklenen görevler önce ya da derleme başvurularını çözüldükten sonra çalışır.|  
|`BeforeResGen`, `AfterResGen`|Bu hedefler birinde eklenen görevler önce ya da kaynak oluşturulduktan sonra çalışır.|  
  
## <a name="override-dependson-properties"></a>DependsOn özelliklerini geçersiz kıl  
 Önceden tanımlanmış hedefleri geçersiz kılma derleme işlemini genişletme için kolay bir yol olduğunu ancak, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hedefleri tanımını ardışık olarak değerlendirir projenizi hedefleri geçersiz kılmasını içeri aktarır. başka bir proje önlemek için bir yolu yoktur, zaten silmiş. Bunu, örneğin, son `AfterBuild` sonra diğer tüm projeleri içe aktarılmış, yapı sırasında kullanılan bir proje dosyasında tanımlanmış hedefi.  
  
 Kullanılan DependsOn özelliklerini geçersiz kılarak hedefleri istenmeyen geçersiz kılmaları karşı önleyebilirsiniz `DependsOnTargets` boyunca öznitelikleri *Microsoft.Common.targets* dosya. Örneğin, `Build` hedefi içeren bir `DependsOnTargets` öznitelik değerini `"$(BuildDependsOn)"`. Göz önünde bulundurun:  
  
```xml  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Bu XML parçası önce belirten `Build` hedef çalışma zamanı, tüm hedefler belirtilen `BuildDependsOn` özelliği ilk çalıştırmalısınız. `BuildDependsOn` Özelliği olarak tanımlanır:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Adlı başka bir özellik bildirerek bu özellik değerini geçersiz kılabilirsiniz `BuildDependsOn` , proje dosyasının sonunda. Önceki ekleyerek `BuildDependsOn` özelliği yeni özelliği, yeni hedefleri başına hem de hedef listesinin sonuna ekleyebilirsiniz. Örneğin:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Proje dosyalarını içeri aktaran projeler, yaptığınız özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilirsiniz.  
  
#### <a name="to-override-a-dependson-property"></a>DependsOn özelliği geçersiz kılmak için  
  
1.  Önceden tanımlanmış bir DependsOn özelliği tanımlamak *Microsoft.Common.targets* geçersiz kılmak istediğiniz. Yaygın olarak geçersiz kılınan DependsOn özelliklerinin bir listesi için aşağıdaki tabloya bakın.  
  
2.  Özellik veya özellikleri, proje dosyasının sonunda başka bir örneğini tanımlar. Özgün özelliği, örneğin `$(BuildDependsOn)`, yeni özellik de.  
  
3.  Önce veya sonra özellik tanımı özel hedeflerinizi tanımlayın.  
  
4.  Proje dosyası oluşturun.  
  
### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak geçersiz kılınan DependsOn özellikleri  
  
|Özellik adı|Açıklama|  
|-------------------|-----------------|  
|`BuildDependsOn`|Önce veya sonra tüm derleme işlemi özel hedefleri eklemek istiyorsanız geçersiz kılmak için özellik.|  
|`CleanDependsOn`|Derleme işlemi özel çıkışı Temizle istiyorsanız geçersiz kılmak için özellik.|  
|`CompileDependsOn`|Özel işlemler önce veya sonra derleme adımı eklemek istiyorsanız geçersiz kılmak için özellik.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [.targets dosyaları](../msbuild/msbuild-dot-targets-files.md)