---
title: Kodunuz aracılığıyla katman diyagramları oluşturma | Microsoft Docs
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
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0a1c5af9394f36f7f89a20b711657a3ca76e8d1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727292"
---
# <a name="create-layer-diagrams-from-your-code"></a>Kodunuz aracılığıyla katman diyagramları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için oluşturma bir *katman diyagramı* Visual Studio'da. Kodunuzun tasarımla tutarlı kalmasını sağlamak için kodunuzu katman diyagramıyla doğrulayın. Visual C# .NET ve Visual Basic .NET projeleri için katman diyagramları oluşturabilirsiniz. Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Katman diyagramı oluşturma](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Bir katman diyagramı, Visual Studio çözüm öğeleri adı verilen mantıklı, soyut gruplar halinde düzenlemenizi sağlar *katmanları*. Bu yapıların gerçekleştirdiği temel görevleri veya sistemin ana bileşenlerini açıklamak için katmanları kullanabilirsiniz. Her katman, daha ayrıntılı görevleri açıklayan başka katmanlar içerebilir. Hedeflenen veya varolan de belirtebilirsiniz *bağımlılıkları* katmanlar arasında. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevi kullanabileceğini veya kullanmakta olduğunu gösterir. Kodunun mimari denetimini sağlamak için diyagram üzerinde hedeflenen bağımlılıkları gösterin ve ardından kodu diyagrama karşı doğrulayın.  
  
