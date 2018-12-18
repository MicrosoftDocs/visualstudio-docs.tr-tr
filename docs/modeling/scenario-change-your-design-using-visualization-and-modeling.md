---
title: 'Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc8066148b2c8612b3a07922e15422022b8c9c4d
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967512"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Yazılım sisteminizin kullanarak Görselleştirme ve modelleme araçları Visual Studio tarafından Kullanıcıların ihtiyaçlarını karşıladığından emin olun.
Kod Haritaları, bağımlılık diyagramları ve sınıf diyagramları gibi araçları kullanın:

Her araç, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Kullanıcı gereksinimlerini ve iş süreçlerini açıklayın.

- Görselleştirin ve varolan kodu keşfedin.

- Varolan bir sistemde yapılan değişiklikleri açıklar.

- Sistem gereksinimleri karşıladığını doğrulayın.

- Kodun tasarımla tutarlılığını tutun.

Bu izlenecek yol:

- Bu araçların yazılım projenizi nasıl avantaj elde edebileceği açıklanmaktadır.

- Nasıl Bu araçlar bağımsız olarak geliştirme yaklaşımınızı içeren bir örnek senaryo kullanabileceğinizi gösterir.

Bu araçlar ve destekledikleri senaryolar hakkında daha fazla bilgi için bkz:

- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu senaryo, iki hayali şirketin yazılım geliştirme proje süreçlerinden açıklar: Şimdi Akşam Yemeği ve Lucerne Publishing. Şimdi Akşam Yemeği Seattle'da Web tabanlı bir yiyecek teslim hizmet sağlar. Müşteriler, yemek siparişi ve Şimdi Akşam Yemeği Web sitesinde bunlar için ödeme yaparsınız. Siparişler, ardından teslimi için üzere uygun yerel restoranlara gönderilir. Lucerne Publishing, New York, şirketinizin Web üzerinde ve dışında birçok müessese çalıştırır. Örneğin, müşterilerin restoran görüşlerini gönderebileceği bir Web sitesi çalıştırın.

Lucerne, kısa süre önce Dinner Now girişimini satın ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi Akşam Yemeği ne Restoran Eleştiri yeteneklerini ekleyerek Web sitelerini tümleştirin.

- Dinner Now ödeme sistemini Lucerne sistemiyle değiştirin.

- Şimdi Akşam Yemeği hizmetini bölge çapında genişletin.

Şimdi Akşam Yemeği SCRUM ve eXtreme Programming kullanır. Çok yüksek sınav kapsamı ve çok az desteklenmeyen kod sahiptirler. Bunlar küçük oluşturma ancak çalışan sürümlerini bir sistem ve ardından işlevsellik ekleyerek artımlı olarak riskleri en aza. Bunlar, kısa ve sık yinelemeler üzerinden kodu geliştirin. Bu bunları değişimi daha güvenle benimsemelerini, kodu sıkça yeniden düzenlemelerini ve "büyük tasarım" önlemenize olanak sağlar.

Lucerne, bazıları 40 yıldan eski olan sistemlerin çok büyük ve karmaşık bir koleksiyonunu tutar. Eski kod kapsamı ve karmaşıklık nedeniyle değişiklik yapma konusunda çok dikkatli değildirler. Bunlar, ayrıntılı çözümleri tasarlamayı ve tasarım ve geliştirme aşamasında oluşan değişiklikleri belgelemek için belgelemeyi daha titiz bir geliştirme işlemini izleyin.

Her iki ekip, kullanıcıların gereksinimlerini karşılayan sistemler geliştirmelerine yardımcı olmak için Visual Studio'da modelleme diyagramları kullanın. Bunlar Team Foundation Server diğer araçların yanı sıra bunları planlamak, düzenlemek ve işlerini yönetmek için kullanın.

Team Foundation Server hakkında daha fazla bilgi için bkz:

- [İş planlama ve izleme](#planning-and-tracking-work)

- [Sınama, doğrulama ve güncellenmiş kodu iade etme](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> Mimari ve modelleme diyagramları yazılım geliştirmede rolleri

Aşağıdaki tablo bu araçların yazılım geliştirme yaşam döngüsünün çoklu ve çeşitli aşamaları sırasında oynayabileceği roller açıklanmıştır:

||**Kullanıcı gereksinimlerini modelleme**|**İş Süreci Modelleme**|**Sistem Mimarisi ve tasarımı**|**Kodu görselleştirme ve keşfetme**|**Doğrulama**|
|------|-|-|-|-|-|
|Etki alanına özgü dil (DSL) diyagramı|Evet|Evet|Evet|||
|Bağımlılık diyagramı, katman doğrulama|||Evet|Evet|Evet|
|Kod Haritası|||Evet|Evet|Evet|
|Sınıf Tasarımcısı (kod tabanlı)||||Evet||

Bağımlılık diyagramları çizmek için varolan bir çözüm ya da yeni bir parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramları modelleme projesinin içinde oluşturulmalıdır.
Bağımlılık diyagramları üzerinde öğeler modelleme projesinin içinde bulunur, ancak ortak modelde saklanmaz. Kod haritaları ve .NET sınıf diyagramları koddan oluşturulan modelleme projesinin dışında yer alır.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Her iki ekip de geliştirme aşamasındaki kodun tasarım ile tutarlı kalmasından emin olmak için bağımlılık doğrulaması kullanın. Bkz.

- [Kodun tasarımla tutarlılığını koruma](#ValidatingCode)

- [Mantıksal mimarisi açıklanmıştır: bağımlılık diyagramları](#DescribeLayers)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Visual Studio'nun bazı sürümlerinin, Görselleştirme ve modelleme için bağımlılık doğrulama ve kod haritaları salt okunur sürümlerini destekler. Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Sistem hakkındaki bilgileri anlayıp

Modelleme diyagramlarını kendi gereksinimlerinize veya yaklaşımlarınıza uygun şekilde kullanabilmek için Visual Studio'yu kullandığınız için önceden belirlenmiş hiçbir sırası yok. Genellikle takımlar modellerini tekrarlayarak ve sık sık proje boyunca yeniden ziyaret edin. Her diyagram geliştirilmekte olan sistemin farklı yönlerini anlamanıza, tanımlamak ve yardımcı olan özel güçler sunar.

Şimdi Akşam Yemeği ve Lucerne diyagramları ortak dil olarak kullanarak birbiriyle ve proje hissedarlarıyla iletişim. Örneğin, bu görevleri gerçekleştirmek için Şimdi Akşam Yemeği diyagramlarını kullanır:

- Varolan kodu görselleştirin.

- Lucerne ile yeni veya güncellenmiş kullanıcı geçmişleri ile iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı öykülerini desteklemek üzere gerekli değişiklikleri tanımlayın.

Lucerne şu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi Akşam Yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Şimdi Akşam Yemeği ile yeni veya güncelleştirilmiş kullanıcı gereksinimleri ile iletişim kurun.

- Sistem güncelleştirmeleri belge.

Takımların planlama, yönetebilir ve işlerini daha kolay izlemek için diyagramlar Team Foundation Server ile tümleşiktir. Örneğin, bunlar modelleri test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmasını tahmin etmek için kullanın. Böylece ilerlemeyi izleyebilmek ve sistemin kullanıcı gereksinimlerini karşıladığından emin olun Lucerne bağlantılar Team Foundation Server iş öğelerini model öğelere. Tüm testler seçildiğinde kullanım testlerinin olduğunu görmek için örneğin, bunlar kullanım örnekleri test çalışması iş öğelerine bağlayın.

Ekipler yaptıkları değişiklikleri kaydetmeden önce bağımlılık doğrulaması ve otomatik testleri içeren yapıları çalıştırarak kodu testlere ve tasarıma karşı doğrulayın. Bu, güncelleştirilmiş kod değil tasarımıyla çakışma yaratmadığından ve daha önce çalışma işlevselliği sonu emin olun yardımcı olur.

### <a name="identify-changes-to-the-existing-system"></a>Varolan sistem değişikliklerini tanımlama

Şimdi Akşam Yemeği yeni gereksinimi Karşılama maliyetini tahmin etmek gerekir. Bu kısmen değişikliğin sistemin diğer bölümlerini etkileme derecesine bağlıdır. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri bu eşlemeleri ve diyagramları mevcut koddan oluşturur:

|**Harita veya diyagram**|**Gösterir**|
|-|-|
|*Kod Haritası*<br /><br /> Bkz.<br /><br /> - [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Gözat ve kod haritaları bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Bağımlılıklar ve diğer koddaki ilişkileri.<br /><br /> Örneğin, Şimdi Akşam Yemeği derlemeler ve bağımlılıklarına bir genel bakış için derleme kod haritaları gözden geçirilmesiyle başlayabilir. Ad alanlarını ve sınıfları bu derlemelerde bulunan keşfetmek için haritalarını halinde inebilir.<br /><br /> Şimdi Akşam Yemeği aynı zamanda belirli alanları ve diğer tür kod içindeki ilişkileri keşfetmek için maps oluşturabilirsiniz. Bunlar, bulmak ve onları ilgilendiren ilişkileri ve alanları seçmek için Çözüm Gezgini'ni kullanın.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Kod üzerinde varolan sınıflar|

 Örneğin, geliştirici bir kod Haritası oluşturur. Filiz kapsamını yeni senaryodan etkilenecek alanlara odaklanmak için ayarlar. Bu alanlar seçilir ve harita üzerinde vurgulanır:

 ![Namespace bağımlılık grafiği](../modeling/media/namespace_reviewsystem.png)

 **Namespace kod Haritası**

 Geliştirici, kendi sınıfları, yöntemleri ve ilişkileri görmek için seçilen ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep_reviewsystem.png)

 **Görünür gruplar arası bağlantılara sahip genişletilmiş ad alanı kod Haritası**

 Geliştirici etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Bunları, yeniden oluşturma yaptığınız gibi her değişikliğin etkilerini görmek için her bir değişiklikten sonra kod eşlemeleri. Bkz: [kodu görselleştirme](../modeling/visualize-code.md).

 Sistemin bileşenler veya etkileşimler gibi öbür parçalarına değişiklikleri açıklamak için takım bu öğeleri panolara çizebilir. Ayrıntılar yakalanan, yönetilen ve her iki takım tarafından anlaşılabilsin diye, bunlar aşağıdaki diyagramları Visual Studio'da çizebilir:

|**Diyagramları**|**Açıklar**|
|-|-|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Kod üzerinde varolan sınıflar.|

### <a name="ValidatingCode"></a> Kodun tasarımla tutarlılığını korumak
 Şimdi Akşam Yemeği güncelleştirilen kodun tasarım ile tutarlı kalmasını sağlayın. Bunlar sistemde işlevselliğe ilişkin katmanları açıklamak, bu katmanlara bunları ve ilişkilendirme çözüm yapılarına izin verilen bağımlılıkları belirtin bağımlılık diyagramları oluşturur.

|**Diyagramı**|**Açıklar**|
|-|-|
|*Bağımlılık diyagramı*<br /><br /> Bkz.<br /><br /> - [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Bir bağımlılık diyagram düzenler ve yapıtlar bir Visual Studio çözümünde adı verilen soyut gruplarla eşleştirir *katmanları*. Bu katmanlar, roller, görevlerin veya bu yapıların sistemde gerçekleştirdiği işlevleri tanımlayın.<br /><br /> Katman diyagramları, sistemin amaçlanan tasarımını açıklayan ve tasarımda gelişen kodu doğrulamak için kullanışlıdır.<br /><br /> Katmanlar oluşturmak için Çözüm Gezgini, kod Haritaları, sınıf görünümü ve Nesne Tarayıcısı'ndan öğeleri sürükleyin. Yeni Katmanlar çizmek için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayın.<br /><br /> Varolan bağımlılıkları görüntülemek için katman diyagramı yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**. Hedeflenen bağımlılıklarını belirtmek için yeni bağımlıklar çizin.|

 Örneğin, aşağıdaki bağımlılık diyagramı katmanlar ve her bir katman ile ilişkili yapıların sayısı arasındaki bağımlılıkları tanımlar:

 ![Tümleşik ödeme sistemi için bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Bağımlılık diyagramı**

Kod geliştirme sırasında tasarımla çakışmaların gerçekleşmez emin olmak için takımlar kullandığı bağımlılık doğrulaması yapılar Azure DevOps üzerinde çalışır. Bunlar ayrıca, iade etme işlemlerini bağımlılık doğrulaması gerektirmek için özel bir MSBuild görevi oluşturur. Bunlar doğrulama hatalarını toplamak için yapı raporları kullanır.

Bkz.

- [Görsel tasarımcıyı kullanmak](/azure/devops/pipelines/get-started-designer)

- [TFVC Geçitli iade](/azure/devops/pipelines/build/triggers#gated)

- [Derleme ve yayın görevleri](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Modelleri oluşturma ve kullanma için genel ipuçları

- Çoğu diyagram birbirine satırlarla bağlı düğümleri oluşur. Her diyagram türü için araç kutusu farklı türde düğümler ve satırlar sağlar.

     Araç kutusunu açmak için **görünümü** menüsünü tıklatın **araç kutusu**.

- Bir düğüm oluşturmak için araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri, varolan düğümlere sürüklenmelidir. Örneğin, bir bileşen diyagramı üzerinde varolan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir çizgi veya bir bağlantı oluşturmak için araç kutusunda uygun aracı tıklayın, kaynak düğümü tıklayın ve sonra hedef düğümü tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. Olası kaynak ya da hedef üzerinde işaretçiyi getirdiğinizde, işaretçi bir bağlantı oluşturup oluşturamayacağınızı gösterir.

### <a name="plan-and-track-work"></a>İşi planlayın ve izleyin

Planlama, yönetme ve çalışmayı daha kolay izlemek için visual Studio modelleme diyagramlarını Team Foundation Server ile tümleşiktir. Her iki ekip, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmasını tahmin etmek için modelleri kullanır. Lucerne oluşturur ve bağlantılar Team Foundation Server iş kullanım durumları veya bileşenleri gibi model öğelere öğeleri. Bu, ilerlemelerini izlemeye ve çalışmalarının izini kullanıcı gereksinimlerine izleme yardımcı olur. Bu değişiklikleri bu gereksinimleri karşılamaya devam ettiğinden emin olun yardımcı olur.

Çalışma ilerledikçe, kendi görevlere harcadıkları süreyi yansıtacak şekilde onların iş öğelerini takımlar güncelleştirme. Ayrıca izlemek ve rapor aşağıdaki Team Foundation Server özelliklerini kullanarak iş durumu:

- Günlük *ilerleme raporları* bunlar planlanmış çalışmaları beklenen süre tamamlayıp tamamlayamayacaklarını gösteren. Onlar, hata aşamalarını izlemek için Team Foundation Server'dan başka benzer raporlar oluşturur.

- Bir *yineleme çalışma* izlemek ve üyeleri arasındaki iş yükünü dengelemek takıma yardımcı olmak üzere Microsoft Excel kullanan. Bu çalışma sayfası Team Foundation Server'a bağlanır ve düzenli ilerleme toplantıları sırasında tartışma odağı sağlar.

- A *geliştirme Panosu* ekibi önemli proje bilgileri hakkında bilgilendirmek için Office Project kullanan.

Bkz.

- [Çevik araçları ve Çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/overview?view=vsts)

- [Grafikler, panolar ve pencere öğeleri (Azure DevOps Hizmetleri)](/azure/devops/report/dashboards/overview?view=vsts)

- [Tasks using Project ve biriktirme listesi oluşturma](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="TestValidateCheckInCode"></a> Kod içinde denetlediğinizde test ve doğrulama

Takımlar her bir görevi tamamladıkça, kaynak denetimine kodlarını ve unuturlarsa Team Foundation Server'dan anımsatıcılar alma. Takımlar, birim testleri ve bağımlılık doğrulama kodu kendi test çalışmalarına ve tasarıma karşı doğrulamak için Team Foundation Server kendi İadelerini kabul önce çalıştırın. Bunlar yapıları çalıştırmak için Team Foundation Server kullanmak otomatik birim testleri ve düzenli olarak bağımlılık doğrulama. Bu, kodun aşağıdaki ölçütleri karşıladığından emin olun yardımcı olur:

- Çalışır.

- Önceden çalışan kodu kesmez.

- Tasarım ile çakışmaz.

Şimdi Akşam Yemeği neredeyse tümü halen uygulanabilir olduğu için Lucerne bunları yeniden kullanabilir, otomatik testleri büyük koleksiyonu vardır. Lucerne Ayrıca bu testleri geliştirebilir ve yeni işlevsellikler yenilerini ekleyin. Hem de Visual Studio el ile testler çalıştırmak için kullanın.

Kodun tasarıma uymasını sağlamak için takımlar yapılarına DevOps bağımlılık doğrulama eklemek için Azure yapılandırın. Herhangi bir çakışma oluşursa, ayrıntılarla bir rapor oluşturulur.

Bkz.

- [Uygulamayı test etme](/azure/devops/test/overview?view=vsts)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimi kullanın](http://go.microsoft.com/fwlink/?LinkID=525605)

- [Azure işlem hatları](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Sistem Görselleştirme ve modelleme kullanarak güncelleştirme

Lucerne ve Dinner Now ödeme sistemleri bütünleştirilmelidir. Aşağıdaki bölümlerde, modelleme diyagramları Visual Studio'da bu görevi yerine getirmede yardımcı gösterilmektedir:

- [Varolan kodu görselleştirin: Kod haritaları](#VisualizeCode)

- [Bir türler sözlüğü tanımlayın: sınıf diyagramları](#DefineClasses)

- [Mantıksal mimarisi açıklanmıştır: bağımlılık diyagramları](#DescribeLayers)

Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="VisualizeCode"></a> Varolan kodu görselleştirin: Kod haritaları

Kod Haritaları, mevcut organizasyon ve ilişkileri kod içerisinde gösterir. Öğeleri tarafından temsil edilir *düğümleri* haritasında ve ilişkiler *bağlantıları*. Kod Haritaları, aşağıdaki türde görevleri gerçekleştirmenize yardımcı olabilir:

- Yabancı kodu keşfedin.

- Önerilen bir değişikliğin varolan kodu nerede ve nasıl etkilediğini anlayın.

- Alanları karmaşıklığı, doğal bağımlılıkları veya modelleri veya iyileştirmeden yararlanabilecek diğer alanları bulun.

Örneğin, Şimdi Akşam Yemeği PaymentProcessing bileşeninin maliyetini tahmin etmek gerekir. Bu kısmen değişikliğin sistemin diğer bölümlerini etkileme derecesine bağlıdır. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri koddan kod haritaları oluşturur ve odağını değişiklik tarafından etkilenebilecek alanlara ayarlar.

Aşağıdaki harita PaymentProcessing sınıfı ve seçili görünen Şimdi Akşam Yemeği sisteminin diğer bölümleri arasındaki bağımlılıkları gösterir:

![Şimdi Akşam Yemeği Ödeme sistemi için bağımlılık grafiği](../modeling/media/dep_dnpayment.png)

**Şimdi Akşam Yemeği Ödeme sistemi için kod Haritası**

Geliştirici PaymentProcessing sınıfını ve üyelerini etkilenme olasılığı bulunan alanları görmek için seçerek eşleme araştırır:

![PaymentProcessing ve bağımlılıkları içinde yer alan yöntemler](../modeling/media/depgraph_expandeddn.png)

**PaymentProcessing sınıfında ve bağımlılıkları içinde yer alan yöntemler**

Onlar sınıflarını, yöntemlerini ve bağımlılıklarını incelemek Lucerne Ödeme sistemi için aşağıdaki eşleme oluşturur. Takım, Lucerne sisteminin de Dinner Now sitesinin diğer bölümleriyle etkileşmek için işe gerek duyabileceğini görür:

![Lucerne Ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph_lucernepay.png)

**Lucerne Ödeme sistemi için kod Haritası**

Her iki ekip iki sistemi tümleştirmek için gereken değişiklikleri belirlemek için birlikte çalışır. Bazı kodları güncelleştirmek için daha kolay olacak şekilde yeniden düzenleyin karar. PaymentApprover sınıfı DinnerNow.Business ad alanına taşıyacak ve bazı yeni yöntemler gerektirecektir. İşlemleri işleyen Şimdi Akşam Yemeği sınıflarının kendi ad alanı olacaktır. Takımlar oluşturun ve planlamak, düzenlemek ve izlemek için çalışma öğelerini kullanın. Bunlar, çalışma öğelerini yararlı olacağı yerlerde model öğelere bağlar.

Kod yeniden düzenledikten sonra ekipler güncellenmiş yapıyı ve ilişkileri görmek için yeni bir kod Haritası oluşturun:

![Yeniden düzenlenen kodu içeren bağımlılık grafiği](../modeling/media/depgraph_integrated.png)

**Yeniden düzenlenen kodu içeren kod Haritası**

Bu harita, PaymentApprover sınıfının artık DinnerNow.Business ad alanında bulunduğunu ve bazı yeni yöntemler gösterilmektedir. Şimdi Akşam Yemeği işlem sınıflarının artık daha sonra kodla başa çıkmak kolaylaştıran kendi PaymentSystem ad var.

#### <a name="creating-a-code-map"></a>Bir kod Haritası oluşturma

- Kaynak koduna hızlı bir genel bakış için bir kod haritası oluşturmak için aşağıdaki adımları izleyin:

     Üzerinde **mimarisi** menüsünde tıklatın **için kod eşlemesi çözümünü oluşturmak**.

     Hızlı bir genel bakış derlenmiş kod, bir boş bir kod Haritası oluşturun ve ardından derleme dosyalarını veya ikili dosyaları eşleme yüzeyine sürükleyin.

- Özel kodu veya çözüm öğelerini araştırmak için öğeleri ve ilişkileri görselleştirmek istediğiniz seçmek için Çözüm Gezgini'ni kullanın. Ardından yeni bir harita oluşturur veya mevcut bir haritayı için seçili öğeleri Ekle. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).

- Harita keşfetmenize yardımcı olmak üzere düzenini gerçekleştirmek istediğiniz görevlerin türlerini uygun şekilde yeniden düzenleyin.

     Örneğin, kod üzerinde katman oluşturmayı görselleştirmek için bir ağaç düzeni seçin. Bkz: [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Özeti: Kod haritaları gücü
 Kod haritaları yardımcı:

- Mevcut koddaki ilişkileri ve kuruluş hakkında bilgi edinin.

- Önerilen bir değişiklik tarafından etkilenebilecek alanları tanımlayın.

- Alanlarını karmaşıklığı, desenleri, katmanları veya kod korumak, değiştirin ve yeniden kolaylaştırmak için geliştirebileceğimiz diğer alanları bulun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagramı**|**Açıklar**|
|-|-|
|Bağımlılık diyagramı|Sistemin mantıksal mimarisi. Bağımlılık doğrulama kodu tasarım ile tutarlı kalmasını sağlamak için kullanın.<br /><br /> Mevcut dependencys veya hedeflenen dependencys tanımlamanıza yardımcı olması için bir kod Haritası oluşturun ve ilişkili öğeleri gruplayın. Bir bağımlılık diyagramı oluşturmak için bkz:<br /><br /> - [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için kod üzerinde varolan sınıflar.<br /><br /> Görselleştirme ve kod içinde varolan bir sınıf değiştirmek için Sınıf Tasarımcısı'nı kullanın.<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DefineClasses"></a> Bir türler sözlüğü tanımlayın: sınıf diyagramları
 Sınıf diyagramları, varlıkları, koşulları veya sistem ve birbirleriyle olan ilişkilerine katılmak kavramları tanımlayın. Örneğin, öznitelikler ve işlemler için dil veya stil uygulamalarına bakılmaksızın, her sınıf tanımlamak için geliştirme sırasında bu diyagramları kullanabilirsiniz.

 İşlem Ödemesi kullanım örneğine katılan varlıkları tanımlamak ve Lucerne yardımcı olmak için bunlar aşağıdaki sınıf diyagramı çizmek:

 ![Sınıf diyagramında İşlem Ödemesi varlıkları](../modeling/media/uml_payentities.png)

 **Bir sınıf diyagramında İşlem Ödemesi varlıkları**

 Bu diyagram bir müşterinin birçok siparişi ve siparişler için farklı yollar olduğunu gösterir. BankAccount hem de CreditCard payment'tan devralır.

 Geliştirme sırasında Lucerne her sınıfın ayrıntılarını tartışmak ve açıklamak için aşağıdaki sınıf diyagramı kullanır:

 ![Bir sınıf diyagramında İşlem Ödemesi varlık ayrıntıları](../modeling/media/uml_payment.png)

 **Sınıf diyagramında İşlem Ödemesi bilgileri**

#### <a name="drawing-a-class-diagram"></a>Sınıf diyagramı çizme

Bir sınıf diyagramı aşağıdaki önemli özelliklere sahiptir:

- Sınıflar, arayüzler ve numaralandırma gibi türler:

    - A *sınıfı* belirli yapısal veya davranışsal özellikleri paylaşan nesnelerin tanımıdır.

    - Bir *arabirimi* bir parçası dışarıdan görünen bir nesne davranışını tanımlar.

    - Bir *numaralandırma* değişmez değerler listesini içeren bir sınıflandırıcıdır.

- *Öznitelikleri* her örneğini açıklayan belirli bir türdeki değerler bir *sınıflandırıcı*. Sınıflandırıcı türler, bileşenler, kullanım örnekleri ve hatta aktörler için genel bir addır.

- *İşlemleri* yöntemleri veya sınıflandırıcı örneklerinin gerçekleştiren işlevleri.

- Bir *ilişkilendirme* tür iki sınıflandırıcı arasındaki ilişkiyi gösterir.

  - Bir *toplama* sınıflandırıcılar arasındaki ortak mülkiyeti gösteren bir ilişkilendirmedir.

  - A *bileşim* bir sınıflandırıcılar arasındaki bütün parça ilişkisini gösteren bir ilişkilendirmedir.

    Toplamaları veya birleşimleri göstermek için **toplama** ilişkilendirme özelliği. **Paylaşılan** toplamaları gösterir ve **bileşik** bileşimleri gösterir.

- A *bağımlılık* bir sınıflandırıcı tanımını değiştirerek başka bir sınıflandırıcı tanımını değiştirebileceğini gösterir.

- A *Genelleştirme* belirli bir sınıflandırıcının kendi tanımının bir parçası genel bir sınıflandırıcı tanımından devraldığını gösterir. A *gerçekleştirme* bir sınıfın arabirim tarafından sunulan öznitelikleri ve işlemleri uyguladığını belirtir.

     Bu ilişkileri oluşturmak için kullanın **devralma** aracı. Alternatif olarak, bir gerçekleştirme olarak gösterilebilir bir *lollipop*.

- *Paketleri* sınıflandırıcılar, ilişkilendirmeler, yaşam çizgileri, bileşenler ve diğer paketleri gruplarıdır. *İçeri aktarma* ilişkileri gösteren bir paketin başka bir paketin bütün tanımlarını içerir.

Keşfedin ve var olan sınıfları tartışmak için başlangıç noktası olarak, koddan sınıf diyagramları oluşturmak için Sınıf Tasarımcısı'nı kullanabilirsiniz.

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: Sınıf Şemalarının Gücü
 Sınıf diyagramları, tanımlamanıza yardımcı olur:

- Kullanıcıların ihtiyaçları ve sisteme katılan varlıklar ele alınırken kullanılacak terimler, ortak bir sözlüğü. Bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

- Uygulamalarından bağımsız olarak bileşenler gibi sistemin parçaları tarafından kullanılan türler. Bkz: [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).

- Türler arası bağımlılıklar gibi ilişkiler. Örneğin, bir tür, başka türdeki birden çok örnek ile ilişkilendirilebilir gösterebilirsiniz.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagramı**|**Açıklama**|
|-|-|
|Bağımlılık diyagramı|Sınıflarla bağlantılı olarak sistemin mantıksal mimarisini tanımlayın.<br /><br /> Bağımlılık doğrulama kodu tasarım ile tutarlı kalmasını sağlamak için kullanın.<br /><br /> Bkz.<br /><br /> - [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Kod Haritası|Kuruluş ve mevcut koddaki ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için bu öğeleri gösteren bir kod Haritası oluşturun.<br /><br /> Bkz.<br /><br /> - [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a> Mantıksal mimarisi açıklanmıştır: bağımlılık diyagramları
 Bağımlılık diyagramları, çözümünüzdeki açıklamaları soyut gruplar düzenleyerek sistemin mantıksal mimarisini açıklar veya *katmanları*. Yapılar ad alanları, projeler, sınıflar, yöntemler vb. gibi birçok şey olabilir. Katmanlar, temsil ve rolleri veya yapıların sistemde gerçekleştirdiği görevleri tanımlayın. Katman doğrulama, derleme ve kodun tasarımıyla uyumlu kalmasını sağlamak için iade etme işlemleri de içerebilir.

 Kodun tasarımla tutarlılığını korumak için Şimdi Akşam Yemeği ve Lucerne aşağıdaki bağımlılık diyagram geliştikçe kodlarını doğrulamak için kullanın:

 ![Tümleşik ödeme sistemi için bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Şimdi Akşam Yemeği için bağımlılık diyagram Lucerne ile tümleştirilmiş**

 Bu Diyagramdaki katmanlar ilgili Şimdi Akşam Yemeği ve Lucerne çözüm yapılarına bağlar. Örneğin, iş katmanı bağlantılar DinnerNow.Business ad alanı ve üyeleri için artık PaymentApprover sınıfını içerir. Kaynak erişimi katmanı DinnerNow.Data ad bağlantıları. Oklar veya *bağımlılıkları*, sadece iş katmanının kaynak erişim katmanındaki işlevselliği kullanabileceğini belirtin. Takımlar kendi kodlarını güncellerken olarak katman doğrulama çakışmaları meydana gelirken yakalamak ve ekiplerin onları derhal çözmesine yardımcı olmak için düzenli olarak gerçekleştirilir.

 Takımlar, kademeli olarak birleştirmek ve iki sistem test etmek için birlikte çalışır. İlk önce PaymentProcessing uygulamasını ele PaymentApprover öğesinin ve Dinner Now öğesinin geri kalan birbiriyle başarıyla çalıştığından emin olun.

 Aşağıdaki kod haritası, Şimdi Akşam Yemeği ve PaymentApprover arasındaki yeni çağrıları gösterir:

 ![Tümleşik sistem içeren güncelleştirilmiş bir bağımlılık grafiği](../modeling/media/depgraph_intsystem.png)

 **Güncelleştirilmiş yöntem çağrılarını içeren kod Haritası**

 Sistem beklendiği gibi çalıştığını doğruladıktan sonra Şimdi Akşam Yemeği PaymentProcessing kodunu işaretler yorumlar. Katman doğrulama raporları temizdir ve ortaya çıkan kod Haritası başka PaymentProcessing bağımlılığının bulunmadığını gösterir:

 ![PaymentProcessing içermeyen bağımlılık grafiği](../modeling/media/depgraph_nomore.png)

 **PaymentProcessing içermeyen kod Haritası**

#### <a name="drawing-a-dependency-diagram"></a>Bir bağımlılık diyagramı çizme

Bir bağımlılık diyagramı aşağıdaki önemli özelliklere sahiptir:

- *Katmanlar* açıklamaların mantıksal gruplarını tanımlar açıklar.

- A *bağlantı* bir katman ve yapı arasındaki ilişkidir.

     Yapılardan katmanlar oluşturmak için Çözüm Gezgini, kod Haritaları, sınıf görünümü veya Nesne Tarayıcısı öğeleri sürükleyin. Yeni Katmanlar çizmek ve ardından bunları yapılara bağlamak için araç kutusunu kullanın veya katmanları oluşturmak üzere diyagram yüzeyine sağ tıklayın ve sonra öğeleri bu katmanlara sürüklemek.

     Bir katmandaki sayı katmana bağlı olan yapıların sayısını gösterir. Bu yapılar ad alanları, projeler, sınıflar, yöntemler vb. olabilir. Bir katmandaki yapı sayısını yorumladığınızda aşağıdakileri unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

       Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Bir katmana bağlı yapıların listesini görmek için bağımlılık sağ tıklayın ve ardından **bağlantıları görüntüle** açmak için **Katman Gezgini**.

- A *bağımlılık* bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ancak tersi doğru değildir. A *çift yönlü bağımlılık* bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ve bunun tersi de geçerlidir.

     Bağımlılık diyagramı üzerinde varolan bağımlılıkları görüntülemek için diyagram yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**. Hedeflenen bağımlılıklarını tanımlamak için yenilerini çizin.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Özet: Bağımlılık Şemalarının Gücü

Bağımlılık diyagramları yardımcı olur:

- Yapılarının işlevlerine göre bir sistemin mantıksal mimarisi açıklanmıştır.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uygun olduğundan emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagramı**|**Açıklama**|
|-|-|
|Kod Haritası|Kuruluş ve mevcut koddaki ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için kod haritası oluşturmak ve sonra harita üzerinde öğeleri olası Katmanlar olarak gruplayın. Grupları eşlemesinden bağımlılık diyagrama sürükleyin.<br /><br /> Bkz.<br /><br /> - [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Gözat ve kod haritaları bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Forumları**|- [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Çevik Yazılım geliştirmede modeller kullanma](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
