---
title: ReadLinesFromFile Görevi | Microsoft Docs
description: MSBuild 'in bir metin dosyasından öğe listesini okumak için ReadLinesFromFile görevini nasıl kullandığını öğrenin. Dosya her satırda bir öğe içermelidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0361d0103afbe662a37b50358e125018a7378f39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931974"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile görevi

Bir metin dosyasından öğelerin listesini okur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `ReadLinesFromFile` .

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Okunacak dosyayı belirtir. Dosya her satırda bir öğe içermelidir.|
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Dosyadan okunan satırları içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `ReadLinesFromFile` bir metin dosyasındaki bir listeden öğe oluşturmak için görevini kullanır. Dosyadan okunan öğeler `ItemsFromFile` öğe koleksiyonunda depolanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Görevler](../msbuild/msbuild-tasks.md)
