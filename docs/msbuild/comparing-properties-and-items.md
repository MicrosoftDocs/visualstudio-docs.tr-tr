---
title: Özellikleri ve öğeleri karşılaştırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96166caefa749138371dd8a5ab2ea9d496553557
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177120"
---
# <a name="compare-properties-and-items"></a>Özellikleri ve öğeleri karşılaştırma
MSBuild özellikleri ve öğeleri hem de bilgi geçirmek için görevler, koşulları değerlendirin ve proje dosyası boyunca başvurulabilir değerleri depolamak için kullanılır.  
  
-   Özellikler, ad-değer çiftleridir. Daha fazla bilgi için [MSBuild özellikleri](../msbuild/msbuild-properties.md).  
  
-   Genelde dosyaları temsil eden nesneleri öğelerdir. Öğesi nesneleri ilişkili meta verileri koleksiyonlar. Ad-değer çiftleri meta verilerdir. Daha fazla bilgi için [öğeleri](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Skalerler ve vektörleri  
 MSBuild özellikleri yalnızca bir dize değerine sahip ad-değer çiftleri olduğundan, bunlar genellikle olarak açıklanan *skaler*. MSBuild öğesi türlerini öğeleri listesi olduğundan, bunlar genellikle olarak açıklanan *vektör*. Ancak, uygulamada, Özellikler birden çok değer gösterebilir ve öğesi sıfır veya bir öğe olabilir.  
  
### <a name="target-dependency-injection"></a>Hedef Bağımlılık ekleme  
 Özellikler birden çok değeri nasıl gösterebilir görmek için bir hedef oluşturulacak hedefler listesine eklemek için yaygın bir kullanım modeli göz önünde bulundurun. Bu liste genellikle hedef adları noktalı virgülle ayrılmış bir özellik değeri tarafından temsil edilir.  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 `BuildDependsOn` Özelliği genellikle bir hedef bağımsız değişken olarak kullanılan `DependsOnTargets` öznitelik, bir öğe listesine etkili bir şekilde dönüştürmeden. Bu özellik bir hedef eklemek veya hedef yürütme sırasını değiştirmek için geçersiz kılınabilir. Örneğin,  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 CustomBuild hedef hedef listesine ekler vererek `BuildDependsOn` değeri `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 MSBuild 4.0 ile başlayarak, hedef bağımlılık ekleme kullanım dışıdır. Kullanım `AfterTargets` ve `BeforeTargets` yerine öznitelikleri. Daha fazla bilgi için [hedef derleme sırası](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Dizeler ve öğesi listeleri arasında dönüştürmeler  
 MSBuild öğesi türleri ve gerektiği gibi dize değerleri dönüşümleri gerçekleştirir. Bir öğe listesini bir dize değeri nasıl dönüşebilir görmek için bir öğe türü bir MSBuild özellik değeri olarak kullanıldığında ne olacağını göz önünde bulundurun:  
  
```xml  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 OutputDir sahip öğe türü bir `Include` değerine sahip öznitelik "KeyFiles\\; Sertifikaları\\". MSBuild, iki öğeyi bu dizeyi ayrıştırır: KeyFiles\ ve sertifikaları\\. Öğe türü OutputDir OutputDirList özelliğinin değeri kullanıldığında, MSBuild dönüştürür veya "öğe türü noktalı virgülle ayrılmış dizesi düzleştirir" "KeyFiles\\; Sertifikaları\\".  
  
## <a name="properties-and-items-in-tasks"></a>Özellikleri ve öğeleri görevler  
 Özellikleri ve öğeleri, girdileri ve çıktıları MSBuild görevleri olarak kullanılır. Daha fazla bilgi için [görevleri](../msbuild/msbuild-tasks.md).  
  
 Özellikleri görevlere öznitelik olarak geçirilir. Görev içinde bir MSBuild özelliği için ve bir dize değeri dönüştürülebilir bir özellik türü tarafından temsil edilir. Desteklenen özellik türleri dahil `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, ve herhangi türdeki <xref:System.Convert.ChangeType%2A> işleyebilir.  
  
 Öğeleri görevlere geçirilir <xref:Microsoft.Build.Framework.ITaskItem> nesneleri. Görev içinde <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> öğenin değerini temsil eder ve <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> meta verilerini alır.  
  
 Öğe listesine bir öğe türünün bir dizi olarak geçirilebilir `ITaskItem` nesneleri. .NET Framework 3.5 ile başlayarak, öğeleri bir öğe listesinden bir hedef kullanılarak kaldırılabilir `Remove` özniteliği. Öğeleri bir öğe listesinden kaldırılması için bir öğe türü sıfır öğeye sahip olacak şekilde olasıdır. Bir öğe listesini bir göreve iletilmezse, görev kod için bu olasılığı denetlemeniz gerekir.  
  
## <a name="property-and-item-evaluation-order"></a>Özelliği ve öğe değerlendirme sırası  
 Bir yapının değerlendirme aşamasında yapı göründükleri sırayla içeri aktarılan dosyaları dahil edilir. Özellikler ve öğeler aşağıdaki sırayla üç geçiş tanımlanır:  
  
-   Özellikleri tanımlanır ve göründükleri sırayla değiştirdi.  
  
-   Öğe tanımları tanımlanır ve göründükleri sırayla değiştirdi.  
  
-   Öğeleri tanımlanır ve göründükleri sırayla değiştirdi.  
 
 
 Bir derleme yürütme aşamasında özellikler ve hedefler içinde tanımlanan öğeleri birlikte tek bir aşamada göründükleri sırayla değerlendirilir.  
 
 Ancak, bu Yazının tamamını değildir. Bir özelliği, öğe tanımı veya öğesi tanımlı değilken değeri değerlendirilir. İfade değerlendirici değeri belirten dizeyi genişletir. Dize genişletme derleme aşamaya bağlıdır. Daha ayrıntılı bir özelliği ve öğe değerlendirme sırası şöyledir:  
  
-   Bir yapının değerlendirme aşamasında:  
  
    -   Özellikleri tanımlanır ve göründükleri sırayla değiştirdi. Özellik işlevleri yürütülür. Özellik değerlerinde form $(PropertyName) ifadeler içinde genişletilir. Özellik değeri, genişletilmiş ifade ayarlanır.  
  
    -   Öğe tanımları tanımlanır ve göründükleri sırayla değiştirdi. Özellik işlevleri ifadeler içinde zaten genişletilmiştir. Meta veri değerleri için genişletilmiş ifadeleri ayarlanır.  
  
    -   Öğesi türleri tanımlı ve göründükleri sırayla değiştirdi. Form @(ItemType) içindeki öğe değerlerini genişletilir. Öğe dönüştürmeler de genişletilir. Özellik işlevleri ve değerleri, ifadeler içinde zaten genişletilmiştir. Öğe listesi ve meta verileri değerlerini genişletilmiş ifadeleri için ayarlanır.  
  
-   Bir derleme yürütme aşaması sırasında:  
  
    -   Özellikler ve hedefler içinde tanımlanan öğeleri birlikte göründükleri sırayla değerlendirilir. Özellik işlevleri yürütülür ve özellik değerlerini ifadeler içinde genişletilir. Öğe değerlerini ve öğesi dönüştürmeler de genişletilir. Özellik değerleri, öğe türü değerlerini ve meta veri değerleri için genişletilmiş ifadeleri ayarlanır.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Hafif etkilerini değerlendirme sırası  
 Bir yapının değerlendirme aşamasında, özellik değerlendirmesini öğesi değerlendirme önce gelir. Bununla birlikte, Özellikler öğesi değerlerine bağımlı görünen değerlere sahip olabilir. Aşağıdaki komut dosyası düşünün.  
  
```xml  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 İleti görevi yürütme şu ileti görüntülenir:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Bunun nedeni, değerini `KeyFileVersion` aslında dize "\@('% (sürüm)' KeyFile ->)". Öğe ve öğesi dönüştürmeleri genişletilmemiş özelliği ilk tanımlandığında, bu nedenle `KeyFileVersion` özelliği genişletilmemiş dize değeri atandı.  
  
 İleti görevi işlediğinde, derleme yürütme aşamasında MSBuild dizeyi genişletir. "\@('% (sürüm)' KeyFile ->)" yield "1.0.0.3" için.  
  
 Özellik ve öğesi grupları sırayla tersine çevrilmiş bile aynı iletiyi görüneceği dikkat edin.  
  
 İkinci bir örnek olarak, özellik ve öğesi grupları hedefleri içinde bulunan zaman neler olabileceğini göz önünde bulundurun:  
  
```xml  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 İleti görevini şu ileti görüntülenir:  
  
```  
KeyFileVersion:   
```  
  
 Derleme yürütme aşamasında hedefleri içinde tanımlanan grupları özelliği ve öğe değerlendirilir olmasıdır yukarıdan aşağıya doğru aynı anda. Zaman `KeyFileVersion` tanımlanan `KeyFile` bilinmiyor. Bu nedenle, öğe dönüşümü boş dize olarak genişletir.  
  
 Bu durumda, özgün iletinin özelliği ve öğe grupların sırasını ters geri yükler:  
  
```xml  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Değerini `KeyFileVersion` "1.0.0.3" ve için "\@('% (sürüm)' KeyFile ->)". İleti görevini şu ileti görüntülenir:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)