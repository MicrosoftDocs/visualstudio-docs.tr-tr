---
title: R araçları seçenekleri
description: Visual Studio'da R dili ve ilişkili özelliklerin seçenekleri referansı.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a40ed2fd72862bde3494edd0c74aebcca6b55711
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250962"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio seçenekleri için R araçları

Ayarları aracılığıyla erişilir **R Araçları** > **seçenekleri** menüsünde aracılığıyla veya **Araçları** > **seçenekleri** ve giderek **R Araçları**:

  ![Seçenekler iletişim kutusu için R araçları](media/options-dialog.png)

Seçenekler ve ayarlar R belirli aşağıdaki yöntemleri kullanılarak erişilir. Seçmelisiniz **tüm ayarları göster** kutusunun alt kısmındaki **seçenekleri** iletişim kutusu tüm bu bölümleri görünür.

- Kod biçimlendirme seçenekleri (bkz [Düzenleyici Seçenekleri](editing-r-code-in-visual-studio.md#editor-options): **Araçları** > **seçenekleri** menüsünde, ardından **metin düzenleyici**  >  **R** > **biçimlendirme**
- Lint seçenekleri (bkz [Linting](linting-r-code.md)): **Araçları** > **seçenekleri** menüsü, ardından **metin düzenleyici**  >   **R** > **Lint**
- Gelişmiş Düzenleyici Seçenekleri ([bu makalede açıklanan](#text-editor--r--advanced-options)): **Araçları** > **seçenekleri** menüsü, ardından **metin düzenleyici**  >  **R** > **Gelişmiş**
- Davranış seçenekleri ([bu makalede açıklanan](#r-tools--advanced-options)): **R Araçları** > **seçenekleri** menüsünden veya **Araçları**  >  **Seçenekleri**, ardından kaydırarak **R Araçları**.

**R Araçları** > **veri bilimi ayarları** komutu Visual Studio'da genel farklı ayar da etkiler. Bu komut, sonraki bölümde açıklanmıştır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R araçları > veri bilimi ayarları

**R araçları > veri bilimi ayarları** menü öğesi için veri bilimcilerine ihtiyaçlarını en iyi duruma getirilmiş bir düzene sahip Visual Studio IDE yapılandırır. Bu seçenek özellikle açılır [etkileşimli](interactive-repl-for-r-in-visual-studio.md), [değişken Gezgini](variable-explorer.md), ve [çalışma alanları](r-workspaces-in-visual-studio.md) windows:

![Visual Studio'da veri Bilimcisi pencere düzeni](media/installation-data-scientist-layout-result.png)

Diğer Visual Studio ayarları için daha sonra geri almak için önce kullanmak **Araçları** > **içeri ve dışarı aktarma ayarları** komutu, select **seçili ortam ayarlarınıDışarıAktar**ve bir dosya adı belirtin. Bu ayarları geri yüklemek için aynı komutu kullanın ve seçin **seçili ortam ayarlarını içeri aktarma**. Veri bilimi insanı düzenini değiştirmek ve daha sonra kullanmak yerine geri isterseniz de aynı komutları kullanabilirsiniz **veri bilimi ayarları** doğrudan komutu.

## <a name="text-editor--r--advanced-options"></a>Metin Düzenleyicisi > R > Gelişmiş Seçenekler

Bu seçenekler biçimlendirme, IntelliSense, anahat oluşturma, girintilendirme ve söz dizimi için r denetimi davranışını denetler.

![R metin Gelişmiş Düzenleyici seçenekleri için Seçenekler iletişim kutusu](media/options-dialog-advanced-text-editor.png)

Her seçeneği Aç veya kapat söz konusu davranışını denetlemek için ayarlanır. Hangi seçeneğin etkiler hakkında daha fazla ayrıntı için iletişim kutusunun alt kısmındaki Yardım bölmesine bakın. Yapma büyük bölmesinde kadar bu Yardım bölmenin üstünde sürükleyebilirsiniz unutmayın.

![R metin düzenleyicisi Gelişmiş Seçenekler iletişim kutusunda Yardım Bölmesi genişletildi](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R araçları > Gelişmiş Seçenekler

**R Araçları** > **seçenekleri** açılır menü komutu **seçenekleri** R Seçenekleri iletişim:

  ![Seçenekler iletişim kutusu için R araçları](media/options-dialog.png)

Aşağıdaki bölümlerde, bu sayfada farklı seçenekler açıklanmaktadır.

### <a name="debugging"></a>Hata Ayıklama

Değerlerin nasıl işleneceğini şu seçenekleri denetlemek [değişken Gezgini](variable-explorer.md) ve izleyin ve yerel öğeler gibi hata ayıklayıcı pencerelerinde (bkz [hata ayıklama R kodunu](debugging-r-in-visual-studio.md)).

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Etkin bağlamalar değerlendirin | `True` | Zaman `True`, her zaman en güncel değeri değişkenleri ve özellikleri incelerken gördüğünüzü sağlar. Bu ifadeler, bunların nasıl uygulandığına bağlı olarak yan-etkiler, neden olabilir değerlendirme riskidir. |
| Nokta önekli değişkenleri Göster | `False` | Değişkenleri ön ekine sahip olup olmadığını belirtir `.` gösterilir. |

### <a name="grid-view"></a>Izgara Görünümü

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Dinamik değerlendirme | `False` | Varsayılan olarak, `View(<expression>)` işlevi, önemli ölçüde bellek büyük veri kümeleriyle tüketebileceği bir veri çerçevesi olarak verilerin bir anlık görüntüsünü alır. Bu seçeneğin ayarlanması `True` kılavuz görüntülenen veri getirmek için yenilendiğinde ifade değerlendirilir anlamına gelir. İfade değişiklikleri de verileri değişirse, ancak hangi dplyr pip ifadeler için uygun olmayabilir. |

### <a name="help"></a>Yardım

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| F1 Web tarayıcısı | `Internal` | Terim kullanmak için arama yaparken yardım nasıl görüntüleneceğini denetimleri **Ctrl**+**F1**. Ayarlandığında `Internal`, Yardım araç penceresi Visual Studio içinde işlenir. Ayarlandığında `External`, Yardım, varsayılan web tarayıcınızda görüntülenir. |
| F1 Web arama dizesi | `R site:stackoverflow.com` | Bastığınızda arama terimlerini arama motorunuz nasıl geçirilir denetimleri **Ctrl**+**F1** bir Terime Düzenleyici. Varsayılan olarak dizedir `R site:stackoverflow.com`, hangi ekler `R` için arama teriminizi. `site:stackoverflow.com` Sayfalara arama kapsamı için bunu bildiren bir arama motoru yönergesiyse `stackoverflow.com` etki alanı. |
| R Yardım tarayıcısı | `Automatic` | Yardım belgelerini R kullanarak ararken nasıl görüntüleneceğini denetimleri **F1**, **?**, veya **??** . Ayarlandığında `Automatic`, Yardım uygun penceresinde işler. Örneğin, varsayılan PDF programınızda PDF görünür ancak HTML Yardımı Visual Studio araç penceresi içinde görüntülenir. Ayarlandığında `External`, Yardım, varsayılan web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Geçmişi her zaman Kaydet | `True` | Komut geçmişinizde RTVS yazıp yazmayacağını belirtir bir *. RHistory* proje kapatıldığında çalışma dizininizde dosya. Bile, çıkmadan önce projenizi kaydetme geçmişini kaydedilirken gerçekleşir. |
| Arama filtresi Sıfırla | `True` | Geçmiş penceresinde komut geçmişinizde eşleşen alt dizenin Historie R iletişim filtre terimini karşı komutları gösterecek şekilde filtreleyebilirsiniz olup olmadığını belirler. Bu ayar, yeni bir komut çalıştırın veya farklı bir yükünü tetikleyen bir yeni projeye geçiş yapmak, geçmiş arama filtresi sıfırlanıp sıfırlanmayacağını belirler *. RHistory* dosya. Varsayılan ayar `True` şaşkınlık, bir filtre kümesiyle bir komut çalıştırın ve az önce çalıştırdığınız komutu geçmişinde neden çıkmadı merak ediyor olduğunda en aza indirir. |
| Çok satırlı seçimi kullan | `True` | Çok satırlı deyimi geçmişinde tek bir tıklamayla seçebileceğiniz olup olmadığını belirtir. Ayrıca yukarı/aşağı ok Gezinti etkileşimli Windows deyimleri satırları yerine sağlar. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| HTML sayfaları tarayıcı | `External` | İçerik gibi yerlerde belirler bir `ggvis` çizim, veya bir `shiny` uygulama işlenir. `Internal` Visual Studio araç penceresi içinde HTML çıktısını gösterir. `External` HTML çıktısı varsayılan tarayıcınızda görüntülenir. |

### <a name="logging"></a>Günlüğe Kaydetme

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Günlük olayları | `Normal` | Ayrıntı RTVS tanılama için kullanılan günlük kaydı düzeyini denetler. Varsayılan ayar `Normal` bir günlük dosyası oluşturur, `TEMP` dizin. Ayarlandığında `Traffic`, RTVS oturumunuzda tüm komutları ve yanıtları kaydeder. Bu günlük dosyaları hiçbir zaman makinenize bırakın, ancak RTVS sorunları tanılamak için yararlı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Markdown Önizleme tarayıcı | `External` | RMarkdown HTML çıktısı görüntülendiği belirler. `Internal` Visual Studio araç penceresi içinde RMarkdown HTML belge gösterir. `External` RMarkdown varsayılan tarayıcınızı kullanarak HTML görüntüler. |

### <a name="r-engine"></a>R motoru

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için (yerel) kod sayfasına ayarlar Varsayılan olarak işletim sisteminin temel alınan yerel ayarı kullanır. |
| Zrcadlových Server cran | `(Use .Rprofile)` | Varsayılan zrcadlových Server cran Paketi yüklemeleri için ayarlar. Varsayılan ayar `Use .Rprofile` Zrcadlových Server cran ayarlarında uyar, *. RProfile* dosya. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Çalışma alanı projesi açıldığında yükleme | `No` | Ayarını `Yes` oturum verileri yüklemeyi etkinleştirir *. RData* projesi açıldığında genel ortamına dosya. |
| Çalışma alanını Sıfırla kaydetmeden önce sor | `Yes` | Ayarını `No` etkileşimli pencerede Sıfırla düğmesine tıkladığınızda çalışma alanınızı kaydetmek istemi devre dışı bırakır. |
| Proje kapandığında çalışma alanını kaydetme | `No` | Ayarını `Yes` genel ortama kaydetmeyi etkinleştirir *. RData* proje kapatıldığında dosya. |
| Çalışma alanları geçmeden önce onay iletişim kutusunu göster | `Yes` | Ayarını `No` farklı çalışma alanları arasında geçiş yaparken kullanıcıdan onay için sormak devre dışı bırakır. Bkz: [çalışma alanları arasında geçiş yapma](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yük Gösterge Göster | `False` | Durum çubuğunda CPU/bellek/Ağ Yük göstergenin görünürlüğünü denetler. Göstergenin ağ trafiğinin artmasına neden olur çünkü bu tutmak yararlı `False` uzak tarifeli senaryolarda. Bu seçenek değiştirilmesi, Visual Studio'yu yeniden başlatmanız gerekir. |
