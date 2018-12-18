---
title: 'Nasıl yapılır: kaynaklara sahip olan bir projeyi derleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7724969a4677bc0d8480b794ae72b2dbee74a86
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180353"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl yapılır: kaynaklara sahip olan bir projeyi derleme
Yerelleştirilmiş sürümlerini bir proje oluşturuyorsanız tüm kullanıcı arabirimi öğeleri kaynak dosyalara farklı diller için ayrılmış olması gerekir. Projeyi yalnızca dizeler kullanıyorsa, kaynak dosyalar metin dosyaları kullanabilirsiniz. Alternatif olarak, *.resx* dosyaları olarak kaynak dosyaları.  
  
## <a name="compile-resources-with-msbuild"></a>Kaynakları MSBuild ile Derle  
 Kitaplığı ile sağlanan ortak görevler [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] içeren bir `GenerateResource` ya da kaynakları derlemek için kullanabileceğiniz görev *.resx* veya metin dosyaları. Bu görevi içeren `Sources` derlemek için hangi kaynak dosyaları belirtmek üzere parametre ve `OutputResources` çıkış kaynak dosyalarının adlarını belirlemek için parametre. Daha fazla bilgi için `GenerateResource` görev bkz [GenerateResource görevi](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Kaynakları MSBuild ile derlemek için  
  
1.  Projenin kaynak dosyaları tanımlayın ve bunlara geçirmek `GenerateResource` öğesi listeleri olarak ya da görev veya farklı dosya adları.  
  
2.  Belirtin `OutputResources` parametresinin `GenerateResource` çıkış kaynak dosyalarının adlarını ayarlamanıza olanak veren bir görev.  
  
3.  Kullanım `Output` değerini depolamak için bir görev öğesinin `OutputResources` parametresinde bir öğe.  
  
4.  Oluşturulan öğesini `Output` öğesi olarak bir giriş başka bir görev ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekte gösterildiği nasıl `Output` öğesi belirtir `OutputResources` özniteliği `GenerateResource` görev derlenmiş kaynak dosyalar içermesi *alpha.resources* ve  *Beta.Resources* ve bu iki dosya içine yerleştirilecek `Resources` öğe listesi. Bu belirleme *.resources* dosyaları aynı ada sahip bir öğe koleksiyonu olarak kolayca kullanabileceğiniz bunları girdi olarak başka bir görev için aşağıdaki gibi [Csc](../msbuild/csc-task.md) görev.  
  
 Bu görev kullanmakla eşdeğerdir **/compile** için geçiş [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```xml  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje iki görevleri içerir: `GenerateResource` kaynakları derlemek için görev ve `Csc` hem kaynak kodu dosyaları ve derlenmiş kaynak dosyaları derleme görevi. Derlenmiş kaynak dosyalar tarafından `GenerateResource` görev depolanır `Resources` öğesini ve geçirilen `Csc` görev.  
  
```xml  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
[MSBuild](../msbuild/msbuild.md)  
 [GenerateResource görevi](../msbuild/generateresource-task.md)   
 [CSC görevi](../msbuild/csc-task.md)   
 [Resgen.exe (Kaynak Dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator)