---
title: Üretilen Sınıfları Geçersiz Kılma ve Genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ff9a548a675451b28d9b08db280dd3b35cf0a53c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511111"
---
# <a name="override-and-extend-the-generated-classes"></a>Geçersiz kılma ve genişletme oluşturulan sınıflar

DSL tanımınızı güçlü bir etki alanına özgü dil tabanlı araçlar kümesi oluşturabileceğiniz bir platformdur. Birçok uzantıları ve uyarlaması, geçersiz kılma ve genişletme DSL tanımını oluşturan sınıfları tarafından yapılabilir. Bu sınıflar yalnızca DSL tanım diyagramı içinde açıkça tanımlanmış alan sınıfları, aynı zamanda tanımlayan araç kutusu, Gezgini, seri hale getirme ve benzeri diğer sınıflar içerir.

## <a name="extensibility-mechanisms"></a>Genişletilebilirlik mekanizması

Çeşitli mekanizmalar oluşturulan kodu genişletme olanak sağlanır.

### <a name="override-methods-in-a-partial-class"></a>Kısmi sınıftaki yöntemleri geçersiz kılın

Kısmi sınıf tanımları, birden fazla yerde tanımlanmış bir sınıf sağlar. Bu, kendi yazdığınız koddan oluşturulan kodu ayırmanızı sağlar. El ile yazılan kodunuzda tarafından oluşturulan kodun devralınan sınıflar geçersiz kılabilirsiniz.

Örneğin, adında bir etki alanı sınıfı, DSL tanımındaki tanımladığınız `Book`, geçersiz kılma yöntemleri ekleyen özel kod yazabilirsiniz:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Oluşturulan bir sınıftaki yöntemleri geçersiz kılmak için her zaman oluşturulan dosyalardan ayrılmış bir dosya içinde kodunuzu yazın. Genellikle, dosya, CustomCode adlı bir klasörde yer alır. Oluşturulan kod için değişiklik yaparsanız, DSL tanımını koddan yeniden oluştururken bunlar kaybolur.

Geçersiz kılma yöntemleri bulmak için yazın **geçersiz kılma** sınıfında, ardından bir boşluk. IntelliSense araç ipucu yöntemleri geçersiz kılınabilir bildirir.

### <a name="double-derived-classes"></a>Çift türetilmiş sınıfları

Üretilen sınıfları yöntemleri çoğunu modelleme ad alanlarındaki sınıfları kümesinden devralınır. Ancak, bazı yöntemler oluşturulan kodda tanımlanır. Bu normalde bunları kılamazsınız anlamına gelir; Aynı sınıfın başka bir kısmi tanım içinde tanımlanan yöntem kısmi bir sınıf tarafından geçersiz kılınamaz.

Bununla birlikte, ayarlayarak bu yöntemleri geçersiz kılabilirsiniz **Generates Double Derived** etki alanı sınıfı bayrağı. Bu neden iki sınıf oluşturulacak, diğer Özet temel sınıf olan bir. Tüm yöntem ve özellik tanımları temel sınıf ve türetilen sınıfta yalnızca Oluşturucu olduğundan.

Örneğin, örnekte Library.dsl, `CirculationBook` etki alanı sınıfında `Generates``Double Derived` özelliğini `true`. Bu etki alanı sınıfı için oluşturulan kod, iki sınıf içerir:

-   `CirculationBookBase`, bir soyut olduğu ve tüm yöntemleri ve özellikleri içerir.

-   `CirculationBook`, türetilen `CirculationBookBase`. Kendi oluşturucular dışında boş.

Herhangi bir yöntemi geçersiz kılmak için kısmi türetilmiş bir sınıf tanımlaması gibi oluşturduğunuz `CirculationBook`. Hem oluşturulan ve modelleme framework devralınan yöntemleri geçersiz kılabilirsiniz.

Öğe, model öğelerini, ilişkileri, şekiller, Diyagram ve bağlayıcılar dahil olmak üzere tüm türleri bu yöntemi kullanabilirsiniz. Ayrıca, oluşturulan diğer sınıfların yöntemleri geçersiz kılabilirsiniz. Bazı, ToolboxHelper gibi her zaman çift türetilmiş sınıfları oluşturulur.

### <a name="custom-constructors"></a>Özel oluşturucular

Bir oluşturucu geçersiz kılamaz. Bile çift türetilmiş sınıflarda, türetilmiş bir sınıf içindeki Oluşturucu olması gerekir.

Kendi Oluşturucu sağlamak istiyorsanız, bunu ayarlayarak yapabilirsiniz `Has Custom Constructor` DSL tanımındaki alan sınıfına yönelik. Tıkladığınızda **tüm Şablonları Dönüştür**, oluşturulan kodun o sınıf için bir oluşturucu dahil edilmez. Bu eksik oluşturucusuna bir çağrı içerir. Çözümü derleyin, bu bir hata raporu neden olur. Bir açıklama sağlamanız gerekir açıklayan oluşturulan kodu görmek için hata raporuna çift tıklayın.

Oluşturulan dosyalardan ayrı bir dosyada bir kısmi sınıf tanımı yazabilir ve oluşturucu sağlayın.

### <a name="flagged-extension-points"></a>Bayrak eklenen uzantı noktaları

Bayrak eklenen genişletme noktası, bir özellik veya özel bir yöntem sağlayacak belirtmek için bir onay kutusu ayarlayabildiğiniz DSL tanımındaki bir yerdir. Özel oluşturucular bir örnektir. Diğer örnekler ayarı `Kind` hesaplanan veya özel depolama veya ayarı için bir etki alanı özelliğinin **olan özel** bayrağı bir bağlantı Oluşturucu.

Bayrağını ayarlayın ve kod yeniden her durumda, bir yapı hatasına neden olur. Sağlamanız gereken anlatan bir açıklama görmek için hataya çift tıklayın.

### <a name="rules"></a>Kurallar

İşlem Yöneticisi, bir işlem içinde belirtilen bir olay, bir özelliği bir değişiklik gibi oluştu bitmeden önce çalışan kuralları tanımlamanızı sağlar. Kurallar, genellikle depolama farklı öğeler arasındaki synchronism korumak için kullanılır. Örneğin, kuralları, diyagram modelin geçerli durumu görüntüler emin olmak için kullanılır.

Sınıf başına temelinde kuralları tanımlanır, böylece kodu olması gerekmez, kural her nesne için kaydeder. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Store olayları

Model Deposu ekleme ve silme işlemlerini öğelerin özellik değerleri, değişiklikler de dahil olmak üzere deposunda değişiklik belirli türlerdeki dinlemek için kullanın ve benzeri bir olay mekanizması sağlar. Olay işleyicileri içinde değişiklik yapılan işlem kapatma sonra çağrılır. Genellikle, bu olaylar, mağaza dışındaki kaynaklar güncelleştirmek için kullanılır.

### <a name="net-events"></a>.NET olayları

Bazı olaylar şekilleri için abone olabilirsiniz. Örneğin, bir şekli üzerinde fare tıklamasıyla dinleyebilirsiniz. Her nesne için bir olaya abone kod yazmak zorunda. Bu kod InitializeInstanceResources() bir geçersiz kılma yazılabilir.

Bazı olaylar şekli dekoratörler çizmek için kullanılan ShapeFields üzerinde oluşturulur. Bir örnek için bkz. [nasıl yapılır: Şekil veya Dekoratörde bir Click için araya girme](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Bu olaylar, genellikle bir işlem içinde gerçekleşmez. Depoda değişiklik yapmak istiyorsanız, bir işlem oluşturmanız gerekir.