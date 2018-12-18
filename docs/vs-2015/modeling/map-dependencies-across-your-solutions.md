---
title: Çözümlerinizdeki bağımlılıkları eşleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20122a1b254eee15efb557b5899e59fc914fda3a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740045"
---
# <a name="map-dependencies-across-your-solutions"></a>Çözümlerinizdeki bağımlılıkları eşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzdaki bağımlılıkları anlamak istediğinizde kod haritaları oluşturarak bunları görselleştirin. Bu, nasıl kod birlikte dosyaları ve kod satırlarını aracılığıyla okumadan uyduğunu görmenize yardımcı olur.  
  
 ![Çözümlerinizdeki bağımlılıkları görüntülemek](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **Bazı videoları işte**:  
  
-   [Görselleştirme yoluyla kod bağımlılıkları anlama](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [Bir değişikliğin etkisini görselleştirin](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [Kod haritaları ile karmaşık kodu anlama](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> Kod haritaları ile çalışmaya başlama  
 **Kod haritaları kullanmak için ya da ihtiyaç duyarsınız**:  
  
-   Visual Studio Enterprise: kod Haritaları, Kod Düzenleyicisi'nde, Çözüm Gezgini, sınıf görünümü ve Nesne Tarayıcısı oluşturun.  
  
-   Visual Studio Professional: kod haritalarını açmak, sınırlı düzenlemeler yapmak ve koda gitmek.  
  
> [!WARNING]
>  Visual Studio Professional kullanan Visual Studio Enterprise'da başkalarıyla oluşturulan haritalar paylaşmadan önce (örneğin, gizli öğeler, genişletilmiş gruplar ve çapraz grup bağlantılarını) eşlemedeki tüm öğelerin görünür yapıldığından emin olun.  
  
 **Bu diller, kod için bağımlılıkları eşleyebilirsiniz**:  
  
- Visual C# .NET veya Visual Basic. NET'te bir çözüm ya da derlemeleri (.dll veya .exe)  
  
- Yerel veya yönetilen C veya C++ koduna Visual C++ projelerinde, üst bilgi dosyaları (.h veya `#include`), veya ikili dosyaları  
  
- X ++ projeleri ve Microsoft Dynamics AX için .NET modüllerinden yapılan derlemeler  
  
  **Not:** dışında C# veya Visual Basic .NET projeleri için kod Haritası başlatma veya mevcut bir kod haritası için öğe ekleme için daha az seçenek vardır. Örneğin, bir C++ projesinin metin düzenleyicisinde bir nesneye sağ tıklayın ve bir kod haritasına ekleyin. Ancak, sürükleyin ve Çözüm Gezgini, sınıf görünümü ve Nesne Tarayıcısı'ndan ayrı bir kod öğeleri veya dosyaları bırakın.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Çözümünüzü arasında genel bağımlılıkları görmek için  
  
1.  Açık **mimarisi** menüsü.  
  
2.  Yalnızca açık çözüm ve henüz yerleşik yapmadıysanız veya kodunuzu son yedeklemeden bu yana değişmişse oluşturulan öğesini **çözüm için kod Haritası Oluştur**.  
  
3.  Kodunuzu son zaman, oluşturduğunuz bu yana değişmedi, seçin **olmadan çözüm oluşturmak için kod Haritası Oluştur** eşleme oluştururken daha hızlı performans sağlayın.  
  
4.  [Bkz: Genel bağımlılıkları](#SeeOverviewSource) çözümünüzü arasında genel bağımlılıkları görüntülemek için kod haritalarını nasıl kullanabileceğinizi anlamak için.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Çözümünüzdeki belirli bağımlılıkları görmek için  
  
1.  Yüklenen çözümünüzle birlikte Aç **Çözüm Gezgini**.  
  
2.  Tüm projeler, derleme başvuruları, klasörleri, dosyaları, türleri veya eşlemek istediğiniz üyeleri seçin.  
  
3.  Üzerinde **Çözüm Gezgini** araç seçin **kod haritasında Göster**![oluşturma yeni graf gelen düğümleri düğmesini seçili](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Kısayol menüsünü açın ve seçin **kod haritasında Göster**. Sınıf Görünümü veya Nesne Tarayıcısı öğelerinden bir yeni veya mevcut bir kod Haritası sürükleyebilirsiniz.  
  
4.  [Belirli bağımlılıkları görmek](#SeeSpecificSource) çözümünüz içinde belirli bağımlılıkları görüntülemek için kod haritalarını nasıl kullanabileceğinizi anlamak için.  
  
###  <a name="CreateEmptyMap"></a> Yeni bir boş bir kod Haritası çözümünüze eklemek için  
  
1.  İçinde **Çözüm Gezgini**, üst düzey çözüm düğümü için kısayol menüsünü açın. Seçin **Ekle** ardından **yeni öğe**.  
  
2.  Altında **yüklü**, seçin **genel**.  
  
3.  Sağ bölmede seçin **yönlendirilmiş grafik belgesi** seçip **Ekle**.  
  
     Artık çözümünüze ait görünür bir boş eşlemeniz de vardır **çözüm öğeleri** klasör.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Çözümünüze eklemeden bir yeni boş bir kod haritası oluşturmak için  
  
1.  Açık **mimarisi** menüsünü seçip **yeni kod Haritası**.  
  
     \- veya -  
  
2.  Açık **dosya** menüsünü seçip **yeni** seçin **dosya**.  
  
3.  Altında **yüklü**, seçin **genel**.  
  
4.  Sağ bölmede seçin **yönlendirilmiş grafik belgesi** seçip **açık**.  
  
     Artık çözümünüzün klasörlerinde görünmüyor boş bir eşlemesi var.  
  
##  <a name="SeeOverviewSource"></a> Bkz: Genel bağımlılıkları  
  
###  <a name="OverviewSource"></a> Çözümünüzü arasında bağımlılıklar bakın  
  
1. Üzerinde **mimarisi** menüsünde seçin **çözüm için kod Haritası Oluştur**.  
  
    ![Bir kod Haritası komutu oluştur](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
    Üst düzey derlemeleri ve bunların arasında toplanmış bağlantıları gösteren bir harita sahip olursunuz. Daha geniş toplama bağlantı, daha fazla bağımlılıkları, temsil eder.  
  
2. Kullanım **gösterge** düğmesini göster veya gizle (örneğin, Test, Web ve telefon projesi), proje türü simgeleri listesi için kod harita araç çubuğunda (örneğin, sınıfları, yöntemleri ve özellikleri) kod öğeleri ve ilişki türleri (örneğin, devralınan gelen Uygular ve çağırır).  
  
    ![Üst&#45;derleme düzeyinde bağımlılık grafiği](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
    Bu örnek çözüm, çözüm klasörleri içerir (**testleri** ve **bileşenleri**), Test projeleri, Web projeleri ve derlemeleri. Varsayılan olarak tüm kapsama ilişkileri görünür *grupları*, hangi genişletin ve daraltın. **Dışlar** grubu, platform bağımlılıkları da dahil olmak üzere çözümünüzün dışındaki her şeyi içerir. Dış derlemeler yalnızca kullanılan öğeleri gösterir. Varsayılan olarak, sistem temel türleri dağınıklığı azaltma için harita üzerinde gizlidir.  
  
3. Haritayı detaya gitmek için projeleri ve derlemeleri temsil eden Gruplar'ı genişletin. Her şeyi tuşlarına basarak genişletin **CTRL + A** tüm düğümleri seçerek ve ardından seçmek için **grubu**, **genişletme** kısayol menüsünden.  
  
    ![Kod Haritası'nda tüm grupların genişletilmesi](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4. Ancak, bu büyük bir çözümde için yararlı olmayabilir. Aslında, karmaşık çözümler için bellek sınırlamaları tüm grupların genişletilmesi gelen engelleyebilir. Bunun yerine, tek bir düğümde görmek için genişletin. Köşeli Çift Ayraca (aşağı ok)'ye tıklayın ve fare imlecini düğümün taşımak ne zaman görüntülenir.  
  
    ![Kod Haritası'nda bir düğümünü genişleterek](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
    Veya öğeyi seçtikten sonra artı tuşuna basarak klavye kullanın (**+**). Kodu daha ayrıntılı düzeyde keşfetmek için ad alanları, türler ve üyeler için de aynısını yapın.  
  
   > [!TIP]
   >  Kodu ile çalışma hakkında daha fazla ayrıntı için kullanarak fare, klavye ve dokunma, bkz: eşler [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).  
  
5. Haritayı basitleştirmek ve tek tek parçaları üzerinde odaklanmak için seçin **filtreleri** yalnızca seçin ve kod Haritası araç çubuğu üzerinde düğüm ve bağlantı türleri, ilgilendiğiniz. Örneğin, tüm derleme ve çözüm klasörü kapsayıcıları gizleyebilirsiniz.  
  
    ![Kapsayıcıları filtreleyerek haritayı basitleştirmek](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
    Harita, gizleme veya tek tek gruplar ve öğeleri eşlemden temel çözüm kodu etkilemeden kaldırarak ayrıca basitleştirebilir.  
  
6. Öğeleri arasındaki ilişkileri görmek için haritada seçin. Bağlantıların renklerini gösterildiği ilişki türlerini belirtmek **gösterge** bölmesi.  
  
    ![Çözümlerinizdeki bağımlılıkları görüntülemek](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
    Bu örnekte, mor bağlantıları çağrılarıdır, başvuruları noktalı bağlantılardır ve açık mavi alan erişimini bağlantılardır. Yeşil bağlantıları, devralma olabilir ya da olabilir *toplama bağlantıları* birden fazla ilişki türünü belirtin (veya *kategori*).  
  
   > [!TIP]
   >  Yeşil bir bağlantı görürseniz, bu yalnızca bir devralma ilişkisi anlamına gelmez. Ayrıca yöntem çağrısı da olabilir, ancak bu devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için onay kutularını kullanın. **filtreleri** ilginizi olmayan türleri gizlemek için bölmesi.  
  
7. Bir öğe veya bağlantı hakkında daha fazla bilgi almak için bir araç ipucu görünene kadar üstüne işaretçiyi taşıyın. Bu, bir kod öğesi veya bir bağlantıyı temsil eden kategorileri ayrıntılarını gösterir.  
  
    ![Bir ilişki kategorilerini Göster](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8. Öğeleri ve bir toplama bağlantısıyla temsil edilen bağımlılıkları incelemek için ilk bağlantıyı seçin ve ardından kısayol menüsünü açın. Seçin **katkıda bulunan bağlantıları göster** (veya **katkıda bulunan bağlantıları yeni kod haritasında Göster**). Bu bağlantının her iki ucunda grupları genişletir ve yalnızca bu öğeleri ve katılan bağımlılıkları gösterir.  
  
9. Haritada belirli kısımlarına odaklanmak için ilginizi olmayan öğeleri kaldırmak devam edebilirsiniz. Örneğin, sınıf ve üye görünümüne gitmek için yalnızca tüm ad alanı düğümleri filtre **filtreleri** bölmesi.  
  
     ![Sınıf ve üye düzeye ayrıntılara](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Başka bir karmaşık çözümü Haritası içinde odaklanmak için mevcut bir haritayı seçili öğeleri içeren yeni bir eşleme oluşturmak için yoludur. Basılı **CTRL** odaklanmak için istediğiniz öğeleri seçerken, kısayol menüsünü açın ve seçin **seçimden yeni graf**.  
  
     ![Seçili öğeleri yeni bir kod haritasında Göster](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. İçeren bağlam yeni haritaya devredilir. Çözüm klasörleri ve kullanarak görmesini istemediğiniz tüm kapsayıcıları Gizle **filtreleri** bölmesi.  
  
     ![Filtre görünümü basitleştirmek için kapsayıcıları](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Grupları Genişlet ve ilişkileri görmek için haritada öğeleri seçin.  
  
     ![İlişkileri görüntülemek için öğeleri seçin](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
    Ayrıca bkz:  
  
-   [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Tarafından kodunuzdaki olası sorunları bulma [çalışan bir çözümleyici](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Derlemeleri veya ikili dosyaları bağımlılıkları bakın  
  
1.  [Bir boş bir kod Haritası oluşturun](#GetStarted), veya varolan bir kod Haritası (.dgml dosyası) açın.  
  
2.  Derlemeleri veya ikili dosyaları harita üzerine dış Visual Studio'dan eşlemek istediğiniz sürükleyin. Örneğin, derlemeleri veya ikili dosyaları Windows Gezgini'nden veya dosya Gezgini'dan sürükleyin.  
  
> [!NOTE]
>  Yalnızca Visual Studio ve aynı kullanıcı erişim denetimi (UAC) izni düzeyinde çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini'nden derlemeleri veya ikili dosyaları sürükleyebilirsiniz. Örneğin, UAC açıksa ve Visual Studio'yu yönetici olarak çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini sürükleme işlemini engelleyecektir. Bu sorunu çözmek için hem aynı izin düzeyindeki çalıştıran veya UAC'yi kapatın emin olun.  
  
##  <a name="SeeSpecificSource"></a> Belirli bağımlılıkları bakın  
 Örneğin, bazı dosyalar ile bekleyen değişiklikleri gerçekleştirmek için bir kod incelemesi olduğunu varsayın. Bu değişiklikleri bağımlılıkları görmek için bu dosyalardan bir kod Haritası oluşturabilirsiniz.  
  
 ![Belirli bağımlılıkları kod haritasında Göster](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Çözümünüzdeki belirli bağımlılıkları bakın  
  
1.  Açık **Çözüm Gezgini**. Projeler, derleme başvuruları, klasörleri, dosyaları, türleri ve ilginizi çeken üyeleri seçin. Türler ve üyelerle ilgili bağımlılıkları olan öğeleri bulmak için tür veya üyenin kısayol menüsünden açın **Çözüm Gezgini**. Bağımlılık türünü seçin ve ardından sonuçlar'ı seçin.  
  
2.  Öğelerinizin ve üyelerinin eşleyin. Üzerinde **Çözüm Gezgini** araç çubuğunda **kod haritasında Göster**![oluşturma yeni graf gelen düğümleri düğmesini seçili](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Eşlemek istediğiniz öğeleri seçin](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  Harita içeren, derlemeler içinde seçili öğeleri gösterir.  
  
     ![Seçilen harita üzerinde gruplar olarak gösterilen öğeleri](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     Ayrıca, Çözüm Gezgini, sınıf görünümü veya nesne tarayıcısı bir boş veya mevcut bir kod Haritası öğeleri sürükleyebilirsiniz. Boş bir harita oluşturmak için bkz: [bir boş bir kod Haritası oluşturun](#GetStarted). Öğelerinize ilişkin üst öğe hiyerarşisini dahil etmek için basın ve basılı tutun **CTRL** öğeleri sürükleyin ya da kullanmak anahtar **üst öğeleri dahil** varsayılan eylemi belirtmek için kod Haritası araç çubuğu düğmesi.  
  
    > [!NOTE]
    >  Windows Phone veya Windows Mağazası gibi birden fazla uygulama arasında paylaşılan bir projeden öğeler eklediğinizde, bu öğeler etkin olan projeyle eşlemede görünür. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.  
  
4.  Öğeleri keşfetmek için onları genişletin. Fare işaretçisini bir öğenin üzerine taşıyın ve göründüğünde çift köşeli ayraç (aşağı ok) simgesine tıklayın.  
  
     ![Kod Haritası'nda bir düğümünü genişleterek](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Tüm öğeleri genişletmek için bunları seçin kullanarak **CTRL + A**, ardından harita kısayol menüsünü açın ve seçin **grubu**, **genişletme**. Ancak, tüm grupların genişletilmesi kullanılamaz bir eşlemesi veya bellek sorunları oluşturursa, bu seçenek kullanılamaz.  
  
5.  Gerekirse doğru sınıf ve üye düzeye ilgilendiğiniz öğeleri genişletmeye devam edin.  
  
     ![Grupları genişletme sınıf ve üye düzeyi](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Haritada görünmez ancak kodda üyeleri görmek için tıklayın **alt öğeleri tekrar Al** simgesi ![öğeleri tekrar Al alt simge](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") üst bir grubun sol üst köşesinde.  
  
6.  Bu harita üzerinde ilgili daha fazla öğe görmek için birini seçip **Göster ilgili** kod harita araç çubuğunda, ardından haritaya eklemek için ilgili öğeleri türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin, kısayol menüsünü açın ve ardından **göster...** Haritaya eklemek için ilgili öğe türü için seçenek. Örneğin:  
  
     İçin bir **derleme**, seçin:  
  
    |||  
    |-|-|  
    |**Bunun başvurduğu derlemeleri Göster**|Bu derlemenin başvurduğu derlemeleri ekleyin. Dış derlemeler görünür **dışlar** grubu.|  
    |**Buna başvuran derlemeleri Göster**|Çözümde bu derlemeye başvuran derlemeleri ekleyin.|  
  
     İçin bir **ad alanı**, seçin **içeren derlemenin Göster**, görünür değilse.  
  
     İçin bir **sınıfı** veya **arabirimi**, seçin:  
  
    |||  
    |-|-|  
    |**Temel türleri Göster**|Bir sınıf için taban sınıfı ve uygulanan arabirimleri ekleyin.<br /><br /> Bir arabirim için temel arabirimleri ekleyin.|  
    |**Türetilmiş türleri Göster**|Bir sınıf için türetilmiş sınıfları ekleyin.<br /><br /> Bir arabirim için türetilmiş arabirimleri ve uygulama sınıflarını veya yapılarını ekleyin.|  
    |**Bunun başvurduğu türleri Göster**|Tüm sınıfları ve bu sınıfın kullandığı üyeleri ekleyin.|  
    |**Buna başvuran türleri Göster**|Tüm sınıfları ve bu sınıfı kullanan üyelerini ekleyin.|  
    |**Namespace kapsayan Göster**|Ana ad uzayını ekleyin.|  
    |**Namespace içeren ve derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|  
    |**Tüm temel türleri Göster**|Yinelemeli olarak taban sınıf veya arabirim hiyerarşisi ekleyin.|  
    |**Tüm türetilmiş türleri Göster**|Bir sınıf için tüm türetilmiş sınıfları yinelemeli olarak ekleyin.<br /><br /> Bir arabirim için türetilmiş tüm arabirimleri ve uygulama sınıflarını veya yapılarını yinelemeli olarak ekleyin.|  
  
     İçin bir **yöntemi**, seçin:  
  
    |||  
    |-|-|  
    |**Bunun çağırdığı yöntemleri Göster**|Bu yöntemin çağırdığı yöntemleri ekleyin.|  
    |**Bunun başvurduğu alanları göster**|Bu yöntemin başvurduğu alanları ekleyin.|  
    |**Kapsayan türü Göster**|Üst türü ekleyin.|  
    |**Türü içeren, Namespace ve derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|  
    |**Geçersiz kılınan yöntemleri Göster**|Diğer yöntemleri geçersiz kılan veya bir arabirimin yöntemini uygulayan bir yöntem için geçersiz kılınan taban sınıflardaki tüm soyut ya da sanal yöntemleri ve varsa arabirimin uygulanan yöntemini ekleyin.|  
  
     İçin bir **alan** veya **özelliği**, seçin:  
  
    |||  
    |-|-|  
    |**Kapsayan türü Göster**|Üst türü ekleyin.|  
    |**Türü içeren, Namespace ve derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|  
  
     ![Bu üye tarafından çağrılır yöntemleri Göster](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  Harita ilişkileri göstermektedir. Bu örnekte, çağırılan yöntemleri `Find` yöntemi ve konumlarını çözüm veya harici olarak.  
  
     ![Belirli bağımlılıkları kod haritasında Göster](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Haritayı basitleştirmek ve tek tek parçaları üzerinde odaklanmak için seçin **filtreleri** yalnızca seçin ve kod Haritası araç çubuğu üzerinde düğüm ve bağlantı türleri, ilgilendiğiniz. Örneğin, çözüm klasörleri, derlemeler ve ad alanlarını görüntülenmesini devre dışı bırakın.  
  
     ![Görüntü basitleştirmek için Filtre bölmesini kullanın](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> C ve C++ kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları bakın  
 C++ projeleri için daha eksiksiz eşlemeleri oluşturmak istiyorsanız, bilgi derleyiciye gözatma seçeneği ayarlayın (**/FR**) bu projelerde. Bkz: [/FR, /Fr (oluşturun. SBR dosyası)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. Seçerseniz **Tamam**, bu seçeneği yalnızca geçerli eşlemesi için ayarlar. Tüm sonraki haritalar için iletiyi gizleyebilirsiniz seçebilirsiniz. Bu iletiyi Gizle ise, yeniden görünür yapabilirsiniz. Aşağıdaki kayıt defteri anahtarını ayarlayın `0` veya anahtarı silin:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**  
  
 Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca, üst bilgisi için kod haritaları oluşturmak mümkün olmayabilir (.h veya `#include`) IntelliSense veritabanı güncelleştirmeyi bitirinceye kadar dosyaları. Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz. Sorunları belirli IntelliSense ayarları devre dışı bırakıldığı için görünen veya iletileri çözmek için bkz [haritalar C ve C++ kodu için sorun giderme](#Troubleshooting).  
  
-   Tüm kaynak dosyaları ve çözümünüzdeki üstbilgi dosyaları arasındaki bağımlılıkları görmek için **mimarisi** menüsünde seçin **oluşturmak grafiği, dosyaları içerir**.  
  
     ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Şu anda açık dosya ve ilgili kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosya veya üstbilgi dosyasını açın. Dosyayı herhangi bir yeri içinde dosyanın kısayol menüsünü açın. Seçin **ekleme dosyalarının Grafını Oluştur**.  
  
     ![İlk&#45;.h dosyası için düzeyinde bağımlılık grafı](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> Haritalar C ve C++ kodu için sorun giderme  
 Bu öğeler, C ve C++ kodu için desteklenmez:  
  
- Temel türler üst hiyerarşiyi içeren ve haritalar üzerinde görünmez.  
  
- Çoğu **Göster** menü öğeleri C ve C++ kodunda kullanılmaz.  
  
  C ve C++ kodu için kod haritaları oluşturduğunuzda, bu sorunları oluşabilir:  
  
|**Sorunu**|**Olası nedeni**|**Çözümleme**|  
|---------------|------------------------|--------------------|  
|Kod Haritası oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan yapı hatalarını düzeltin ve sonra haritanın yeniden.|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir kod eşlemden oluşturmaya çalıştığınızda yanıt vermemeye başlıyor **mimarisi** menüsü.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|  
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|Belirli IntelliSense ayarları devre dışı bırakılmış [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **seçenekleri** iletişim kutusu.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz: [seçenekler, metin düzenleyici, C/C++, Gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|İleti **bilinmeyen yöntemler** bir yöntem düğümünde görünür.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Açma **/FIXED: No** bağlayıcı seçeneği.<br /><br /> Bkz: [/FIXED (sabit temel adres)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|  
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Açma **/DEBUG** bağlayıcı seçeneği.<br /><br /> Bkz: [/DEBUG (hata ayıklama bilgileri üret)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|  
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|  
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|Varsa **/pdbstrıpped** bağlayıcıda seçeneği kullanıldıysa, bunun yerine tam .pdb dosyasını dahil edin.<br /><br /> Bkz: [/pdbstrıpped (özel simgeleri)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Arayan bir dönüştürücü olduğunda, kullanmayı deneyin `_declspec(dllimport)` dönüştürücüden kaçınmak için.<br /><br /> Bkz.<br /><br /> -   [Genel kurallar ve sınırlamalar](http://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [__Declspec(dllimport) kullanarak işlev çağrılarını içeri aktarma](http://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](http://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
##  <a name="RenderMoreQuickly"></a> Kod haritaları daha hızlı işleme olun  
 İlk kez bir eşleme oluşturduğunuzda, Visual Studio bulduğu tüm bağımlılıkların dizinini oluşturur. Bu işlem, özellikle büyük çözümler için biraz zaman alabilir ancak daha sonra performansı iyileştirir. Kodunuzu değişirse, Visual Studio yalnızca güncelleştirilmiş kodun yeniden dizinini oluşturur. Harita işleme tamamlamak geçen süreyi en aza indirmek için aşağıdakileri dikkate alın:  
  
- [İlginizi çeken bağımlılıkların eşleyin.](#SeeSpecificSource)  
  
- Çözümün tamamı için harita oluşturmadan önce çözüm kapsamını azaltın.  
  
- Otomatik derleme ile çözümü kapatmak **Atla derleme** kod harita araç çubuğunda düğme.  
  
- Otomatik ile üst öğe ekleme devre dışı kapatma **üst öğeleri dahil** kod harita araç çubuğunda düğme.  
  
- Düğümlere ve bağlantılara ihtiyacınız olmayan doğrudan kaldırmak için kod Haritası dosyasını düzenleyin. Haritanın değiştirilmesi, arka plandaki kod etkilemez. Bkz: [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
  ![Skip derleme ve üst öğeleri dahil düğmeleri](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
  Visual Studio ile 1 GB bellek çalıştırabilirsiniz, ancak bilgisayarınızda en az 2 Visual Studio kod dizini ve eşleme üretir oluştururken uzun gecikmeleri önlemek için GB bellek olması önerilir.  
  
  Eşlemeleri oluşturmak veya öğeleri Çözüm Gezgini'nden bir proje öğesi ayarlandığında haritaya eklemek için daha uzun sürebilir **çıkış dizinine Kopyala** özelliği **her zaman Kopyala**. Bu, artımlı yapılarla ve Visual Studio'nun projeyi her seferinde yeniden oluşturmasıyla ilgili sorunlara neden olabilir. Performansı artırmak için bu özelliği değiştirmek **yeniyse Kopyala** veya `PreserveNewest`. Bkz: [artımlı derlemeleri](../msbuild/incremental-builds.md).  
  
  Tamamlanan harita yalnızca başarıyla oluşturulmuş kod için bağımlılıkları gösterir. Derleme hataları belirli bileşenleri meydana gelirse, bu hatalar harita üzerinde görüntülenir. Bir bileşenin gerçekten oluştuğundan ve harita üzerinde temel mimari kararlar almadan önce bağımlılıkları olduğundan emin olun.  
  
##  <a name="SavingExporting"></a> Kod haritaları paylaşın  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Harita diğer Visual Studio kullanıcılarıyla paylaşma  
 Kullanım **dosya** harita kaydetmek için menü.  
  
 veya  
  
 Haritanın harita araç çubuğunda belirli projenin bir parçası kaydetmek için seçin **paylaşımı**, **taşıma** \< *CodeMapName*>**.dgml içine**, harita kaydetmek istediğiniz projeyi seçin.  
  
 ![Bir harita başka bir projeye taşımak](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Visual Studio harita diğer Visual Studio Enterprise ve Visual Studio Professional kullanıcılarıyla paylaşabileceğiniz bir .dgml dosyası olarak kaydeder.  
  
> [!NOTE]
>  Bir harita Visual Studio Professional kullanıcılarıyla paylaşmadan önce grupları genişlettiğinizden, gizli düğümleri göstermek ve çapraz grup bağlantılarını ve başkalarının haritanızda görmesini istediğiniz silinmiş düğümleri aldığınızdan emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.  
>   
>  Bir modelleme projesinde olan ya da bir modelleme projesinden başka bir konuma kopyalanan bir harita kaydettiğinizde aşağıdaki hata oluşabilir:  
>   
>  "Kaydedilemiyor *fileName* proje dizininin dışına. Bağlantılı öğeler desteklenmez."  
>   
>  Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için harita modelleme projesinin dışında oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Microsoft Word veya PowerPoint gibi diğer uygulamalara kopyalayabilmeniz için eşlemeyi bir görüntü olarak dışarı aktarma  
  
1.  Kod Haritası araç çubuğunda **paylaşımı**, **görüntü olarak e-posta** veya **görüntüsünü kopyalama**.  
  
2.  Görüntüyü başka bir uygulamaya yapıştırın.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Harita Internet Explorer gibi XML veya XAML görüntüleyicilerde görebilmeniz için XPS dosyası olarak dışarı aktarma  
  
1.  Kod Haritası araç çubuğunda **paylaşımı**, **taşınabilir XPS olarak e-posta** veya **taşınabilir XPS olarak Kaydet**.  
  
2.  Dosyayı kaydetmek istediğiniz yere göz atın.  
  
3.  Kod Haritası adı. Emin olun **farklı kaydetme türü** kutusu ayarlandığında **XPS dosyaları (\*.xps)**. Seçin **Kaydet**.  
  
## <a name="what-else-can-i-do"></a>Başka ne yapabilirim?  
  
-   [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)



