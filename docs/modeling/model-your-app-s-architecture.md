---
title: Uygulamanızı model&#39;s mimarisi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7322738fe1bd17944bc5d1883bc9c16e56cc59e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855098"
---
# <a name="model-your-app39s-architecture"></a>Uygulamanızı model&#39;s mimarisi
Yazılım sisteminizin veya uygulama kullanıcılarınızın karşıladığından emin olmak için gereken, Visual Studio'da genel yapısı, açıklamasını ve yazılım sisteminin veya uygulamanın davranışını bir parçası olarak modeller oluşturabilirsiniz. Modelleri kullanarak tasarım boyunca kullanılan desenleri de tanımlayabilirsiniz. Bu modeller mevcut mimarisini anlama, değişiklikleri tartışmak ve amacınızı NET bir şekilde iletişim kurmasına yardımcı olur.

 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir modelinin amacı, doğal dil açıklamasında ortaya belirsizlikleri azaltma ve iş arkadaşlarınızla tasarım görselleştirin ve Alternatif tasarımlar tartışmak için yardımcı olmak için ' dir. Bir model, diğer belgelerin ya da tartışmalar ile birlikte kullanılmalıdır. Tek başına bir model mimarinin eksiksiz bir belirtimi göstermiyor.

> [!NOTE]
>  Bu konu başlığı altında yaptığımız, geliştirmekte olduğunuz yazılımı "Sistem" anlamına gelir. Büyük bir koleksiyonu, çok sayıda yazılım ve donanım bileşenleri, tek bir uygulama veya uygulamanın bir parçası olabilir.

 Bir sistem mimarisi, iki alana ayrılabilir:

-   [Üst düzey tasarım](#Structure). Bu, ana bileşenleri ve her gereksinimi karşılamak için birbiriyle nasıl etkileşim kurduklarını açıklar. Sistem büyükse, her bileşenin nasıl daha küçük bileşenlerden oluştuğunu gösteren kendi üst düzey tasarım olabilir.

-   [Tasarım Düzenleri](#Patterns) ve bileşenleri tasarımları boyunca kullanılan kuralları. Bir programlama hedefini sağlamak için belirli bir yaklaşım bir deseni açıklar. Bir tasarım boyunca aynı desenleri kullanarak, takımınızın değişiklikleri yapma ve yeni yazılım geliştirme maliyetini azaltabilir.

## <a name="Structure"></a> Üst düzey tasarım
 Üst düzey tasarım ana bileşenleri sisteminizi ve tasarım hedeflere ulaşmak için birbiriyle nasıl etkileşim kurduklarını açıklar. Etkinlikler, aşağıdaki listede, üst düzey tasarım, geliştirme mutlaka belirli bir sırada ancak faydalanırsınız.

 Varolan kodu güncelleştirmekte olduğunuz, ana bileşenleri açıklayarak başlayabilir. Herhangi bir değişiklik kullanıcı gereksinimlerini anlamak ve eklediğinizde veya değiştirdiğinizde bileşenler arasındaki etkileşimleri emin olun. Yeni bir sistem geliştiriyorsanız ana özelliklerini Kullanıcıların ihtiyaçlarını anlayarak başlayın. Ardından etkileşim ana kullanım örnekleri için keşfetmek ve ardından bir bileşen tasarım dizileri birleştirin.

 Her durumda, farklı etkinlikler paralel geliştirmeyi ve kod geliştirmelerine yardımcı olur ve erken bir aşamada test eder. Başka bir başlamadan önce bu yönlerinden tamamlanması çalışmaktan kaçının. Genellikle, yazma ve test ederken gereksinimleri hem Anlayışınızı sistemi tasarlamak için en iyi yolu değişir. Bu nedenle, anlama ve gereksinimleri ve tasarımınızı ana özelliklerini kodlama başlamalısınız. Projenin sonraki yinelemeler ayrıntıları doldurun.

-   [Gereksinimleri anlama](#Requirements). Herhangi bir tasarım Kullanıcıların ihtiyaçlarını NET bir anlayış başlangıçtır.

-   [Mimari desenleri](#BigDecisions). Çekirdek teknolojiler ve sistemin mimari öğeleri yaptığınız seçimleri.

-   Veri modeli bileşenleri ve arabirimleri. Bileşenleri arasında geçirilen ve bileşenler içinde depolanan bilgileri tanımlamak için sınıf diyagramlarını çizebilirsiniz.

## <a name="Requirements"></a> Gereksinimleri anlama
 Tam bir uygulamayı üst düzey tasarımı, gereksinimler modelini veya diğer kullanıcıların ihtiyaçlarını açıklaması ile birlikte en etkili bir şekilde geliştirilmiştir. Gereksinim modelleri hakkında daha fazla bilgi için bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

 Geliştirmekte olduğunuz bir bileşen daha büyük bir sistemde sistemidir, kısmını veya tamamını gereksinimlerinizi program arayüzlerinde.

 Bu temel bilgi parçasını gereksinimler modeli sağlar:

- Sağlanan arabirimleri. İnsan kullanıcılara veya diğer yazılım bileşenleri olmalarından sağlanan arabirim Hizmetleri veya sistem veya bileşen, kullanıcılar için sağlaması gereken işlemleri listeler.

- Gerekli arabirimleri. Gerekli arabirimi, hizmetleri veya sistem veya bileşen kullanabileceğiniz işlemleri listeler. Bazı durumlarda, bu hizmetlerin tümü kendi sisteminin bir parçası tasarlamak mümkün olacaktır. Diğer durumlarda, özellikle birçok yapılandırması içindeki diğer bileşenlere birlikte bir bileşeni tasarlıyorsanız gerekli arabirime dış etkenler tarafından ayarlanır.

- Hizmet gereksinimlerinin kalitesini. Performans, güvenlik, sağlamlık ve diğer hedefler ve sistem karşılamalıdır kısıtlamaları.

  Kişiler veya diğer yazılım bileşenleri olmalarından gereksinimler modelini açısından bakıldığında, sisteminizin kullanıcılarının yazılır. Hiçbir şey sisteminizi iç işleyişini bildirin. Aksine, amacınız bir mimari modelinde iç işleyişini açıklar ve kullanıcıların nasıl karşıladıklarından göstermek için gerekiyor.

  Mimari modeller ve gereksinimleri ayrı tutmak kullanıcılarla gereksinimleri görüşmek üzere kolaylaştırır için yararlıdır. Ayrıca, tasarımı yeniden düzenleyin ve gereksinimleri değişmeden tutarken diğer mimarileri göz önünde bulundurun yardımcı olur.

  Gereksinimler veya mimari bir model koymanız gerekir ayrıntı miktarını ölçek ve proje boyutu ve takım dağıtımı bağlıdır. Küçük bir takımda kısa bir projedeki başka bir sınıf diyagramı iş kavramlar ve bazı tasarım desenleri tasarlamaktan daha geçebilir; büyük bir projenin birden fazla bölge dağıtılmış önemli ölçüde daha fazla ayrıntı gerekir.

## <a name="BigDecisions"></a> Mimari desenleri
 Geliştirme aşamasında bir ana teknolojileri ve tasarım bağlı olacağı öğeleri seçmeniz gerekir. Bu seçenek hale getirilmesi gereken alanları şunlardır:

- Bir veritabanı ve dosya sistemi ve bir ağ uygulaması ve bir web istemcisi arasında seçim arasında seçim yapma gibi teknoloji seçimleri temel vb. kullanın.

- Windows Workflow Foundation ya da ADO.NET Entity Framework arasında seçim yapma gibi çerçeveleri seçenekleri.

- Örneğin bir enterprise service bus veya noktadan noktaya kanal arasında tümleştirme yöntemi seçenekleri.

  Bu seçimleri sık ölçeklendirme ve esneklik gibi hizmet gereksinimlerinin kalitesini tarafından belirlenir ve ayrıntılı gereksinimleri bilinen önce yapılabilir. Büyük bir sistemde, donanım ve yazılım yapılandırmasını kesin birbiriyle ilişkili.

  Kullanımınızı ve mimari modelini yorumlamak, yaptığınız seçimleri etkiler. XML dosyalarını temel alan bir sistemde, XPath kullanan çapraz ilişkilendirmeleri gösterebilir ancak örneğin, bir veritabanını kullanan bir sistemde, bir sınıf diyagramı ilişkilendirmeler ilişkileri ya da bir veritabanındaki yabancı anahtarlar temsil edebilir. Dağıtılmış bir sistemde iletilerin sıralı diyagramda bir kablo iletileri temsil edebilir; kendi içinde bir uygulamada, işlev çağrıları temsil edebilir.

## <a name="Patterns"></a> Tasarım desenleri
 Belirli bir yazılım, özellikle de sistemin farklı bölümlerinin yinelenen durumuyla tasarlamak nasıl bir özetini bir tasarım örüntüsüdür. Proje boyunca Tekdüzen bir yaklaşım benimseyerek, tasarım maliyetini azaltmak, kullanıcı arabiriminde tutarlılığı ve anlama ve kod değiştirme maliyetini azaltın.

 Gözlemci gibi bazı genel tasarım desenleri, bilinen ve yaygın olarak uygulanabilir. Ayrıca, yalnızca projeniz için geçerli olan desenleri vardır. Örneğin, web satış sistemine olacaktır kodunu çeşitli işlemleri bir müşterinin siparişine değişiklikler burada yapılır. Tüm bu işlemleri, siparişin durumunu doğru şekilde her aşamasında görüntülendiğinden emin olmak için veritabanını güncellemek için belirli bir protokol izlemelidir.

 Yazılım mimarisi çalışmanın bir parçası olan desenleri olması gerektiğini belirlemek için tasarım uyguladık. Proje ilerledikçe, yeni desenler ve geliştirmeler var olan desenleri bulunacaktır genellikle devam eden bir görev olmasıdır. Böylece her biri, başlıca tasarım desenleri erken bir aşamada alıştırma geliştirme planı düzenlemek yararlıdır.

 Çoğu tasarım desenleri kısmen framework kodunda. Belirli sınıfları ve veritabanı doğru bir şekilde işlendiğini sağlar bir veritabanı erişim katmanı gibi bileşenler kullanmak Geliştirici isteyerek deseni parçası azaltılabilir.

 Bir tasarım deseni bir belgede açıklanan ve genellikle aşağıdaki bölümleri içerir:

-   Adı.

-   Komutun geçerli olduğu açıklaması. Hangi kriterleri, bir geliştirici bu düzeni uygularken yapmanız gerekir?

-   Çözdüğü sorunun kısa bir açıklama.

-   Başlıca parçaları ve aralarındaki ilişkiler modeli. Bunlar, sınıfları veya bileşenleri ve arabirimler, ilişkileri ve aralarındaki bağımlılıkları olabilir. Öğeleri genellikle iki kategoriye ayrılır:

-   Adlandırma kuralları.

-   Nasıl deseni sorunu çözdü açıklaması.

-   Geliştiricilerin benimseyebileceği değişikliklerin çeşitlemeleri açıklaması.

## <a name="see-also"></a>Ayrıca Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)