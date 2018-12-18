---
title: 'UML Kullanım durumu diyagramları: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b4a4bc02202f8ec1f41052dcdea63d97bbcb9671
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793093"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML Kullanım Durumu Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da çizdiğiniz bir *kullanım örneği diyagramı* kullanan uygulama ya da sistemin ve onunla neler özetlemek için. Bir UML Kullanım durumu diyagramı oluşturmak için **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
 Video gösterimi için bkz. [kullanım örnekleri düzenleme özelliklerini](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bir kullanım durumu diyagramı yardımıyla iletişim tartışmak ve:  
  
- Senaryoları, sistem veya uygulama kişiler, kuruluşlar veya dış sistemlerle etkileşim içinde.  
  
- Bu aktörlerin başarmasına yardımcı olan hedefler.  
  
- Sisteminizin kapsam.  
  
  Ayrıntılı kullanım örneklerinin bir kullanım durumu diyagramı göstermiyor: Bu yalnızca bazı kullanım örnekleri, aktörler ve sistemler arasındaki ilişkileri özetlenmektedir. Özellikle, diyagram, her kullanım örneği hedeflere ulaşmak için adımlar gerçekleştirildiği sırada göstermez. Bu ayrıntıları başka diyagramları ve her kullanım örneğine bağlayabilirsiniz belgelerini tanımlayabilirsiniz. Daha fazla bilgi için [kullanım örneklerini açıklayan ayrıntılı](#Details) bu konuda.  
  
  Kullanım durumları için sağladığınız açıklamaları sistem çalıştığı, satış, menü, müşteri ve benzeri gibi etki alanı ile ilgili çeşitli koşulları kullanır. Bu hüküm ve aralarındaki ilişkiler açıkça tanımlamak önemlidir ve UML sınıf diyagramı yardımıyla bunu yapabilirsiniz. Daha fazla bilgi için [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).  
  
  Kullanım örnekleri, yalnızca bir sistem işlevsel gereksinimlerini de ilgilidir. İş kuralları, hizmet gereksinimleri ve uygulama kısıtlamaları kalitesi gibi diğer gereksinimleri ayrı ayrı gösterilmelidir. Mimari ve dahili ayrıntılar da ayrı olarak tanımlanmış olmalıdır. Kullanıcı gereksinimlerini tanımlama hakkında daha fazla bilgi için bkz. [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
  Bu konuda kullanılan örnekler müşterilerin yerel restoranlar gelen yemek sipariş edebilirsiniz bir Web sitesi ilgilidir.  
  
  ![Bir kullanım durumu diyagramı öğeleri](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
- Bir *aktör* (1) bir kişi, kuruluş, cihaz veya sisteminizin ile etkileşime giren dış yazılım bileşeni sınıfıdır. Örnek aktörler **müşteri**, **Restoran**, **sıcaklık algılayıcısı**, **kredi kartı Yetkilendiricisi.**  
  
- A *kullanım* (2) içinde takip belirli bir hedef, bir veya daha fazla aktör tarafından gerçekleştirilen eylemleri gösterir. Örnek kullanım örnekleri **Yemek Sipariş Et**, **güncelleştirme menü**, **işlem ödemesi**.  
  
   Bir kullanım durumu diyagramında kullanım örnekleri, bunları gerçekleştiren aktörleri ile ilişkili (3) ' dir.  
  
- *Sistem (4)* geliştirdiğiniz olduğu. Aktörleri yalnızca diğer yazılım bileşenleri olan küçük bir yazılım bileşeni olabilir; veya tam bir uygulamayı olabilir; veya büyük dağıtılmış birçok bilgisayarları ve cihazları dağıtılan uygulamalar dizisi olabilir. Örnek alt sistemleridir **Yemek Sipariş Web sitesi**, **yiyecek teslim iş**, **Web sitesi sürüm 2**.  
  
   Hangi kullanım örnekleri sisteminize veya onun alt sistemleri tarafından desteklenen bir kullanım durumu diyagramı gösterebilirsiniz.  
  
##  <a name="BasicSteps"></a> Kullanım örneği diyagramları çizmek için temel adımlar  
  
> [!NOTE]
>  Herhangi bir modelleme diyagramının oluşturmaya yönelik ayrıntılı adımlar açıklanmıştır [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>Yeni bir kullanım durumu diyagramı oluşturmak için  
  
1.  Üzerinde **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
2.  Altında **şablonları**, tıklayın **UMLUse durumu diyagramı**.  
  
3.  Diyagrama ad verin.  
  
4.  İçinde **modelleme projesine Ekle**, çözümünüzde varolan modelleme projesini seçin veya **yeni modelleme projesi oluşturma**ve ardından **Tamam**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>Bir kullanım durumu diyagramı çizmek için  
  
1.  Sürükleme **alt** tüm sisteminizi veya ana bileşenlerini göstermek için diyagramda, araç kutusundan sınırlar.  
  
    -   Sisteminizde veya bileşenleri tarafından hangi kullanım örneklerinin açıklamak istemiyorsanız sınırları desteklenen sistemi olmayan bir kullanım durumu diyagramı çizebilirsiniz.  
  
    -   Gerekliyse daha büyük, yapmak için bir sisteme köşesindeki sürükleyin.  
  
    -   Uygun şekilde yeniden adlandırın.  
  
2.  Sürükleme **aktörler** (bunları herhangi bir sistem sınırları dışından yerleştirerek) Diyagram Araç kutusundan.  
  
    -   Aktör, kullanıcılar ve kuruluşlar sisteminizi etkileşimli dış sistemlerle sınıfları temsil eder.  
  
    -   Bunları yeniden adlandırın. Örneğin: **müşteri, Restoran, kredi kartı kurumu.**  
  
3.  Sürükleme **kullanım durumları** ilgili sistemlere araç kutusundan.  
  
    -   Kullanım örnekleri, sisteminizin yardımıyla aktörler gerçekleştiren etkinlikler temsil eder.  
  
    -   Bunları aktörlerin öğrenmesi başlıklarını kullanarak yeniden adlandırın. Kodunuz ile ilgili başlıkları kullanmayın. Örneğin: **Yemek Sipariş Et, Yemek yemek sunmak için ödeme**.  
  
    -   Gibi önemli işlemler ile başlayan **Yemek Sipariş Et**, bırakma gibi daha küçük etkileşimler **seçin menü öğesi**.  
  
    -   Her yerde, sistem veya (herhangi bir cephe veya bileşen yalnızca kullanıcıya bağlanmada dahil yoksayar) destekliyorsa büyük alt sistemi durumu kullanın.  
  
    -   Bir kullanım örneği, sisteminiz tarafından belki de bir belirli sürümünün veya desteklenmediğini göstermek için sistem sınırının dışında çizebilirsiniz.  
  
4.  Tıklayın **ilişkilendirme** araç, sonra bir kullanım durumu ve kullanım örneğine katılan bir aktör üzerinde. Bu şekilde, kullanım örnekleri her aktör bağlayın.  
  
5.  Yapı kullanımı durumlarda ile **INCLUDE**, **Genişlet** ve **Genelleştirme** ilişkileri. Bu bağlantıların her birini oluşturmak için kaynak ardından durumda, ardından hedef aracı tıklayın. Aşağıdaki başlıklı bölüme bakın [kullanım örneklerini](#Structuring).  
  
6.  Kullanım örnekleri daha ayrıntılı açıklanmaktadır. Aşağıdaki başlıklı bölüme bakın [kullanım örneklerini açıklayan ayrıntılı](#Details).  
  
7.  Farklı alt sistemler veya ilgili kullanım farklı gruplara odaklanmak için farklı diyagramlar çizin. Bir modelleme projesindeki tüm diyagramları aynı modelin görünümleridir.  
  
##  <a name="Actors"></a> Çizim aktörler ve kullanım  
 Ana amacı, bir kullanım durumu diyagramı, sisteminiz ve onunla ulaştıkları ana hedeflerinden ile kimin etkileşim kurar göstermektir.  
  
-   Oluşturma **aktörler** kişiler, kuruluşlar, diğer sistemler, yazılım veya sistem veya alt sistem ile etkileşimde bulunan cihazları sınıfları temsil etmek için.  
  
    -   Aktörler ve diğer öğeleri nasıl çizileceğini bilgi edinmek için [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
    -   Fiziksel bir kişi veya varlıkları aynı olsa bile farklı her hedef için kümesi aktörler kendi türü veya rolüne göre belirleyin. Bir restoran çalışan bir müşteri bazen olsa bile, Restoran ve müşteri ayrı, birer aktördür.  
  
-   Oluşturma **kullanım durumları** sistemiyle elde etmek için her aktör aradığı hedeflerinden her biri için.  
  
    -   Ad ve aktör öğrenmesi, uygulama koşulları yerine sözcükleri kullanım örneklerini tanımlayın.  
  
-   Kullanma **ilişkilendirmeleri** aktörleri kullanım örneklerine bağlanacak.  
  
### <a name="inheritance-between-actors"></a>Aktörler arasında devralma  
 ![Devralma gösteren kullanım durumu diyagramı](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 Çizim yapabileceği bir **Genelleştirme** aktörler arasında bağlantı. Örnekte, kulübü müşteri gibi özelleştirilmiş bir aktör genelleştirilmiş aktör, müşteri gibi kullanım örneklerini alır. Ok, müşteri gibi daha genel bir aktör, işaret etmelidir. İlk bağlantı oluşturduğunuzda, daha özel aktörü işaret edin.  
  
 Özelleştirilmiş bir aktör diğer aktörler için kullanılabilir değil, kendi ek kullanım örnekleri olabilir.  
  
> [!CAUTION]
>  Döngüler aktörün kendisini genelleştiriliyor neden Genelleştirme ilişkilerinin yapmamanız gerekir. Döngüler, hatalara neden.  
  
### <a name="alternative-actor-icons"></a>Alternatif bir aktör simge  
 Özel simge yerine standart çubuk aktörün temsil etmek için kullanabilirsiniz. Örneğin, bir cihaz, Restoran, Banka ve benzeri benzer şekilde değiştirebilirsiniz.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>Bir aktör görünümünü değiştirmek için  
  
1.  Aktör sağ tıklayın ve ardından **özellikleri**.  
  
     **Özellikleri** penceresi görüntülenir.  
  
2.  Ayarlama **görüntü yolu** özelliğini bir görüntü dosyasının konumu.  
  
    -   .Gif, .jpg ve .bmp dahil olmak üzere çeşitli görüntü biçimlerinde kullanabilirsiniz.  
  
    -   Çözüm veya projeyi kaynak denetimine dahil ve böylece çözümü taşınamaz veya kopyalanamaz hala olduğunda bir dosya kullanın.  
  
3.  Bu görünüm diğer kullanım durumu diyagramlarındaki çoğaltmak için aktör kopyalayın ve başka bir diyagrama yapıştırın.  
  
    -   Görüntü değiştirmek, yalnızca belirli bir diyagram görünümünde uygulanır. Temel alınan model öğesi için geçerli değildir. Aktör UML Model Gezgini'nden başka bir diyagrama sürüklerseniz, standart çubuk görünür.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Aktörler ve kullanım örnekleri arasında Çeşitlilikler  
 Aktörün ve kullanım örneği arasındaki ilişkilendirmeyi gösterebilir bir *çoğulluk* her iki ucunda.  
  
 ![Bire bir aktör ile kullanım](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
>  Her ikisi de bir ilişkilendirmenin bir kullanım durumu diyagramı üzerinde çeşitliliği gizlenir **1**.  
  
 Varsayılan olarak, her çoğulluk, **1**. Model katı bir yorumu çokluğu 1, örneğin, yalnızca bir müşteri, her bir paket sıralamada karmaşıktır ve her müşteri aynı anda yalnızca bir Yemek Sipariş anlamına gelir.  
  
 Bu Çeşitlilikler değiştirebilirsiniz.  
  
 Örneğin:  
  
 ![Birçok çokluğunu gösteren kullanım](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
- Aynı sınıfın birkaç aktörleri kullanım örneği tek bir oluşumunu yer alabilir durumuna ilişkilendirmesine aktör sonunda çokluğu Ayarla ** 1... \\***.  
  
   Çizimde, bir veya daha fazla restoranlar aynı yemek siparişi yerine getirmesini yer alabilir.  
  
- Her aktör birkaç kez kullanım örneğinin aynı anda katılabilir göstermek için ilişkilendirme büyük/küçük harf kullanımı sonunda çokluğu Ayarla **\\***.  
  
   Çizimde, aynı anda birden fazla siparişi yerine getirmek için her bir restoran çalışabilir.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>Bir ilişkinin üzerinde Çeşitlilikler ayarlamak için  
  
1. İlişkilendirme sağ tıklayın ve ardından **özellikleri**.  
  
2. Ya da genişletin **ilk rol** veya **ikinci rol**.  
  
    *Rol* ilişkilendirmenin bir ucunda öğe anlamına gelir.  
  
3. Listeden seçerek Multiplicity özelliği ayarlayın:  
  
   - **1** bu rolün tam olarak bir örneğini belirtin. her bağlantıya katılan.  
  
   - **1..\\*** bu rol bir veya daha fazla örneği katıldığını her bağlantıyı belirtir.  
  
   - **0..1** katılım isteğe bağlı olduğunu belirtir.  
  
   - **\\*** Bu rolün sıfır veya daha fazla örneğini bağlantıya katılan durumu.  
  
> [!NOTE]
>  Birçok ekip varsayılan değer olan 1 çeşitliliği bırakarak kullanım örneği diyagramları çoğulluk bilgi yerleştirmeyin. Bunun yerine, kullanım örneklerini ayrı açıklamalarını bilgileri sağlar. Bu durumda, tüm kullanım örneği diyagramları Çeşitlilikler gizlenir.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Birden çok diyagram üzerinde bir aktör veya kullanım örneği kullanma  
 Aynı aktör Göster ve çeşitli diyagramlarda kullanım. Örneğin:  
  
-   Farklı diyagramlarda bir aktör dahil olduğu farklı kullanım örnekleri tanımlayabilirsiniz.  
  
-   Aktörler ve alt kullanım örneği ile ilişkili olduğu gösterilecek bir diyagram kullanın ve kullanım örneği dahildir ve genişletilmiş kullanım örneklerine nasıl yapılandırıldığını göstermek için başka bir diyagram kullanın.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Aynı aktör göstermek veya farklı diyagramlarda kullanım örneği  
  
1.  Aktör oluşturun veya bir diyagram üzerinde çalışması kullanın.  
  
2.  Başka bir kullanım durumu diyagramı oluşturun.  
  
3.  Aktörün sürükleyin ya da devre dışı kullanım **Model Gezgini** yeni diyagram üzerine.  
  
    > [!NOTE]
    >  Yeni Diyagram üzerinde bir aktör ve ilişkili olan bir kullanım örneği yerleştirirseniz, bunları arasındaki ilişki otomatik olarak yeni diyagramda görünecektir.  
  
##  <a name="Details"></a> Açıklayan ayrıntılı kullanım örnekleri  
 Kullanım örneği temsil eder:  
  
- Bir hedef sistem gibi kullanarak aktörün **yemek satın**; ve  
  
- Bir veya daha fazla *senaryoları*, diğer bir deyişle, test adımları gerçekleştirilen hedef gibi sürdürdüğünü: {**yemek siparişi, ödeme, teslim**}. Başarı senaryoların yanı sıra olabilir birkaç özel durum veya hata senaryoları gibi **kredi kartı reddedildi**.  
  
  Kullanım örneği farklı ayrıntı düzeyleri içinde tanımlanabilir. Erken bir aşamada tasarımının, yalnızca adı kullanım durumu diyagramı üzerinde yeterli olur.  Daha sonra senaryoları daha ayrıntılı açıklamaları yazılabilir.  
  
  Visual Studio Ultimate içinde bir kullanım örneği ayrı olarak veya birlikte kullanılabilecek çeşitli yollarla tanımlayabilirsiniz:  
  
- Kullanım örneği başka bir diyagramı veya diyagramları projedeki bağlayın.  
  
  -   Etkinlik diyagramı daha karmaşık bir işlem açıklayan yardımcı olan döngü, dal ve paralel iş parçacığı olduğu. Ayrıca, işlem bölümleri arasındaki veri akışını da gösterebilirsiniz. Daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
  -   Sıralı diyagram, farklı aktör arasındaki etkileşimler karmaşık bir dizi açıklayan yardımcı olur. Sistem her kullanım örneğine yanıt içinde neler göstermek için de kullanabilirsiniz. Daha fazla bilgi için [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
- Kullanım örneği bir OneNote sayfası, bölüm veya ayrıntılı kullanım örneğini açıklanacak paragraf bağlayın.  
  
- Kullanım örneği, metin, ekran görüntüleri ve benzeri kullanım örneği senaryolarının tanımlamak için kullandığınız bir Word belgesi için bağlayın. Daha fazla bilgi için [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Bir kullanım durumu diyagramı veya aynı çözüm içindeki dosya bağlamak için  
  
1.  Bir sıralı diyagram veya kullanım örneğinin bir senaryoyu göstermek üzere etkinlik diyagramı gibi bir diyagramı.  
  
2.  Kullanım durumu diyagramı geri dönün.  
  
3.  Çözüm Gezgini'nden boş bir kısmına kullanım durumu diyagramı diyagram veya dosya sürükleyin.  
  
4.  Yapıdan kullanım örneği bağlanırken bir **bağımlılık**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Bir çözüm dosyası gibi bir Word belgesi veya PowerPoint sunumu bağlamak için  
  
1.  Kullanım örneği senaryosu tanımlamak için metin, ekran görüntüleri, vb. kullanan bir belge yazma.  
  
2.  Belge ekleyin.  
  
    1.  Word belgesi çözümü olarak aynı Windows klasöre taşıyın.  
  
    2.  Çözüm Gezgini'nde çözüme sağ tıklayın, fareyle **Ekle**ve ardından **var olan öğe**.  
  
    3.  Word belgesine gelin ve tıklayın **Ekle**.  
  
         Word belgesi bir çözüm klasörü Çözüm Gezgini'nde görünür.  
  
3.  Çözüm Gezgini'nden kullanım durumu diyagramı boş bir kısmına Word belgesi sürükleyin.  
  
     Yeni Yapıt görünür.  
  
4.  Yapıdan kullanım örneği bağlanırken bir **bağımlılık**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Paylaşılan belge, OneNote öğesi veya web sayfası bağlamak için  
  
1.  Paylaşılan öğe URL'sini alın. Bu, örneğin, bir ağ dosya yolu başlangıç olabilir '\\\\', veya bir web sayfası veya Sharepoint URL'si başına 'http://' veya bir OneNote bölümüne bir bağlantı sayfa, paragraf başına ' onenote:'.  
  
2.  Araç kutusunda tıklayın **Yapıt** ve kullanım örneği diyagramı'ye tıklayın.  
  
3.  Yeni yapıt seçili yazın veya URL'sini yapıştırın **köprü** özelliği.  
  
> [!NOTE]
>  Diyagramı açın veya bağlandığı belge için yapıya çift tıklayabilirsiniz.  
  
### <a name="linking-use-cases-to-work-items"></a>Kullanım örnekleri, iş öğelerine bağlama  
 Projeniz kullanıyorsa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] ve [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], her kullanım örneği, bir iş öğesine bağlayabilirsiniz [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Bu bağlantılar yapmayı öğrenmek için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).  
  
 Şunları yapmanızı sağlar:  
  
-   Bağlantılı iş öğesi kullanım örneğini açıklar. Özellikle, projenizi Visual Studio, biçimsel işlem şablonu kullanıyorsa, bir kullanım durumu iş öğesine bağlayabilirsiniz. Bu iş öğesi türü, kullanım örneği senaryoları ve hedeflerinizi açıklamak için alan sağlar.  
  
-   Bağlantı test çalışmaları kullanım örneğine raporları alabilmeniz için geliştirilen ne kadar kod uygular kullanım örneği.  
  
-   Geliştirme çalışmanın ilerlemesini takip edebilmeniz, görevleri kullanım örneğine bağlayın.  
  
##  <a name="Structuring"></a> Kullanım örnekleri yapılandırma  
 Yalnızca birkaç önemli kullanım örneklerini sisteminizin davranışını açıklamak denemelisiniz. Her büyük kullanım örneği, bir aktör, bir ürün satın alma gibi veya, satıcının açısından, satış için ürünler sağlama elde eden ana hedefi tanımlar.  
  
 Bu hedefleri yaptıktan sonra temel hedefleri Çeşitlemeler ve her bir hedefe nasıl elde edildiğini hakkında daha fazla ayrıntıya gidebilirsiniz.  
  
 Kullanım örnekleri çok fazla ayrıntıya parçalama kaçının. Kullanım örnekleri, kullanıcıların deneyimini yerine kendi iç işleyişini sisteminizin üzeresiniz. Ayrıca, genel olarak, zaman içinde ince ayrıntılı kullanım örneklerini yapılandırma yerine kod erken çalışan sürümlerini oluşturmak için daha üretken bulacaksınız.  
  
 Büyük ve daha ayrıntılı kullanım örnekleri arasındaki ilişkileri bir kullanım durumu diyagramında özetleyebilir. Aşağıdaki bölümlerde bu açıklanmaktadır:  
  
-   [Bir kullanım örneği ile dahil etme ayrıntılarını gösterme](#Include)  
  
-   [Hedefleri Genelleştirme ile paylaşma](#Inheritance)  
  
-   [Değişken durumları genişletme ile ayrılması](#Extend)  
  
###  <a name="Include"></a> Bir kullanım örneği ile dahil etme ayrıntılarını gösterme  
 Kullanan bir **INCLUDE** ilişkisi, bir kullanım durumu gösterilecek başka ayrıntılarını bazılarını açıklar. Çizimde, **yemek siparişi** içerir **ödeme**, **seçin menü**, ve **seçin menü öğesi**. Her dahil, daha ayrıntılı kullanım durumlarından biri aktör veya aktörleri dahil olmak üzere kullanım örneğinin genel kaydetme amacına ulaşmanız için gerçekleştirmesi gereken bir adımdır. Ok, ayrıntılı ve dahil edilen kullanım örneğine işaret etmelidir.  
  
> [!CAUTION]
>  Bir kullanım örneği, kendisi de dahil olmak üzere neden ilişkileri döngüleri yapmamanız gerekir. Döngüler, hatalara neden olabilir.  
  
 Dahil olan kullanım örneklerini paylaşabilirsiniz. Örnekte, **yemek siparişi** ve **abone olmak için gözden geçirmeleri** iki dahil kullanım **ödeme**.  
  
 ![Kullanım durumları ile bölünmüş içerir](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 Daha sonra tasarlanan kullanım örneklerini eklenebilir böylece dahil olan kullanım örneği senaryoları ve hedef bağımsız olarak anlamlıdır.  
  
 Ayırma kullanım örneklerini dahil eden ve dahil edilen parçalar, aşağıdaki hedeflere ulaşmak kullanışlıdır:  
  
-   Ayrıntı farklı katmanlara kullanım örneği açıklamalarınızı yapılandırın.  
  
-   Paylaşılan senaryolarda farklı kullanım durumlarına yinelemekten kaçının.  
  
####  <a name="Steps"></a> Ayrıntılı adımlar sıralamasını tanımlama  
 Kullanım durumu diyagramı, hiçbir şey hakkında daha ayrıntılı adımlar gerçekleştirilmelidir siparişi ya da bunların her biri her zaman gerekli olup olmadığı hakkında diyor.  
  
 Sırasını yapmak için adımları temizleyin, kullanabileceğiniz bir **Yapıt** dahil olmak üzere ayrı bir belge kullanım örneği eklenecek. Aşağıdaki örnekte, bir etkinlik diyagramı siparişe yemek kullanım örneğine bağlı. Alternatif olarak, adımlar ve ekran görüntüleri bir dizi listesini içeren bir metin belgesi kullanabilirsiniz. Daha fazla bilgi için [kullanım örneklerini açıklayan ayrıntılı](#Details).  
  
 Etkinlik diyagramı kullandığınızda bu adlandırma kuralları dikkat edin:  
  
- Tüm etkinlik adı dahil olmak üzere kullanım örneği ile aynıdır.  
  
- Etkinlik diyagramı eylemleri, kullanım örnekleri dahil olarak aynı ada sahip.  
  
  Daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
  ![Bağlı etkinlik diyagramında gösterilen kullanım örneği adımları](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
###  <a name="Inheritance"></a> Hedefleri Genelleştirme ile paylaşma  
 Genelleştirme ilişkisine gösteren kullanılacağını bir *özelleştirilmiş* kullanım örneği olan başka bir ifade hedeflere ulaşmak için belirli bir şekilde *genel* kullanım örneği. Açık ok ucu daha genel kullanım örneğine işaret etmelidir.  
  
 ![Genelleştirme ilişkisine gösteren kullanım](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Örneğin, **ödeme** genelleştirir **tarafından kredi kartıyla ödeme** ve **nakit göre ödeme**.  
  
> [!CAUTION]
>  Aktörün kendisi genelleştiriliyor neden Genelleştirme ilişki, döngü yapmamanız gerekir. Döngüler, hatalara neden.  
  
 Özelleştirilmiş kullanım örnekleri, sisteminizi aynı kaydetme amacına ulaşmanız farklı yollar gösterir yardımcı olabilir.  
  
 Özelleştirilmiş kullanım örnekleri hedefleri devralmak için kabul edilir ve aktörler genel kullanım örneği. Genel kullanım örneği senaryoları kendi olması gerekmez; kendi uzmanlıkları hedeflerine ulaşmak için farklı yollar açıklanmaktadır.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Ortak yeniden düzenlemenin iki veya daha fazla kullanım  
  
1.  Adı yeni genel kullanım örneği ve oluşturun.  
  
2.  Oluşturma bir **Genelleştirme** yeni genel kullanım örneğini işaret eden büyük bir ok ile ilişkisi.  
  
    1.  Tıklayın **Genelleştirme** araç.  
  
    2.  Özelleştirilmiş kullanım örneğine tıklayın (**tarafından kredi kartıyla ödeme** örnekte).  
  
    3.  Genel kullanım örneğine tıklayın (**ödeme** örnekte).  
  
3.  Özel durumlara ilişkin hedeflerini açıklanan, genel bir açıklama ortak parçalara kullanım taşıyın.  
  
4.  Özelleştirilmiş kullanım örnekleri arasında paylaşılan aktörler için genel kullanım örneği taşınabilir.  
  
###  <a name="Extend"></a> Değişken durumları ayrılması ile genişletme  
 Bir kullanım örneği, belirli koşullar altında başka bir kullanım örneği işlevsellik ekleyen olduğunu göstermek için bir genişletme bağlantıyı kullanın. Oku, ana ve genişletilmiş kullanım örneğine işaret etmelidir.  
  
 ![Başka bir genişleyen bir kullanım örneği](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
>  Aktörün kendisi genelleştiriliyor neden olan ilişkilerini genişletmek döngüleri yapmamanız gerekir. Döngüler, hatalara neden.  
  
 Örneğin, **oturum açma** kullanım örneği tipik bir Web sitesinin içerebilir **yeni kullanıcı Kaydet** - ancak yalnızca, kullanıcı zaten bir hesabınız yok.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Kullanım örneği ana ve genişletme parçalara ayırmak için  
  
1. Yeni uzantı adı kullanım örneği ve oluşturun.  
  
2. Oluşturma bir **Genişlet** genişletilmiş kullanım örneğine işaret eden bir ok ile ilişkisi.  
  
   1.  Tıklayın **Genişlet** araç.  
  
   2.  Genişletme kullanım örneğine tıklayın (**yeni kullanıcı Kaydet** örnekte).  
  
   3.  Genişletilmiş kullanım örneğine tıklayın (**oturum açma** örnekte).  
  
       > [!NOTE]
       >  Diyagramda Genişlet ilişkileri döngüsünü oluşturmaktan kaçının. Bu, kendisinin bir uzantı bir kullanım örneği için doğru değil.  
  
3. Genişletilmiş kullanım örneği senaryoları zaten oluşturduysanız, uzantının senaryoya ilgili adımları taşıyın.  
  
4. Uzantı açıklamasını (**yeni kullanıcı Kaydet** örnekte) bu gerçekleşir ana kullanım örneği senaryoları ve hangi koşullar altında ayrıntıları burada içermelidir. Bunu ana durumun açıklaması değiştirme olarak düşünün.  
  
   Uzantı kullanım örneği, aksi durumda ana kullanım örneği senaryolarının parçası olacak senaryo adımları temsil eder. Senaryo ve hedef uzantısı her zaman ana kullanım örneği bağlamında bu nedenle bağımsız olarak yararlı olmak zorunda değildir okunacak.  
  
   Uzantıları ayırmak bu durumlar açıklamak için yararlı olabilir:  
  
-   Yalnızca uzantı kullanım örneğine katılan olan ek aktör vardır. Örneğin, bir yönetici, bir müşterinin kayıt Web sitesinde onaylamak için gereklidir.  
  
-   Ayrı bir alt uzantısı kullanım örneği ile ilgilenecektir.  
  
-   Bu uzantı yalnızca sistem belirli sürümlerinde kullanıma sunulacak. Her sürüm ayrı bir alt kullanım örneği diyagramı sisteminde olarak gösterebilirsiniz.  
  
##  <a name="Subsystems"></a> Alt sistem sınırları kullanma  
 Hangi kullanım göstermek için alt sınır olan sisteminizi kapsamında kullanın.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>Bir alt sistem sınırının çizmek için  
  
1. Araç kutusunda tıklayın **alt**, diyagram'ye tıklayın.  
  
    Bir alt diyagramda görünür.  
  
2. Boyutunu ayarlamak için alt sistemi köşelerini sürükleyin.  
  
3. Var olan kullanım örneklerini içine veya dışına içindekileri ayarlamak için alt sistemi sürükleyin.  
  
   \- veya -  
  
   Doğrudan alt sistemde yeni bir kullanım örneği oluşturmak için tıklayın **kullanım örneği** araç kutusundan alt sistemin içine'ye tıklayın.  
  
> [!NOTE]
>  **Konuları** kullanım özelliği bulunan içinde hangi alt sistemi belirtir.  
  
### <a name="use-cases-outside-the-system-scope"></a>Sistem kapsamı dışında kullanım örnekleri  
 İş bir parçasıdır ancak ile geliştirdiğiniz sistem tarafından ele değil diyagram kullanım örneklerini eklemek genellikle yararlıdır. Bu, geliştiricilerin iş bağlamında anlamasına yardımcı olur. Örneğin, Restoran ve müşteri aktörleri içeren bir kullanım örneği, ancak sorumluluk, yemek siparişi Web Sitesi'nin dışında Yemek Dağıt gösterilebilir.  
  
### <a name="multiple-subsystems"></a>Birden çok alt sistemi  
 Çeşitli alt sistem sınırları nasıl farklı kullanım durumları sistemin farklı bileşenler tarafından çözüldüğünü göstermek için oluşturabilir. Örneğin, **Restoran Değerlendirmesi Ekle** ile ayrı forum Web sitesinde ele alınabilir. Bir kullanım durumu diyagramı kullanıcıya görünür nedir ile uğraşmak unutmayın. Sistemde iç bölme çalışmanın açıklamak isterseniz, bir bileşen diyagramı kullanmayı göz önünde bulundurun.  
  
### <a name="system-versions"></a>Sistemi sürümleri  
 Farklı bir alt sistem sınırları sisteminin farklı sürümleri göstermek için kullanabilirsiniz. Örneğin, ödeme kullanım örneği, Web sitesi sürüm 2'de sunulan ancak sürüm 1'de bu sistem siparişlerini yapmalarına yardımcı gelir değil. Ancak, bunlar doğrudan restorana ödeme gerekir.  
  
 Kullanım **bağımlılık** farklı sürümleri veya türevleri temsil eden alt sistemleri bağlamak için ilişkileri.  
  
 ![Alt sisteminin farklı sürümleri göster](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)   
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)   
 [Video: Kullanım örneklerine özelliklerini düzenleme](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)



