---
title: DslDefinition.dsl Dosyası
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5988876bc1cdc7d186efb60d7d3875f9946bfc7d
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967525"
---
# <a name="the-dsldefinitiondsl-file"></a>DslDefinition.dsl Dosyası

Bu konuda Dsl projedeki DslDefinition.dsl dosyası yapısını açıklayan bir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] tanımlayan çözüm bir *etki alanına özgü dil*. DslDefinition.dsl dosyası sınıflar ve ilişkiler diyagram, şekil, bağlayıcılar, serileştirme biçimi ile birlikte bir etki alanına özgü dil açıklar ve **araç kutusu** etki alanına özgü dil ve düzenleme araçları. Bir etki alanına özgü dil çözümünde DslDefinition.dsl dosyasındaki bilgilere göre bu araçların tanımlar kod oluşturulur.

Genel olarak, kullandığınız *etki alanına özgü dil tasarımcısını* DslDefinition.dsl dosyası düzenlenecek. Ancak, ham biçimiyle XML ve DslDefinition.dsl dosyası XML düzenleyicisinde açabilirsiniz. Dosyayı içeren bilgiler ve hata ayıklama ve uzantı amacıyla nasıl düzenlendiğini anlamak yararlı bulabilirsiniz.

Bu konudaki örnekler bileşen diyagramı çözüm şablonundan alınır. Bir örnek için bileşeni modelleri çözüm şablonu temel alan bir etki alanına özgü dil çözümü oluşturun. DslDefinition.dsl dosyası, çözüm oluşturduktan sonra etki alanına özgü dil Tasarımcısı'nda görünür. Dosyayı kapatın, projeyi sağ **Çözüm Gezgini**, işaret **birlikte Aç**, tıklayın **XML Düzenleyicisi**ve ardından **Tamam**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>DslDefinition.dsl dosyası bölümleri

Kök öğe \<Dsl >, etki alanına özgü dil, ad alanı adı özniteliklerini tanımlamak ve birincil ve ikincil sürüm numaraları için sürüm oluşturma. `DslDefinitionModel` Şemasını tanımlayan içeriği ve yapısı için geçerli bir DslDefinition.dsl dosyası.

Alt öğeleri \<Dsl > kök öğesi aşağıdaki gibidir:

### <a name="classes"></a>Sınıflar

Bu bölümde, üretilen kodda bir sınıfın oluşturduğu her etki alanı sınıfı tanımlar.

### <a name="relationships"></a>İlişkiler

Bu bölümde, modeldeki her ilişkiyi tanımlar. Kaynak ve hedef bir ilişkinin iki tarafında temsil eder.

### <a name="types"></a>Türler

Bu bölümde, her tür ve ad alanı tanımlar. Etki alanı özellikleri, iki tür vardır. `DomainEnumerations` modelde tanımlanmıştır ve DomainModel.cs türleri üretmek. `ExternalTypes` başka bir yerde tanımlanan türlere başvurur (gibi `String` veya `Int32`) ve her şeyi oluşturmaz.

### <a name="shapes"></a>Şekiller

Bu bölümde, model Tasarımcısı'nda nasıl göründüğünü açıklayan şekilleri tanımlar. Bu geometrik şekiller, Diyagram bölümünde modeli sınıflarda eşlenir.

### <a name="connectors"></a>Bağlayıcılar

Bu bölümde Tasarımcısı'nda görünen bağlayıcıları görünümünü tanımlar. Bu geometrik stili açıklamalar modeli diyagramı bölümünde belirli ilişkiler eşlenir.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Bu bölümde, serileştirme düzenini tanımlar ve her sınıfın bir dosyaya nasıl kaydedileceği hakkında ek bilgi sağlar.

### <a name="explorerbehavior"></a>ExplorerBehavior

Bu bölüm tanımlar nasıl **DSL Gezgini** kullanıcı bir model düzenlerken penceresi görüntülenir.

### <a name="connectionbuilders"></a>ConnectionBuilders

Bu bölümde her bağlayıcı aracını (her iki sınıf arasında bağlantı yapmak için araç bağlı olarak) için bağlantı oluşturucuyu tanımlar. Bu bölümde, kaynak ve hedef sınıf bağlanabilir olup olmadığını belirler.

### <a name="diagram"></a>Diyagram

Bu bölüm bir diyagram tanımlar ve arka plan rengi gibi özellikleri ve kök sınıfı belirtmek için kullanın. (Kök etki alanı sınıfı, bir bütün olarak diyagram tarafından temsil edilen sınıftır.) Ayrıca Diyagramı bölüm Şekil veya her bir etki alanı sınıfı ya da ilişkiyi temsil eden bağlayıcı belirtin, ShapeMap ve ConnectorMap öğeleri içerir.

### <a name="designer"></a>Tasarımcı

