---
title: 'Katman diyagramları: Yönergeler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fa7483a000b5abd59b846edceead3af93f41dbc4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734438"
---
# <a name="layer-diagrams-guidelines"></a>Katman Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızın yüksek bir düzeyde oluşturarak mimarisini *katman diyagramları* Visual Studio'da. Kodunuzu katman diyagramıyla doğrulayarak kodunuzun tasarımla tutarlı kalmasını sağlayın. Ayrıca yapı işleminizde katman doğrulama ekleyebilirsiniz. Bkz: [kanal 9 videosu: tasarım ve katman diyagramlarını kullanarak Mimarinizi geçerli](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-layer-diagram"></a>Bir katman diyagramı nedir?  
 Gibi geleneksel mimarisi diyagramı, katman diyagramına ana bileşenlerini veya tasarım ve onların bağımlılıklarını işlevsel birimi tanımlar. Diyagramdaki her bir düğüm olarak adlandırılan bir *katman*, ad alanları, projeler ve diğer yapıtları oluşan mantıksal bir grubu temsil eder. Tasarımınızı bulunması gereken bağımlılıklar çizebilirsiniz. Geleneksel mimarisi diyagramı, kaynak kodunda gerçek bağımlılıkları belirttiğiniz istenen bağımlılıkları için uygun doğrulayabilirsiniz. Üzerinde doğrulama parçası normal bir derleme yaparak [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], program kodu gelecek değişiklikler sisteminin mimarisine bağlı olarak devam etmesini sağlayabilirsiniz. Bkz: [katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a> Tasarım veya katman diyagramları ile uygulamanızı güncelleştirin  
 Aşağıdaki adımlar, geliştirme süreci içinde katman diyagramları kullanma hakkında genel bakış sağlar. Bu konunun sonraki bölümlerinde, her bir adım hakkında daha ayrıntılı açıklanmaktadır. Yeni bir tasarım geliştiriyorsanız varolan koda başvuran adımları atlayın.  
  
> [!NOTE]
>  Bu adımlar, yaklaşık sırada görünür. Büyük olasılıkla, görevleri çakışma, bunları kendi durumunuza uygun olarak yeniden sıralayabilir ve bunları, projenizdeki her yineleme başlangıcında yeniden ziyaret isteyeceksiniz.  
  
1.  [Katman diyagramı oluşturma](#Create) tüm uygulama veya içerdiği bir katman.  
  
2.  [Birincil işlev alanı ve bileşenine göstermek için katman tanımlama](#CreateLayers) uygulamanızın. Bu katmanlar, işlevlerine göre örneğin, "Sunu" veya "Hizmetler" olarak adlandırın. Varsa bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm, her katman koleksiyonu ile ilişkilendirebilir *yapıtları*projeleri, ad alanları, dosyalar vb. gibi.  
  
3.  [Varolan bağımlılıkları keşfetme](#Generate) katmanlar arasında.  
  
4.  [Katmanları ve bağımlılıkları düzenleme](#EditArchitecture) güncelleştirilmiş gösterecek şekilde yansıtmak için kodu istediğiniz tasarım.  
  
5.  [Tasarım, uygulamanızın yeni alanlar](#NewAreas) asıl mimari blok veya bileşenleri temsil etmek için katmanlar oluşturarak ve her katmanın diğerlerinden nasıl kullandığını gösterilecek bağımlılıklarını tanımlama.  
  
6.  [Düzen ve diyagram görünümünü Düzenle](#EditLayout) arkadaşlarınızla tartışmak yardımcı olacak.  
  
7.  [Kodu katman diyagramına karşı doğrulamak](#Validate) kod ve mimari arasındaki çakışmaları vurgulayın.  
  
8.  [Yeni Mimarinizi uymak için kodu güncelleştirmeniz](#UpdateCode). Yinelemeli olarak geliştirin ve çakışma olmadığından doğrulama gösterir kadar kodu yeniden düzenleyin.  
  
9. [Derleme işleminde katman doğrulamasını içerecek](#BuildValidation) kod tasarımınıza devam etmesini sağlamak için.  
  
##  <a name="Create"></a> Katman diyagramı oluşturma  
 Bir katman diyagramı modelleme projesinin içinde oluşturulmalıdır. Varolan bir modelleme projesine yeni bir katman diyagramı eklemek, yeni modelleme projesi için katman diyagramı oluşturun veya aynı modelleme projesinin içinde varolan katman diyagramını kopyalayın.  
  
> [!IMPORTANT]
>  Değil eklemek, sürükleyin veya varolan katman diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözüm içindeki başka bir konuma kopyalayın. Bu şekilde kopyalanan katman diyagramı, diyagramı değiştirseniz bile orijinal diyagram aynı başvuruları olacaktır. Bu katman doğrulama düzgün çalışmasını engeller ve diyagramı açmaya çalışırken kayıp öğeler gibi diğer sorunları veya diğer hataları neden olabilir.  
  
 Bkz: [kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a> İşlevsel alanlara veya bileşenleri temsil etmek için katman tanımlama  
 Katmanlar mantıksal gruplarını temsil *yapıtları*projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi. Visual C# .NET ve Visual Basic .NET projelerindeki Yapılardan katmanlar oluşturma veya Word dosyaları veya PowerPoint sunumları gibi belgeleri bağlayarak özellikler veya planlar katmana ekleyebilirsiniz. Her katman diyagramında bir dikdörtgen görünür ve ona bağlı olan yapıların sayısını gösterir. Bir katman, daha ayrıntılı görevleri açıklayan iç içe katmanlar içerebilir.  
  
 Genel bir kural olarak, örneğin, "Sunu" veya "Hizmetler", işlevlerine göre adı katmanları. Yapıtlar yakından bağlıysa bunları aynı katmanda yerleştirin. Yapıtlar ayrı olarak güncelleştirilen ya da ayrı uygulamalarında kullanılan, bunları farklı katmanlara yerleştirin. Katmanlama desenler hakkında bilgi almak için desenler ve uygulamalar sitesini ziyaret edin [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Belirli türdeki katmanlara bağlayabilirsiniz yapıtlar vardır, ancak katman diyagramına karşı doğrulamayı desteklemez. Yapıt doğrulamayı destekleyip desteklemediğini görmek için **Katman Gezgini** incelemek için **doğrulamayı destekler** yapıt bağlantı özelliği. Bkz: [Katmanlar arasındaki mevcut bağımlılıklara Bul](#Generate).  
  
 Kod Haritaları, bilmediğiniz bir uygulamayı güncelleştirirken de oluşturabilir. Bu diyagramları Kodu Keşfetme sırasında desenleri ve bağımlılıkları keşfetmenize yardımcı olabilir. Ad alanlarını ve sınıfları, genellikle de varolan katmanlarla keşfetmek için Çözüm Gezgini'ni kullanın. Bu kod yapıları katmanlara katman diyagramları için Çözüm Gezgini'nden sürükleyerek atayın. Ardından, kodu güncelleştirmeye veya uygulamanızı tasarım ile tutarlı kalmasını sağlamak amacıyla katman diyagramları da kullanabilirsiniz.  
  
 Bkz.  
  
-   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a> Katmanlar arasındaki mevcut bağımlılıklara keşfedin  
 Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Varolan bağımlılıklara ters mühendislik tarafından bulabilir bunları.  
  
> [!NOTE]
>  Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıların ters mühendislik uygulayabileceğiniz bağımlılıkları olduğunu görmek için bir veya birden çok katmana sağ tıklayın ve ardından **bağlantıları görüntüle**. İçinde **Katman Gezgini**, inceleyin **doğrulamayı destekler** sütun. Bağımlılıklar, bu sütunda görüntülenir yapıtlar için ters mühendislik olmayacak **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Katmanlar arasında ters mühendislik Varolan bağımlılıkları için  
  
- Tek veya birden fazla katman seçin, seçilen katmanın sağ tıklayın ve ardından **Bağımlılıklar Oluştur**.  
  
  Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.  
  
##  <a name="EditArchitecture"></a> Katmanları ve bağımlılıkları hedeflenen tasarımı göstermek için düzenleme  
 İçin sisteminizde veya hedeflenen mimaride yapmayı planladığınız değişiklikleri açıklamak için katman diyagramı düzenlemek için aşağıdaki adımları kullanın. Kod yapısını genişletmeden önce iyileştirmek için yeniden düzenleme bazı değişiklikler de göz önünde bulundurabilirsiniz. Bkz: [kod yapısını iyileştirme](#Improving).  
  
|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|  
|------------|-----------------------------|  
|Var olmaması gereken bir bağımlılık Sil|Bağımlılık tıklatın ve sonra basın **Sil**.|  
|Bağımlılık yönünü değiştirme veya kısıtlama|Ayarlama, **yönü** özelliği.|  
|Yeni bağımlılıklar oluşturma|Kullanım **bağımlılık** ve **çift yönlü bağımlılık** araçları.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. İşlemi tamamladığınızda, tıklayın **işaretçi** aracını veya ENTER tuşuna **ESC** anahtarı.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın ad alanlarını yazın **Yasak Namespace bağımlılıkları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın ad alanlarını yazın **Yasak Ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın ad türü **gerekli ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
  
###  <a name="Improving"></a> Kod yapısını artırma  
 Yeniden düzenleme değişiklikler, uygulama davranışını etkilemez, ancak kodu değiştirmek ve gelecekte genişletmek kolaylaştırılmasına yardımcı olmak geliştirmeleridir. İyi yapılandırılmış kod, bir katman diyagramına soyutlamak kolay bir tasarıma sahiptir.  
  
 Örneğin, her ad alanı için bir katman kod ve sonra ters mühendislik bağımlılıkları oluşturursanız, bulunmamalıdır katmanlar arasında tek yönlü bağımlılıkları en az bir dizi. Sınıfları veya yöntemleri katmanları kullanarak daha ayrıntılı bir diyagram oluşturursanız, sonucu da aynı özellikleri olmalıdır.  
  
 Durum bu değilse, kod ömrü boyunca değiştirmek daha zor olacaktır ve katman diyagramları kullanarak doğrulama için daha az uygun olacaktır.  
  
##  <a name="NewAreas"></a> Uygulamanızın yeni alanları tasarlama  
 Yeni projede yeni bir proje veya yeni bir alan geliştirme başlattığınızda, katmanları ve bağımlılıkları kod geliştirmeye başlamadan önce ana bileşenleri belirlemenize yardımcı olması için çizebilirsiniz.  
  
-   **Tanımlanabilen mimari desenleri Göster** Mümkünse, katman diyagramları. Örneğin, bir masaüstü uygulamasını tanımlayan bir katman diyagramı Katmanlar sunusu, etki alanı mantığı ve veri Store gibi içerebilir. Bir uygulama içinde tek bir özellik kapsayan bir katman diyagramı Katmanlar gibi Model, Görünüm ve denetleyici olabilir. Desenler hakkında daha fazla bilgi için bkz. [desenler ve uygulamalar: uygulama mimarisi](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Sık de benzer modeller oluşturursanız, özel bir araç oluşturabilir. Bkz: [tanımlayan özel bir modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Her katman için bir kod yapısı oluşturma** gibi bir ad alanı, sınıf veya bileşeni. Bu kodu izler ve kod yapıları katmanlara bağlamak için kolaylaştırır. Her bir yapıt oluşturma hemen sonra uygun katmana bağlayın.  
  
-   **Çoğu sınıf ve diğer yapıları katmanlara bağlamak zorunda değilsiniz** katmanlara zaten bağlı ad alanları gibi daha büyük yapılar aralığında olduğundan.  
  
-   **Yeni bir özellik için yeni bir diyagram oluşturma**. Genellikle, tüm uygulama tanımlayan bir veya daha fazla katman diyagramları olacaktır. Uygulamanın içinde yeni bir özellik tasarlıyorsanız, eklemeyin veya mevcut diyagramları değiştirin. Bunun yerine, yeni kod parçalarını yansıtır kendi diyagramı oluşturun. Yeni Diyagram Katmanlar sunusu, etki alanı mantığı ve yeni özellik için veritabanı katmanları içerebilir.  
  
     Uygulamayı oluşturduğunuzda, kodunuzu hem genel diyagramı ve daha ayrıntılı özellik diyagramınızı karşı doğrulanır.  
  
##  <a name="EditLayout"></a> Sunu ve tartışma için Düzen  
 Katmanları ve bağımlılıkları tanımlayın veya bunları ekip üyeleriyle tartışmanıza yardımcı olması için aşağıdaki yollarla diyagramın düzenini ve görünümü düzenleyin:  
  
-   Boyutları, şekiller ve Katmanlar konumlarını değiştirin.  
  
-   Katmanları ve bağımlılıkları renklerini değiştirin.  
  
    -   Bir veya daha fazla katmanları veya bağımlılıkları, sağ tıklayın ve ardından seçin **özellikleri**. İçinde **özellikleri** penceresinde Düzenle **renk** özelliği.  
  
##  <a name="Validate"></a> Kodu diyagrama karşı doğrulayın  
 Diyagram düzenledikten sonra istediğiniz zaman el ile veya otomatik olarak karşı kodu yerel bir yapı çalıştırdığınız her seferde doğrulamak için veya [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].  
  
 Bkz.  
  
-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Derleme işleminde katman doğrulamasını içerecek](#BuildValidation)  
  
##  <a name="UpdateCode"></a> Yeni mimarinize uygun olması için kodu güncelleştirme  
 Genellikle, hata kodu güncellenmiş katman diyagramına karşı doğrulamak ilk kez görünür. Bu hatalar, birkaç nedeni olabilir:  
  
- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.  
  
- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.  
  
  Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu genellikle yinelemeli bir işlemdir. Bu hatalar hakkında daha fazla bilgi için bkz. [katman diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Geliştirme veya kodu yeniden düzenleyin, katman diyagramına bağlamak için yeni yapılar olabilir. Ancak, var olan ad alanları temsil eden katmanlarına sahip olduğunda bu örneğin, gerekli olmayabilir ve yeni kod, daha fazla malzeme yalnızca bu ad alanlarına ekler.  
  
 Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Hatayı gizlediğinizde, bir iş öğesi oturum açmak için iyi bir uygulamadır [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Bu görevi gerçekleştirmek için bkz: [katman diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a> Derleme işleminde katman doğrulamasını içerecek  
 Kodda gelecekteki yapılan değişiklikler için katman diyagramları uyumlu olmasını sağlamak için katman doğrulaması çözümünüzün standart derleme işlemini içerir. Çözüm diğer takım üyelerinin yapı olduğunda, kodda bağımlılıklar hem de katman diyagramını arasındaki farklılıkları derleme hataları olarak bildirilir. Derleme işleminde katman doğrulama ekleme hakkında daha fazla bilgi için bkz. [katman diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)   
 [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)



