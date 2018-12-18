---
title: Bir etki alanına özgü dil özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7fd63546f7d85ddbcc7661ac600a56bd340e6ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965232"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Bir etki alanına özgü dil özelleştirmek için kod yazma

Bu bölümde özel kod erişim, değiştirme veya bir etki alanına özgü dil bir model oluşturmak için nasıl kullanılacağını gösterir.

DSL ile çalışan kod yazabilirsiniz birkaç bağlamları vardır:

-   **Özel komutlar.** Kullanıcıların Diyagramı sağ tıklayarak çağırabileceği ve hangi model değiştirebilirsiniz bir komutu kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir komut için kısayol menüsü ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

-   **Doğrulama.** Model doğru bir durumda olduğunu doğrular kod yazabilirsiniz. Daha fazla bilgi için bkz: [bir etki alanına özgü dil doğrulama](../modeling/validation-in-a-domain-specific-language.md).

-   **Varsayılan davranışı geçersiz kılma.** Birçok yönünü DslDefinition.dsl oluşturulan kodu değiştirebilirsiniz. Daha fazla bilgi için bkz: [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).

-   **Metin dönüştürmeyi.** Bir model erişir ve bu örneğin program kodu oluşturmak bir metin dosyası oluşturur kodu içeren metin şablonları yazabilirsiniz. Daha fazla bilgi için bkz: [bir etki alanına özgü dil oluşturma koddan](../modeling/generating-code-from-a-domain-specific-language.md).

-   **Diğer Visual Studio uzantıları.** Modelleri okumak ve değiştirmek ayrı VSIX uzantıları yazabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: Program kodundaki dosyasından bir Model açın](../modeling/how-to-open-a-model-from-file-in-program-code.md)

İçinde DslDefinition.dsl tanımlayan sınıflar örneklerini adlı bir veri yapısında tutulur *bellek içi deposu* (IMS) veya *deposu*. Her zaman bir DSL tanımlayın sınıfları mağaza oluşturucuya bağımsız değişken olarak alın. Örneğin, DSL örnek adlı bir sınıf tanımlar:

`Example element = new Example (theStore);`

nesneler (yerine yalnızca olarak normal nesneler) deposunda tutmak birkaç avantaj sağlar.

-   **İşlemler**. Bir dizi ilgili değişikliği bir hareket halinde gruplayabilirsiniz.

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Bir özel durum değişiklikleri sırasında oluşursa, böylece son Commit() gerçekleştirilemiyor Store önceki durumuna geri sıfırlanır. Bu, hataları modeli tutarsız bir durumda bırakmadığından emin olmak için yardımcı olur. Daha fazla bilgi için bkz: [gezinme ve Program kodundaki bir modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **İkili ilişkileri**. İki sınıf arasında bir ilişki tanımlamak, her iki örnek diğer uçtaki gider bir özelliği vardır. İki ucu her zaman eşitlenir. Örneğin, üst ve alt öğeleri adlı rolleriyle parenthood ilişki tanımlarsanız yazabilirsiniz:

     `John.Children.Add(Mary)`

     Aşağıdaki ifadeler her ikisi de true sunulmuştur:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Aynı sonucu elde yazarak:

     `Mary.Parents.Add(John)`

     Daha fazla bilgi için bkz: [gezinme ve Program kodundaki bir modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Kurallar ve olayları**. Belirtilen değişiklik yapıldığında, yangın kurallar tanımlayabilirsiniz. Kurallar, örneğin, Şekil diyagramı bunlar sunmak model öğelerini ile güncel tutmak için kullanılır. Daha fazla bilgi için bkz: [yanıtlama ve yayılıyor değişiklikleri](../modeling/responding-to-and-propagating-changes.md).

-   **Seri hale getirme**. Deponun bir dosyaya içindeki nesneleri serileştirmek için standart bir yol sağlar. Seri hale getirme ve seri durumdan kuralları özelleştirebilirsiniz. Daha fazla bilgi için bkz: [özelleştirme dosya depolama ve XML serileştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)