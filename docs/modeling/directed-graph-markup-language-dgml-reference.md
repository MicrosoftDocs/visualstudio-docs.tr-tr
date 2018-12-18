---
title: Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2eb13ad2b7b18b493e3de48d5b385c01e72857a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853850"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu

Yönlendirilmiş Grafik işaretleme dili (DGML) Görselleştirme ve karmaşıklık analizleri gerçekleştirmek için kullanılan bilgileri açıklar ve biçimi Visual Studio'daki kod haritaları kalıcı hale getirmek için kullanılır. Döngüsel ve döngüsel olmayan yönlendirilmiş grafikleri açıklamak için basit XML kullanır. Yönlendirilmiş bir grafik, bağlantılarla veya kenarlarla bağlanmış bir düğüm kümesidir. Düğümler ve bağlantılar, bir yazılım projesindeki öğeler gibi ağ yapılarını açıklamak için kullanılabilir.

Visual Studio'nun bazı sürümlerinin yalnızca bir alt kümesini DGML özellikleri desteği, bkz: Not [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bir .dgml dosyasını düzenlerken, IntelliSense her öğe için kullanılabilen öznitelikleri ve değerlerini belirlemenize yardımcı olur. Bir öznitelikte renk belirlemek için "Mavi" gibi genel renklerin adlarını veya "#ffa0b1c3" gibi ARGB onaltılık değerlerini kullanın. DGML Windows Presentation Foundation (WPF) renk tanımı biçimlerinin küçük bir alt kümesini kullanır. Daha fazla bilgi için [renkler sınıfı](http://go.microsoft.com/fwlink/?LinkId=182345).

##  <a name="DGML"></a> DGML söz dizimi

Aşağıdaki tabloda, DGML'de kullanılan öğelerin türleri açıklanmaktadır:

