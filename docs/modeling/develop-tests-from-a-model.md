---
title: Model aracılığıyla test geliştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e1fd3b1cd19efa9032b7b92576a489e3b17373db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919346"
---
# <a name="develop-tests-from-a-model"></a>Model aracılığıyla test geliştirme
Sisteminiz ve bileşenlerinin testleri düzenlemenize yardımcı olması için gereksinimleri ve mimari modelleri kullanabilirsiniz. Bu uygulama, kullanıcıların ve diğer proje katılımcıları için önemli olan gereksinimleri test etmek ve gereklilikler değiştiğinde testleri hızlı bir şekilde güncelleştirmenize yardımcı emin olun yardımcı olur. Kullanırsanız [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], modeller ve testler arasındaki bağlantıları da sağlayabilirsiniz.

 Visual Studio'nun hangi sürümlerinin bu özellikleri desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Sistem ve alt test etme
 *Sistem sınaması,* olarak da bilinen *kabul testi*, kullanıcıların gereksinimlerini karşılayıp karşılamadığını test anlamına gelir. Bu tür testler iç tasarımının yerine sistem dışarıdan görünen davranışını hakkında duyarlıdır.

 Sistem testleri genişletme veya bir sistem yeniden tasarlanmasını çok değerlidir. Bunlar, hata kodu değiştirdiğinizde oluşturmaktan kaçının yardımcı olur.

 Herhangi bir değişiklik veya bir sistem uzantısı planlarken, mevcut sistem üzerinde çalışan sistem testleri bir dizi başlatmak yararlıdır. Ardından genişletin veya yeni gereksinimleri test etmek, koda değişiklik ve test kümesinin tamamını yeniden çalıştırmak için testleri ayarlayın.

 Yeni bir sistem geliştirdiğinizde, geliştirme başlar başlamaz testleri oluşturmaya başlayabilirsiniz. Her bir özellik geliştirme önce testleri tanımlayarak belirli bir biçimde gereksinimleri tartışmalar yakalayabilirsiniz.

 Alt sistem testi sistemin ana bileşenleri için aynı ilkeler geçerlidir. Her bir bileşeni ayrı olarak başka bir bileşenden test edilir. Alt sistemi bileşenin kullanıcı arabirimleri veya API görünür davranışına odaklanmak sınar.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Sistem testleri gereksinimleri modelden türetme
 Oluşturun ve sistem testleri ve gereksinimler modeli arasında bir ilişki korumak. Bu ilişki kurmak için gereksinimler modelinin ana öğelere karşılık gelen testler yazın. Visual Studio testleri ve model bölümleri arasında bağlantılar oluşturmanıza imkan vererek bu ilişkiyi tutmanıza yardımcı olur. Gereksinim modelleri hakkında daha fazla bilgi için bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Her kullanım örneği için testleri yazma
 Kullanırsanız [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], gereksinimleri modelinizde tanımlı her kullanım örneği için testleri bir grup oluşturabilirsiniz. Örneğin, bir kullanım örneği oluştur ve sipariş Ekle öğesine içerir, yemek siparişi varsa her iki genel testler oluşturabilirsiniz ve bunların daha ayrıntılı kullanım örnekleri.

 Bu yönergeler yararlı olabilir:

-   Her kullanım örneği, ana yollar ve özel sonuçlar için çeşitli sınamalar olması gerekir.

-   Bir kullanım örneği gereksinimlerini modeli, açıklayan, diğer bir deyişle, daha ayrıntılı bir yordam tanımlamak için kullanıcı kaydetme amacına ulaşmanız için takip eden sağlanır, hedef kendi sonkoşulunu tanımlamak daha önemlidir. Örneğin, yemek siparişi Sonkoşul, olabilir bir restoran, bir müşterinin yemek hazırlanıyor ve müşteriye ödediği. Sonkoşul testlerinizi doğrulamalıdır ölçüttür.

-   Ayrı yan tümceleri Sonkoşul temel ayrı testler. Örneğin, restorana sipariş bilgilendirme ve müşterinin Ödeme almak için ayrı testler oluşturun. Bu ayrım bu avantajları vardır:

    -   Gereksinimleri farklı yönlerini değişiklikleri sık bağımsız olarak gerçekleşir. Bu şekilde farklı yönlere testleri ayırarak, testleri gereklilikler değiştiğinde güncelleştirmenin kolaylaştırır.

    -   Geliştirme planı önce başka bir kullanım örneği tek bir yönüne uygularsa, geliştirme ilerledikçe testleri ayrı ayrı etkinleştirebilirsiniz.

