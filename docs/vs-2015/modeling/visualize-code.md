---
title: Kodu görselleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 071048fba8d3663639747ea35dbae4375d101c26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738926"
---
# <a name="visualize-code"></a>Kodu görselleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirme ve modelleme araçlarını Visual Studio'da, mevcut kodu anlamanıza ve uygulamanızı tanımlamanıza yardımcı olması için kullanabilirsiniz. Bu görsel olarak yaptığınız değişiklikler kod ve iş ve bu değişikliklerden kaynaklanan riskleri değerlendirme Yardım nasıl etkileyebilecek öğrenmenize olanak tanır. Örneğin:  
  
- Kodunuzdaki ilişkileri anlamak için bu ilişkileri görsel olarak eşleyin.  
  
- Sisteminizin mimarisini ve kod, tasarım ile tutarlı tutmak için katman diyagramları oluşturun ve bu diyagramları karşı kodu doğrulayın.  
  
- Sınıf yapılarını açıklamak için sınıf diyagramları oluşturun.  
  
- Model ve sistem çeşitli yönlerini iletmek için Birleşik Modelleme Dili (UML) diyagramları çizin. Örneğin, bir sistemin bileşenleri, türleri, etkileşimleri ve işlemlerini modelleyebilir.  
  
  Bu araçlar, ayrıca daha kolay proje ile ilgili kişilerle iletişim kurmasına yardımcı olur. Örneğin, proje hissedarları, kullanıcılar ve takım üyeleri ile sistem tartışmak için ortak bir sözlüğü oluşturmak için UML sınıf diyagramları kullanabilirsiniz.  
  
  Visual Studio'nun hangi sürümlerinin her özelliğini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?  
  
|||  
|-|-|  
|**Kod ve ilişkilerini anlayın:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleyin.<br /><br /> Çözümün tamamını kodunuzdaki ilişkileri genel bir bakış görürsünüz.<br /><br /> **Not**: Visual Studio'nun bu sürümünde terimi *kod Haritası* yerine kullanılan *bağımlılık grafiği*.|-   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Kod Haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Hata ayıklarken çağrı yığınında yöntemler eşleştirme](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Sınıf yapıları anlayın:**<br /><br /> Koddan sınıf diyagramları oluşturarak bir projedeki sınıf yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Üst düzey sistem tasarımı tanımlamak ve bu tasarım karşı kodu doğrulayın:**<br /><br /> Katman diyagramları oluşturarak, üst düzey sistem tasarımı ve hedeflenen bağımlılıklarını açıklar. Kodu bir koddaki bağımlılıkları tasarım ile tutarlı kalmasını sağlamak için bu tasarım karşı doğrulayın.|-   [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)|  
|**Mimarisi ve kullanıcı gereksinimleri iletişim kurar:**<br /><br /> Yazılım sisteminizin mimarisi ve kullanıcı gereksinimleri aşağıdaki UML diyagramları çizerek modeli: etkinlik, bileşen, sınıfı, dizisi ve kullanım örneği.|-   [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)<br />-   [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)<br />-   [Uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
|**Kategori**|**Bağlantılar**|  
|------------------|---------------|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Teknik makaleler ve belgeler**|[MSDN mimari Forumu](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Çözümleme ve mimarinin modelini oluşturma](../modeling/analyze-and-model-your-architecture.md)   
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)   
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)   
 [Uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)   
 [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)



