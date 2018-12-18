---
title: Kod haritalarına göz atma ve bunları yeniden düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3b3a751a25d65560a85d853e083a4bbdd33b91ac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921684"
---
# <a name="browse-and-rearrange-code-maps"></a>Kod haritalarına göz atma ve bunları yeniden düzenleme

Okuma ve bunların performansı daha kolay hale getirmek için kod haritalarını öğelerde yeniden düzenleyin.

Kod haritaları bir çözümde temel kodu etkilemeden özelleştirebilirsiniz. Önemli kod öğeleri üzerinde odaklanmak veya kodla ilgili iletişim kurmak istediğinizde bu kullanışlıdır. Örneğin, ilginç alanları vurgulamak için haritadaki kod öğelerini seçin ve filtreleyebilir, kod öğeleri ve bağlantıların stilini değiştirmek, Gizle veya kod öğelerini silin ve özellikleri, kategorileri veya grupları kullanarak kod öğelerini düzenlemek.

 **Gereksinimler**

-   Kod haritaları oluşturmak için Visual Studio Enterprise'ı olması gerekir.

-   Kod haritaları görüntüleyebilir ve kod haritaları ile Visual Studio Professional için sınırlı düzenlemeler yapmak.

##  <a name="ManageLargeGraphs"></a> Kod haritaları ile çalışmaya başlama

Bir kod Haritası oluşturun (bkz [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md) daha fazla ayrıntı için). Harita oluşturma işleminin tamamlanması beklenecek istemiyorsanız **iptal** oluşturma işlemini durdurmak için herhangi bir zamanda bağlantı. Ancak bunu yaparsanız tüm bağımlılıkları ve bağlantı ayrıntılarını görmemeniz.

Harita oluşturduktan sonra kodunuzu gözden geçirme için bu ipuçlarını kullanmaya başlayın:

