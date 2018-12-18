---
title: Değişiklikleri Modelin İçinde Yayan Kurallar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8f506b71240024206523821080cdf958660aa963
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865979"
---
# <a name="rules-propagate-changes-within-the-model"></a>Değişiklikleri Modelin İçinde Yayan Kurallar
Bir değişiklik bir öğeden diğerine Görselleştirme ve modelleme SDK'sı (VMSDK) yaymak için bir depo oluşturabilirsiniz. Store herhangi bir öğeye bir değişiklik meydana geldiğinde, kuralları genellikle en dıştaki işlem tamamlandığında, yürütülmek üzere zamanlanır. Farklı türde bir öğe ekleme veya silme gibi olaylar, farklı türleri için kuralları vardır. Belirli öğeleri, şekilleri ve diyagramları türleri için kurallar ekleyebilirsiniz. Birçok yerleşik özellik kuralları tarafından tanımlanır: Örneğin, kuralları modeli değiştiğinde, diyagram güncelleştirildiğinden emin olun. Kendi kurallarınızı ekleyerek, etki alanına özgü dil özelleştirebilirsiniz.

 Store kuralları mağazasındaki - diğer bir deyişle, değişiklikleri yayma model öğelerini, ilişkiler, şekiller veya bağlayıcıları ve kendi etki alanı değişiklikleri özellikleri için özellikle yararlıdır. Kullanıcı geri alma veya yineleme komutları çağırdığında kuralları çalıştırmayın. Bunun yerine, hareket Yöneticisi deposu içeriği doğru duruma geri yüklendiğinden emin yapar. Mağaza dışındaki kaynaklar değişiklikleri yaymak Store olayları kullanın. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Örneğin, kullanıcı (veya kodunuzu) ExampleDomainClass türünde yeni bir öğe oluşturduğunda, başka bir tür ek bir öğe başka bir modelin parçası oluşturduğunuz belirlemek istediğinizi varsayalım. Bir AddRule yazma ve ExampleDomainClass ile ilişkilendirebilirsiniz. Kuralda ek öğesi oluşturmak için kod yazmak istediğiniz.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
>  Store içinde öğeleri durumunu yalnızca bir kural kodunu değiştirmeniz gerekir; diğer bir deyişle, kuralı, yalnızca model öğelerini, ilişkileri, şekiller, bağlayıcılar, diyagram veya özelliklerini değiştirmeniz gerekir. Mağaza dışındaki kaynaklar için değişiklikleri yayan istiyorsanız, Store olaylarını tanımlayın. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Bir kural tanımlamak için

1. Bir sınıf ön eki olarak kuralı tanımlamak `RuleOn` özniteliği. Öznitelik kuralı bir etki alanı sınıfları, ilişkilerini veya diyagram öğeleri ile ilişkilendirir. Kural soyut bu sınıfın her örneği için uygulanır.

2. Kural kümesi tarafından döndürülen ekleyerek kaydetme `GetCustomDomainModelTypes()` etki alanı model sınıfınızdaki.

3. Kural sınıfı soyut kural sınıflarının birinden türetilir ve yürütme yönteminin yazma.

   Aşağıdaki bölümlerde daha ayrıntılı adımları açıklanmaktadır.

### <a name="to-define-a-rule-on-a-domain-class"></a>Bir etki alanı sınıf üzerinde bir kural tanımlamak için

-   Özel bir kod dosyasında, bir sınıf tanımlayabilir ve önüne <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> özniteliği:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   Konu Türü ilk parametre olarak bir etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya diyagram olabilir. Genellikle, kurallar alan sınıfları ile ilişkiler için geçerlidir.

     `FireTime` Genellikle `TopLevelCommit`. Bu, yalnızca işlem birincil tüm değişiklikler yapıldıktan sonra kuralın yürütülmesini sağlar. Alternatifleri satır içi kural değişiklikten hemen sonra yürütür niteliktedir; ve LocalCommit, kural (Bu, en dıştaki olmayabilir) geçerli işlem sonunda yürütür. Ayrıca kuyrukta sıralama etkilemek için bir kuralın önceliğini ayarlayabilirsiniz ancak ihtiyaç duyduğunuz sonucu elde etmek, güvenilir olmayan bir yöntem budur.

-   Bir Özet sınıf konu türü olarak belirtebilirsiniz.

-   Kural, konu sınıfın tüm örnekleri için geçerlidir.

-   İçin varsayılan değer `FireTime` TimeToFire.TopLevelCommit olduğu. Bu kural, en dıştaki işlem tamamlandığında yürütülecek neden olur. TimeToFire.Inline yönteminin bir alternatifidir. Bu kural yakında tetikleme olayından sonra yürütülecek neden olur.

### <a name="to-register-the-rule"></a>Kuralı kaydetmek için

-   Tarafından döndürülen türleri listesinde, kural sınıfı eklemek `GetCustomDomainModelTypes` etki alanı modelinizdeki:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

-   Etki alanı model sınıfınızın adından emin değilseniz, dosyanın konum **Dsl\GeneratedCode\DomainModel.cs**

-   DSL projenize özel bir kod dosyasında bu kod yazın.

### <a name="to-write-the-code-of-the-rule"></a>Kuralın kod yazmak için

