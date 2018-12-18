---
title: Etki Alanı Özellik Değeri Değişiklik İşleyicileri
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 834ee518269c414c8a4ee08b056369813e0a1751
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057554"
---
# <a name="domain-property-value-change-handlers"></a>Etki alanı özellik değeri değişiklik işleyicileri

Bir etki alanı özelliğinin değeri değiştiğinde bir Visual Studio etki alanına özgü dil de `OnValueChanging()` ve `OnValueChanged()` yöntemleri, etki alanı özelliği işleyicisinde çağrılır. Değişikliğin yanıt vermek için bu yöntemleri geçersiz kılabilirsiniz.

## <a name="override-the-property-handler-methods"></a>Özellik işleyici yöntemleri geçersiz kılın

Her bir etki alanı, etki alanına özgü dil özelliği, üst etki alanı sınıf içinde iç içe geçmiş bir sınıf tarafından işlenir. Biçim adını izleyen *PropertyName*PropertyHandler. Bu özellik işleyicisi sınıf dosyasında inceleyebilirsiniz **Dsl\Generated Code\DomainClasses.cs**. Sınıfında, `OnValueChanging()` değer değişikliklerini hemen önce çağrılır ve `OnValueChanged()` hemen değeri değiştikten sonra çağrılır.

Örneğin, adında bir etki alanı sınıfı olduğunu varsayalım `Comment` adlı bir dize etki alanı özelliği olan `Text` ve adlı bir tamsayı özelliği `TextLengthCount`. Neden `TextLengthCount` her zaman uzunluğunu içeren `Text` dize Dsl projesi içinde ayrı bir dosyada aşağıdaki kodu yazabilirsiniz:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Özellik işleyicileri hakkında aşağıdaki noktalara dikkat edin:

-   Kullanıcı bir alan özelliği için değişiklik yapıldığında, hem program kodu özelliği için farklı bir değer atandığında özellik işleyici yöntemleri çağrılır.

-   Yöntemleri aslında yalnızca değeri değiştiğinde çağrılır. Program kodu geçerli değerine eşit olan bir değer atar, işleyici çağrılmaz.

-   Hesaplanan ve özel depolama etki alanı özellikleri T:System.Windows.PropertyChangedCallback ve OnValueChanging yöntemleri yok.

-   Bir değişiklik işleyici yeni değeri değiştirmek için kullanamazsınız. Örneğin belirli bir aralık değeri kısıtlamak, tanımlamak Bunu yapmak istiyorsanız bir `ChangeRule`.

-   Bir ilişkinin bir rolü temsil eden bir özellik için bir değişiklik işleyicisi eklenemiyor. Bunun yerine tanımlayın bir `AddRule` ve `DeleteRule` ilişki sınıfı üzerinde. Bağlantı oluşturulduğunda veya değiştirildiğinde, bu kural tetiklenir. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Mağazada değişiklikleri

Değişiklik başlatan bir işlem içinde özellik işleyici yöntemleri çağrılır. Bu nedenle, daha fazla depoda yeni bir işlem açmaya gerek kalmadan değişiklik yapabilirsiniz. Değişikliklerinizi ek işleyicisi çağrıları neden olabilir.

Bir işlem geri alınamaz, geri alınmış veya geri alınamaz; değişiklik yapmamalısınız Mağazası'nda, diğer bir deyişle, model öğelerini, ilişkiler, şekiller, bağlayıcılar diyagramları veya özelliklerini değiştirir.

Model dosyasından yüklenirken Ayrıca, genellikle değerleri güncelleştirilecek değil.

Model değişiklikleri, bu nedenle böyle bir test tarafından korunmalıdır:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Aksine, özellik işleyicisi değişiklikleri store dışına yayılırsa, örneğin, bir dosya, veritabanı veya mağaza içi değişkenler, ardından her zaman kullanıcı geri çağırdığında dış değerlerin güncelleştirilmesi belirtilen değişiklikleri yapmak veya gerekir Yinele.

### <a name="cancel-a-change"></a>Değişikliği iptal et

Bir değişiklik engellemek istiyorsanız, geçerli işlem geri alabilirsiniz. Örneğin, bir özelliği belirli bir aralıkta kalmasını sağlamak isteyebilirsiniz.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatif yöntem: hesaplanan özellikleri

Önceki örnekte, bir etki alanı özelliğinden değerlere yayılması OnValueChanged()'ın nasıl kullanılabileceğini gösterir. Her bir özellik depolanan değerine sahiptir.

Bunun yerine, türetilen özelliği hesaplanan özellik tanımlama düşünebilirsiniz. Durumda, özelliği, kendi hiçbir depolama alanına sahip ve tanımlanıyor işlevi değeri gerekli olduğunda değerlendirilir. Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

Önceki örnekte yerine, ayarlayabilirsiniz **tür** alanını `TextLengthCount` olmasını **hesaplanan** DSL tanımındaki. Kendi sağlandığından **alma** bu etki alanı özelliği için yöntemi. **Alma** yöntemi geçerli uzunluğunu döndürmesine `Text` dize.

Ancak, olası bir dezavantajı hesaplanan özellikler, ifade değeri, bir performans sorunu sayacağı kullanıldığı her zaman değerlendirilir olur. Ayrıca, hiçbir OnValueChanging() ve yoktur OnValueChanged() hesaplanan bir özellik.

### <a name="alternative-technique-change-rules"></a>Alternatif yöntem: kuralları Değiştir

Bir ChangeRule tanımlarsanız, bir özelliğin değerini değiştirir, bir işlem sonunda yürütülür.  Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).

Bir işlemde birkaç değişiklik yapılırsa, tüm tamamlandığı zaman ChangeRule yürütür. Bunun aksine, OnValue... tarafından yöntemleri, bazı değişiklikler gerçekleştirilmemiş olduğunda yürütülür. Elde etmek istediğinize bağlı olarak, bu bir ChangeRule daha uygun hale getirebilirsiniz.

Bir ChangeRule, belirli bir aralıkta tutmak için özelliğin yeni değeri ayarlamak için de kullanabilirsiniz.

> [!WARNING]
> Kural deposu içeriği değişiklikler yaparsa, diğer kurallar ve özellik işleyicileri tetiklenebilir. Bir kural tetiklediği özelliği değişirse, tekrar çağrılır. Kural tanımlarınızı sonsuz tetikleme neden olduğunu emin olmanız gerekir.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, bir etki alanı özelliğin özellik işleyicisi geçersiz kılar ve bir özellik için kullanıcıyı uyarır `ExampleElement` etki alanı sınıfı değişti.

### <a name="code"></a>Kod

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```