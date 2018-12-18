---
title: Visual Studio için Blend - kullanıcı Arabirimi oluşturma
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76743674ef4e92f2ad52be108c1dafb8d942676c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059872"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma

Visual Studio için Blend tasarım XAML tabanlı Windows ve Web uygulamalarına yardımcı olur. Visual Studio aynı temel XAML tasarım deneyimini sunar ve animasyon ve davranışlarla gibi gelişmiş görevler için görsel tasarımcılar ekler. Blend ve Visual Studio arasında bir karşılaştırma için bkz. [Visual Studio ve Visual Studio için Blend tasarım XAML](../designers/designing-xaml-in-visual-studio.md).

Visual Studio için Blend, Visual Studio'nun bir bileşenidir. Blend, yüklemek için **Visual Studio yükleyicisi** seçin ya da **Evrensel Windows platformu geliştirme** veya **.NET Masaüstü geliştirmesinden** iş yükü. Bu iş yüklerinin hem de Visual Studio bileşeni için Blend içerir.

![UWP iş yükü bileşenleri](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET masaüstü geliştirme iş yükü bileşenleri](media/installer-dotnet-desktop.png)

Visual Studio için Blend yeniyseniz, çalışma alanının benzersiz özellikleri ile aşina olmak için bir dakikanızı ayırın. Bu konu üzerinde hızlı bir tura alır.

