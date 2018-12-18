---
title: Uygulamanızı model&#39;s mimarisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 770f93c0ede93201ee873820d6701356837f4ea9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803857"
---
# <a name="model-your-app39s-architecture"></a>Uygulamanızı model&#39;s mimarisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin veya uygulama kullanıcılarınızın karşıladığından emin olmak için gereken, Visual Studio'da genel yapısı, açıklamasını ve yazılım sisteminin veya uygulamanın davranışını bir parçası olarak modeller oluşturabilirsiniz. Modelleri kullanarak tasarım boyunca kullanılan desenleri de tanımlayabilirsiniz. Bu modeller mevcut mimarisini anlama, değişiklikleri tartışmak ve amacınızı NET bir şekilde iletişim kurmasına yardımcı olur.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bir modelinin amacı, doğal dil açıklamasında ortaya belirsizlikleri azaltma ve iş arkadaşlarınızla tasarım görselleştirin ve Alternatif tasarımlar tartışmak için yardımcı olmak için ' dir. Bir model, diğer belgelerin ya da tartışmalar ile birlikte kullanılmalıdır. Tek başına bir model mimarinin eksiksiz bir belirtimi göstermiyor.  
  
> [!NOTE]
>  Bu konu başlığı altında yaptığımız, geliştirmekte olduğunuz yazılımı "Sistem" anlamına gelir. Büyük bir koleksiyonu, çok sayıda yazılım ve donanım bileşenleri, tek bir uygulama veya uygulamanın bir parçası olabilir.  
  
 Bir sistem mimarisi, iki alana ayrılabilir:  
  
