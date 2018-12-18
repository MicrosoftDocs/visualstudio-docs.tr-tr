---
title: CallTarget görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4546fc47ddb38fabcd0ff84926d942f6ae10d59e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874689"
---
# <a name="calltarget-task"></a>CallTarget görevi
Proje dosyası içinde belirtilen hedefleri çağırır.  

## <a name="task-parameters"></a>Görev parametreleri  
 Parametreleri aşağıdaki tabloda açıklanmıştır `CallTarget` görev.  


| Parametre | Açıklama |
|---------------------------| - |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` giriş parametresi.<br /><br /> Varsa `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı hedef bir kez çağrılır. Varsa `false`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı adlı bir kez tüm hedefler oluşturmak için. Varsayılan değer `false` şeklindedir. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Tüm oluşturulmuş hedefleri çıktıları içeriyor. |
| `Targets` | İsteğe bağlı `String[]` parametresi.<br /><br /> Hedef veya oluşturulacak hedeflerin belirtir. |
| `UseResultsCache` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `true`, önbelleğe alınan sonuç varsa, döndürülür.<br /><br /> **Not** olduğunda bir MSBuild görevi çalıştırılana, çıktısını bir kapsamda (ProjectFileName, GlobalProperties) önbelleğe alınmış [TargetNames] derleme öğe listesi olarak. |

## <a name="remarks"></a>Açıklamalar  
 Bir hedef içinde belirtilen `Targets` başarısız olur ve `RunEachTargetSeparately` olduğu `true`, görev derleme kalan hedeflerini devam eder.  

 Varsayılan hedefler oluşturmak istiyorsanız, kullanmanız [MSBuild görevi](../msbuild/msbuild-task.md) ayarlayıp `Projects` parametresi eşit `$(MSBuildProjectFile)`.  

 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları `TargetA` gelen içinde `CallOtherTargets`.  

```xml  
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

## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Hedefler](../msbuild/msbuild-targets.md)