---
title: DGML dosyalarını düzenleyerek kod haritalarını özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
ms.assetid: a2e141f4-4fd8-4611-b236-6b9e7bc54fc1
caps.latest.revision: 93
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e370e805df8e3a6ee253e3560738e882a247d2de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817465"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>DGML dosyalarını düzenleyerek kod haritalarını özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kod Haritası özelleştirmek için bir haritanın yönlendirilmiş grafik işaretleme dili (.dgml) dosyasını düzenleyebilirsiniz. Örneğin, öğeleri özel stilleri belirtmek, özellikleri ve kategorileri kod öğeleri ve bağlantılarına veya bağlantı belgeler veya URL'ler için kod öğeleri veya bağlantıları atamak için düzenleyebilirsiniz. DGML öğeleri hakkında daha fazla bilgi için bkz. [yönlendirilmiş grafik işaretleme dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md).  
  
 Kod Haritası'nın .dgml dosyasını bir metin veya XML Düzenleyicisi'ni düzenleyin. Harita, Visual Studio çözümünün parçası ise, seçin **Çözüm Gezgini**, kısayol menüsünü açın ve seçin **birlikte Aç**, **XML (metin) Düzenleyicisi**.  
  
> [!NOTE]
>  Kod haritaları oluşturmak için Visual Studio Enterprise'ı olması gerekir. Visual Studio'da bir kod Haritası düzenlediğinizde, tüm kullanılmayan DGML öğelerini ve özniteliklerini .dgml dosyasını kaydettiğinizde onları silerek temizler. El ile yeni bağlantılar eklediğiniz zaman ayrıca kod öğeleri otomatik olarak oluşturur. .dgml dosyasını kaydettiğinizde, bir öğeye eklediğiniz tüm öznitelikler kendilerini alfabetik sırada yeniden düzenleyebilir.  
  
##  <a name="OrganizeNodes"></a> Kod öğeleri grubu  
 Yeni gruplar ekleyebilir veya var olan düğümleri bir gruba Dönüştür.  
  
1. .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2. Bir kod öğesi bir gruba dönüştürmek için bulma `<Node/>` Bu kod öğesi için öğesi.  
  
    \- veya -  
  
    Yeni grubu eklemek için Bul `<Nodes>` bölümü. Yeni bir `<Node/>` öğesi.  
  
