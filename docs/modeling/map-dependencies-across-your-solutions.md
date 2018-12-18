---
title: Kod haritaları
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 51b03ce504b2fe8f588cf3e360882f97d61664f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896949"
---
# <a name="map-dependencies-with-code-maps"></a>Kod haritaları ile bağımlılıkları eşleştirme

Bir kod Haritası oluşturarak, kodunuzdaki bağımlılıkları görselleştirebilirsiniz. Nasıl kod birlikte dosyaları ve kod satırlarını aracılığıyla okumadan uyduğunu görmenize yardımcı kod eşlemeleri.

![Visual Studio'daki kod haritaları ile bağımlılıkları görüntüle](../modeling/media/codemapsmainintro.png)

Oluşturma ve kod haritaları düzenlemek için Visual Studio Enterprise edition gerekiyor. Visual Studio Community ve Professional sürümleri için Enterprise sürümünde oluşturulan şemaları açabilir, ancak onları düzenleyemezsiniz.

> [!NOTE]
> Visual Studio Professional kullanan Visual Studio Enterprise'da başkalarıyla oluşturulan haritalar paylaşmadan önce (örneğin, gizli öğeler, genişletilmiş gruplar ve çapraz grup bağlantılarını) eşlemedeki tüm öğelerin görünür olduğundan emin olun.

Bu diller, kod için bağımlılıkları eşleyebilirsiniz:

- Visual C# veya Visual Basic'te bir çözüm ya da derlemeleri (*.dll* veya *.exe*)

- Yerel veya yönetilen C veya C++ koduna Visual C++ projelerinde, üst bilgi dosyaları (*.h* veya `#include`), veya ikili dosyaları

- X ++ projeleri ve Microsoft Dynamics AX için .NET modüllerinden yapılan derlemeler

> [!NOTE]
> C# veya Visual Basic projeleri için kod Haritası başlatma veya mevcut bir kod haritası için öğe ekleme için daha az seçenek vardır. Örneğin, bir C++ projesinin metin düzenleyicisinde bir nesneye sağ tıklayın ve bir kod haritasına ekleyin. Ancak, sürükleyip bırakabilirsiniz ayrı kod öğeleri veya dosyalarından **Çözüm Gezgini**, **sınıf görünümü**, ve **Nesne Tarayıcısı**.

## <a name="install-code-map-and-live-dependency-validation"></a>Yükleme kod Haritası ve canlı bağımlılık doğrulama

Visual Studio 2017'de bir kod haritası oluşturmak için önce yükleme **kod Haritası** ve **Canlı bağımlılık doğrulama** bileşenler:

1. Açık **Visual Studio yükleyicisi**. Windows Başlat menüsünden veya Visual Studio içinden seçerek açabilirsiniz **Araçları** > **araçları ve özellikleri Al**.

1. Seçin **tek tek bileşenler** sekmesi.

1. Ekranı aşağı kaydırarak **kod Araçları** seçin ve bölüm **kod Haritası** ve **Canlı bağımlılık doğrulama**.

   ![Visual Studio Yükleyicisi'nde kod Haritası ve canlı bağımlılık doğrulama bileşenleri](media/modeling-components.png)

1. Seçin **değiştirme**.

   **Kod Haritası** ve **Canlı bağımlılık doğrulama** bileşenlerini yükleme başlar. Visual Studio'yu kapatın istenebilir.

## <a name="add-a-code-map"></a>Kod Eşlemesi Ekle

Bir boş bir kod Haritası oluşturun ve öğeleri, derleme başvuruları, dosyalar ve klasörler dahil olmak üzere sürükleyin veya tümü için kod haritası veya çözümünüzün bir parçası oluşturabilirsiniz.

Bir boş bir kod Haritası eklemek için:

1. İçinde **Çözüm Gezgini**, üst düzey çözüm düğümü için kısayol menüsünü açın. Seçin **ekleme** > **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim altında **yüklü**, seçin **genel** kategorisi.

3. Seçin **yönlendirilmiş grafik Document(.dgml)** şablonu ve ardından **Ekle**.

   > [!TIP]
   > Bu şablon kadar kaydırın, görmüyorsanız, şablon listenin alfabetik olarak görünmeyebilir.

   Çözümünüzün içinde boş bir harita görüntülenir **çözüm öğeleri** klasör.

Benzer şekilde, yeni bir kod haritası, çözümünüze seçerek eklemeden oluşturabileceğiniz **mimarisi** > **yeni kod Haritası** veya **dosya**  >  **Yeni** > **dosya**.

## <a name="generate-a-code-map-for-your-solution"></a>Çözümünüz için bir kod Haritası Oluştur

Çözümünüzdeki tüm bağımlılıkları görmek için:

1. Menü çubuğunda, **mimarisi** > **çözüm için kod Haritası Oluştur**. Kodunuzu son zaman, oluşturduğunuz bu yana değişmedi, seçebileceğiniz **mimarisi** > **olmadan çözüm oluşturmak için kod Haritası Oluştur** yerine.

   ![Bir kod Haritası komutu oluştur](../modeling/media/codemapsarchitecturemenu.png)

   Üst düzey derlemeleri ve bunların arasında toplanmış bağlantıları gösteren bir harita oluşturulur. Daha geniş toplama bağlantı, daha fazla bağımlılıkları, temsil eder.

2. Kullanım **gösterge** düğmesini göster veya gizle (örneğin, Test, Web ve telefon projesi), proje türü simgeleri listesi için kod harita araç çubuğunda (örneğin, sınıfları, yöntemleri ve özellikleri) kod öğeleri ve ilişki türleri (örneğin, devralınan gelen Uygular ve çağırır).

   ![Derlemelerin en üst düzey bir bağımlılık grafiği](../modeling/media/dependencygraph_toplevelassemblies.png)

   Bu örnek çözüm, çözüm klasörleri içerir (**testleri** ve **bileşenleri**), Test projeleri, Web projeleri ve derlemeleri. Varsayılan olarak tüm kapsama ilişkileri görünür *grupları*, hangi genişletin ve daraltın. **Dışlar** grubu, platform bağımlılıkları da dahil olmak üzere çözümünüzün dışındaki her şeyi içerir. Dış derlemeler yalnızca kullanılan öğeleri gösterir. Varsayılan olarak, sistem temel türleri dağınıklığı azaltma için harita üzerinde gizlidir.

3. Haritayı detaya gitmek için projeleri ve derlemeleri temsil eden Gruplar'ı genişletin. Her şeyi tuşlarına basarak genişletin **CTRL + A** tüm düğümleri seçerek ve ardından seçmek için **grubu**, **genişletme** kısayol menüsünden.

   ![Kod Haritası'nda tüm grupların genişletilmesi](../modeling/media/codemapsexpandallgroups.png)

4. Ancak, bu büyük bir çözümde için yararlı olmayabilir. Aslında, karmaşık çözümler için bellek sınırlamaları tüm grupların genişletilmesi gelen engelleyebilir. Bunun yerine, tek bir düğümde görmek için genişletin. Köşeli Çift Ayraca (aşağı ok)'ye tıklayın ve fare imlecini düğümün taşımak ne zaman görüntülenir.

   ![Kod Haritası'nda bir düğümü genişletme](../modeling/media/dependencygraph_containment.png)

   Veya öğeyi seçtikten sonra artı tuşuna basarak klavye kullanın (**+**). Kodu daha ayrıntılı düzeyde keşfetmek için ad alanları, türler ve üyeler için de aynısını yapın.

   > [!TIP]
   > Kodu ile çalışma hakkında daha fazla ayrıntı için kullanarak fare, klavye ve dokunma, bkz: eşler [göz atma ve yeniden düzenleme kod eşlemeleri](../modeling/browse-and-rearrange-code-maps.md).

5. Haritayı basitleştirmek ve tek tek parçaları üzerinde odaklanmak için seçin **filtreleri** yalnızca seçin ve kod Haritası araç çubuğu üzerinde düğüm ve bağlantı türleri, ilgilendiğiniz. Örneğin, tüm derleme ve çözüm klasörü kapsayıcıları gizleyebilirsiniz.

   ![Harita kapsayıcıları filtreleyerek basitleştirin](../modeling/media/codemapsfilterfoldersassemblies.png)

   Harita, gizleme veya tek tek gruplar ve öğeleri eşlemden temel çözüm kodu etkilemeden kaldırarak ayrıca basitleştirebilir.

6. Öğeleri arasındaki ilişkileri görmek için haritada seçin. Bağlantıların renklerini gösterildiği ilişki türlerini belirtmek **gösterge** bölmesi.

   ![Çözümlerinizi arasında bağımlılıklarını görüntüleme](../modeling/media/codemapsmainintro.png)

   Bu örnekte, mor bağlantıları çağrılarıdır, başvuruları noktalı bağlantılardır ve açık mavi alan erişimini bağlantılardır. Yeşil bağlantıları, devralma olabilir ya da olabilir *toplama bağlantıları* birden fazla ilişki türünü belirtin (veya *kategori*).

   > [!TIP]
   > Yeşil bir bağlantı görürseniz, bu yalnızca bir devralma ilişkisi anlamına gelmez. Ayrıca yöntem çağrısı da olabilir, ancak bu devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için onay kutularını kullanın. **filtreleri** ilginizi olmayan türleri gizlemek için bölmesi.

7. Bir öğe veya bağlantı hakkında daha fazla bilgi almak için bir araç ipucu görünene kadar üstüne işaretçiyi taşıyın. Bu, bir kod öğesi veya bir bağlantıyı temsil eden kategorileri ayrıntılarını gösterir.

   ![Bir ilişkinin kategorileri göster](../modeling/media/codemapsshowlinkcatgories.png)

8. Öğeleri ve bir toplama bağlantısıyla temsil edilen bağımlılıkları incelemek için ilk bağlantıyı seçin ve ardından kısayol menüsünü açın. Seçin **katkıda bulunan bağlantıları göster** (veya **katkıda bulunan bağlantıları yeni kod haritasında Göster**). Bu bağlantının her iki ucunda grupları genişletir ve yalnızca bu öğeleri ve katılan bağımlılıkları gösterir.

9. Haritada belirli kısımlarına odaklanmak için ilginizi olmayan öğeleri kaldırmak devam edebilirsiniz. Örneğin, sınıf ve üye görünümüne gitmek için yalnızca tüm ad alanı düğümleri filtre **filtreleri** bölmesi.

   ![Sınıf ve üye düzeye araştırıp bulma](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Başka bir karmaşık çözümü Haritası içinde odaklanmak için mevcut bir haritayı seçili öğeleri içeren yeni bir eşleme oluşturmak için yoludur. Basılı **Ctrl** odaklanmak için istediğiniz öğeleri seçerken, kısayol menüsünü açın ve seçin **seçimden yeni graf**.

    ![Seçili öğeleri yeni bir kod haritasında Göster](../modeling/media/codemapsshowonnewmap.png)

11. İçeren bağlam yeni haritaya devredilir. Çözüm klasörleri ve kullanarak görmesini istemediğiniz tüm kapsayıcıları Gizle **filtreleri** bölmesi.

    ![Filtre görünümü basitleştirmek için kapsayıcılar](../modeling/media/codemapsexpandnewgroups.png)

12. Grupları Genişlet ve ilişkileri görmek için haritada öğeleri seçin.

    ![İlişkileri görüntülemek için öğeleri seçin](../modeling/media/codemapsviewnewrelationships.png)

Ayrıca bkz:

- [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Tarafından kodunuzdaki olası sorunları bulma [bir Çözümleyicisi'ni çalıştırma](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Kod Haritası'nda belirli bağımlılıkları görüntüle

İle bazı dosyalar bekleyen değişiklikleri gerçekleştirmek için bir kod incelemesi olduğunu varsayın. Bu değişiklikleri bağımlılıkları görmek için bu dosyalardan bir kod Haritası oluşturabilirsiniz.

   ![Belirli bağımlılıkları kod haritasında Göster](../modeling/media/codemapsspecificdependenciesintro.png)

1. İçinde **Çözüm Gezgini**, projeler, derleme başvuruları, klasörleri, dosyaları, türleri veya eşlemek istediğiniz üyeleri seçin.

   ![Eşlemek istediğiniz öğeleri seçin](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Üzerinde **Çözüm Gezgini** araç seçin **kod haritasında Göster** ![oluşturma yeni graf gelen düğümleri düğmesini seçili](../modeling/media/createnewgraphfromselectedbutton.gif). Veya, bir veya bir Grup öğesi için kısayol menüsünü açın ve seçin **kod haritasında Göster**.

   Öğeleri sürükleyerek de **Çözüm Gezgini**, **sınıf görünümü**, veya **Nesne Tarayıcısı**, içine bir [yeni](#add-a-code-map) veya var olan kod eşleme. Öğelerinize ilişkin üst öğe hiyerarşisini dahil etmek için basın ve basılı tutun **Ctrl** öğeleri sürükleyin ya da kullanmak anahtar **üst öğeleri dahil** varsayılan eylemi belirtmek için kod Haritası araç çubuğu düğmesi. Visual Studio dışında derleme dosyalarından gibi gelen sürükleyebilirsiniz **Windows Explorer**.

   > [!NOTE]
   > Windows Phone veya Microsoft Store gibi birden fazla uygulama arasında paylaşılan bir projeden öğeler eklediğinizde, bu öğeler etkin proje harita üzerinde görünür. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

3. Harita içeren, derlemeler içinde seçili öğeleri gösterir.

   ![Harita üzerinde gruplar olarak gösterilen seçilen öğeler](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Öğeleri keşfetmek için onları genişletin. Fare işaretçisini bir öğenin üzerine taşıyın ve göründüğünde çift köşeli ayraç (aşağı ok) simgesine tıklayın.

   ![Kod Haritası'nda bir düğümünü genişletin](../modeling/media/dependencygraph_containment.png)

   Tüm öğeleri genişletmek için bunları seçin kullanarak **Ctrl**+**A**, ardından harita kısayol menüsünü açın ve seçin **grubu**  >   **Genişletin**. Ancak, tüm grupların genişletilmesi kullanılamaz bir eşlemesi veya bellek sorunları oluşturursa, bu seçenek kullanılamaz.

5. Doğru sınıf ve üye düzeye gerekirse ilgilendiğiniz öğeleri genişletmeye devam edin.

   ![Sınıf ve üye düzeyine Grupları Genişlet](../modeling/media/codemapsexpandtoclassandmember.png)

   Haritada görünmez ancak kodda üyeleri görmek için tıklayın **alt öğeleri tekrar Al** simgesi ![öğeleri tekrar Al alt simge](../modeling/media/dependencygraph_deletednodesicon.png) bir grubun sol üst köşedeki.

6. Bu harita üzerinde ilgili daha fazla öğe görmek için birini seçip **Göster ilgili** kod harita araç çubuğunda, ardından haritaya eklemek için ilgili öğeleri türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin, kısayol menüsünü açın ve ardından **Göster** haritaya eklemek için ilgili öğe türü için seçeneği. Örneğin:

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

    ![Bu üye tarafından çağrılır yöntemleri Göster](../modeling/media/codemapsshowrelatedmethods.png)

7. Harita ilişkileri göstermektedir. Bu örnekte, harita çağıran yöntemleri gösterir. `Find` yöntemi ve konumlarını çözüm veya harici olarak.

   ![Belirli bağımlılıkları kod haritasında Göster](../modeling/media/codemapsspecificdependenciesintro.png)

8. Haritayı basitleştirmek ve tek tek parçaları üzerinde odaklanmak için seçin **filtreleri** yalnızca seçin ve kod Haritası araç çubuğu üzerinde düğüm ve bağlantı türleri, ilgilendiğiniz. Örneğin, çözüm klasörleri, derlemeler ve ad alanlarını görüntülenmesini devre dışı bırakın.

   ![Görüntü basitleştirmek için Filtre bölmesini kullanma](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Video: Visual Studio 2015 kod haritaları ile koddan tasarımı anlama](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
