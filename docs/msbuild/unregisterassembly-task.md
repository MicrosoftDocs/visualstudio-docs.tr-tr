---
title: UnregisterAssembly görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6f1712192f8d68131a9adbbc8eb6de5d85429ad
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150541"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly görevi
Belirtilen derlemeleri COM birlikte çalışma amacıyla kaydını siler. Gerçekleştirir, ters [RegisterAssembly görevi](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametreler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `UnregisterAssembly` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Sona erdirilecek bütünleştirilmiş kodları belirtir.|  
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Arasında durumu hakkındaki bilgileri içeren `RegisterAssembly` görev ve `UnregisterAssembly` görev. Bu görev kaydetmek için başarısız bir derleme kaydını denemelerini engeller `RegisterAssembly` görev.<br /><br /> Bu parametre belirtilmezse, `Assemblies` ve `TypeLibFiles` parametreleri yok sayılır.|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Belirtilen derlemedeki belirtilen tür kitaplığının kaydını siler. **Not:** Bu parametre, yalnızca tür kitaplığı dosyasının adını derleme adından farklıysa gereklidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derlemenin başarılı olması bu görev için mevcut gerekli. Var olmayan bir derleme kaydını çalışırsanız, görev bir uyarıyla başarılı olur. Derleme kayıt defterinden kaldırmak için bu görev iş oluşur. Derleme mevcut değilse, kayıt defterinde değildir ve bu nedenle, görev başarılı oldu.  
  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> kendisi sınıfının devraldığı <xref:System.MarshalByRefObject> sınıfı. `MarshalByRefObject` Sınıfı aynı işlevleri sağlar <xref:Microsoft.Build.Utilities.Task> sınıfı, ancak, kendi uygulama etki alanında oluşturulabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `UnregisterAssembly` tarafından belirtilen yolda derleme kaydını silmek için görev `OutputPath` ve `FileName` varsa özellikleri.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [RegisterAssembly görevi](../msbuild/registerassembly-task.md)   
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)