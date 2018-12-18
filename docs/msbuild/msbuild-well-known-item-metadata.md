---
title: MSBuild tanınmış öğe meta verileri | Microsoft Docs
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
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d1ec2d2ade7162f08db954d8a7bebe059a21878
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154566"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild tanınmış öğe meta verisi
Aşağıdaki tabloda, oluşturulduktan sonra her öğeye atanan meta veriler açıklanmaktadır. Her örnekte, aşağıdaki öğe bildirimi dosya eklemek için kullanılan *C:\MyProject\Source\Program.cs* projedeki.  
  
```xml  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Öğe meta verileri|Açıklama|  
|-------------------|-----------------|  
|%(FullPath)|Öğenin tam yolunu içerir. Örneğin:<br /><br /> *C:\MyProject\Source\Program.cs*|  
|%(RootDir)|Öğenin kök dizinini içerir. Örneğin:<br /><br /> *C:\\*|  
|%(Filename)|Uzantı olmadan öğenin dosya adını içerir. Örneğin:<br /><br /> *Programı*|  
|%(Extension)|Öğesinin dosya adı uzantısını içerir. Örneğin:<br /><br /> *.cs*|  
|%(RelativeDir)|Belirtilen yolu içerir `Include` son eğik çizgiyi kadar bir öznitelik (\\). Örneğin:<br /><br /> *Kaynak\\*|  
|%(Directory)|Kök dizin olmadan öğenin dizinini içerir. Örneğin:<br /><br /> *MyProject\\kaynak\\*|  
|%(RecursiveDir)|Varsa `Include` öznitelik joker karakter içeren \* \*, bu meta veri joker karakterin yerini alan yolu parçası belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: derleme dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Varsa klasörü *C:\MySolution\MyProject\Source\\*  dosyayı içeren *Program.cs*, ve proje dosyası bu öğe içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> ardından değerini `%(MyItem.RecursiveDir)` olacaktır *MySolution\MyProject\Source\\*.|  
|%(Identity)|Belirtilen öğe `Include` özniteliği... Örneğin:<br /><br /> *Source\Program.cs*|  
|%(ModifiedTime)|Öğeye erişildiği son zamandan itibaren zaman damgası içerir. Örneğin:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Öğesi oluşturulduğu zaman damgası içerir. Örneğin:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Öğeye erişildiği son zamandan itibaren zaman damgası içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Öğeleri](../msbuild/msbuild-items.md)   
 [Toplu işleme](../msbuild/msbuild-batching.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)