Bu bölümde, bir araya getiren bir tasarımcı (Düzenleyicisi) tanımlayan bir **araç kutusu**, doğrulama ayarları, bir diyagram ve bir seri hale getirme düzeni. Tasarımcı bölüm ayrıca, genellikle kök sınıfı diyagramın olan modeli, kök sınıfı tanımlar.

### <a name="explorer"></a>Gezgini

Bu bölüm tanımlar **DSL Gezgini** (XmlSerializationBehavior bölümünde tanımlanan) davranışı.

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Bilinen Adlardaki niteleyiciyi DslDefinition.dsl dosyası

DslDefinition.dsl dosyası boyunca belirli öğeleri çapraz başvuru yapmak için bilinen adlar kullanabilirsiniz. Örneğin, bir kaynak alt ve bir hedef alt her ilişki tanımı içerir. Her bir alt ilişkinin ile bağlantılı nesne sınıfının ad içerir:

```
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Genellikle, başvurulan öğenin ad alanı (Bu örnekte, `Library` etki alanı sınıfı) (Bu durumda, LibraryHasMembers etki alanı ilişkisi) başvuru öğesi ile aynıdır. Bu gibi durumlarda ad, yalnızca sınıf adını vermeniz gerekir. Aksi halde, tam form /Namespace/Name kullanmanız gerekir:

```
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Bilinen ad sistem XML ağacındaki eşdüzey farklı adlara sahip olmasını gerektirir. Örneğin, iki sınıf aynı ada sahip bir etki alanına özgü dil tanımı kaydetmeyi denerseniz, bu nedenle, doğrulama hataları oluşur. Böylece, doğru bir şekilde daha sonra yeniden yükleyebilirsiniz DslDefinition.dsl dosyası kaydetmeden önce her zaman böyle yinelenen ad hataları düzeltmeniz gerekir.

Bilinen ad türünün her türünde: DomainClassMoniker, DomainRelationshipMoniker, ve benzeri.

## <a name="types"></a>Türler

Türler bölümüne DslDefinition.dsl dosyası içeren tüm özelliklerin türleri belirtir. İki tür içinde bu tür ayrılır: System.String gibi dış türler ve numaralandırılmış türler.

### <a name="external-types"></a>Dış türler

Yalnızca bazıları kullanılsa bileşen diyagramı örneği bir dizi standart basit türlerden listeler.

Her bir dış tür tanımı yalnızca bir ad ve dize ve sistemi gibi bir ad alanı oluşur:

```
<ExternalType Name="String" Namespace="System" />
```

Türlerinin tam adlarını eşdeğer derleyici anahtar sözcükler "dize" gibi yerine kullanılır.

Dış türler, standart kitaplık türleri için sınırlı değildir.

### <a name="enumerations"></a>Numaralandırmalar

Tipik bir sabit listesi belirtimi şu örnektekine benzer:

```
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

`IsFlags` Özniteliği denetimleri tarafından oluşturulan kodun önekli olmadığını `[Flags]` ortak dil çalışma zamanı (CLR) özniteliği, numaralandırma değerlerinin Bitsel birleştirilebilir olup olmadığını belirler. Bu öznitelik ayarlanırsa true değişmez değerleri iki power değerlerini belirtmeniz gerekir.

## <a name="classes"></a>Sınıflar

Herhangi bir etki alanına özgü dil tanımı'ndaki öğelerin çoğu doğrudan veya dolaylı olarak örneklerini `DomainClass`. Adornerset'in alt `DomainClass` dahil `DomainRelationship`, `Shape`, `Connector`, ve `Diagram`. `Classes` DslDefinition.dsl dosyası bölümünü alan sınıfları listeler.

Her sınıf, bir özellik kümesine sahiptir ve bir temel sınıfa sahip. Bileşen Diyagramı örnekte `NamedElement` sahip bir Özet sınıf bir `Name` türü olan dize özelliği:

```
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` olduğu gibi birkaç başka sınıfların temel `Component`, ek olarak kendi özelliklerine sahip `Name` öğesinden devralınan özelliği `NamedElement`. Bilinen ad başvuru BaseClass alt düğüm içerir. Başvurulan sınıfı aynı ad alanında olduğundan, adı yalnızca bilinen adı gereklidir:

```
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

(İlişkileri, şekiller, bağlayıcılar ve diyagramları dahil) her etki alanı sınıfı, bu öznitelikler ve alt düğümleri sahip olabilir:

-   **Id.** Bu öznitelik bir GUID'dir. Dosyasındaki bir değer belirtmezseniz, etki alanına özgü dil tasarımcısını, bir değer oluşturur. (Bu belgede çizimleri, bu öznitelik genellikle yer kazanmak için atlandı.)

-   **Ad ve Namespace.** Bu öznitelikler oluşturulan kodda sınıfın ad alanı ve adını belirtin. Birlikte, etki alanına özgü dil içinde benzersiz olmalıdır.

