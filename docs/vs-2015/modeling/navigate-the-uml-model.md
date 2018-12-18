---
title: UML modelinde gezinme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f77e72c55c0984f66a6884b0582716e5529abd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727767"
---
# <a name="navigate-the-uml-model"></a>UML modelinde gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu UML modelinin ana türlerini tanıtır.  
  
## <a name="the-model-elements-model-and-model-store"></a>Model öğelerini, Model ve Model Store  
 Derlemede tanımlanan türlerin **Microsoft.VisualStudio.UML.Interfaces.dll'yi** içinde tanımlanmış türlere karşılık gelen [UML Belirtimi sürüm 2.1.2'ye](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 UML belirtimindeki türler, Visual Studio'da arabirimleri olarak alırlar. Harf 'I' her tür adına eklenir. Örneğin: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 IElement dışında tüm türler özelliklerini bir veya daha fazla üst türden devralır.  
  
-   Model türlerinin özeti için bkz: [UML model öğe türleri](../modeling/uml-model-element-types.md).  
  
-   API tam ayrıntıları için bkz. [UML modelleme genişletilebilirliği için API Başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>İlişkiler  
 Özellikler ve UML belirtiminde tanımlanmış ilişkiler .NET özellikleri olarak uygulanır.  
  
 Çoğu ilişki her iki yönde de gezinilebilir. Bir ilişki her uçtaki türde bir özelliği olan özelliklerin bir çift karşılık gelir. Örneğin, özelliklerini `IElement.Owner` ve `IElement.OwnedElements` ilişkinin iki ucunu gösterir. Bu nedenle, bu ifade her zaman doğru olarak değerlendirilir:  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 IAssociation gibi birçok ilişki de kendi özelliklerine sahip olabilen bir nesne tarafından temsil edilir.  
  
 Modelden öğeyi silerseniz, parça aldığı herhangi bir ilişki otomatik olarak silinir ve diğer uçtaki özellik güncelleştirilir.  
  
 UML Belirtimi özelliğe 0..1 çeşitliliği atarsa, değer yakınlarında `null`. En fazla 1 .NET özelliğinin şu türünün olduğu anlamına gelir. büyük ile olan çeşitlilik: `IEnumerable<` *türü*`>`.  
  
 Geçiş yapan ilişkiler hakkında daha fazla bilgi için bkz. [UML API ile ilişkilerde gezinme](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Sahiplik ağacı  
 Bir model ağacını içerir <xref:Microsoft.VisualStudio.Uml.Classes.IElement> nesneleri. Her öğesinin özellikleri var `OwnedElements` ve `Owner`.  
  
 Çoğu durumda hedefleri `Owner` ve `OwnedElements` özellikleri daha özel isimleri olan diğer özellikler tarafından da başvurulur. Örneğin, her UML işlemi bir UML sınıfı tarafından sahiplenilir. Bu nedenle <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> adlı bir özelliği <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A>ve her <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> nesnesi `Class == Owner`.  
  
 Sahibi yok, ağacın en üst öğesi olan bir <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. IModel içinde yer alan bir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, içindeki <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Her model öğesi sahip ile birlikte oluşturulur. Daha fazla bilgi için [UML modellerinde öğe ve ilişki oluşturmak](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Sınıf diyagramı: Model, diyagram, Şekil ve öğe](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Şekilleri ve diyagramları  
 UML modelindeki öğeler diyagramlarda gösterilebilir. Farklı tür diyagramlar IElement'in farklı alt türlerini görüntüleyebilirsiniz.  
  
 Bazı durumlarda, bir öğe birden çok diyagramda görünebilir. Örneğin, IUseCase öğesinin bir diyagramda veya farklı diyagramlarda görünebilen birkaç IShapes'i.  
  
 Şekiller bir ağaçta düzenlenir. Ağacın kenarları ParentShape ve ChildShapes özellikleri tarafından gösterilir. Diyagramlar üst öğeleri olmayan tek şekildir. Diyagramın yüzeyindeki şekiller daha küçük parçalardan oluşur. Örneğin, sınıf şeklinin öznitelikler ve işlemler için bölmeleri vardır.  
  
 Şekiller hakkında daha fazla bilgi için bkz. [diyagramlar üzerinde bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Uzantılardaki modele erişim  
 İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantıları MEF Bileşenleri olarak tanımlanmış, uzantının çalıştığı bağlamdan bilgi içeri aktaran özellikleri bildirebilirsiniz.  
  
|Öznitelik türü|Bu erişim sağlar|Daha fazla bilgi|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> . IDiagramContext<br /><br /> (Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll dosyasında)|Geçerli odak diyagramı.|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (Microsoft.VisualStudio.Modeling.Sdk içinde. [sürüm] .dll)|Grup değişiklikleri işlemleri sağlar.|[İşlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell. SVsServiceProvider<br /><br /> (Microsoft.VisualStudio.Shell.Immutable içinde. [sürüm] .dll)|Konak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Buradan dosyalara, projelere ve diğer yönlere erişebilirsiniz.|[Visual Studio API kullanarak UML modeli açma](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Bağlamı almak için  
 Uzantı Sınıfınız içinde aşağıdaki arabirimlerinden birini veya bildirin:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Yönetilen Genişletilebilirlik Çerçevesi (MEF), bu, geçerli diyagrama, model deposu, kök nesnesi ve benzeri elde edebilirsiniz tanımları bağlayacaktır:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Geçerli seçimi almak için  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>Başka bir model ve diyagramlara erişme  
 Şunları yapabilirsiniz:  
  
-   Kullanım [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model farklı modellerdeki öğeler arasında bağlantılar oluşturmak için veri yolu. Daha fazla bilgi için [tümleştirme UML modellerini diğer modeller ve araçlarla birlikte](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Bir modelleme projesi ve diyagramları salt okunur modda görünür yapmadan yük [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanıcı arabirimi. Daha fazla bilgi için [program kodundaki UML modelini okuma](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Bir modelleme projesi ve onun diyagramlarını açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ve sonra içeriklere erişin. Daha fazla bilgi için [Visual Studio API kullanarak bir UML modeli açma](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



