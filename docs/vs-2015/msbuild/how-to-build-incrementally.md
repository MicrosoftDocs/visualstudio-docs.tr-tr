---
title: 'Nasıl yapılır: artımlı olarak derleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88ad4f984af2be6884005c5ec3c7dec4d7b5c6aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844631"
---
# <a name="how-to-build-incrementally"></a>Nasıl Yapılır: Artımlı Olarak Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Büyük bir proje oluşturduğunuzda, daha önce hala güncel olan bileşenleri yerleşik olmayan yeniden önemlidir. Her yapı, her zaman tüm hedefleri oluşturulduysa, tamamlanması uzun sürer. Artımlı derlemeleri Etkinleştir için (hangi derlemelerde yalnızca önce oluşturulmuş değil veya hedefleyen bu hedefleri güncel yeniden), [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) giriş dosyaları zaman damgaları ve çıkış dosyalarının zaman damgalı karşılaştırabilirsiniz ve atlayın, yapı ya da kısmi bir hedef yeniden belirleyin. Ancak, giriş ve çıkışları arasında bire bir eşleme olmalıdır. Dönüşümleri, doğrudan bu eşleme tanımlamak hedefleri etkinleştirmek için kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [dönüştüren](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Giriş ve çıkışları belirtme  
 Proje dosyasında belirtilen girişler ve çıkışlar, bir hedef artımlı olarak oluşturulabilir.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Giriş ve çıkışları hedef belirtmek için  
  
- Kullanım `Inputs` ve `Outputs` özniteliklerini `Target` öğesi. Örneğin:  
  
  ```  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Giriş dosyaları zaman damgaları ve çıkış dosyalarının zaman damgalı karşılaştırın ve karar atlayın, yapı ya da kısmi bir hedefe yeniden kullanabilirsiniz. Aşağıdaki örnekte herhangi dosyası varsa `@(CSFile)` öğe listesi hello.exe Dosya yeniyse [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hedef çalışır; Aksi takdirde atlanacak:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Giriş ve çıkışları bir hedef olarak belirtildiğinde, her çıkış için yalnızca bir girişi eşleyebilirsiniz veya doğrudan bir eşleme girişleri ve çıkışları arasında olabilir. Önceki [Csc görevi](../msbuild/csc-task.md), örneğin, çıkış hello.exe, herhangi bir tek giriş eşleştirilemez – hepsinde bağlıdır.  
  
> [!NOTE]
>  Giriş ve çıkışları arasında doğrudan eşleme olduğu bir hedef her zaman, her çıkış eşlenebilir yalnızca bir giriş için bir hedef çok sık oluşturacaksınız [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hangi çıkışları bazı girişleri değiştirdiyseniz yeniden derlenmesi gerekiyor belirlenemiyor .  
  
 Hangi belirleyebilirsiniz giriş ve çıkışları arasında doğrudan bir eşleme gibi görevleri [LC görevi](../msbuild/lc-task.md), aşağıdakiler gibi görevleri farklı olarak, artımlı derlemeleri için en uygun olan `Csc` ve [Vbc](../msbuild/vbc-task.md), hangi üretebilir bir giriş bir sayı derlemesinden çıkış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Yardım dosyaları kuramsal bir Yardım sistemine için oluşturan bir proje kullanır. Proje, kaynak .txt dosyaları Yardım sistemi tarafından kullanılan son .help dosyası üretmek için XML meta veri dosyaları ile birleştirilen Ara .content dosyaları dönüştürerek çalışır. Proje aşağıdaki kuramsal görevleri kullanır:  
  
- `GenerateContentFiles`: .txt dosyaları .content dosyalarına dönüştürür.  
  
- `BuildHelp`: .content ve son .help dosyasını oluşturmak için XML meta veri dosyaları birleştirir.  
  
  Proje dönüşümler girdi arasında bire bir eşleme oluşturmak için kullanır ve içinde çıkaran `GenerateContentFiles` görev. Daha fazla bilgi için [dönüştüren](../msbuild/msbuild-transforms.md). Ayrıca, `Output` öğesi çıkışları otomatik olarak kullanmak üzere ayarlanmış `GenerateContentFiles` görevi için girişler olarak `BuildHelp` görev.  
  
  Bu proje dosyasını içeren `Convert` ve `Build` hedefler. `GenerateContentFiles` Ve `BuildHelp` görevleri yerleştirildiğinde `Convert` ve `Build` her hedef artımlı olarak derlenebilir, sırasıyla hedefler. Kullanarak `Output` öğesinde, çıkışlarına `GenerateContentFiles` görev yerleştirildiğinde `ContentFile` öğesi listesinin nerede bunlar kullanılabilir için girdi olarak `BuildHelp` görev. Kullanarak `Output` öğesi bu şekilde otomatik olarak sağlar bir görev çıkışları girdi olarak başka bir görev için bireysel öğeleri listelemek veya her bir görevin elle listelerinde öğe sahip değil.  
  
> [!NOTE]
>  Ancak `GenerateContentFiles` hedef artımlı olarak oluşturabilirsiniz, hedefleyen tüm çıkışları için girdi olarak her zaman gereklidir `BuildHelp` hedef. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kullanırken bir hedef tüm çıktılarını başka bir hedef için girdi olarak otomatik olarak sağlar `Output` öğesi.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
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
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hedefleri](../msbuild/msbuild-targets.md)   
 [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Dönüşümler](../msbuild/msbuild-transforms.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Vbc Görevi](../msbuild/vbc-task.md)