- `<DirectedGraph></DirectedGraph>`

   Kod Haritası (.dgml) belgesinin kök öğesi öğesidir. Diğer tüm DGML öğeleri, bu öğe kapsamı içinde görünür.

   Aşağıdaki liste dahil edebileceğiniz isteğe bağlı öznitelikleri tanımlar:

   `Background` -Harita arka plan rengi

   `BackgroundImage` -Harita arka planı olarak kullanılacak bir görüntü dosyasının konumu.

   `GraphDirection` -Map ayarlandığında ağaç düzenine (`Sugiyama`), düğümleri bağlantıların çoğu belirtilen yönde akmasını şekilde düzenleyin: `TopToBottom`, `BottomToTop`, `LeftToRight`, veya `RightToLeft`. Bkz: [eşleme düzenini](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` -Map şu düzenlere ayarlayın: `None`, `Sugiyama` (ağaç düzeni) `ForceDirected` (hızlı kümeler) veya `DependencyMatrix`. Bkz: [eşleme düzenini](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` -Map ağaç düzenine veya hızlı küme düzenine ayarlandığında, seçilen düğümlerden belirtilen sayıda (1-7) olan düğümleri gösterir. Bkz: [eşleme düzenini](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Bu isteğe bağlı öğe listesini içeren `<Node/>` haritada düğümleri tanımlayan öğeleri. Daha fazla bilgi için `<Node/>` öğesi.

  > [!NOTE]
  > İçinde tanımlanmamış bir düğüme başvurduğunuzda bir `<Link/>` harita öğesi, oluşturur bir `<Node/>` öğe otomatik olarak.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Bu öğe tek bir düğümü tanımlar. İçinde görünür `<Nodes><Nodes/>` öğe listesi.

   Bu öğenin öznitelikleri şunlardır:

   `Id` -Düğüm ve varsayılan değerini benzersiz bir ad `Label` ayrı özniteliği `Label` özniteliği belirtildi. Bu adı eşleşmelidir `Source` veya `Target` , kendisine başvuran bağlantının özniteliği.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Düğüm görünen adı.

   Stil öznitelikleri. Bkz: [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` -Bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için `<Category/>` öğesi.

   `Property` -Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` öğesi.

   `Group` -Düğümü diğer düğümleri içeriyorsa, bu öznitelik ayarlanan `Expanded` veya `Collapsed` içeriğini gizlemek veya göstermek için. Olmalıdır bir `<Link/>` içeren öğe `Category="Contains"` özniteliği ve üst düğümü kaynak düğüm ve alt düğümü hedef düğüm olarak belirtir. Bkz: [Grup kod öğeleri](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` -Bu öznitelik ayarlanan `Visible`, `Hidden`, veya `Collapsed`. Kullanan `System.Windows.Visibility`. Bkz: [Gizle veya Göster düğümlere ve bağlantılara](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` -Bu özniteliği bir belgeye veya URL'ye bağlanacak ayarlayın. Bkz: [bağlantı belgeler veya URL'ler için kod öğeleri ve bağlantılarına](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Bu öğe listesini içeren `<Link>` düğümler arasındaki bağlantıları belirleyen öğeleri. Daha fazla bilgi için `<Link/>` öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Bu öğe, bir kaynak düğümünü hedef düğüme bağlayan tek bir bağlantıyı tanımlar. İçinde görünür `<Links></Links>` öğe listesi.

  > [!NOTE]
  > Bu öğe tanımlanmamış bir düğüme başvuruyorsa, harita belge belirtilen öznitelikleri, varsa var olan bir düğümü otomatik olarak oluşturur.

   Bu öğenin öznitelikleri şunlardır:

   `Source` -Bağlantının kaynak düğümü

   `Target` -Bağlantının hedef düğümü

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Bağlantının görünen adı

   Stil öznitelikleri. Bkz: [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` -Bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için `<Category/>` öğesi.

   `Property` -Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Bu öğe listesini içeren `<Category/>` öğeleri. Daha fazla bilgi için `<Category/>` öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Bu öğe tanımlar bir `Category` bu özniteliği paylaşan öğeleri tanımlamak için kullanılan öznitelik. A `Category` özniteliği, harita öğelerini düzenlemek, devralma yoluyla paylaşılan öznitelikler sağlamak veya ek meta verileri tanımlamak için kullanılabilir.

   Bu öğenin öznitelikleri şunlardır:

   `Id` -Benzersiz bir ad, kategori ve varsayılan değerini `Label` ayrı özniteliği `Label` özniteliği belirtildi.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Kategori için okuyucuya kolaylık sağlayan ad bir.

   `BasedOn` -Üst kategori `<Category/>` geçerli öğenin devralır.

   Bu öğenin örneğinde `FailedTest` kategorisi kendi `Stroke` özniteliğini `PassedTest` kategorisi. "Hiyerarşik kategoriler oluşturmak için" bölümüne bakın [Özelleştir kod eşlemeleri DGML dosyalarını düzenleyerek](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategoriler, düğümlerin ve bağlantıların görünümünü bir haritada görüntülendiklerinde denetleyen birkaç temel şablon davranışı da sağlar. Bkz: [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Bu öğe listesini içeren `<Property/>` öğeleri. Daha fazla bilgi için `<Property/>` öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Bu öğe tanımlar bir `Property` herhangi bir DGML öğesine ya özniteliğine, kategoriler ve diğer özellikler dahil olmak üzere bir değer atamak için kullanabileceğiniz bir öznitelik.

   Bu öğenin öznitelikleri şunlardır:

  - `Id` -Özellik ve varsayılan değerini benzersiz bir ad `Label` ayrı özniteliği `Label` özniteliği belirtildi.

  - `DataType` -Özellik tarafından depolanan verinin türü

    Özellik görünmesini istiyorsanız **özellikleri** kullanın `Label` özelliği Özelliğin görünen adı belirtin.

    Bkz: [kod öğeleri ve bağlantılara kategoriler atama](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

###  <a name="AddAlias"></a> Sık kullanılan yolların diğer adları

Yaygın olarak kullanılan yolların takma adlarla değiştirilmesi .dgml dosyasının boyutunu azaltır ve dosyayı yüklemek veya kaydetmek için gereken süreyi kısaltır. Bir diğer ad oluşturmak için bir `<Paths></Paths>` .dgml dosyasının sonundaki bölümü. Bu bölümde, ekleme bir `<Path/>` yolu için bir diğer ad tanımlamak için:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

.Dgml dosyasındaki bir öğeden diğer ada başvuru yapmak içine `Id` , \<Path / > öğesi bir dolar işareti ($) ve parantez (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)