---
title: 'Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 260a1fdb78f1a9acf72a9789f12d7024cafe0c93
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859204"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme

Sürükle ve bırak olayları için işleyiciler DSL'nizi için ekleyebilirsiniz, böylece kullanıcılar öğeleri, diyagram üzerine diğer diyagramlardan veya Visual Studio'nun diğer kısımlarından sürükleyebilirsiniz. Olayları gibi çift tıklamaları birbirinden ayırma için de işleyicileri ekleyebilirsiniz. Sürükle ve bırak ve çift işleyicileri olarak birlikte bilinen *hareket işleyicileri*.

Bu konuda, diğer diyagramlar üzerinde kaynaklanan sürükle ve bırak hareketlerini anlatılmaktadır. Öğesinin tanımlamanın alternatif bir tek diyagramı içinde taşıma ve kopyalama olayları için göz önünde bulundurun `ElementOperations`. Daha fazla bilgi için [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md). DSL tanımını özelleştirmek mümkün olabilir.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Hareket işleyicileri ShapeElement yöntemi geçersiz kılarak tanımlama

`OnDragDrop`, `OnDoubleClick`, `OnDragOver`, ve diğer yöntemleri geçersiz kılınabilir.

Yeni bir kod dosyası DSL projenize ekleyin. Bir hareket işleyicisi için genellikle en az aşağıdaki olmalıdır `using` ifadeleri:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

