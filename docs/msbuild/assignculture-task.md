---
title: AssignCulture görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf333c5339ce9a4d6046fb5156e37157004491b9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177886"
---
# <a name="assignculture-task"></a>AssignCulture görevi
Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcı dizesi içerebilir öğelerinin bir listesini kabul eder ve adlı bir meta veri içermeyen öğeleri üretir `Culture` karşılık gelen içeren kültür tanımlayıcısı. Örneğin, dosya adı *Form1.fr-fr.resx* bu görev meta verilerle aynı dosya adını içeren bir öğe oluşturur tanımlayıcı "fr-fr", katıştırılmış bir kültür bulunduğundan `Culture` eşit `fr-fr`. Görev, dosya adları listesini de dosya kaldırıldı kültürüyle üretir.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Parametreleri aşağıdaki tabloda açıklanmıştır `AssignCulture` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Alınan öğelerin listesini içeren `Files` parametresi ile bir `Culture` meta veri girdisi her öğesine eklendi.<br /><br /> Gelen öğesini varsa `Files` parametre zaten var. bir `Culture` meta veri girdisi, özgün meta veri girdisi kullanılır.<br /><br /> Yalnızca görevi atayan bir `Culture` dosya adı, geçerli kültür tanımlayıcısı içeriyorsa meta veri girdisi. Kültür tanımlayıcısı, dosya adında son iki nokta arasında olmalıdır.|  
|`AssignedFilesWithCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Alt öğeleri kümesini içeren `AssignedFiles` sahip parametre bir `Culture` meta veri girdisi.|  
|`AssignedFilesWithNoCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Alt öğeleri kümesini içeren `AssignedFiles` sahip olmayan bir parametre bir `Culture` meta veri girdisi.|  
|`CultureNeutralAssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> İçinde oluşturulan öğeler aynı listesini içeren `AssignedFiles` parametresi dışındaki kültürüyle dosya adından kaldırıldı.<br /><br /> Geçerli kültür tanımlayıcısı olması durumunda görev kültürü yalnızca dosya adını kaldırır.|  
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir kültüre atamak için katıştırılmış kültür adları olan dosyaların listesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yürütür `AssignCulture` ile görev `ResourceFiles` öğe koleksiyonu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 Aşağıdaki tabloda, görev yürütme sonrasında çıkış öğelerin değerini açıklanmaktadır. Öğe meta verileri öğeden sonra parantez içinde gösterilmektedir.  
  
|Öğe koleksiyonu|İçindekiler|  
|---------------------|--------------|  
|`OutAssignedFiles`|*MyResource1.fr.resx* (kültür = "fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|  
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (kültür = "fr")|  
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (ek meta veri yok)|  
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (kültür = "fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)