3. İçinde `<Node/>` öğe, Ekle bir `Group` grubun genişletilmiş veya daraltılmış olarak görünüp görünmediğini belirtmek için özniteliği. Örneğin:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyFirstGroup" Group="Expanded" />  
      <Node Id="MySecondGroup" Group="Collapsed" />  
   </Nodes>  
   ```  
  
4. İçinde `<Links>` bölümünde, emin bir `<Link/>` grubu kod öğesi ve onun alt kod öğeleri arasındaki her ilişki için aşağıdaki özniteliklere sahip öğe:  
  
   - A `Source` grubu kod öğesi belirten özniteliği  
  
   - A `Target` alt kod öğesi belirten özniteliği  
  
   - A `Category` belirten özniteliği bir `Contains` grubu kod öğesinden ve onun alt kod öğesi arasındaki ilişki  
  
     Örneğin:  
  
   ```xml  
   <Links>  
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />  
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />  
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />  
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />  
   </Links>  
   ```  
  
    Hakkında daha fazla bilgi için `Category` özniteliği için bkz: [kod öğeleri ve bağlantılara kategoriler atama](#AssignCategories).  
  
##  <a name="ChangeGraphStyle"></a> Harita stilini değiştirme  
 Haritanın .dgml dosyasını düzenleyerek haritanın kenarlık rengini ve arka plan rengini değiştirebilirsiniz. Kod öğeleri ve bağlantıların stilini değiştirmek için bkz [kod öğeleri ve bağlantıların stilini değiştirme](#Highlight).  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  İçinde `<DirectedGraph>` öğesinde, stilini değiştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:  
  
     Arka plan rengi  
  
    ```xml  
    Background="ColorNameOrHexadecimalValue"  
    ```  
  
     Kenarlık rengi  
  
    ```xml  
    Stroke="StrokeValue"  
    ```  
  
     Örneğin:  
  
    ```xml  
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >  
       ...  
       ...  
    </DirectedGraph>  
    ```  
  
##  <a name="Highlight"></a> Kod öğeleri ve bağlantıların stilini değiştirme  
  
###  <a name="CreateCustomStyles"></a>   
 Aşağıdaki kod öğeleri özel stilleri uygulayabilirsiniz:  
  
-   Tek bir kod öğeleri ve bağlantılarına  
  
-   Kod öğeleri ve bağlantı grupları  
  
-   Kod öğeleri ve belirli koşullara göre bağlantı grupları  
  
> [!TIP]
>  Stilleri birçok kod öğeleri veya bağlantı arasında tekrarlanan varsa, bu kod öğeleri veya bağlantılara bir kategoriyi uygulama ve ardından bu kategoriye bir stil uygulamadan düşünebilirsiniz. Daha fazla bilgi için [kod öğeleri ve bağlantılara kategori atama](#AssignCategories) ve [kod öğeleri ve bağlantılara özellikler atama](#AssignProperties).  
  
##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Bir tek bir kod öğesi için özel bir stil uygulamak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Kod öğesinin Bul `<Node/>` öğesi. Stilini özelleştirmek için bu özelliklerden herhangi birini ekleyin:  
  
     Arka plan rengi  
  
    ```xml  
    Background="ColorNameOrHexadecimalValue"  
    ```  
  
     Anahat  
  
    ```xml  
    Stroke="ColorNameOrHexadecimalValue"  
    ```  
  
     Anahat kalınlığı  
  
    ```xml  
    StrokeThickness="StrokeValue"  
    ```  
  
     Metin rengi  
  
    ```xml  
    Foreground="ColorNameOrHexadecimalValue"  
    ```  
  
     Simge  
  
    ```xml  
    Icon="IconFilePathLocation"  
    ```  
  
     Metin boyutu  
  
    ```xml  
    FontSize="FontSizeValue"  
    ```  
  
     Metin türü  
  
    ```xml  
    FontFamily="FontFamilyName"  
    ```  
  
     Metin ağırlığı  
  
    ```xml  
    FontWeight="FontWeightValue"  
    ```  
  
     Metin stili  
  
    ```xml  
    FontStyle="FontStyleName"  
    ```  
  
     Örneğin, belirtebilirsiniz `Italic` metin stili olarak.  
  
     Doku  
  
    ```xml  
    Style="Glass"  
    ```  
  
     - veya -  
  
    ```xml  
    Style="Plain"  
    ```  
  
     Şekil  
  
     Şekli bir simgeyle değiştirmek için Ayarla `Shape` özelliğini `None` ayarlayıp `Icon` özelliğini simge dosyasının yolu.  
  
    ```xml  
    Shape="ShapeFilePathLocation"  
    ```  
  
     Örneğin:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"  
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>  
    </Nodes>  
    ```  
  
##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Özel bir stili tek bir bağlantıya uygulamak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Bulma `<Link/>` adlarını kaynak kod öğesi ve hedef kod öğe içeren öğe.  
  
