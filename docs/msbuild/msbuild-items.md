---
title: MSBuild öğeleri | Microsoft Docs
description: ItemGroup Msbuild'i içerecek öznitelik bir derlemede dahil edilecek dosyaları belirtmek için kullanın
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28d98b7c74ebc57bd5b7b529303f2f5a17277ff5
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443603"
---
# <a name="msbuild-items"></a>MSBuild öğeleri
MSBuild öğeleri yapı sistemine girdi ve bunlar genelde dosyaları temsil eder (dosyaları belirtilen `Include` özniteliği). Öğeleri öğesi adlarına dayalı öğe türlerine gruplanır. Öğe türleri parametre olarak görevleri için kullanılabilir öğe listeleri içeren adlandırılır. Görevler, derleme işleminin adımları gerçekleştirmek için öğe değerlerini kullanın.  
  
 Koşulları "Item" ve "öğesi value" öğelerini ait oldukları öğe türü adlandırılır çünkü birbirlerinin yerine kullanılabilir.  
  
##  <a name="create-items-in-a-project-file"></a>Bir proje dosyasında öğeleri oluşturma  
 Öğeleri alt öğesi olarak proje dosyasındaki öğeleri bildirmek bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesi. Öğe türü alt öğenin adıdır. `Include` Öğesinin özniteliği, bu öğe türünü içeren eklenecek öğeler (dosyalar) belirtir. Örneğin, aşağıdaki XML adında bir öğe türü oluşturur `Compile`, iki dosya içerir.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Öğe *file2.cs* öğesi kaldırmayacağına *file1.cs*; bunun yerine, dosya adı için değerleri listesine eklenir `Compile` öğe türü.
  
 Aşağıdaki XML bir her iki dosyada bildirerek aynı öğe türü oluşturur. `Include` özniteliği. Dosya adları noktalı virgülle ayrılır dikkat edin.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="create-items-during-execution"></a>Yürütme sırasında öğeleri oluşturma  
 Dışında olan öğeleri [hedef](../msbuild/target-element-msbuild.md) öğeleri, bir yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında öğe oluşturulduğunda veya değiştirildiğinde aşağıdaki yollarla:  
  
-   Herhangi bir görev, bir öğe gönderebilir. Bir öğe yaymak için [görev](../msbuild/task-element-msbuild.md) bir alt öğesi olmalıdır [çıkış](../msbuild/output-element-msbuild.md) sahip öğe bir `ItemName` özniteliği.  
  
-   [CreateItem](../msbuild/createitem-task.md) görev, bir öğe yayabilir. Bu kullanım önerilmiyor.  
  