-   **InheritanceModifier.** Bu, "soyut", "korumalı" veya hiçbiri özniteliğidir.

-   **DisplayName.** Bu öznitelik görünen addır **özellikleri** penceresi. DisplayName özniteliğini, boşluk ve noktalama işareti içerebilir.

-   **GeneratesDoubleDerived.** Bu öznitelik ayarlanırsa true, iki sınıf oluşturulur ve diğer öğesinin biridir. Oluşturulan tüm yöntemler temel, ve oluşturucular alt sınıfta. Bu öznitelik ayarlayarak, özel kod içinde oluşturulan tüm yöntemin üzerine yazabilir.

-   **HasCustomConstructor**. Bu öznitelik ayarlanırsa kendi sürüm yazabilmesi amacıyla true Oluşturucusu üretilen koddan atlanır.

-   **Öznitelikleri**. Bu öznitelik, oluşturulan sınıfın CLR öznitelikleri içerir.

-   **BaseClass**. Bir temel sınıf belirtirseniz, aynı türde olmalıdır. Örneğin, bir etki alanı sınıfı, temel olarak başka bir etki alanı sınıfı olmalıdır ve bir bölme şekli, bölme şekli olması gerekir. Bir temel sınıf belirtmezseniz, oluşturulan kodda sınıfı bir standart framework sınıfından türetilir. Bir etki alanı sınıfın türetildiği gibi `ModelElement`.

-   **Özellikleri**. Bu öznitelik, işlem denetiminde saklanır ve modeli kaydettiğinizde kalıcı özellikleri içerir.

-   **ElementMergeDirectives**. Her öğe birleştirme yönergesi, bir üst sınıf örneği için başka bir sınıfın farklı bir örneğine nasıl eklenir denetler. Bu konunun ilerleyen bölümlerinde öğe birleştirme yönergeleri hakkında daha fazla ayrıntı bulabilirsiniz.

-   Listelenen her bir etki alanı sınıfı için C# sınıfı oluşturulan `Classes` bölümü. C# sınıfları Dsl\GeneratedCode\DomainClasses.cs içinde oluşturulur.

### <a name="properties"></a>Özellikler

Her bir etki alanı özellik, bir ad ve bir türü vardır. Ad etki alanı sınıfı ve geçişli temelleri içinde benzersiz olmalıdır.

Listelenenler birine türüne başvurmalıdır `Types` bölümü. Genel olarak, ad, ad alanı içermelidir.

