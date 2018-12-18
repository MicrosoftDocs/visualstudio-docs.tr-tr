---
title: Kullanıcı gereksinimlerini modelleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab92a08aa7359aa4393b3356384a4ccc352afb27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776492"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etkinlikler ve bölümü hakkında diyagramlar çizerek kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışın ve visual Studio yardımcı sisteminizi hedeflerine elde etmelerine yardımcı oynadığı. Her biri farklı bir açısını Kullanıcıların ihtiyaçlarını üzerinde odaklanır. Bu diyagramları kümesi gereksinimleri modelidir. Video gösterimi için bkz: [iş etki alanı modelleme](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Visual Studio'nun hangi sürümlerinin her model türünü desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Gereksinimler modeli, yardımcı olur:  
  
- İç tasarımından ayrı olarak sistemin dış özelliklerine odaklanır.  
  
- Kullanıcıların ve hissedarların ile doğal dilde daha az belirsizlik gerekiyor.  
  
- Tutarlı bir kullanıcı, geliştiriciler ve testçiler tarafından kullanılan terimler sözlüğü tanımlayın.  
  
- Boşluk ve tutarsızlıkları azaltın.  
  
- Gereksinim değişikliklerine yanıt vermek için gereken iş miktarını azaltmaya.  
  
- Özellikleri geliştirileceğini sırasını planlayın.  
  
