---
title: Toplu hedef işlemede meta veri öğesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486169788ad4533f5d45bf48c979ce3d0f5f7920
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081065"
---
# <a name="item-metadata-in-target-batching"></a>Toplu hedef işlemede öğe meta verileri
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Giriş ve çıkışlarını yapı hedef üzerinde bağımlılık analizleri gerçekleştirmek özelliğine sahiptir. Giriş veya çıkış hedefin güncel olduğunu belirlenirse hedef atlanacak ve derleme devam edecek. `Target` öğeleri kullanın `Inputs` ve `Outputs` bağımlılık analizi sırasında incelemek için öğeleri belirtmek için öznitelikler.  
  
 Bir hedef toplu öğeler giriş veya çıkış, olarak kullanan bir görev içeriyorsa `Target` hedef öğenin de toplu işleme kullanması gereken, `Inputs` veya `Outputs` etkinleştirmek için öznitelikleri [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] maddelerini toplu olarak, zaten güncel olduğundan atlanacak.  
  
## <a name="batch-targets"></a>Toplu iş hedefleri  
 Aşağıdaki örnekte adlı bir öğe listesini içeren `Res` göre iki gruplayın bölünmüş `Culture` öğe meta verileri. Yöntemlere geçirilen her biri bu toplu `AL` bir çıkış derlemesi için her toplu iş oluşturan bir görev. Üzerinde işlem grubu oluşturma kullanılarak `Outputs` özniteliği `Target` öğesi [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] her biri ayrı ayrı toplu işler hedef çalıştırmadan önce güncel olup olmadığını belirleyebilirsiniz. Toplu hedef işlemede kullanmadan hedef yürütülen her zaman her iki maddelerini toplu olarak görev tarafından çalıştırılmaz.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md)   
 [Toplu işleme](../msbuild/msbuild-batching.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Toplu Görev işlemede öğe meta verileri](../msbuild/item-metadata-in-task-batching.md)