```
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Her etki alanı özelliği bu öznitelikler de sahip olabilir:

-   **IsBrowsable**. Bu öznitelik, özellik görüntülenip görüntülenmeyeceğini belirler **özellikleri** kullanıcı üst sınıfın bir nesnesi tıkladığında penceresi.

-   **IsUIReadOnly**. Bu öznitelik özelliğinde kullanıcı değiştirip değiştiremeyeceğini belirler **özellikleri** penceresi veya bir dekoratör özelliği sunulur.

-   **Tür**. Bu öznitelik, Normal, hesaplanmış veya CustomStorage ayarlayabilirsiniz. Hesaplanan bu öznitelik ayarlanırsa, değerini belirleyen özel kod sağlaması gerekir ve özellik salt okunur olacaktır. CustomStorage için bu öznitelik ayarlanırsa, hem alan ve değerleri ayarlar kod sağlamanız gerekir.

-   **Iselementname**. Bu öznitelik ayarlanırsa üst sınıfın bir örneği oluşturulduğunda true değeri otomatik olarak benzersiz bir değere ayarlanır. Bu öznitelik ayarlanabilir bir dize türünde olmalıdır her sınıfta yalnızca tek bir özellik için true. Bileşen Diyagramı örnekte `Name` özelliğinde `NamedElement` sahip `IsElementName` true olarak ayarlanmış. Her bir kullanıcının oluşturduğu bir `Component` öğesi (işlevinden devralan `NamedElement`), adı "Component6." gibi bir şekilde otomatik olarak başlatılır

-   `DefaultValue`. Bu öznitelik belirttiyseniz, bu özniteliği bu sınıfın yeni örneklerini için belirttiğiniz değeri atanır. Varsa `IsElementName` , DefaultValue özniteliği belirtir yeni dizenin ilk bölümü ayarlanmış.

-   **Kategori** üst bilgisi altında özellik görünür **özellikleri** penceresi.

## <a name="relationships"></a>İlişkiler

`Relationships` Bölümü, etki alanına özgü dil tüm ilişkileri listeler. Her `Domain Relationship` ikili ve yönlendirilmiş bir hedef sınıf üyeleri için bir kaynak sınıfının üyesi bağlama. Kaynak ve hedef sınıflarını genellikle etki alanı sınıflardır, ancak diğer ilişkiler ilişkileri de izin verilir.

Örneğin, bağlantı ilişki OutPort sınıf üyelerini InPort sınıfın üyelerine bağlar. İlişkinin her bağlantı örneğini bir OutPort örneği bir InPort örneğine bağlanır. İlişki olduğundan çok-çok, birçok bağlantı bağlantılar üzerindeki kaynaklarıyla her OutPort olabilir ve her InPort örneği hedeflemek birçok bağlantı bağlantı olabilir.

### <a name="source-and-target-roles"></a>Kaynak ve hedef rolleri

Her ilişki aşağıdaki özniteliklere sahip bir kaynak ve hedef rolleri içerir:

-   `RolePlayer` Özniteliği başvuruda bağlı örnek etki alanı sınıfı: OutPort kaynağı için hedef InPort.

-   `Multiplicity` Özniteliğine sahip dört olası değerler (ZeroMany, ZeroOne, tek ve OneMany). Bu öznitelik, bir rol oyuncusu ile ilişkilendirilebilir bu ilişkisine ait bağlantıların sayısını ifade eder.

-   `PropertyName` Öznitelik sınıfı diğer uçtaki nesnelere erişmek için yürütme rolü kullanılan adını belirtir. Bu ad, şablon veya özel kod, ilişki geçirmek için kullanılır. Örneğin, `PropertyName` özniteliği kaynak rolünün `Targets`. Bu nedenle, aşağıdaki kodu çalışır:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Kural gereği, çokluğu ZeroMany veya OneMany ise özellik adları çoğuldur.

     Karşı rol kaç olabilir bir rolün çokluğu başvuruyor her bu rol örneği ile ilişkili olabilir. Örneğin, hedef rolü ilişki ComponentHasPorts sahip `RolePlayer` bağlantı noktasına özniteliği `PropertyName` özniteliği bileşene ayarlanmasına izin vermez ve `Multiplicity` özniteliği ayarlanmış ZeroOne için. Bu nedenle, bu rolü kullanmak için uygun kodu verilmiştir:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

-   Rolün `Name` ilişki sınıfı içinde bir bağlantının bu amaçla başvurmak için kullanılan addır. Her bağlantı yalnızca bir örneği her sonunda sahip kural olarak, bir rol adı her zaman tekil, olmasıdır. Aşağıdaki kod işe yarar:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

-   Varsayılan olarak, `IsPropertyGenerator` özniteliği true. False olarak ayarlanmışsa, özellik rol oyuncusu sınıf üzerinde oluşturulur. (Bu durumda, `op.Targets`, örneğin, çalışmaz). Ancak, ilişkinin çapraz geçiş yapamaz veya özel kod ilişki açıkça kullanıyorsa bağlantılara erişim elde etmek için özel kod kullanma yine de mümkündür:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>İlişki öznitelikleri

Öznitelikler ve tüm sınıflar için kullanılabilen alt düğümleri ek olarak, her ilişki bu özniteliklere sahiptir:

-   **Isembedding**. Bu Boole öznitelik ilişkisi ekleme ağacın parçası olup olmadığını belirtir. Her model ile kendi gömme ilişkisi bir ağaç oluşturması gerekir. Model kökü olmadığı sürece her etki alanı sınıfı, bu nedenle en az bir gömme ilişkisi hedef olmalıdır.

-   **AllowsDuplicates**. Varsayılan olarak yanlıştır, bu Boolean özniteliği "many" çeşitlilik hem kaynak hem de hedef olan ilişkileri için geçerlidir. Dil kullanıcılar, aynı ilişki birden fazla bağlantı tarafından tek bir kaynak ve hedef öğe çiftinin bağlanarak olup olmadığını belirler.

## <a name="designer-and-toolbox-tabs"></a>Tasarımcı ve araç kutusu sekmeleri

Ana bölümünü **Tasarımcısı** DslDefinition.dsl dosyası bölümüdür **ToolboxTab** öğeleri. Bir tasarımcı birkaç bu öğelerin her biri oluşturulan tasarımcının headed bir bölümde temsil eden olabilir **araç kutusu**. Her **ToolboxTab** bir veya daha fazla öğe içerebilir **ElementTool** öğeleri **ConnectionTool** öğelerin veya her ikisi de.

Öğe araçlarını, belirli bir alan sınıfına bir örneğini oluşturabilirsiniz. Kullanıcı bir öğeyi aracı diyagram üzerine sürüklediğinde, sonuç bu konunun ilerleyen bölümlerinde öğe birleştirme yönergeleri hakkında bölümünde belirtildiği gibi öğe birleştirme yönergeleri tarafından belirlenir.

Her bağlantı aracını, belirli bir bağlantı Oluşturucu çağırabilirsiniz. Birden fazla ilişki türünde, burada kullanıcı bağlantı oluşturucular hakkında bölümünde açıklandığı gibi fareye tıklayana bağlı olarak, bir bağlantı Oluşturucu oluşturabilirsiniz.

Ne tür bir araç, şekiller veya bağlayıcıları doğrudan oluşturur. Her bir alan sınıfıyla ya da bir etki alanı ilişkisi başlatır; Şekil ve bağlayıcı eşlemeleri, ardından bu alan sınıfıyla ya da etki alanı ilişkisi nasıl görüneceğini belirler.

## <a name="paths"></a>Yolları

DslDefinition.dsl dosyası çeşitli konumlarda etki alanı yollarını görünür. Bu yolları (diğer bir deyişle, bir etki alanına özgü dil örneğini) başka bir model bir dizi öğesinden bir bağlantı belirtin. Basit ama ayrıntılı yolu sözdizimi.

DslDefinition.dsl dosyası içinde yolları görünür `<DomainPath>...</DomainPath>` etiketler. Yolları, birden çok bağlantı gidebilirsiniz olsa da, uygulamada çoğu örnekleri yalnızca bir bağlantı çapraz geçiş yapma.

Bir yolu, segmentleri bir dizi oluşur. Her bağlantı için bir nesne veya bir nesneye yönelik bağlantıyı bir atlama segmenttir. Bu nedenle, atlama genellikle uzun bir yolda diğer. İlk atlamanın bir nesneden bir bağlantıdır, ikinci atlama bağlantının diğer ucundaki nesneye, üçüncü atlama ileri bağlantı vb. için. Bazen bu sıralı bir ilişki kendisini kaynak veya hedef başka bir ilişkinin olduğu istisnadır.

Her segmentinde bir ilişki adı ile başlar. Bir nokta ve özellik adı ilişki nesnesi bağlantı atlama önündeki: "`Relationship . Property`". Bir bağlantı nesnesi atlama ilişki ünlem işareti ve rol adının önünde: "`Relationship ! Role`".

Bileşen Diyagramı örneği için InPort ParentElementPath ShapeMap, bir yolda içerir. Bu yol şu şekilde başlar:

```
    ComponentHasPorts.Component
