---
title: Kopyalama davranışını özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87fff01c-60ba-440a-b8a0-185edcef83ac
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c2478925ecf481aaf49dbfbe5818d8839b9ad54f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844100"
---
# <a name="customizing-copy-behavior"></a>Kopyalama Davranışını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İle oluşturulmuş bir etki alanına özgü dil (DSL) içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'sı, kullanıcıya kopyalar ve öğeleri yapıştırır ne olur değiştirebilirsiniz.  
  
## <a name="standard-copy-and-paste-behavior"></a>Standart Kopyala ve yapıştır davranışı  
 Kopyalama etkinleştirmek için ayarlayın **etkinleştirme Kopyala Yapıştır** özelliği **Düzenleyicisi** DSL Gezgininde.  
  
 Kullanıcı öğelerini Pano'ya kopyalar, varsayılan olarak, aşağıdaki öğeleri de kopyalanır:  
  
- Seçilen öğeleri ekli alt öğeleri. (Diğer bir deyişle, adresindeki kaynaklanan ilişkileri ekleme hedefleri olan öğeler öğeleri kopyaladınız.)  
  
- Kopyalanan öğeler arasındaki ilişki bağlantılar.  
  
  Bu kural, bağlantılar ve kopyalanan öğeler özyinelemeli olarak uygulanır.  
  
  ![Kopyalanır ve öğeleri yapıştırdığınız](../modeling/media/dslcopypastedefault.png "DslCopyPasteDefault")  
  
  Kopyalanan öğeleri ve bağlantılarına serileştirilmiş ve depolanan bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) panoya yerleştirilir.  
  
  Kopyalanan öğeler görüntüsü de panoya yerleştirilir. Bu kullanıcının Word gibi başka uygulamalara yapıştırmayı sağlar.  
  
  Kullanıcı, DSL tanımını göre öğeleri kabul edebilen bir hedef kopyalanan öğeleri yapıştırabilirsiniz. Örneğin, bileşenleri çözüm şablonundan oluşturulan bir DSL içinde kullanıcı bağlantı noktaları bileşenleri üzerine ancak değil diyagram üzerine yapıştırabilirsiniz; ve bileşenlerinin diyagram üzerine, ancak diğer bileşenlere değil üzerine yapıştırabilirsiniz.  
  
