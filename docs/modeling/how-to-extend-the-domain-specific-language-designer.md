---
title: 'Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6a2388619dea31696fe4416032cc12cd1fe5b372
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860374"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme

DSL tanımlarına düzenlemek için kullandığınız Tasarımcı için Uzantılar yapabilirsiniz. Menü komutları, ekleme, işleyiciler için sürükleyin ve hareketlerini ve belirli tür değerleri veya ilişkileri değiştirdiğinizde tetiklenen kuralları ekleme yapabileceğiniz uzantı türleri. Uzantılar, paketlenmiş bir Visual Studio Tümleştirme Uzantısı (VSIX olarak) ve diğer kullanıcılara dağıtılır.

Örnek kod ve bu özellik hakkında daha fazla bilgi için bkz. Visual Studio [Görselleştirme ve modelleme SDK'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Çözümü ayarlama

Uzantınızı kodunu içeren bir proje ve proje dışarı aktaran bir VSIX projesine ayarlayın. Çözümünüzü aynı VSIX içinde eklenen diğer proje içerebilir.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Bir DSL Tasarımcısı uzantısı çözümü oluşturmak için

1.  Sınıf kitaplığı proje şablonunu kullanarak yeni bir proje oluşturun. İçinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** ve tıklayın ardından Orta penceresinde **sınıf kitaplığı**.

     Bu proje uzantılarınızı kodunu içerir.

2.  VSIX proje şablonunu kullanarak yeni bir proje oluşturun. İçinde **yeni proje** iletişim kutusunda **Visual C#**, tıklayın **genişletilebilirlik**ve ardından Orta penceresi seçin **VSIX projesi**.

     Seçin **çözüme ekleyin**.

     Source.extension.vsixmanifest VSIX bildirim düzenleyicisinde açılır.

3.  İçerik alanı **İçerik Ekle**.

4.  İçinde **İçerik Ekle** iletişim kutusu, kümesi **içerik türünü seçin** için **MEF Bileşeni**, ayarlayıp **proje** sınıf kitaplığı projenize.

5.  Tıklayın **sürümleri seçin** emin olun **Visual Studio Enterprise** denetlenir.

6.  VSIX projesinin çözümün başlangıç projesi olduğundan emin olun.

7.  Sınıf kitaplığı projesinde aşağıdaki derlemelere başvurular ekleyin:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Test ve dağıtım

Bu konuda herhangi bir uzantı sınamak için derleme ve çözümü çalıştırın. Visual Studio deneysel örneği açılır. Bu örnekte, bir DSL çözümünü açın. DslDefinition diyagramını düzenleyin. Uzantı davranışı görülebilir.

Uzantıları için ana Visual Studio ve diğer bilgisayarlara dağıtmak için aşağıdaki adımları izleyin:

1.  VSIX projenizde depo VSIX yükleme dosyasını bulmak\\*\*\\\*.vsix

2.  Bu dosyayı hedef bilgisayara kopyalayın ve ardından Windows Explorer (veya dosya Gezgini) çift tıklayın.

     Uzantının yüklü olduğunu doğrulamak için Visual Studio Uzantı Yöneticisi açılır.

Uzantıyı kaldırmak için aşağıdaki adımları izleyin:

1.  Visual Studio'da üzerinde **Araçları** menüsünde tıklatın **Uzantı Yöneticisi**.

2.  Uzantıyı seçin ve silin.

## <a name="add-a-shortcut-menu-command"></a>Bir kısayol menü komutu ekleme

DSL Tasarımcısı yüzeyine veya DSL Gezgini penceresinde görünen bir kısayol menü komutu yapmak için aşağıdaki benzeyen bir sınıf yazın.

Sınıf uygulamalıdır `ICommandExtension` ve özniteliği olmalıdır `DslDefinitionModelCommandExtension`.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Fare hareketlerini işleme

Kod menü komutunu koda benzer.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Değişiklikleri değerine Yanıtla

Bu işleyici, düzgün çalışması için bir etki alanı modeli gerekir. Basit bir etki alanı modeli sunuyoruz.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Aşağıdaki kod, basit bir modeli uygular. Yer tutucu değiştirmek için yeni bir GUID oluşturun.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```