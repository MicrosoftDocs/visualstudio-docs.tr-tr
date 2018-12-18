---
title: 'Nasıl yapılır: kaynaklara sahip olan bir projeyi derleme | Microsoft Docs'
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
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2383f563b8f6e80111d382c9abe96a66efadd69
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256937"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl Yapılır: Kaynaklara Sahip Olan Bir Projeyi Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yerelleştirilmiş sürümlerini bir proje oluşturuyorsanız tüm kullanıcı arabirimi öğeleri kaynak dosyalara farklı diller için ayrılmış olması gerekir. Projeyi yalnızca dizeler kullanıyorsa, kaynak dosyalar metin dosyaları kullanabilirsiniz. Alternatif olarak, .resx dosyaları kaynak dosya olarak kullanabilirsiniz.  
  
## <a name="compiling-resources-with-msbuild"></a>Kaynakları MSBuild ile derleme  
 Kitaplığı ile sağlanan ortak görevler [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] içeren bir `GenerateResource` .resx veya metin dosyalarındaki kaynaklar derlemek için kullanabileceğiniz bir görev. Bu görevi içeren `Sources` derlemek için hangi kaynak dosyaları belirtmek üzere parametre ve `OutputResources` çıkış kaynak dosyalarının adlarını belirlemek için parametre. Daha fazla bilgi için `GenerateResource` görev bkz [GenerateResource görevi](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Kaynakları MSBuild ile derlemek için  
  
1.  Projenin kaynak dosyaları tanımlayın ve bunlara geçirmek `GenerateResource` öğesi listeleri olarak ya da görev veya farklı dosya adları.  
  
2.  Belirtin `OutputResources` parametresinin `GenerateResource` çıkış kaynak dosyalarının adlarını ayarlamanıza olanak veren bir görev.  
  
3.  Kullanım `Output` değerini depolamak için bir görev öğesinin `OutputResources` parametresinde bir öğe.  
  
4.  Oluşturulan öğesini `Output` öğesi olarak bir giriş başka bir görev ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekte gösterildiği nasıl `Output` öğesi belirtir `OutputResources` özniteliği `GenerateResource` görev derlenmiş kaynak dosyalar içermesi `alpha.resources` ve `beta.resources` ve bu iki dosya içine yerleştirilecek `Resources` öğe listesi. .Resources dosyaları aynı ada sahip bir öğe koleksiyonu belirleyerek kolayca bunları giriş başka bir görev için gibi kullanabileceğiniz [Csc](../msbuild/csc-task.md) görev.  
  
 Bu görev kullanmakla eşdeğerdir **/compile** için geçiş [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje iki görevleri içerir: `GenerateResource` kaynakları derlemek için görev ve `Csc` hem kaynak kodu dosyaları ve derlenmiş kaynak dosyaları derleme görevi. Derlenmiş kaynak dosyalar tarafından `GenerateResource` görev depolanır `Resources` öğesini ve geçirilen `Csc` görev.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBuild](msbuild.md)  
 [GenerateResource görevi](../msbuild/generateresource-task.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Resgen.exe (Kaynak Dosya Oluşturucu)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)


