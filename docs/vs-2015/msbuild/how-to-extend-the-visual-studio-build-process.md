---
title: 'Nasıl yapılır: derleme işlemini genişletme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e552b75ea5ba34004d0c53850f1af77a120b20cb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050263"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl Yapılır: Visual Studio Derleme İşlemini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yapı işlemi bir dizi tarafından tanımlanan [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyanıza içe aktarılan .targets dosyaları. Microsoft.Common.targets, içeri aktarılan bu dosyaların bir yapı işleminde bazı noktalarda özel görevleri çalıştırmanıza olanak tanır şekilde genişletilebilir. Bu konu, genişletmek için kullanabileceğiniz iki yöntem açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] derleme işlemi:

-   Microsoft.Common.targets içinde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma.

-   Microsoft.Common.targets içinde tanımlanan "DependsOn" özelliklerini geçersiz kılma.

## <a name="overriding-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma
 Microsoft.Common.targets dosya önce ve sonra yapı işleminin ana hedeflerin bazıları adlı önceden tanımlanmış boş hedefleri kümesini içerir. Örneğin, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çağrıları `BeforeBuild` ana önce hedef `CoreBuild` hedef ve `AfterBuild` sonra hedef `CoreBuild` hedef. Varsayılan olarak, Microsoft.common.targets'ı boş hedeflerin hiçbir şey yapma, ancak Microsoft.Common.targets içe aktaran bir proje dosyasında istediğiniz hedefler tanımlayarak kendi varsayılan davranışı geçersiz kılabilirsiniz. Bunu yaptığınızda kullanabilirsiniz [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yapı işlemi hakkında daha fazla denetime size görevleri.

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz Microsoft.Common.targets içinde önceden tanımlanmış bir hedef belirleyin. Güvenli bir şekilde geçersiz kılabilirsiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.

2. Hemen önce hedef veya hedefleri, proje dosyasının sonunda tanımlamak `</Project>` etiketi. Örneğin:

   ```
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

3. Proje dosyası oluşturun.

   Aşağıdaki tabloda tüm hedefleri güvenli bir şekilde geçersiz kılabilirsiniz Microsoft.Common.targets içinde gösterir.

|Hedef Adı|Açıklama|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedefler birinde eklenen görevler, önce veya çekirdek derleme tamamlandıktan sonra çalışır. Çoğu özelleştirmeleri, bu iki hedefi birinde gerçekleştirilir.|
|`BeforeBuild`, `AfterBuild`|Bu hedefler birinde eklenen görevler önce veya sonra yapı diğer her şey çalışır. **Not:** `BeforeBuild` ve `AfterBuild` hedefleri sonunda, çoğu proje dosyalarını açıklamalardaki önceden tanımlanır. Bu proje dosyanıza öncesi ve derleme sonrası olayları kolayca eklemenizi sağlar.|
|`BeforeRebuild`, `AfterRebuild`|Görevleri önce çalıştırması şu hedeflerinden birini eklenebilir veya çekirdek yeniden oluşturduktan sonra işlevi çağrılır. Microsoft.Common.targets içinde hedef yürütme sırası: `BeforeRebuild`, `Clean`, `Build`, ardından `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Önce bu hedefler birinde eklenen görevleri çalıştırmak veya çekirdek sonra temiz işlevi çağrılır.|
|`BeforePublish`, `AfterPublish`|Görevleri önce çalıştırması şu hedeflerinden birini eklenebilir veya çekirdek işlevselliğini yayımladığınızda çağrılır.|
|`BeforeResolveReference`, `AfterResolveReferences`|Bu hedefler birinde eklenen görevler, önce ya da derleme başvurularını çözüldükten sonra çalışır.|
|`BeforeResGen`, `AfterResGen`|Bu hedefler birinde eklenen görevler, önce veya kaynak oluşturulduktan sonra çalışır.|

## <a name="overriding-dependson-properties"></a>"DependsOn" özelliklerini geçersiz kılma
 Önceden tanımlanmış hedefleri geçersiz kılma derleme işlemini genişletme için kolay bir yol olduğunu ancak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hedefleri tanımını ardışık olarak değerlendirir projenizi hedefleri geçersiz kılmasını içeri aktarır. başka bir proje önlemek için bir yolu yoktur, zaten silmiş. Bunu, örneğin, son `AfterBuild` sonra diğer tüm projeleri içe aktarılmış, yapı sırasında kullanılan bir proje dosyasında tanımlanmış hedefi.

 Kullanılan "DependsOn" özellikleri geçersiz kılarak hedefleri istenmeyen geçersiz kılmaları karşı önleyebilirsiniz `DependsOnTargets` Microsoft.Common.targets dosyası boyunca öznitelikleri. Örneğin, `Build` hedefi içeren bir `DependsOnTargets` öznitelik değerini `"$(BuildDependsOn)"`. Göz önünde bulundurun:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Bu XML parçası önce belirten `Build` hedef çalışma zamanı, tüm hedefler belirtilen `BuildDependsOn` özelliği ilk çalıştırmalısınız. `BuildDependsOn` Özelliği olarak tanımlanır:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Adlı başka bir özellik bildirerek bu özellik değerini geçersiz kılabilirsiniz `BuildDependsOn` , proje dosyasının sonunda. Önceki ekleyerek `BuildDependsOn` özelliği yeni özelliği, yeni hedefleri başına hem de hedef listesinin sonuna ekleyebilirsiniz. Örneğin:

```
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

#### <a name="to-override-a-dependson-property"></a>"DependsOn" özelliği geçersiz kılmak için

1.  Önceden tanımlanmış bir "DependsOn" özelliği geçersiz kılmak istediğiniz Microsoft.Common.targets içinde tanımlayın. Yaygın olarak geçersiz kılınan "DependsOn" özelliklerinin bir listesi için aşağıdaki tabloya bakın.

2.  Özellik veya özellikleri, proje dosyasının sonunda başka bir örneğini tanımlar. Özgün özelliği, örneğin `$(BuildDependsOn)`, yeni özellik de.

3.  Önce veya sonra özellik tanımı özel hedeflerinizi tanımlayın.

4.  Proje dosyası oluşturun.

### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak geçersiz kılınan "DependsOn" özellikleri

|Özellik adı|Açıklama|
|-------------------|-----------------|
|`BuildDependsOn`|Önce veya sonra tüm derleme işlemi özel hedefleri eklemek istiyorsanız geçersiz kılmak için özellik.|
|`CleanDependsOn`|Derleme işlemi özel çıkışı Temizle istiyorsanız geçersiz kılmak için özellik.|
|`CompileDependsOn`|Özel işlemler önce veya sonra derleme adımı eklemek istiyorsanız geçersiz kılmak için özellik.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md) [MSBuild kavramları](../msbuild/msbuild-concepts.md) [. MSBuild](../msbuild/msbuild-dot-targets-files.md)