> [!NOTE]
> Paylaşılan tasarım özellikleri gibi çalışma yüzeyine gezmesine izin **belge anahattı** penceresinde ve **cihaz** penceresinde görmek [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Araçlar panelini turu

Kullanabileceğiniz **Araçları** uygulamanızdaki nesneleri oluşturup değiştirmesi Visual Studio için blend'de paneli. Bir araç seçerek ve farenizle çalışma yüzeyi üzerinde çizim nesneleri oluşturun.

![Araçlar paneli](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![Seçim araçları](../designers/media/b1_1.png)|**Seçim araçları** nesneleri ve yolları seçin.<br /><br /> Kullanım **doğrudan seçim** iç içe geçmiş nesnelerde ve yol kesimleri seçme aracı.|![Bir açıklama balonu](../designers/media/b5_label_a.png)|**Gradyan ve fırça araçları**|
|![Görünüm Araçları](../designers/media/b1_2.png)|**Görünüm Araçları** kaydırma ve yakınlaştırma için olduğu gibi çalışma yüzeyinin görünümü ayarlayın.|![Belirtme çizgisi B](../designers/media/b5_label_b.png)|**Yol araçları**|
|![Fırça araçları](../designers/media/b1_3.png)|**Fırça Araçları** fırça dönüştürme, bir nesne boyama veya onları başka bir nesneye uygulamak için bir nesne öznitelikleri seçme gibi bir nesnenin görsel öznitelikleri ile çalışır.|![Belirtme çizgisi C](../designers/media/b5_label_c.png)|**Şekil araçları**|
|![Nesne araçları](../designers/media/b1_4.png)|**Nesne Araçları** en yaygın nesneleri yolları, şekiller, Düzen bölmeleri, metin ve denetimler gibi çalışma yüzeyinde çizin.|![Belirtme çizgisi D](../designers/media/b5_label_d.png)|**Düzen bölmeleri**|
|![Varlık araçları](../designers/media/b1_5.png)|**Varlık Araçları** erişim **varlıklar** paneli ve en son göstermek için kitaplıktan varlık kullanılır.|![Belirtme çizgisi E](../designers/media/b5_label_e.png)|**Metin denetimi**|
|||![Belirtme çizgisi F](../designers/media/b5_label_f.png)|**Ortak Denetimler**|

**Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [araç](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Varlıklar panelini turu

Tüm denetimleri bulabilirsiniz **varlıklar** paneli, benzer **araç kutusu** Visual Studio'da. Denetimleri ek olarak, her şey için çalışma yüzeyine ekleyebilirsiniz bulabilirsiniz **varlıklar** paneli, stilleri, ortam, davranışları ve efektleri gibi.

![Varlıklar paneli](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Arama kutusuna** yazın **arama** varlıklar listesine filtre uygulamak için.|
|![Kılavuz modu ve liste modu](../designers/media/b1_2.png)|**Kılavuz modu ve liste modu** arasında geçiş **kılavuz modu** görünümü ve **liste modu** varlıklar görünümü.|
|![Varlıklar kategorileri](../designers/media/b1_3.png)|**Varlıklar kategorileri** bir kategori veya alt kategorideki varlıkların listesini görüntülemek için tıklayın.|
|![Stilleri](../designers/media/b1_4.png)|**Stilleri** kaynak sözlüğünde yer alan tüm stilleri gösterir.|
|![Açıklama](../designers/media/b1_5.png)|**Açıklama** seçili varlıklar kategorisinin veya alt kategorinin açıklamasını görüntüleyin.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Nesneler ve zaman çizelgesi Gezinti paneli

Çalışma yüzeyinde nesneleri düzenlemek için bu paneli kullanın ve bunları animasyon uygulamak isterseniz.

![Animasyon modunda nesne ve zaman çizelgesi paneli](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Nesneleri görüntüle](../designers/media/b1_1.png)|**Nesneler görünümü** bir belgenin görsel ağacı görüntüleyin. Farklı düzeylerde ayrıntıya gidebilirsiniz. Daha fazla çalışma yüzeyinde nesneleri düzenlemek için katmanları da ekleyebilirsiniz. Bu şekilde kilitlemek ve onları bir grup olarak gizleyebilirsiniz.|
|![Kayıt modu göstergesi](../designers/media/b1_2.png)|**Kayıt modu göstergesi** bir zaman çizelgesinde özellik değişiklikleri kaydederken olmadığını bakın.|
|![Film şeridi Seçicisi](../designers/media/b1_3.png)|**Film şeridi Seçicisi** oluşturduğunuz görsel taslaklara listesini görüntüleyin.|
|![Görsel taslağı Kapat](../designers/media/b1_4.png)|**Görsel taslağı Kapat** geçerli görsel taslağı kapatın.|
|![Görsel taslak seçenekleri](../designers/media/b1_5.png)|**Film şeridi seçenekleri** oluşturun, yinelenen, ters, silme, yeniden adlandırmak veya bir görsel taslağı kapatın.|
|![Kayıttan yürütme denetimleri](../designers/media/b1_6.png)|**Kayıttan yürütme denetimleri** zaman çizelgesi boyunca gidin. Gezinmek için oynatma kafasını da sürükleyebilirsiniz (veya *kaydırın*) zaman çizelgesi.|
|![Kapsamı geri döndür](../designers/media/b1_7.png)|**Kapsamı geri döndür** kapsamını önceki kök nesneye veya önceki kapsama için nesneleri görüntüleyin. Bir stil veya şablon yalnızca değişiklik yaptığınız zaman bunu yapabilirsiniz.|
|![Ana kareyi kaydedin](../designers/media/b1_8.png)|**Ana kareyi kaydedin** sürede seçili nesnenin geçerli noktadaki özelliklerinin anlık görüntüsünü kayıt.|
|![Yaslama seçenekleri](../designers/media/b1_9.png)|**Yaslama seçenekleri** zaman çizelgesi yaslamasını ayarlayın, yaslama çözünürlüğü ve zaman çizelgesi yaslamasını açın.|
|![Göster Gizle Kilitle Kilidini Aç](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Göster/Gizle**, **Kilitle/Kilidini Aç** göster veya gizle görünürlük ve kilitleme seçenekleri nesneleri görüntülemek için.|
|![Zaman çizelgesinde oynatma kafası konumu](../designers/media/b1_11.png)|**Oynatma kafası zaman çizelgesinde** milisaniye olarak geçerli saati gösterir. Zaman içinde belirli bir noktaya atlamak için bu alana doğrudan bir zaman değeri girebilirsiniz. Duyarlık ayarlanan yaslama çözünürlüğünü bağlıdır **yaslama seçenekleri**.|
|![Oynatma](../designers/media/b1_12.png)|**Oynatma kafası** ne animasyonun zaman noktasından belirleyin. Animasyonun önizlemesini görüntülemek için, oynatma kafasını zaman çizelgesi boyunca sürükleyebilirsiniz.|
|![Çizelgelerinde ayarlanan ana kareler](../designers/media/b1_13.png)|**Çizelgelerinde ayarlanan ana kareler** zaman içinde belirli bir noktada bir özellik değeri değiştirin.|
|![Nesnelerin sırasını değiştirme](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Nesnelerin sırasını değiştir** nesnelerinin görüntülenme sırasını ayarlayın. Nesneleri yapı görünümünde Z sırasına (önden arkaya) veya biçimlendirme sırasına göre düzenlemek için bu düğmeye tıklayın (içinde görünen sırası **XAML** Görünüm).|
|![Zaman Çizelgesi Yakınlaştırması](../designers/media/b1_15.png)|**Zaman Çizelgesi Yakınlaştırması** zaman çizelgesinin yakınlaştırma çözünürlüğünü ayarlayın. Yakınlaştırma bir animasyonu daha ayrıntılı düzenlemenize izin verir ve uzaklaştırmaysa daha uzun süreler boyunca neler olduğuna ilişkin daha kapsamlı bir özet gösterir. Yakınlaştırma yapar, ancak zaman içinde istediğiniz konumunda bir ana kare ayarlayamazsınız, yaslama çözünürlüğünün yeterince yüksek olarak ayarlandığını doğrulayın.|
|![Belirtme çizgisi 16](../designers/media/b5_label_16.png)|**Zaman Çizelgesi kompozisyon alanı** zaman çizelgesini görüntüleyin ve ana kareleri sürükleyerek veya kendi kısayol menülerini kullanarak taşıyabilirsiniz.|

## <a name="tour-of-the-properties-panel"></a>Özellikler panelini turu

Bir nesnenin özelliklerini görüntüleme ve değiştirme için bu paneli kullanın. Bunları doğrudan çalışma yüzeyi üzerinde de ayarlayabilirsiniz. Bunu yaparsanız, özellik değişikliklerinin yansıtılır **özellikleri** paneli.

![Özellikler paneli](../designers/media/blend5_properties_panel.png)

**Kategorileri** Genişlet ve Daralt kategorileri özellikleri. Tıklayın **genişletme** ![genişletme](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) ve **Daralt** ![Daralt](../designers/media/b5_collapse_button.png) kategorisi ayrıntıları göstermek veya gizlemek için.

|||
|-|-|
|![Ad ve tür](../designers/media/b1_1.png)|**Ad ve tür** simgesi, ad ve seçili nesnenin türünü görüntüleyin.|
|![Düzenleme ölçütü](../designers/media/b1_2.png)|**Düzenleme ölçütü** adı, kaynak veya kategoriye göre alfabetik olarak özelliklerini düzenleyin.|
|![Fırça özellikleri](../designers/media/b1_3.png)|**Fırça özellikleri** Fırçalar dolgu Fırçası ve vuruş fırça ön plan fırça gibi görsel özelliklerini ayarlayın.|
|![Renk Düzenleyicisi](../designers/media/b1_4.png)|**Renk Düzenleyicisi** düz renk ve gradyan fırçası için kullanın.|
|![Renk Seçici](../designers/media/b1_5.png)|**Renk Seçici** bir renk seçin.|
|![Renk yongaları](../designers/media/b1_6.png)|**Renk yongaları** ilk renk, geçerli bir renk ve son rengi görüntüleyin|
|![Damlalıkları](../designers/media/b1_7.png)|**Damlalıkları** ekrandaki herhangi bir öğenin rengini kullanın. **Renk damlalığı** kullanılabilir olduğunda **tek renk Fırçası** seçilir. **Gradyan renk damlalığı** kullanılabilir olduğunda **gradyan fırçası** seçilir.|
|![Özellikler ve olaylar](../designers/media/b1_8.png)|**Özellikler ve olaylar** özellikleri ayarlamak veya seçili öğe için olayları seçin.|
|![Arama kutusu](../designers/media/b1_9.png)|**Arama kutusuna** özellikleri arayın. Yazarak görüntülenen özellikleri filtrelemek **arama** kutusu.|
|![Fırça Düzenleyicisi sekmeleri](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Fırça Düzenleyicisi sekmeleri** bir fırça Düzenleyicisi'ni seçmek için kullanın. Seçebileceğiniz **fırça yok**, **tek renk Fırçası**, **gradyan fırçası**, **döşeme Fırçası**, veya **fırça kaynağı**.|
|![Renk kaynağı](../designers/media/b1_11.png)|**Renk kaynakları** farklı özelliklere tam aynı rengi uygulayın. **Renk kaynakları** sekmesini içeren **yerel kaynakları** ve **sistem kaynaklarının**.|
|![RGB renk alanı](../designers/media/b1_12.png)|**RGB renk alanı** değerleri ayarlayarak rengi değiştirme **R**, **G**, veya **B** (kırmızı, yeşil, mavi) sayı düzenleyiciler.|
|![Alfa kanalı](../designers/media/b1_13.png)|**Alfa kanalını** yanındaki numara düzenleyici kullanarak alfa değeri değiştirmek **A**.|
|![Rengi kaynağa dönüştürün](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Rengi kaynağa dönüştürün** seçilen rengi bir rengi kaynağa dönüştürün. Renk kaynakları renk Kaynaklar sekmesini tıkladığınızda kullanılabilir.|
|![](../designers/media/b1_15.png)|**Onaltılık değer** görüntülenen renk onaltılık değerini görüntüleyin.|
|![Belirtme çizgisi 16](../designers/media/b5_label_16.png)|**Gradyan kaydırıcı** yalnızca bir gradyan fırçası seçtiyseniz görünür.|
|![Gelişmiş özellikleri göster](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Gelişmiş özellikleri göster** daha az yaygın olarak kullanılan özellikleri kategorilerini görüntüleyin.|

**Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [özellikler panelini](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler ekleme ve bunların davranışlarını değiştirme](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Nesnelere animasyon ekleme](../designers/animate-objects-in-xaml-designer.md)
- [Şekiller ve yollar çizme](../designers/draw-shapes-and-paths.md)
- [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../designers/designing-xaml-in-visual-studio.md)
