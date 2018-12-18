---
title: UML API kullanarak UML sıralı diyagramlar Düzenle | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f68cf87a7f45b906c6de43e0a837d49132b7a3e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725553"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>UML API kullanarak sıralama diyagramlarını düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etkileşim bir dizi yaşam çizgileri arasında iletileri dizisidir. Etkileşim, UML sıralı diyagramda görüntülenir.  
  
 API tam ayrıntıları için bkz. <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Komut ve hareket işleyicileri için UML diyagramları yazmak için daha fazla genel bilgi için bkz. [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Temel kod  
  
### <a name="namespace-imports"></a>Namespace alır  
 Aşağıdaki içermelidir `using` ifadeleri:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Menü komutları oluşturma ve hareket işleyicileri, ayrıca gerekir:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Daha fazla bilgi için [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Bağlamı alma  
 Bir komut veya hareket işleyici sıralı diyagramda bir parçası olarak etkileşim düzenliyorsanız, başvuru içeriği elde edebilirsiniz. Örneğin:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Oluşturulan ve UML sıralı diyagramları  
 Sıralı diyagramlar iki tür vardır: bir UML modelleme projesinde el ile oluşturulan ve program kodundan oluşturulan olanlar. Kullanım `UmlMode` hangi sıralı diyagram bulunacak özelliğine sahiptir.  
  
> [!NOTE]
>  Bu özellik yalnızca sıralı diyagramlar false Visual Studio 2013'ü kullanarak koddan oluşturulan ve önceki döndürür. Bu koddan oluşturulan sıralı diyagramları 2013'ten ve daha önce geçirilen içerir. Yeni bir sıralı diyagramlar oluşturma Visual Studio'nun bu sürümü desteklemiyor.  
  
 Örneğin, bir menü komutu yalnızca UML sıralı diyagramlar üzerinde görünür hale getirmek isterseniz sonra `QueryStatus()` yöntemi aşağıdaki deyim içerir:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 Üzerinde oluşturulan bir sıralı diyagram, yaşam çizgilerini, iletileri ve diğer öğeleri çoğunlukla bir UML sıralı diyagramı üzerinde aynıdır. UML modelinde, diğer tüm öğelere sahip model bir kök modeli Store sahiptir. Ancak, bir null kök varsa kendi Model Store içinde oluşturulan etkileşim bulunmaktadır:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Oluşturma ve etkileşim görüntüleme  
 Alt öğe olarak etkileşim bir paket veya model oluşturun.  
  
 Boş bir sıralı diyagram üzerinde gerçekleştirilebilen bir komut geliştiriyorsanız Örneğin, her zaman etkileşim var olup olmadığını kontrol ederek başlamalısınız.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Etkileşim ve powerapps'in Düzen güncelleştiriliyor  
 Her zaman etkileşim güncelleştirdiğinizde, bağlantı işlemi aşağıdaki yöntemlerden birini kullanarak düzenini güncelleştirerek Bitir:  
  
- `ISequenceDiagram.UpdateShapePositions()` en son eklenen veya taşınan şekiller ve onların komşu şekillerinin konumunu ayarlar.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` tüm diyagramı yeniden çizer. Parametresi, yaşam çizgilerini, iletileri veya her ikisini de yeniden konumlandırma belirtmek için kullanabilirsiniz.  
  
  Yeni öğeler eklediğinizde veya mevcut öğeleri Taşı özellikle önemlidir. Bu işlemlerden birini gerçekleştirene kadar diyagram üzerinde doğru konumlarda olmayacaktır. Yalnızca bir kez sonunda bir dizi değişikliği, bu işlemlerin çağırmak gerekir.  
  
  Komutunuz sonra geri alma gerçekleştiren kullanıcının aklının karışmasını önlemek için bir `ILinkedUndoTransaction` yaptığınız değişiklikleri ve en son kapsamak için `Layout()` veya `UpdateShapePositions()` operations. Örneğin:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Kullanılacak bir `ILinkedUndoTransaction`, bu bildirim Sınıfınız içinde yapmanız gerekir:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Daha fazla bilgi için [işlemleri kullanarak bağlantı UML model güncelleştirmelerini](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Bir etkileşim oluşturma  
  
### <a name="to-create-lifelines"></a>Yaşam çizgileri oluşturmak için  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Bir yaşam çizgisi bağlanılabilir bir öğeyi diğer bir deyişle, bir türün bir örneğini temsil eder. Örneğin, bir bileşen kendi iç parçalarını gelen iletileri nasıl dağıttığını göstermek için etkileşim kullandıysanız, yaşam çizgilerini bileşenin parça ve bağlantı noktalarını temsil edebilir:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Etkileşim rasgele bir nesneler kümesini gösteriyorsa, alternatif olarak, bir özellik veya diğer oluşturabileceğiniz `IConnectableElement` etkileşim içinde:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Başka bir alternatif olarak, bir yaşam çizgisi türü ve adını bağlanılabilir bir öğeye bağlantılandırmadan ayarlayabilirsiniz:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>İletileri oluşturmak için  
 Bir ileti oluşturmak üzere ekleme noktalarını kaynak ve hedef yaşam çizgilerini belirlemeniz gerekir. Örneğin:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Tanımlanmamış bir kaynak veya hedef tanımlanmamış olan bir iletisi oluşturmak için:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Bir yaşam çizgisi üzerinde önemli noktaları hiç ekleme noktaları tanımlamak için kullanabileceğiniz birkaç ileti vardır:  
  
|ILifeline yöntemi|Bu noktada eklemek için kullanın|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|Yaşam çizgisinin üstünde.|  
|`FindInsertionPointAtBottom()`|Yaşam çizgisinin alt.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Belirtilen iletiyi hemen sonra bir nokta.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Nokta yaşam çizgisinin veya bir üst yürütme belirtimi bloğu üzerinde olabilir.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Etkileşim kullanımı izleyen bir nokta.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Birleştirilmiş parça izleyen bir nokta.|  
|`FindInsertionPoint(IExecutionSpecification block)`|Yürütme bloklarıyla üst.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|Bir işlenen bir birleştirilmiş parça üst.|  
  
 İletileri oluşturduğunuzda, başka bir iletiler üzerinden geçen bir ileti tanımlama kaçınmak için dikkatli olun.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Birleştirilmiş parçaları ve etkileşimi oluşturmak için kullanır  
 Öğe tarafından ele alınması gereken her yaşam çizgisi üzerinde bir ekleme noktası belirterek birleştirilmiş parçaları ve etkileşim kullanımları oluşturabilirsiniz. Var olan bir ileti veya parça üzerinden geçen noktaları kümesini belirtmekten kaçınmak için dikkatli olun.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Ayrıca, var olan bir dizi ileti kapsayan birleştirilmiş parça oluşturabilirsiniz. İletileri aynı yaşam çizgisinin veya yürütme bloğu tüm belirlenmelidir.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Birleştirilmiş parça ile tek bir işlenen her zaman oluşturulur. Yeni bir işlenen oluşturmak için önce veya sonra eklemek istediğiniz mevcut bir işlenen belirtin ve sonraki veya önceki eklemek istediğinizi:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Şekiller ile değişiklikleri tamamlanmazsa, yanlış konumda görünür bir `UpdateShapePositions()` veya `Layout()` işlemi.  
  
 Çoğu diğer sorunları, böylece yeni iletiler veya parçalar başkalarının geçmek zorunda yanlış hizalanmış, ekleme punto olarak kaynaklanır. Belirtiler değişiklik yapılmasını veya bir özel durum olabilir. Özel durum kadar atılabilir değil `UpdateShapePositions()` veya `Layout()` işlemi gerçekleştirildi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Özel tanımlama Modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



