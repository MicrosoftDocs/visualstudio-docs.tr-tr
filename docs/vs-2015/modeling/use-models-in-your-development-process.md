---
title: Geliştirme sürecinizde modelleri kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 56534483f8b9cda99b756524d87408efbedfe275
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757698"
---
# <a name="use-models-in-your-development-process"></a>Geliştirme sürecinizde modelleri kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da anlamanıza ve sistem, uygulama veya bileşen değiştirme yardımcı olmak için bir model kullanabilirsiniz. Bir model, sisteminizin çalıştığı dünyanın görselleştirin, kullanıcıların ihtiyaçlarını açıklamak, sisteminizin mimarisini tanımlayın, kod çözümleme ve kodunuzu gereksinimleri karşıladığından emin olun yardımcı olabilir. Bkz: [kanal 9 videosu: mimariyi modelleme aracılığıyla geliştirmek](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Visual Studio'nun hangi sürümlerinin her model türünü desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="how-to-use-models"></a>Modelleri kullanma  
 Modelleri, çeşitli şekillerde yardımcı olabilir:  
  
- Modelleme diyagramları çizmek gereksinimleri, mimari ve üst düzey tasarım kavramları açıklamak yardımcı olur. Daha fazla bilgi için [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
- Modellerle çalışma gereksinimleri tutarsızlıklar kullanıma yardımcı olabilir.  
  
- Modelleri ile iletişim kurulurken önemli kavramlar iletişim kurmasına yardımcı değerinden muğlak doğal dil. Daha fazla bilgi için [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).  
  
- Modelleri, kod veya veritabanı şemalarını veya belgeler gibi diğer yapıları üretmek için bazen kullanabilirsiniz. Örneğin, modelleme bileşenlerini [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] modelden oluşturulur.  Daha fazla bilgi için [oluşturur ve uygulamanızı modeller aracılığıyla yapılandırma](../modeling/generate-and-configure-your-app-from-models.md).  
  
  Çok çeşitli işlemlerden aşırı yüksek Çevik seremoni modellerinde kullanabilirsiniz.  
  
### <a name="use-models-to-reduce-ambiguity"></a>Belirsizliği azaltmak için modelleri kullanır.  
 Dil modelleme, doğal dil daha az belirsiz ve genellikle yazılım geliştirme sırasında gerekli fikirleri ifade etmek için tasarlanmıştır.  
  
 Çevik yöntemleri küçük bir takım projeniz varsa, kullanıcı hikayelerini açıklığa kavuşturmanıza yardımcı olacak modeller kullanabilirsiniz. Müşteri ihtiyaçlarını hakkındaki tartışmalara model oluşturma yararlı soruları çok daha hızlı ve ani değişiklik ya da prototip kod yazmaya daha geniş bir alan, ürünün üzerinden oluşturabilirsiniz.  
  
 Projeniz büyük ve takımlar dünyanın dört bir yanındaki farklı kısımlarını içerir, gereksinimleri ve mimari düz metin olarak yapabilecekleriniz daha verimli iletişim kurmasına yardımcı olacak modeller kullanabilirsiniz.  
  
 Her iki durumda da neredeyse her zaman bir model oluşturma önemli bir azalma tutarsızlıklar ve belirsizlikleri sonuçlanır. Farklı proje katılımcıları sık sistem çalıştığı iş dünyanın farklı anlayışları sahip ve farklı geliştiriciler genellikle sistem nasıl çalıştığına ilişkin farklı anlarlar. Bir model, genellikle bir tartışmaya bir odak olarak kullanarak bu farklılıkları gösterir. Tutarsızlıkları azaltmak için bir modeli kullanma hakkında daha fazla bilgi için bkz. [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
### <a name="use-models-with-other-artifacts"></a>Diğer yapılar ile modelleri kullanma  
 Bir modeli kendisini gereksinimleri belirtimi veya bir mimari değildir. Bunların bazılarını daha net bir şekilde ifade etmek için bir araç olan, ancak yazılım tasarımı sırasında gerekli tüm kavramları ifade edilebilir. Modelleri, iletişimin OneNote sayfaları veya paragrafları gibi başka bir yolla birlikte bu nedenle kullanılmalıdır, Microsoft Office belgeleri, iş öğelerini [!INCLUDE[esprfound](../includes/esprfound-md.md)], ya da proje odası duvardaki Yapışkan Notlar. Son öğe dışında tüm bu nesne türleri için model öğeleri bölümleri bağlanabilir.  
  
 Normalde modelleri ile birlikte kullanılan belirtimi diğer yönleri arasında şunlar yer alır. Ölçek ve projenizin stili bağlı olarak birkaç bu görünüşler kullanın veya herhangi kullanmamak:  
  
-   Kullanıcı hikayeleri. Kullanıcı hikayesi kullanıcıların ve diğer proje katılımcıları projenin yineleme birinde teslim sistemin davranışı durumunun ele kısa bir açıklamasıdır. "Müşteri şunları yapabilecek..." tipik bir kullanıcı hikayesi başlar. Kullanıcı hikayesi, kullanım örnekleri grubu yapabilecek veya kullanım örneklerinin önceden geliştirilen uzantıları tanımlayabilirsiniz. Tanımlama veya kullanım örneklerinin genişletme kullanıcı hikayesinin daha anlaşılır hale getirmeye yardımcı olur.  
  
-   Değişiklik istekleri. Daha resmi proje içinde bir değişiklik isteğinin, Çevik bir proje içinde bir kullanıcı hikayesini çok benzer. Çevik bir yaklaşım, önceki yinelemelerde geliştirildiği bilgisayardakinden için tüm gereksinimleri değiştikçe değerlendirir.  
  
-   Kullanım örneği açıklaması. Kullanım örneği, bir kullanıcı belirli bir hedefe ulaşmak için sistemi ile etkileşime giren bir yolunu temsil eder. Tam bir açıklaması, olaylar ve olağanüstü sonuçlar ana ve alternatif dizileri, hedef içerir. Bir kullanım durumu diyagramı özetlemenize ve kullanım örneklerine genel bakış sağlayan yardımcı olur.  
  
-   Senaryo. Bir sistem, kullanıcıların ve diğer sistemler için birlikte nasıl değer proje katılımcılarına sağlamak çalıştığını gösteren bir olay dizisi oldukça ayrıntılı bir açıklaması bir senaryodur. Bu kullanıcı arabiriminin bir slide show veya kullanıcı arabiriminin bir prototip biçiminde. Bir kullanım örneği veya kullanım örneklerinin bir dizisini tanımlayabilirsiniz.  
  
-   Sözlük. Projenin gereksinimleri sözlüğü, müşteriler kendi dünya tartışmak kelimeleri açıklar. Kullanıcı arabirimi ve gereksinim modelleri de bu koşulları kullanmalısınız. Bir sınıf diyagramı, çoğu bu terimlerin arasındaki ilişkiler açıklanmasına yardımcı olabilir. Sözlük ve diyagramları oluşturma yalnızca kullanıcılar ve geliştiriciler arasında anlamaları azaltır, ancak artırarak yanlış anlaşılmaların farklı iş hissedarları arasında de neredeyse her zaman kullanıma sunar.  
  
-   İş kuralları. Birçok iş kuralları, ilişkileri ve gereksinimleri sınıfı modeldeki öznitelik sabit kısıtlama olarak ve sıralı diyagramlar üzerinde kısıtlama olarak belirtilebilir.  
  
-   Üst düzey tasarım. Başlıca parçaları ve bunlar birbirine nasıl uyduğunu açıklar. Bileşen, dizisi ve arabirimi diyagramları bir üst düzey tasarım önemli bir parçasıdır.  
  
-   Tasarım desenleri. Sistemin farklı bölümlerinin arasında paylaşılan Tasarım Kuralları açıklar.  
  
-   Sınama belirtimleri. Test betikleri ve test kodu tasarımlarında test adımları dizileri tanımlamak için etkinlik ve sıra diyagramları iyi kullanımını yapabilirsiniz. Böylece gereksinimleri değiştiğinde bunlar kolayca değiştirilebilir sistem testleri gereksinimleri modeli açısından ifade edilmelidir.  
  
-   Proje planı. Proje planı veya biriktirme listesine her bir özelliğin ne zaman teslim edilecek tanımlar. Her özellik, çalışmaları ve iş kuralları uygulayan veya genişletir kullandıklarınız belirterek tanımlayabilirsiniz. İş kuralları ve kullanım durumları için plan doğrudan ya da başvurabilir veya bir özellikler kümesi içinde ayrı bir belge tanımlayın ve özellik başlıkları plandaki kullanın.  
  
### <a name="use-models-in-iteration-planning"></a>Yineleme planlamasında modelleri kullanma  
 Tüm projeler, ölçek ve kuruluşun farklı olsa da, tipik bir proje yinelemesi iki ve altı hafta arasında bir dizi olarak sunulması planlanmaktadır. Erken yinelemeler kapsam ve sonraki yinelemeler için planları ayarlamak için kullanılacak görüşleri izin vermek için yeterli yinelemeler önemlidir.  
  
 Aşağıdaki öneriler, modelleme projesinde yinelemeli avantajlarını daha iyi anlamanıza yardımcı olmak yararlı bulabilirsiniz.  
  
#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Her yineleme yaklaşımlar odak keskinleştirin  
 Her yineleme yaklaştığında, yinelemenin sonunda teslim edilecek nedir tanımlamaya yardımcı olmak için modelleri kullanır.  
  
-   Erken yinelemeler ayrıntılı her şeyi model yok. İlk yinelemeyi kullanıcı sözlüğündeki ana öğeler için bir sınıf diyagramı oluşturun, önemli kullanım örneği diyagramı çizme ve ana bileşenleri diyagramı çizme. Daha sonra projede ayrıntı değişeceği ince ayrıntılı olarak bunlardan birine tanımlamaz. Bu modelde tanımlanan koşullara özellikleri veya kullanıcı hikayelerini listesini oluşturmak için kullanın. Özellikleri yaklaşık proje boyunca tahmini iş yükünü dengelemek için yinelemelere atayabilirsiniz. Bu atamaları, daha sonra projeyi değiştirir.  
  
-   En önemli kullanım örneklerini Basitleştirilmiş sürümleri erken bir yineleme uygulamak bu seçeneği deneyin. Genişletme sonraki yinelemelerde bu kullanım örnekleri. Bu yaklaşım, özel olarak gereksinimler eksiktir veya mimari hakkında herhangi bir şey yapmak için çok geç projesinde keşfetme riskini azaltmaya yardımcı olur.  
  
-   Her yinelemenin sonuna, ayrıntılı olarak sonraki yinelemesine geliştirilen kullanıcı hikayeleri ve gereksinimlerini tanımlamak için gereksinimler Atölyesi tutun. Kullanıcılar ve öncelikler, yanı sıra geliştiricilere ve sistem test edicilere karar verebilirsiniz iş hissedarlar davet edin. 2 haftalık yineleme gereksinimlerini tanımlamak üç saat bekleyin.  
  
-   Atölyesi amacı, sonraki yineleme sonunda elde edilecek kabul herkese yöneliktir. Modelleri araçlarından birini gereksinimleri belirlemenize yardımcı olması için kullanın. Atölyesi çıktısını bir yineleme biriktirme listesi olduğu: geliştirme listesi diğer bir deyişle, görevlerinin [!INCLUDE[esprfound](../includes/esprfound-md.md)] ve test paketleri [!INCLUDE[TCMext](../includes/tcmext-md.md)].  
  
-   Geliştirme görevlerini tahminleri belirlemek yalnızca gereksinim duymanıza kadar tasarımı gereksinimlerini atölyeyi tartışın. Aksi takdirde, kullanıcıların doğrudan deneyebileceği sistemi davranışını tartışmaya tutun. Gereksinimler modelini mimari modelden ayrı tutun.  
  
-   Yedeğin proje katılımcıları, genellikle sizden bazı yönergeler içeren bir UML diyagramları anlama herhangi bir sorun vardır.  
  
#### <a name="link-model-to-work-items"></a>İş öğelerine bağlantı modeli  
 Gereksinimleri Atölyesi sonra gereksinimler modelini ayrıntılarını özenli ve model geliştirme görevlerine bağlayın. İş öğelerini bağlayarak bunu yapabilirsiniz [!INCLUDE[esprfound](../includes/esprfound-md.md)] modeldeki öğeleri. Bunu yapma hakkında bilgi için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).  
  
 Herhangi bir öğe iş öğelerine bağlayabilirsiniz, ancak en yararlı öğeler aşağıdaki gibidir:  
  
-   Kullanım örnekleri. Bir kullanım durumu, uygulama geliştirme görevleri bağlayabilirsiniz.  
  
-   Uzantılar büyük/küçük harf kullanın. Yalnızca bir kullanım örneği tek bir yönüne yinelemeyi uygulanacak bir veya daha fazla uzantıları ile birlikte temel bir kullanım örneği içine ayırabilirsiniz. «Genişletmek» ilişki temel çalışmasıyla bağlantılı kullanım örnekleri uzantılarıdır. Kullanım örneği uzantıları hakkında daha fazla bilgi için bkz. [UML kullanma durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md).  
  
-   İş kuralları veya hizmet gereksinimlerinin kalitesini açıklayan yorumlar. Daha fazla bilgi için [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
#### <a name="link-model-to-tests"></a>Testler için bağlantı modeli  
 Kabul testleri tasarım kılavuzu için gereksinimler modelini kullanın. Bu testleri eşzamanlı geliştirme işi oluşturun.  
  
 Bu yöntem hakkında daha fazla bilgi için bkz: [model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md).  
  
#### <a name="estimate-remaining-work"></a>Kalan işi tahmin etme  
 Gereksinimler modelini, her yineleme boyutu ile ilgili proje toplam boyutunu tahmin yardımcı olabilir. Sayısı ve karmaşıklığı kullanım örnekleri ve sınıflarının değerlendirerek gerekli olacak geliştirme iş tahmin etmenize yardımcı olabilir. İlk birkaç yinelemenin kapsanan gereksinimler karşılaştırması tamamladıktan ve gereksinimlerini karşılamak için hala zaman maliyeti yaklaşık bir ölçü ve projenin geri kalanını kapsamını verebilirsiniz.  
  
 Her yinelemenin sonuna, gelecekteki yinelemeleri için gereksinimlerin atamasını gözden geçirin. Alt kullanım örneği diyagramı sistemde olarak her yinelemenin sonunda, yazılım durumunu göstermek için yararlı olabilir. Tartışmalarınızda kullanım örneklerini ve bu alt sistemlerin birinden diğerine büyük/küçük harf uzantıları kullanın.  
  
## <a name="levels-of-abstraction"></a>Özet Düzeyi  
 Modelleri, bir dizi yazılım ile ilgili Özet vardır. En somut modeller, program kodu doğrudan temsil eder ve en soyut modeller olabilir veya kodda temsil edilmeyen iş kavramlarını göstermek.  
  
 Bir model çeşitli türlerde diyagramları görüntülenebilir. Modelleri ve diyagramları hakkında daha fazla bilgi için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).  
  
 Farklı türlerdeki diyagram, farklı düzeylerde soyutlama tasarım açıklamak için yararlıdır. Çoğu diyagram türleri, birden fazla düzeyde yararlı olur. Bu tablo, her diyagram türü nasıl kullanılabileceğini gösterir.  
  
|Tasarım düzeyi|Diyagram türleri|  
|------------------|-------------------|  
|İş süreci<br /><br /> Sisteminiz içinde kullanılacak bağlamı anlamak kullanıcılar bundan gerekenler anlamanıza yardımcı olur.|-Etkinlik diyagramları iş hedeflerine ulaşmak için insanlar ve sistemler arasındaki iş akışını açıklar.<br />-Kavramsal sınıf diyagramları, iş süreci içinde kullanılan iş kavramlarını açıklar.|  
|Kullanıcı gereksinimleri<br /><br /> Kullanıcıların sisteminizi gerekenler tanımı.|-Kullanım örneği diyagramları, kullanıcıların ve diğer dış sistemler, geliştirmekte olduğunuz sistemiyle sahip etkileşimleri özetleyin. Ayrıntılı tanımlamak için her kullanım örneğine başka belgeler ekleyebilirsiniz.<br />-Sınıf diyagramları UML iletişim kuran sistem ve kullanıcılar hakkında bilgi türleri açıklanmaktadır.<br />-İş kuralları ve hizmet gereksinimleri kalitesini ayrı belgelerinde açıklanabilir.|  
|Üst düzey tasarım<br /><br /> Sistemin genel yapısını: ana bileşenleri ve bunların birlikte nasıl birleştirin.|-Katman diyagramları, sistemin bölümler halinde nasıl yapılandırıldığını açıklar. Program kodunu katman diyagramları, mimari uymasını sağlamak için karşı doğrulayabilir.<br />-Bileşen diyagramları sağlanan ve her bir bileşen tarafından gerekli olan hizmetler ve iletileri belirtme parçaların arabirimleri gösterin.<br />-Sıralı diyagramlar, her kullanım örneği uygulama bileşenlerini nasıl iletişim kurduğunu gösterir.<br />-Sınıf diyagramları UML bileşenleri ve bileşenleri arasında geçirilen veri türlerine arabirimler açıklanmaktadır.|  
|Tasarım desenleri<br /><br /> Kuralları ve tasarım tüm bölümlerinde kullanılan tasarım sorunlarını çözme yöntemleri|-UML sınıf diyagramları bir desen yapıları açıklar.<br />-Sıra veya etkinlik diyagramları etkileşimleri ve algoritmaları Göster|  
|Kod Analizi<br /><br /> Birden fazla diyagram koddan oluşturulabilir.|-Sıralı diyagramlar, koddaki nesneler arasındaki etkileşimi gösterir.<br />-Katman diyagramları sınıfları arasındaki bağımlılıkları gösterir. Bir katman diyagramına karşı güncelleştirilmiş kod doğrulanabilir.<br />-Sınıf diyagramları, kod içinde sınıfları gösterir.|  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
|**Kategori**|**Bağlantılar**|  
|------------------|---------------|  
|**Videolar**|![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [videoları MSDN Nasıl Yaparım: oluşturma ve kullanma UML modellerini ve diyagramları (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Visual Studio 2010 ile UML](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [MSDN nasıl yaparım serisi: UML araçları ve genişletilebilirlik (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Teknik makaleler ve belgeler**|[MSDN Mimari Merkezi](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Visual Studio Mimari Araç Kullanımı Kılavuzu](../modeling/visual-studio-architecture-tooling-guidance.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çevik Yazılım geliştirmede modeller kullanma](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)   
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)   
 [Uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)   
 [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)   
 [Modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)