##  <a name="CreateDiagram"></a> Katman diyagramı oluşturma  
 Bir katman diyagramı oluşturmadan önce, çözümünüzde bir modelle projesi olduğundan emin olun. Bkz: [oluşturma UML modelleme projeleri ve diyagramları](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
> [!IMPORTANT]
>  Varolan katman diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözüm içindeki başka bir yere eklemeyin, kopyalamayın veya sürüklemeyin. Bu, diyagramı değiştirseniz bile orijinal diyagramdan yapılan başvuruları korur. Bu, katman doğrulamasının doğru çalışmasını da engeller ve siz diyagramı açmaya çalışırken kayıp öğeler veya başka hatalar gibi diğer sorunlara da neden olabilir.  
>   
>  Bunun yerine, modelleme projesine yeni bir katman diyagramı ekleyin. Öğeleri kaynak diyagramdan yeni diyagrama kopyalayın. Hem modelleme projesini hem de yeni katman diyagramını kaydedin.  
  
#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Modelleme projesine yeni bir katman diyagramı eklemek için  
  
1.  Üzerinde **mimarisi** menüsünde seçin **yeni UML veya katman diyagramı**.  
  
2.  Altında **şablonları**, seçin **katman diyagramı**.  
  
3.  Diyagrama ad verin.  
  
4.  İçinde **modelleme projesine Ekle**göz atın ve çözümünüzde varolan modelleme projesini seçin.  
  
     veya  
  
     Seçin **yeni modelleme projesi oluşturma** çözüme yeni bir modelleme projesi eklemek için.  
  
    > [!NOTE]
    >  Katman diyagramı modelleme projesinin içinde olmalıdır. Bununla birlikte, bunu çözümün herhangi bir yerindeki öğelere bağlayabilirsiniz.  
  
5.  Hem modelleme projesini hem de katman diyagramını kaydettiğinizden emin olun.  
  
##  <a name="CreateLayers"></a> Yapılardan katmanlar oluşturma  
 Visual Studio çözüm öğelerinden projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi katmanlar oluşturabilirsiniz. Bu, katmanlar ve öğeler arasında otomatik olarak bağlantılar oluşturarak bunları katman doğrulama işlemine dahil eder.  
  
 Katmanları Word belgeleri veya PowerPoint sunumları gibi doğrulamayı desteklemeyen öğelere de ekleyebilir ve böylece bir katmanı belirtimlerle veya planlarla ilişkilendirebilirsiniz. Katmanları birden fazla uygulama arasında paylaşılan projelerdeki dosyalara da bağlayabilirsiniz, ancak doğrulama işlemi "Katman 1" ve "Katman 2" gibi genel adlarla görünen bu katmanları içermez.  
  
 Bağlı öğenin doğrulamayı destekleyip desteklemediğini görmek için **Katman Gezgini** ve incelemek **doğrulamayı destekler** öğesinin özelliği. Bkz: [yapıların bağlantılarını yönetme](#Managing).  
  
|**Hedef**|**Aşağıdaki adımları izleyin**|  
|------------|----------------------------|  
|Tek bir yapı için katman oluşturma|<ol><li>Öğesi, bu kaynaklardan katman diyagramına sürükleyin:<br /><br /> <ul><li>**Çözüm Gezgini**<br /><br />         Örneğin, dosyaları veya projeleri sürükleyebilirsiniz.</li><li>Kod haritaları<br /><br />         Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md) ve [kullanmak kod eşlemeleri uygulamalarınızda hata ayıklamak için](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Sınıf Görünümü** veya **Nesne Tarayıcısı**</li></ul><br />     Katman, diyagramda görünür ve yapıya bağlanır.</li><li>İlişkili kodun veya yapıların sorumluluklarını yansıtmak için katmanı yeniden adlandırın.</li></ol> **Önemli:** ikili dosyaların katman diyagramına sürüklenmesi otomatik olarak eklemez başvurularını modelleme projesi için. Doğrulamak istediğiniz ikili dosyaları el ile modelleme projesine eklemeniz gerekir. **Modelleme projesine ikili dosyalar eklemek için** <ol><li>İçinde **Çözüm Gezgini**, modelleme projesi için kısayol menüsünü açın ve ardından **varolan öğeyi Ekle**.</li><li>İçinde **varolan öğeyi Ekle** iletişim kutusunda ikili dosyalara göz atın, bunları seçin ve ardından **Tamam**.     İkili dosyalar modelleme projesinde görünür.</li><li>İçinde **Çözüm Gezgini**, eklenen ve ENTER tuşuna basın bir ikili dosya **F4** açmak için **özellikleri** penceresi.</li><li>Her ikili dosyası üzerinde ayarlı **derleme eylemi** özelliğini **doğrulama**.</li></ol>|  
|Seçilen tüm yapılar için tek bir katman oluşturma|Tüm yapıları aynı anda katman diyagramına sürükleyin.<br /><br /> Katman diyagramda görünür ve tüm yapılara bağlıdır.|  
|Seçilen her yapı için bir katman oluşturma|Basılı **SHIFT** aynı anda tüm yapıları katman diyagramına sürüklerken tuşu. **Not:** kullanırsanız **SHIFT** anahtarı bir öğe aralığı seçmek için yapıları seçtikten sonra tuşu serbest bırakın. Yapıları diyagrama sürüklerken tuşu tekrar basılı tutun. <br /><br /> Katman her yapı için diyagramda görünür ve her yapıya bağlanır.|  
|Katmana yapı ekleme|Yapıyı katmana sürükleyin.|  
|Bağlantısız bir katman oluşturma|İçinde **araç kutusu**, genişletin **katman diyagramı** bölümüne ve ardından bir **katman** katman diyagramına.<br /><br /> Çoklu katman eklemek için araca çift tıklayın. İşlemi tamamladığınızda, seçin **işaretçi** aracını veya basın **ESC** anahtarı.<br /><br /> - veya -<br /><br /> Katman diyagramının kısayol menüsünü açın, **Ekle**ve ardından **katman**.|  
|İç içe katmanlar oluşturma|Varolan katmanı başka bir katmanın üzerine sürükleyin.<br /><br /> - veya -<br /><br /> Katmanın kısayol menüsünü açın, **Ekle**ve ardından **katman**.|  
|Varolan iki veya daha fazla katmanı içeren yeni bir katman oluşturma|Katmanları seçin, seçiminizin kısayol menüsünü açın ve ardından **grubu**.|  
|Katmanın rengini değiştirme|Ayarlama, **renk** özelliğini istediğiniz rengi.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın ad alanlarını yazın **Yasak Ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın ad alanlarını yazın **Yasak Namespace bağımlılıkları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın ad türü **gerekli ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
  
 Bir katmandaki sayı, katmana bağlı olan yapıların sayısını gösterir. Ancak, bu sayıyı okurken, aşağıdakileri unutmayın:  
  
-   Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.  
  
     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.  
  
-   Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.  
  
##  <a name="Managing"></a> Katmanlar ve Yapılar arasındaki bağlantıları yönetme  
  
1.  Katman diyagramında katmanın kısayol menüsünü açın ve ardından **bağlantıları görüntüle**.  
  
     **Katman Gezgini** seçili katman için yapı bağlantılarını gösterir.  
  
2.  Bu bağlantıları yönetmek için aşağıdaki görevleri kullanın.  
  
|**Hedef**|**Katman Gezgini**|  
|------------|---------------------------|  
|Katman ve yapı arasındaki bağlantıyı silme|Yapı bağlantısının kısayol menüsünü açın ve ardından **Sil**.|  
|Bağlantıyı bir katmandan diğerine taşıma|Yapı bağlantısını diyagramda varolan bir katmana sürükleyin.<br /><br /> - veya -<br /><br /> 1.  Yapı bağlantısının kısayol menüsünü açın ve ardından **Kes**.<br />2.  Katman diyagramında katmanın kısayol menüsünü açın ve ardından **Yapıştır**.|  
|Bağlantıyı bir katmandan diğerine kopyalama|1.  Yapı bağlantısının kısayol menüsünü açın ve ardından **kopyalama**.<br />2.  Katman diyagramında katmanın kısayol menüsünü açın ve ardından **Yapıştır**.|  
|Varolan yapı bağlantısından yeni bir katman oluşturma|Yapı bağlantısını diyagramdaki boş bir alana sürükleyin.|  
|Bağlantılı bir yapının, katman diyagramına karşı doğrulamayı desteklediğini onaylayın.|Bakmak **doğrulamayı destekler** Yapı bağlantısını için sütun.|  
  
##  <a name="Discovering"></a> Varolan bağımlılıklara ters mühendislik  
 Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Diyagramdaki katmanlara bağlanmış yapılar için varolan bağımlılıklara ters mühendislik uygulayabilirsiniz.  
  
> [!NOTE]
>  Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıların ters mühendislik uygulayabileceğiniz bağımlılıkları olduğunu görmek için bir veya daha fazla katmanın kısayol menüsünü açın ve ardından **bağlantıları görüntüle**. İçinde **Katman Gezgini**, inceleyin **doğrulamayı destekler** sütun. Bağımlılıklar, bu sütunda görüntülenir yapıtlar için ters mühendislik olmayacak **False**.  
  
- Bir veya birden fazla katman seçin, seçilen katmanın kısayol menüsünü açın ve ardından **Bağımlılıklar Oluştur**.  
  
  Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.  
  
##  <a name="EditDependencies"></a> Katmanları ve bağımlılıkları hedeflenen tasarımı göstermek için düzenleme  
 Sisteminizde veya hedeflenen mimaride yapmayı planladığınız değişiklikleri açıklamak için katman diyagramını düzenleyin:  
  
|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|  
|------------|-----------------------------|  
|Bağımlılık yönünü değiştirme veya kısıtlama|Ayarlama, **yönü** özelliği.|  
|Yeni bağımlılıklar oluşturma|Kullanım **bağımlılık** ve **çift yönlü bağımlılık** araçları.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. İşlemi tamamladığınızda, seçin **işaretçi** aracını veya basın **ESC** anahtarı.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın ad alanlarını yazın **Yasak Namespace bağımlılıkları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın ad alanlarını yazın **Yasak Ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın ad türü **gerekli ad alanları** özelliği. Noktalı virgül kullanın (**;**) ad alanlarını ayırmak için.|  
  
##  <a name="EditLayout"></a> Öğelerin diyagramda görüntülenme şeklini değiştirme  
 Özelliklerini düzenleyerek katmanların boyutunu, şeklini, rengini ve konumunu veya bağımlılıkların rengini değiştirebilirsiniz.  
  
##  <a name="Codemaps"></a> Desenler ve kod haritasında bağımlılıklarını keşfedin  
 Katman diyagramları oluştururken, aynı zamanda oluşturacağınız **kod haritaları**. Bu diyagramları Kodu Keşfetme sırasında desenleri ve bağımlılıkları keşfetmenize yardımcı olabilir. Derlemeler, ad alanlarını ve genellikle de varolan katmanlarla - sınıfları keşfetmek için Çözüm Gezgini, sınıf görünümü ve Nesne Tarayıcısı'nı kullanın. Kod haritaları hakkında daha fazla bilgi için bkz:  
  
-   [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kanal 9 Video: Tasarlayın ve katman diyagramlarını kullanarak Mimarinizi doğrula](http://go.microsoft.com/fwlink/?LinkID=252073)   
 [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)   
 [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)   
 [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)   
 [Kodu görselleştirme](../modeling/visualize-code.md)