-   Testleri tasarlarken, test verileri seçimi sonkoşulun olup olmadığını belirten bir betik veya kod ayırın. Örneğin, bir basit aritmetik işlevinin bir test olabilir: Giriş 4; Çıkış 2 olduğundan emin olun. Bunun yerine, betiği şu şekilde tasarlayın: giriş; seçin Çıkış kendisi tarafından çarpma ve sonuç, özgün girişi olduğundan emin olun. Bu stil, testin ana gövdesini değiştirmeden test girdilerine değiştirmenizi sağlar.

#### <a name="linking-tests-to-use-cases"></a>Kullanım örnekleri için testleri bağlama
 Kullanıyorsanız [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] tasarlama ve testleri çalıştırmak için testlerinizin gereksinimi, kullanım durumu ve kullanıcı hikayesi iş öğeleri altında düzenleyebilirsiniz. Bu bağlantı iş öğeleri, modelinizde kullanım için. Bu hızlı bir şekilde izleme gereksinimleri değişiklikler testleri sağlar ve kullanım örneği her ilerlemesini izlemenize yardımcı olur.

###### <a name="to-link-tests-to-a-use-case"></a>Testleri bir kullanım örneğine bağlamak için

1. İçinde [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], bir gereksinim oluşturmanız ve bir test paketi üzerinde temel.

    Bir iş öğesinde oluşturduğunuz gereksinimi olan [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Team Foundation ile projenizin kullandığı işlem şablonuna bağlı olarak kullanıcı hikayesi, gereksinim veya kullanım örneği iş öğesi olabilir. Daha fazla bilgi için [hakkında Çevik araçları ve Çevik proje yönetimi](/azure/devops/boards/backlogs/overview?view=vsts).

2. Modelinizde bir veya daha fazla kullanım örnekleri için gereksinim iş öğesine bağlayın.

    Bir kullanım durumu diyagramı, kullanım örneğine sağ tıklayın ve ardından **iş öğesine bağlantı**.

3. Kullanım örnekleri doğrulama test çalışmaları, test paketine ekleyin.

   Genellikle, her kullanıcı hikayesi veya gereksinim çalışma öğesi, modelinizdeki çeşitli kullanım örnekleri için bağlantı içerir ve her kullanım örneği, birkaç kullanıcı hikayeleri veya gereksinimler bağlayacaksınız. Her kullanıcı öyküsü veya gereksinime çeşitli kullanım örnekleri geliştirme görevlerin kümesi sağlanmıştır olmasıdır. Örneğin, projenizin erken bir yineleme bir müşteri Kataloğu'ndan öğeleri seçin ve bunları teslim temel kullanıcı hikayesi geliştirebilir. Bir sonraki yinelemede hikayeyi malları gönderdikten sonra para sırasını ve tedarikçi Tamamlanıyor aldığında, kullanıcı öder olabilir.  Her hikayenin Sonkoşul sırasını ürün kullanım örneği için bir yan tümce ekler.

   Bu yan tümceleri ayrı açıklamalara kullanım durumu diyagramında yazarak Sonkoşul yan tümceyi gereksinimlerinden ayrı bağlantılar oluşturabilirsiniz. Her bir gereksinim iş öğesine bağlayın ve açıklama kullanım örneği diyagramındaki bağlayabilirsiniz.

### <a name="base-tests-on-the-requirements-types"></a>Gereksinim türleri temel testler
 Olan türler, sınıflar, arabirimler ve numaralandırmalar, gereksinimler modelini kavramlar ve kullanıcıların nasıl düşünün ve iş hakkında iletişim açısından ilişkiler açıklanmaktadır. Bu, sistemin yalnızca iç tasarımı ile ilgili türler hariç tutar.

 Bu gereksinim türleri açısından testlerinizi tasarlayın. Bu yöntem, değişiklikler gereksinimleri ele alınmıştır, bunun gerekli değişiklikleri testlerdeki değişiklikleri ilişkilendirilecek kolay olduğundan emin olun yardımcı olur. Testleri ve son kullanıcılar ve diğer proje katılımcıları ile doğrudan hedeflenen sonuçları tartışmanıza olanak sağlar. Bu, kullanıcıların geliştirme süreci dışında tutulabilir ve olası tasarım eksiklikler etrafında testleri yanlışlıkla tasarımını önler anlamına gelir.

 El ile testler için test betiklerdeki gereksinimleri modeli için bağlılığı bu yöntem içerir. Otomatik sınamalar için bu yöntem, gereksinimleri sınıf diyagramları, test kodunuz için bir temel olarak kullanarak ve erişimcisi ve güncelleştirici gereksinim modelini koda bağlamak için işlevleri oluşturmayı içerir.

 Örneğin, model içerebilir bir gereksinimleri menü, menü öğesi, sipariş ve onlar arasındaki ilişkileri türleri. Bu model, depolanır ve ile sistem sıralama yemek tarafından ele ancak uygulanması karmaşıklığını göstermiyor bilgileri temsil eder. Çalışma sisteminde birkaç farklı veritabanlarındaki kullanıcı arabirimleri ve API'leri her tür gerçekleştirimi olabilir. Dağıtılmış bir sistemde her örneğinin aynı anda sistemin farklı bölümlerinin depolanan birkaç çeşitleri olabilir.

 Bir kullanım örneği siparişi Ekle öğesine gibi test etmek için bir test yöntemi kodu şuna benzer şekilde ekleyebilirsiniz:

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Bu test yöntemi gereksinimleri modeli sınıflarını kullandığına dikkat edin. İlişkilendirmeleri ve öznitelikleri .NET özellikleri olarak gerçekleşir.

 Bunun çalışmasını sağlamak için sınıflarının özellikleri salt okunur işlevleri veya geçerli durumunda hakkında bilgi almak için sistem erişimi erişimcileri, olarak yeniden tanımlanması gerekir. Benzetimini yapan yöntemler kullanım örnekleri gibi AddItemToOrder sistem API'si aracılığıyla veya bir katmanı aracılığıyla kullanıcı arabirimi sürücüsü gerekir. Test nesnelerin sırasını ve MenuItem gibi Oluşturucular, da sistem içinde karşılık gelen öğeleri oluşturmak için sistem sürücüsü gerekir.

 Erişimciler ve güncelleyici çoğunu zaten uygulamanın normal API aracılığıyla kullanılabilir. Ancak, bazı ek işlevler testleri etkinleştirmek için yazılması gerekebilir. Bazen bu ek erişimci ve güncelleyici 'test Araçları' bilinir. Bunlar iç sistemin tasarımını üzerinde bağımlı olduğundan test edicilere test gereksinimler modelini açısından kod yazmaya ise bunları sağlamak için sistemin geliştiricilerin sorumluluğundadır.

 Otomatikleştirilmiş testleri yazdığınızda, erişimci ve güncelleyici kaydırmak için genel testler kullanabilirsiniz.

### <a name="tests-for-business-rules"></a>İş kuralları için testler
 Bazı gereksinimler herhangi bir kullanım durumu için doğrudan ilgili değildir. Örneğin, DinnerNow iş birçok menülerden seçme özgürlüğü tanır, ancak her sırada gerektiren tüm seçilen öğeleri tek bir menüden olacaktır. Bu iş kuralı, siparişler, menüler ve öğeler arasındaki ilişkilendirmeleri gereksinimleri sınıfı modelinde hakkında bir değişmez değer olarak ifade edilebilir.

 Bu tür sabit bir kuralı, yalnızca şu anda tanımlanmış tüm kullanım durumlarını ancak daha sonra yeniden tanımlanacak ayrıca diğer kullanım örneklerini yönetir. Bu nedenle, ayrı olarak herhangi bir kullanım örneğinden yazma ve kullanım örneklerinden ayrı olarak test etmek için yararlı olur.

## <a name="deriving-subsystem-tests-from-models"></a>Alt sistem testleri modellerinden türetme
 İçinde üst düzey tasarım büyük bir sistemin bileşenler veya alt sistemlerin tanımlayabilirsiniz. Bunlar, birçok bakımdan tasarlanabilen yeniden kullanılabilir modüller ayrı olarak tasarlanmış veya farklı bilgisayarlarda bulunan bölümleri temsil eder.

 Tam bir sistem için kullandığınız her ana bileşene aynı ilkeler uygulayabilirsiniz. Büyük bir projenin her bileşenin kendi gereksinimler modelini olabilir. Daha küçük projelerinde, ana bileşenleri ve bunların etkileşimleri göstermek için mimari model veya üst düzey tasarım oluşturulabilir. Daha fazla bilgi için [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).

 Her iki durumda da, gereksinimler modelini ve sistem testleri arasında olduğu gibi aynı şekilde model öğelerini ve alt sistem testleri arasında bir ilişki kurabilirsiniz.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Sağlanan ve gerekli arabirimleri bileşenleriyle Ayır
 Sistem veya dış hizmetlere diğer kısımlarına bir bileşeni olan tüm bağımlılıkları belirlemek ve gerekli arabirimleri olarak göstermek için kullanışlıdır. Bu alıştırmada genellikle bileşeni daha ayrılmış ve bir kolayca ayrılabilir tasarımınızı geri kalanından ayrılması bazı yöntemini yeniden tasarlamaya neden olur.

 Bu ayırma bir avantajı, genellikle hizmetler sahte nesneler ile değiştirerek test etmek için bileşen yürütülebilecek olmasıdır. Bu test etme amacıyla ayarlanan bileşenlerdir. Sahte bir bileşen benzetimli verilerle sorgulara yanıt bileşeniniz gerektirdiği için arabirim sağlar. Sahte bileşenleri, bileşenin tüm arabirimleri bağlanabilen bir tam test bandı bir parçasını oluşturur.

 Sahte test bileşeniniz kullanacağı olan hizmetleri hala geliştirilmektedir diğer bileşenleri sırasında geliştirebilirsiniz avantajdır.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Testleri ve Model arasındaki ilişkileri koru
 Birkaç haftada yineleme gerçekleştiren tipik bir projede, her yineleme başlangıcı yakınında gereksinimlerini gözden geçirme tutulur. Toplantı sonraki yinelemesine sağlanacak olan özellikler açıklanmaktadır. Gereksinimler modelini kavramları, senaryolar ve geliştirilecek Eylemler dizisi tartışmanıza yardımcı olmak için kullanılabilir. İş hissedarları öncelikleri ayarlar, geliştiriciler tahminler yapın ve test edicilere Beklenen davranış her özelliğin doğru şekilde yakalanan emin olun.

 Testleri yazma gereksinim tanımlamak için en etkili yoludur ve ayrıca bir kişi, gerekli olan açık bir anlama sahip olmamasını sağlamaya etkili bir yoludur. Yazma testleri zaman alırken bir belirtim Atölyesi sırasında çok uzun, ancak modelleri oluşturmak çok daha hızlı bir şekilde gerçekleştirebilirsiniz.

 Bir test açısından bakıldığında, gereksinimler modelini testler için bir toplu olarak görülebilir. Bu nedenle, testler ve proje boyunca model arasındaki ilişkiyi sağlamak önemlidir.

## <a name="Attaching"></a> Model öğelerine test çalışmalarını ekleme
 Projeniz kullanıyorsa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], testleri modelinizde öğelerine bağlayabilirsiniz. Bu değişikliği gereksinimleri etkilenen testleri hızla bulmanıza olanak tanır ve bir gereksinim gerçekleşti ölçüde izlemenize yardımcı olur.

 Tüm öğe türleri için testleri bağlayabilirsiniz. Bazı örnekler şunlardır:

