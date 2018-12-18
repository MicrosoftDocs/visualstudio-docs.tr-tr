---
title: Toplu hedef işlemede meta veri öğesi | Microsoft Docs
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
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 011bb9b738aa135fd14c4dbddfb26f9cea2f7bd1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232694"
---
# <a name="item-metadata-in-target-batching"></a>Toplu Hedef İşlemede Öğe Meta Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Giriş ve çıkışlarını yapı hedef üzerinde bağımlılık analizleri gerçekleştirmek özelliğine sahiptir. Giriş veya çıkış hedefin güncel olduğunu belirlenirse hedef atlanacak ve yapı procede olur. `Target` öğeleri kullanın `Inputs` ve `Outputs` bağımlılık analizi sırasında incelemek için öğeleri belirtmek için öznitelikler.  
  
 Bir hedef toplu öğeler giriş veya çıkış, olarak kullanan bir görev içeriyorsa `Target` hedef öğenin de toplu işleme kullanması gereken, `Inputs` veya `Outputs` etkinleştirmek için öznitelikleri [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] maddelerini toplu olarak, zaten güncel olduğundan atlanacak.  
  
## <a name="batching-targets"></a>Toplu işleme hedefleri  
 Aşağıdaki örnekte adlı bir öğe listesini içeren `Res` göre iki gruplayın bölünmüş `Culture` öğe meta verileri. Yöntemlere geçirilen her biri bu toplu `AL` bir çıkış derlemesi için her toplu iş oluşturan bir görev. Üzerinde işlem grubu oluşturma kullanılarak `Outputs` özniteliği `Target` öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] her biri ayrı ayrı toplu işler hedef çalıştırmadan önce güncel olup olmadığını belirleyebilirsiniz. Toplu hedef işlemede kullanmadan hedef yürütülen her zaman her iki maddelerini toplu olarak görev tarafından çalıştırılmaz.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md)   
 [Toplu işleme](../msbuild/msbuild-batching.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Toplu Görev İşlemede Öğe Meta Verileri](../msbuild/item-metadata-in-task-batching.md)



