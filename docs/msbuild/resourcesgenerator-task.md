---
title: ResourcesGenerator görevi | Microsoft Docs
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
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b72ce231b514250a40e9f3a4bf5ceb5aa2c69f8
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178897"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator görevi
<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> Görev bir veya daha fazla kaynak katıştırır (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimi ve diğer uzantı türleri) bir içine *.resources* dosya.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Çıktı dizini yolunu belirtir. Yol mutlak bir yol yoksa kök proje dizinine göreli bir yol olarak kabul edilir.|  
|`OutputResourcesFile`|Gerekli **Itaskıtem []** çıkış parametresi.<br /><br /> Oluşturulan adını ve yolunu belirtir *.resources* dosya. Yol mutlak bir yol değilse *.resources* dosyası kök proje dizinine göreli oluşturulur.|  
|`ResourcesFiles`|Gerekli **Itaskıtem []** parametresi.<br /><br /> Oluşturulan eklemek için bir veya daha fazla kaynak belirtir *.resources* dosya.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir *.resources* tek bir dosyayla *.bmp* kaynak. *.Bmp* kaynak proje kök dizinine göreli bir dizin oluşturulur.  
  
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
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Bir WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)