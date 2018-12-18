---
title: MSBuild dönüşümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1a3ff7cbd2025a909ab0c5fb044bb61b24388ff
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151206"
---
# <a name="msbuild-transforms"></a>MSBuild dönüşümleri
Dönüşüm bir bire bir öğe listesinin başka bir dönüştürmedir. Bir proje öğesi listeleri dönüştürmek etkinleştirmeye ek olarak, bir dönüştürme giriş ve çıkışlarını arasında doğrudan bir eşleme tanımlamak bir hedef sağlar. Bu konu, dönüşümler açıklar ve nasıl [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri daha verimli bir şekilde oluşturmak için bunları kullanır.  
  
## <a name="transform-modifiers"></a>Değiştiriciler dönüştürme  
Dönüşümler rastgele değildir, ancak özel sözdizimi tüm dönüştürme değiştiricilere olması gereken biçimde %(tarafından sınırlandırılmıştır\<ItemMetaDataName >). Öğe meta verileri, dönüştürme değiştirici olarak kullanılabilir. Bu, oluşturulduğunda, her öğeye atanan tanınmış öğe meta verileri içerir. İyi bilinen öğe meta verileri bir listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).  
  
Aşağıdaki örnekte, bir listesini *.resx* dosyaları bir listeye dönüştürülen *.resources* dosyaları. %(Filename) dönüştürme değiştiricisi, her belirtir *.resources* dosya ilgili olarak aynı dosya adına sahip *.resx* dosya.  
  
```xml  
@(RESXFile->'%(filename).resources')  
```

Örneğin, @(RESXFile) öğesi listedeki öğeler varsa *Form1.resx*, *Form2.resx*, ve *Form3.resx*, dönüştürülen listesinde çıktılar olacağını  *Form1.Resources*, *Form2.resources*, ve *Form3.resources*.  

> [!NOTE]
>  Ayırıcı standart öğesi listesi için belirttiğiniz aynı şekilde dönüştürülmüş öğesi listesi için özel bir ayırıcı belirtebilirsiniz. Örneğin, varsayılan noktalı virgül (;) yerine bir virgül (,) kullanarak dönüştürülmüş öğesi listesini ayırmak için aşağıdaki XML kullanın:  
> `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`
  
## <a name="use-multiple-modifiers"></a>Birden çok değiştiriciler kullanın  
 Bir dönüştürme ifadesi herhangi bir sırada birleştirilebilen ve yinelenebilen birden çok değiştiriciler içerebilir. Aşağıdaki örnekte, dosyaları içeren dizine adı değiştirildi, ancak dosya özgün adı ve dosya adı uzantısı korunur.  
  
```xml  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Örneğin, olmayan öğeler bulunan `RESXFile` öğe listesi *Project1\Form1.resx*, *Project1\Form2.resx*, ve *Project1\Form3.text*, Dönüştürülen listesinde çıkışları olacaktır *Toolset\Form1.resx*, *Toolset\Form2.resx*, ve *Toolset\Form3.text*.  
  
## <a name="dependency-analysis"></a>Bağımlılık çözümlemesi  
 Dönüşümler dönüştürülmüş öğe listesi ve özgün öğe listesi arasında bire bir eşleme garanti. Bu nedenle, bir hedef oluşturur girişlere dönüştürmeler çıkışları [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zaman damgaları girişler ve çıkışlar, analiz ve atlayın, yapı veya kısmen hedef yeniden karar.  
  
 İçinde [kopyalama görevi](../msbuild/copy-task.md) aşağıdaki örnekte, her bir dosyanın `BuiltAssemblies` öğe listesi eşleyen bir dönüştürme kullanılarak belirtilen görev, hedef klasörde bir dosyaya `Outputs` özniteliği. Bir dosya varsa `BuiltAssemblies` öğe listesi değişikliklerinin `Copy` görev yalnızca değiştirilen dosya için çalışır ve diğer tüm dosyalar atlanır. Bağımlılık analizi ve dönüşümler kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dönüşümler kullanan bir proje dosyası. Bu örnek yalnızca bir tane olduğunu varsayar *.xsd* dosyası *c:\sub0\sub1\sub2\sub3* directory ve çalışma dizinini olduğunu *c:\sub0*.  
  
### <a name="code"></a>Kod  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Nasıl yapılır: artımlı olarak derleme](../msbuild/how-to-build-incrementally.md)