```

Bu örnekte, InPort ComponentPort sınıfıdır ve ComponentHasPorts bir ilişkisi vardır. Özelliği, bileşen adı verilir.

C# bu modelinde yazarken, tek bir adımda bir bağlantı üzerinden her, ilişkili sınıfları ilişki oluşturan özelliğini kullanarak atlayabilirsiniz:

```
     InPort port; ...  Component c = port.Component;
```

Ancak, iki atlama yolu sözdiziminde açıkça yapmanız gerekir. Bu gereksinimden dolayı Ara Bağlantı daha kolay erişebilirsiniz. Aşağıdaki kod, bağlantıdan atlama bileşenine tamamlar:

```
    ComponentHasPorts.Component / ! Component
```

(Önceki kesime olduğu gibi aynı olduğu ilişki adı atlayabilirsiniz.)

## <a name="element-merge-directives"></a>Öğe birleştirme yönergeleri

Dil Kullanıcı, bir öğe sürüklediğinde **araç kutusu** diyagram üzerine Aracı'nın sınıfının bir örneği oluşturulur. Ayrıca, bu örneği ve var olan model öğeleri arasında bağlantılar yapılır. Bileşenleri veya açıklamalar gibi bazı öğeler dil kullanıcı bunları sürüklediğinde oluşturulur **araç kutusu** diyagramın boş bir bölümüne sürükleyin. Diğer öğeleri dil kullanıcı bunları diğer konak öğeleri sürüklediğinde oluşturulur. Örneğin, dil kullanıcı, bir bileşen üzerine sürüklediğinde OutPort ya da InPort oluşturulur.

Yalnızca konak sınıfı bir öğe birleştirme yönergesinde sınıfına ait yeni bir öğe varsa bileşeni gibi olası bir konak sınıfının yeni bir öğe kabul eder. Örneğin, adı DomainClass düğümle "Component" = içerir:

```
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Dizin düğüm altında sınıf ad kabul edilebilir öğe sınıfı başvuruyor. Bu durumda, ComponentPort InPort ve OutPort soyut temel sınıf ' dir. Bu nedenle, söz konusu öğelerin ya da kabul edilebilir.

ComponentModel, kök sınıfı dilinin bileşenleri ve açıklamalar için öğe birleştirme yönergeleri sahiptir. Diyagramın boş parçalarını temsil ettiği kök sınıfı için dil kullanıcı bu sınıfların öğeleri doğrudan diyagram üzerine sürükleyebilirsiniz. Bununla birlikte, ComponentModel ComponentPort için hiçbir öğe birleştirme yönergesinde vardır. Bu nedenle, dil kullanıcı doğrudan diyagram üzerine InPorts veya OutPorts sürükleyemezsiniz.

