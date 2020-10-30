---
title: ResourcesGenerator görevi | Microsoft Docs
description: MSBuild 'in bir. resources dosyasına bir veya daha fazla kaynak eklemek için ResourcesGenerator görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288d83cd16b9faebc9c6826a08da7c11811663d5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048482"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator görevi

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>Görev bir veya daha fazla kaynağı ( *. jpg* , *. ico* , *. bmp* , ikili biçimdeki XAML ve diğer uzantı türlerini) bir *. resources* dosyasına katıştırır.

## <a name="task-parameters"></a>Görev parametreleri

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Çıkış dizininin yolunu belirtir. Yol mutlak bir yol değilse, kök proje diziniyle ilişkili bir yol olarak kabul edilir.|
|`OutputResourcesFile`|Gerekli **ITaskItem []** çıkış parametresi.<br /><br /> Oluşturulan *. resources* dosyasının yolunu ve adını belirtir. Yol mutlak bir yol değilse, *. resources* dosyası kök proje dizinine göre oluşturulur.|
|`ResourcesFiles`|Gerekli **ıtaskitem []** parametresi.<br /><br /> Oluşturulan *. resources* dosyasına eklemek için bir veya daha fazla kaynak belirtir.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, tek bir *. bmp* kaynağı ile bir *. resources* dosyası oluşturur. *. Bmp* kaynağı, proje kök dizinine göreli bir dizine üretilir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)