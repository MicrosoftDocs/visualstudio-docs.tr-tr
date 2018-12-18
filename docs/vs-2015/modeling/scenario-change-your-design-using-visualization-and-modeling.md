---
title: 'Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme | Microsoft Docs'
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
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4dface8e157e44aa09b271446dba68b2779d0a6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745766"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin kullanarak Görselleştirme ve modelleme araçları Visual Studio tarafından Kullanıcıların ihtiyaçlarını karşıladığından emin olun. Birleşik Modelleme Dili (UML) diyagramları, kod Haritaları, katman diyagramları ve sınıf diyagramları gibi araçları kullanın:  
  
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
  
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)  
  
##  <a name="ScenarioOverview"></a> Senaryoya genel bakış  
 Bu senaryo, iki hayali şirketin yazılım geliştirme proje süreçlerinden açıklar: Şimdi Akşam Yemeği ve Lucerne Publishing. Şimdi Akşam Yemeği Seattle'da Web tabanlı bir yiyecek teslim hizmet sağlar. Müşteriler, yemek siparişi ve Şimdi Akşam Yemeği Web sitesinde bunlar için ödeme yaparsınız. Siparişler, ardından teslimi için üzere uygun yerel restoranlara gönderilir. Lucerne Publishing, New York, şirketinizin Web üzerinde ve dışında birçok müessese çalıştırır. Örneğin, müşterilerin restoran görüşlerini gönderebileceği bir Web sitesini çalıştırır.  
  
 Lucerne, kısa süre önce Dinner Now girişimini satın ve aşağıdaki değişiklikleri yapmak istiyor:  
  
- Şimdi Akşam Yemeği ne Restoran Eleştiri yeteneklerini ekleyerek Web sitelerinin bütünleştirin.  
  
- Dinner Now ödeme sistemini Lucerne sistemiyle değiştirin.  
  
- Şimdi Akşam Yemeği hizmetini bölge çapında genişletin.  
  
  Şimdi Akşam Yemeği SCRUM ve eXtreme Programming kullanır. Çok yüksek sınav kapsamı ve çok az desteklenmeyen kod sahiptirler. Bunlar küçük oluşturma ancak çalışan sürümlerini bir sistem ve ardından işlevsellik ekleyerek artımlı olarak riskleri en aza. Bunlar, kısa ve sık yinelemeler üzerinden kodu geliştirin. Bu bunları değişimi daha güvenle benimsemelerini, kodu sıkça yeniden düzenlemelerini ve "büyük tasarım" önlemenize olanak sağlar.  
  
  Lucerne, bazıları 40 yıldan eski olan sistemlerin çok büyük ve karmaşık bir koleksiyonunu tutar. Eski kod kapsamı ve karmaşıklık nedeniyle değişiklik yapma konusunda çok dikkatli değildirler. Bunlar, ayrıntılı çözümleri tasarlamayı ve tasarım ve geliştirme aşamasında oluşan değişiklikleri belgelemek için belgelemeyi daha titiz bir geliştirme işlemini izleyin.  
  
  Her iki ekip, kullanıcıların gereksinimlerini karşılayan sistemler geliştirmelerine yardımcı olmak için Visual Studio'da modelleme diyagramları kullanın. Bunlar Team Foundation Server diğer araçların yanı sıra bunları planlamak, düzenlemek ve işlerini yönetmek için kullanın.  
  
  Team Foundation Server hakkında daha fazla bilgi için bkz:  
  