Öğe birleştirme yönergesi, böylece yeni bir öğe tümleştirin veya mevcut modele birleştirme hangi bağlantıyı veya bağlantıları oluşturulan belirler. Bir ComponentPort için ComponentHasPorts örneği oluşturulur. DomainPath yeni öğe eklenecek bağlantı noktaları, hem ilişki hem de üst sınıfın özelliği tanımlar.

Bir öğe birleştirme yönergesinde birden fazla bağlantı oluşturma yolundaki ekleyerek, birden fazla bağlantı oluşturabilirsiniz. Yollardan biri gömülü olması gerekir.

Birden fazla bölüm bir bağlantı oluşturma yolu kullanabilirsiniz. Bu durumda, hangi bağlantı oluşturulması gereken son segmenti tanımlar. Önceki bölümleri yeni bağlantısının oluşturulması gereken nesnenin üst sınıftan gidin.

Örneğin, bu öğe birleştirme yönergesi için bileşen sınıfı ekleyebilirsiniz:

```
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Dil kullanıcılar yorum bir bileşen üzerine sürükleyin ve bileşen bağlantısını içeren bir otomatik olarak oluşturulan yeni yorum varsa olabilir.

İlk bağlantı oluşturma yolundaki gelen gider `Component` için `ComponentModel` ve ardından Gömme ilişkisi örneği oluşturan `ComponentModelHasComments`. İkinci bağlantı oluşturma yolu, yeni açıklama bileşen konaktan başvuru ilişkisi CommentsReferenceComponents bağlantısını oluşturur. Tüm bağlantı oluşturma yolları ana sınıf ile başlamalı ve bir bağlantıyı yeni oluşturulan sınıf doğrultusunda bu adımları bitmelidir.

## <a name="xmlclassdata"></a>XmlClassData

Sağlanan ek bilgileri (ilişkileri ve diğer alt türleri dahil) her etki alanı sınıfı olabilir bir `XmlClassData` düğümünün altında görüntülenen `XmlSerializationBehavior` DslDefinition.dsl dosyası bölümünü. Bu bilgileri özellikle, bir dosyaya bir modeli kaydettiğinizde sınıfı bir örneğini serileştirilmiş biçiminde nasıl depolandığını ilgilidir.

Oluşturulan çoğunu kod `XmlSerializationBehavior` etkileri olan `Dsl\GeneratedCode\Serializer.cs`.

Her `XmlClassData` düğüm, bu alt düğümleri ve öznitelikleri içerir:

-   Verilerinin geçerli olduğu sınıf başvuran bir bilinen ad düğümü.

-   **XmlPropertyData** sınıf üzerinde tanımlanan her bir özellik için.

-   **XmlRelationshipData** sınıfı kaynaklanan her ilişki için. (İlişki de kendi XmlClassData düğümlerin vardır.)

-   **TypeName** oluşturulan kodda serileştirme yardımcı sınıf adını belirleyen dize özniteliği.

-   **ElementName** XML etiketi bu sınıfın serileştirilmiş örneklerinin belirleyen bir dize. İlk harfini, küçük harf olması dışında Kural gereği, ElementName genellikle sınıfı adıyla aynıdır. Örneğin, bir örnek model dosyası aşağıdakiler ile başlar:

    ```
    <componentModel ...
    ```

-   **MonikerElementName** kullanıcının serileştirilmiş modeli dosyalarında. Bu öznitelik, bu sınıf başvuran bir bilinen ad tanıtır.

-   **MonikerAttributeName**, XML özniteliği bir bilinen ad içinde adını tanımlar. Bu seri hale getirilmiş bir kullanıcının dosya parçasında tanımlanan etki alanına özgü dil yazarı **MonikerElementName** "inPortMoniker" olarak ve **MonikerAttributeName** "path" olarak:

    ```
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Bir bağlantı Oluşturucu her bağlantı aracı için tanımlanır. Her bağlantı Oluşturucu her biri bir veya daha fazla SourceDirective öğeleri ve bir veya daha fazla TargetDirective öğeleri içeren bir veya daha fazla atanamayan öğelerden oluşur. Bağlantı aracını tıklandıktan sonra kullanıcı bir bağlantı SourceDirective öğeleri listesinde görüntülenen model öğesine eşlenen herhangi bir şekil başlatabilirsiniz. Bağlantının ardından TargetDirective öğeleri listesinde görünen bir öğeye eşlenmiş bir şekil üzerinde tamamlanabilir. İlişki örneği sınıfının bağlantısı burada başlatıldı tarafından belirlenen atanamayan öğesi bağlıdır.

### <a name="xmlpropertydata"></a>XmlPropertyData

A **DomainPropertyMoniker** öznitelik verileri başvurduğu özelliği tanımlar. Bu öznitelik, kapsayan ClassData'nın sınıfın bir özelliği olmalıdır.