3.  İçinde `<Link/>` öğesinde, stilini özelleştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:  
  
     Anahat ve ok ucu rengi  
  
    ```xml  
    Stroke="ColorNameOrHexadecimalValue"  
    ```  
  
     Anahat kalınlığı  
  
    ```xml  
    StrokeThickness="StrokeValue"  
    ```  
  
     Anahat stili  
  
    ```xml  
    StrokeDashArray="StrokeArrayValues"  
    ```  
  
     Örneğin:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>  
    </Links>  
    ```  
  
##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Kod öğeleri veya bağlantılar grubuna özel stiller uygulamak için  
  
1. .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2. Varsa bir `<Styles></Styles>` öğe mevcut değilse, altında bir tane ekleyin `<DirectedGraph></DirectedGraph>` öğeden sonra `<Links></Links>` öğesi.  
  
3. İçinde `<Styles></Styles>` öğesi altında `<Style/>` öğesi ve aşağıdaki öznitelikleri belirtin:  
  
   - `TargetType="Node` &#124; `Link | Graph"`  
  
   - `GroupLabel="` *NameInLegendBox* `"`  
  
   - `ValueLabel="` *NameInStylePickerBox* `"`  
  
     Tüm hedef türlere özel bir stil uygulamak için bir koşul kullanmayın.  
  
##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Kod öğeleri veya bağlantı gruplarına koşullu bir stil uygulamak için  
  
1. .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2. İçinde `<Style/>` öğe, Ekle bir `<Condition/>` öğesini içeren bir `Expression` bir Boole değeri döndüren bir ifadeyi belirtmek için özniteliği.  
  
    Örneğin:  
  
   ```xml  
   <Condition Expression="MyCategory"/>  
   ```  
  
    - veya -  
  
   ```xml  
   <Condition Expression="MyCategory > 100"/>  
   ```  
  
    - veya -  
  
   ```xml  
   <Condition Expression="HasCategory('MyCategory')"/>  
   ```  
  
    Bu ifade aşağıdaki Backus-Naur Form (BNF) sözdizimini kullanır:  
  
    <Expression> ::= <BinaryExpression> &#124; <UnaryExpression> &#124; "("<Expression>")" &#124; <MemberBindings> &#124; <Literal> &#124; <Number>  
  
    <BinaryExpression> ::= <Expression> <Operator> <Expression>  
  
    <UnaryExpression> ::= "!" <Expression> &#124; "+" <Expression> &#124; "-" <Expression>  
  
    <Operator> :: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "veya" &#124; "ve" &#124; "+" &#124; "*" &#124; "/" &#124; "-"  
  
    <MemberBindings> ::= <MemberBindings> &#124; <MemberBinding> "." <MemberBinding>  
  
    <MemberBinding> ::= <MethodCall> &#124; <PropertyGet>  
  
    <MethodCall> ::= <Identifier> "(" <MethodArgs> ")"  
  
    <PropertyGet> :: Tanımlayıcısı =  
  
    <MethodArgs> ::= <Expression> &#124; <Expression> "," <MethodArgs> &#124; <empty>  
  
    <Identifier> ::= [^. ]*  
  
    <Literal> :: = tek veya çift tırnak içinde dize sabit değeri  
  
    <Number> :: = isteğe bağlı ondalık noktası ile rakamlar dizesi  
  
    Birden çok belirtebilirsiniz `<Condition/>` tüm stil uygulamak için true olması gereken öğeler.  
  
3. Sonra bir sonraki satırdaki `<Condition/>` öğesi, bir veya birden çok eklemeye `<Setter/>` öğeleri belirtmek için bir `Property` özniteliğini ve sabitlenmiş `Value` özniteliği veya bir hesaplanan `Expression` haritası, kod öğeleri veya uyan bağlantılara uygulamak için özniteliği Koşul.  
  
    Örneğin:  
  
   ```xml  
   <Setter Property="BackGround" Value="Green"/>  
   ```  
  
   Basit tam bir örnek, aşağıdaki iki koşul, bir kod öğesi yeşil görünür veya kırmızı bağlı belirtir. kendi `Passed` kategori ayarı `True` veya `False`:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
   <Nodes>  
      <Node Id="MyFirstNode" Passed="True" />  
      <Node Id="MySecondNode" Passed="False" />  
   </Nodes>  
   <Links>  
   </Links>  
   <Styles>  
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">  
         <Condition Expression="Passed='True'"/>  
         <Setter Property="Background" Value="Green"/>  
      </Style>  
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">  
         <Condition Expression="Passed='False'"/>  
         <Setter Property="Background" Value="Red"/>  
      </Style>  
   </Styles>  
</DirectedGraph>  
```  
  
 Aşağıdaki tabloda kullanabileceğiniz bazı örnek koşullar bulunmaktadır:  
  
 Bir kod öğesi boyutunu da değiştiren bir kod satırı sayısını işlevi olarak yazı tipi boyutunu ayarlayın. Bu örnek, birden çok özelliği ayarlamak için tek bir koşullu ifade kullanır. `FontSize` ve `FontFamily`.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Class1" LinesOfCode ="200" />  
   <Node Id="Class2" LinesOfCode ="1000" />  
   <Node Id="Class3" LinesOfCode ="20" />  
</Nodes>  
<Properties>  
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">  
      <Condition Expression="LinesOfCode > 0" />  
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />  
      <Setter Property="FontFamily" Value="Papyrus" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
 Temel bir kod öğesinin arka plan rengini ayarlamak `Coverage` özelliği. Stilleri, benzer göründükleri sırayla değerlendirilir `if-else` deyimleri.  
  
 Bu örnekte:  
  
1.  Varsa `Coverage` > 80 ise ayarlayın `Background` özelliğini yeşile.  
  
2.  Else if `Coverage` > 50 ise ayarlayın `Background` göre turuncu gölgeye özelliğini değerini temel alarak `Coverage` özelliği.  
  
3.  Ayarlayın `Background` özelliğini kırmızı gölgeye değerini temel alarak `Coverage` özelliği.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Class1" Coverage="58" />  
   <Node Id="Class2" Coverage="95" />  
   <Node Id="Class3" Coverage="32" />  
</Nodes>  
<Properties>  
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">  
      <Condition Expression="Coverage > 80" />  
      <Setter Property="Background" Value="Green" />  
   </Style>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">  
      <Condition Expression="Coverage > 50" />  
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />  
   </Style>  
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">  
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
 Ayarlama `Shape` özelliğini `None` simgenin şekille yer değiştirmesi. Kullanım `Icon` simgenin konumunu belirtmek için özellik.  
  