- Kural sınıfı aşağıdaki temel sınıflarının birinden türetilir:


  | Temel sınıf | Tetikleyici |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Bir öğe, bağlantı veya şekil eklenir.<br /><br /> Yeni öğelerin yanı sıra yeni ilişkiler algılamak için bunu kullanın. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Bir etki alanı özellik değeri değiştirilir. Yöntem bağımsız değişkenleri, eski ve yeni değerleri sağlar.<br /><br /> Şekiller için bu kural tetiklenir, yerleşik `AbsoluteBounds` şekli taşınırsa özellik değişiklikleri.<br /><br /> Çoğu durumda, geçersiz kılmak daha kullanışlı olan `OnValueChanged` veya `OnValueChanging` özellik işleyicisi. Bu yöntemler hemen önce ve değişiklikten sonra çağrılır. Aksine, kural, genellikle işlem sonunda çalışır. Daha fazla bilgi için [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md). **Not:** bağlantı oluşturulduğunda veya bu kural tetiklenir değil. Bunun yerine, yazma bir `AddRule` ve `DeleteRule` alan ilişkisine yönelik. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Bir öğe veya bağlantı silinmek üzere olduğunda tetiklenir. ' % S'özelliği ModelElement.IsDeleting işlemin sonuna kadar geçerlidir. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Bir öğe veya bağlantı silindiğinde gerçekleştirdi. Kural DeletingRules dahil olmak üzere diğer tüm kurallar yürütüldüğünü sonra yürütülür. ModelElement.IsDeleting yanlış ve ModelElement.IsDeleted geçerlidir. Bir sonraki geri alma için izin vermek için öğe gerçekten bellekten kaldırılmaz, ancak Store.ElementDirectory kaldırılır. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Bir öğenin bir depo bölümünden diğerine taşınır.<br /><br /> (Bu bir şekil grafik konumuna ilgili olmadığını unutmayın.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Bu kural yalnızca etki alanı ilişkileri için geçerlidir. Bir model öğesini açıkça bir bağlantı ya da sonuna kadar atarsanız tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Bağlantılar için veya bir öğeden sıralama MoveBefore veya MoveToIndex yöntemleri bir bağlantıyı kullanarak değiştirildiğinde tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Bir işlem oluşturulduğunda yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | İşlem yaklaşık olarak yürütülmesi için olduğunda yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Hareket hakkında geri alınması ise yürütülür. |


- Her sınıf, geçersiz bir yönteme sahip. Tür `override` sınıfınızdaki bulmak için. Bu yöntem parametresi olarak değiştirilmektedir öğe tanımlar.

  Kurallar hakkında aşağıdaki noktalara dikkat edin:

1.  Bir işlemde değişiklik kümesini birçok kuralları tetikleyebilir. Genellikle, en dıştaki işlem tamamlandığında kurallar yürütülür. Bunlar, belirtilmemiş sırayla yürütülür.

2.  Bir kural, bir işlem içinde her zaman yürütülür. Bu nedenle, değişiklik yapmak için yeni bir işlem oluşturmanız gerekmez.

3.  Kurallar, bir işlem geri alındı veya geri alma veya yineleme işlemleri gerçekleştirildiğinde yürütülmez. Bu işlemler Store tüm içeriği önceki durumuna sıfırlayın. Kural Store dışındaki her şeyi durumu değişirse, bu nedenle, bunu synchronism Store ile içerik bulundurun değil. Store dışında durumunu güncellemek için olayları kullanmak en iyisidir. Daha fazla bilgi için [olay işleyicileri yaymak değişiklikleri dışında modeli](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4.  Bir model dosyasından yüklendiğinde bazı kurallar yürütülür. Yüklenirken veya kaydedilirken ediyor olup olmadığını belirlemek için `store.TransactionManager.CurrentTransaction.IsSerializing`.

5.  Daha fazla kural tetiklendiğinde, kural kodunu oluşturur, bunlar Açmadığınızda listenin sonuna eklenir ve işlem tamamlanmadan önce yürütülür. DeletedRules sonra diğer tüm kurallar yürütülür. Bir kural her değişiklik için bir kez bir işlemde birden çok kez çalıştırabilirsiniz.

6.  Gelen kuralları ve bilgi geçirmek için bilgileri depolayabilirsiniz `TransactionContext`. İşlem sırasında korunur bir sözlük budur. İşlem sona erdiğinde atıldı. Olay bağımsız değişkenleri her kuralda erişim sağlamak. Kuralları tahmin edilebilir bir sırada yürütülmez unutmayın.

7.  Diğer seçenekleri dikkate alındıktan sonra kuralları kullanın. Örneğin, bir özellik değeri değiştiğinde güncelleştirmek istiyorsanız, hesaplanan bir özellik kullanmayı düşünün. Bir şekil konumunu ve boyutunu sınırlandırmak istiyorsanız, kullanan bir `BoundsRule`. Bir özellik değeri bir değişikliğe yanıt vermek istiyorsanız ekleyin bir `OnValueChanged` özelliğine işleyici. Daha fazla bilgi için [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki öğe bağlamak için bir etki alanı ilişkisi örneği oluşturulduğunda bir özelliğini güncelleştirir. Program kodu bir bağlantı oluşturması halinde yalnızca kullanıcı bağlantısını bir diyagram üzerinde de oluşturduğunda, bu kural tetiklenir.

 Bu örnekte test etmek için Görev akışı çözüm şablonu kullanarak bir DSL oluşturmak ve bir Dsl proje dosyasında aşağıdaki kodu ekleyin. Derleme çözümü çalıştırın ve hata ayıklama projede örnek dosyasını açın. Açıklama şekli ile bir akış öğesi arasında bir açıklama bağlantısı çizin. Yorum metni ona bağlı en son öğeyi raporda değiştirir.

 Uygulamada, her AddRule için genellikle bir DeleteRule yazmalısınız.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)
- [BoundsRules Şekil Konumunu ve Boyutunu Kısıtlamama](../modeling/boundsrules-constrain-shape-location-and-size.md)