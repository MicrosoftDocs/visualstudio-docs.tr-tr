---
title: Toplu Görev işlemede meta veri öğesi | Microsoft Docs
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
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c117f6864aadd7c981aa2b89302c06ccfd6c9768
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923790"
---
# <a name="item-metadata-in-task-batching"></a>Toplu Görev İşlemede Öğe Meta Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listeleri farklı kategorileri veya toplu işlemi bölmek için özelliği, öğe meta verileri temel alarak ve bir görevi, her batch ile bir kez çalıştırın. Tam olarak hangi batch ile hangi öğeleri geçirilen anlamak kafa karıştırıcı olabilir. Bu konu, toplu işleme içeren aşağıdaki yaygın senaryoları kapsar.  
  
- Bir öğe listesini toplu işler bölme  
  
- Toplu işler çeşitli öğesi listeleri bölme  
  
- Bir öğe aynı anda toplu işleme  
  
- Filtre öğesi listeleri  
  
  İle toplu işlem hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bkz: [toplu işleme](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Bir öğe listesini toplu işler bölme  
 Toplu işleme, öğe meta verileri temel alarak farklı toplu bir öğe listesi bölün ve her toplu işlerin bir görevle ayrı ayrı geçirebilirsiniz olanak tanır. Uydu derlemeleri oluşturmak için kullanışlıdır.  
  
 Aşağıdaki örnek, bir öğe listesi öğesi meta verileri temel alarak gruplayın bölmek gösterilmektedir. `ExampColl` Öğe listesi üç toplu göre bölündüğü `Number` öğe meta verileri. Varlığını `%(ExampColl.Number)`içinde `Text` öznitelik bildirir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] toplu işleme gerçekleştirilmesi. `ExampColl` Öğe listesi üç toplu göre bölündüğü `Number` meta verileri ve her toplu işin geçirilen ayrı olarak görevle.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [İleti görevini](../msbuild/message-task.md) görev aşağıdaki bilgileri görüntüler:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Birden çok öğe bölme yığınlara listeler  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] birden çok öğe listesi, aynı meta verileri temel alarak gruplayın bölebilirsiniz. Bu, farklı öğe listeleri birden çok derleme oluşturmak için yığınlara ayırmak kolaylaştırır. Örneğin, bir öğe listesini bir uygulama toplu bir derleme toplu işlemi ve kaynak dosyaların bir uygulama batch ve bir derleme toplu iş bir öğe listesi bölünmüş .cs dosya olabilir. Bu öğe listeleri bir görevle geçirmek ve hem uygulama hem de derleme oluşturmak için toplu işleme sonra kullanabilirsiniz.  
  
> [!NOTE]
>  Bir göreve geçirilen bir öğe listesi başvurulan meta verilerle hiçbir öğe içeriyorsa, her öğe, öğe listesinde her toplu iş içine geçirilir.  
  
 Aşağıdaki örnek, birden çok öğe listesi öğesi meta verileri temel alarak gruplayın bölme gösterilmektedir. `ExampColl` Ve `ExampColl2` öğesi listeleri her ayrılmıştır göre üç gruplayın `Number` öğe meta verileri. Varlığını `%(Number)`içinde `Text` öznitelik bildirir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] toplu işleme gerçekleştirilmesi. `ExampColl` Ve `ExampColl2` öğesi listeleri göre üç toplu işler halinde bölünmüştür `Number` meta verileri ve her toplu işin geçirilen ayrı olarak görevle.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [İleti görevini](../msbuild/message-task.md) görev aşağıdaki bilgileri görüntüler:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Bir öğe aynı anda toplu işleme  
 Toplu işleme da oluşturulduktan sonra her öğeye atanan tanınmış öğe meta verileri üzerinde gerçekleştirilebilir. Bu, bir koleksiyondaki her öğe için toplu işlem kullanma için bazı meta verileri olacağını garanti eder. `Identity` Meta veri değeri, her öğe için benzersiz olan ve bir öğe listesini her öğe ayrı bir toplu iş ayırma için kullanışlıdır. İyi bilinen öğe meta verileri tam bir listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Aşağıdaki örnek, her bir öğe listesini bir öğe aynı anda toplu olarak gösterilmiştir. Çünkü `Identity` her öğenin meta veri değerini benzersiz `ExampColl` her toplu iş öğesi listesi bir öğe içeren öğe listesi altı toplu işler bölünmüştür. Varlığını `%(Identity)`içinde `Text` öznitelik bildirir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] toplu işleme gerçekleştirilmesi.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [İleti görevini](../msbuild/message-task.md) görev aşağıdaki bilgileri görüntüler:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Filtre öğesi listeler  
 Toplu işleme için bir görev iletmeden önce belirli öğeleri bir öğe listesini filtrelemek için kullanılabilir. Örneğin, filtre `Extension` tanınmış öğe meta veri değeri bir görev yalnızca belirli bir uzantıya sahip dosya çubuğunda çalıştırmanıza olanak sağlar.  
  
 Aşağıdaki örnek, bir öğe listesi, toplu iş öğesi meta verileri temel alarak böler ve bir görevle geçirildiğinde bu toplu filtre uygulamak gösterilmektedir. `ExampColl` Öğe listesi üç toplu göre bölündüğü `Number` öğe meta verileri. `Condition` Görevin özniteliği belirtir, sadece toplu işlemleri ile bir `Number` öğesi meta veri değeri `2` görevle geçirilir  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [İleti görevini](../msbuild/message-task.md) görev aşağıdaki bilgileri görüntüler:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanınmış öğe meta verisi](../msbuild/msbuild-well-known-item-metadata.md)   
 [Öğe unsuru (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Itemmetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Toplu işleme](../msbuild/msbuild-batching.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild Başvurusu](../msbuild/msbuild-reference.md)