- [İş planlama ve izleme](#PlanningTracking)  
  
- [Sınama, doğrulama ve güncellenmiş kodu iade etme](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a> Mimari ve modelleme diyagramları yazılım geliştirmede rolleri  
 Aşağıdaki tablo bu araçların yazılım geliştirme yaşam döngüsünün çoklu ve çeşitli aşamaları sırasında oynayabileceği roller açıklanmıştır:  
  
||**Kullanıcı gereksinimlerini modelleme**|**İş Süreci Modelleme**|**Sistem Mimarisi ve tasarımı**|**Kodu görselleştirme ve keşfetme**|**Doğrulama**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Kullanım örneği diyagramı (UML)|√|√|||√|  
|Etkinlik diyagramı (UML)|√|√|√||√|  
|Sınıf diyagramı (UML)|√|√|√||√|  
|Bileşen diyagramı (UML)|√|√|√||√|  
|Sıralı diyagram (UML)|√|√|√||√|  
|Etki alanına özgü dil (DSL) diyagramı|√|√|√|||  
|Katman diyagramı, katman doğrulama|||√|√|√|  
|Kod Haritası|||√|√|√|  
|Sınıf Tasarımcısı (kod tabanlı)||||√||  
  
 UML diyagramları ve katman diyagramları çizmek için varolan bir çözüm ya da yeni bir parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramları modelleme projesinin içinde oluşturulmalıdır. UML diyagramlarındaki öğeler ortak bir modelin bir parçasıdır ve UML diyagramları Bu modelin görünümleridir. Katman diyagramındaki öğeler modelleme projesinin içinde bulunur, ancak ortak modelde saklanmaz. Kod haritaları ve .NET sınıf diyagramları koddan oluşturulan modelleme projesinin dışında yer alır.  
  
 Bkz.  
  
- [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
  Mimarinin alternatif görünümlerini göstermek için birden çok aynı modelden belirli öğeleri yeniden kullanabilir veya farklı diyagramlarda. Örneğin, bir oyuncu olarak çalışması bir bileşen başka bir bileşen diyagramı veya bir sıralama diyagramına sürükleyebilirsiniz. Bkz: [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
  Her iki ekip de geliştirme aşamasındaki kodun tasarım ile tutarlı kalmasından emin olmak için katman doğrulaması kullanın.  
  
  Bkz.  
  
- [Kodun tasarımla tutarlılığını koruma](#ValidatingCode)  
  
- [Mantıksal mimarisi açıklanmıştır: katman diyagramları](#DescribeLayers)  
  
- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)  
  
  > [!NOTE]
  >  Visual Studio'nun bazı sürümlerinin, Görselleştirme ve modelleme için katman doğrulamayı ve UML diyagramları ile kod haritaları ve salt okunur sürümlerini destekler. Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="UnderstandingCommunicating"></a> Anlama ve sistem hakkındaki bilgileri iletişim kurma  
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
  
  Ekipler yaptıkları değişiklikleri kaydetmeden önce katman doğrulamayı ve otomatik testleri içeren yapıları çalıştırarak kodu testlere ve tasarıma karşı doğrulayın. Bu, güncelleştirilmiş kod değil tasarımıyla çakışma yaratmadığından ve daha önce çalışma işlevselliği sonu emin olun yardımcı olur.  
  
  Bkz.  
  
- [İş sürecinde sistemin rolünü anlamak](#UnderstandingBPMandSystemDesign)  
  
- [Yeni veya güncelleştirilmiş kullanıcı gereksinimleri açıklanır](#DescribingURM)  
  
- [Modellerden testler oluşturma](#CreatingTests)  
  
- [Varolan sistem değişikliklerini tanımlama](#DeterminingChanges)  
  
- [Kodun tasarımla tutarlılığını koruma](#ValidatingCode)  
  
- [Modelleri oluşturma ve kullanma hakkında genel ipuçları](#GeneralTips)  
  
- [İş planlama ve izleme](#PlanningTracking)  
  
- [Sınama, doğrulama ve güncellenmiş kodu iade etme](#TestValidateCheckInCode)  
  
###  <a name="UnderstandingBPMandSystemDesign"></a> İş sürecinde sistemin rolünü anlamak  
 Lucerne, Dinner Now iş süreci hakkında daha fazla bilgi istiyor. Dinner Now sitesiyle daha kolay açıklığa kavuşturmak için aşağıdaki diyagramları oluştururlar:  
  
|**Diyagramı**|**Açıklar**|  
|-----------------|-------------------|  
|*Kullanım örneği diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|-Şimdi Akşam Yemeği sisteminin desteklediği etkinlikleri<br />-İnsanlar ve etkinlikleri gerçekleştiren dış sistemler<br />-Tüm etkinlikleri destekleyen ana bileşenleri sistem<br />-Geçerli sistemin kapsamı dışında Örneğin, yiyecek dağıtımı bölümleri iş sürecinin|  
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Bir müşteri bir sipariş oluştururken ortaya çıkan adımların akışı|  
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|İş varlıklarını ve tartışmalar ve bu varlıkları arasındaki ilişkileri kullanılan terimler. Örneğin, sıralama ve menü öğesi bu senaryoda sözlüğün parçasıdır.|  
  
 Örneğin, Lucerne Şimdi Akşam Yemeği Web sitesinde yapılan ve onları görevleri anlamak için aşağıdaki kullanım çalışması diyagramı oluşturur:  
  
 ![UML Kullanım durumu diyagramı](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **UML Kullanım durumu diyagramı**  
  
 Bir müşteri Şimdi Akşam Yemeği Web sitesinde bir sipariş oluşturduğunda aşağıdaki etkinlik diyagramı adımların akışını tanımlar. Bu sürümde, yorum öğeleri rolleri tanımlar ve satırlar *Kulvarlar*, adımları rol bakımından Düzenleyen:  
  
 ![UML etkinlik diyagramı](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **UML etkinlik diyagramı**  
  
 Aşağıdaki sınıf diyagramı sipariş işlemlerine katılan varlıkları tanımlar:  
  
 ![UML sınıf diyagramı](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **UML sınıf diyagramı**  
  
###  <a name="DescribingURM"></a> Yeni veya güncelleştirilmiş kullanıcı gereksinimleri açıklanır  
 Lucerne, işlevi, Şimdi Akşam Yemeği sisteminin ekleyebilirsiniz, böylece müşteriler, okuma ve Restoran katkıda istiyor. Bunlar aşağıdaki diyagramları güncelleştirin, böylece açıklamak ve tartışmak ile Şimdi Akşam Yemeği yeni gereksinimi:  
  
|**Diyagramı**|**Açıklar**|  
|-----------------|-------------------|  
|*Kullanım örneği diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|"Bir restoran incelemesi yazın" için yeni bir kullanım örneği|  
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Bir müşteri bir restoran incelemesi yazmak istediğinde oluşan adımlar|  
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Bir incelemeyi saklamak için gerekli verileri|  
  
 Örneğin, aşağıdaki kullanım çalışması diyagramı yeni gereksinimi göstermek için yeni bir "İnceleme Yaz" kullanım çalışması içermektedir. Bunu daha kolay tanımlanmak için diyagramda turuncu ile vurgulanmıştır:  
  
 ![UML Kullanım durumu diyagramı](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **UML Kullanım durumu diyagramı**  
  
 Aşağıdaki etkinlik diyagramı yeni kullanım örneğindeki adımların akışını tanımlamak için turuncu renkli yeni öğeler içerir:  
  
 ![UML etkinlik diyagramı](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **UML etkinlik diyagramı**  
  
 Böylece takımlar detayları tartışabilirler aşağıdaki sınıf diyagramı yeni bir inceleme sınıfı ve kendi diğer sınıflarla ilişkilerini içerir. Bir müşteri ya da Restoran birden fazla değerlendirme alabilir dikkat edin:  
  
 ![UML sınıf diyagramı](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **UML sınıf diyagramı**  
  
###  <a name="CreatingTests"></a> Modellerden testler oluşturma  
 Her iki ekip, değişiklik yapmadan önce test kümesinin tamamını sistem ve bileşenleri için ihtiyaç duydukları olduğunu kabul etmiş olursunuz. Lucerne sistem ve bileşen düzeyinde testler yapan uzman bir ekibe sahiptir. Bunlar Dinner Now öğesi tarafından oluşturulan testleri yeniden kullanır ve UML diyagramları kullanarak bu testleri düzenler:  
  
- Her kullanım örneği, bir veya birden çok test tarafından temsil edilir. Test çalışması kullanım durumu diyagramı bağlantısı üzerindeki öğeleri Team Foundation Server'da iş öğeleri.  
  
- Bir etkinlik veya sistem düzeyi dizi diyagramı üzerindeki akış en azından bir test bağlantılıdır. Test takımı, sistematik olarak etkinlik diyagramı aracılığıyla olası her yolun test etmenizi emin olur.  
  
- Testleri tanımlamakta kullanılan terimler kullanım çalışması, sınıf ve etkinlik diyagramları tarafından tanımlanan koşullara dayanır.  
  
  Gereksinimler değiştikçe ve diyagramlar o değişiklikleri yansıtacak şekilde güncelleştirilir, testler de güncellenir. Bir gereksinim, yalnızca testler başarılı getirildiğinin kabul edilir. Mümkün ve pratik olduğunda, testler tanımlanır ve uygulama başlamadan önce UML diyagramlarına dayandırılır.  
  
  Bkz.  
  
- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)  
  
- [UML modelinizi doğrulama](../modeling/validate-your-uml-model.md)  
  
###  <a name="DeterminingChanges"></a> Varolan sistem değişikliklerini tanımlama  
 Şimdi Akşam Yemeği yeni gereksinimi Karşılama maliyetini tahmin etmek gerekir. Bu kısmen değişikliğin sistemin diğer bölümlerini etkileme derecesine bağlıdır. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri bu eşlemeleri ve diyagramları mevcut koddan oluşturur:  
  
|**Harita veya diyagram**|**Gösterir**|  
|------------------------|---------------|  
|*Kod Haritası*<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Gözat ve kod haritaları bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />-   [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Bağımlılıklar ve diğer koddaki ilişkileri.<br /><br /> Örneğin, Şimdi Akşam Yemeği derlemeler ve bağımlılıklarına bir genel bakış için derleme kod haritaları gözden geçirilmesiyle başlayabilir. Ad alanlarını ve sınıfları bu derlemelerde bulunan keşfetmek için haritalarını halinde inebilir.<br /><br /> Şimdi Akşam Yemeği aynı zamanda belirli alanları ve diğer tür kod içindeki ilişkileri keşfetmek için maps oluşturabilirsiniz. Bunlar, bulmak ve onları ilgilendiren ilişkileri ve alanları seçmek için Çözüm Gezgini'ni kullanın.|  
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Kod üzerinde varolan sınıflar|  
  
 Örneğin, geliştirici bir kod Haritası oluşturur. Filiz kapsamını yeni senaryodan etkilenecek alanlara odaklanmak için ayarlar. Bu alanlar seçilir ve harita üzerinde vurgulanır:  
  
 ![Namespace bağımlılık grafiği](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Namespace kod Haritası**  
  
 Geliştirici, kendi sınıfları, yöntemleri ve ilişkileri görmek için seçilen ad alanlarını genişletir:  
  
 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Görünür gruplar arası bağlantılara sahip genişletilmiş ad alanı kod Haritası**  
  
 Geliştirici etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Bunları, yeniden oluşturma yaptığınız gibi her değişikliğin etkilerini görmek için her bir değişiklikten sonra kod eşlemeleri. Bkz: [kodu görselleştirme](../modeling/visualize-code.md).  
  
 Sistemin bileşenler veya etkileşimler gibi öbür parçalarına değişiklikleri açıklamak için takım bu öğeleri panolara çizebilir. Ayrıntılar yakalanan, yönetilen ve her iki takım tarafından anlaşılabilsin diye, bunlar aşağıdaki diyagramları Visual Studio'da çizebilir:  
  
|**Diyagramları**|**Açıklar**|  
|------------------|-------------------|  
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Sistem bir müşterinin yeniden bir restorana sipariş isteyen bir inceleme yazmasını istediğinde ortaya çıkan adımların akışı.|  
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Mantıksal sınıflar ve ilişkileri. Örneğin, yeni bir sınıf tanımlamak için eklenen bir **gözden geçirme** ve diğer varlıklarla ilişkilerini gibi **Restoran**, **menü**, ve **müşteri**.<br /><br /> İncelemeler, bir müşteri ile ilişkilendirmek için sistemin müşteri detaylarını saklaması gerekir. Bir UML sınıf diyagramı, bu ayrıntıların açıklanmasına yardımcı olabilir.|  
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Kod üzerinde varolan sınıflar.|  
|*Bileşen diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|Sistemin Şimdi Akşam Yemeği Web sitesi ve arabirimlerini gibi üst düzey bölümleri. Bu arabirimler nasıl bileşenleri her biri diğerine kullandıkları ve sağladıkları hizmetler veya yöntemler etkileşim tanımlar.|  
|*Sıralı diyagram (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|Örnekler arasındaki etkileşimler dizesi dizisi.|  
  
 Örneğin, aşağıdaki bileşen diyagramı Şimdi Akşam Yemeği Web sitesi bileşeninin bir parçasıdır yeni bileşeni gösterir. ReviewProcessing bileşeni değerlendirmeleri oluşturmaya ilişkin işlevselliği ele alır ve turuncu renkte vurgulanarak görüntülenir:  
  
 ![UML bileşen diyagramı](../modeling/media/uml-internal.png "UML_Internal")  
  
 **UML bileşen diyagramı**  
  
 Aşağıdaki sıralama diyagramı Şimdi Akşam Yemeği Web sitesi müşterinin önce bir restorana sipariş verip vermediğini denetlerken oluşan etkileşimler dizisini gösterir. True ise, ardından kullanıcıdan restorana gönderilecek ve Web sitesi tarafından yayımlanacak bir inceleme oluşturmasını ister:  
  
 ![UML sıralı diyagramı](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **UML sıralı diyagramı**  
  
###  <a name="ValidatingCode"></a> Kodun tasarımla tutarlılığını koruma  
 Şimdi Akşam Yemeği güncelleştirilen kodun tasarım ile tutarlı kalmasını sağlayın. Bunlar sistemde işlevselliğe ilişkin katmanları açıklamak, bu katmanlara bunları ve ilişkilendirme çözüm yapılarına izin verilen bağımlılıkları belirtin ve katman diyagramları oluşturun.  
  
|**Diyagramı**|**Açıklar**|  
|-----------------|-------------------|  
|*Katman diyagramı*<br /><br /> Bkz.<br /><br /> -   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Bir katman diyagramı düzenler ve yapılar eşleyen bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm adı verilen soyut gruplarla *katmanları*. Bu katmanlar, roller, görevlerin veya bu yapıların sistemde gerçekleştirdiği işlevleri tanımlayın.<br /><br /> Katman diyagramları, sistemin amaçlanan tasarımını açıklayan ve tasarımda gelişen kodu doğrulamak için kullanışlıdır.<br /><br /> Katmanlar oluşturmak için Çözüm Gezgini, kod Haritaları, sınıf görünümü ve Nesne Tarayıcısı'ndan öğeleri sürükleyin. Yeni Katmanlar çizmek için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayın.<br /><br /> Varolan bağımlılıkları görüntülemek için katman diyagramı yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**. Hedeflenen bağımlılıklarını belirtmek için yeni bağımlıklar çizin.|  
  
 Örneğin, aşağıdaki katman diyagramı katmanlar ve her bir katman ile ilişkili yapıların sayısı arasındaki bağımlılıkları açıklanmaktadır:  
  
 ![Katman diyagramı tümleşik ödeme sisteminin](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Katman diyagramı**  
  
 Kod geliştirme sırasında tasarımla çakışmaların gerçekleşmez emin olmak için katman doğrulaması yapılar takımlar kullanır, Team Foundation Build üzerinde çalıştırılır. Bunlar ayrıca işlemlerini iade etme işleminde katman doğrulama gerektirecek şekilde özel bir MSBuild görevi oluşturur. Bunlar doğrulama hatalarını toplamak için yapı raporları kullanır.  
  
 Bkz.  
  
-   [Derleme işleminizi tanımlama](http://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Değişiklikleri doğrulamak için geçişli iade derleme işlemi kullanın](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Yapı işlemi şablonunuzu özelleştirme](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a> Modelleri oluşturma ve kullanma için genel ipuçları  
  
- Çoğu diyagram birbirine satırlarla bağlı düğümleri oluşur. Her diyagram türü için araç kutusu farklı türde düğümler ve satırlar sağlar.  
  
   Araç kutusunu açmak için **görünümü** menüsünü tıklatın **araç kutusu**.  
  
- Bir düğüm oluşturmak için araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri, varolan düğümlere sürüklenmelidir. Örneğin, bir bileşen diyagramı üzerinde varolan bir bileşene yeni bir bağlantı noktası eklenmelidir.  
  
- Bir çizgi veya bir bağlantı oluşturmak için araç kutusunda uygun aracı tıklayın, kaynak düğümü tıklayın ve sonra hedef düğümü tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. Olası kaynak ya da hedef üzerinde işaretçiyi getirdiğinizde, işaretçi bir bağlantı oluşturup oluşturamayacağınızı gösterir.  
  
- UML diyagramları üzerinde öğeler oluştururken, bunları ortak bir modele de eklemiş olursunuz. Modelleme projesindeki UML diyagramları aynı modelin görünümleridir. Ortak modelde saklanmaz olsa bile bir katman diyagramındaki öğeler modelleme projesinin parçasıdır.  
  
   Modeli görmek için **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
- Bazı durumlarda, belirli öğeleri sürükleyebilirsiniz **UML Model Gezgini** UML diyagramına. Aynı modelin içindeki bazı öğeler üzerinde birden çok kullanılabilir veya göstermek için farklı diyagramlar diğer görünümleri mimarisi. Örneğin, bir bileşen başka bir bileşen diyagramı ya da bir oyuncu olarak kullanması için bir sıralama diyagramına sürükleyebilirsiniz.  
  
- Visual Studio UML 2.1.2'yi destekler. Bu genel bakış, bu sürümdeki UML diyagramlarının yalnızca önemli özelliklerini açıklar ancak UML ve kullanım alanlarını anlatan bir çok kitap mevcuttur.  
  
  Bkz: [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).  
  
###  <a name="PlanningTracking"></a> İş planlama ve izleme  
 Planlama, yönetme ve çalışmayı daha kolay izlemek için visual Studio modelleme diyagramlarını Team Foundation Server ile tümleşiktir. Her iki ekip, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmasını tahmin etmek için modelleri kullanır. Lucerne oluşturur ve bağlantılar Team Foundation Server iş kullanım durumları veya bileşenleri gibi model öğelere öğeleri. Bu, ilerlemelerini izlemeye ve çalışmalarının izini kullanıcı gereksinimlerine izleme yardımcı olur. Bu değişiklikleri bu gereksinimleri karşılamaya devam ettiğinden emin olun yardımcı olur.  
  
 Çalışma ilerledikçe, kendi görevlere harcadıkları süreyi yansıtacak şekilde onların iş öğelerini takımlar güncelleştirme. Ayrıca izlemek ve rapor aşağıdaki Team Foundation Server özelliklerini kullanarak iş durumu:  
  
- Günlük *ilerleme raporları* bunlar planlanmış çalışmaları beklenen süre tamamlayıp tamamlayamayacaklarını gösteren. Onlar, hata aşamalarını izlemek için Team Foundation Server'dan başka benzer raporlar oluşturur.  
  
- Bir *yineleme çalışma* izlemek ve üyeleri arasındaki iş yükünü dengelemek takıma yardımcı olmak üzere Microsoft Excel kullanan. Bu çalışma sayfası Team Foundation Server'a bağlanır ve düzenli ilerleme toplantıları sırasında tartışma odağı sağlar.  
  
- A *geliştirme Panosu* ekibi önemli proje bilgileri hakkında bilgilendirmek için Office Project kullanan.  
  
  Bkz.  
  
- [Visual Studio Team Services veya Team Foundation Server kullanarak iş izleme](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
- [Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)  
  
- [Grafikler, panolar ve Visual Studio ALM için raporlar](http://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
- [Tasks using Project ve biriktirme listesi oluşturma](http://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a> Sınama, doğrulama ve kodu iade etme  
 Takımlar her bir görevi tamamladıkça, Team Foundation sürüm denetiminde kendi kodlarını kontrol edin ve unuturlarsa Team Foundation Server'dan anımsatıcılar alma. Takımlar, birim testleri ve katman doğrulama kodu kendi test çalışmalarına ve tasarıma karşı doğrulamak için Team Foundation Server kendi İadelerini kabul önce çalıştırın. Bunlar yapıları çalıştırmak için Team Foundation Server kullanmak otomatik birim testleri ve düzenli olarak katman doğrulama. Bu, kodun aşağıdaki ölçütleri karşıladığından emin olun yardımcı olur:  
  
- Çalışır.  
  
- Önceden çalışan kodu kesmez.  
  
- Tasarım ile çakışmaz.  
  
  Şimdi Akşam Yemeği neredeyse tümü halen uygulanabilir olduğu için Lucerne bunları yeniden kullanabilir, otomatik testleri büyük koleksiyonu vardır. Lucerne Ayrıca bu testleri geliştirebilir ve yeni işlevsellikler yenilerini ekleyin. Hem de Visual Studio el ile testler çalıştırmak için kullanın.  
  
  Kodun tasarıma uymasını sağlamak için takımlar yapılarını katman doğrulamasını içerecek şekilde Team Foundation yapısı içinde yapılandırın. Herhangi bir çakışma oluşursa, ayrıntılarla bir rapor oluşturulur.  
  
  Bkz.  
  
- [Uygulamayı test etme](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)  
  
- [Sürüm denetimi kullanın](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
- [Uygulamayı oluşturun](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="UpdatingSystem"></a> Güncelleştirme kullanarak sistem Görselleştirme ve modelleme  
 Lucerne ve Dinner Now ödeme sistemleri bütünleştirilmelidir. Aşağıdaki bölümlerde, modelleme diyagramları Visual Studio'da bu görevi yerine getirmede yardımcı gösterilmektedir:  
  
- [Kullanıcı gereksinimlerini anlayın: kullanım örneği diyagramları](#UnderstandUseCases)  
  
- [İş sürecini anlayın: etkinlik diyagramları](#UnderstandActivities)  
  
- [Sistem yapısı açıklanmıştır: Bileşen diyagramları](#DescribeComponents)  
  
- [Etkileşimler açıklanmıştır: sıralı diyagramlar](#DescribeSequence)  
  
- [Varolan kodu görselleştirin: Kod haritaları](#VisualizeCode)  
  
- [Bir türler sözlüğü tanımlayın: sınıf diyagramları](#DefineClasses)  
  
- [Mantıksal mimarisi açıklanmıştır: katman diyagramları](#DescribeLayers)  
  
  Bkz.  
  
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)  
  
- [Kodu görselleştirme](../modeling/visualize-code.md)  
  
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)  
  
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)  
  
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)  
  
###  <a name="UnderstandUseCases"></a> Kullanıcı gereksinimlerini anlayın: kullanım örneği diyagramları  
 Kullanım örneği diyagramları bir sistemin desteklediği ve bu etkinlikleri kimin gerçekleştirdiğini özetler. Lucerne bir kullanım durumu diyagramı aşağıdaki Dinner Now sistemi hakkında bilgi edinmek için kullanır:  
  
- Müşteriler sipariş oluşturur.  
  
- Lokantalar siparişleri alır.  
  
- Harici Ödeme İşlemci Şimdi Akşam Yemeği Ödeme sistemi ödemeleri doğrulamak için kullandığı, ağ geçidi, Web sitesi için kapsam dışındadır.  
  
  Diyagramda ayrıca bazı temel daha küçük ayrıldığını kullanma gösterilmektedir. Lucerne, kendi ödeme sistemini kullanmak istiyor. Bunlar, İşlem Ödemesi kullanım örneğini değişiklik gerektirdiğini belirtmek için farklı bir renkte vurgular:  
  
  ![Bir kullanım durumu diyagramında İşlem Ödemesi vurgulama](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
  **Kullanım durumu diyagramında İşlem Ödemesi vurgulama**  
  
  Geliştirme süresini kısa ise takım, müşterilerin restoranlara doğrudan ödeme yapmalarına izin vermek isteyip istemediklerini konuşmalıdır. Bu göstermek için bunlar İşlem Ödemesi kullanım örneğini Dinner Now sistem sınırları dışından biriyle değiştirirler. Bunlar ardından müşteri Şimdi Akşam Yemeği yalnızca siparişleri işleyeceğini belirterek doğrudan restorana bağlar:  
  
  ![Kullanım durumu diyagramında Ödeme Restoran rescoping](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
  **Kullanım durumu diyagramında Ödeme Restoran rescoping**  
  
  Bkz.  
  
- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)  
  
- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Kullanım çalışması diyagramı çizme  
 Bir kullanım durumu diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- *Aktörler* kişiler, kuruluşlar, makineler veya yazılım sistemleri tarafından oynanan rolleri temsil eder. Örneğin, müşteri, Restoran ve Şimdi Akşam Yemeği Ödeme Sistemi birer aktördür.  
  
- *Kullanım örnekleri* aktörler ve geliştirilmekte olan sistem arasındaki etkileşimi temsil eder.  Onlar tek fare tıklatın ya da ileti etkileşim günler boyunca Uzatılan bir işleme için herhangi bir ölçekte temsil edebilir.  
  
- *İlişkilendirmeleri* aktörleri kullanım örneklerine bağlayın.  
  
- Daha büyük bir kullanım durumu için *dahil* daha küçük depolara, örneğin, Sipariş Oluştur restoranı seçin'i içerir. Yapabilecekleriniz *genişletmek* hedefler ve adımları genişletilmiş kullanım örneğine kullanım örneğinin yalnızca belirli koşullar altında ortaya çıktığını göstermek için ekler bir kullanım örneği. Kullanım örnekleri aynı zamanda her birinden diğerine devralabilir.  
  
- A *alt* geliştirme ya da bileşenlerinden biri altında yazılım sistemini temsil eder. Kullanım durumları içeren büyük bir kutudur. Bir kullanım durumu diyagramı içinde veya alt sistem sınırı dışında ne olduğunu açıklar. Kullanıcının belirli amaçlara başka yollardan gerçekleştirmek gerekir, çizim belirtmek için bu durumları alt sistem sınırı dışında kullanırsınız.  
  
- *Yapıtları* bağlantı diyagram üzerindeki öğeleri diğer diyagramlara veya belgelere bağlar.  
  
  Bkz.  
  
- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)  
  
- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Özet: Kullanım örneği diyagramları gücü  
 Kullanım örneği diyagramları görselleştirmenize yardımcı olur:  
  
-   Bir sistemin desteklediği veya desteklemediği etkinlikler  
  
-   İnsanlar ve bu etkinlikleri gerçekleştiren dış sistemler  
  
-   Alt sistemler olarak temsil eden tüm etkinlikleri destekleyen sisteminin ana bileşenleri üst sistemin içine geçmiştir  
  
-   Bir kullanım durumu daha küçük olanlara ya da çeşitlere nasıl bölünmelidir  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklar**|  
|-----------------|-------------------|  
|Etkinlik diyagramı|Kullanım örneği ve o bu adımları gerçekleştiren kullanım adımların akışı.<br /><br /> Kullanım durumlarının adları sıklıkla bir eylem diyagramındaki adımları yansıtır. Etkinlik diyagramları kararları, birleştirme, girişler ve çıkışlar, eşzamanlı akışlar ve benzeri gibi öğeleri destekler.<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|  
|Sıralı diyagram|Bir kullanım durumunda katılımcılar arasındaki etkileşimler dizisini.<br /><br /> Bkz.<br /><br /> -   [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Sınıf diyagramı (UML)|Varlıklar veya kullanım örneğine katılan türleri.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
  
###  <a name="UnderstandActivities"></a> İş sürecini anlayın: etkinlik diyagramları  
 Faaliyet diyagramları, bir iş sürecindeki adım akışını açıklar ve iş akışıyla iletişim kurmak için basit bir yol sağlar. Geliştirme projesinin birden çok faaliyet diyagramı olabilir. Genellikle, bir etkinlik, Yemek Sipariş etmek, bir menüyü güncelleştirmek veya yeni bir restoran eklemek gibi bir dış eylem sonucunda tüm eylemleri kapsar. Bir etkinlik, karmaşık bir işlemin ayrıntılarını da açıklayabilir.  
  
 Lucerne, Lucerne ödemeyi işleme aldığını ve restorana ödeme olduğunu göstermek için aşağıdaki etkinlik diyagramı güncelleştirir. Bunlar Dinner Now ödeme sistemini Lucerne Ödeme sistemiyle vurgulandığı gibi değiştirin:  
  
 ![Lucerne Ödeme sistemi etkinlik diyagramında](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **Şimdi Akşam Yemeği Ödeme sistemi etkinlik diyagramında değiştiriliyor**  
  
 Lucerne ve Dinner Now güncellenen diyagram yardımcı olur, burada Lucerne Ödeme sisteminin iş süreci içinde uyum görselleştirin. Bu sürümde, açıklamalar adımları gerçekleştiren rolleri tanımlamak için kullanılır. Satırları oluşturmak için kullanılan *Kulvarlar*, adımları rol bakımından düzenleyen.  
  
 Takımlar alternatif bir hikaye siparişi aldıktan sonra burada müşteri görüşmeyi de düşünebilir. Bu yazılım sistemi için farklı gereksinimler oluşturursunuz.  
  
 Daha önce Şimdi Akşam Yemeği bu diyagramları PowerPoint'te Beyaz Tahta açıp u çizdiğini. Şimdi de Visual Studio her iki ekip yakalamak, anlamak ve ayrıntıları yönetmek için bu diyagramları çizmek için kullanırlar.  
  
 Bkz.  
  
-   [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)  
  
-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Etkinlik diyagramı çizme  
 Bir faaliyet diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- Bir *ilk düğüm* etkinliği ilk eylemini gösterir.  
  
   Diyagramda her zaman bu düğümlerinden biri olmalıdır.  
  
- *Eylemler* açıklayan adımları burada kullanıcı veya yazılımın bir görev gerçekleştirir.  
  
- *Denetim Akışları* Eylemler arasındaki akışı gösteren.  
  
- *Karar düğümleri* akış üzerinde koşullu dalları temsil eder.  
  
- *Çatal düğümler* tekli bölen eşzamanlı akışlara akar.  
  
- *Etkinliğin son düğümleri* faaliyetin sonlarını gösterir.  
  
   Bu düğümler isteğe bağlı olsa da, bunları nerede bittiğini göstermek için diyagramda dahil etmeyi yararlı etkinlik sona erer.  
  
  Bkz.  
  
- [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)  
  
- [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Özet: Etkinlik Şemalarının Gücü  
 Etkinlik diyagramları görselleştirmenize ve denetimi ve bir iş, sistem veya programa ait Eylemler arasındaki bilgi akışını açıklayan yardımcı olur. Diğer kişilerle iletişim kurarken iş akışını açıklamak için basit ve kullanışlı bir yolu budur.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklama**|  
|-----------------|---------------------|  
|Kullanım örneği diyagramı|Her bir etkin nesnenin gerçekleştirdiği etkinliklerini özetleyin.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Bileşen diyagramı|Sistem koleksiyonu bir iyi tanımlanmış arabirim kümeleri üzerinden davranış sağlayan veya tüketen bir grup yeniden kullanılabilir parça olarak görselleştirin.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|  
  
###  <a name="DescribeComponents"></a> Sistem yapısı açıklanmıştır: Bileşen diyagramları  
 Bileşen diyagramları bir sistemin, bir iyi tanımlanmış arabirim kümeleri üzerinden davranış sağlayan veya tüketen ayrılabilir parçalar koleksiyonu olarak açıklar. Parçalar herhangi bir ölçeğe ait olabilir ve herhangi bir şekilde bağlanabilir.  
  
 Lucerne ve Dinner görselleştirin ve sistemin bileşenlerini ve bunların artık yardımcı olmak için aşağıdaki Bileşen diyagramları oluştururlar:  
  
 ![Dış bileşenler ödeme sistemine](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Şimdi Akşam Yemeği Ödeme sisteminin bileşenleri**  
  
 Bu diyagramda gösterilmektedir farklı bileşen türlerini ve bunların *bağımlılıkları*. Örneğin, hem Şimdi Akşam Yemeği Web sitesi ve Lucerne Ödeme sistemi ödemeleri doğrulamak Harici Ödeme İşlemci Ağ'geçidi gerektirir. Bileşenler arasındaki oklar, hangi bileşenlerin diğer bileşenlerin işlevselliğine gerek duyduğunu gösteren bağımlılıkları temsil eder.  
  
 Lucerne Ödeme Sistemi'ni kullanmak için Dinner Now Web Sitesi'nin PaymentApproval ve PayableInsertion arabirimlerini Lucerne Ödeme Sistemi'nde kullanmak üzere güncelleştirilmelidir.  
  
 Aşağıdaki diyagram Şimdi Akşam Yemeği Web sitesi için bileşenlerin belirli bir yapılandırma gösterilmektedir. Bu yapılandırma, Web sitesinin herhangi bir örneğine dört içerdiğini belirtir *bölümleri*:  
  
- CustomerProcessing  
  
- OrderProcessing  
  
- ReviewProcessing  
  
- PaymentProcessing  
  
  Bu bölümler belirtilen bileşen türlerinin örnekleridir ve aşağıdaki gibi bağlanır:  
  
  ![Şimdi Akşam Yemeği Web sitesi içindeki bileşenler](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
  **Bileşenleri içinde Şimdi Akşam Yemeği Web sitesi**  
  
  Şimdi Akşam Yemeği Web sitesi davranışını Web sitesi işlevlerini işleyen bu parçalara atar. Ana bileşen ve onun üye bileşeni arasındaki oklar *temsilcileri* belirtmek hangi parçalarının üst aldığı veya gönderdiği arabirimleri aracılığıyla iletileri işleyecek.  
  
  Bu yapılandırmada, Müşteri ödemelerini PaymentProcessing bileşeni işler. Bu nedenle, Lucerne Ödeme sistemiyle tümleştirmek için güncelleştirilmelidir. Diğer senaryolarda, aynı ana bileşende birden çok bileşen türü örneği bulunuyor olabilir.  
  
  Bkz.  
  
- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)  
  
- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Bileşen diyagramı çizme  
 Bir bileşen diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- *Bileşenleri* Sistem işlevselliğinin ayrılabilir parçalarını temsil eder.  
  
- *Sağlanan arabirim bağlantı noktalarına* iletileri ya da hangi bileşenlerin uyguladığı ve diğer bileşenler veya dış sistemler tarafından kullanılan çağrıları grubuna temsil eder.  
  
- *Gerekli arabirim bağlantı noktalarına* ileti gruplarını veya bileşenlerin diğer bileşenlere veya harici sistemlere gönderdiği çağrıları temsil eder. Bu tür bir bağlantı noktası, bir bileşenin en az diğer bileşenler veya dış sistemlerden beklediği işlemleri açıklar.  
  
- *Bölümleri* , bileşenlerin üyeleridir ve genellikle diğer bileşenlerin örnekleridir. Bir parça ana bileşeninin iç tasarımının bir parçasıdır.  
  
- *Bağımlılıkları* belirtmek bileşenlerin diğer bileşenlerin işlevselliğini gerektirir.  
  
- *Temsilciler* bileşenin parçalarını gönderilen veya ana bileşen tarafından alınan iletileri işleyen gösterir.  
  
  Bkz.  
  
- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)  
  
- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Özet: Bileşen Şemalarının Gücü  
 Bileşen diyagramları görselleştirmenize yardımcı olur:  
  
-   Kendi dil veya stil uygulamalarına bakılmaksızın ayrılabilir parçalar koleksiyonu olarak sistem.  
  
-   Tasarımı anlamak ve gereklilikler değiştiğinde güncelleştirmenin daha kolay hale getirme, iyi tanımlanmış arabirimlere sahip bileşenler.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklama**|  
|-----------------|---------------------|  
|Kod Haritası|Kuruluş ve mevcut koddaki ilişkileri görselleştirin.<br /><br /> Bileşenler için adayları belirlemek için bir kod Haritası ve Grup öğeleri sistemdeki işlevlerine göre oluşturun.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)|  
|Sıralı diyagram|Bileşenler veya bileşen içindeki bölümlerin arasında etkileşim sırasını görselleştirin.<br /><br /> Bir bileşenden bir dizi diyagramına bir yaşam çizgisi oluşturmak için bileşene sağ tıklayın ve ardından **yaşam çizgisi Oluştur**.<br /><br /> Bkz.<br /><br /> -   [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Sınıf diyagramı (UML)|Sağlanan veya gerekli bağlantı noktaları ve bileşenlerin işlevselliğini uygulayan sınıflar arabirimleri tanımlayabilirsiniz.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
|Katman diyagramı|Bileşenlerle bağlantılı olarak sistemin mantıksal mimarisini açıklar. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulaması kullanın.<br /><br /> Bkz.<br /><br /> -   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|  
|Etkinlik diyagramı|Bileşenleri gelen iletilere yanıt olarak gerçekleştirdiği iç işlemeyi görselleştirin.<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|  
  
###  <a name="VisualizeCode"></a> Varolan kodu görselleştirin: Kod haritaları  
 Kod Haritaları, mevcut organizasyon ve ilişkileri kod içerisinde gösterir. Öğeleri tarafından temsil edilir *düğümleri* haritasında ve ilişkiler *bağlantıları*. Kod Haritaları, aşağıdaki türde görevleri gerçekleştirmenize yardımcı olabilir:  
  
- Yabancı kodu keşfedin.  
  
- Önerilen bir değişikliğin varolan kodu nerede ve nasıl etkilediğini anlayın.  
  
- Alanları karmaşıklığı, doğal Katmanlar veya modelleri veya iyileştirmeden yararlanabilecek diğer alanları bulun.  
  
  Örneğin, Şimdi Akşam Yemeği PaymentProcessing bileşeninin maliyetini tahmin etmek gerekir. Bu kısmen değişikliğin sistemin diğer bölümlerini etkileme derecesine bağlıdır. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri koddan kod haritaları oluşturur ve odağını değişiklik tarafından etkilenebilecek alanlara ayarlar.  
  
  Aşağıdaki harita PaymentProcessing sınıfı ve seçili görünen Şimdi Akşam Yemeği sisteminin diğer bölümleri arasındaki bağımlılıkları gösterir:  
  
  ![Şimdi Akşam Yemeği Ödeme sistemi için bağımlılık grafiği](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
  **Şimdi Akşam Yemeği Ödeme sistemi için kod Haritası**  
  
  Geliştirici PaymentProcessing sınıfını ve üyelerini etkilenme olasılığı bulunan alanları görmek için seçerek eşleme araştırır:  
  
  ![PaymentProcessing ve bağımlılıkları içinde yöntemleri](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
  **PaymentProcessing sınıfında ve bağımlılıkları içinde yer alan yöntemler**  
  
  Onlar sınıflarını, yöntemlerini ve bağımlılıklarını incelemek Lucerne Ödeme sistemi için aşağıdaki eşleme oluşturur. Takım, Lucerne sisteminin de Dinner Now sitesinin diğer bölümleriyle etkileşmek için işe gerek duyabileceğini görür:  
  
  ![Lucerne Ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
  **Lucerne Ödeme sistemi için kod Haritası**  
  
  Her iki ekip iki sistemi tümleştirmek için gereken değişiklikleri belirlemek için birlikte çalışır. Bazı kodları güncelleştirmek için daha kolay olacak şekilde yeniden düzenleyin karar. PaymentApprover sınıfı DinnerNow.Business ad alanına taşıyacak ve bazı yeni yöntemler gerektirecektir. İşlemleri işleyen Şimdi Akşam Yemeği sınıflarının kendi ad alanı olacaktır. Takımlar oluşturun ve planlamak, düzenlemek ve izlemek için çalışma öğelerini kullanın. Bunlar, çalışma öğelerini yararlı olacağı yerlerde model öğelere bağlar.  
  
  Kod yeniden düzenledikten sonra ekipler güncellenmiş yapıyı ve ilişkileri görmek için yeni bir kod Haritası oluşturun:  
  
  ![Yeniden düzenlenen kodu içeren bağımlılık grafiği](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
  **Yeniden düzenlenen kodu içeren kod Haritası**  
  
  Bu harita, PaymentApprover sınıfının artık DinnerNow.Business ad alanında bulunduğunu ve bazı yeni yöntemler gösterilmektedir. Şimdi Akşam Yemeği işlem sınıflarının artık daha sonra kodla başa çıkmak kolaylaştıran kendi PaymentSystem ad var.  
  
#### <a name="creating-a-code-map"></a>Bir kod Haritası oluşturma  
  
-   Kaynak koduna hızlı bir genel bakış için bir kod haritası oluşturmak için aşağıdaki adımları izleyin:  
  
     Üzerinde **mimarisi** menüsünde tıklatın **için kod eşlemesi çözümünü oluşturmak**.  
  
     Hızlı bir genel bakış derlenmiş kod, bir boş bir kod Haritası oluşturun ve ardından derleme dosyalarını veya ikili dosyaları eşleme yüzeyine sürükleyin.  
  
-   Özel kodu veya çözüm öğelerini araştırmak için öğeleri ve ilişkileri görselleştirmek istediğiniz seçmek için Çözüm Gezgini'ni kullanın. Ardından yeni bir harita oluşturur veya mevcut bir haritayı için seçili öğeleri Ekle. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Harita keşfetmenize yardımcı olmak üzere düzenini gerçekleştirmek istediğiniz görevlerin türlerini uygun şekilde yeniden düzenleyin.  
  
     Örneğin, kod üzerinde katman oluşturmayı görselleştirmek için bir ağaç düzeni seçin. Bkz: [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Özeti: Kod haritaları gücü  
 Kod haritaları yardımcı:  
  
-   Mevcut koddaki ilişkileri ve kuruluş hakkında bilgi edinin.  
  
-   Önerilen bir değişiklik tarafından etkilenebilecek alanları tanımlayın.  
  
-   Alanlarını karmaşıklığı, desenleri, katmanları veya kod korumak, değiştirin ve yeniden kolaylaştırmak için geliştirebileceğimiz diğer alanları bulun.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklar**|  
|-----------------|-------------------|  
|Katman diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulaması kullanın.<br /><br /> Varolan veya hedeflenen katmanları tanımlamanıza yardımcı olması için bir kod Haritası oluşturun ve ilişkili öğeleri gruplayın. Bir katman diyagramı oluşturmak için bkz:<br /><br /> -   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)|  
|Bileşen diyagramı|Bileşenleri, arabirimler ve aralarındaki ilişkiler.<br /><br /> Bileşenleri tanımlamanıza yardımcı olması için bir kod Haritası ve Grup öğeleri sistemdeki işlevlerine göre oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|  
|Sınıf diyagramı (UML)|Sınıfları, öznitelikleri ve işlemleri ve ilişkilerini.<br /><br /> Bu öğeleri tanımlamanıza yardımcı olması için bu öğeleri gösteren bir UML sınıf diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için kod üzerinde varolan sınıflar.<br /><br /> Görselleştirme ve kod içinde varolan bir sınıf değiştirmek için Sınıf Tasarımcısı'nı kullanın.<br /><br /> Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="DescribeSequence"></a> Etkileşimler açıklanmıştır: sıralı diyagramlar  
 Sıralı diyagramları bir sistemin bölümleri arasındaki etkileşimlerin sırasını tanımlar. Parçalar herhangi bir ölçeğe ait olabilir. Örneğin, bunlar bir programdaki ayrı nesneler geniş alt sistemler veya harici aktörler arasında değişebilir. Etkileşimler herhangi bir ölçek ve türden olabilir. Örneğin, bireysel iletiler ile genişletilmiş işlemlere arasında değişebilir ve işlev çağrıları veya Web hizmeti iletileri olabilir.  
  
 Lucerne ve Şimdi Akşam Yemeği İşlem Ödemesi kullanım örneğindeki adımları tanımlamak ve gidermek için bileşen diyagramından aşağıdaki sıralı diyagramı bunlar oluşturur. Yaşam çizgileri Şimdi Akşam Yemeği Web sitesi bileşeni ve onun parçalarını yansıtır. Yaşam çizgileri arasında görünen iletiler bileşeni diyagramlarda bağlantıları izleyin:  
  
 ![Sıralı diyagram için İşlem Ödemesi kullanım örneği](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Sıralı diyagram için İşlem Ödemesi kullanım örneği**  
  
 Sıralı diyagram, Şimdi Akşam Yemeği Web sitesi müşterinin sipariş oluşturduğunda OrderProcessing işleminin bir örneği öğesinin görüntüleyip ProcessOrder gösterir. Sonra OrderProcessing PaymentProcessing üzerinde ProcessPayment çağırır. Harici Ödeme İşlemci Ağ Geçidi ödemeyi doğrulayıncaya kadar bu devam eder. Denetim, Şimdi Akşam Yemeği Web sitesi için sadece döndürür.  
  
 Lucerne, ödeme sistemini Dinner Now sistemiyle bütünleştirmek üzere güncelleştirmenin maliyetini öngörmelidir. Bunu anlamalarına yardımcı olmak için etkilenen kodu görselleştirmek için kod haritalarını de oluşturabilir.  
  
 Bkz.  
  
-   [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)  
  
-   [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)  
  
-   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Dizi diyagramı çizme  
 Bir sıralı diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- Dikey *yaşam çizgilerini* aktörlerini veya yazılım nesnelerinin örneklerini temsil eder.  
  
   Geliştirilmekte olan sistemin dışında bir katılımcı olduğunu gösteren bir aktör simge eklemek için yaşam çizgisine tıklayın. İçinde **özellikleri** penceresinde **aktör** için **True**. Varsa **özellikleri** penceresi açık değilse, basın **F4**.  
  
- Yatay *iletileri* yöntem çağrılarını, Web hizmeti iletilerini veya bazı diğer iletişimleri temsil eder. *Yürütme yinelemeleri* yaşam çizgilerinde görüntülenen ve dönemlerde temsil dikey gölgeli dikdörtgenler nesneleri işlem çağrıları alıyorsunuz.  
  
- Sırasında bir *zaman uyumlu* ileti gönderen nesne bekler denetimi için <\<dönüş >> normal işlev çağrısı olduğu gibi. Sırasında bir *zaman uyumsuz* ileti gönderen hemen devam edebilir.  
  
- Kullanım <\<oluşturma >> nesneleri diğer nesnelere göre üretim belirtmek için iletiler. Nesneye gönderilen ilk ileti olmalıdır.  
  
  Bkz.  
  
- [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)  
  
- [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Özet: Sıra Şemalarının Gücü  
 Sıralama diyagramları görselleştirmenize yardımcı olur:  
  
-   Kullanım örneğinin yürütülmesi sırasında aktörler ve nesneler arasında aktarır denetim akışı.  
  
-   Bir yöntem çağrısı veya iletinin uygulaması.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklama**|  
|-----------------|---------------------|  
|Sınıf diyagramı (UML)|Yaşam çizgilerinin temsil ettiği sınıfları ve parametreleri tanımlayın ve yaşam çizgileri arasında gönderilen iletilerde kullanılan değerleri döndürür.<br /><br /> Yaşam çizgisinden bir sınıf oluşturmak için yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur** veya **oluşturma arabirimi**. Bir sınıf diyagramında bir türden bir yaşam çizgisi oluşturmak için türe sağ tıklayın ve ardından **yaşam çizgisi Oluştur**.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|  
|Bileşen diyagramı|Yaşam çizgilerinin temsil ettiği bileşenler ve sağlayan ve iletiler tarafından temsil edilen davranışı tüketen arabirimler açıklanmaktadır.<br /><br /> Bir bileşen diyagramından bir yaşam çizgisi oluşturmak için bileşene sağ tıklayın ve ardından **yaşam çizgisi Oluştur**.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|  
|Kullanım örneği diyagramı|Bir kullanıcının amacını temsil eden bir kullanım durumu olarak kullanıcılar ve sıralı diyagram bileşenler arasındaki etkileşimleri özetleyin.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
###  <a name="DefineClasses"></a> Bir türler sözlüğü tanımlayın: sınıf diyagramları  
 Sınıf diyagramları, varlıkları, koşulları veya sistem ve birbirleriyle olan ilişkilerine katılmak kavramları tanımlayın. Örneğin, öznitelikler ve işlemler için dil veya stil uygulamalarına bakılmaksızın, her sınıf tanımlamak için geliştirme sırasında bu diyagramları kullanabilirsiniz.  
  
 İşlem Ödemesi kullanım örneğine katılan varlıkları tanımlamak ve Lucerne yardımcı olmak için bunlar aşağıdaki sınıf diyagramı çizmek:  
  
 ![Sınıf diyagramında Ödeme varlıkları işlemek](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Bir sınıf diyagramında İşlem Ödemesi varlıkları**  
  
 Bu diyagram bir müşterinin birçok siparişi ve siparişler için farklı yollar olduğunu gösterir. BankAccount hem de CreditCard payment'tan devralır.  
  
 Geliştirme sırasında Lucerne her sınıfın ayrıntılarını tartışmak ve açıklamak için aşağıdaki sınıf diyagramı kullanır:  
  
 ![Bir sınıf diyagramında Ödeme varlık ayrıntıları işlem](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Sınıf diyagramında İşlem Ödemesi bilgileri**  
  
 Bkz.  
  
-   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Sınıf diyagramı çizme  
 Bir sınıf diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- Sınıflar, arayüzler ve numaralandırma gibi türler:  
  
  -   A *sınıfı* belirli yapısal veya davranışsal özellikleri paylaşan nesnelerin tanımıdır.  
  
  -   Bir *arabirimi* bir parçası dışarıdan görünen bir nesne davranışını tanımlar.  
  
  -   Bir *numaralandırma* değişmez değerler listesini içeren bir sınıflandırıcıdır.  
  
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
  
  Bkz.  
  
- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)  
  
- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Özet: Sınıf Şemalarının Gücü  
 Sınıf diyagramları, tanımlamanıza yardımcı olur:  
  
-   Kullanıcıların ihtiyaçları ve sisteme katılan varlıklar ele alınırken kullanılacak terimler, ortak bir sözlüğü. Bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
-   Uygulamalarından bağımsız olarak bileşenler gibi sistemin parçaları tarafından kullanılan türler. Bkz: [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md).  
  
-   Türler arası bağımlılıklar gibi ilişkiler. Örneğin, bir tür, başka türdeki birden çok örnek ile ilişkilendirilebilir gösterebilirsiniz.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklama**|  
|-----------------|---------------------|  
|Kullanım örneği diyagramı|Hedeflerinizi açıklamak için kullanılan türleri tanımlar ve çalışmaları içindeki adımları kullanın.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Etkinlik diyagramı|Nesne düğümleri, giriş sabitleyicileri, çıkış sabitleyicileri ve etkinlik parametre düğümleri geçen veri türlerini tanımlayın.<br /><br /> Bkz.<br /><br /> -   [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|  
|Bileşen diyagramı|Bileşenler, arabirimleri ve aralarındaki ilişkiler açıklanmaktadır. Bir sınıf, ayrıca tam bir bileşeni açıklayabilir.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|  
|Katman diyagramı|Sınıflarla bağlantılı olarak sistemin mantıksal mimarisini tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulaması kullanın.<br /><br /> Bkz.<br /><br /> -   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|  
|Sıralı diyagram|Yaşam çizgilerini işlem, parametre türlerini tanımlamak ve dönüş değerlerini yaşam çizgisinin alabileceği tüm iletiler için.<br /><br /> Bir sınıf diyagramında bir türden bir yaşam çizgisi oluşturmak için türe sağ tıklayın ve ardından **yaşam çizgisi Oluştur**.<br /><br /> Bkz.<br /><br /> -   [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Kod Haritası|Kuruluş ve mevcut koddaki ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için bu öğeleri gösteren bir kod Haritası oluşturun.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a> Mantıksal mimarisi açıklanmıştır: katman diyagramları  
 Katman diyagramları, çözümünüzdeki açıklamaları soyut gruplar düzenleyerek sistemin mantıksal mimarisini açıklar veya *katmanları*. Yapılar ad alanları, projeler, sınıflar, yöntemler vb. gibi birçok şey olabilir. Katmanlar, temsil ve rolleri veya yapıların sistemde gerçekleştirdiği görevleri tanımlayın. Katman doğrulama, derleme ve kodun tasarımıyla uyumlu kalmasını sağlamak için iade etme işlemleri de içerebilir.  
  
 Kodun tasarımla tutarlılığını korumak için Şimdi Akşam Yemeği ve Lucerne aşağıdaki katman diyagramını geliştikçe kodlarını doğrulamak için kullanın:  
  
 ![Katman diyagramı tümleşik ödeme sisteminin](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Şimdi Akşam Yemeği için katman diyagramı Lucerne ile tümleştirilmiş**  
  
 Bu Diyagramdaki katmanlar ilgili Şimdi Akşam Yemeği ve Lucerne çözüm yapılarına bağlar. Örneğin, iş katmanı bağlantılar DinnerNow.Business ad alanı ve üyeleri için artık PaymentApprover sınıfını içerir. Kaynak erişimi katmanı DinnerNow.Data ad bağlantıları. Oklar veya *bağımlılıkları*, sadece iş katmanının kaynak erişim katmanındaki işlevselliği kullanabileceğini belirtin. Takımlar kendi kodlarını güncellerken olarak katman doğrulama çakışmaları meydana gelirken yakalamak ve ekiplerin onları derhal çözmesine yardımcı olmak için düzenli olarak gerçekleştirilir.  
  
 Takımlar, kademeli olarak birleştirmek ve iki sistem test etmek için birlikte çalışır. İlk önce PaymentProcessing uygulamasını ele PaymentApprover öğesinin ve Dinner Now öğesinin geri kalan birbiriyle başarıyla çalıştığından emin olun.  
  
 Aşağıdaki kod haritası, Şimdi Akşam Yemeği ve PaymentApprover arasındaki yeni çağrıları gösterir:  
  
 ![Tümleşik sistem içeren güncelleştirilmiş bir bağımlılık grafiği](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Güncelleştirilmiş yöntem çağrılarını içeren kod Haritası**  
  
 Sistem beklendiği gibi çalıştığını doğruladıktan sonra Şimdi Akşam Yemeği PaymentProcessing kodunu işaretler yorumlar. Katman doğrulama raporları temizdir ve ortaya çıkan kod Haritası başka PaymentProcessing bağımlılığının bulunmadığını gösterir:  
  
 ![PaymentProcessing içermeyen bağımlılık grafiği](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **PaymentProcessing içermeyen kod Haritası**  
  
#### <a name="drawing-a-layer-diagram"></a>Katman diyagramı çizme  
 Bir katman diyagramı aşağıdaki önemli özelliklere sahiptir:  
  
- *Katmanlar* açıklamaların mantıksal gruplarını tanımlar açıklar.  
  
- A *bağlantı* bir katman ve yapı arasındaki ilişkidir.  
  
   Yapılardan katmanlar oluşturmak için Çözüm Gezgini, kod Haritaları, sınıf görünümü veya Nesne Tarayıcısı öğeleri sürükleyin. Yeni Katmanlar çizmek ve ardından bunları yapılara bağlamak için araç kutusunu kullanın veya katmanları oluşturmak üzere diyagram yüzeyine sağ tıklayın ve sonra öğeleri bu katmanlara sürüklemek.  
  
   Bir katmandaki sayı katmana bağlı olan yapıların sayısını gösterir. Bu yapılar ad alanları, projeler, sınıflar, yöntemler vb. olabilir. Bir katmandaki yapı sayısını yorumladığınızda aşağıdakileri unutmayın:  
  
  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.  
  
     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.  
  
  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.  
  
    Bir katmana bağlı yapıların listesini görmek için katmanı sağ tıklayın ve ardından **bağlantıları görüntüle** açmak için **Katman Gezgini**.  
  
- A *bağımlılık* bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ancak tersi doğru değildir. A *çift yönlü bağımlılık* bir katmanın işlevselliği kullanabileceğini belirtir başka bir katmanda ve bunun tersi de geçerlidir.  
  
   Katman diyagramı üzerinde varolan bağımlılıkları görüntülemek için diyagram yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**. Hedeflenen bağımlılıklarını tanımlamak için yenilerini çizin.  
  
  Bkz.  
  
- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)  
  
- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)  
  
- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Özet: Katman Şemalarının Gücü  
 Katman diyagramları yardımcı olur:  
  
-   Yapılarının işlevlerine göre bir sistemin mantıksal mimarisi açıklanmıştır.  
  
-   Geliştirme aşamasındaki kodun belirtilen tasarıma uygun olduğundan emin olun.  
  
#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki  
  
|**Diyagramı**|**Açıklama**|  
|-----------------|---------------------|  
|Kod Haritası|Kuruluş ve mevcut koddaki ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için kod haritası oluşturmak ve sonra harita üzerinde öğeleri olası Katmanlar olarak gruplayın. Grupları eşlemesinden katman diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Gözat ve kod haritaları bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|  
|Bileşen diyagramı|Bileşenler, arabirimleri ve aralarındaki ilişkiler açıklanmaktadır.<br /><br /> Katmanlar görselleştirmek için sistemdeki farklı bileşenlerin işlevselliğini açıklayan bir bileşen diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
|**Kategori**|**Bağlantılar**|  
|------------------|---------------|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodu görselleştirme](../modeling/visualize-code.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)   
 [Çevik Yazılım geliştirmede modeller kullanma](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)



