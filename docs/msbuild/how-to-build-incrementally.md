---
title: 'Nasıl yapılır: artımlı olarak derleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9e0251d41feb5bd9c61a719d932c6fd954be947
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932436"
---
# <a name="how-to-build-incrementally"></a>Nasıl yapılır: artımlı olarak derleme
Büyük bir proje oluşturduğunuzda, daha önce hala güncel olan bileşenleri yerleşik olmayan yeniden önemlidir. Her yapı, her zaman tüm hedefleri oluşturulduysa, tamamlanması uzun sürer. Artımlı derlemeleri Etkinleştir için (hangi derlemelerde yalnızca önce oluşturulmuş değil veya hedefleyen bu hedefleri güncel yeniden), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) giriş dosyaları zaman damgaları ve çıkış dosyalarının zaman damgalı karşılaştırabilirsiniz ve atlayın, yapı ya da kısmi bir hedef yeniden belirleyin. Ancak, giriş ve çıkışları arasında bire bir eşleme olmalıdır. Dönüşümleri, doğrudan bu eşleme tanımlamak hedefleri etkinleştirmek için kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [dönüştüren](../msbuild/msbuild-transforms.md).  
  
## <a name="specify-inputs-and-outputs"></a>Giriş ve çıkışları belirtin  
 Proje dosyasında belirtilen girişler ve çıkışlar, bir hedef artımlı olarak oluşturulabilir.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Giriş ve çıkışları hedef belirtmek için  
  
- Kullanım `Inputs` ve `Outputs` özniteliklerini `Target` öğesi. Örneğin:  
  
  ```xml  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Giriş dosyaları zaman damgaları ve çıkış dosyalarının zaman damgalı karşılaştırın ve karar atlayın, yapı ya da kısmi bir hedefe yeniden kullanabilirsiniz. Aşağıdaki örnekte herhangi dosyası varsa `@(CSFile)` öğesi listesini daha yeniyse *hello.exe* dosyası [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hedef çalışır; Aksi halde atlanır:  
  
```xml  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Giriş ve çıkışları bir hedef olarak belirtildiğinde, her çıkış için yalnızca bir girişi eşleyebilirsiniz veya doğrudan bir eşleme girişleri ve çıkışları arasında olabilir. Önceki [Csc görevi](../msbuild/csc-task.md), örneğin, çıkış *hello.exe*, eşlenemez herhangi tek bir giriş için - bu hepsinde bağlıdır.  
  
> [!NOTE]
>  Giriş ve çıkışları arasında doğrudan eşleme olduğu bir hedef her zaman, her çıkış eşlenebilir yalnızca bir giriş için bir hedef çok sık oluşturacaksınız [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hangi çıkışları bazı girişleri değiştirdiyseniz yeniden derlenmesi gerekiyor belirlenemiyor .  
  
 Hangi belirleyebilirsiniz giriş ve çıkışları arasında doğrudan bir eşleme gibi görevleri [LC görevi](../msbuild/lc-task.md), aşağıdakiler gibi görevleri farklı olarak, artımlı derlemeleri için en uygun olan [Csc](../msbuild/csc-task.md) ve [Vbc](../msbuild/vbc-task.md), bir çıkış derlemesi girişleri bir dizi üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Yardım dosyaları kuramsal bir Yardım sistemine için oluşturan bir proje kullanır. Proje çalıştığı kaynak dönüştürerek *.txt* Ara dosyalarına *.content* ardından son üretmek için XML meta veri dosyaları ile birleştirilen dosyalar *.help* dosyası Yardım sistemi tarafından kullanılır. Proje aşağıdaki kuramsal görevleri kullanır:  
  
-   `GenerateContentFiles`: Dönüştürür *.txt* dosyalarınızı *.content* dosyaları.  
  
-   `BuildHelp`: Birleştirir *.content* ve en son oluşturmak için XML meta veri dosyaları *.help* dosya.  
  

 Proje dönüşümler girdi arasında bire bir eşleme oluşturmak için kullanır ve içinde çıkaran `GenerateContentFiles` görev. Daha fazla bilgi için [dönüştüren](../msbuild/msbuild-transforms.md). Ayrıca, `Output` öğesi çıkışları otomatik olarak kullanmak üzere ayarlanmış `GenerateContentFiles` görevi için girişler olarak `BuildHelp` görev.  
  
 Bu proje dosyasını içeren `Convert` ve `Build` hedefler. `GenerateContentFiles` Ve `BuildHelp` görevleri yerleştirildiğinde `Convert` ve `Build` her hedef artımlı olarak derlenebilir, sırasıyla hedefler. Kullanarak `Output` öğesinde, çıkışlarına `GenerateContentFiles` görev yerleştirildiğinde `ContentFile` öğesi listesinin nerede bunlar kullanılabilir için girdi olarak `BuildHelp` görev. Kullanarak `Output` öğesi bu şekilde otomatik olarak sağlar bir görev çıkışları girdi olarak başka bir görev için bireysel öğeleri listelemek veya her bir görevin elle listelerinde öğe sahip değil.  
  
> [!NOTE]
>  Ancak `GenerateContentFiles` hedef artımlı olarak oluşturabilirsiniz, hedefleyen tüm çıkışları için girdi olarak her zaman gereklidir `BuildHelp` hedef. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kullanırken bir hedef tüm çıktılarını başka bir hedef için girdi olarak otomatik olarak sağlar `Output` öğesi.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFiles Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFiles)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hedefleri](../msbuild/msbuild-targets.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Dönüşümler](../msbuild/msbuild-transforms.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Vbc görevi](../msbuild/vbc-task.md)