**XmlName** özniteliği XML içinde görünmesi gereken şekilde karşılık gelen bir öznitelik adı sağlar. İlk harfi küçük harf olması dışında kural olarak, bu dize özellik adı olarak aynıdır.

Varsayılan olarak, **gösterimi** öznitelik, öznitelik için ayarlanır. Varsa **gösterimi** öğe, bir alt kümesi düğümü XML'de oluşturulur. Varsa **gösterimi** olan Yoksay olarak ayarlanmıştır, özelliği değil serileştirilmiş.

**Ismonikerkey** ve **Ismonikerqualifier** öznitelikleri üst sınıfın örneğini tanımlayan bir rol bir özellik sunar. Ayarlayabileceğiniz **Ismonikerkey** tanımlanan veya bir sınıf tarafından devralınan bir özellik için true. Bu öznitelik, üst sınıfın tek bir örneğini tanımlar. Ayarlamak için özellik `IsMonikerKey` genellikle bir veya başka bir anahtar tanımlayıcı adıdır. Örneğin, `Name` dize özelliğidir NamedElement ve türetilmiş sınıflarının için bilinen ad anahtarı. Kullanıcı, bir model dosyasını kaydettiğinde, bu öznitelik ilişkileri ekleme ağacında Eşdüzey öğeleri arasında her örneği için benzersiz değerler içermelidir.

Serileştirilmiş modeli dosyasında, bir öğenin tam ad, her noktasında bilinen ad anahtarı Alıntısı ilişkileri ekleme ağaç modeli kökünden yoludur. Örneğin, model kök dizininde sırayla katıştırılmış bileşenleri içinde InPorts katıştırılır. Bu nedenle geçerli bilinen adı şöyledir:

```
<inPortMoniker name="//Component2/InPort1" />
```

Ayarlayabileceğiniz **Ismonikerqualifier** özniteliği için bir dize özelliğini ve bir öğenin tam adı oluşturmak için ek bir yol sağlar. Örneğin, DslDefinition.dsl dosyası içinde **Namespace** bir bilinen ad niteleyicisi olduğundan.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

Bir seri hale getirilmiş model dosyası içinde bağlantılar (ilişkilerinin hem ekleme hem de başvuru) ilişki kaynak tarafının alt düğümler tarafından temsil edilir. İlişki eklemek için bir alt ağacı alt düğüm içerir. Başvuru ilişkilerini için başka bir ağacın parçası başvuran bir bilinen ad alt düğüm içerir.

**XmlRelationshipData** özniteliğini bir **XmlClassData** özniteliği, tam olarak nasıl alt düğümleri kaynak öğesi içinde iç içe tanımlar. Bir kaynak etki alanı sınıfı üzerindeki her ilişkinin varsa **XmlRelationshipData** özniteliği.

**DomainRelationshipMoniker** özniteliği bir sınıf üzerinde kaynaklanan ilişkileri tanımlar.

**RoleElementName** özniteliği alt düğüm seri hale getirilmiş verileri alır XML etiket adı sağlar.

Örneğin, DslDefinition.dsl dosyası içerir:

```
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Bu nedenle, seri hale getirilmiş dosya içeriyor:

```
<component name="Component1"> <!-- parent ->
   <ports> <!-- role ->
     <outPort name="OutPort1"> <!-- child element ->
       ...
     </outPort>
   </ports> ...
```

Varsa **UseFullForm** özniteliği true, ek bir koruma katmanı iç içe geçme sunulmuştur. Bu katman, ilişkinin kendisini temsil eder. Öznitelik, ilişki özelliklere sahipse true olarak ayarlanmalıdır.

```
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Seri hale getirilmiş dosya içeriyor:

```
<outPort name="OutPort1">  <!-- Parent ->
   <targets>  <!-- role ->
     <connection sourceRoleName="X">  <!-- relationship link ->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->
     </connection>
    </targets>
  </outPort>
```

(Alt öğe ve öznitelik adları sağlar, kendi XML sınıfı verilerinde bağlantı ilişkisi yok.)

Varsa **OmitElement** özniteliği true olarak ilişki rolü adı, seri hale getirilmiş dosya kısaltmasıdır ve iki sınıf birden fazla ilişki varsa belirsizliği atlanır. Örneğin:

```
<component name="Component3">
  <!-- only one relationship could get here: ->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Etki alanına özgü dil tanımı serileştirme

DslDefinition.dsl dosyası ve bir etki alanına özgü dil tanımına uyan kendisini seri hale getirilmiş bir dosyasıdır. XML serileştirme tanımları bazı örnekleri şunlardır:

-   **DSL** RootClass düğüm ve sınıf diyagramı. DomainClass DomainRelationship ve diğer öğeleri altında katıştırılmış `Dsl`.

-   **Sınıflar** olduğu **RoleElementName** etki alanına özgü dil ve DomainClass arasındaki ilişki.

```
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

