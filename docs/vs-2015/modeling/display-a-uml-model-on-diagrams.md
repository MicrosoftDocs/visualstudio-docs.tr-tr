---
title: Bir UML modeli diyagramlar üzerinde görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd30d626d6500f7bf904350133ea33f2b2a25ac5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757309"
---
# <a name="display-a-uml-model-on-diagrams"></a>Diyagramlar üzerinde model görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program kodunda uzantı Visual Studio için diyagramlar üzerinde model öğelerini nasıl görüntüleneceğini denetleyebilirsiniz. Visual Studio'nun hangi sürümlerinin UML modellerini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bu konuda:  
 -   [Diyagramdaki bir öğe görüntülemek için](#Display)  
  
-   [Bir öğeyi temsil eden şekiller erişme](#GetShapes)  
  
-   [Şekiller yeniden boyutlandırma ve taşıma](#Moving)  
  
-   [Şekil diyagramdan kaldırmak için](#Removing)  
  
-   [Açma ve diyagramları oluşturma](#Opening)  
  
-   [Örnek: şekiller hizalamak için komutu](#AlignCommand)  
  
##  <a name="Display"></a> Diyagramdaki bir öğe görüntülemek için  
 Kullanım örneği veya bir eylem gibi bir öğe oluşturduğunuzda, kullanıcı UML Model Gezgini'nde görebilirsiniz, ancak bir diyagramda her zaman otomatik olarak görüntülenmez. Bazı durumlarda, görüntülenmesi için kod yazmanız gerekir. Aşağıdaki tabloda seçenekler özetlenmektedir.  
  
|Öğe türü|Örneğin|Bunu görüntülemek için kodunuzu gerekir.|  
|---------------------|-----------------|-------------------------------------|  
|Sınıflandırıcısı|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Belirtilen diyagramlarda ilişkili şekiller oluşturun. Herhangi bir sayıda her sınıflandırıcı şekilleri oluşturabilirsiniz.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Ayarlama `parentShape` için `null` diyagramın üst düzeyinde bir şekil için.<br /><br /> İçinde başka bir şekil görüntülenecek:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Not:** içinde görünen gerçekleştirirseniz bir **ILinkedUndo** işlem, yöntem bazen Hayır döndürür `IShape`. Ancak şekli doğru oluşturulur ve kullanarak erişilebilir. `IElement.Shapes().`|  
|Alt sınıflandırıcı|Öznitelik, işlem,<br /><br /> Bölümü, bağlantı noktası|Otomatik - kod gerekmez.<br /><br /> Bu, üst bir parçası olarak görüntülenir.|  
|Davranış|Etkileşim (dizi)<br /><br /> Etkinlik|Davranışı, uygun bir diyagrama bağlayın.<br /><br /> Her davranışı aynı anda en fazla bir diyagrama bağlı olabilir.<br /><br /> Örneğin:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Alt davranışı|Yaşam çizgilerini, iletileri, Eylemler, nesne düğümleri|Otomatik - kod gerekmez.<br /><br /> Üst bir diyagrama bağlıysa görüntülenir.|  
|İlişki|İlişkilendirme, Genelleştirme, akış, bağımlılık|Otomatik - kod gerekmez.<br /><br /> Bu diyagramda her ikisinde görüntülendiği görüntülenir.|  
  
##  <a name="GetShapes"></a> Bir öğeyi temsil eden şekiller erişme  
 Bir öğeyi temsil eden şekle türlerine ait:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 Burada *ElementType* model öğesi bir tür olduğu gibi `IClass` veya `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Tüm `IShapes` açık diyagramlarında bu öğenin temsil eder.|  
|`anElement.Shapes(aDiagram)`|Tüm `IShapes` belirli bir diyagram üzerinde bu öğenin temsil eder.|  
|`anIShape.GetElement()`|`IElement` Şekli temsil eden. Normalde IElement'in bir alt dönüştürürsünüz.|  
|`anIShape.Diagram`|`IDiagram` Şekli içeren.|  
|`anIShape.ParentShape`|İçeren şekil `anIShape`. Örneğin, bir bağlantı noktası şeklini bir bileşen şekil içinde yer alır.|  
|`anIShape.ChildShapes`|Şekil içinde yer alan bir `IShape` veya `IDiagram`.|  
|`anIShape.GetChildShapes<IUseCase>()`|İçinde bulunan şekiller bir `IShape` veya `IDiagram` gibi belirtilen türdeki öğeleri temsil `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Genel tür dönüştürme `IShape` için türü kesin belirlenmiş `IShape<IElement>`.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Bir şekil parametreli bir şekil türden diğerine dönüştürün.|  
  
##  <a name="Moving"></a> Şekiller yeniden boyutlandırma ve taşıma  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Taşıma veya bir şekil yeniden boyutlandırabilirsiniz.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Penceresini etkinleştir ve verilen tüm şekiller görünür, böylece diyagramı kaydırın. Şekilleri diyagram üzerinde olması gerekir. Varsa `zoomToFit` diyagram ölçeği gerekirse tüm şekiller görünür, böylece true olur.|  
  
 Bir örnek için bkz. [hizalama komutunu tanımlama](#AlignCommand).  
  
##  <a name="Removing"></a> Şekil diyagramdan kaldırmak için  
 Bazı öğe türleri şekilleri öğe silmeden silebilirsiniz.  
  
|Model öğesi|Şekil kaldırmak için|  
|-------------------|-------------------------|  
|Sınıflandırıcı: sınıf, arabirim, numaralandırma, aktör, kullanım örneği veya bileşeni|`shape.Delete();`|  
|Bir davranış: etkileşimi veya etkinlik|Diyagram projeden silebilirsiniz. Kullanım `IDiagram.FileName` olan yolu almak için.<br /><br /> Bu davranışı modelden silmez.|  
|Başka bir şekil|Bu gibi durumlarda, diğer şekiller açıkça diyagramdan silemezsiniz. Şekil, otomatik olarak modelden öğeyi silinirse veya üst şekil diyagramdan kaldırılır kaybolur.|  
  
##  <a name="Opening"></a> Açma ve diyagramları oluşturma  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Kullanıcının geçerli diyagrama bir komut veya hareket uzantısını erişmek için  
 İçeri aktarılan bu özelliği sınıfınızda bildirin:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 Bir yöntemde diyagrama erişebilirsiniz:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
>  Örneği `IDiagram` (ve onun alt türleri gibi `IClassDiagram`) işlerken komut içinde geçerlidir. Tutmak önerilmez bir `IDiagram` , kullanıcıya döndürülür ancak devam eden bir değişkende nesne.  
  
 Daha fazla bilgi için [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>Açık diyagramları bir listesini almak için  
 Projede şu anda açık olan diyagramları listesi:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>Bir proje diyagramlarında erişmek için  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, açın ve modelleme projeleri ve diyagramları oluşturmak için kullanılabilir.  
  
 Değerinden bool değerine atama fark `EnvDTE.ProjectItem` için `IDiagramContext`.  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 Örneklerini `IDiagram` ve denetime döndükten sonra onun alt türleri geçerli olmayan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Model deposundan de edinebilirsiniz bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
##  <a name="AlignCommand"></a> Örnek: şekiller hizalamak için komutu  
 Aşağıdaki kod, şekilleri düzgünce hizalayan bir menü komutu uygular. Kullanıcının ilk iki veya daha fazla şekil yaklaşık uyum içinde dikey veya yatay yerleştirmeniz gerekir. Ardından Hizala komutu merkezlerini hizalamak için kullanılabilir.  
  
 Komutunu kullanabilmek için bu kodu bir menü komutu projesine ekleyin ve sonra elde edilen uzantısı kullanıcılarınıza dağıtın. Daha fazla bilgi için [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [UML modelinde gezinme](../modeling/navigate-the-uml-model.md)   
 [Örnek: Şekilleri diyagram komutu Hizala.](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Örnek: Öğe, şekiller ve stereotipler oluşturma](http://go.microsoft.com/fwlink/?LinkId=213811)



