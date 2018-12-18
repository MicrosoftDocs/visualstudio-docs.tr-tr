---
title: XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8928f725e144c980d3e625d557a71047959b8b9b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058827"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Visual Studio’da XAML Tasarımcısı’nı kullanarak kullanıcı arabirimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da XAML Tasarımcısı, XAML tabanlı Windows Store, Windows Phone, WPF ve Silverlight uygulamaları tasarlamanıza yardımcı olması için görsel bir arabirim sağlar. Denetimlerden sürükleyerek, uygulamalarınız için kullanıcı arabirimleri oluşturabilirsiniz **araç kutusu** ve ayarları **özellikleri** penceresi. Ayrıca, XAML XAML görünümünde doğrudan düzenleyebilirsiniz.

 Gelişmiş XAML tasarım görevleri için animasyon ve davranışlarla gibi bkz [Visual Studio için Blend'i kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı
 XAML Tasarımcısı'nda çalışma birkaç görsel arabirim öğelerini içerir. Çalışma yüzeyini, XAML Düzenleyicisi, bunlar cihaz penceresi ve belge ana hattı penceresinin Özellikler penceresi. XAML Tasarımcısı'nı açmak için bir XAML dosyasında sağ **Çözüm Gezgini** ve **Görünüm Tasarımcısı**.

## <a name="authoring-views"></a>Yazma görünümleri
 XAML Tasarımcısı, uygulamanızın biçimlendirmenin XAML eşitlenmiş bir Tasarım görünümünü ve XAML görünümü sağlar. Visual Studio'da açık bir XAML dosyası ile XAML görünümünü ve Tasarım görünümü arasında kullanarak geçebilirsiniz **tasarım** ve **XAML** sekmeler. Kullanabileceğiniz **takas bölmeleri** düğmesi hangi penceresinde geçiş yapmak için en üstte görünür: çalışma yüzeyine ya da XAML Düzenleyicisi.

 Tasarım görünümünde, pencereyi içeren *çalışma yüzeyine* etkin pencere ve birincil çalışma yüzeyi olarak kullanabilirsiniz. Görsel olarak bir sayfa veya çizim öğeleri ekleyerek ve ardından bunları değiştirerek uygulamanızı tasarlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı'nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md). Bu örnekte, çalışma yüzeyinde Tasarım görünümünde gösterilmiştir.

 ![Tasarım görünümü XAML Tasarımcısı'nın](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Bu özellikler, çalışma yüzeyine kullanılabilir:

 **Dayama çizgileri** dayama çizgileri olan *hizalama sınırları* denetimleri kenarlarına zaman hizalanır veya ne zaman metin taban çizgileri hizalanmış göstermek için kırmızı kesik çizgili satırlar halinde görünür. Hizalama sınırları yalnızca görünür **dayama çizgilerine yaslamayı** etkinleştirilir.

 **Kılavuz rayları** `Grid` rails içindeki satırları ve sütunları yönetmek için kullanılan bir [kılavuz](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) paneli. Oluşturma ve satırları ve sütunları Sil ve kendi göreli genişlik ve yükseklik ayarlayabilirsiniz. Çalışma yüzeyinin sol tarafında görünür, dikey kılavuz parmaklık için satırlar kullanılır ve üst kısmında görünür, yatay çizgi sütunlar için kullanılır.

 **Kılavuz donatıcıları** A `Grid` donatıcı görünür üzerinde bağlı dikey veya yatay çizgi bulunan bir üçgen olarak `Grid` parmaklık. Sürüklediğinizde bir `Grid` donatıcı, genişliklerini veya bitişik sütun veya satır yüksekliklerini fareyi hareket ettirdiğinizde güncelleştirin.

 `Grid` donatıcıları genişliğini ve yüksekliğini kontrol etmek için kullanılan bir `Grid`ait satırları ve sütunları. Tıklayarak yeni bir sütun veya satır ekleyebilirsiniz `Grid` rails. Yeni bir satır veya sütun satır eklediğinizde bir `Grid` sahip iki veya daha fazla sütun veya satır, kısa bir araç çubuğu panelinde genişlik ve yükseklik açıkça ayarlamanıza olanak tanır parmaklık dışında görünür. Boyutlandırma seçeneklerini ayarlamak Mini araç sağlar `Grid` satırları ve sütunları.

 **Yeniden boyutlandırma tutamaçları** yeniden boyutlandırma tutamaçları üzerinde Seçili denetimleri görünür ve yeniden boyutlandırma sağlar. Bir denetimi yeniden boyutlandırdığınızda, genişlik ve yükseklik değerlerini, genellikle denetiminin boyutunu yardımcı olması için görünür. Denetimleri Tasarım görünümünde düzenleme hakkında daha fazla bilgi için bkz. [XAML Tasarımcısı'nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md).

 **Kenar boşlukları** kenar boşlukları, bir denetimin kenarı ile onun kapsayıcısının arasındaki sabit boşluk miktarını temsil eder. Bir denetim kenar boşluklarını kullanarak ayarlayabilirsiniz [kenar boşluğu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) özellikleri altında **Düzen** Özellikler penceresinde.

 **Margin donatıcıları** Düzen kapsayıcısı göreli öğe kenar boşluklarını değiştirmek için kenar boşluğu donatıcıları kullanabilirsiniz. Kenar boşluğu donatıcısı açıksa, bir kenar boşluğu ayarlı değildir ve kenar boşluğu donatıcısı bozuk zincirini görüntüler. Kenar boşluğu ayarlı değil, Düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığında öğeleri yerinde kalır. Kenar boşluğu donatıcısı kapalı olduğunda, kenar boşluğu donatıcısı sertifikalarından zinciri görüntüler ve öğeleri Düzen kapsayıcısı (kenar sabit kalır), çalışma zamanında yeniden boyutlandırıldığından kenar boşlukları ile taşınır.

 **Öğe tanıtıcıları** öğenin çevreleyen mavi kutusunun köşeleri işaretçiyi getirdiğinizde çalışma yüzeyinde görüntülenen öğe tutamaçları kullanarak bir öğeyi değiştirebilirsiniz. Bu tanıtıcıları, döndürme, yeniden boyutlandırma, çevir, taşıyın veya öğeye bir köşe yarıçapı eklemenizi sağlar. Öğesi işleyici için Sembol işlevi değişir ve işaretçiyi tam konumuna bağlı olarak değişir. Öğe tutamaçları görmüyorsanız, öğe seçili olduğundan emin olun.

 Tasarım görünümünde, ek çalışma yüzeyine komutlar burada gösterildiği gibi ekranın sol alt bölümünde kullanılabilir:

 ![Tasarım görünümü komutları](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Bu komutlar, bu araç çubuğunda kullanılabilir:

 **Yakınlaştırma** yakınlaştırma tasarım yüzeyine boyut olanak sağlar. %12,5 %800 yakınlaştırma veya gibi seçeneklerini **seçimi Sığdır** ve **tümünü Sığdır**.

 **Yaslama kılavuzunu Göster/Gizle** görüntüler veya kılavuz çizgilerini gösterir kılavuza gizler. Kılavuz çizgileri kullanılan olduğunda ya da **çizgilerine yaslamayı** veya **dayama çizgilerine yaslamayı** etkinleştirilir.

 **Açma / kapatma çizgilerine yaslamayı** varsa **çizgilerine yaslamayı** çalışma yüzeyinde bir öğeyi sürüklediğinizde etkin öğeyi en yakın yatay ve dikey kılavuz çizgilerine hizalamak eğilimindedir.

 **Açma / kapatma dayama çizgilerine yaslamayı** dayama çizgileri Yardım, hizalama, birbirlerine göreli denetler. Varsa **dayama çizgilerine yaslamayı** denetimini diğer denetimlere göre sınırları görünür kenarları ve bazı denetimler metnin yatay veya dikey olarak hizalandığında hizalama sürüklediğinizde, etkinleştirilir. Bir hizalama sınırı kırmızı kesik çizgili bir çizgi olarak görünür.

 XAML görünümünde, XAML Düzenleyicisi'ni içeren etkin penceresidir ve XAML Düzenleyicisi'ni, birincil yazma aracıdır. Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirim temelli, XML tabanlı bir sözlüğünü sağlar. XAML görünümü, IntelliSense, otomatik biçimlendirme, söz dizimi vurgulama ve etiket Gezinti içerir. Bu örnekte, XAML görünümü gösterilmiştir:

 ![XAML görünümü](../designers/media/xaml-editor.png "xaml_editor")

 **Bölünmüş Görünüm çubuğunun** XAML Düzenleyicisi'ni alt pencereye olduğunda Bölünmüş Görünüm Çubuğu XAML görünümü üst kısmında görünür. Bölünmüş Görünüm Çubuğu Tasarım görünümünde ve XAML görünümünde göreli boyutlarını denetlemenizi sağlar. Görünüm konumları da değiştirebilir (kullanarak **takas bölmeleri** düğmesi), görünümleri yatay veya dikey olarak düzenlenmiş belirtin ve ya da görünümü Daralt.

 **Biçimlendirme yakınlaştırma** biçimlendirme Yakınlaştırma boyutu XAML görünüm sağlar. %400 %20 değerinden yakınlaştırma yapabilirsiniz.

## <a name="device-window"></a>Cihaz penceresi
 XAML Tasarımcısı'nda cihaz penceresi, tasarım zamanında çeşitli görünümler, görüntüler, benzetimini gerçekleştirmek ve Windows Store veya Windows Phone projeniz için seçenekleri görüntüleme sağlar. Cihaz penceresi kullanılabilir **tasarım** XAML Tasarımcısı'nda çalışırken menüsü. İşte bu şekilde görünür:

 ![Cihaz penceresi](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Cihaz penceresindeki Seçenekler şunlardır:

 **Görüntüleme** farklı ekran boyutları ve uygulama çözümü belirtir.

 **Yönlendirme** uygulama için farklı yönleri belirtir: **yatay** veya **dikey**.

 **Edge** uygulamanızın farklı edge hizalamaları belirtir: **hem**, **sol**, **sağ**, veya **hiçbiri**.

 **Yüksek Karşıtlık** seçili karşıltık ayarını temel alarak uygulamayı önizleyin. Dışında bir değere ayarlanırsa, bu ayar **varsayılan**, geçersiz kılacak olan `RequestedTheme` App.xaml içinde ayarlanan özellik.

 **Ölçeklendirme geçersiz kılma** odasının ışıklarının belge tasarım yüzeyine içinde ölçeklendirme öykünmesini etkinleştirir. Bu bir faktörüyle ölçeğe artırmanıza olanak sağlar. Öykünme üzerinde etkinleştirmek için onay kutusunu seçin. Örneğin, ölçeklendirme, yüzde %100 ise, belge tasarım yüzeyine içinde %140 ölçeklendirin. Geçerli ölçeğe 180 ise bu seçenek devre dışıdır.

 **Minimum Genişlik** minimum genişlik ayarını belirtir. Minimum genişlik, App.xaml içinde değiştirilebilir.

 **Tema** uygulama temasını belirtir. Örneğin, koyu ve açık bir tema arasında geçiş.

 **Chrome Göster** etkinleştirebilir veya sanal tablet çerçeve Tasarım görünümünde uygulamanızın etrafında'devre dışı bırakır. Çerçeve göstermek için onay kutusunu seçin.

 **Görüntülenecek küçük** görüntü modunu belirtir. Belge boyutunu görüntüleme boyutuna kırpmak için bu onay kutusunu seçin.

## <a name="document-outline-window"></a>Belge Anahattı penceresi
 Belge Anahattı penceresi XAML Tasarımcısı'nda bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğeleri hiyerarşik yapısını görüntüleyin.

- Öğeleri seçin, böylece bunları (hiyerarşisinde etrafında onları çalışma yüzeyinde değiştirin, özelliklerini Özellikler penceresinde ayarlayın ve benzeri taşıma) değiştirebilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı'nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md)

- Denetimleri olan öğeler için şablonları oluşturup yeniden açın.

- Seçilen öğeler için bağlam menüsünü kullanın. Aynı menüyü, çalışma yüzeyinde seçilen öğeleri için de kullanılabilir.

  Belge Anahattı penceresini görüntülemek için menü çubuğunda **görünümü**, **diğer Windows**, **belge anahattı**.

  ![Belge Anahattı penceresi](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Belge Anahattı penceresindeki Seçenekler şunlardır:

  **Belge Anahattı** Belge Anahattı penceresi ana görünümünde bir belge hiyerarşisini bir ağaç yapısında görüntüler. Farklı düzeylerde, belge inceleme ve kilitleme ve öğeleri tek veya grup gizlemek için Belge Anahattı hiyerarşik yapısını kullanabilirsiniz.

  **Göster/Gizle** Belge Anahattı öğelere karşılık gelen gösterir veya gizler çalışma yüzeyine öğeleri. Kullanım **Göster/Gizle** düğmeleri, gösterilen göz önünde bir sembolü görüntülemek veya öğeleri gizlemek için CTRL + H ve bunları görüntülemek için SHIFT + CTRL + H tuşuna basın.

  **Kilitle/Kilidini Aç** kilitler veya belge ana hattı öğelere karşılık gelen çalışma yüzeyine öğeleri kilidini açar. Kilitli öğeler değiştirilemez. Kullanım **Kilitle/Kilidini Aç** asma kilide görüntüleyen düğmeleri, kilitli olduğunda simge veya kilidini açmak için CTRL + L kilit öğelere ve SHIFT + CTRL + L tuşlarına basın.

  **Kapsamına dönmek için pageRoot** yukarı ok simgesi gösterir, belge ana hattı penceresinin üst kısmındaki seçeneğini belge anahattı önceki kapsama döndürür. Üst kapsama gitme yalnızca bir stil veya şablon kapsamı içinde olduğunuzda geçerlidir.

## <a name="properties-window"></a>Özellik penceresi
 Özellikler penceresinde denetimlerinde özellik değerlerini ayarlamanıza imkan sağlar. İşte bu şekilde görünür:

 ![Özellikler penceresi](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Özellikler penceresinin üst kısmındaki çeşitli seçenek vardır. Seçili olan öğenin adını kullanarak değiştirebileceğiniz **adı** kutusu. Sol üst köşesinde şu anda seçilen öğeyi temsil eden bir simge yoktur. Özellikleri kategoriye veya alfabetik olarak düzenlemek için tıklayın **kategori**, **adı**, veya **kaynak** içinde **ölçütü** listesi. Bir denetim için olayların listesini görmek için tıklayın **olayları** düğmesi, bir ışık Şimşek simgesi görüntüler. Bir özellik için arama yapmak için özelliğin adını yazmaya başlayın **arama özellikleri** kutusu. Siz yazarken aramanızla eşleşen özellikleri Özellikler penceresinde görüntülenir. Bazı özellikler bir aşağı ok düğmesini seçerek gelişmiş özelliklerini ayarlamanıza olanak sağlar. Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz. [hızlı başlangıç: denetimler ekleme ve olayları işleme](http://go.microsoft.com/fwlink/?LinkID=247983)

 Her bir özellik sağındaki değer bir *özelliği işaretçisi* kutusu simgesi olarak görünür. Özellik işaretçisi görünümünü veri bağlama veya özelliğine uygulanan bir kaynak olup olmadığını belirtir. Örneğin, beyaz kutu simgesi varsayılan bir değer belirtir, yerel kaynak uygulanan ve turuncu bir kutu, genellikle bir veri bağlamayı uygulanan gösterir genellikle bir siyah kutu simgesi gösterir. Özellik işaretçisi tıkladığınızda stili tanımına gidin, veri bağlama Oluşturucusu'nu açmak veya Kaynak Seçici'yi açın.

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı'nda öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md) [oluşturma ve bir kaynağı uygulama](../designers/how-to-create-and-apply-a-resource.md) [izlenecek yol: XAML Tasarımcısı'nda verilere bağlama](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
