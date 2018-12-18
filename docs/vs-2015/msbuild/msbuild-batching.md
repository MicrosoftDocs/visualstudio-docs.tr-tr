---
title: MSBuild toplu işleme | Microsoft Docs
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
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24baafbaf213e90999a5e4e0eea030f2ef608501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304180"
---
# <a name="msbuild-batching"></a>MSBuild Toplu İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listeleri farklı kategorileri veya toplu işlemi bölmek için özelliği, öğe meta verileri temel alarak ve bir hedef veya görevi, her batch ile bir kez çalıştırın.  
  
## <a name="task-batching"></a>Toplu Görev işlemede  
 Toplu Görev işlemede öğe listeleri farklı yığınlara ayırmak ve bu toplu işlerin her bir görevle ayrı olarak geçirmek için bir yol sağlayarak proje dosyalarınızı basitleştirmek sağlar. Bu, bir proje dosyası yalnızca birkaç kez çalıştırılabilir olsa bile görev ve bir kez bildirilen özniteliklerini sahip olması gerektiğini anlamına gelir.  
  
 İstediğinizi belirtin [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevle kullanarak toplu işleme gerçekleştirmek için %(*ItemMetaDataName*) görev özniteliklerinden biri olarak gösterimi. Aşağıdaki örnek böler `Example` toplu iş öğesi listesine dayalı `Color` öğesi meta veri değeri ve geçişleri her toplu `MyTask` ayrı olarak görev.  
  
> [!NOTE]
>  Öğeyi listeden başka bir yerde görev öznitelikleri başvurmadığından veya meta veri adı belirsiz olabilir, kullanabileceğiniz %(*ItemCollection.ItemMetaDataName*) için toplu işlem kullanma için öğe meta veri değeri tam olarak nitelemek için gösterimi.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Toplu işlem daha ayrıntılı örnekler için bkz. [toplu görev işlemede öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Toplu hedef işlemede  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Hedef çalıştırılmadan önce giriş ve çıkışları bir hedefin güncel olup olmadığını denetler. Hem girişler ve çıkışlar güncel olduğundan, hedef atlandı. Toplu işlem, bir hedef içinde bir görevi kullanıyorsa, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] girişler ve çıkışlar öğelerinin her toplu iş için güncel olup olmadığını gerekiyor. Aksi takdirde, isabet her zaman hedef yürütülür.  
  
 Aşağıdaki örnekte gösterildiği bir `Target` öğesini içeren bir `Outputs` özniteliğini %(*ItemMetaDataName*) gösterimi. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bölecek `Example` toplu iş öğesi listesine dayalı `Color` öğe meta verileri ve zaman damgaları ve çıkış dosyalarının her toplu iş için analiz edin. Bir toplu iş çıkışları güncel değilse, hedef çalıştırılır. Aksi takdirde, hedef atlandı.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Toplu hedef işlemede başka bir örnek için bkz. [toplu hedef işlemede öğe meta verileri](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Meta verileri kullanarak özellik işlevleri  
 Toplu işleme, meta verileri içeren özellik işlevleri tarafından denetlenebilir. Örneğin,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 kullanan <xref:System.IO.Path.Combine%2A> bir kök klasör yolu derleme öğe yolu ile birleştirilecek.  
  
 Özellik işlevleri içindeki meta veri değerleri görünmeyebilir.  Örneğin,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 izin verilmiyor.  
  
 Özellik işlevleri hakkında daha fazla bilgi için bkz: [özellik işlevleri](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Itemmetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Gelişmiş Kavramlar](../msbuild/msbuild-advanced-concepts.md)