## <a name="customizing-copy-and-paste-behavior"></a>Kopyalama ve yapıştırma davranışını özelleştirme  
 Program kodu kullanarak model özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 **Etkinleştirmek veya Kopyala, Kes ve Yapıştır devre dışı bırakın.**  
 DSL Gezgini içinde ayarlamak **etkinleştirme Kopyala Yapıştır** özelliği **Düzenleyicisi** düğümü.  
  
 **Bağlantılar aynı hedefe kopyalar.** Örneğin, kopyalanan açıklama kutusunun aynı konu öğesine bağlı.  
 Ayarlama **yayar kopyalama** rolüne özelliği **yalnızca bağlamak için kopyalama yaymak**. Daha fazla bilgi için [bağlantı kopyalama davranışını özelleştirme](#customizeLinks).  
  
 Bağlantılı öğeler kopyalayın. Örneğin, yeni bir öğe kopyalarken, bağlı bir açıklama kutuların kopyalarını da yapılır.  
 Ayarlama **yayar kopyalama** rolüne özelliği **kopyalama bağlamak ve karşı rol oyuncusu yaymak**. Daha fazla bilgi için [bağlantı kopyalama davranışını özelleştirme](#customizeLinks).  
  
 **Kopyalayıp yapıştırarak hızlı bir şekilde yinelenen öğeleri.** Normalde, az önce kopyaladığınız öğesi seçili durumdayken ve aynı türdeki öğe üzerine yapıştırılamıyor.  
 Etki alanı sınıfı için bir öğe birleştirme yönergesinde ekleyin ve üst sınıfı için ileriye doğru birleştirmeleri ayarlayın. Bu aynı sürükleme işlemleri üzerinde etkisi olmaz. Daha fazla bilgi için [özelleştirme öğe oluşturma ve hareketini](../modeling/customizing-element-creation-and-movement.md).  
  
 \- veya -  
  
 Geçersiz kılarak öğeleri yapıştırmadan önce diyagramı `ClipboardCommandSet.ProcessOnPasteCommand()`. Özel bir DslPackage proje dosyasında bu kodu ekleyin:  
  
```csharp  
namespace Company.MyDsl {  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;   
using Microsoft.VisualStudio.Modeling.Shell;  
partial class MyDslClipboardCommandSet  
{  
  protected override void ProcessOnMenuPasteCommand()  
  {  
 // Deselect the current selection after copying:  
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;  
    this.CurrentModelingDocView  
     .SelectObjects(1, new object[] { diagram }, 0);  
  }  
} }  
  
```  
  
 **Kullanıcının seçili bir hedefe yapıştırır ek bağlantılar oluşturun.** Örneğin, bir açıklama kutusuna bir öğenin üstüne yapıştırıldığında, bağlantı aralarında yapılır.  
 Hedef etki alanı sınıfı için bir öğe birleştirme yönergesi ekleyin ve bağlantılar ekleyerek birleştirme işlemeye ayarlayın. Bu aynı sürükleme işlemleri üzerinde etkisi olmaz. Daha fazla bilgi için [özelleştirme öğe oluşturma ve hareketini](../modeling/customizing-element-creation-and-movement.md).  
  
 \- veya -  
  
 Geçersiz kılma `ClipboardCommandSet.ProcessOnPasteCommand()` taban yöntemi çağrıldıktan sonra ek bağlantılar oluşturmak için.  
  
 **Hangi öğeleri kopyalanabilir biçimlerini özelleştirmek** bit eşlem forma bir kenarlık eklemek için dış uygulamalara – örneğin.  
 Geçersiz kılma *MyDsl* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` DslPackage projedeki.  
  
 **Nasıl öğeleri Panoya Kopyala komutu, ancak bir sürükleme işleminde kopyalanır özelleştirin.**  
 Geçersiz kılma *MyDsl* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` DslPackage projedeki.  
  
 **Şekil düzenini kopyalama aracılığıyla korumak ve yapıştırın.**  
 Kullanıcı birden çok şekil kopyaladığında, bunlar yapıştırıldığında göreli konumlarını koruyabilirsiniz. Bu teknik örneğe tarafından gösterilen [VMSDK: bağlantı hattı diyagramları örnek](http://go.microsoft.com/fwlink/?LinkId=213879).  
  
 Bu etkiyi elde etmek için şekilleri ve bağlayıcıları için kopyalanan ElementGroupPrototype ekleyin. ElementOperations.CreateElementGroupPrototype() geçersiz kılmak için en uygun yöntemdir. Bunu yapmak için Dsl projesine aşağıdaki kodu ekleyin:  
  
```csharp  
  
public class MyElementOperations : DesignSurfaceElementOperations  
{  
  // Create an EGP to add to the clipboard.  
  // Called when the elements to be copied have been  
  // collected into an ElementGroup.  
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)  
  {  
 // Add the shapes and connectors:  
 // Get the elements already in the group:  
    ModelElement[] mels = elementGroup.ModelElements  
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.  
        .ToArray();  
 // Get their shapes:  
    IEnumerable<PresentationElement> shapes =   
       mels.SelectMany(mel =>   
            PresentationViewsSubject.GetPresentation(mel));  
    elementGroup.AddRange(shapes);  
  
 return base.CreateElementGroupPrototype  
           (elementGroup, elements, closureType);  
  }  
  
 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)  
      : base(serviceProvider, diagram)  
  { }  
}  
  
// Replace the standard ElementOperations  
// singleton with your own:  
partial class MyDslDiagram // EDIT NAME  
{  
 /// <summary>  
 /// Singleton ElementOperations attached to this diagram.  
 /// </summary>  
 public override DesignSurfaceElementOperations ElementOperations  
  {  
 get  
    {  
 if (singleton == null)  
      {  
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);  
      }  
 return singleton;  
    }  
  }  
 private MyElementOperations singleton = null;  
}  
  
```  
  
 **Şekiller geçerli imleç konumu gibi seçtiğiniz bir konuma yapıştırın.**  
 Kullanıcı birden çok şekil kopyaladığında, bunlar yapıştırıldığında göreli konumlarını koruyabilirsiniz. Bu teknik örneğe tarafından gösterilen [VMSDK: bağlantı hattı diyagramları örnek](http://go.microsoft.com/fwlink/?LinkId=213879).  
  
 Bu etkiyi elde etmek için geçersiz kılma `ClipboardCommandSet.ProcessOnMenuPasteCommand()` konuma özgü sürümünü kullanacak şekilde `ElementOperations.Merge()`. Bunu yapmak için DslPackage projesinde aşağıdaki kodu ekleyin:  
  
```csharp  
  
partial class MyDslClipboardCommandSet // EDIT NAME  
{  
   /// <summary>  
    /// This method assumes we only want to paste things onto the diagram  
    /// - not onto anything contained in the diagram.  
    /// The base method pastes in a free space on the diagram.  
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.  
    /// </summary>  
    protected override void ProcessOnMenuPasteCommand()  
    {  
  
  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;  
  
      // Retrieve data from clipboard:  
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();  
  
      Diagram diagram = docView.CurrentDiagram;  
      if (diagram == null) return;  
  
      if (!docView.IsContextMenuShowing)  
      {  
        // User hit CTRL+V - just use base method.  
  
        // Deselect anything that's selected, otherwise  
        // pasted item will be incompatible:  
        if (!this.IsDiagramSelected())  
        {  
          docView.SelectObjects(1, new object[] { diagram }, 0);  
        }  
  
        // Paste into a convenient spare space on diagram:  
    base.ProcessOnMenuPasteCommand();  
      }  
      else  
      {  
        // User right-clicked - paste at mouse position.  
  
        // Utility class:  
        DesignSurfaceElementOperations op = diagram.ElementOperations;  
  
        ShapeElement pasteTarget = diagram;  
  
        // Check whether what's in the paste buffer is acceptable on the target.  
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))  
        {  
  
        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first  
          // so that we don't create an empty transaction (after which Undo would be no-op).  
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))  
          {  
            PointD place = docView.ContextMenuMousePosition;  
            op.Merge(pasteTarget, data, PointD.ToPointF(place));  
            t.Commit();  
          }  
        }  
      }  
    }  
  }  
```  
  
 **Öğeleri sürükleyip kullanıcı sağlar.**  
 Bkz: [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
##  <a name="customizeLinks"></a> Bağlantı kopyalama davranışını özelleştirme  
 Kullanıcının bir öğe kopyalarken standart katıştırılmış öğeleri de kopyalanır davranışıdır. Standart kopyalama davranışı değiştirebilirsiniz. DSL tanımındaki bir ilişkinin ve Özellikler penceresinde kümedeki bir tarafındaki bir rol seçin **yayar kopyalama** değeri.  
  
 ![Etki alanı rolünün kopyalama özelliği yayar](../modeling/media/dslpropagatescopy.png "DslPropagatesCopy")  
  
 Üç değer vardır:  
  
- Kopyalama yayılmamasını  
  
- Yalnızca - bağlamak için kopyalama yaymak grubu yapıştırıldığında, bu bağlantı yeni kopyasını bağlantının diğer ucundaki var olan öğeye başvuracaktır.  
  
- Bağlamak için kopyalama yayar ve rol oyuncusu - bağlantının diğer ucundaki öğenin bir kopyasını kopyalanan grubu içerir.  
  
  ![İle PropagateCopyToLinkOnly kopyalama etkisini](../modeling/media/dslpropagatecopy.png "DslPropagateCopy")  
  
  Yaptığınız değişiklikler, öğeleri hem kopyalanan görüntünün etkiler.  
  
## <a name="programming-copy-and-paste-behavior"></a>Programlama Kopyala ve yapıştır davranışı  
 Birçok yönden bir DSL'nin davranış kopyalama, yapıştırma, oluşturma ve nesnelerin silinmesi ile ilgili bir örneği tarafından yönetilir <xref:Microsoft.VisualStudio.Modeling.ElementOperations> diyagrama eşleşmiş. Kendi sınıftan türetme tarafından DSL'NİZİN davranışı değiştirebilirsiniz <xref:Microsoft.VisualStudio.Modeling.ElementOperations> ve geçersiz kılma <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> diyagram sınıfınızın özelliği.  
  
> [!TIP]
>  Program kodu kullanarak model özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 ![Kopyalama işlemi için sıralı diyagram](../modeling/media/dslcopyseqdiagram.png "dslCopySeqDiagram")  
  
 ![Yapıştırma işlemi sıralı diyagramı](../modeling/media/dslpasteseqdiagram.png "dslPasteSeqDiagram")  
  
#### <a name="to-define-your-own-elementoperations"></a>Kendi ElementOperations tanımlamak için  
  
1. DSL projenizde yeni bir dosyasında türetilen bir sınıf oluşturun <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations>.  
  
2. Diyagram sınıfınız için bir parçalı sınıf tanımı ekleyin. Bu sınıf adını bulunabilir **Dsl\GeneratedCode\Diagrams.cs**.  
  
    Diyagram sınıfta geçersiz <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> , ElementOperations alt sınıf örneği dönün. Her çağrıda aynı örneği döndürmelidir.  
  
   Özel bir kod dosyasında DslPackage projesinde bu kodu ekleyin:  
  
```csharp  
  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
  
  public partial class MyDslDiagram  
  {  
    public override DesignSurfaceElementOperations ElementOperations  
    {  
      get  
      {  
        if (this.elementOperations == null)  
        {  
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);  
        }  
        return this.elementOperations;  
      }  
    }  
    private MyElementOperations elementOperations = null;  
  }  
  
  public class MyElementOperations : DesignSurfaceElementOperations  
  {  
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)  
      : base(serviceProvider, diagram)  
    { }  
    // Overridden methods follow  
  }  
  
```  
  
## <a name="receiving-items-dragged-from-other-models"></a>Diğer modellerinden sürüklenen öğe alma  
 ElementOperations, kopyalama ve taşıma, silme ve sürükle ve bırak davranışını tanımlamak için de kullanılabilir. ElementOperations kullanımına bir örnek, burada verilen örnek özel sürükle ve bırak davranışını tanımlar. Ancak, bu amaç için açıklanan alternatif bir yaklaşım göz önünde tutabileceğiniz [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md), olduğu daha genişletilebilir.  
  
 İki yöntem ElementOperations sınıfınızda tanımlayın:  
  
-   `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` Kaynak öğesi hedef şekli, bağlayıcı veya diyagram sürüklenebilen olup olmadığını belirler.  
  
-   `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` hangi hedef kaynak öğesi birleştirir.  
  
### <a name="canmerge"></a>CanMerge()  
 `CanMerge()` Diyagram üzerinde fareyi hareket ettirdikçe kullanıcıya verilmesi gerektiğini geri bildirim belirlemek için çağrılır. Yöntem parametreleri fareyi üzerine getirildiğinde öğesi ve sürükleme işlemi gerçekleştirildikten kaynağıyla ilgili verileri bilgileridir. Kullanıcının herhangi bir ekranda sürükleyebilirsiniz. Bu nedenle, kaynak nesnesi, farklı türlerde olabilir ve farklı biçimlerde seri hale getirilebilir. Kaynak bir DSL veya UML model veri parametresi serileştirmek ise, bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Sürükleyin, kopyalama ve araç operations ElementGroupPrototypes modelleri parçalarını temsil etmek için kullanın.  
  
 Bir öğe grubu prototip öğeleri ve bağlantılarına herhangi bir sayıda içerebilir. Öğe türleri GUID'ler tarafından tanımlanabilir. Temel alınan model öğesi değil sürüklenmiştir şeklin GUID'dir. Aşağıdaki örnekte, `CanMerge()` bir UML diyagramından bir sınıf şekil Bu diyagram üzerine sürüklediyseniz true değerini döndürür.  
  
```csharp  
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)  
 {  
  // Extract the element prototype from the data.  
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);  
  if (targetShape is MyTargetShape && prototype != null &&  
        prototype.RootProtoElements.Any(rootElement =>   
          rootElement.DomainClassId.ToString()   
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes  
          // or SourceClass.DomainClassId  
        return true;  
   return base.CanMerge(targetShape, data);  
 }  
  
```  
  
## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()  
 Bu yöntem, kullanıcının bir diyagram, Şekil veya bir bağlayıcı bir öğe bıraktığında çağrılır. Sürüklenen içeriği hedef öğeye birleştirmeniz gerekir. Bu örnekte, hedef ve prototip türleri birleşiminin tanıyıp tanımadığını kod belirler; Bu durumda, yöntem modele eklenmesi gereken öğelerin bir prototip sürüklenen öğeler dönüştürür. Taban yönteminin birleştirme dönüştürülmüş ya da dönüştürülmemiş öğeleri birini gerçekleştirmek için çağrılır.  
  
```csharp  
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)  
{  
  ElementGroupPrototype prototypeToMerge = sourcePrototype;  
  MyTargetShape pel = targetShape as MyTargetShape;  
  if (pel != null)  
  {  
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);  
  }  
  if (prototypeToMerge != null)  
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);  
}  
  
```  
  
 Bu örnek, bir UML sınıf diyagramından sürüklenen bir UML sınıf öğeleri ile ilgilidir. DSL UML sınıfları doğrudan depolamak üzere tasarlanmamıştır, ancak bunun yerine, her sürüklenen bir UML sınıf için bir DSL öğesi oluştururuz. Örneğin DSL örneği diyagram ise bu yararlı olacaktır. Kullanıcı sınıfları bu sınıfların örnekleri oluşturmak için diyagram üzerine sürükleyebilirsiniz.  
  
```csharp  
  
private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)  
{  
  // Find the UML project:  
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;  
  foreach (EnvDTE.Project project in dte.Solution.Projects)  
  {  
    IModelingProject modelingProject = project as IModelingProject;  
    if (modelingProject == null) continue; // not a modeling project  
    IModelStore store = modelingProject.Store;  
    if (store == null) continue;  
    // Look for the shape that was dragged:  
    foreach (IDiagram umlDiagram in store.Diagrams())  
    {  
      // Get modeling diagram that implements UML diagram:  
      Diagram diagram = umlDiagram.GetObject<Diagram>();  
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();  
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;  
      if (shape == null) continue;  
      IClass classElement = shape.ModelElement as IClass;  
      if (classElement == null) continue;  
  
      // Create a prototype of elements in my DSL, based on the UML element:  
      Instance instance = new Instance(snapshot.Store);  
      instance.Type = classElement.Name;  
      // Pack them into a prototype:  
      ElementGroup group = new ElementGroup(instance);  
      return group.CreatePrototype();  
    }  
  }  
  return null;  
}  
  
```  
  
## <a name="standard-copy-behavior"></a>Standart kopyalama davranışı  
 Bu bölümdeki kod yapabilecekleriniz yöntemleri kopyalama davranışı değiştirmek için geçersiz kılabilirsiniz gösterir. Kendi özelleştirmeleri elde etmeyi öğrenmek yardımcı olmak için bu bölümde kopyalanırken yöntemleri geçersiz kılan kodunu göstermektedir, ancak standart davranışını değiştirmez.  
  
 Kullanıcı CTRL + C tuşuna bastığında veya yöntem kopyalama menü komutunu kullanan <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> çağrılır. Nasıl bu ayarlanır gördüğünüz **DslPackage\Generated Code\CommandSet.cs**. Ayarlanan komutlar şeklini hakkında daha fazla bilgi için bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Kısmi sınıf tanımının ekleyerek ProcessOnMenuCopyCommand geçersiz kılabilirsiniz *MyDsl* `ClipboardCommandSet` DslPackage projedeki.  
  
```csharp  
using System.Collections.Generic;  
using System.Drawing;  
using System.Windows.Forms;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
partial class MyDslClipboardCommandSet  
{  
  /// <summary>  
  /// Override ProcessOnMenuCopyCommand() to copy elements to the  
  /// clipboard in different formats, or to perform additional tasks  
  /// before or after copying – for example deselect the copied elements.  
  /// </summary>  
  protected override void ProcessOnMenuCopyCommand()  
  {  
    IList<ModelElement> selectedModelElements = this.SelectedElements;  
    if (selectedModelElements.Count == 0) return;  
  
    // System container for clipboard data.  
    // The IDataObject can contain data in several formats.  
    IDataObject dataObject = new DataObject();  
  
    Bitmap bitmap = null; // For export to other programs.  
    try  
    {  
      #region Create EGP for copying to a DSL.  
      this.CopyModelElementsIntoElementGroupPrototype  
                     (dataObject, selectedModelElements);  
      #endregion  
  
      #region Create bitmap for copying to another application.   
      // Find all the shapes associated with this selection:  
      List<ShapeElement> shapes = new List<ShapeElement>(  
        this.ResolveExportedShapesForClipboardImages  
              (dataObject, selectedModelElements));  
  
      bitmap = this.CreateBitmapForClipboard(shapes);  
      if (bitmap != null)  
      {  
        dataObject.SetData(DataFormats.Bitmap, bitmap);  
      }  
      #endregion   
  
      // Add the data to the clipboard:  
      Clipboard.SetDataObject(dataObject, true, 5, 100);  
    }  
    finally  
    {  
      // Dispose bitmap after SetDataObject:  
      if (bitmap != null) bitmap.Dispose();  
    }  
  }  
/// <summary>  
/// Override this to customize the element group that is copied to the clipboard.  
/// </summary>  
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)  
{  
  return this.ElementOperations.Copy(dataObject, selectedModelElements);  
}  
}  
```  
  
 Her diyagram ElementOperations tekil örneğini yok. Kendi Türev sağlayabilirsiniz. DSL projede yerleştirilebilir, bu dosya, onu geçersiz kılar kodu aynı davranır:  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
namespace Company.MyDsl  
{  
  partial class MyDslDiagram  
  {  
    /// <summary>  
    /// Singleton ElementOperations attached to this diagram.  
    /// </summary>  
    public override DesignSurfaceElementOperations ElementOperations  
    {  
      get  
      {  
        if (this.elementOperations == null)  
        {  
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);  
        }  
        return this.elementOperations;  
      }  
    }  
    private MyElementOperations elementOperations = null;  
  }  
  
  // Our own version of ElementOperations so that we can override:  
  public class MyElementOperations : DesignSurfaceElementOperations  
  {  
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)  
      : base(serviceProvider, diagram)  
    { }  
  
    /// <summary>  
    /// Copy elements to the clipboard data.  
    /// Provides a hook for adding custom data.  
    /// </summary>  
    public override void Copy(System.Windows.Forms.IDataObject data,   
      ICollection<ModelElement> elements,   
      ClosureType closureType,   
      System.Drawing.PointF sourcePosition)  
    {  
      if (CanAddElementGroupFormat(elements, closureType))  
      {  
        AddElementGroupFormat(data, elements, closureType);   
      }  
  
      // Override these to store additional data:  
      if (CanAddCustomFormat(elements, closureType))  
      {  
        AddCustomFormat(data, elements, closureType, sourcePosition);  
      }  
    }  
  
    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)  
    {  
      // Add the selected elements and those implied by the propagate copy rules:  
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);  
  
      // Mark all the elements that are not embedded under other elements:  
      this.MarkRootElements(elementGroup, elements, closureType);  
  
      // Store in the clipboard data:  
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);  
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);  
    }  
  
    /// <summary>  
    /// Override this to store additional elements in the element group:  
    /// </summary>  
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)  
    {  
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);  
      return prototype;  
    }  
  
    /// <summary>  
    /// Create an element group from the given starting elements, using the   
    /// copy propagation rules specified in the DSL Definition.  
    /// By default, this includes all the embedded descendants of the starting elements,  
    /// and also includes reference links where both ends are already included.  
    /// </summary>  
    /// <param name="startElements">model elements to copy</param>  
    /// <param name="closureType"></param>  
    /// <returns></returns>  
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)  
    {  
      // ElementClosureWalker finds all the connected elements,   
      // according to the propagate copy rules specified in the DSL Definition:  
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,   
        closureType, // Normally ClosureType.CopyClosure  
        startElements,   
        true, // Do not load other models.  
        null, // Optional list of domain roles not to traverse.  
        true); // Include relationship links where both ends are already included.  
  
      walker.Traverse(startElements);  
      IList<ModelElement> closureList = walker.ClosureList;  
      Dictionary<object, object> closureContext = walker.Context;  
  
      // create a group for this closure  
      ElementGroup group = new ElementGroup(this.Partition);  
      group.AddRange(closureList, false);  
  
      // create the element group prototype for the group  
      foreach (object key in closureContext.Keys)  
      {  
        group.SourceContext.ContextInfo[key] = closureContext[key];  
      }  
  
      return group;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md)   
 [Nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md)   
 [Örnek: VMSDK devre diyagramları örnek](http://go.microsoft.com/fwlink/?LinkId=213879)