-   [Üst düzey tasarım](#Structure). Bu, ana bileşenleri ve her gereksinimi karşılamak için birbiriyle nasıl etkileşim kurduklarını açıklar. Sistem büyükse, her bileşenin nasıl daha küçük bileşenlerden oluştuğunu gösteren kendi üst düzey tasarım olabilir.  
  
-   [Tasarım Düzenleri](#Patterns) ve bileşenleri tasarımları boyunca kullanılan kuralları. Bir programlama hedefini sağlamak için belirli bir yaklaşım bir deseni açıklar. Bir tasarım boyunca aynı desenleri kullanarak, takımınızın değişiklikleri yapma ve yeni yazılım geliştirme maliyetini azaltabilir.  
  
##  <a name="Structure"></a> Üst düzey tasarım  
 Üst düzey tasarım ana bileşenleri sisteminizi ve tasarım hedeflere ulaşmak için birbiriyle nasıl etkileşim kurduklarını açıklar. Etkinlikler, aşağıdaki listede, üst düzey tasarım, geliştirme mutlaka belirli bir sırada ancak faydalanırsınız.  
  
 Varolan kodu güncelleştirmekte olduğunuz, ana bileşenleri açıklayarak başlayabilir. Herhangi bir değişiklik kullanıcı gereksinimlerini anlamak ve eklediğinizde veya değiştirdiğinizde bileşenler arasındaki etkileşimleri emin olun. Yeni bir sistem geliştiriyorsanız ana özelliklerini Kullanıcıların ihtiyaçlarını anlayarak başlayın. Ardından etkileşim ana kullanım örnekleri için keşfetmek ve ardından bir bileşen tasarım dizileri birleştirin.  
  
 Her durumda, farklı etkinlikler paralel geliştirmeyi ve kod geliştirmelerine yardımcı olur ve erken bir aşamada test eder. Başka bir başlamadan önce bu yönlerinden tamamlanması çalışmaktan kaçının. Genellikle, yazma ve test ederken gereksinimleri hem Anlayışınızı sistemi tasarlamak için en iyi yolu değişir. Bu nedenle, anlama ve gereksinimleri ve tasarımınızı ana özelliklerini kodlama başlamalısınız. Projenin sonraki yinelemeler ayrıntıları doldurun.  
  
-   [Gereksinimleri anlama](#Requirements). Herhangi bir tasarım Kullanıcıların ihtiyaçlarını NET bir anlayış başlangıçtır.  
  
-   [Mimari desenleri](#BigDecisions). Çekirdek teknolojiler ve sistemin mimari öğeleri yaptığınız seçimleri.  
  
-   [Bileşenlerini ve bunların](#Components). Sistem başlıca parçaları göstermek için Bileşen diyagramları çizmek ve arabirimler üzerinden birbiriyle etkileşim kurduklarını gösterir. Her bileşenin arabirimleri sıralı diyagramlarında tanımladığınız tüm iletileri içerir.  
  
-   [Bileşenler arasındaki etkileşimler](#Interactions). Her kullanım örneği, olay veya gelen ileti için gerekli yanıtı elde etmek için sistemin ana bileşenlerini nasıl etkileşim kurduğu gösterilmektedir bir sıralı diyagram çizebilirsiniz.  
  
-   [Veri modeli bileşenleri ve arabirimleri](#Data). Bileşenleri arasında geçirilen ve bileşenler içinde depolanan bilgileri tanımlamak için sınıf diyagramlarını çizebilirsiniz.  
  
##  <a name="Requirements"></a> Gereksinimleri anlama  
 Tam bir uygulamayı üst düzey tasarımı, gereksinimler modelini veya diğer kullanıcıların ihtiyaçlarını açıklaması ile birlikte en etkili bir şekilde geliştirilmiştir. Gereksinim modelleri hakkında daha fazla bilgi için bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
 Geliştirmekte olduğunuz bir bileşen daha büyük bir sistemde sistemidir, kısmını veya tamamını gereksinimlerinizi program arayüzlerinde.  
  
 Bu temel bilgi parçasını gereksinimler modeli sağlar:  
  
- Sağlanan arabirimleri. İnsan kullanıcılara veya diğer yazılım bileşenleri olmalarından sağlanan arabirim Hizmetleri veya sistem veya bileşen, kullanıcılar için sağlaması gereken işlemleri listeler.  
  
- Gerekli arabirimleri. Gerekli arabirimi, hizmetleri veya sistem veya bileşen kullanabileceğiniz işlemleri listeler. Bazı durumlarda, bu hizmetlerin tümü kendi sisteminin bir parçası tasarlamak mümkün olacaktır. Diğer durumlarda, özellikle birçok yapılandırması içindeki diğer bileşenlere birlikte bir bileşeni tasarlıyorsanız gerekli arabirime dış etkenler tarafından ayarlanır.  
  
- Hizmet gereksinimlerinin kalitesini. Performans, güvenlik, sağlamlık ve diğer hedefler ve sistem karşılamalıdır kısıtlamaları.  
  
  Kişiler veya diğer yazılım bileşenleri olmalarından gereksinimler modelini açısından bakıldığında, sisteminizin kullanıcılarının yazılır. Hiçbir şey sisteminizi iç işleyişini bildirin. Aksine, amacınız bir mimari modelinde iç işleyişini açıklar ve kullanıcıların nasıl karşıladıklarından göstermek için gerekiyor.  
  
  Mimari modeller ve gereksinimleri ayrı tutmak kullanıcılarla gereksinimleri görüşmek üzere kolaylaştırır için yararlıdır. Ayrıca, tasarımı yeniden düzenleyin ve gereksinimleri değişmeden tutarken diğer mimarileri göz önünde bulundurun yardımcı olur.  
  
  Mimari modeller ve gereksinimleri iki farklı şekilde ayırabilirsiniz:  
  
- Bunları aynı çözüm içinde ancak farklı projelerde tutun. Ayrı modelleri UML Model Gezgini'nde olarak görünür. Farklı ekip üyeleri, modeller üzerinde paralel olarak çalışabilir. İzlemenin sınırlı türleri arasında modelleri oluşturulabilir.  
  
- Bunları aynı UML modeli, ancak farklı paketler yerleştirin. Bu modelleri arasındaki bağımlılıkları izlemenizi kolaylaştırır, ancak birden fazla kişi aynı anda model üzerinde çalışmasını engeller. Ayrıca, çok büyük bir modelin Visual Studio'ya yüklemek için daha uzun sürer. Bu yaklaşım bu nedenle büyük projeler için daha az uygundur.  
  
  Gereksinimler veya mimari bir model koymanız gerekir ayrıntı miktarını ölçek ve proje boyutu ve takım dağıtımı bağlıdır. Küçük bir takımda kısa bir projedeki başka bir sınıf diyagramı iş kavramlar ve bazı tasarım desenleri tasarlamaktan daha geçebilir; büyük bir projenin birden fazla bölge dağıtılmış önemli ölçüde daha fazla ayrıntı gerekir.  
  
##  <a name="BigDecisions"></a> Mimari desenleri  
 Geliştirme aşamasında bir ana teknolojileri ve tasarım bağlı olacağı öğeleri seçmeniz gerekir. Bu seçenek hale getirilmesi gereken alanları şunlardır:  
  
- Bir veritabanı ve dosya sistemi ve bir ağ uygulaması ve bir Web istemcisi arasında seçim arasında seçim yapma gibi teknoloji seçimleri temel vb. kullanın.  
  
- Windows Workflow Foundation ya da ADO.NET Entity Framework arasında seçim yapma gibi çerçeveleri seçenekleri.  
  
- Örneğin bir enterprise service bus veya noktadan noktaya kanal arasında tümleştirme yöntemi seçenekleri.  
  
  Bu seçimleri sık ölçeklendirme ve esneklik gibi hizmet gereksinimlerinin kalitesini tarafından belirlenir ve ayrıntılı gereksinimleri bilinen önce yapılabilir. Büyük bir sistemde, donanım ve yazılım yapılandırmasını kesin birbiriyle ilişkili.  
  
  Kullanımınızı ve mimari modelini yorumlamak, yaptığınız seçimleri etkiler. XML dosyalarını temel alan bir sistemde, XPath kullanan çapraz ilişkilendirmeleri gösterebilir ancak örneğin, bir veritabanını kullanan bir sistemde, bir sınıf diyagramı ilişkilendirmeler ilişkileri ya da bir veritabanındaki yabancı anahtarlar temsil edebilir. Dağıtılmış bir sistemde iletilerin sıralı diyagramda bir kablo iletileri temsil edebilir; kendi içinde bir uygulamada, işlev çağrıları temsil edebilir.  
  
##  <a name="Components"></a> Bileşenlerini ve bunların  
 Bu bölümde başlıca önerileri aşağıdaki gibidir:  
  
- Sisteminizin başlıca parçaları göstermek için Bileşen diyagramları oluşturun.  
  
- Bileşenler veya sisteminin yapısını göstermek üzere arabirimlerini arasında bağımlıklar çizin.  
  
- Arabirimleri, her bileşen sağlar veya gerektirir Hizmetleri göstermek için bileşene kullanın.  
  
- Büyük bir tasarım içinde her bileşenin daha küçük parçalara ayırmak için ayrı diyagramlar çizebilirsiniz.  
  
  Bu bölümün geri kalanında bu noktaları ayrıntılandırılmıştır.  
  
### <a name="components"></a>Bileşenler  
 Merkezi bir mimari modeli sistem ve birbirine nasıl bağlı olan başlıca parçaları Göster Bileşen diyagramları görünümleridir. Bileşen diyagramları hakkında daha fazla bilgi için bkz: [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md).  
  
 ![UML bileşen diyagramı bölümleri gösteren](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Büyük bir sistem için tipik bir bileşen diyagramı, bunlar gibi bileşenleri şunlar olabilir:  
  
-   Sunu. Genellikle bir Web tarayıcısında çalışan kullanıcı, erişim sağlayan bir bileşen.  
  
-   Web hizmeti bileşenleri. İstemciler ve sunucular arasında bağlantı sağlar.  
  
-   Kullanım örneği denetleyicileri. Kullanıcının her senaryonun adımlarını gerçekleştirin.  
  
-   İş çekirdek. Gereksinimler modeli sınıflarını temel alan sınıfları içeren, anahtar işlemleri gerçekleştirir ve iş kısıtlamalarını uygular.  
  
-   Veritabanı. İş nesnelerini depolar.  
  
-   Günlük kaydı ve hata işleme bileşenleri.  
  
### <a name="dependencies-between-components"></a>Bileşenler arasındaki bağımlılıklar  
 Bileşenleri kendilerini yanı sıra, aralarındaki bağımlılıkları gösterebilirsiniz. Bir tasarım değişiklikleri, diğer tasarım etkileyebilecek iki bileşen arasında bir bağımlılık okunun gösterir. Bu durum, genellikle bir Bileşen Hizmetleri veya doğrudan veya dolaylı olarak başka bir bileşen tarafından sağlanan işlevleri kullandığından gerçekleşir.  
  
 İyi yapılandırılmış bir mimari bağımlılıkları, bu koşullar doğru olduğunda açık bir yerleşimini sahiptir:  
  
- Kod haritasında döngü vardır.  
  
- Bileşenler, her bağımlılık bir katmandaki bir bileşenden alınan sonraki bir bileşen gider katmanlara düzenlenebilir. Her iki katman arasındaki tüm bağımlılıkları aynı yönde gidin.  
  
  Bileşenler arasındaki bağımlılıkları doğrudan gösterebilir veya gerekli ve sağlanan bileşenlere iliştirilmiş arabirimleri arasındaki bağımlılıkları gösterebilirsiniz. Arabirimler kullanarak hangi işlemleri her bir bağımlılığın içinde kullanılan tanımlayabilirsiniz. Genellikle, bağımlılıkları diyagramları çizilmiş önce ve sonra daha fazla bilgi eklendikçe arabirimleri arasındaki bağımlılıkları yerini bileşenleri arasında gösterilir. Her iki sürümü yazılım doğru açıklamalardır ancak arabirimleri sürümle önceki sürümden daha fazla ayrıntı sağlar.  
  
  Bağımlılık Yönetimi yazılım sürdürülebilir üretim için en önemli şey. Bileşen diyagramları, kodunuzdaki tüm bağımlılıkları yansıtmalıdır. Kodu zaten varsa, tüm bağımlılıkları diyagramlara gösterildiğinden emin olun. Kod geliştirilen, onu değil planlanan bağımlılıkları bileşen diyagramında içermediğinden emin olun. Bir koddaki bağımlılıkları keşfetmenize yardımcı olmak için katman diyagramları oluşturabilirsiniz. Planlanan bağımlılık kısıtlamaları karşılandığından emin olun yardımcı olmak için kodu katman diyagramlarına karşı doğrulayabilir. Daha fazla bilgi için [katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Arabirimler  
 Arabirimleri bileşenlerinizin üzerine yerleştirerek, ayırın ve her bir bileşen tarafından sağlanan işlemlerinin büyük grup adı. Örneğin, web tabanlı bir satış sistemine bileşenlerde bir arabirim üzerinden müşterilere mal satın alma, bir arabirim üzerinden tedarikçileri, katalog güncelleştirmesi ve sistem yönetilen aracılığıyla üçüncü arabirim olabilir.  
  
 Bir bileşenin sağlanan ve gerekli arabirimleri herhangi bir sayıda olabilir. Sağlanan arabirimleri bileşeni, diğer bileşenler için sağlar. hizmetleri gösterir. Gerekli arabirimlere Bileşen Hizmetleri içindeki diğer bileşenlere gösterir.  
  
 Tanımlarsanız hem de sağlanan ve bu teknikler kullanabilmesi için gerekli arabirimlere bu bileşeni düzgün bir şekilde tasarım geri kalanından ayrı yardımcı olur:  
  
- Bileşen çevreleyen bileşenler tarafından test bandı benzetimi yapılmış bir test bandı yerleştirin.  
  
- Bileşeniniz diğer bileşenleri bağımsız olarak geliştirin.  
  
- Farklı bileşenlere arabirimlerinden eşleyerek diğer bağlamlarda bileşeni yeniden.  
  
  Bir arabirimde işlemlerin listesini tanımlamak istediğiniz zaman bir UML sınıf diyagramında arabirimi başka bir görünümünü oluşturabilirsiniz. Bunu yapmak için arabirimi UML Model Gezgini'nde bulun ve bir sınıf diyagramına sürükleyin. Arabirimi işlemleri daha sonra ekleyebilirsiniz.  
  
  Bir bileşenin davranış çağrılabilir herhangi bir şekilde bir UML arabirimde bir işlemi temsil edebilir. Bir Web hizmeti isteği, bir sinyal veya başka bir tür ya da bir sıradan program işlev çağrısı etkileşimi temsil edebilir.  
  
  Eklemek için hangi işlemleri belirlemek için bileşenlerin birbirleriyle nasıl etkileşim göstermek için sıralı diyagramlar oluşturun. Bkz: [bileşenler arasındaki etkileşimler](#Interactions). Her biri bu sıralı diyagramlar oluşan etkileşimler farklı kullanım örneğini gösterir. Kullanım örnekleri keşfedin bu şekilde, kademeli olarak her bileşenin arabiriminde işlemler listesine ekleyebilirsiniz.  
  
### <a name="decomposing-a-component-into-parts"></a>Bir bileşeni parçalara ayırma  
 Her bileşen için önceki bölümlerde açıklanan yordamı uygulayabilirsiniz.  
  
 Her bir bileşen içinde alt bileşenlerinden parçaları olarak gösterebilirsiniz. Bir bölümü etkin bir türde bir sınıfı, ana bileşeninin bir özniteliğidir. Her parça bir bileşen olan kendi türü vardır. Bu bileşen bir diyagram üzerinde yerleştirebilir ve onun parçalarını gösterir. Daha fazla bilgi için [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).  
  
 Bu teknik tüm sisteme uygulamak kullanışlıdır. Tek bir bileşen olarak çizme ve ana bileşenlerini parçaları olarak göster. Bu arabirimler sisteminizin dış dünya ile açıkça belirlemenize yardımcı olur.  
  
 Tasarımınız bir bileşen için başka bir bileşen kullandığında, sık konusunda bir parçası olarak veya bir gerektirir arabirimi üzerinden erişmek için ayrı bir bileşen olarak göstermek vardır.  
  
 Parçalar, aşağıdaki durumlarda kullanın:  
  
- Tasarım ana bileşenin her zaman parçanın bileşen türü kullanmanız gerekir. Bu nedenle bölümünün tasarım ana bileşenin tasarıma tamsayı gereklidir.  
  
- Ana bileşen kendi hiçbir somut varlığını sahiptir. Örneğin, görünümleri ve Kullanıcı etkileşimlerine işleyen gerçek bileşenleri koleksiyonunu temsil eder bir sunu katmanı adlı kavramsal bir bileşen olabilir.  
  
  Bu gibi durumlarda gerekli arabirimleri aracılığıyla erişilen ayrı bileşenler kullanın:  
  
- Gerektiren bileşenin arabirimleri aracılığıyla çalışma zamanında sağlayan farklı bileşenleri eşleştirilmek.  
  
- Bir sağlayıcı değiştirileceği kolay şekilde tasarımdır.  
  
  Gerekli arabirimlerin parça kullanımı için genellikle tercih edilir. Elde edilen sistem tasarımı daha uzun sürebilir ancak daha esnektir. Bileşenlerini ayrı ayrı test etmek kolaydır. Bu, geliştirme planlarında daha az eşleşmeye izin verir.  
  
##  <a name="Interactions"></a> Bileşenler arasındaki etkileşimler  
 Bu bölümde başlıca önerileri aşağıdaki gibidir:  
  
- Sisteminizin kullanım örnekleri tanımlayın.  
  
- Her kullanım örneği için nasıl sisteminizi bileşenlerinin birbirleriyle ve kullanıcılar ile birlikte çalışarak gerekli sonuç elde göstermek için bir veya daha fazla diyagramlar çizin. Genellikle, sıralı diyagramlar veya etkinlik diyagramları şunlardır.  
  
- Arabirimleri, her bileşen tarafından alınan iletileri belirtmek için kullanın.  
  
- Arabirimlerdeki işlemlerin etkisini açıklar.  
  
- Parçalarının nasıl etkileştiğini gösteren her bileşen için yordamı yineleyin.  
  
  Örneğin, web tabanlı bir satış sistemine, gereksinimler modelini bir müşterinin satın bir kullanım durumu olarak tanımlayabilir. Etkileşimler müşteri sunu katmanındaki bileşenlerle olduğunu göstermek için ve etkileşimler ambarı ve hesap bileşenleri ile olduğunu göstermek için sıralı diyagram oluşturabilirsiniz.  
  
### <a name="identifying-the-initiating-events"></a>Başlatma olaylarını belirleme  
 Çoğu yazılım sistemleri tarafından çalışmanın, kolayca, farklı giriş veya olayları için verdiği yanıtlar tarafından da bölünebilir. Başlatma olayı, aşağıdaki olaylardan biri olabilir:  
  
-   Kullanım örneği ilk eylem. Gereksinimler modelinde, bir kullanım örneği bir adım veya bir eylem diyagramındaki bir eylem olarak görünebilir. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md) ve [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
-   Bir programlama arabirimi bir ileti. Geliştirmekte olduğunuz sistem daha büyük bir sistemde bir bileşeni ise, bir bileşenin arabirimleri işlem olarak açıklanmalıdır. Bkz: [bileşenlerini ve bunların](#Components).  
  
-   Sisteminizde veya saat gibi normal bir olay tarafından izlenmemesi belirli bir koşul.  
  
### <a name="describe-the-computations"></a>Hesaplamaları açıklayın  
 Bileşenler için ilk olay nasıl yanıt verdiğini göstermek için sıralı diyagramlar çizin.  
  
 Tipik bir sırayla bölümü alır her bileşen örneği için yaşam çizgisi çizin. Bazı durumlarda, her türden birden fazla örneği olabilir. Tek bir bileşeni olarak tüm sisteminizi açıklanan içerdiği her bir bölümü için bir yaşam çizgisi olmalıdır.  
  
 Daha fazla bilgi için [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Faaliyet diyagramları, bazı durumlarda da kullanışlıdır. Örneğin, sürekli bir veri akışı bileşenleriniz varsa, nesne akışı olarak tanımlayabilirsiniz. Bir karmaşık algoritma Bileşeniniz varsa, denetim akışı olarak tanımlayabilirsiniz. Bu bileşeni açıklamaları kullanarak her eylem, örneğin gerçekleştirir. Temizle yaptığınızdan emin olun. Daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>İşlemleri belirtin  
 Her bir bileşen tarafından gerçekleştirilen işlemleri diyagramlarda da gösterildiği bir sıralı diyagram veya eylemleri bir eylem diyagramındaki iletileri olarak ya da gösterilen.  
  
 Bu işlemler için her bileşeni için bir arada toplayın. Sağlanan Arabirim bileşende oluşturun ve işlemleri arabirimleri ekleyin. Genellikle ayrı arabirim istemci her tür için kullanılır. İşlemleri en kolay arabirimlerde eklenir **UML Model Gezgini**. Aynı şekilde, her bileşen işlemleri başka bir bileşenden toplayın ve bunları gerekli bileşene bağlı arabirimler yerleştirin.  
  
 Her işlemden sonra elde dikkat edilecek etkinlik veya sıralı diyagramları, yorum eklemek yararlıdır. Ayrıca, her bir işlemin etkisini yazabilirsiniz, **Yerel Sonkoşul** özelliği.  
  
###  <a name="Data"></a> Veri modeli bileşenleri ve arabirimleri  
 Parametreleri tanımlayın ve bileşen arabirimlerde her işlemin değerleri döndürür. Burada çağrılarını Web hizmeti istekleri gibi işlemleri temsil etmekte parametreleri, isteğin bir parçası gönderilen bu bilgilere bağlıdır. Bir işlemden döndürülen değerlerden burada parametrelerle kullanabileceğiniz **yönü** özelliğini **kullanıma**.  
  
 Her bir parametre ve dönüş değeri bir türü vardır. UML sınıf diyagramları kullanarak bu tür tanımlayabilirsiniz. Bu diyagramları uygulama ayrıntılarını temsil gerekmez. Örneğin, XML olarak aktarılan veriler tanımlamakta olduğunuz, herhangi bir türden XML düğümler arasında çapraz temsil etmek için bir ilişkilendirme kullanın ve düğümleri göstermek için sınıflarını kullanın.  
  
 Öznitelikler ve ilişkilendirmeler iş kısıtlamaları tanımlamak için açıklamaları kullanabilirsiniz. Örneğin, bir müşterinin siparişine tüm öğeleri aynı tedarikçiden gelmesi gerekir, bu katalog öğesi, tedarikçi arasında ve öğeleri sipariş ve ürün kataloğu öğeleri arasındaki ilişkileri başvuruya göre tanımlayabilirsiniz.  
  
##  <a name="Patterns"></a> Tasarım desenleri  
 Belirli bir yazılım, özellikle de sistemin farklı bölümlerinin yinelenen durumuyla tasarlamak nasıl bir özetini bir tasarım örüntüsüdür. Proje boyunca Tekdüzen bir yaklaşım benimseyerek, tasarım maliyetini azaltmak, kullanıcı arabiriminde tutarlılığı ve anlama ve kod değiştirme maliyetini azaltın.  
  
 Gözlemci gibi bazı genel tasarım desenleri, bilinen ve yaygın olarak uygulanabilir. Ayrıca, yalnızca projeniz için geçerli olan desenleri vardır. Örneğin, Web satış sistemine olacaktır kodunu çeşitli işlemleri bir müşterinin siparişine değişiklikler burada yapılır. Tüm bu işlemleri, siparişin durumunu doğru şekilde her aşamasında görüntülendiğinden emin olmak için veritabanını güncellemek için belirli bir protokol izlemelidir.  
  
 Yazılım mimarisi çalışmanın bir parçası olan desenleri olması gerektiğini belirlemek için tasarım uyguladık. Proje ilerledikçe, yeni desenler ve geliştirmeler var olan desenleri bulunacaktır genellikle devam eden bir görev olmasıdır. Böylece her biri, başlıca tasarım desenleri erken bir aşamada alıştırma geliştirme planı düzenlemek yararlıdır.  
  
 Çoğu tasarım desenleri kısmen framework kodunda. Belirli sınıfları ve veritabanı doğru bir şekilde işlendiğini sağlar bir veritabanı erişim katmanı gibi bileşenler kullanmak Geliştirici isteyerek deseni parçası azaltılabilir.  
  
 Bir tasarım deseni bir belgede açıklanan ve genellikle aşağıdaki bölümleri içerir:  
  
-   Adı.  
  
-   Komutun geçerli olduğu açıklaması. Hangi kriterleri, bir geliştirici bu düzeni uygularken yapmanız gerekir?  
  
-   Çözdüğü sorunun kısa bir açıklama.  
  
-   Başlıca parçaları ve aralarındaki ilişkiler modeli. Bunlar, sınıfları veya bileşenleri ve arabirimler, ilişkileri ve aralarındaki bağımlılıkları olabilir. Öğeleri genellikle iki kategoriye ayrılır:  
  
    -   Her desen kullanıldığı kod bölümünde Geliştirici çoğaltmalıdır öğeleri. Bunları açıklamak için şablon türleri kullanabilirsiniz. Daha fazla bilgi için [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md).  
  
    -   Geliştirici kullanması gereken framework sınıfları tanımlayan öğeler.  
  
-   Sıralı veya etkinlik diyagramları kullanarak parçalar arasındaki etkileşimler modeli.  
  
-   Adlandırma kuralları.  
  
-   Nasıl deseni sorunu çözdü açıklaması.  
  
-   Geliştiricilerin benimseyebileceği değişikliklerin çeşitlemeleri açıklaması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [Kodu görselleştirme](../modeling/visualize-code.md)   
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)   
 [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)



