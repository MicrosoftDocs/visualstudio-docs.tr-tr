---
title: Öğe öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e33f057f3184a9a9bb19311f7206c6ab273dab8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081026"
---
# <a name="item-element-msbuild"></a>Öğe unsuru (MSBuild)
Kullanıcı tanımlı bir öğe ve meta verilerini içerir. Kullanılan her öğe bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] alt öğesi olarak proje belirtilen bir `ItemGroup` öğesi.  

 \<Proje >  
 \<ItemGroup >  
 \<Öğesi >  

## <a name="syntax"></a>Sözdizimi  

```xml  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Meta veri öznitelikleri belirtin.
MSBuild 15.1 veya sonraki sürümlerde, herhangi bir meta veri öznitelikleri geçerli listesi ile çakışmadığından bir ad ile isteğe bağlı olarak bir özniteliği olarak ifade edilebilir.

Örneğin, NuGet paketlerinin bir listesini belirtmek için normalde sözdizimine benzer bir şey kullanırsınız.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Şimdi, Bununla birlikte, geçirebilirsiniz `Version` olarak bir öznitelik, aşağıdaki söz dizimini gibi meta veriler:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  

### <a name="attributes"></a>Öznitelikler  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Include`|İsteğe bağlı öznitelik.<br /><br /> Dosya veya öğe listesinde içermek için joker karakter.|  
|`Exclude`|İsteğe bağlı öznitelik.<br /><br /> Dosya veya öğe listesinden dışlamak için joker karakter.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
|`Remove`|İsteğe bağlı öznitelik.<br /><br /> Dosya veya öğe listesinden kaldırmak için joker karakter.<br /><br />|  
|`KeepDuplicates`|İsteğe bağlı öznitelik.<br /><br /> Var olan bir öğeye tam bir kopyasını ise bir öğe için hedef grubu eklenip eklenmeyeceğini belirtir. Kaynak ve hedef öğesi aynı varsa `Include` değeri ancak farklı meta veriler, öğedir eklenmiş olsa bile `KeepDuplicates` ayarlanır `false`. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`KeepMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğeleri eklemek kaynak öğeleri için meta veriler. Yalnızca, adları noktalı virgülle ayrılmış listede belirtilen meta veriler, bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`RemoveMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğe için Aktarım değil kaynak öğeleri meta verileri. Tüm meta veriler bir kaynak öğeden hedef öğesi meta veri dışında adları adları noktalı virgülle ayrılmış listesi yer alır aktarılır. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`Update`|İsteğe bağlı öznitelik. (Yalnızca Visual Studio 2017 veya sonraki bir sürümünde .NET Core projeleri için kullanılabilir.)<br /><br /> Bir glob kullanarak dahil bir dosyanın meta verilerini değiştirmenize olanak sağlar.<br /><br />  Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` içinde değil bir `Target`.|  

### <a name="child-elements"></a>Alt öğeleri  

|Öğe|Açıklama|  
|-------------|-----------------|  
|[Itemmetadata](../msbuild/itemmetadata-element-msbuild.md)|Öğe meta veri değeri içeren bir kullanıcı tanımlı meta veri, öğe anahtarı. Sıfır veya daha fazla olabilir `ItemMetadata` öğeleri bir öğe.|  

### <a name="parent-elements"></a>Üst öğeler  

|Öğe|Açıklama|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Öğeleri için gruplandırma öğesi.|  

## <a name="remarks"></a>Açıklamalar  
 `Item` öğeleri, derleme sistemine girişleri tanımlayın ve öğe koleksiyonlarını, kullanıcı tanımlı toplama adlarına göre gruplanmıştır. Bu öğe koleksiyonlarını için parametre olarak kullanılan [görevleri](../msbuild/msbuild-tasks.md), hangi bireysel öğeleri koleksiyonlarında derleme işleminin adımları gerçekleştirmek için kullanın. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  

 Gösterimini kullanarak @(\<myType >) tür öğelerinin bir koleksiyonunu sağlayan \<myType > bir noktalı virgül ile ayrılmış dize listesi genişletilir ve bir parametre geçirildi. Parametre türü ise `string`, sonra parametresinin değeri öğeleri noktalı virgülle ayrılmış listesidir. Parametre dizisini ise (`string[]`), sonra her öğe noktalı konumunu temel alarak diziye eklenir. Görev parametresi türü ise <xref:Microsoft.Build.Framework.ITaskItem> `[]`, birlikte bağlı herhangi bir meta veri öğesi koleksiyonun içeriğini değeridir. Bir karakteri dışındaki bir noktalı virgül kullanarak her bir öğe sınırlandırmak için söz dizimini kullanın @(<myType>, '<separator>').  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Altyapısı değerlendirme joker karakterler gibi `*` ve `?` ve yinelemeli joker karakterler gibi  */ \* \* / \*.cs*. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneği, iki öğe türünde bildirmeniz gösterilmektedir `CSFile`. İkinci öğe olan metaverilerini içeren bildirilen `MyMetadata` kümesine `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
Aşağıdaki kod örneği kullanma işlemini gösterir `Update` adlı bir dosyaya meta verilerde değiştirmek için özniteliği *somefile.cs* , bir glob dahil. (Yalnızca Visual Studio 2017 veya sonraki bir sürümünde .NET Core projeleri için kullanılabilir.)

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Ayrıca bkz.  
 [Öğeleri](../msbuild/msbuild-items.md)   
 [MSBuild özellikleri](../msbuild/msbuild-properties.md)   
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
