---
title: CallTarget görevi | Microsoft Docs
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
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc3c5822732a4ae584500bfe1c48d7ba9e29b038
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307683"
---
# <a name="calltarget-task"></a>CallTarget Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Proje dosyası içinde belirtilen hedefleri çağırır.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Parametreleri aşağıdaki tabloda açıklanmıştır `CallTarget` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|İsteğe bağlı `Boolean` çıkış parametresi.<br /><br /> Varsa `true`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] altyapısı hedef bir kez çağrılır. Varsa `false`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] altyapısı adlı bir kez tüm hedefler oluşturmak için. Varsayılan değer `false` şeklindedir.|  
|`TargetOutputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Tüm oluşturulmuş hedefleri çıktıları içeriyor.|  
|`Targets`|İsteğe bağlı `String[]` parametresi.<br /><br /> Hedef veya oluşturulacak hedeflerin belirtir.|  
|`UseResultsCache`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, önbelleğe alınan sonuç varsa, döndürülür.<br /><br /> **Not** olduğunda bir MSBuild görevi çalıştırılana, çıktısını bir kapsamda (ProjectFileName, GlobalProperties) önbelleğe alınmış [TargetNames] derleme öğe listesi olarak.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hedef içinde belirtilen `Targets` başarısız olur ve `RunEachTargetSeparately` olduğu `true`, görev derleme kalan hedeflerini devam eder.  
  
 Varsayılan hedefler oluşturmak istiyorsanız, kullanmanız [MSBuild görevi](../msbuild/msbuild-task.md) ayarlayıp `Projects` parametresi eşit `$(MSBuildProjectFile)`.  
  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları `TargetA` gelen içinde `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Hedefler](../msbuild/msbuild-targets.md)



