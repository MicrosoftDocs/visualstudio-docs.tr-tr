---
title: Program Kodunda Modeli Gezinme ve Güncelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 930d7ededf4a54aaf75516c59001eaccf38c210c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896776"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Program Kodunda Modelde Gezinme ve Modeli Güncelleştirme

Model öğelerini silin, bunların özelliklerini ayarlamak ve oluşturmasına ve öğeler arasında bağlantılar silmek için kod yazabilirsiniz. Bir işlem içinde tüm değişiklik yapılması gerekir. Diyagram üzerindeki öğeleri görüntülerse, diyagram "otomatik olarak işlem sonunda düzeltilecektir".

##  <a name="example"></a> Bir örneği DSL tanımı
 Bu DslDefinition.dsl ana bölümü için bu konudaki örnekleri.

 ![DSL tanım diyagramı &#45; ailesi ağaç modeli](../modeling/media/familyt_person.png)

 Bu model, bu DSL örneğidir:

 ![Tudor ailesi ağaç modeli](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Başvurular ve ad alanları
 Bu konudaki kodu çalıştırmak için başvuru:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kodunuzu bu ad alanı kullanır:

 `using Microsoft.VisualStudio.Modeling;`

 DSL'nizi tanımlandığı olandan farklı bir projede kod yazıyorsanız, Dsl proje tarafından oluşturulan derleme içeri aktarmalısınız.

##  <a name="navigation"></a> Model gezinme

### <a name="properties"></a>Özellikler
 DSL tanımındaki tanımlayan bir etki alanı özellikleri, program kodu içinde erişebildiği özellikleri olur:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Bir özelliği ayarlamak istiyorsanız, bunu içine yapmalısınız bir [işlem](#transaction):

 `henry.Name = "Henry VIII";`

 DSL tanımının, bir özelliğe sahipse **tür** olduğu **hesaplanan**, bunu göremezsiniz. Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>İlişkiler
 DSL tanımındaki tanımladığınız etki alanı ilişkilerinin özellikleri, bir ilişkinin her iki ucunda sınıfı çiftlerini haline gelir. Özellik adlarının DslDefinition diyagramda her tarafındaki ilişkinin rolleri hakkında daha fazla etiket olarak görüntülenir. Rol'ün çoğulluğunun bağlı olarak, ilişkinin diğer ucundaki sınıfı veya söz konusu sınıfın bir koleksiyon özelliği türüdür.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Bir ilişkinin diğer ucundaki her zaman özelliklerdir tersini. Bir bağlantı oluşturulduğu veya silindiği iki öğeyi rol özellikleri güncelleştirilir. Aşağıdaki ifade (uzantıları kullanan `System.Linq`) örnekte ParentsHaveChildren ilişki her zaman doğrudur:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Bir ilişki de adlı bir model öğesi tarafından temsil edilen bir *bağlantı*, etki alanı ilişki türünün bir örneği olduğu. Bir bağlantı, bir kaynak öğesi ve bir hedef öğe her zaman vardır. Kaynak öğesi ve hedef öğe aynı olabilir.

 Bir bağlantı ve özelliklerine erişebilirsiniz:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Varsayılan olarak, herhangi bir model öğe çiftinin bağlamak için birden fazla örneğini bir ilişki izin verilir. DSL tanımı varsa, ancak `Allow Duplicates` ilişki için bayrağı doğruysa sonra birden fazla bağlantı olabilir ve kullanmalısınız `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Bağlantılar erişmek için başka yöntemler de vardır. Örneğin:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Gizli roller.** DSL tanımı varsa, **özelliği oluşturulan** olduğu **false** belirli bir rol için ardından hiçbir özelliği bu role karşılık gelen oluşturulur. Ancak, yine de bağlantıları erişebilir ve ilişki yöntemleri kullanılarak bağlantılar:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 En sık kullanılan örnek <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> diyagram üzerinde görüntüleyen şekli bir model öğesine bağlandığı ilişkisi:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Öğe dizini
 Öğe dizini kullanarak mağaza tüm öğeleri erişebilirsiniz:

 `store.ElementDirectory.AllElements`

 Aşağıdaki gibi öğeleri bulmak için yöntemleri vardır:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Sınıf bilgilerine erişme
 Sınıfları ve ilişkileri DSL tanımını diğer yönleri hakkında bilgi edinebilirsiniz. Örneğin:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Model öğelerinin üst sınıfları aşağıdaki gibidir:

-   ModelElement - tüm öğeleri ve ilişkileri olan ModelElements

-   ElementLink - tüm ilişkiler ElementLinks olan.

##  <a name="transaction"></a> Bir işlem içinde değişiklikleri gerçekleştirin
 Program kodunuza Store içinde herhangi bir şey değiştiğinde, bunu bir işlem içinde yapmalısınız. Bu, tüm model öğelerini, ilişkiler, şekiller, diyagramları ve özellikleri için geçerlidir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Bir işlem yönetmenin en kolay yöntemi olan bir `using` ifadesi içine bir `try...catch` deyimi:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Herhangi bir sayıda bir işlem içinde değişiklik yapabilirsiniz. Yeni işlemlerinin etkin bir işlem içinde açabilirsiniz.

 Yaptığınız değişiklikleri kalıcı hale getirmek için gereken `Commit` bırakılana önce işlem. İşlem içinde yakalanmamış özel bir durum oluşursa, Store değişiklikleri önce durumuna sıfırlar.

##  <a name="elements"></a> Model öğeleri oluşturma
 Bu örnekte, mevcut bir model için bir öğe ekler:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Bu örnekte, bir öğe oluşturma hakkında daha fazla şu önemli noktaları gösterilmektedir:

- Store belirli bir bölüme yeni öğe oluşturun. Model öğeleri ve ilişkileri ancak olmayan şekiller için bu genellikle varsayılan bölümdür.

- Gömme ilişkisi hedef kolaylaştırır. Bu örnekte DslDefinition içinde her kişi gömme ilişkisi FamilyTreeHasPeople hedef olmalıdır. Bunu başarmak için biz kişi nesnesinin FamilyTreeModel rolü özelliği ayarlamak veya FamilyTreeModel nesnesinin kişiler rol özelliğine kişiyi ekler.

- Özellikle özelliği olan yeni bir öğe özelliklerini ayarlayın `IsName` DslDefinition geçerlidir. Bu bayrak, öğe sahibi içinde benzersiz şekilde tanımlamak için hizmet veren özelliği işaretler. Bu durumda, Name özelliği bu bayrağı vardır.

- Bu DSL DSL tanımını Store yüklenmiş olmalıdır. Bir menü komutu gibi bir uzantı yazıyorsanız, bu genellikle önceden true olması gerekir. Diğer durumlarda, bunu açıkça modeli Store yüklemek, veya kullanabilirsiniz <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> yüklemek için. Daha fazla bilgi için [nasıl yapılır: Program kodunda dosyadan Model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Bu şekilde bir öğe oluşturduğunuzda, bir şekil (DSL diyagram varsa) otomatik olarak oluşturulur. Varsayılan şekli, rengi ve diğer özellikleri otomatik olarak atanmış bir konumda görüntülenir. Nerede ve nasıl ilişkili şekli görünür denetlemek istiyorsanız bkz [bir öğe ve şeklini oluşturma](#merge).

##  <a name="links"></a> İlişki bağlantılar oluşturma
 DSL tanımını örnekte tanımlanan iki ilişkisi vardır. Her ilişkiyi tanımlayan bir *rolü özelliği* sınıfındaki ilişkinin her iki ucunda.

 Bir ilişkinin örneğini oluşturabileceğiniz üç yolu vardır. Bu üç yöntemlerin her biri aynı etkiye sahiptir:

- Kaynak rol oyuncusu özelliğini ayarlayın. Örneğin:

  -   `familyTree.People.Add(edward);`

  -   `edward.Parents.Add(henry);`

- Hedef rol oyuncusu özelliğini ayarlayın. Örneğin:

  -   `edward.familyTreeModel = familyTree;`

       Bu rolün çokluğu olan `1..1`, biz değerini atayın.

  -   `henry.Children.Add(edward);`

       Bu rolün çokluğu olan `0..*`, koleksiyona ekleriz.

- Bir ilişkinin örneğini açıkça oluşturur. Örneğin:

  -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Son yöntem, ilişki özellikleri ayarlamak istiyorsanız kullanışlıdır.

  Bu şekilde bir öğe oluşturduğunuzda, diyagram bağlayıcıda otomatik olarak oluşturulur, ancak bir varsayılan şekli, rengi ve diğer özellikleri vardır. İlişkili bağlayıcısının nasıl oluşturulacağını denetlemek için bkz: [bir öğe ve şeklini oluşturma](#merge).

##  <a name="deleteelements"></a> Öğeleri silme
 Çağırarak öğeyi Sil `Delete()`:

 `henry.Delete();`

 Bu işlem ayrıca silecek:

- Bağlantılar öğesinden ilişki. Örneğin, `edward.Parents` artık içerecek `henry`.

- Rollerin öğeler `PropagatesDelete` bayrağı doğrudur. Örneğin, öğeyi görüntüleyen şekli silinir.

  Varsayılan olarak, her bir gömme ilişkisi vardır `PropagatesDelete` hedef rolü true. Silme `henry` silmediği `familyTree`, ancak `familyTree.Delete()` tüm siler `Persons`. Daha fazla bilgi için [silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md).

  Varsayılan olarak, `PropagatesDelete` başvuru ilişkileri rolleri için geçerli değildir.

  Bir nesne sildiğinizde belirli yayılmaları atlamak silme kuralları neden olabilir. Bu işlem için başka bir öğe değiştirerek, kullanışlıdır. Siz kendisi için silme yayılmayacak bir veya daha fazla rol GUID'sini sağlayın. GUID ilişki sınıfı alınabilir:

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (Söz konusu örnekte hiçbir etkisi yoktur, çünkü `PropagatesDelete` olduğu `false` rolleri için `ParentsHaveChildren` ilişki.)

  Bazı durumlarda, silme, öğe veya yayma tarafından silinmiş bir öğe üzerinde bir kilit varlığı tarafından engellenir. Kullanabileceğiniz `element.CanDelete()` öğe silinmiş olup olmadığını denetlemek için.

##  <a name="deletelinks"></a> İlişki bağlantıları siliniyor
 Bir öğenin bir rol özelliği kaldırarak bir ilişki bağlantı silebilirsiniz:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Bağlantı açıkça silebilirsiniz:

 `edwardHenryLink.Delete();`

 Tüm bu üç yöntem aynı etkiye sahiptir. Yalnızca bunlardan birini kullanmanız gerekir.

 0..1 veya 1.. 1 Çokluk rolü varsa, bunu ayarlayabilirsiniz `null`, veya başka bir değerle:

 `edward.FamilyTreeModel = null;` veya:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Bir ilişkinin bağlantıları yeniden sıralama
 Belirli bir sırada kaynaklanan ya da belirli bir model öğesi hedeflenen belirli bir ilişkinin bağlantıları vardır. İçinde eklendikleri sırayla görünürler. Örneğin, bu ifade her zaman aynı sırada alt verir:

 `foreach (Person child in henry.Children) ...`

 Bağlantı sırasını değiştirebilirsiniz:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Kilitler
 Değişikliklerinizi bir kilit tarafından engellenebilir. Kilitleri, tek tek öğelerine, bölümler ve deponun ayarlanabilir. Bu düzeylerden herhangi birinde yapmak istediğiniz değişiklik türünü engelleyen bir kilit varsa, bunu çalıştığınızda bir özel durum. Kilit öğesi kullanarak ayarlanıp ayarlanmadığını bulabilir. Ad alanında tanımlanan genişletme yöntemi olan GetLocks() <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Daha fazla bilgi için [için salt okunur kesimler oluşturmak kilitleme ilkesi tanımlama](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Kopyala ve Yapıştır
 Öğeleri ya da grupları öğelerine kopyalayabilirsiniz bir <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Öğeleri sıralanmış bir öğe grubu depolanır.

 Bir modele bir bilgisine birleştirebilirsiniz:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` kabul ya da bir `PresentationElement` veya `ModelElement`. Bu bildirimde bulunursanız bir `PresentationElement`, üçüncü parametre olarak hedef diyagram üzerinde bir konum belirtebilirsiniz.

##  <a name="diagrams"></a> Gezinme ve güncelleştirme diyagramları
 Bir DSL içinde kişi veya şarkı gibi bir kavram temsil eder, etki alanı model öğesi diyagramda gördüğünüz temsil eder şekil öğesinden ayrıdır. Etki alanı model öğesi önemli özellikler ve ilişkiler kavramları depolar. Şekil öğesi boyutunu, konumunu ve diyagram görünümünde nesnenin rengini ve düzenini bileşen parçalarından depolar.

### <a name="presentation-elements"></a>Sunum öğelerini
 ![Temel şekil ve öğesi türlerinin sınıf diyagramı](../modeling/media/dslshapesandelements.png)

 DSL Tanımınızda, belirttiğiniz her bir öğe aşağıdaki standart sınıflarının birinden türetilmiş bir sınıf oluşturur.

|Öğe türü|Temel sınıf|
|-|-|
|Etki alanı sınıfı|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Etki alanı ilişkisi|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Şekil|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Bağlayıcı|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diyagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Bir öğeyi bir diyagram üzerinde genellikle bir model öğesini temsil eder. Genellikle (ama her zaman kullanılmaz), bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> bir etki alanı sınıfı örneğini temsil eder ve bir <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> bir etki alanı ilişkisi örneğini temsil eder. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> İlişki bir düğüm veya bağlantı şekli temsil ettiği model öğesine bağlar.

 Her düğüm veya bağlantı şekli bir diyagrama aittir. İkili bağlantı şekli iki düğüm şekillere bağlanır.

 Şekiller iki kümelerinde alt şekillere sahip olabilir. Bir şekle `NestedChildShapes` kümesi, üst öğesinin sınırlayıcı kutu için sınırlı. Bir şekle `RelativeChildShapes` listesi dışında ya da kısmen - Örneğin, bir etiket ya da bir bağlantı noktası üst sınırları dışında görünebilir. Bir diyagram sahip olmayan `RelativeChildShapes` ve hiçbir `Parent`.

###  <a name="views"></a> Şekiller ve öğeleri arasında gezinme
 Etki alanı model öğelerini ve Şekil öğelerine tarafından ilişkilidir <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> ilişki.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Aynı ilişki diyagramda bağlayıcılar ilişkileri bağlar:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Bu ilişki, ayrıca modelin kökü diyagrama bağlar:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Bir şekil tarafından temsil edilen model öğesine almak için kullanın:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Geçici bir çözüm diyagramı gezinme
 Genel şekilleri ve bağlayıcıları diyagramda arasında gezinmek için önerilir değil. Modelde, yalnızca Diyagram görünümünü üzerinde çalışması gerekli olduğunda şekiller ve bağlayıcılar arasında taşıma ilişkilerde gezinme daha iyidir. Bu yöntemlerin her iki ucunda şekilleri bağlayıcıları bağlantı:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Birçok şekiller bileşik niteliktedir; Bunlar bir ana şeklin ve bir veya daha fazla alt katmanları oluşur. Başka bir şekil göreli konumlu şekiller söylediğiniz olmasını kendi *alt*. Üst şeklin taşındığında alt öğeleri ile taşıyın.

 *Göreli alt* üst şeklin sınırlayıcı kutusunun dışında görünebilir. *İç içe geçmiş* alt ve üst sınırları içinde kesin olarak görünür.

 Şekilleri diyagram üzerinde üst kümesi elde etmek için kullanın:

 `Diagram.NestedChildShapes`

 Şekilleri ve bağlayıcıları üst sınıfları şunlardır:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Şekillerin ve bağlayıcıların özellikleri
 Çoğu durumda, şekillere açık değişiklik yapmak gerekli değildir. Model öğeleri değiştirildiğinde "Düzelt" kuralları şekilleri ve bağlayıcıları güncelleştirme. Daha fazla bilgi için [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).

 Ancak, model öğelerini bağımsız olan özellikleri şekillerde açık bazı değişiklikler yapmak kullanışlıdır. Örneğin, bu özellikleri değiştirebilir:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Şekil genişliğini ve yüksekliğini belirler.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -üst şekil veya diyagram göreli konumu

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -kalemler ve Şekil veya bağlayıcının çizmek için kullanılan Fırçalar

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -Şekil tarafından görülmez

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -Şekil sonra görünür hale getirir bir `Hide()`

###  <a name="merge"></a> Bir öğe ve alt şekil oluşturma

Bir öğe oluşturma ve ilişkileri ekleme ağacına bağlamak, bir şekil otomatik olarak oluşturulur ve onunla ilişkili. Bu işlem sonunda yürütülen "düzeltme" kuralları tarafından gerçekleştirilir. Ancak, otomatik olarak atanmış bir konumda şekli görünür ve şeklini, rengini ve diğer özellikler varsayılan değerlere sahip olur. Şekil nasıl oluşturulacağını denetlemek için birleştirme işlevi kullanabilirsiniz. Önce ElementGroup eklemek istediğiniz öğeleri ekleyin ve ardından grubun diyagrama birleştirmeniz gerekir.

Bu yöntem:

-   Bir özellik öğe adı olarak atadıysanız adını ayarlar.

-   Hiçbir öğe birleştirme DSL tanımında belirtilen yönergeleri görür.

Bu örnek, kullanıcı diyagramda sağ tıkladığında fare konumuna bir şekil oluşturur. Bu örnek, DSL tanımındaki `FillColor` özelliği `ExampleShape` ifşa.

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 Birden fazla şekil sağlarsanız, göreli konumlarını kullanarak ayarlayın `AbsoluteBounds`.

 Renk ve bu yöntemi kullanarak bağlayıcıların kullanıma sunulan diğer özellikleri de ayarlayabilirsiniz.

### <a name="use-transactions"></a>İşlemleri kullanma
 Şekiller ve bağlayıcılar diyagramları olan alt türlerini <xref:Microsoft.VisualStudio.Modeling.ModelElement> ve Store Canlı. Bu nedenle değişiklikleri için yalnızca bir işlem içinde yapmanız gerekir. Daha fazla bilgi için [nasıl yapılır: modeli güncelleştirmek için kullanım işlemleri](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Belge görünüm ve belge verilerini
 ![Standart diyagram türleri sınıf diyagramı](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Store bölümleri
 Bir model yüklendiğinde eşlik eden diyagram aynı anda yüklenir. Genellikle, model Store.DefaultPartition yüklenir ve diyagram içeriği başka bir bölüme yüklenir. Genellikle, her bölüm içeriği yüklendi ve ayrı bir dosyaya kaydedilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)
- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
