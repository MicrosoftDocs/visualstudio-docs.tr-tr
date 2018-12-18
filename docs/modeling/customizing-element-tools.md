---
title: Öğe Araçlarını Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 332d7599543efbe5ee6e15ccc89d5fce595e5341
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566885"
---
# <a name="customizing-element-tools"></a>Öğe Araçlarını Özelleştirme
Bazı DSL tanımlarında öğeleri bir grup olarak tek bir kavramı gösterir. Örneğin, bir bileşen sabit bir dizi bağlantı noktası olan bir model oluşturursanız, her zaman aynı zamanda kendi ana bileşen oluşturulacak bağlantı noktalarını isteyebilirsiniz. Bu nedenle, bir grubu yerine yalnızca bir öğe oluşturur, böylece öğe oluşturma aracı özelleştirmeniz gerekir. Bunu başarmak için öğe oluşturma Aracı nasıl başlatılır özelleştirebilirsiniz.

 Ayrıca, araç diyagram veya öğenin sürüklediğinizde ne geçersiz kılabilirsiniz.

## <a name="customizing-the-content-of-an-element-tool"></a>Öğe araç içeriğini özelleştirme
 Her öğe araç bir örneğini depolar bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) bir veya daha fazla model öğelerini ve bağlantıları seri hale getirilmiş bir sürümünü içerir. Varsayılan olarak, bir öğe aracının EGP araç için belirttiğiniz sınıfının bir örneğini içerir. Geçersiz kılarak bu ayarı değiştirebilirsiniz *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. DSL paketi yüklendiğinde, bu yöntem çağrılır.

 Yönteminin parametresi, DSL tanımında belirtilen sınıfın kimliğidir. İlgilendiğiniz sınıfı ile yöntemi çağrıldığında, EGP ekstra öğeler ekleyebilirsiniz.

 EGP paketinizle öğeleri için bir ana öğe bağlantılarını ekleme içermesi gerekir. Referans bağlantıları da dahil edebilirsiniz.

 Aşağıdaki örnek, bir ana öğesi ve iki katıştırılmış öğeleri oluşturur. Ana sınıfı Direnci çağrılır ve iki gömme ilişkisi için Terminal adlı öğe vardır. Gömme rol özellikleri Terminal1 ve Terminal2 olarak adlandırılır ve her ikisi de 1..1 çokluğu sahip.

```csharp
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Öğe Oluşturma ve Hareketini Özelleştirme](../modeling/customizing-element-creation-and-movement.md)