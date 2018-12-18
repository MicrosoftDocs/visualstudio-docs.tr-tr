---
title: CreateItem görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a53bbac8f1d4549b49183d0e90b2f33c925654d6
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945306"
---
# <a name="createitem-task"></a>CreateItem görevi
Öğe koleksiyonlarını girdi öğelerinin ile doldurur. Bu, bir listeden diğerine kopyalanmasına öğeleri sağlar.  
  
> [!NOTE]
>  Bu görevi kullanım dışı bırakılmıştır. İçinde .NET Framework 3.5 ile öğesi grupları başlangıç yerleştirilebilir [hedef](../msbuild/target-element-msbuild.md) öğeleri. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Öznitelikler  
 Parametreleri aşağıdaki tabloda açıklanmıştır `CreateItem` görev.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalMetadata`|İsteğe bağlı `String` dizi parametresi.<br /><br /> Çıktı öğeleri eklemek için ek meta verileri belirtir.  Meta veri adı ve değeri öğe için şu sözdizimini belirtin:<br /><br /> *Metadataname'in* `=` *MetadataValue*<br /><br /> Birden fazla meta veri adı/değer çiftleri noktalı virgül ile ayrılmalıdır. Adı veya değeri bir noktalı virgül veya diğer özel karakterleri içeriyorsa, bunlar kaçış karakterleri eklenmelidir. Daha fazla bilgi için [nasıl yapılır: MSBuild özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çıktı öğesi koleksiyondan hariç tutmak için öğeleri belirtir. Bu parametre joker karakteri belirtimlerine içerebilir. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md) ve [nasıl yapılır: dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametresi.<br /><br /> Çıktı öğesi koleksiyonda eklemek istediğiniz öğeleri belirtir. Bu parametre joker karakteri belirtimlerine içerebilir.|  
|`PreserveExistingMetadata`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Varsa `True`, zaten mevcut değilse ek meta veriler yalnızca geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde adlı yeni bir öğe koleksiyonu oluşturur `MySourceItemsWithMetadata` öğeyi koleksiyondan `MySourceItems`. `CreateItem` Görev yeni bir öğe koleksiyonu öğeleri ile doldurur `MySourceItems` öğesi. Ardından adlı bir ek meta veri girdisi ekler `MyMetadata` değeriyle `Hello` yeni koleksiyondaki her öğe için.  
  
 Görev yürütüldükten sonra `MySourceItemsWithMetadata` öğe koleksiyonu öğeleri içeren *file1.resx* ve *file2.resx*, hem meta veri girişleriyle `MyMetadata`. `MySourceItems` Öğe koleksiyonu değişmez.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 Aşağıdaki tabloda, görev yürütme sonrasında çıkış öğesinin değeri açıklanmaktadır. Öğe meta verileri öğeden sonra parantez içinde gösterilmektedir.  
  
|Öğe koleksiyonu|İçindekiler|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|*File1.resx* (`MyMetadata="Hello"`)<br /><br /> *File2.resx* (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevleri](../msbuild/msbuild-tasks.md)