```xml  
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
<Nodes>  
   <Node Id="Automation" Category="Test" Label="Automation" />  
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />  
</Nodes>  
<Categories>  
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />  
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />  
</Categories>  
<Properties>  
   <Property Id="Icon" DataType="System.String" />  
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />  
   <Property Id="Shape" DataType="System.String" />  
</Properties>  
<Styles>  
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">  
      <Condition Expression="HasCategory('Group')" />  
      <Setter Property="Background" Value="#80008080" />  
   </Style>  
   <Style TargetType="Node">  
      <Setter Property="HorizontalAlignment" Value="Center" />  
   </Style>  
</Styles>  
</DirectedGraph>  
```  
  
##  <a name="AssignProperties"></a> Kod öğeleri ve bağlantılara özellikler atama  
 Kod öğeleri ve bağlantıları onlara özellikler atayarak düzenleyebilirsiniz. Örneğin, böylece gruplamak, stillerini değiştirebilmek veya gizleyebilmek belirli özellikleri olan kod öğeleri seçebilirsiniz.  
  
#### <a name="to-assign-a-property-to-a-code-element"></a>Bir kod öğesi için bir özellik atamak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Bulma `<Node/>` Bu kod öğesi için öğesi. Özelliğin adını ve değerini belirtin. Örneğin:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" MyPropertyName="PropertyValue" />  
    </Nodes>  
    ```  
  
3.  Ekleme bir `<Property/>` öğesine `<Properties>` bölümünde görünen adı ve veri türü gibi öznitelikleri belirtmek için:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
#### <a name="to-assign-a-property-to-a-link"></a>Bağlantıya bir özellik atamak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Bulma `<Link/>` adlarını kaynak kod öğesi ve hedef kod öğe içeren öğe.  
  
3.  İçinde `<Node/>` öğesinde, özelliğin adını ve değerini belirtin. Örneğin:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />  
    </Links>  
    ```  
  
4.  Ekleme bir `<Property/>` öğesine `<Properties>` bölümünde görünen adı ve veri türü gibi öznitelikleri belirtmek için:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
##  <a name="AssignCategories"></a> Kod öğeleri ve bağlantılara kategoriler atama  
 Aşağıdaki bölümlerde, onlara kategoriler atayarak kod öğeleri nasıl düzenleyebilirsiniz göstermek ve hiyerarşik oluşturabilirsiniz nasıl yardımcı olacak kategoriler kod öğelerini düzenlemek ve devralma kullanarak alt kategorilere öznitelikler ekleyin.  
  
#### <a name="to-assign-a-category-to-a-code-element"></a>Bir kod öğesi için bir kategori atamak için  
  
-   .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
-   Bulma `<Node/>` istediğiniz kod öğesi için öğesi.  
  
-   İçinde `<Node/>` öğe, Ekle bir `Category` kategorinin adını belirtmek için özniteliği. Örneğin:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Category="MyCategory" />  
    </Nodes>  
    ```  
  
     Ekleme bir `<Category/>` öğesine `<Categories>` kullanabileceğiniz bölümüne `Label` o kategorinin görüntü metnini belirtmek için özniteliği:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-assign-a-category-to-a-link"></a>Bir bağlantıya kategori atamak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Bulma `<Link/>` adlarını kaynak kod öğesi ve hedef kod öğe içeren öğe.  
  
3.  İçinde `<Link/>` öğe, Ekle bir `Category` kategorinin adını belirtmek için özniteliği. Örneğin:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"  
    </Links>  
    ```  
  
4.  Ekleme bir `<Category/>` öğesine `<Categories>` kullanabileceğiniz bölümüne `Label` o kategorinin görüntü metnini belirtmek için özniteliği:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-create-hierarchical-categories"></a>Hiyerarşik kategoriler oluşturmak için  
  
