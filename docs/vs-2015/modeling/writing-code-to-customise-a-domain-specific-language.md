---
title: Bir etki alanına özgü dili özelleştirmek için kod yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: affa3db292ed23ca52b0cca810daf5ca70ad0fd1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866330"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde erişim, değiştirme veya bir etki alanına özgü dili bir model oluşturmak için özel kod kullanma gösterilmektedir.  
  
 Bir DSL ile çalışan kod yazabileceğiniz birkaç bağlamları vardır:  
  
- **Özel komutlar içerir.** Kullanıcı diyagramda sağ tıklayarak çağırabilir ve model değişiklik yapabilir, bir komut oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
- **Doğrulama.** Model doğru bir durumda olduğunu doğrulayan bir kod yazabilirsiniz. Daha fazla bilgi için [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).  
  
- **Varsayılan davranışı geçersiz kılma.** DslDefinition.dsl oluşturulan kodu birçok yönünü değiştirebilirsiniz. Daha fazla bilgi için [geçersiz kılma ve oluşturulan sınıflar genişletme](../modeling/overriding-and-extending-the-generated-classes.md).  
  
- **Metin dönüştürme.** Bir model erişen ve örneğin program kodu oluşturmak bir metin dosyası oluşturur, kodu içeren metin şablonlarınızı yazabilirsiniz. Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).  
  
- **Diğer Visual Studio uzantıları.** Okuma ve değiştirme modelleri ayrı VSIX uzantıları yazabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Program kodunda dosyadan Model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  DslDefinition.dsl tanımlayan sınıf örneklerini adlı bir veri yapısı içinde tutulur *bellek içi Store* (IMS) veya *Store*. Bir DSL içinde her zaman tanımladığınız sınıfları bir Store oluşturucusuna bağımsız değişken olarak yararlanın. Örneğin DSL'nizi örnek adlı bir sınıf tanımlar:  
  
  `Example element = new Example (theStore);`  
  
  Store (yalnızca olarak sıradan nesneler) yerine, nesneleri tutma çeşitli avantajlar sağlar.  
  
- **İşlem**. Bir dizi ilgili diğer değişiklikleri bir hareket halinde gruplayabilirsiniz.  
  
   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
   `{`  
  
   `// make several changes to Store elements here`  
  
   `t.Commit();`  
  
   `}`  
  
   Son Commit() yapılmaz, böylece değişiklik sırasında bir özel durum oluşursa, Store önceki durumuna sıfırlar. Bu, hataları modeli tutarsız bir durumda bırakmadığından emin olmak için yardımcı olur. Daha fazla bilgi için [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **İkili ilişkileri**. İki sınıf arasında bir ilişki tanımlarsanız, her iki End'i örnekleri diğer uçtaki ızgaranın bir özelliği vardır. İki ucu her zaman eşitlenir. Üst ve alt adlı rolleriyle parenthood ilişki tanımlarsanız, örneğin, şunu yazabilirsiniz:  
  
   `John.Children.Add(Mary)`  
  
   Her ikisi de aşağıdaki deyimleri artık doğrudur:  
  
   `John.Children.Contains(Mary)`  
  
   `Mary.Parents.Contains(John)`  
  
   Aynı etkiyi elde yazarak:  
  
   `Mary.Parents.Add(John)`  
  
   Daha fazla bilgi için [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Kuralları ve olayları**. Belirtilen değişiklikler yapıldığında yangın kuralları tanımlayabilirsiniz. Kuralları, örneğin, diyagramdaki şekilleri sundukları model öğeleriyle güncel tutmak için kullanılır. Daha fazla bilgi için [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).  
  
- **Serileştirme**. Store bir dosyayı içeren nesneleri serileştirmek için standart bir yolunu sunar. Serileştirme ve seri durumdan çıkarılırken kurallarını özelleştirebilirsiniz. Daha fazla bilgi için [özelleştirme dosya depolamayı ve XML serileştirmeyi](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)