Yeni dosya için sürükleme işlemi yanıt vermelidir Şekil veya diyagram sınıfı için bir parçalı sınıf tanımlar. Aşağıdaki yöntemleri geçersiz kıl:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-Bu yöntem, fare işaretçisini bir sürükleme işlemi sırasında şekil girdiğinde çağrılır. Yönteminizi kullanıcı sürükleyerek öğeyi incelemek ve kullanıcının bu şekli üzerinde öğeyi bırak olup olmadığını belirtmek için etkili özelliğini ayarlayın. Bu şeklin olduğundan ve ayrıca belirler efekt özelliği imleç görünümünü belirler olmadığını `OnDragDrop()` kullanıcı fare düğmesini bıraktığında çağrılır.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -Bu şekil veya diyagram fare işaretçisini ye dayanıyorsa sırasında kullanıcı fare düğmesi durumunda yayımlarsa bu yöntem çağrılır `OnDragOver(DiagramDragEventArgs e)` önceden ayarlanan `e.Effect` dışında bir değere `None`.

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -Bu yöntem, kullanıcı bir şekil veya diyagram çift tıkladığında çağrılır.

     Daha fazla bilgi için [nasıl yapılır: Şekil veya Dekoratörde bir Click için araya girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Tanımlama `IsAcceptableDropItem(e)` sürüklenen öğe kabul edilebilir olup ve öğe bırakıldığında modelinizi güncelleştirilecek ProcessDragDropItem(e) belirlemek için. Bu yöntemler olay bağımsız değişkenlerini öğesi ilk ayıklamanız gerekir. Bunu nasıl yapacağınız hakkında daha fazla bilgi için bkz. [sürüklenen öğe için bir başvuru almak nasıl](#extracting).

## <a name="define-gesture-handlers-by-using-mef"></a>MEF kullanarak hareket işleyicileri tanımlayın

DSL'nizi için kendi işleyicilerini tanımlamak için üçüncü taraf geliştiriciler istiyorsanız bu yöntemi kullanın. Kullanıcılar, bunlar DSL'nizi yükledikten sonra üçüncü taraf uzantıları yüklemeye seçebilirsiniz.

MEF (Yönetilen Genişletilebilirlik Çerçevesi) en düşük yapılandırmayla yüklenebilir bileşenleri tanımlamanıza olanak sağlar. Daha fazla bilgi için [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>MEF hareket işleyicisi tanımlama

1.  Ekleme, **Dsl** ve **DslPackage** projeleri **MefExtension** açıklanan dosyaları [MEF kullanarak DSL'nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md).

2.  Artık, bir MEF Bileşeni olarak hareket işleyici tanımlayabilirsiniz:

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     Sürüklenen nesne farklı türde olduğunda, gibi birden fazla hareket işleyicisi bileşeni oluşturabilirsiniz.

3.  Hedef şekli, bağlayıcının ya da diyagramda sınıfları için kısmi sınıf tanımları ekleyin ve yöntemleri tanımlamak `IsAcceptableDropItem()` ve `ProcessDragDropItem()`. Bu yöntemler olay bağımsız değişkenlerini sürüklenen öğe ayıklayarak başlaması gerekir. Daha fazla bilgi için [sürüklenen öğe için bir başvuru almak nasıl](#extracting).

## <a name="how-to-decode-the-dragged-item"></a>Sürüklenen öğe kodunu çözme

Öğeleri, herhangi bir penceresinden veya masaüstünden yanı sıra bir DSL sürüklenebilir.

Ne zaman kullanıcı bir öğeyi diyagram sürüklediğinde veya başka bir diyagram bir bölümünden sürüklenen öğe hakkındaki bilgilerin kullanılabilir `DiagramDragEventArgs`. Sürükleme işlemi ekrandaki herhangi bir nesnede başlattığınız için veriler çeşitli biçimlerde herhangi birinde kullanılabilir olabilir. Kodunuz, dağıtılmadan, uyumlu olduğu biçimleri tanıması gerekir.

Sürükle kaynak bilgileri kullanılabildiği biçimleri bulmak için hata ayıklama modu, giriş için bir kesme noktası ayarlamak kodunuzu çalıştırmak `OnDragOver()` veya `CanDragDrop()`. Değerlerini İnceleme `DiagramDragEventArgs` parametresi. Bilgiler iki biçimde sağlanır:

-   <xref:System.Windows.Forms.IDataObject>  `Data` -Bu özellik kaynak nesneleri seri hale getirilmiş sürümlerini genellikle birden çok biçimde gerçekleştirir. Kendi en kullanışlı işlevler şunlardır:

    -   diagramEventArgs.Data.GetDataFormats() - sürüklenen nesnenin çözmek biçimleri listeler. Örneğin, kullanıcı bir dosyayı masaüstünden sürüklediğinde, kullanılabilir biçimler dosya adı dahil ("`FileNameW`").

    -   `diagramEventArgs.Data.GetData(format)` -Belirtilen biçimde sürüklenen nesnenin kodunu çözer. Nesne için uygun bir tür cast. Örneğin:

         `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

         Ayrıca, kendi özel biçiminde kaynak modeli yol başvuruları gibi nesneleri iletebilir. Daha fazla bilgi için [gönderme modeli yol başvuruları bir Sürükle ve bırak nasıl](#mbr).

-   <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` -Bir DSL veya UML model öğelerini sürükleyin açmasını istiyorsanız bu özelliği kullanın. Bir öğe grubu prototip, bir veya daha fazla nesneyi, bağlantılar ve özellik değerlerini içerir. Ayrıca, yapıştırma işlemlerine ve ne zaman araç kutusundan bir öğe ekleme kullanılır. Bir prototip içinde nesneler ve bunların türlerini GUID ile tanımlanır. Örneğin, bu kod, kullanıcının bir UML diyagram veya UML Model Gezgini sınıfı öğelerini sürükleyin izin verir:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     UML şekiller kabul etmek için deneme tarafından UML Şekil sınıfları GUID'lerini belirleyin. Olduğunu genellikle birden fazla öğe türüne ilişkin herhangi bir diyagram üzerindeki unutmayın. Ayrıca bir DSL veya UML diyagramından sürüklenen nesnenin şeklini, model öğesi olduğunu unutmayın.

`DiagramDragEventArgs` Ayrıca, geçerli fare işaretçisi konumunu ve kullanıcı CTRL, ALT veya üst karakter tuşları basarak olduğunu belirten özellikleri vardır.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Sürüklenen öğenin özgün alma

Bir DSL öğesi sürüklenen öğe ise kaynak modeli açmak ve öğesine erişme.

`Data` Ve `Prototype` olay bağımsız değişkenlerinin özellikleri sürüklenen şekli yalnızca bir başvuru içerir. Bir şekilde prototip türetilir DSL hedef nesneyi oluşturmak istiyorsanız, genellikle, özgün erişim elde etmek Örneğin, dosya içeriğini okumak veya bir şekil tarafından temsil edilen model öğesine giderek gerekir. Visual Studio Model veri yolu, bu konuda yardımcı olmak için kullanabilirsiniz.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Model veri yolu için bir DSL projesini hazırlama

1.  DSL kaynak Visual Studio Model veri yolu tarafından erişilebilir hale getirir:

    1.  İndirip Visual Studio Model veri yolu uzantı zaten yüklü değilse yükleyin. Daha fazla bilgi için [Görselleştirme ve modelleme SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  DSL tanım dosyası kaynak DSL DSL Tasarımcısı'nda açın. Tasarım yüzeyine sağ tıklayın ve ardından **etkinleştirme Modelbus**. İletişim kutusunda, birini veya her ikisini seçenekleri seçin.  **Tamam**'ı tıklatın. Yeni bir proje "ModelBus" DSL çözüme eklenir.

    3.  Tıklayın **tüm Şablonları Dönüştür** ve çözümü yeniden oluşturun.

### <a name="to-send-an-object-from-a-source-dsl"></a>Bir nesne bir kaynaktan DSL göndermek için

1.  ElementOperations alt sınıfı geçersiz kılma `Copy()` böylece IDataObject bir Model veri yolu başvurusu (MBR) kodlar. Kullanıcının kaynak diyagramdan sürükleyin başladığında, bu yöntem çağrılır. Kullanıcı hedef diyagramda düştüğünde kodlanmış MBR IDataObject kullanılabilir olacaktır.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Bir DSL hedef DSL veya UML projede modeli Bus başvurusu almak için

1.  Hedef DSL proje proje başvurular ekleyin:

    -   Kaynak Dsl projesi.

    -   Kaynak ModelBus proje.

2.  Hareket işleyici kod dosyasında, aşağıdaki ad alanı başvurularını ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3.  Aşağıdaki örnek, kaynak model öğesine erişmek verilmektedir:

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Bir öğe kabul etmek için bir UML modelinden kaynağı

-   Aşağıdaki kod örneği bir nesne kabul eden bir UML diyagramından bırakıldı.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Fare eylemleri kullanarak: Bölme öğeleri sürükleme

Bir şeklin alanlarda fare işlemlerini durdurur bir işleyici yazabilirsiniz. Aşağıdaki örnek, kullanıcının fare ile sürükleyerek bir bölme öğeleri yeniden sıralamak olanak tanır.

Bu örneği oluşturmak için bir çözüm kullanarak oluşturma **sınıf diyagramları** çözüm şablonu. Bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin. Ad alanı olarak kendi aynı olacak şekilde ayarlayın.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)
- [Etki Alanına Özgü Dil Çözümlerini Dağıtma](../modeling/deploying-domain-specific-language-solutions.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