- Modelleri, testler ve gereksinimler arasında NET bir ilişki yapma, sistem testleri için temel olarak kullanın. Gereksinimleri değiştiğinde, bu ilişki, testler doğru bir şekilde güncelleştirmenize yardımcı olur. Bu, sistemin yeni gereksinimlerini karşıladığından emin olur.  
  
  Kullanıcıları veya temsilciler ile tartışmalara odaklanmak için kullanın ve bunu her yineleme başlangıcında yeniden ziyaret gereksinimler modelini en büyük avantajı sağlar. Ayrıntılı olarak kod yazmadan önce tamamlamanız gerekmez. Kısmen çalışan bir uygulama, çok Basitleştirilmiş bile genellikle kullanıcıların gereksinimleriyle irdelemesi en cazip temelini oluşturur. Model, bu tartışmaların sonuçları özetlemek için etkili bir yoludur. Daha fazla bilgi için [geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  Bu konular boyunca sistem ya da geliştirmekte olduğunuz uygulamanın "Sistem" anlamına gelir. Birçok yazılım ve donanım bileşenleri büyük koleksiyonu olabilir; ya da tek bir uygulama; veya daha büyük bir sistemde içinde bir yazılım bileşeni. Her durumda, bir kullanıcı arabirimi ya da API aracılığıyla sistemin dışından görülemediğinden, davranışı gereksinimler modelini açıklar.  
  
## <a name="common-tasks"></a>Ortak Görevler  
 Kullanıcı gereksinimlerini birkaç farklı görünümler oluşturabilirsiniz.  Her görünüm, belirli türde bilgi sağlar.  Bu görünümler oluşturduğunuzda, sık birinden diğerine taşımak idealdir. Herhangi bir görüntüden yeniden başlatabilirsiniz.  
  
|Diyagram veya belge|Bu gereksinimler modelinde açıklar|Bölüm|  
|-------------------------|-----------------------------------------------|-------------|  
|Kullanım örneği diyagramı|Sistem ve onunla neler kullanan.|[Sisteminizi nasıl kullanıldığını açıklayan](#UseCases)|  
|Kavramsal bir sınıf diyagramı|Gereksinimlerini tanımlamak için kullanılan türler sözlüğü; görünen türler sistemin arabirimi.|[Gereksinimlerini tanımlamak için kullanılan terimleri tanımlama](#RequirementsClasses)|  
|Etkinlik diyagramı|Kullanıcılar ve sistemini veya parçalarından tarafından gerçekleştirilen etkinlikleri arasındaki iş ve bilgi akışı.|[Kullanıcılar ve sistem arasındaki iş akışını gösterme](#Workflow)|  
|Sıralı diyagram|Kullanıcılar ve sistem veya parçalarından arasındaki etkileşimler dizisini. Etkinlik diyagramı alternatif görünüm.|[Kullanıcılar ve sistem arasındaki etkileşimler gösteriliyor](#Sequences)|  
|Ek belgelerin veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet gereksinimlerinin kalitesini açıklayan](#QoSRequirements)|  
|Ek belgelerin veya iş öğeleri|Kullanım kısıtlamaları ve belirli bir özel olmayan kuralları|[İş kurallarını gösterme](#BusinessRules)|  
  
 Diyagram türlerin çoğu başka bir amaçla kullanılabilir dikkat edin. Diyagram türleri genel bakış için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md). Diyagramları çizmek hakkında temel bilgiler için bkz: [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
##  <a name="UseCases"></a> Sisteminizi nasıl kullanıldığını açıklayan  
 Sistem kullanan ve bunun için kullandıkları açıklamak için kullanım örneği diyagramları oluşturun. Kullanım örneği, bir kullanıcı sistemi ve hedefe ulaşmak için gerçekleştirdikleri yordamı hedefi temsil eder.  
  
 Örneğin, sistem satış bir çevrimiçi yemek menü öğeleri seçme özgürlüğü tanıyın gerekir ve menüyü güncelleştirmek sağlama restoranlar izin vermeniz gerekir. Bu bir kullanım durumu diyagramı özetleyebilir:  
  
 ![Kullanım örnekleri için müşteri ve Restoran](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 Ayrıca, bir kullanım durumu daha küçük örneklerini nasıl oluştuğunu da gösterebilirsiniz. Örneğin, yemek siparişi, ödeme ve teslim yöntemlerine yemek satın parçasıdır:  
  
 ![Sistem, ödeme ancak teslime katılır. ](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 Hangi kullanım örnekleri, geliştirmekte olduğunuz sisteminin kapsamına dahildir da gösterebilirsiniz. Örneğin, çizimdeki sistem bölümü Yemek Dağıt kullanım örneğine almaz. Bu, geliştirme iş bağlamını ayarlayın yardımcı olur. (Kullanım örneği diyagramı alt kapsayıcıları sistem veya bileşenleri temsil etmek için kullanılabilir.)  
  
 Ayrıca takım birbirini izleyen sürümlerde eklenecektir tartışmanıza yardımcı olur. Örneğin, tartışmak mi, ilk sürümde sistemin kullandıkça doğrudan restorana ve sistem üzerinden gitmek yerine müşteri arasında yemek düzenlenmiş için. Bu durumda, ilk yayın için Dinner Now sistemi dikdörtgen dışında yemek Kullandıkça Ödeme yaparak taşıyabilirsiniz.  
  
 Bir kullanım durumu diyagramı, yalnızca kullanım örneklerini özetini sağlar. Daha ayrıntılı açıklamalar sağlamak için diyagramda ayrı belgelere ve diğer diyagramlarla kullanım örneklerine bağlayabilirsiniz. Bunu yapma hakkında bilgi için bkz: [kullanım örneğini belgelere ve diyagramlara bağlama](../modeling/link-a-use-case-to-documents-and-diagrams.md).  
  
 Kullanım çalışması diyagramı çizme, takımınızın yardımcı olur:  
  
- Hangi kullanıcılar tarafından uygulamasının Ayrıntılar dikkatiniz olmadan sistemiyle yapmak beklediğinize odaklanın.  
  
- Sisteminizin kapsam ya da sistem belirli sürümlerini ele alınmıştır.  
  
  Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|Nasıl oluşturulacağı hakkında daha ayrıntılı bilgi kullanım örnekleri|[UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Kullanım örneği diyagramındaki öğeler|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|  
|Kullanım örneklerinden kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> Gereksinimlerini tanımlamak için kullanılan terimleri tanımlama  
 UML sınıf diyagramları, tutarlı bir sözlük aşağıdaki amaçlar için kullanılan iş kavramlarını geliştirmenize yardımcı olması için kullanabilirsiniz:  
  
- Sistem çalıştığı iş tartışmak için kullanıcılar tarafından.  
  
- Örnek kullanım durumları, iş kuralları ve kullanıcı hikayeleri açıklamalarında Kullanıcıların ihtiyaçlarını açıklamak için.  
  
- Sistemin API veya kullanıcı arabirimi aracılığıyla alınıp bilgi türleri.  
  
- Sistem veya onay testleri açıklamaları.  
  
  Bu amaç için kullanılan bir UML sınıf diyagramı içeriğini kavramsal sınıf diyagramı çağrılır. (Olarak da bilinen bir *etki alanı modeli* veya *sınıf çözümleme modeli*.)  
  
  Kavramsal bir sınıf diyagramında, sistemin iç tasarımının ayrıntısı göstermeden gereksinimleri açıklamasında gereken yalnızca sınıfları göster. Diyagram sistemin iç tasarım ayrıntılarını göstermez. Genellikle işlemleri veya arabirimleri kavramsal sınıflarında göstermeniz gerekmez.  
  
  Örneğin, Şimdi Akşam Yemeği sisteminin kavramsal bu sınıfların çizebilirsiniz:  
  
  ![Sınıfları menü, sipariş menü öğesi, Düzen öğesi. ](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
  Kavramsal bir sınıf diyagramı boyunca gereksinimler modelini kullanan terimlerin sözlüğünü sağlar. Örneğin, ayrıntılı açıklama kullanım durumu, Yemek Sipariş, yazabilirsiniz:  
  
  Müşterinin seçtiği bir *menü* oluşturmak üzere bir *sipariş*ve ardından oluşturan *öğeleri sıralama* içinde *sipariş* seçerek *Menü öğelerini* gelen *menü*.  
  
  Açıklamada kullanılan terimler modelinde sınıfların adlarını nasıl olduğuna dikkat edin. Diyagram, bu sınıflar arasındaki ilişkileri belirsizlikleri kaldırır. Örneğin, bu açıkça her sipariş yalnızca bir menü ile ilişkili olduğunu gösterir.  
  
  Artırarak yanlış anlaşılmaların kullanıcıların gereksinimleri hakkında sık sözcük ayrıntılı ilgili anlamaları için de izlenebilir. Örneğin, çoğu Restoran menüsü ve sipariş terimleri paylaşılan bir anlayışa sahip olacaktır, ancak bir öğe üzerinde bir sipariş menüsündeki bir öğeyi arasındaki fark daha az açıktır. Gereksinimleri ile işletme paydaşları tartışılırken, bu farklılıkları kullanıma sunmak önemlidir. Sınıf diyagramı, koşulları ve ilişkilerini açıklamak yardımcı olmak için yararlı bir araçtır.  
  
  Sistem iş mantığı açıklanabilir temel sözlük kavramsal sınıf modeli oluşturabilir. Ancak uygulamanızın performans, dağıtım, esneklik ve diğer faktörler gibi konuları göz önünde bulundurmanız gerekir çünkü yazılım sınıflarda genellikle kullanılan kavramsal model çok daha karmaşık olacaktır. Kavramsal bir sınıfın birkaç farklı uygulamaları bir sistemde nadir bulunan hatalardır.  
  
  Örneğin, siparişler, XML, SQL, HTML ve C# dilinde ve sistemin farklı parçaları parçalar arasındaki farklı arabirimlerde gösterilebilir. Siparişi ile menü arasındaki ilişki, C# kodu, bir veritabanında ilişkileri başvurulara gibi birçok farklı şekillerde gösterilebilir veya XML kimlikleri çapraz başvuru. Ancak şu farklılıklara rağmen kavramsal model yazılımın her bir parçası doğru olan önemli bilgiler sağlar. Örnek sınıf diyagramında bize her uygulamada olacağını tek her siparişi ile menü ilişkili gösterir.  
  
  Takımınızın gereksinimlerini sınıf diyagramı çizme yardımcı olur:  
  
- Kullanıcıların ihtiyaçlarını tartışmalara temel terimleri standartlaştırmak ve tanımlayın.  
  
- Bu terimler arasındaki ilişkileri açıklayın.  
  
  Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|Gereksinimler sınıflarını bulma hakkında daha ayrıntılı bilgi|[UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
|Kavramsal sınıf diyagramındaki öğeler|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|  
|Kavramsal sınıflardan kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
 Kavramsal bir sınıf diyagramında, bunu genellikle oklar gezinebilirliği ilişkilendirmeleri yerleştirmek kullanışlı değildir. Diyagram uygulaması göstermiyor olmasıdır. İlişkilendirmeleri gerçek nesneler arasındaki ilişkileri temsil eder. Aşağıdaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı olmayan yönlü oklar varsayılan yap: [örnek: etki alanı UML modelleme özellikleri](http://go.microsoft.com/fwlink/?LinkId=213849).  
  
##  <a name="BusinessRules"></a> İş kurallarını gösterme  
 Bir iş kuralı, belirli kullanım örneği ile ilişkili değil ve sistem genelinde gözlenmelidir bir gereksinimdir.  
  
 Birçok iş kuralları kavramsal sınıflar arasındaki ilişkileri kısıtlamalar şunlardır. Bu yazma *statik iş kuralları* kavramsal sınıf diyagramında ilgili sınıflar ile ilgili açıklamalar olarak. Örneğin:  
  
 ![Açıklama kuralında sırasını sınıfa iliştirilen. ](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 *Dinamik iş kuralları* kısıtlamak izin verilen olaylar dizisi. Örneğin, bir kullanıcı, sisteminizdeki diğer işlemleri gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıralı veya etkinlik diyagramı kullanın.  
  
 Ancak, çok sayıda dinamik kurallar daha etkili bir şekilde ve genel statik kuralları ile değiştirerek belirtilebilir. Örneğin, bir sınıfa sınıf kavramsal modeldeki 'Farklı oturum' bir Boolean özniteliği ekleyebilirsiniz. Günlük kullanım örneğindeki Sonkoşul olarak oturum ekleyin ve diğer kullanım örnekleri çoğunu önkoşulu olarak ekleyin. Bu yaklaşım, tüm olası eşleştirme birleşimlerini olaylar dizisini tanımlamamaya özen gösterin sağlar. Yeni kullanım durumlarını modele eklemek, ihtiyacınız olduğunda, ayrıca daha esnektir.  
  
 Seçimi buraya gereksinimleri nasıl tanımlayacağınız hakkında olduğunu ve bunun nasıl gereksinimleri program kodu içinde uygulamanız bağımsız olduğuna dikkat edin.  
  
 Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|Bulma ve statik iş kurallarını kaydetme hakkında daha ayrıntılı bilgi|[UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
|Kavramsal sınıf diyagramındaki öğeler|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|  
|İş kurallarının aynılarını kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Hizmet gereksinimlerinin kalitesini açıklayan  
 Hizmet gereksinimi kalitesi birkaç işlem kategorisi vardır. Bunlar aşağıdakileri içerir:  
  
- Performans  
  
- Güvenlik  
  
- Kullanılabilirlik  
  
- Güvenilirlik  
  
- Sağlamlık  
  
  Bu gereksinimlerin bazıları belirli kullanım durumları açıklamasında içerebilir. Diğer gereksinimler kullanım örneklerine özgü olmayan ve ayrı bir belgede en etkili bir şekilde yazılır. Mümkün olduğunda, gereksinimler modeli tarafından tanımlanan sözlük izliyor kullanışlıdır. Aşağıdaki örnekte, özel olarak gereksinimini kullanılan ana sözcüklerin aktörleri kullanım örnekleri ve önceki çizimlerde sınıfları başlıklarını olduğuna dikkat edin:  
  
  Bir müşteri, Yemek Sipariş sırada bir restoran, bir menü öğesini siler. Bu menü öğesine başvuran bir sipariş öğesi kırmızı renkte görüntülenir.  
  
  Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|Hizmet gereksinimlerinin kalitesini kaydetme hakkında daha ayrıntılı bilgi|[Kalite hizmet gereksinimlerini tanımlama yönergeleri](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Kullanım örnekleri için ek belgelere ekleme|[Kullanım örneğini belgelere ve diyagramlara bağlama](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|Hizmet gereksinimlerinin kalitesini için uyar kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> Kullanıcılar ve sistem arasındaki iş akışını gösterme  
 Etkinlik diyagramı, farklı kullanım örnekleri arasında iş akışını göstermek için kullanabilirsiniz. Kullanıcılar - sistemiyle ve bunun dışında gerçekleştirdiği temel görevleri gösteren bir etkinlik diyagramı çizme tarafından gereksinimler modelini başlamak genellikle yararlıdır.  
  
 Örneğin:  
  
 ![Üç eylem ve bir döngünün olan etkinlik. ](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 Kullanım örneği diyagramları ve aynı bilgilerle farklı görünümler göstermek için etkinlik diyagramlar çizebilirsiniz.  Kullanım durumu diyagramı daha küçük eylemleri daha büyük bir etkinlik içinde iç içe gösterme konusunda etkili olsa da, iş akışı göstermez. Örneğin:  
  
 ![Kullanım örnekleri için önceki eylemlerin](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 Ayrıca etkinlik diyagramları, yazılım içinde ancak iş süreci, sistem dışında görünür olan eylemleri odaklanmak için diyagramları kullandığınızda algoritmaları tarif için kullanabileceğiniz dikkat edin.  
  
 Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|İş iş akışları tanımlama hakkında daha fazla bilgi|[UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|  
|Bir etkinlik diyagramındaki öğeler|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|  
|Etkinlik diyagramları koddan geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> Kullanıcılar ve sistem arasındaki etkileşimler gösteriliyor  
 Sıralı diyagram, ileti sistemi ve harici aktörler arasında ya da sistemin bölümleri arasındaki değişimi göstermek için kullanabilirsiniz. Bu açıkça etkileşimler dizisini gösterir bir kullanım örneğindeki adımların bir görünüm sağlar. Sıralı diyagramlar taraflarla bir kullanım örneği ve sisteminizin bir API'ye sahip olduğu da birkaç etkileşimde bulunduğu özellikle yararlıdır.  
  
 Örneğin:  
  
 ![Sistem ve aktör sıralı diyagram. ](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 Sıralı diyagramlar bir avantajı, oluşturmak sisteme hangi iletileri geldiğini görmenin kolay olmasıdır. Sistem tasarlamak için her bir bileşen için ayrı bir yaşam çizgisi tek bir sistem yaşam çizgisi değiştirin ve ardından bunları her gelen iletiye yanıt olarak arasındaki etkileşimler göster.  
  
 Aşağıdaki konular, daha fazla bilgi sağlar:  
  
|Hakkında bilgi edinmek için|Oku|  
|--------------------|----------|  
|Etkileşimler tanımlama hakkında daha fazla bilgi|[UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Bir sıralı diyagram üzerindeki öğeleri|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|  
|Sıralama diyagramları koddan geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>Tutarsızlıkları azaltmak için bir modeli kullanma  
 Model oluşturma genellikle tutarsızlıklar önemli azalmaya ve kullanıcı gereksinimlerini belirsizliklerden sonuçlanır. Farklı proje katılımcıları, sistem çalıştığı iş dünyanın farklı anlayışları sık vardır. Bu nedenle, ilk görevi istemcileriniz arasındaki farklar çözmek sağlamaktır.  
  
 Bir model oluştururken iş etki alanı hakkındaki kadar fazla soruyu doğal olarak oluşan bulabilirsiniz. Kullanıcıların bu soruları koyarak projedeki daha sonraki bir aşamada değişiklikleri gereksinimini azaltır. İlk başta kendinize ve ardından yanıt belirsiz olup işletme paydaşları sorun belirli bazı sorular şunlardır:  
  
- "Hangi kullanım bu sınıfın örneklerinin oluşturur?" gereksinimleri modeldeki her bir sınıf için sor Örneğin, bir çevrimiçi yemek siparişi hizmet içinde isteyebilir, "hangi kullanım Restoran menüsü sınıfının bir örneğini oluşturur?" Bu tartışma nasıl yeni bir restoran hizmete kaydolan ve onun menü katkıda bulunduğu yol açar. Neyin oluşturduğu veya öznitelikler ve ilişkilendirmeler değişiklikleri hakkında benzer sorular sorabilirsiniz.  
  
- Sonucu veya sınıf diyagramları tarafından sağlanan sözcüklerdeki her kullanım örneği sonkoşulunu açıklamak gereksinimleri modeldeki her kullanım örneği için deneyin. Önce ve sonra bir oluşum kullanım örneğinin sınıfların örneklerini hazırlayarak kullanım etkisini göstermek sık kullanışlıdır. Örneğin, kullanım örneği sonkoşulunun "menü öğesi için müşterinin sipariş eklendiğinde" derse, sıralama ve menü öğesi sınıfların örneklerini tasarlayın. Yeni bir bağlantı veya yeni bir nesne gibi bir kullanım örneği etkilerini yeni bir çizim veya farklı bir renkte gösterir. Bu sık hangi bilgilerin modelde gerekli olduğu hakkında tartışmalar neden olur. Gereksinimleri sınıfları doğrudan bir uygulama ile ilgilenir değil olsa da, sisteminizin depolamak ve iletmek için gereken bilgileri açıklar.  
  
- Öznitelikler ve ilişkilendirmeler, özellikle birden fazla öznitelik veya ilişkilendirme ilgili kısıtlamalar kısıtlamalar hakkında isteyin.  
  
- Kullanım örnekleri, bunları göstermek için sıralı veya etkinlik diyagramları çizmek geçerli ve geçersiz dizileri hakkında isteyin.  
  
  Farklı diyagramlarda sağlayan görünümleri arasındaki ilişkileri inceleyerek, kullanıcılarınızın iş, ana kavramları hızla anlayabilmeniz ve bunları sistemden ihtiyaç duydukları anlamak için yardımcı olur. Ayrıca hangi gereksinimler paydaşlara hakkında az belirli daha iyi anlayabilirsiniz. Bu özellikler, kullanıcıların onları denemelerine izin vermek için bu projenin erken bir aşamada Basitleştirilmiş en az geliştirmek planlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)   
 [Uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)   
 [Örnek VS uzantısı: Etki alanı UML modelleme özellikleri](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [Örnek VS uzantısı: Renkli UML öğeleri Sterotipe göre](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Örnek VS uzantısı: Bağlantı UML öğelerini diyagramları, dosyalarına ve diğer öğeleri](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [Örnek VS uzantısı: UML diyagramında şekilleri Hizala](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [Video: iş etki alanı modelleme](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



