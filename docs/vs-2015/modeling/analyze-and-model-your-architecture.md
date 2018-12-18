---
title: Çözümleme ve mimarinizin modelini | Microsoft Docs
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
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b7d7f9f478e85229eaa72ab04d12b6b542cbab5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781042"
---
# <a name="analyze-and-model-your-architecture"></a>Mimarinizi çözümleme ve mimarinizin modelini oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı kullanarak Visual Studio mimari ve Modelleme Araçları tasarlayıp uygulamanıza model kullanıcı gereksinimlerini karşıladığından emin olun. Var olan program kodu daha kolay kodun yapısını, davranış ve ilişkileri görselleştirmek için Visual Studio kullanarak anlayın.  
  
 Farklı geliştirme sürecinizin bir parçası olarak uygulama yaşam döngüsü boyunca ayrıntı düzeylerinde modeller oluşturun. Gereksinimleri, görevleri, test çalışmalarını, hataları ve Team Foundation Server iş öğelerini model öğelere ve geliştirme planınızı bağlantılandırarak Modellerinizi ile ilişkili diğer işleri izleyin. Bkz: [senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Visual Studio'nun hangi sürümlerinin her özelliğini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="to"></a>Bitiş  
  
|||  
|-|-|  
|**Kodu görselleştirme**:<br /><br /> -Kod haritaları oluşturarak kodun organizasyon ve ilişkileri bakın. Derlemeler, ad alanları, sınıflar, yöntemler vb. arasındaki bağımlılıkları görselleştirin.<br />-Koddan sınıf diyagramları oluşturarak belirli bir projenin üyeleri ve sınıf yapısı bakın.<br />-Kodu doğrulamak için katman diyagramları oluşturarak, kodunuzun tasarımı arasındaki çakışmaları bulun.<br /><br /> **Not**: Visual Studio'nun bu sürümünde terimi *kod Haritası* yerine kullanılan *bağımlılık grafiği*. Terim *grafik* tek başına kullanıldığında genellikle bir yönlendirilmiş grafik veya DGML diyagramı (veya belge) ifade eder. Kod haritaları DGML diyagram uzmanlaşmış bir türü var.|-   [Kodu görselleştirme](../modeling/visualize-code.md)<br />-   [Sınıflarla ve diğer türlerle (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video:, (kanal 9) görselleştirme yoluyla kod bağımlılıkları anlama](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: (kanal 9) bir değişikliğin etkisini görselleştirin](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Açıklayan ve kullanıcı gereksinimlerinden**:<br /><br /> -Kullanıcı hikayeleri, iş kuralları ve diğer gereksinimler açıklamak ve UML diyagramları kullanım örneği, etkinlik ve sınıf diyagramları gibi çizerek, tutarlılık sağlanmasına yardımcı olmak.|-   [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)<br />-   [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)<br />-   [Video: Mimari (kanal 9) modelleme aracılığıyla geliştirme](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Mimariyi tanımlayın**:<br /><br /> -Yazılım sisteminizin ve tasarım desenleri büyük ölçekli yapısını UML bileşeni, sınıf ve sıralı diyagramlar çizerek model.<br />-Tanımlama ve katman diyagramları oluşturarak kodunuzun bileşenler arasındaki bağımlılıklar kısıtlamaları zorunlu kılma.|-   [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)<br />-   [Uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Mimari (kanal 9) modelleme aracılığıyla geliştirme](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: katman diyagramlarını tasarlama ve Mimarinizi (kanal 9) doğrulamak için kullanın.](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Sisteminiz gereksinimleri ile doğrulamak ve hedeflenen tasarım:**<br /><br /> -Onay testleri veya gereksinimleri modellerine göre sistem testleri tanımlayın. Bu testleri ve kullanıcılarınızın gereksinimlerini arasında güçlü bir ilişki oluşturur ve gereksinimleri değiştiğinde daha fazla sistem bir kolayca güncelleştirmenize yardımcı olur.<br />-Hedeflenen mimarisini katman diyagramları ile kod bağımlılıklarını doğrulamak ve tasarım ile çakışabilecek değişiklikleri engelleyebilirsiniz.|-   [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)<br />-   [Video: katman diyagramlarını tasarlama ve Mimarinizi (kanal 9) doğrulamak için kullanın.](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Paylaşım modelleri ve diyagramları Team Foundation sürüm denetimini kullanarak kod haritaları**:<br /><br /> -Kod Haritaları, bunları paylaşabilmek modelleme projeleri, UML diyagramları ve katman diyagramları, Team Foundation sürüm denetimi altına yerleştirin.|Bu öğeleri Team Foundation sürüm denetimi altında çalışan birden çok kullanıcı varsa, sürüm denetimi sorunları önlemek için aşağıdaki yönergeleri kullanın:<br /><br /> -   [Sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Oluşturma veya UML veya etki alanına özgü diller uygulamanızın parçalarını yapılandırma**:<br /><br /> -Tasarımınızı gereksinimlerindeki değişiklikler daha hızlı ve kolay bir değişken bir ürün hattında olun.|-   [Oluşturma ve uygulamanızı modeller aracılığıyla yapılandırma](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Modellerini ve diyagramlarını özelleştirme**:<br /><br /> -Nasıl projenizin UML öğeleri, Modellerinizi iş kurallarınızı ve ek menü komutları ve araç kutusu öğeleri için uyduğundan emin olmak için doğrulama kısıtlamaları için ek özellikler tanımlayarak kullanmasına modellerini uyarlayın.<br />-Kendi etki alanına özgü diller oluşturun.|-   [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Visual Studio - etki alanına özgü diller için modelleme SDK'sı](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**T4 şablonlarını kullanarak metin oluşturmak**:<br /><br /> -Metin tabanlı dosyaları oluşturmak için metin blokları ve şablonları içinde denetim mantığının kullanın.|-   [Kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Model türleri ve kullanımları  
  
|**Model türünü ve tipik kullanımları**|  
|-------------------------------------|  
|**Kod haritaları**<br /><br /> Kodunuzda organizasyon ve ilişkileri görmenize yardımcı kod eşlemeleri.<br /><br /> Tipik kullanımları:<br /><br /> -Program kodu İnceleme yapısı ve bağımlılıklarını daha iyi anlamak için nasıl güncelleştirmek ve maliyetini tahmin etmek önerilen değişiklikleri.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Kod Haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Katman diyagramı**<br /><br /> Katman diyagramları Katmanlar veya açık bağımlılıkları olan bloklar kümesi olarak uygulamanın yapısını tanımlamanıza olanak sağlar. Kodda bağımlılıklar açıklandığı bir katman diyagramı üzerinde bağımlılıkları arasındaki çakışmaları bulmak için doğrulama çalıştırabilirsiniz.<br /><br /> Tipik kullanımları:<br /><br /> -Birçok değişiklik ile uygulamanın yapısını, kullanım ömrü boyunca Sabitle.<br />-Kod değişiklikleri iade etmeden önce istenmeyen bağımlılık çakışmaları keşfedin.<br /><br /> Bkz.<br /><br /> -   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML modeli**<br /><br /> Bir UML modeli sınıfı, bileşen, kullanım örneği, etkinlik ve sıralı diyagramlar dahil olmak üzere çeşitli görünümlerini içerir. UML uygulama etki alanınıza uyacak şekilde özelleştirebilirsiniz. Örneğin, etiketler, ek bilgi ve kısıtlamaları model öğelere ekleyebilirsiniz. Çalışan araçları modelleri de tanımlayabilirsiniz. Bkz: [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).<br /><br /> Tipik kullanımları:<br /><br /> -Gereksinimlerini ve tasarım açıklanmaktadır. Herhangi bir uygulama geliştirmesi için UML hızlı bir şekilde uygulayabilirsiniz. Bkz: [geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md).<br />-Oluşturma veya test veya uygulama bölümlerini yapılandırın. Bazı iş gösterimini özelleştirmek ve nesil şablonları veya yapılandırılabilir uygulama geliştirmek için gereklidir. Bkz: [oluşturur ve uygulamanızı modeller aracılığıyla yapılandırma](../modeling/generate-and-configure-your-app-from-models.md).<br />-Kod oluşturma ya da daha küçük projeleri yapılandırmasında ve için genel açıklama.|  
|**Etki alanına özgü dil (DSL)**<br /><br /> Bir DSL belirli bir amaç için tasarım bir gösterimidir. Visual Studio'da, genellikle grafik.<br /><br /> Tipik kullanımları:<br /><br /> -Oluşturma veya uygulamanın parçaları yapılandırın. İş, araçları ve gösterimi geliştirmek için gereklidir. Sonuç, etki alanınıza daha iyi bir UML özelleştirme daha uygun olabilir.<br />-Ürün serileri burada DSL ve araçlarını geliştirmeye yatırım tarafından döndürülen birden fazla proje kullanımını veya büyük projeler için.<br /><br /> Bkz.<br /><br /> -   [Visual Studio - etki alanına özgü diller için modelleme SDK'sı](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?  
  
|||  
|-|-|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yenilikler](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps ve uygulama yaşam döngüsü yönetimi](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