1.  .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2.  Ekleme bir `<Category/>` öğesi üst kategori için ve ardından eklemek `BasedOn` özniteliği alt kategorinin `<Category/>` öğesi.  
  
     Örneğin:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />  
       <Node Id="MySecondNode" Label="My Second Node" />  
    </Nodes>  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" />  
    </Links>  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>  
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>  
    </Categories>  
    ```  
  
     Bu örnekte, arka planını `MyFirstNode` yeşil olduğundan, `Category` inherits özniteliği `Background` özniteliği `MyParentCategory`.  
  
##  <a name="AddReferences"></a> Kod öğeleri ve bağlantılar belgeler veya URL'ler bağlama  
 Belgeler veya URL'ler için kod öğeleri veya bağlantılara haritanın .dgml dosyasını düzenleyerek ve ekleyerek bağlayabilirsiniz bir `Reference` özniteliğini `<Node/>` öğesi için bir kod öğesi veya `<Link/>` bağlantısını için öğesi. Ardından, açın ve kod öğesi veya bağlantı bu içeriği görüntüleme. `Reference` Özniteliği o içeriğin yolunu belirtir. Bu, .dgml dosya konumu veya mutlak yol ile göreli bir yol olabilir.  
  
> [!CAUTION]
>  Göreli yollar kullanıyorsanız ve .dgml dosyası farklı bir konuma taşınırsa, bu yollar artık çözümlenmez. Bağlantılı içeriği açmaya ve görüntülemeye çalıştığınızda, içeriğin görüntülenemediğini bildiren bir hata ortaya çıkar.  
  
 Örneğin, aşağıdaki kod öğeleri bağlamak isteyebilirsiniz:  
  
-   Sınıfta yapılan değişiklikleri açıklamak için bir iş kod öğesi, belge veya başka bir .dgml dosyasının URL'sini bir sınıf için kod öğesi bağlayabilirsiniz.  
  
-   Katman diyagramını yazılımın mantıksal mimarisinde bir katmanı gösteren bir grup kod öğesi bağlayabilirsiniz.  
  
-   Bir arabirimi kullanıma sunan bir bileşen hakkında daha fazla bilgi göstermek için bu arabirim için kod öğesi için Bileşen diyagramını bağlayabilirsiniz.  
  
-   Bir kod öğesi Team Foundation Server çalışma öğesine, hataya veya kod öğesine ilgili bazı diğer bilgilere bağlayın.  
  
#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Bir belgeye veya URL'ye kod öğesine bağlamak için  
  
1. .Dgml dosyasını bir metin veya XML düzenleyicisinde açın.  
  
2. Bulma `<Node/>` istediğiniz kod öğesi için öğesi.  
  
3. Aşağıdaki tabloda yer alan görevlerden birini gerçekleştirin:  
  
    Tek bir kod öğesinden  
  
   - İçinde `<Node/>` veya `<Link/>` öğe, Ekle bir `Reference` kod öğesinin konumunu belirtmek için özniteliği.  
  
     > [!NOTE]
     >  Tek sahip `Reference` öğe başına özniteliği.  
  
     Örneğin:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyNode" Reference="MyDocument.txt" />  
   </Nodes>  
   <Properties>  
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
   </Properties>  
   ```  
  
    Birden çok kod öğeleri  
  
   1. İçinde `<Node/>` veya `<Link/>` öğesi, her başvurunun konumunu belirtmek için yeni bir öznitelik ekleyin.  
  
   2. İçinde `<Properties>` bölümü:  
  
      1.  Ekleme bir `<Property/>` her yeni başvuru türü için öğesi.  
  
      2.  Ayarlama `Id` özniteliğini yeni başvuru özniteliğinin adına.  
  
      3.  Ekleme `IsReference` özniteliği ve değerini `True` başvuruyu kod öğenin üzerinde görünür yapmak için **Git başvurusu için** kısayol menüsü.  
  
      4.  Kullanım `Label` kod öğenin üzerinde görüntü metnini belirtmek için özniteliği **başvuru Git** kısayol menüsü.  
  
      Örneğin:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>  
   </Nodes>  
   <Properties>  
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />  
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />  
   </Properties>  
   ```  
  
    Harita üzerinde kod öğe adı altı çizili olarak görünür. Kod öğesi veya bağlantının kısayol menüsünü açtığınızda, göreceğiniz bir **başvuru Git** seçmeniz için bağlantılı kod öğeleri içeren bir kısayol menüsü.  
  
4. Kullanım `ReferenceTemplate` başvuruda o dizeyi yinelemek yerine birden çok başvuru tarafından kullanılan bir URL gibi ortak bir dizeyi belirtmek için özniteliği.  
  
    `ReferenceTemplate` Özniteliği başvuru değeri için bir yer tutucu belirtir. Aşağıdaki örnekte, `{0}` yer tutucu `ReferenceTemplate` öznitelik değerleriyle değiştirilecektir `MyFirstReference` ve `MySecondReference` öznitelikleri `<Node/>` tam yol üretmek için:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>  
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>  
   </Nodes>  
   <Properties>  
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>  
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>  
   </Properties>  
   ```  
  
5. Başvurulan kod öğesi veya eşlemesinden kod öğeleri görüntülemek için kod öğesi veya bağlantının kısayol menüsünü açın. Seçin **başvuru Git** ve ardından kod öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)   
 [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Kod Haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Gözat ve kod haritaları bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)   
 [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)