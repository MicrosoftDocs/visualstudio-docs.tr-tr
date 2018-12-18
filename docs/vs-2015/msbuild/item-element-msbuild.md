---
title: Öğe öğesi (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dfec558a9958d980d25d4160c4b7f2ce269cbb5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270044"
---
# <a name="item-element-msbuild"></a>Öğe Unsuru (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Kullanıcı tanımlı bir öğe ve meta verilerini içerir. Kullanılan her öğe bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] alt öğesi olarak proje belirtilen bir `ItemGroup` öğesi.  
  
 \<Proje >  
 \<ItemGroup >  
 \<Öğesi >  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Include`|Gerekli öznitelik.<br /><br /> Dosya veya öğe listesinde içermek için joker karakter.|  
|`Exclude`|İsteğe bağlı öznitelik.<br /><br /> Dosya veya öğe listesinden dışlamak için joker karakter.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için [koşullar](../msbuild/msbuild-conditions.md).|  
|`Remove`|İsteğe bağlı öznitelik.<br /><br /> Dosya veya öğe listesinden kaldırmak için joker karakter.<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`KeepMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğeleri eklemek kaynak öğeleri için meta veriler. Yalnızca, adları noktalı virgülle ayrılmış listede belirtilen meta veriler, bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`RemoveMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğe için Aktarım değil kaynak öğeleri meta verileri. Tüm meta veriler bir kaynak öğeden hedef öğesi meta veri dışında adları adları noktalı virgülle ayrılmış listesi yer alır aktarılır. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
|`KeepDuplicates`|İsteğe bağlı öznitelik.<br /><br /> Var olan bir öğeye tam bir kopyasını ise bir öğe için hedef grubu eklenip eklenmeyeceğini belirtir. Kaynak ve hedef öğesi aynı varsa `Include` değeri ancak farklı meta veriler, öğedir eklenmiş olsa bile `KeepDuplicates` ayarlanır `false`. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca bir öğe için belirtilmişse geçerli bir `ItemGroup` olan bir `Target`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Itemmetadata](../msbuild/itemmetadata-element-msbuild.md)|Öğe meta veri değeri içeren bir kullanıcı tanımlı meta veri, öğe anahtarı. Sıfır veya daha fazla olabilir `ItemMetadata` öğeleri bir öğe.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Öğeleri için gruplandırma öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Item` öğeleri, derleme sistemine girişleri tanımlayın ve öğe koleksiyonlarını, kullanıcı tanımlı toplama adlarına göre gruplanmıştır. Bu öğe koleksiyonlarını için parametre olarak kullanılan [görevleri](../msbuild/msbuild-tasks.md), hangi bireysel öğeleri koleksiyonlarında derleme işleminin adımları gerçekleştirmek için kullanın. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
 Gösterimini kullanarak `@(` *myType* `)` tür öğelerinin bir koleksiyonunu sağlayan *myType* bir noktalı virgül ile ayrılmış dize listesi genişletilir ve bir parametre geçirildi. Parametre türü ise `string`, sonra parametresinin değeri öğeleri noktalı virgülle ayrılmış listesidir. Parametre dizisini ise (`string[]`), sonra her öğe noktalı konumunu temel alarak diziye eklenir. Görev parametresi türü ise <xref:Microsoft.Build.Framework.ITaskItem> `[]`, birlikte bağlı herhangi bir meta veri öğesi koleksiyonun içeriğini değeridir. Bir karakteri dışındaki bir noktalı virgül kullanarak her bir öğe sınırlandırmak için söz dizimini kullanın `@(` *myType*`, '`*ayırıcı*`')`.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Altyapısı değerlendirme joker karakterler gibi `*` ve `?` ve yinelemeli joker karakterler gibi `/**/*.cs`. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki öğe türünde bildirmeniz gösterilmektedir `CSFile`. İkinci öğe olan metaverilerini içeren bildirilen `MyMetadata` kümesine `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeleri](../msbuild/msbuild-items.md)   
 [MSBuild özellikleri](msbuild-properties1.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)



