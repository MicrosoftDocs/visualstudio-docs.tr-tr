---
title: UML modellerini ve diyagramları genişletme | Microsoft Docs
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
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 74f3c518682997dca57a630c6f084437f7175d80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794770"
---
# <a name="extend-uml-models-and-diagrams"></a>UML modellerini ve diyagramları genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu UML modelleme araçları Visual Studio'ya dahil edildi genişletebileceğiniz farklı yollarını özetler. Her model türünü ve aracı Visual Studio'nun hangi sürümlerinin desteklediği için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Aşağıdaki örnek senaryoyu, Fabrikam tasarlar ve havaalanı bagaj sistemleri işleme yükler. Sonraki bir Havalimanı projeden temel donanım ve onu denetleyen bir yazılım benzer vardır. Ancak, aynı zamanda taşıyıcı bantları, iade etme masalarını, depo depolama ve işleme diğer paketi yapılandırma gibi büyük ölçüde farklılık gösteren birkaç faktör vardır.  
  
 Yeni bir proje başlatılırken Fabrikam ekibi aralarında ve müşterilerle bu gereksinimleri görüşmek yardımcı olması için bir UML modeli oluşturur. Etkinlik diyagramları ekipman her parçasını temsil eden nesne düğümleri ile paketleri akışını göstermek için kullanırlar. UML modeli doğrudan sistemin kodunu temsil etmiyor.  
  
 Fabrikam'ın araçları takım geliştirme ekipleri yardımcı olacak bir dizi sağlar. Aşağıdaki bölümlerde, farklı türlerde tanımlayabileceğiniz uzantıları açıklanmaktadır. Bir Visual Studio Uzantısı'na aşağıdaki tekniklerden birini birleştirebilirsiniz.  
  
 Bu videoda daha fazla bilgi için bkz: ![video bağlantı](../data-tools/media/playvideo.gif "PlayVideo")[MSDN nasıl yaparım serisi: UML araçları ve genişletilebilirlik](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
##  <a name="Requirements"></a> Gereksinimleri  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
-   [Visual Studio 2015 için modelleme SDK](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profiller  
 Profilleri, UML öğeleri üzerinde stereotipler ve ek özellikler tanımlamanıza olanak tanır.  
  
 Fabrikam'ın aracı geliştiricileri «taşıyıcı bandı» gibi etkinlik diyagramlarındaki nesne düğümleri üzerinde stereotipler tanımlayın ve «iade etme Masası». Bir takım üyesi bagaj işleme düzeni etkinlik diyagramı kullanarak oluşturduğunda, bunlar artık stereotipler her düğümün temsil ettiği donanım türünü belirtmek için ayarlayabilirsiniz. Kullanıcılar bir taşıyıcı bandı kapasitesini ve bir iade etme masasına taşınabilirliğini gibi değerler kaydedebilmesi için araç geliştiricileri stereotipler bazılarında ek özelliklerini tanımlayın.  
  
 Daha fazla bilgi için [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Özel araç kutusu öğeleri  
 Özel araç kutusu öğesi, bir diyagramda tanımlayan bir prototipten bir öğeyi veya öğelerin bir grup oluşturur. Örneğin, belirli bir renk veya stereotip veya tasarım deseni temsil eden bir grup sınıfları ve ilişkileri kullanım örneklerini oluşturan bir aracı oluşturabilirsiniz. Bu araç kutusu öğeleri eklemek için Visual Studio uzantıları ve diğer kullanıcılara dağıtın.  
  
 Daha fazla bilgi için [tanımlayan özel bir modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Doğrulama  
 Bir UML modeli, belirtilen kısıtlamalara uyduğundan emin olmak için kurallar tanımlayabilirsiniz.  
  
 Fabrikam'ın aracı geliştiricileri, takım üyelerinin bagaj işleme modellerinde basit hataları önlemenize yardımcı kurallar tanımlayın. Örneğin, bir iade etme masasına bir depolama birimine doğrudan bağlanamaz. En az olmalıdır bir taşıyıcı bandı bunlar arasında.  
  
 Daha fazla bilgi için [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Menü Komutları  
 Kullanıcılar bir UML diyagram üzerindeki öğeleri sağ tıklayarak çağırabilirsiniz komutları tanımlayabilirsiniz. Komutlar model ve diyagramları güncelleştirin veya diğer işlemleri [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Fabrikam sık gerçekleştirilen işlemleri otomatikleştirin, gibi bir iade masasına oluşturmak ve seçili taşıyıcı bandına bağlanmak veya diyagram şirketin Düzen kurallara göre yeniden düzenlemek için menü komutlarını tanımlar.  
  
 Bkz: [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Hareketler  
 Bir diyagram öğesini çift tıklayarak ya da diyagramda bir diyagram veya öğenin sürükleyerek başlatabilecek kullanıcıları komutları tanımlayabilirsiniz. Visual Studio ya da diğer uygulamalar veya Windows Explorer (veya dosya Gezgini. diğer kısımlarından UML diğer diyagramlardan sürüklenen öğeler ile giderebilirsiniz komutları tanımlayabilirsiniz.  
  
 Fabrikam takım üyeleri Windows masaüstünden sürükleyerek dosya belirtimini gibi herhangi bir model öğesi ile ilişkilendirebilirsiniz. Araç geliştiricileri, herhangi bir öğe bir dosya yolu özelliği ve öğenin üzerine bir dosya bırakıldığında stereotip ve dosya yolu ayarlar hareket sağlayan bir stereotip tanımlanır.  
  
 Daha fazla bilgi için [modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Değişikliklere yanıt verme  
 Kullanıcı eylemleri veya başka bir program kodu neden olmadığını modelindeki değişikliklere yanıt veren kodu yazabilirsiniz.  
  
 Fabrikam'ın Geliştirici otomatik olarak bir öğenin rengini, stereotip bağımlı ayarlayan kodu oluşturur. Bu, kullanıcıların modellerdeki öğeler tarafından yürütülen farklı rollere ayırt etmek kolaylaştırır.  
  
 Daha fazla bilgi için [nasıl yapılır: bir UML modelindeki değişikliklere yanıt](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Model veri yolu  
 Model veri yolu başka bir diyagrama veya başka bir diyagrama veya model erişmenize olanak sağlayan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantısı. Birleşik model üzerinde aynı anda birkaç kişinin çalışabilmek yanı sıra, bu, birden fazla model arasında bilgi yaymak sağlar.  
  
 Fabrikam bagaj işleme donanımını temsil etmek için etkinlik diyagramları üzerinde öğeler kullanır. Daha ayrıntılı bir belirtim donanımın her öğesi, başka bir modelde olabilecek başka bir diyagrama sahip olabilir. Doğrulama kısıtlamaları bagaj akış diyagramı diğer diyagramlardan ilgili donanım özelliklerini alabilir. Diğer diyagramlarla başvuruları ek özellikleri stereotiplerin tanımlanan depolanır.  
  
 Daha fazla bilgi için [tümleştirme UML modellerini diğer modeller ve araçlarla birlikte](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Oluşturma  
 Bir modelden, program kodu, betikleri, yapılandırmaları, belge, yeni modeller veya diğer yapıtlar oluşturabilirsiniz.  
  
 Fabrikam tasarlar bagaj sistemlerinde, program kodu çoğunu bir projeden diğerine aynıdır. Önemli değişken havaalanı etrafında bagaj flow planını yönüdür. Tasarım ekibi, deneyimi ilk birkaç projelerini oluşmuş sonra araç geliştiricileri oluşturur, bagaj akış modelinden çok değişken program kodu ve diğer dosyaları kullanıcı belgeleri gibi bir şablon oluşturun. Bu, her yeni proje için geliştirme zamanı ve hata oranı önemli ölçüde azaltır.  
  
 Daha fazla bilgi için [bir UML modelinden dosyalar oluşturma](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server tümleştirmesi  
 İş öğelerini model öğelere bağlar ve bağlantılı öğeler programlamayla erişme.  
  
 Fabrikam'ın aracı geliştiricileri her havaalanı projesi için iş zamanlama oluşturan bir aracı yazın. Zamanlamadaki iş öğelerini model öğelere bağlıdır.  
  
 Daha fazla bilgi için [bir iş öğesi bağlantı işleyicisini tanımlama](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Modelleri güncelleştirme araçları  
 Tek başına uygulamalar ve UML modellerini yükleyebilir ve Visual Studio uzantılarını oluşturabilirsiniz.  
  
 Fabrikam'ın geliştiricileri bir modeli okuyan ve modelin her bir öğede işin ilerleme raporları oluşturur bir aracı oluşturun.  
  
 Daha fazla bilgi için [program kodundaki UML modelini okuma](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Etki alanına özgü diller  
 Belirli bir model türü, sık kullandığınız, bir etki alanına özgü dil oluşturma faydalı olabilir. Bir UML modeli daha yakından iş gereksinimlerinize uyacak şekilde yapılabilir ancak derleyin ve sürdürmek daha fazla çaba gerektirir. Daha fazla bilgi için [Visual Studio - etki alanına özgü diller için modelleme SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
|**Kategori**|**Bağlantılar**|  
|------------------|---------------|  
|**Videolar**|![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [MSDN nasıl yaparım serisi: UML araçları ve genişletilebilirlik](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML Visual Studio ile](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Teknik makaleler ve belgeler**|[MSDN Mimari Merkezi](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)   
 [UML Genişletilebilirlik Modellemesi için API Başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md)



