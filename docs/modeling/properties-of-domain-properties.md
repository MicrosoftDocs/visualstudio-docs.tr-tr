---
title: Etki Alanı Özelliklerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 431dad2f87fdd5857c91b39152d7f119945c0867
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966524"
---
# <a name="properties-of-domain-properties"></a>Etki Alanı Özelliklerinin Özellikleri
A *domain özelliği* değer tutan bir model öğesi olan bir özelliktir. Örneğin, `Person` etki alanı sınıfı özellikleri vardır `Name` ve `BirthDate`. DSL tanımındaki etki alanı özellikleri, etki alanı sınıfı kutusuna Diyagramı'nda ve etki alanı sınıfı, DSL Gezgini altında listelenir. Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
>  "Özelliği" sözcüğü iki kullanımı vardır. A *domain özelliği* üzerinde bir etki alanı sınıfı tanımlayan bir özelliktir. Bunun aksine, DSL'nin birçok öğe sahip *özellikleri*, bu makalenin **özellikleri** DSL tanımı penceresinde. Örneğin, her etki alanı özelliği, bu konuda açıklanan özellikler kümesi vardır.

 Çalışma zamanında, bir kullanıcı etki alanı sınıfı örneğini oluşturduğunda, etki alanı özelliklerinin değerlerini Özellikler penceresinde görülebilir ve diyagramdaki şekilleri görüntülenebilir.

 Çoğu etki alanı özellikleri sıradan CLR özellikleri olarak uygulanır. Ancak, bir programlama açısından bakıldığında, etki alanı özellikleri daha zengin işlevsellik sıradan program özellikleri vardır:

- Kurallar ve bir özelliğinin durumu izleme olayları tanımlayabilirsiniz. Daha fazla bilgi için [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).

- İşlem, özel olarak tutarsız durumları önlemeye yardımcı olur. Daha fazla bilgi için [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Bir diyagram veya DSL Gezgini'nde bir etki alanı özelliğini seçtiğinizde, aşağıdaki öğeleri Özellikler penceresinde görebilirsiniz. Bu öğelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan Değer|
|-|-|-|
|**Açıklama**|Belge oluşturulan tasarımcının kullanıcı arabirimi (UI) için kullanılan bir açıklaması.|\<yok >|
|**Görünen ad**|Bu etki alanı özellik için oluşturulan tasarımcıda görüntülenecek ad. Boşluk ve noktalama işaretleri, örneğin "şarkı Title" içerebilir.|\<yok >|
|**Öğe adı sağlayıcısı**|Bunun yalnızca belirlediğiniz geçerli `Is Element Name` için `true`. Varsayılan davranışı geçersiz kılma alan sınıfının yeni bir öğe için bir ad sağlar kod yazabilirsiniz.<br /><br /> DSL projesi içinde bir kod dosyasında, türetilen bir sınıf oluşturun <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Ardından DSL Gezgini DSL kök sağ tıklatın ve eklemek dış türüne tıklayın. Sınıfın adını girin.<br /><br /> Bu etki alanı özelliği yeniden seçin ve açılan listeden sınıfın adını seçin.|\<yok >|
|**Alıcı erişim değiştiricisi**|Etki alanı sınıfı, erişim düzeyi (`public` veya `internal`). Bu özelliği erişip hangi programda kod kapsamı denetler.|`public`|
|**Yardım anahtar sözcüğü**|Bu alan özelliği için F1 Yardımı dizini oluşturmak için kullanılan isteğe bağlı anahtar sözcük.|\<yok >|
|**Gözatılabilir olduğu**|Varsa `True`, bu DSL modelleri açıkken etki alanı özelliği kullanıcıya Özellikler penceresinde görüntülenir.<br /><br /> Varsa `False`, etki alanı özelliği kullanıcı Arabiriminde gizlenir.<br /><br /> Görünür ancak salt okunur etki alanı özelliği yapmak istiyorsanız, **kullanıcı Arabirimi salt okunur**.|`True`|
|**Öğe adı:**|Varsa `True`, bu etki alanı özelliği DSL Gezgini içinde model öğesinin adı olarak görüntülenir.<br /><br /> Yeni model öğeleri bu özellik için benzersiz bir varsayılan bir değer alır. Bu değerleri nasıl oluşturulacağını denetlemek istiyorsanız, **öğe adı sağlayıcısı**.|`False`|
|**Kullanıcı Arabirimi salt okunur**|Varsa `True`, kullanıcı arabirimini kullanarak etki alanı özelliğinin değeri değiştirilemez. Programlar tarafından hala ayarlanabilir ve Özellikler penceresinde görünür.<br /><br /> Kullanıcı etki alanı özelliği gizlemek istiyorsanız, ayarlama **olan gözatılabilir**. Programlar tarafından erişimi denetlemek istiyorsanız, **ayarlayıcı erişim değiştiricisi**.|`False`|
|**tür**|Etki alanı özelliğin türünü (`Normal`, `Calculated`, veya `CustomStorage`). Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Ad**|Bu etki alanı özelliğinin adı. Örneğin geçerli bir tanımlayıcı olmalıdır **SongTitle**.|\<yok >|
|**Notlar**|Bu etki alanı özelliği ile ilişkili resmi olmayan notlar.|\<yok >|
|**Ayarlayıcı erişim değiştiricisi**|Ayarlayıcının erişim değiştiricisini. Bu, hangi programda kod özelliği ayarlayabilirsiniz kapsamı denetler.|`public`|
|**Türü**|Özellik türü. Kullanılabilir türler listesine eklemek için DSL DSL Gezgini içinde kök sağ tıklayın ve tıklayın **dış türü Ekle**.|`String`|

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)