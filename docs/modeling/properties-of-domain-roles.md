---
title: Etki Alanı Rollerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b3078fdc54a5efa652d9de737559365cca7f58a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927092"
---
# <a name="properties-of-domain-roles"></a>Etki Alanı Rollerinin Özellikleri
Özellikler aşağıdaki tabloda, bir etki alanı rolüyle ilişkilidir. Etki alanı rolleri hakkında daha fazla bilgi için bkz. [anlama modelleri, sınıfları ve ilişkileri](../modeling/understanding-models-classes-and-relationships.md). Bu özellikler kullanma hakkında daha fazla bilgi için bkz. [bir etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Koleksiyon türü|Bu rolün çokluğu 0 varsa.. * veya 1.. \*, bu özellik bağlantıları koleksiyonunu depolamak için kullanılan genel tür özelleştirir.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> kullanılır|
|Özel Öznitelikler|Burada belirttiğiniz öznitelikleri için kod sınıfı öznitelikler eklenir.|< yok\>|
|Özellik gözatılabilir mi|Varsa `True`, ve kullanıcı tarafından ilişki çokluğu 0.. 1 veya 1..1 ise, rolü özelliği gözatılabilir **özellikleri** penceresi. Özelliği, ilişki bağlantısı diğer sonunda öğenin adını görüntüler.|`True`|
|Özellik Oluşturucusu|Varsa `True`, program kodu içinde ilişkide geçirmek için kullanabileceğiniz bu rol için bir rol özelliği oluşturulur. Bu yanlış ayarlarsanız, etki alanı ilişkisi statik yöntemleri kullanılarak ilişki daha az verimli bir şekilde geçiş yapabilirsiniz.|`True`|
|Özellik alıcısı erişim değiştiricisi|İçin oluşturulan özelliğe ait alıcının erişim değiştiricisini (`public`, `internal`, `private`, `protected`, veya `protected internal`).|`public`|
|Özellik ayarlayıcı erişim değiştiricisi|Oluşturulan özellik için ayarlayıcının erişim değiştiricisini (`public`, `internal`, `private`, `protected`, veya `protected internal`).|`public`|
|Çokluk|Karşı rol oynayabilir model öğelerinin sayısı (`0..1`, `1..1`, `0..*`, veya `1..*`). Çokluğu ise `0..*` veya `1..*`, ardından oluşturulan özellik bir koleksiyonu temsil eder; Aksi takdirde, oluşturulan özellik bir tek bir model öğesini temsil eder.|İlişki türüne göre değişir ve bu ilişkiyi kaynak veya hedef rolde olup olmadığını.|
|Ad|Etki alanı rolü adı. Bu özellik, boşluk içeremez.|Bu rol için etki alanı rol oyuncusu sınıfının adı.|
|Kopyalama yayar|`DoNotPropagateCopy` -Kopyalanan rol oyuncusu, bu bağlantı herhangi bir kopyasına sahip olacaktır.<br /><br /> `PropagateCopyToLinkOnly` -Rol oyuncusu varolan kopyalanmış bağlantı noktaları.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Kopyalanan bağlantıyı karşı rol oyuncusuna bir kopyasına işaret eder.|`PropagateCopyToLinkAndOppositeRolePlayer` katıştırılmış kaynak rolleri için.<br /><br /> `DoNotPropagateCopy` diğer roller için.<br /><br /> Daha fazla bilgi için [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)|
|Delete yayar|`True` ilişkili bağlantı silindiğinde, bu rol oynayan öğe silinemedi.|`True` bir gömme rol hedefi için.<br /><br /> `False` diğer roller için.<br /><br /> Daha fazla bilgi için [silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md).|
|Özellik adı|Rol oyuncusu kodda oluşturulan özelliğin adı. Bu ad, boşluk içeremez.|Bu rol bir sıfır bir varsa karşı rolün adını veya bire bir çoğulluk; Aksi halde, ters rolün pluralized adı.|
|Rol oyuncusu|İlişkide bu rolü oynayabileceği öğenin etki alanı sınıfı. Bu özellik salt okunurdur.|Bu rol için rol oyuncusu için etki alanı sınıfı.|
|Notlar|Etki alanı rolle ilişkili resmi olmayan notlar.|< yok\>|
|Kategori|Altında oluşturulan özellik görünür kategori **özellikleri** oluşturulan tasarımcıda penceresi. Bu özellik boştur sonra altında oluşturulan özellik görünür **çeşitli** kategorisi|< yok\>|
|Açıklama|Kod belge için kullanılır ve oluşturulan tasarımcının kullanıcı Arabiriminde kullanılan açıklaması.<br /><br /> Rol oyuncusu sınıfı üzerinde oluşturulan özellik için IntelliSense araç ipucu açıklaması görünür.|`Description for` *rolün tam adı*|
|Görünen ad|Etki alanı rolü için oluşturulan tasarımcıda görüntülenecek ad.|Name özelliği ayarlanmış değeri.|
|Yardım anahtar sözcüğü|Etki alanı rolü için F1 Yardımı dizini oluşturmak için kullanılan isteğe bağlı anahtar sözcük.|\<yok >|
|Özellik görünen adı|Oluşturulan rol özellik için oluşturulan tasarımcıda görüntülenecek ad.|Özellik adı özelliği ayarlanmış değeri.|

> [!NOTE]
> Varsayılan değer olan bir görünen ad, her büyük harf karakter, bir küçük harf karakteriyle öncesinde ve başka bir büyük harf karakteri tarafından izlenmeyen önce boşluk ekleyerek ilişkili özelliğin değere göre belirlenir.

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md)