-   Kullanım örneği, onu çalıştıran testlere bağlayın.

-   Yan tümceleri bir kullanım örneği sonkoşulunun veya hedef, kullanım örneğine bağlı yorumlar üzerine yazma ve testler her açıklama bağlayın.

-   Sınıf diyagramları veya etkinlik diyagramları açıklamalarda sabit kuralları yazma ve bunları testler bağlayabilirsiniz.

-   Testleri bir etkinlik diyagramı veya tek tek etkinliklerin bağlayın.

-   Bir test paketi bileşen veya alt test bağlayın.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Testleri bir model öğe veya ilişki bağlamak için

1. İçinde [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], bir gereksinim oluşturmanız ve bir test paketi üzerinde temel.

    Bir iş öğesinde oluşturduğunuz gereksinimi olan [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Team Foundation ile projenizin kullandığı işlem şablonuna bağlı olarak kullanıcı hikayesi, gereksinim veya kullanım örneği iş öğesi olabilir. Daha fazla bilgi için [hakkında Çevik araçları ve Çevik proje yönetimi](/azure/devops/boards/backlogs/overview?view=vsts).

2. Bir veya daha fazla öğe modelinizdeki gereksinim iş öğesine bağlayın.

    Modelleme diyagramında bir öğe, yorum veya ilişkiye sağ tıklayın ve ardından **iş öğesine bağlantı**.

3. Model öğe ifade gereksinim doğrulayın test çalışmalarını test paketine ekleyin.

## <a name="see-also"></a>Ayrıca Bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)