-   Kod doğal bağımlılık kümelerinde bakın. Harita araç çubuğunda **Düzen**, **hızlı kümeler**![Grafik araç çubuğu düğmesi hızlı kümeler](../modeling/media/quickclustersicon.gif). Bkz: [eşleme düzenini](#Selecting).

     ![Bağımlılık grafiği &#45; hızlı kümeler yerleşimini](../modeling/media/dependencygraph_quickclusters.png)

-   Harita, ilgili düğümlerin gruplandırarak daha küçük alanlarına düzenleyin. Otomatik olarak görünen yalnızca intergroup bağımlılıkları görmek için bu grupları daraltabilirsiniz. Bkz: [Grup düğümleri](#OrganizeGroups).

-   Haritayı basitleştirmek ve düğümlere veya bağlantılara ilgilendiğiniz türlerini odaklanmak için filtreleri kullanın. Bkz: [filtre düğümlere ve bağlantılara](#FilterNodes).

-   Büyük haritalar performansını en üst düzeye çıkarın. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md) daha fazla bilgi için. Örneğin, açma **Atla derleme** eşlemedeki öğeler güncelleştirdiğinizde, Visual Studio çözümünüzü yeniden olmayan şekilde harita araç çubuğunda.

##  <a name="Selecting"></a> Harita düzenini değiştirme

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Belirli bir yönde tüm harita bağımlılık akışını düzenleyin. Bu mimari katmanları kodda görmenize yardımcı olabilir.|Harita araç çubuğunda **Düzen**ve ardından:<br /><br /> -   **Yukarıdan aşağıya doğru** ![yukarıdan alt graf düğmesi](../modeling/media/topbottomgraphbutton.gif)<br />-   **Aşağıdan yukarıya** ![üst grafik düğme alt](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Soldan sağa** ![doğru düzene düğmeye sol](../modeling/media/leftrightgraphbutton.gif)<br />-   **Sağdan sola** ![sol Grafik düğmesini hakkı](../modeling/media/rightleftgraphbutton.gif)|
|Kod merkezinde kümelerinin en bağımlı düğümleri ve az bağımlı düğümler dışarıdan bu kümelerin kümelerindeki doğal bağımlılık bakın.|Harita araç çubuğunda **Düzen**, ardından **hızlı kümeler**![Grafik araç çubuğu düğmesi hızlı kümeler](../modeling/media/quickclustersicon.gif).|
|Harita üzerinde bir veya daha fazla düğüm seçin.|Bir düğümde seçmek için tıklayın. Seçin veya birden fazla düğüm seçimini kaldırmak için tutun **CTRL** tıklatırken.<br /><br /> Klavye: basın **sekmesini** veya bir düğüm ve ENTER'a basın noktalı odak dikdörtgeni taşımak için ok tuşlarını kullanın **alanı** seçin. Tuşuna **CTRL** + **alanı** çoklu seçim için veya düğümlerin seçimini kaldırın.|
|Harita üzerinde belirli düğümler hareket ettirin.|Bunları taşımak için düğümleri sürükleyin. Diğer düğümlere ve bağlantılara göz önünden düğümler, sürüklerken basın ve basılı tutun taşımak **SHIFT** anahtarı.<br /><br /> Klavye: tutun **CTRL** ve OK tuşlarına basın.|
|Diğer düğümlere bağımsız olarak bir grup ve harita üzerinde gruplar içinde düzenini değiştirin.|Bir düğüm seçin ve kısayol menüsünü açın. Seçin **Düzen** ve bir düzen stili seçin.<br /><br /> - veya -<br /><br /> Bir düğüm seçin ve alt düğümleri göstermek için genişletin. Grup açılır araç çubuğunu gösterme ve açmak için düğümü başlığını tıklatın **grubun yerleşim stilini değiştir**![bağımlılık grafiği &#45; grubu araç &#45; Düzen](../modeling/media/dependencygraph_grouptoolbar.gif) listesi. Bir ağaç düzeni seçin **hızlı kümeler**, veya **liste görünümü** (hangi düzenler grubun içeriğinin bir liste olarak).<br /><br /> Bkz: [Grup düğümleri](#OrganizeGroups) daha fazla ayrıntı için.|
|Eşlem içindeki bir eylemi geri al.|Tuşuna **CTRL** + **Z** veya Visual Studio **geri** komutu.|

##  <a name="Explore"></a> Harita Gözat

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Harita tarayın.|Harita herhangi bir yönde fareyle sürükleyin.<br /><br /> - veya -<br /><br /> Basılı **SHIFT** ve yatay kaydırma için fare tekerleğini döndürün. Basılı **SHIFT** + **CTRL** ve yatay kaydırma için fare tekerleğini döndürün.|
|İçine veya dışına harita yakınlaştırma.|Fare tekerleğini döndürün.<br /><br /> - veya -<br /><br /> Kullanım **yakınlaştırma** kod Haritası araç çubuğundaki açılan liste.<br /><br /> - veya -<br /><br /> Klavye kısayollarını kullanın. Yakınlaştırmak için basın **CTRL + SHIFT +.** (nokta). Uzaklaştırmak için basın **CTRL + SHIFT +,** (ayrılmış).|
|Fareyi kullanarak belirli bir alanı yakınlaştırın.|Sağ fare düğmesine ilgilendiğiniz o alanı çevresinde bir dikdörtgen çizerken tutun.|
|Yeniden boyutlandırma ve kendi pencere haritada uygun.|Seçin **sığacak kadar Yaklaştır** gelen **yakınlaştırma** kod harita araç çubuğunda listesi.<br /><br /> - veya -<br /><br /> Tıklayın **sığdırmak için Yakınlaştır** simgesi ![harita araç çubuğundaki Yakınlaştır simgesi](../modeling/media/almcodemapzoomicon.png) kod harita araç çubuğunda. Klavye: basın **CTRL + 0** (sıfır).|
|Bir düğüm, sunucu adına göre harita üzerinde bulun. **İpucu:** bu öğeler için harita üzerinde çalışır. Çözümünüzdeki ancak harita öğelerini bulmak için bunları bulma **Çözüm Gezgini**ve ardından bunları haritasına sürükleyin. (Sizin seçiminiz sürükleyin veya **Çözüm Gezgini** araç çubuğunda tıklatın **kod haritasında Göster**).|1.  Seçin **Bul** simgesi ![harita araç çubuğunda Bul simgesi](../modeling/media/almcodemapfindicon.png) kod harita araç çubuğunda (klavye: basın **CTRL + F**) eşleme sağ üst köşesindeki arama kutusunu göstermek için.<br />2.  Öğe adı yazıp ENTER tuşuna **dönüş** veya "Büyüteç" simgesine tıklayın. Aramanızla eşleşen ilk öğe haritada seçilen görünür.<br />3.  Aramanızı özelleştirmek için açılır listeyi açın ve bir arama seçeneği belirleyin. Seçenekler **Sonrakini Bul**, **Öncekini Bul**, ve **Tümünü Seç**. Ardından, arama metin kutusuna yanındaki karşılık gelen düğmeye tıklayın.<br />     ![Arama Seçenekleri bırakma&#45;açılan listesinde](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternatif olarak, klavyeyi kullanma: basın **F3** sonraki eşleşen düğümü seçmek için veya **SHIFT + F3** önceki eşleşen düğüm seçin.<br />4.  Arama metin kutusuna aşağıdaki simgelere tıklayarak arama terimlerini nasıl işleneceğini belirtebilirsiniz seçeneklerden herhangi birini seçin.<br />     ![Arama eşleşme seçenekleri](../modeling/media/almcodemapssearchmatchicons.png)<br />     Seçenekler, soldan sağa, hassas eşleşen servis talebi, yalnızca tam sözcükleri eşleştirmeye, .NET normal ifade sözdizimini kullanır, otomatik olarak eşleşmeleri göstermek için grupları genişlet: kapalı öğeleri. **Önemli:** yalnızca bu gruplara daha önce genişletilen eşleşme daraltılmış grupları bulmak için arama kutusunu kullanın. Bu bulmaya ve kendi üst grupları otomatik olarak genişletmek için arama kutusunun altındaki bu seçeneği seçin.|
|Seçili olmayan tüm düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. Seçin **seçin**, **seçimi ters çevir**.|
|Seçili düğümlere bağlanacak ek düğümler'i seçin.|Seçili düğümlerin kısayol menüsünü açın. Seçin **seçin** ve bunlardan biri:<br /><br /> -Doğrudan Seçili düğüme bağlanan ek düğümler seçmek için Seç **gelen bağımlılıklar**.<br />-Doğrudan seçili düğümden bağlanan ek düğümler seçmek için seçin **giden bağımlılıklar**.<br />-Doğrudan ve seçili düğümden bağlanan ek düğümler seçmek için Seç **hem**.<br />-İçin ve seçili düğümden bağlanan tüm düğümleri seçmek için Seç **bağlı alt grafik**.<br />-Seçili düğümün tüm alt öğeleri seçmek için Seç **alt**.|

##  <a name="FilterNodes"></a> Filtre düğümleri ve bağlantıları

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Gösterebilir veya Filtre bölmesini gizleyebilirsiniz.|Seçin **filtreleri** kod harita araç çubuğunda düğme. **Filtreleri** bölmesinde bir sekmeli sayfada görüntülenmesini **Çözüm Gezgini**, varsayılan olarak.|
|Harita üzerinde gösterilen düğüm türlerini filtreleyin.|Ayarlayın veya içinde onay kutularını temizleyin **kod öğeleri** filtreler bölmesindeki liste.|
|Harita üzerinde gösterilen bağlantı türlerini filtreleyin.|Ayarlayın veya içinde onay kutularını temizleyin **ilişkileri** filtreler bölmesindeki liste.|
|Gösterin veya gizleyin harita üzerinde Test projesi düğümleri.|Ayarlama veya kaldırma **Test varlıklar** onay kutusu **çeşitli** filtreler bölmesindeki liste.|

Harita göstergesi panel içinde gösterilen simge listesinde yaptığınız ayarları yansıtır. Gösterge panelini göstermek veya gizlemek için tıklayın **gösterge** kod harita araç çubuğunda düğme.

##  <a name="Inspect"></a> Düğümlere ve bağlantılara inceleyin

Kod Haritaları, bu tür bağlantıları göster:

-   Tek bir bağlantı iki düğüm arasındaki tek bir ilişkiyi temsil eder.

-   Çapraz Grup bağlantısı farklı gruplardaki iki düğüm arasındaki bir ilişkiyi temsil eder.

-   Toplu bir bağlantının iki grupları arasında aynı yönde işaret eden tüm ilişkiler temsil eder.

> [!TIP]
> Varsayılan olarak, çapraz grup bağlantılarını seçili düğümler için yalnızca eşlemeyi gösterir. Gruplar arasında toplanmış bağlantıları göstermek veya gizlemek için bu davranışı değiştirmek için tıklayın **Düzen** kodu seçin ve araç harita **Gelişmiş**, ardından **tüm çapraz grup bağlantılarını göster** veya **Tüm çapraz grup bağlantılarını Gizle**. Bkz: [Gizle veya Göster düğümlere ve bağlantılara](#HidingShowing) daha fazla ayrıntı için.

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Bir düğüm veya bağlantı hakkında daha fazla bilgi.|Fare imlecini düğümün taşıma veya bir araç ipucu görünene kadar bağlayın.<br /><br /> Araç ipucu için toplanan bir bağlantı, temsil ettiği tek bağımlılıkları listeler.<br /><br /> - veya -<br /><br /> Düğümün veya bağlantının kısayol menüsünü açın. Seçin **Düzenle**, **özellikleri**.|
|Gösterin veya bir grubun içeriğini gizleyin.|-Bir grubu genişletmek için düğümü için kısayol menüsünü açın ve seçin **grubu**, **genişletme**.<br />     - veya -<br />     Köşeli Çift Ayraca (aşağı ok) düğmesini görünene kadar fare imlecini düğümün taşıyın. Grubu genişletmek için bu düğmeye tıklayın. Klavye: Seçili grubu genişletmek veya daraltmak basın **yanı SIRA** anahtarı (**+**) veya **eksi** anahtarı (**-**).<br />-Bir grubu daraltmak için düğümü için kısayol menüsünü açın ve seçin **grubu**, **Daralt**.<br />     - veya -<br />     Köşeli Çift Ayraca (yukarı ok) düğmesini görünene kadar fare işaretçisini bir grup üzerine taşıyın. Grubu daraltmak için bu düğmeye tıklayın.<br />-Tüm grupları Genişlet için basın **CTRL** + **A** tüm düğümleri seçin. Eşleme için kısayol menüsünü açın ve seçin **grubu**, **genişletme**. **Not:** tüm grupların genişletilmesi kullanılamaz bir eşlemesi veya bellek sorunları oluşturursa, bu komut kullanılamaz. Bu, yalnızca önem verdiğiniz ayrıntı düzeyi için haritasını Genişlet önerilir.<br />-Tüm grupları Daralt için harita veya bir düğümü için kısayol menüsünü açın. Seçin **grubu**, **Tümünü Daralt**.|
|Bir ad alanı, tür veya üye için kod tanımı bakın.|Düğümü için kısayol menüsünü açın ve seçin **tanıma**.<br /><br /> veya<br /><br /> Bu düğüme çift tıklayın. Genişletilmiş gruplar için Grup başlığına çift tıklayın.<br /><br /> veya<br /><br /> Düğümünü seçip ENTER tuşuna **F12**.<br /><br /> Örneğin:<br /><br /> -Bir sınıf içeren bir ad için o sınıf tanımını göstermek için sınıf için kod dosyasını açar. Diğer durumlarda **sembol sonuçları Bul** penceresi kodu dosyalarının bir listesini gösterir. **Not:** bu görevi, Visual Basic ad alanınızdaki gerçekleştirdiğinizde, ad alanı arkasındaki kod dosyasını açılmaz. Bu sorun, ayrıca bir Visual Basic ad alanı dahil seçili düğümler bir grubu üzerinde bu görevi gerçekleştirmek oluşur. Bu sorunu çözmek için el ile ad alanı arkasındaki kod dosyasına göz atın veya ad alanından seçiminizi düğümü çıkarın.<br />-Bir sınıf veya kısmi bir sınıf için sınıf tanımının göstermek için bu sınıf için kod dosyasını açar.<br />-İçin bir yöntem, yöntem tanımını göstermek için üst sınıfı için kod dosyasını açar.|
|Bağımlılıklar ve birleşik bir bağlantıya katılan öğe inceleyin.|İlginizi çeken ve seçiminiz için kısayol menüsünü açın bağlantıyı seçin. Seçin **katkıda bulunan bağlantıları göster** veya **katkıda bulunan bağlantıları yeni kod haritasında Göster**.<br /><br /> Visual Studio, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir. **Not:** kısmi gruplardaki öğeler arasındaki bağımlılıkları incelediğinizde, bu davranışı görebilirsiniz: <ul><li>Bu bağlantıların hala mevcut olsa bile, inceleme içinde yer alan yoksa öğe bağlantılarını eşlemesinden kaybolur.</li><li>Kısmi bir grup içindeki bir öğenin bağlantısını inceleyin ve daha sonra farklı bir bağlantı ile aynı öğenin inceleyin varsayalım. İkinci, inceleme sırasında hedef kısmi grubu yalnızca, ilk İnceleme öğeleri gösterir. Bağlantılar ve içinde ilk, inceleme katılmak olmadı, ancak ikinci, inceleme katılmak hedef öğe görünmez.</li></ul> Bir gruptan öğe eksik görmek için **alt öğeleri tekrar Al**![öğeleri tekrar Al alt simge](../modeling/media/dependencygraph_deletednodesicon.png) (gösterir bir grubun tüm üyelerinin haritada görünmez). Eylemlerinizi geri almayı deneyebilirsiniz (klavye: basın **CTRL + Z**) ve yeni bir haritada bağımlılıkları inceleyin.|
|Farklı gruplardaki birden fazla düğümde bağımlılıkları inceleyin.|Tüm alt öğelerini görebilmeniz için gruplar'ı genişletin. Bunların alt öğeleri dahil olmak üzere ilginizi çeken tüm düğümleri seçin. Çapraz grup bağlantılarını seçili düğümler arasındaki eşlemeyi gösterir.<br /><br /> Bir gruptaki tüm düğümleri seçmek için basılı **SHIFT** ve bu gruba çevresinde bir dikdörtgen çizerken farenin sol düğmesi. Bir haritada tüm düğümleri seçmek için basın **CTRL**+**A**. **İpucu:** çapraz grup bağlantılarını her zaman göstermek için **Düzen** harita araç çubuğunda **Gelişmiş**, **tüm çapraz grup bağlantılarını göster**.|
|Bir düğümün veya bağlantının başvuran öğeler bakın.|Düğümü için kısayol menüsünü açın ve seçin **tüm başvuruları Bul**. **Not:** yalnızca bu geçerlidir `Reference` öznitelik düğümü veya bağlantıyı ayarlayın haritanın .dgml dosyası olarak. Düğümleri veya bağlantıları öğelere başvurular eklemek için bkz [Özelleştir kod eşlemeleri DGML dosyalarını düzenleyerek](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

##  <a name="HidingShowing"></a> Düğümlere ve bağlantılara gösterme veya gizleme

Düğümlerin gizlenmesi, düzen algoritmasına katılmalarını engeller. Varsayılan olarak, çapraz grup bağlantıları gizlidir. Çapraz grup bağlantıları, düğümleri gruplar arasında bağlayan tek bağlantılardır. Gruplar daraltıldığında, haritada tüm çapraz grup bağlantılarını gruplar arasındaki tek bağlantılar içinde toplar. Bir grubu genişlettiğinizde veya grup içindeki düğümleri seçtiğinizde, çapraz grup bağlantıları görünür ve o gruptaki bağımlılıkları gösterir.

> [!CAUTION]
> Visual Studio Enterprise Visual Studio Professional kullanıcılarıyla oluşturulmuş bir harita paylaşmadan önce tüm düğümlerin veya başkalarının görmesini istediğiniz çapraz grup bağlantılarının gizlenmediğinden emin olun. Aksi takdirde, bu kullanıcılar bu öğelerin gizliliğini kaldıramayacaktır.

### <a name="to-hide-or-show-nodes"></a>Düğümleri gizlemek veya göstermek için

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Seçili düğümleri gizleme.|1.  Gizlemek istediğiniz düğümleri seçin.<br />2.  Seçili düğümlerin veya eşleme için kısayol menüsünü açın. Seçin **seçin**, **Gizle**.|
|Seçili olmayan düğümleri gizleme.|1.  Görünür kalmasını istediğiniz düğümleri seçin.<br />2.  Seçili düğümlerin veya eşleme için kısayol menüsünü açın. Seçin **seçin**, **seçili Gizle**.|
|Gizli düğümleri göstermek.|-Bir grup içindeki tüm gizli düğümleri göstermek için önce grubun genişletildiğinden emin olun. Kısayol menüsünü açın ve seçin **seçin**, **alt öğeleri göster**.<br />     - veya -<br />     Tıklayın **alt öğeleri göster**![göstermek için alt simge](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) (Bu, görünür yalnızca alt gizli düğümleri olduğunda) grubun sol üst köşesindeki simgeyi.<br />-Tüm gizli düğümleri göstermek için harita veya bir düğümü için kısayol menüsünü açın ve seçin **seçin**, **Tümünü Göster**.|

### <a name="to-hide-or-show-links"></a>Bağlantıları göstermek veya gizlemek için

|**Hedef**|**Harita araç çubuğunda düzeni, Gelişmiş ve ardından**|
|-|-|
|Çapraz grup bağlantılarını her zaman göster.|**Tüm çapraz grup bağlantılarını göster**. Bu, gruplar arasında toplanmış bağlantıları gizler.|
|Çapraz grup bağlantılarını her zaman gizler.|**Tüm çapraz grup bağlantılarını Gizle**|
|Seçilen düğümler için yalnızca çapraz grup bağlantılarını göster.|**Çapraz grup bağlantılarını seçili düğümler üzerinde göster**|
|Tüm bağlantıları gizle.|**Tüm bağlantıları gizle**. Yeniden bağlantıları göstermek için yukarıda listelenen seçeneklerden birini seçin.|

##  <a name="OrganizeGroups"></a> Düğümleri gruplandırma

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Kapsayıcı düğümlerini Grup düğümleri veya yaprak düğümleri olarak göstermek.|Kapsayıcı düğümlerini yaprak düğümleri olarak göstermek için: düğümleri seçin, seçiminizin kısayol menüsünü açın ve seçin **grubu**, **yaprak dönüştürme**.<br /><br /> Kapsayıcı düğümlerini Grup düğümleri olarak göstermek için: düğümleri seçin, seçiminizin kısayol menüsünü açın ve seçin **grubu**, **gruba dönüştürmek**.|
|Bir grup içindeki düzenini değiştirin.|Grubunu seçin, kısayol menüsünü açın, **Düzen**, istediğiniz düzen stili seçin.<br /><br /> - veya -<br /><br /> 1.  Grup seçin ve bunu genişletildiğinden emin olun.<br />2.  Grup başlığına yeniden tıklayın ve Grup araç çubuğu görünür.<br />     ![Bağımlılık grafiği &#45; Grup araç çubuğu](../modeling/media/dependencygraph_group.png)<br />3.  Açık **grubun yerleşim stilini değiştir** listesi ![bağımlılık grafiği &#45; grubu araç &#45; Düzen](../modeling/media/dependencygraph_grouptoolbar.gif) ve istediğiniz düzen stili seçin.<br /><br /> **Liste görünümü** listesine grubun üyeleri yeniden düzenler. **Graf varsayılanı** Grup düzeni eşlemesi varsayılan düzene sıfırlar. Diğer seçenekler için bkz. [eşleme düzenini](#Selecting).|
|Bir düğümü bir gruba ekleyin.|Düğümü gruba sürükleyin.<br /><br /> Düğüm sürüklerken, Visual Studio düğüme taşıdığınızdan emin göstermek için bir gösterge görüntüler.<br /><br /> Düğümleri grubun dışına da sürükleyebilirsiniz.|
|Bir grup olmayan düğüme düğüm ekleyin.|Düğümü hedef düğüme sürükleyin. Düğüm ekleyerek herhangi bir hedef düğümü bir gruba dönüştürebilirsiniz.|
|Seçili düğümleri Gruplandır.|1.  Gruplandırmak istediğiniz düğümleri seçin. Bir açılır araç çubuğu, seçtiğiniz son düğümün üzerinde görünür.<br />     ![Bağımlılık Grafik araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2.  Dördüncü simgesi araç çubuğunda **seçili düğümleri grupla** (düğüm genişlettiyseniz, beş dört simgeleri yerine gerekir). Tuşuna basın ve yeni grup adını yazın **dönüş**.<br />     - veya -<br />     Seçiminizin kısayol menüsünü açın ve gruplandırmak istediğiniz düğümleri seçin. Seçin **grubu**, **üst Grup Ekle**, tuşuna basın ve yeni grup adını yazın **dönüş**.<br /><br /> Bir grubu yeniden adlandırabilirsiniz. Grup için kısayol menüsünü açın ve seçin **Düzenle**, **özellikleri** Visual Studio özellikleri penceresini açın. İçinde **etiket** özelliği, grubu gerektiği gibi yeniden adlandırın.|
|Grupları kaldırın.|Kaldırmak istediğiniz grup veya grupları seçin. Seçiminizin kısayol menüsünü açın ve seçin **grubu**, **grubunu kaldırma**.|
|Düğümleri onların üst grubundan kaldırın.|Taşımak istediğiniz düğümleri seçin. Seçiminizin kısayol menüsünü açın ve seçin **grubu**, **Üst Gruptan Kaldır**. Bunlar hiçbir üst grupları yoksa grubun bu düğümleri yukarı kendi dizinleriyle veya çok grubun dışına kaldırır.<br /><br /> - veya -<br /><br /> Düğümleri seçin ve bunları grubun dışına sürükleyin.|

##  <a name="AddRemoveNodesLinks"></a> Ekleme, kaldırma veya düğümler ve bağlantılar açıklamaları yeniden adlandır

Detaya gitme veya haritayı basitleştirmek için daha fazla veya daha az öğe bir haritada görüntüleyebilirsiniz. Öğeleri yeniden adlandırmak ve açıklama öğeleri ekleyin.

> [!CAUTION]
> Visual Studio Enterprise Visual Professional kullanıcılarıyla kullanılarak oluşturulmuş bir harita paylaşmadan önce başkalarının görmesini istediğiniz tüm kod öğelerini harita üzerinde görünür olduğundan emin olun. Aksi halde bu kullanıcılar silinmiş kod öğeleri almak mümkün olmayacaktır.

### <a name="add-a-node-for-a-code-element"></a>Bir kod öğesi için bir düğüm Ekle

|**Hedef**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Yeni bir genel düğüm geçerli fare işaretçisi konumuna ekleyin.|1.  Fare işaretçisini tuşuna basın ve yeni kod öğesi koymak istediğiniz yere haritada taşıyın **Ekle**.<br />     - veya -<br />     Eşleme için kısayol menüsünü açın ve seçin **Düzenle**, **Ekle**, **genel düğüm**.<br />2.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|
|Belirli türde bir kod öğe düğümü geçerli fare işaretçisi konumuna ekleyin.|1.  Fare işaretçisini, haritada eşlemesi için kısayol menüsünü açın ve yeni kod öğesi koymak istediğiniz yere taşıyın.<br />2.  Seçin **Düzenle**, **Ekle**ve istediğiniz düğümü seçin.<br />3.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|
|Genel veya belirli türde bir kod öğe düğümü bir gruba ekleyin.|1.  Grup düğümünü seçin ve kısayol menüsünü açın.<br />2.  Seçin **Düzenle**, **Ekle**ve istediğiniz düğümü seçin.<br />3.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|
|Aynı türde yeni bir düğüm ekleyin ve varolan bir düğümü, bağlı.|1.  Kod öğesi seçin. Bir açılır araç çubuğu üzerinde görünür.<br />     ![Bağımlılık Grafik araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2.  İkinci simgeyi araç çubuğunda **bu düğümle aynı kategoride bir düğüm oluşturmak ve yeni bir bağlantı ekleyin**.<br />3.  Farenin sol düğmesine tıklayın ve yeni kod öğesi yerleştirmek için harita üzerinde bir alan seçin.<br />4.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|
|Bağlı olan yeni bir genel düğüm odağa sahip mevcut bir kod öğeyi ekleyin.|1.  Klavyeyi kullanarak basın **sekmesini** bağlantı için kod öğesi (noktalı dikdörtgen) odağa sahip oluncaya kadar.<br />2.  Tuşuna **Alt**+**Ekle**.<br />3.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|
|Odağa sahip mevcut bir kod öğesi bağlantıları yeni bir genel düğüm ekleyin.|1.  Klavyeyi kullanarak basın **sekmesini** bağlamak için kod öğesi (noktalı dikdörtgen) odağa sahip oluncaya kadar.<br />2.  Tuşuna **Alt**+**Shift**+**Ekle**.<br />3.  Tuşuna basın ve yeni düğüm için bir ad yazın **dönüş**.|

|**Kod öğeleri eklemek için**|**Aşağıdaki adımları gerçekleştirin**|
|-|-|
|Çözümde kod öğeleri.|1.  Kod öğesinin Bul **Çözüm Gezgini**. Kullanım **Çözüm Gezgini** arama kutusuna veya çözüme göz atın. **İpucu:** bir tür veya üye üzerinde bağımlılıkları olan kod öğeleri bulmak için tür veya üye için kısayol menüsünü açın **Çözüm Gezgini**. Sizi ilgilendiren ilişkiyi seçin. **Çözüm Gezgini** yalnızca belirtilen bağımlılıklara sahip kod öğeleri gösterir.<br />2.  Eşleme yüzeyine ilgilendiğiniz kod öğelerini sürükleyin. Kod öğeleri, sınıf görünümü veya nesne tarayıcısı da sürükleyebilirsiniz.<br />     - veya -<br />     İçinde **Çözüm Gezgini**, eşlemek istediğiniz kod öğelerini seçin. Ardından **Çözüm Gezgini** araç çubuğunda tıklatın **kod haritasında Göster**.<br /><br /> Varsayılan olarak, yeni kod öğeleri için üst kapsayıcı hiyerarşisini harita üzerinde görünür. Kullanım **dahil üst** bu davranışı değiştirmek için kod Haritası araç çubuğu düğmesi. Devre dışı bırakıldığında, yalnızca kod öğenin kendisinin eşlemesine eklenir. Bu davranış için yalnızca bir Sürükle ters ve eylem, basılı tutarak **CTRL** haritaya kod öğeleri sürüklerken tuşu.<br /><br /> Visual Studio, seçiminizdeki üst düzey kod öğeleri kod öğeleri ekler. Bir kod öğesi diğer kod öğeleri içerip içermediğini görmek için köşeli çift Ayraca (aşağı ok) görünür, böylece kod öğesi fare imlecini taşıyın. Kod öğesi genişletmek için köşeli çift ayracı seçin. Tüm kod öğelerini genişletmek için basın **CTRL**+**A** tüm öğeleri seçmek için eşleme için kısayol menüsünü açın ve seçin **grubu**, **Genişlet** . Tüm grupların genişletilmesi kullanılamaz bir harita oluşturmak veya yetersiz bellek sorunlarını neden bu komut kullanılamaz.|
|Kod öğeleri haritaya ilgili kod öğeleri.|Tıklayın **Göster ilgili** kod harita araç çubuğunda düğmesini ve ilgilendiğiniz öğeyi seçin.<br /><br /> - veya -<br /><br /> Kod öğesi için kısayol menüsünü açın. Birini **göster...**  ilginizi çeken ilişki türünü bağlı olarak menüsündeki öğeler. Örneğin, geçerli öğeye başvuran öğeleri başvuran sınıflar, yöntemi çağıranlar ve içeren sınıflar, ad alanları ve derlemeler için temel ve türetilen türlerin, geçerli öğe öğeleri görebilir.<br /><br /> Daha fazla ayrıntı için [bu konuda](../modeling/map-dependencies-across-your-solutions.md).|
|Derlenmiş .NET derlemeleri (.dll veya .exe) veya ikili dosyaları.|Derlemeleri veya ikili dosyaları dış Visual Studio'dan bir haritasına sürükleyin.<br /><br /> Yalnızca Visual Studio ve aynı kullanıcı erişim denetimi (UAC) izni düzeyinde çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini'nden sürükleyebilirsiniz. Örneğin, UAC açıksa ve Visual Studio'yu yönetici olarak çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini sürükleme işlemini engelleyecektir.|

###  <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Varolan kod öğeleri arasında bir bağlantı ekleyin

1. Kaynak kodu öğesi seçin. Bir araç çubuğu üzerinde kod öğesi görünür.

    ![Bağımlılık Grafik araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. İlk simgesi, araç çubuğunda **yeni bağlantı oluşturun bu düğümden tıklayacağınız düğüme sonraki**.

3. Hedef kod öğesi seçin. İki kod öğeleri arasında bir bağlantı görüntülenir.

**VEYA**

1. Harita üzerinde kaynak kodu öğesi seçin.

2. Yüklü bir fare varsa, fare işaretçisini harita sınırları dışında taşıyın.

3. Kod öğenin kısayol menüsünü açın ve seçin **Düzenle** > **Ekle** > **genel bağlantı**.

4. İçin sekmesinde ve bağlantının hedef kod öğesi seçin.

5. Tuşuna **girin**.

###  <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Harita üzerinde varolan düğüm için bir açıklama ekleyin

1.  Kod öğesi seçin. Bir araç çubuğu üzerinde görünür.

     ![Bağımlılık Grafik araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2.  Üçüncü simgesi, araç çubuğunda **Seçili düğüme yeni bir bağlantı ile yeni bir açıklama düğümü Oluştur**.

     \- veya -

     Kod öğesi için kısayol menüsünü açın ve seçin **Düzenle** > **yeni açıklama**.

3.  Açıklamalarınızı yazın. Yeni bir satıra yazmak için basın **Shift** + **Enter**.

#### <a name="add-a-comment-to-the-map-itself"></a>Eşleme için bir açıklama ekleyin

1.  Eşleme için kısayol menüsünü açın ve seçin **Düzenle** > **yeni açıklama**.

2.  Açıklamalarınızı yazın. Yeni bir satıra yazmak için basın **Shift** + **Enter**.

###  <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Bir kod öğesi veya bağlantı yeniden adlandır

1.  Kod öğesi veya yeniden adlandırmak istediğiniz bağlantıyı seçin.

2.  Tuşuna **F2**, kısayol menüsünü açın ve seçin **Düzenle** > **Yeniden Adlandır**.

3.  Haritada düzenleme kutusu göründüğünde, kod öğesi veya bağlantıyı yeniden adlandırın.

**VEYA**

1.  Kısayol menüsünü açın ve seçin **Düzenle** > **özellikleri**.

2.  Düzen **etiket** Visual Studio Özellikler penceresindeki özellik.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Haritadaki bir kod öğesi veya bağlantı kaldırma

1.  Kod öğesi veya bağlantı ve ENTER tuşuna seçin **Sil** anahtarı.

     \- veya -

     Bağlantı ve kod öğesi için kısayol menüsünü açın ve seçin **Düzenle** > **Kaldır**.

2.  Öğe veya bağlantı bir grubun parçası ise **alt öğeleri tekrar Al** düğmesi ![öğeleri tekrar Al alt simge](../modeling/media/dependencygraph_deletednodesicon.png) grup içinde görünür. Bu eksik öğeleri ve bağlantılarına almak için tıklayın.

-   Temel kodu etkilemeden bir eşlemden kod öğeleri ve bağlantılarına kaldırabilirsiniz. Bunları sildiğinizde, tanımları DGML (.dgml) dosyasından kaldırılır.

-   DGML düzenlenerek, tanımsız kod öğeleri ekleyerek veya Visual Studio'nun bazı daha önceki sürümleri kullanılarak oluşturulan eşlemeler bu özelliği desteklemez.

#### <a name="flag-a-code-element-for-follow-up"></a>İzleme için kod öğesi bayrak

1.  Kod öğesi veya için izleme bayrağı istediğiniz bağlantıyı seçin.

2.  Kısayol menüsünü açın ve seçin **Düzenle** > **izleme bayrağı**.

-   Varsayılan olarak, kırmızı bir arka plan kod öğesi kazanır. Göz önünde bulundurun [açıklama ekleme](#AddComments) bunu ilgili izleme bilgileri.

-   Öğenin arka plan rengini değiştirme veya izleme bayrağı seçerek temizleyin **Düzenle** > **diğer bayrağı renkleri**.

##  <a name="ChangeStyleCodeOrLink"></a> Bir kod öğesi veya bağlantı stilini değiştirme

Kod öğeleri düğümlerdeki simgeleri ve kod öğeleri ve önceden tanımlanmış simgeleri ve renkleri kullanarak bağlantıların renklerini değiştirebilirsiniz. Örneğin, kod öğeleri ve belirli bir kategori veya özellik sahip bağlantıları vurgulamak için bir renk seçebilirsiniz. Bu belirleyip harita belirli alanlara odaklanmanıza olanak tanır. Özel simgeleri ve renkleri haritanın .dgml dosyasını düzenleyerek belirtebilirsiniz; bkz: [Özelleştir kod eşlemeleri DGML dosyalarını düzenleyerek](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Kod öğeleri veya belirli bir kategori veya özellik bağlantılarıyla bir önceden tanımlanmış bir rengi veya simgeyi uygulamak için

1.  Harita araç çubuğunda **gösterge**.

2.  İçinde **gösterge** kutusunda, kod öğesi kategori veya özellik zaten listede görünüp görünmediğine bakın.

3.  Liste kategori veya özellik içermiyorsa seçin **+** içinde **gösterge** kutusuna ve ardından **düğüm özelliği**, **düğüm kategorisi** , **Bağlantı özelliğinin**, veya **bağlantı kategorisi**. Özellik veya kategori seçin. Kategori veya özellik artık görünür **gösterge** kutusu.

    > [!NOTE]
    > Oluşturma ve bir kategori veya özellik için bir kod öğesi atamak için haritanın .dgml dosyasını düzenleyebilirsiniz; bkz: [Özelleştir kod eşlemeleri DGML dosyalarını düzenleyerek](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4.  İçinde **gösterge** kutusunda, kategori veya özellik eklediğiniz yanındaki simgeye tıklamanız veya değiştirmek istediğiniz.

5.  Değiştirmek istediğiniz stili seçmek için aşağıdaki tabloyu kullanın:

    |**Değiştirmek için**|**Seçin**|
    |-|-|
    |Arka plan rengi|**Arka plan**|
    |Anahat rengi|**Fırça darbesi**|
    |Metin rengi ("f" harfi sonucu göstermek için görüntülenir)|**Ön plan**|
    |Simge|**Simgeler**|

     **Renk kümesi Seçicisi** veya **simge kümesi Seçicisi** rengi veya simgeyi seçmeniz için iletişim kutusu görüntülenir.

6.  İçinde **renk kümesi Seçicisi** veya **simge kümesi Seçicisi** iletişim kutusunda, aşağıdakilerden birini yapın:

    |**Uygulanacak bir**|**Aşağıdaki adımları gerçekleştirin**|
    |-|-|
    |Simgeleri ve renkleri ayarlama|Açık **rengi seçin** (veya **simgesi**) **ayarlamak** listesi. Renk ve simge kümesi seçin.|
    |Belirli bir rengi veya simgeyi|Kategori veya özellik değer listesini açın. Bir rengi veya simgeyi seçin.|

    > [!NOTE]
    > Yeniden düzenleyebilir, silebilir veya geçici olarak stillerini devre dışı bırak **gösterge** kutusu. Bkz: [Gösterge kutusunu Düzenle](#ModifyLegend).

##  <a name="ModifyLegend"></a> Gösterge kutusunu Düzenle

Yeniden düzenleyebilir, silebilir veya geçici olarak stillerini devre dışı bırak **gösterge** kutusunda:

1.  Bir stilin kısayol menüsünü açın **gösterge** kutusu.

2.  Aşağıdaki görevlerden birini uygulayın:

    |**Hedef**|**Seçin**|
    |-|-|
    |Kod öğesi devre dışı bırak|**Devre Dışı Bırak**|
    |Kod öğesi silme|**Delete**|
    |Stili yukarı taşıyın|**Yukarı Taşı**|
    |Kod öğesini Aşağı Taşı|**Aşağı Taşı**|

##  <a name="CopyLegend"></a> Stilleri bir eşlemden kopyalayın

1.  Emin **gösterge** kutusu kaynak harita üzerinde görüntülenir. Harita araç çubuğunda görünür durumda değilse, **gösterge**.

2.  Kısayol menüsünü açın **gösterge** kutusu. Seçin **kopyalama gösterge**.

3.  Göstergeyi hedef harita yapıştırın.

##  <a name="MergeMaps"></a> Kod haritaları Birleştir

Kod öğeleri arasındaki eşlemeleri yapıştırarak haritalar birleştirebilirsiniz. Kod öğesi tanımlayıcıları eşleşirse, yapıştırma kod öğeleri işlevleri bir birleştirme işlemi gibi. Bu görevi kolaylaştırmak için tüm derlemeleri veya tam yolun her derlemenin veya ikili birleştirmek istediğiniz her eşleme için aynı olması, aynı klasörde görselleştirmek istediğiniz ikili dosyaları'nı koyun.

Alternatif olarak, bu klasörden aynı Eşle bu derlemeleri veya ikili dosyaları sürükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
