---
title: 'Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4fdcdbead361a189d6b99a32ba09063e784aa5e2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892928"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama

Bir komut veya hareket işleyici alana özgü dilinizi yazarken, hangi öğe kullanıcı sağ belirleyebilirsiniz. Bazı şekilleri veya alanları seçilmesini de engelleyebilir. Örneğin, kullanıcı bir simge dekoratör tıkladığında, içerdiği şekli yerine seçili düzenleyebilirsiniz. Seçim bu şekilde sınırlama yazmanız gereken işleyicileri sayısını azaltır. Ayrıca şeklinde dekoratör önlemek gerek kalmadan herhangi bir yere tıklayın kullanıcı, kolaylaştırır.

## <a name="access-the-current-selection-from-a-command-handler"></a>Erişim geçerli seçim komut işleyicisi

Komut kümesi sınıfı için bir etki alanına özgü dil, özel komutları için komut işleyicileri içerir. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Komut kümesi sınıfı için bir etki alanına özgü dil türetildiği, sınıf, geçerli seçime erişme için bazı üyeleri sağlar.

Komut bağlı olarak, model Tasarımcısı, model Gezgini veya etkin pencere seçimi komut işleyici gerekebilir.

### <a name="to-access-selection-information"></a>Seçimi bilgilere erişmek için

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Sınıfı, geçerli seçimi erişmek için kullanılan aşağıdaki üyeleri tanımlar.

    |Üye|Açıklama|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> Yöntemi|Döndürür `true` modeli Tasarımcısı'nda seçilen öğelerden ise bir bölme şekli; Aksi takdirde, `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> Yöntemi|Döndürür `true` diyagram ise, model Tasarımcısı'nda seçilen; Aksi takdirde `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> Yöntemi|Döndürür `true` tam olarak bir öğe varsa seçili modeli Tasarımcısı'nda; Aksi takdirde `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> Yöntemi|Döndürür `true` tam olarak bir öğe varsa etkin pencere seçili; Aksi takdirde `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> Özelliği|Model Tasarımcısı'nda seçilen öğeleri salt okunur bir koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> Özelliği|Etkin penceresinde seçilen öğeleri salt okunur bir koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> Özelliği|Model tasarımcısında seçimin birincil öğe alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> Özelliği|Seçimin birincil öğe Etkin pencerede alır.|

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Özelliği <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> sınıfı erişim sağlar <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> model Tasarımcısı penceresinde temsil eder ve seçilen öğeleri modeli Tasarımcısı'nda ek erişim sağlayan nesne.

3.  Ayrıca, oluşturulan kod bir Gezgini araç penceresi özelliği tanımlar ve etki alanına özgü dil için sınıf komutu Gezgini seçimi özelliğinde ayarlayın.

    -   Gezgini araç penceresi özelliği etki alanına özgü dil Gezgini araç penceresi sınıfının bir örneğini döndürür. Gezgini araç penceresi sınıfın türetildiği <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> sınıfı ve etki alanına özgü dil modeli Gezgini temsil eder.

    -   `ExplorerSelection` Özelliği etki alanına özgü dil modeli Gezgini penceresinde seçilen öğeyi döndürür.

## <a name="determine-which-window-is-active"></a>Hangi pencerenin etkin olduğundan belirleme

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Arabirimi içeren geçerli seçim durumu Kabuğu'nda erişim sağlayan üyeleri tanımlar. Alabileceğiniz bir <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> paketi sınıf ya da komut kümesi sınıfı etki alanına özgü dil nesneden `MonitorSelection` her bir temel sınıfta tanımlanan özellik. Paket sınıfın türetildiği <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> sınıfı ve komut kümesi sınıfı türetilir <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> sınıfı.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Hangi türde bir pencere etkin olan bir komut işleyici belirlemek için

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Özelliği <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> sınıfı döndürür bir <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Kabuğu'nda geçerli seçim durumu erişim sağlayan nesne.

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Özelliği <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> arabirimi etkin penceresinden farklı olabilir etkin seçimin kapsayıcısı alır.

3.  Komutu aşağıdaki özelliklerde sınıfı sizin için ne tür bir pencere etkin olduğunu belirlemek için etki alanına özgü dil kümesine ekleyin.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Seçimi oranları

Seçim kuralları ekleyerek, hangi öğelerin kullanıcı modelde bir öğe seçtiğinde seçili kontrol edebilirsiniz. Örneğin, bir dizi öğe tek bir birim olarak değerlendirilecek izin vermek için bir seçim kuralı kullanabilirsiniz.

### <a name="to-create-a-selection-rule"></a>Bir seçim kuralı oluşturmak için

1.  DSL projesi içinde bir özel kod dosyası oluşturma

2.  Türetilen bir seçim kuralı sınıf tanımlama <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> sınıfı.

3.  Geçersiz kılma <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> seçimi kural sınıfının seçim ölçütlerini uygulamak için yöntemi.

4.  Özel kod dosyanıza ClassDiagram sınıfı için bir parçalı sınıf tanımı ekleyin.

     `ClassDiagram` Sınıf türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> sınıfı ve DSL projedeki Diagram.cs, üretilen kod dosyasında tanımlanır.

5.  Geçersiz kılma <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> özelliği `ClassDiagram` özel seçim kural döndürmek için sınıf.

     Varsayılan uygulaması <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> özellik seçimi değiştirmez bir seçim kuralı nesnesi alır.

### <a name="example"></a>Örnek

Aşağıdaki kod dosyası, her etki alanı şekillerinin başlangıçta seçili tüm örneklerini dahil etmek için seçimi genişletir bir seçim kuralı oluşturur.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>