-   .NET Framework 3.5, başlangıç `Target` öğeleri [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeler içerebilir öğeler öğesi.  
  
##  <a name="reference-items-in-a-project-file"></a>Bir proje dosyasında öğeleri başvurusu  
 Öğe türlerine proje dosyası boyunca başvurulacak söz dizimini kullanın. @(\<Itemtype >). Örneğin, kullanarak önceki örnekte öğesi türü başvuru `@(Compile)`. Bu söz dizimini kullanarak bu görevi parametre olarak öğe türü belirterek görevlere öğeleri geçirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: derleme dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md).  
  
 Genişletildiğinde, varsayılan olarak, bir öğe türünün öğeleri noktalı virgülle (;) ayrılır. Kullanabileceğiniz sözdizimi @(\<Itemtype >, '\<ayırıcı >') varsayılan dışındaki bir ayırıcı belirtmek için. Daha fazla bilgi için [nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="use-wildcards-to-specify-items"></a>Joker karakter öğelerini belirtmek için kullanın  

Kullanabileceğiniz `**`, `*`, ve `?` her dosyayı ayrı ayrı listelemek yerine bir yapı için girdi olarak bir dosya grubu belirtmek için joker karakter.
  
- `?` Joker karakter, bir tek karakterle eşleşir.
- `*` Joker karakter, sıfır veya daha fazla karakter ile eşleşir.
- `**` Joker karakter dizisi ile eşleşen bir kısmi yol.

Örneğin, tüm belirtebilirsiniz `.cs` projesini içeren bir dizindeki dosyaları dosya proje dosyanızda aşağıdaki öğesini kullanarak.

```xml  
<CSFile Include="*.cs"/>  
```  

Şu öğe tüm seçer `.vb` dosya çubuğunda `D:` sürücü:

```xml  
<VBFile Include="D:/**/*.vb"/>  
```  

Dahil etmek değişmez değer isterseniz `*` veya `?` joker karakter genişletmesi olmadan bir öğe karakterleriyle gerekir [joker karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Joker karakterler hakkında daha fazla bilgi için bkz: [nasıl yapılır: derleme dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md).  

##  <a name="use-the-exclude-attribute"></a>Hariç tutma özniteliği kullanın  
 Öğeler içerebilir `Exclude` belirli öğeler (dosyalar) öğesi türünden dışlar özniteliği. `Exclude` Öznitelik genellikle joker karakterler ile birlikte kullanılır. Örneğin, aşağıdaki XML ekler her *.cs* dışında dosya CSFile öğesi türü dizindeki *DoNotBuild.cs* dosya.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude` Özniteliği tarafından eklenen öğeleri etkiler `Include` her ikisinin de içeren item öğesine özniteliği. Aşağıdaki örnek, dosyayı hariç tutacak mıydı *Form1.cs*, önceki item öğesine eklendi.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Daha fazla bilgi için [nasıl yapılır: dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="item-metadata"></a>Öğe meta verileri  
 Öğe meta veri bilgilerine ek olarak içerebilir `Include` ve `Exclude` öznitelikleri. Bu meta veriler, toplu iş görevleri ve hedefleri için veya öğeler hakkında daha fazla bilgi gerektiren görevler tarafından kullanılabilir. Daha fazla bilgi için [toplu işleme](../msbuild/msbuild-batching.md).  
  
 Proje dosyasında bir öğe alt öğeleri olarak bildirilen bir anahtar-değer çiftleri koleksiyonu meta verilerdir. Meta veri adı alt öğenin adıdır ve meta veri değeri alt öğenin değeridir.  
  
 Meta veriler içeren item öğesine ile ilişkilidir. Örneğin, aşağıdaki XML ekler `Culture` değerine sahip meta veriler `Fr` hem *one.cs* ve *two.cs* öğelerin CSFile öğesi türü.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Bir öğe sıfır veya daha fazla meta veri değerine sahip olabilir. Meta veri değerlerini dilediğiniz zaman değiştirebilirsiniz. Meta verileri boş bir değere ayarlarsanız, etkili bir şekilde derlemeden kaldırın.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Başvuru öğe meta verileri bir proje dosyasında  
 Öğe meta verileri proje dosyası boyunca sözdizimi kullanılarak %(başvurabilirsiniz\<ItemMetadataName >). Belirsizlik varsa, öğe türü adını kullanarak bir başvuru kazanabilir. For example, belirtebileceğiniz %(\<ItemType.ItemMetaDataName >). Aşağıdaki örnek, ileti görevini toplu görüntü meta verileri kullanır. Toplu işleme için öğe meta verileri kullanma hakkında daha fazla bilgi için bkz. [toplu görev işlemede öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Tanınmış öğe meta verisi  
 Bir öğe türüne bir öğe eklendiğinde, bu öğe bazı iyi bilinen meta verilere atanır. For example, tüm öğelerin iyi bilinen meta verilerine de sahip %(\<Filename >), değeri öğenin dosya adıdır. Daha fazla bilgi için [tanınmış öğe meta verisi](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Meta verileri kullanarak öğesi türlerini dönüştürme  
 Meta verileri kullanarak öğe listeleri yeni öğe listelerine dönüştürebilirsiniz. Örneğin, bir öğe türüne dönüştürebilirsiniz `CppFiles` temsil eden öğeleri olan *.cpp* karşılık gelen bir listesini bir dosyaya *.obj* ifade kullanarak dosyaları `@(CppFiles -> '%(Filename).obj')`.  
  
 Aşağıdaki kod oluşturur bir `CultureResource` öğe tüm kopyalarını içeren tür `EmbeddedResource` öğeler `Culture` meta verileri. `Culture` Yeni meta veri değeri meta veri değeri olur `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Daha fazla bilgi için [dönüştüren](../msbuild/msbuild-transforms.md).  
  
##  <a name="item-definitions"></a>Öğe tanımları  
 .NET Framework 3. 5'dan başlayarak, varsayılan meta veri herhangi bir öğe türüne ekleyebilirsiniz [Itemdefinitiongroup öğesi](../msbuild/itemdefinitiongroup-element-msbuild.md). İyi bilinen meta verileri gibi varsayılan meta veri öğesi türünün, belirttiğiniz tüm öğeleri ile ilişkilidir. Açıkça varsayılan meta veri öğesi tanımı geçersiz kılabilirsiniz. Örneğin, aşağıdaki XML verir `Compile` öğeleri *one.cs* ve *three.cs* meta veriler `BuildDay` "Pazartesi" değerine sahip. Kod öğesi verir *two.cs* meta veriler `BuildDay` "Salı" değerine sahip.  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Daha fazla bilgi için [öğesi tanımları](../msbuild/item-definitions.md).  
  
##  <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Öznitelik bir ItemGroup öğelerinin hedefi  
 .NET Framework 3.5, başlangıç `Target` öğeleri [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğeler içerebilir öğeler öğesi. Bu bölümdeki öznitelikleri bir öğe için belirtilen geçerli bir `ItemGroup` olan bir `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Öznitelik Kaldır  
 `Remove` Öznitelik öğesi türünden belirli öğeler (dosyalar) kaldırır. Bu öznitelik .NET Framework 3. 5 ' kullanıma sunulmuştur, ancak yalnızca içinde hedefleri MSBuild 15.0 kadar destekleniyordu.
  
 Aşağıdaki örnek kaldırır her *.config* dosyasından derleme öğe türü.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> KeepMetadata özniteliği  
 Bir öğe içindeki hedef oluşturulursa öğesi öğe içerebilir `KeepMetadata` özniteliği. Bu öznitelik belirtilmezse, adları noktalı virgülle ayrılmış liste belirtilen meta veri kaynak öğeden hedef öğeye aktarılır. Bu öznitelik için boş değer bu belirlemek değil ile aynıdır. `KeepMetadata` Özniteliği, .NET Framework 4. 5 ' tanıtılmıştır.  
  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `KeepMetadata` özniteliği.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> RemoveMetadata özniteliği  
 Bir öğe içindeki hedef oluşturulursa öğesi öğe içerebilir `RemoveMetadata` özniteliği. Bu öznitelik belirtilmezse, tüm meta veri kaynak öğeden hedef öğeye meta veriler hariç, adları adları noktalı virgülle ayrılmış listesi yer alır aktarılır. Bu öznitelik için boş değer bu belirlemek değil ile aynıdır. `RemoveMetadata` Özniteliği, .NET Framework 4. 5 ' tanıtılmıştır.  
  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `RemoveMetadata` özniteliği.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> KeepDuplicates özniteliği  
 Bir öğe içindeki hedef oluşturulursa öğesi öğe içerebilir `KeepDuplicates` özniteliği. `KeepDuplicates` olan bir `Boolean` öğe var olan bir öğeye tam bir kopyasını ise bir öğe için hedef grubu eklenip eklenmeyeceğini belirten özniteliği.  
  
 Kaynak ve hedef öğesi farklı meta veriler ancak aynı dahil etme değeri varsa, bir öğe eklendiğinde bile `KeepDuplicates` ayarlanır `false`. Bu öznitelik için boş değer bu belirlemek değil ile aynıdır. `KeepDuplicates` Özniteliği, .NET Framework 4. 5 ' tanıtılmıştır.  
  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `KeepDuplicates` özniteliği.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)   
 [Nasıl yapılır: derleme dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md)   
 [Nasıl yapılır: dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Öğe tanımları](../msbuild/item-definitions.md)   
 [Toplu işleme](../msbuild/msbuild-batching.md)   
 [Öğe unsuru (MSBuild)](../msbuild/item-element-msbuild.md)