-   **XmlSerializationBehavior** özniteliği altında gömüldüğü `Dsl` özniteliği, ancak **OmitElement** gömme ilişkisi üzerinde öznitelik ayarlandı. Bu nedenle, Hayır `RoleElementName` müdahalesi özniteliği. Aksine, bir **ClassData** özniteliği `RoleElementName` gömme ilişkisi özniteliği bir **XmlSerializationBehavior** özniteliğini ve bir **XmlClassData** özniteliği.

```
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

-   ConnectorHasDecorators gömme ilişkisi olduğundan `Connector` ve `Decorator`. `UseFullForm` İlişki adı, her bağlantı için özellik listesiyle birlikte Bağlayıcısı nesneden görünmesi ayarlandı. Ancak, `OmitElement` ayrıca ayarlayın böylece hiçbir `RoleElementName` içinde gömülü birden çok bağlantı kapsayan `Connector`:

```
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Şekilleri ve bağlayıcıları

Şekil ve bağlayıcı tanımları alan sınıfları, ek olarak aşağıdaki öznitelikler ve alt düğümleri devralır:

-   `Color` ve `Line``Style` öznitelikleri.

-   **ExposesFillColorAsProperty** ve birkaç benzer öznitelikleri. Bu Boolean öznitelikler kullanıcı tarafından karşılık gelen özellik değişkeni yapın. Genellikle, bir dil kullanıcı Diyagramı'nda bir şekil tıkladığında, özellikleri, görünür **özellikleri** penceresinde bu şekli eşlenmiş etki alanı sınıf örneği bulunur. Varsa `ExposesFillColorAsProperty` şekil özelliğini de görünür, true olarak ayarlanır.

-   **ShapeHasDecorators**. Bu öznitelik örneği her metin, simge veya dekoratör Genişlet/Daralt gerçekleşir. (DslDefinition.dsl dosyası içinde `ShapeHasDecorators` ile bir ilişki `UseFullForm` true olarak ayarlanmış.)

## <a name="shape-maps"></a>Şekil eşlemeleri

Belirtilen alan sınıfının örnekleri bir şekil tarafından temsil edilen ekranda görüntülenme şekil eşlemeleri belirler. Hem şekil ve bağlayıcı eşlemelerinin altında görünen `Diagram` DslDefinition.dsl dosyası bölümünü.

Aşağıdaki örnekte olduğu gibi `ShapeMap` öğeler varsa, en az bir alan sınıfının ad, bilinen adı, şekil, ve `ParentElementPath` öğesi:

```
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Sunucunun birincil işlevi `ParentElementPath` öğesi olduğundan nesnelerin aynı sınıf farklı bağlamlarda farklı bir şekil olarak görünebilir. Örneğin, bir `InPort` ayrıca bir yorum ile katıştırılmış `InPort` bu amaç için farklı bir şeklinde görünebilir.

İkincisi, kendi üst şeklin ilişkisini yolu belirler. Gömme hiçbir yapı şekilleri DslDefinition.dsl dosyası arasında tanımlanır. Şekil haritaları yapısından Infer gerekir. Üst şeklin üst öğe yolu tanımlayan etki alanı öğesine eşlenen şekildir. Bu durumda, yolu bileşenine tanımlar `InPort` ait. Başka bir şekil eşlemesinde bileşen sınıfı için ComponentShape eşlenir. Bu nedenle, yeni `InPort` şekil, bir alt yapıldığında, bileşenin şeklini `ComponentShape`.

InPort şekil diyagrama yerine bağlıysa, üst öğe yolu diyagrama eşlenen bileşen modeli için başka bir adım uygulamanız gerekir:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Şekil eşlemesi modelin kökü yok. Kök olan doğrudan diyagramdan, bunun yerine, başvurulan bir `Class` öğesi:

```
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Dekoratör eşlemeleri

Dekoratör eşlemesi, dekoratör şekli üzerinde eşlenen sınıfa özelliğinde ilişkilendirir. Özelliği bir listeden seçimli ya da Boole türü ise, değeri dekoratörün görünür olup olmayacağını belirleyebilirsiniz. Dekoratörün metin dekoratör ise, özelliğin değerini görünebilir ve kullanıcı düzenleyebilirsiniz.

### <a name="compartment-shape-maps"></a>Bölme şekli eşlemeleri

Bölme şekli eşlemeleri alt şekil haritaları türlerini ' dir.

## <a name="connector-maps"></a>Bağlayıcı eşlemeleri

En az bir bağlayıcı eşlemesi, bağlayıcı ve ilişki başvuruyor:

```
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Bağlayıcı eşlemesi, dekoratör eşlemeleri de içerebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)