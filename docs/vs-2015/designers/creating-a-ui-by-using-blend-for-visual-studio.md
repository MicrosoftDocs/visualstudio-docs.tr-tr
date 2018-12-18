---
title: Blend'i kullanarak kullanıcı Arabirimi oluşturma
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
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f77fba9ed184d5def85aa7ca260b7c552dddbfd1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054547"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için Blend, XAML tabanlı Windows Masaüstü, web tasarlamanıza yardımcı olan [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx), ve [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) uygulamalar. Visual Studio aynı temel XAML tasarım deneyimini sunar ve animasyon ve davranışlarla gibi gelişmiş görevler için görsel tasarımcılar ekler.

 Visual Studio için Blend, Visual Studio'nun bir parçası dahil olduğundan, bunu indirmeniz gerekmez. Ancak sisteminizde yüklemek için Visual Studio yükleyicisi de seçmeniz gerekir.

 Visual Studio için Blend yeniyseniz, çalışma alanının benzersiz özellikleri ile aşina olmak için bir dakikanızı ayırın. Bu konu üzerinde hızlı bir tura alır.

> [!NOTE]
>  Çalışma yüzeyi, Belge Anahattı penceresi ve cihaz penceresi gibi paylaşılan tasarım özelliklerini anlatan bir tura için bkz: [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **Bu konudaki**:

-   [Araçlar panelini turu](#Tools)

-   [Varlıklar panelini turu](#Assets)

-   [Nesneler ve zaman çizelgesi Gezinti paneli](#Objects)

-   [Özellikler panelini turu](#Properties)

##  <a name="Tools"></a> Araçlar panelini turu
 Kullanabileceğiniz **Araçları** uygulamanızdaki nesneleri oluşturup değiştirmesi Visual Studio için blend'de paneli. Bir araç seçerek ve farenizle çalışma yüzeyi üzerinde çizim nesneleri oluşturun.

 ![Araçlar paneli](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Seçim araçları** nesneleri ve yolları seçin.<br /><br /> Kullanım **doğrudan seçim** iç içe geçmiş nesnelerde ve yol kesimleri seçme aracı.|![Belirtme çizgisi A](../designers/media/b5-label-a.png "b5_label_A")|**Gradyan ve fırça araçları**|
|![](../designers/media/b1-2.png "B1_2")|**Görünüm Araçları** kaydırma ve yakınlaştırma için olduğu gibi çalışma yüzeyinin görünümü ayarlayın.|![Belirtme çizgisi B](../designers/media/b5-label-b.png "b5_label_B")|**Yol araçları**|
|![](../designers/media/b1-3.png "B1_3")|**Fırça Araçları** fırça dönüştürme, bir nesne boyama veya onları başka bir nesneye uygulamak için bir nesne öznitelikleri seçme gibi bir nesnenin görsel öznitelikleri ile çalışır.|![Belirtme çizgisi C](../designers/media/b5-label-c.png "b5_label_C")|**Şekil araçları**|
|![](../designers/media/b1-4.png "B1_4")|**Nesne Araçları** en yaygın nesneleri yolları, şekiller, Düzen bölmeleri, metin ve denetimler gibi çalışma yüzeyinde çizin.|![Belirtme çizgisi D](../designers/media/b5-label-d.png "b5_label_D")|**Düzen bölmeleri**|
|![](../designers/media/b1-5.png "B1_5")|**Varlık Araçları** erişim **varlıklar** paneli ve en son göstermek için kitaplıktan varlık kullanılır.|![Belirtme çizgisi E](../designers/media/b5-label-e.png "b5_label_E")|**Metin denetimi**|
|||![Belirtme çizgisi F](../designers/media/b5-label-f.png "b5_label_F")|**Ortak Denetimler**|

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [araç](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

##  <a name="Assets"></a> Varlıklar panelini turu
 Tüm denetimleri bulabilirsiniz **varlıklar** paneli, benzer **araç kutusu** Visual Studio'da. Denetimleri ek olarak, her şey için çalışma yüzeyine ekleyebilirsiniz bulabilirsiniz **varlıklar** paneli, stilleri, ortam, davranışları ve efektleri gibi.

 ![Varlıklar paneli](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Arama kutusuna** yazın **arama** varlıklar listesine filtre uygulamak için.|
|![](../designers/media/b1-2.png "B1_2")|**Kılavuz modu ve liste modu** arasında geçiş **kılavuz modu** görünümü ve **liste modu** varlıklar görünümü.|
|![](../designers/media/b1-3.png "B1_3")|**Varlıklar kategorileri** bir kategori veya alt kategorideki varlıkların listesini görüntülemek için tıklayın.|
|![](../designers/media/b1-4.png "B1_4")|**Stilleri** kaynak sözlüğünde yer alan tüm stilleri gösterir.|
|![](../designers/media/b1-5.png "B1_5")|**Açıklama** seçili varlıklar kategorisinin veya alt kategorinin açıklamasını görüntüleyin.|

##  <a name="Objects"></a> Nesneler ve zaman çizelgesi Gezinti paneli
 Çalışma yüzeyinde nesneleri düzenlemek için bu paneli kullanın ve bunları animasyon uygulamak isterseniz.

 ![Nesne ve zaman çizelgesi panelinde Animasyon modunda](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Nesneler görünümü** bir belgenin görsel ağacı görüntüleyin. Farklı düzeylerde ayrıntıya gidebilirsiniz. Daha fazla çalışma yüzeyinde nesneleri düzenlemek için katmanları da ekleyebilirsiniz. Bu şekilde kilitlemek ve onları bir grup olarak gizleyebilirsiniz.|
|![](../designers/media/b1-2.png "B1_2")|**Kayıt modu göstergesi** bir zaman çizelgesinde özellik değişiklikleri kaydederken olmadığını bakın.|
|![](../designers/media/b1-3.png "B1_3")|**Film şeridi Seçicisi** oluşturduğunuz görsel taslaklara listesini görüntüleyin.|
|![](../designers/media/b1-4.png "B1_4")|**Görsel taslağı Kapat** geçerli görsel taslağı kapatın.|
|![](../designers/media/b1-5.png "B1_5")|**Film şeridi seçenekleri** oluşturun, yinelenen, ters, silme, yeniden adlandırmak veya bir görsel taslağı kapatın.|
|![](../designers/media/b1-6.png "B1_6")|**Kayıttan yürütme denetimleri** zaman çizelgesi boyunca gidin. Gezinmek için oynatma kafasını da sürükleyebilirsiniz (veya *kaydırın*) zaman çizelgesi.|
|![](../designers/media/b1-7.png "B1_7")|**Kapsamı geri döndür** kapsamını önceki kök nesneye veya önceki kapsama için nesneleri görüntüleyin. Bir stil veya şablon yalnızca değişiklik yaptığınız zaman bunu yapabilirsiniz.|
|![](../designers/media/b1-8.png "B1_8")|**Ana kareyi kaydedin** sürede seçili nesnenin geçerli noktadaki özelliklerinin anlık görüntüsünü kayıt.|
|![](../designers/media/b1-9.png "B1_9")|**Yaslama seçenekleri** zaman çizelgesi yaslamasını ayarlayın, yaslama çözünürlüğü ve zaman çizelgesi yaslamasını açın.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Göster/Gizle**, **Kilitle/Kilidini Aç** göster veya gizle görünürlük ve kilitleme seçenekleri nesneleri görüntülemek için.|
|![](../designers/media/b1-11.png "B1_11")|**Oynatma kafası zaman çizelgesinde** milisaniye olarak geçerli saati gösterir. Zaman içinde belirli bir noktaya atlamak için bu alana doğrudan bir zaman değeri girebilirsiniz. Duyarlık ayarlanan yaslama çözünürlüğünü bağlıdır **yaslama seçenekleri**.|
|![](../designers/media/b1-12.png "B1_12")|**Oynatma kafası** ne animasyonun zaman noktasından belirleyin. Animasyonun önizlemesini görüntülemek için, oynatma kafasını zaman çizelgesi boyunca sürükleyebilirsiniz.|
|![](../designers/media/b1-13.png "B1_13")|**Çizelgelerinde ayarlanan ana kareler** zaman içinde belirli bir noktada bir özellik değeri değiştirin.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Nesnelerin sırasını değiştir** nesnelerinin görüntülenme sırasını ayarlayın. Nesneleri yapı görünümünde Z sırasına (önden arkaya) veya biçimlendirme sırasına göre düzenlemek için bu düğmeye tıklayın (içinde görünen sırası **XAML** Görünüm).|
|![](../designers/media/b1-15.png "B1_15")|**Zaman Çizelgesi Yakınlaştırması** zaman çizelgesinin yakınlaştırma çözünürlüğünü ayarlayın. Yakınlaştırma bir animasyonu daha ayrıntılı düzenlemenize izin verir ve uzaklaştırmaysa daha uzun süreler boyunca neler olduğuna ilişkin daha kapsamlı bir özet gösterir. Yakınlaştırma yapar, ancak zaman içinde istediğiniz konumunda bir ana kare ayarlayamazsınız, yaslama çözünürlüğünün yeterince yüksek olarak ayarlandığını doğrulayın.|
|![Belirtme çizgisi 16](../designers/media/b5-label-16.png "b5_label_16")|**Zaman Çizelgesi kompozisyon alanı** zaman çizelgesini görüntüleyin ve ana kareleri sürükleyerek veya kendi kısayol menülerini kullanarak taşıyabilirsiniz.|

##  <a name="Properties"></a> Özellikler panelini turu
 Bir nesnenin özelliklerini görüntüleme ve değiştirme için bu paneli kullanın. Bunları doğrudan çalışma yüzeyi üzerinde de ayarlayabilirsiniz. Bunu yaparsanız, özellik değişikliklerinin yansıtılır **özellikleri** paneli.

 ![Özellikler panelini](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategorileri** Genişlet ve Daralt kategorileri özellikleri. Tıklayın **genişletin** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") ve **Daralt** ![Daralt](../designers/media/b5-collapse-button.png "b5_collapse_button") kategorisi ayrıntıları göstermek veya gizlemek için.


|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Ad ve tür** simgesi, ad ve seçili nesnenin türünü görüntüleyin.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Düzenleme ölçütü** adı, kaynak veya kategoriye göre alfabetik olarak özelliklerini düzenleyin.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Fırça özellikleri** Fırçalar dolgu Fırçası ve vuruş fırça ön plan fırça gibi görsel özelliklerini ayarlayın.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Renk Düzenleyicisi** düz renk ve gradyan fırçası için kullanın.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Renk Seçici** bir renk seçin.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Renk yongaları** ilk renk, geçerli bir renk ve son rengi görüntüleyin                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Damlalıkları** ekrandaki herhangi bir öğenin rengini kullanın. **Renk damlalığı** kullanılabilir olduğunda **tek renk Fırçası** seçilir. **Gradyan renk damlalığı** kullanılabilir olduğunda **gradyan fırçası** seçilir. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Özellikler ve olaylar** özellikleri ayarlamak veya seçili öğe için olayları seçin.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Arama kutusuna** özellikleri arayın. Yazarak görüntülenen özellikleri filtrelemek **arama** kutusu.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Fırça Düzenleyicisi sekmeleri** bir fırça Düzenleyicisi'ni seçmek için kullanın. Seçebileceğiniz **fırça yok**, **tek renk Fırçası**, **gradyan fırçası**, **döşeme Fırçası**, veya **fırça kaynağı**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Renk kaynakları** farklı özelliklere tam aynı rengi uygulayın. **Renk kaynakları** sekmesini içeren **yerel kaynakları** ve **sistem kaynaklarının**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **RGB renk alanı** değerleri ayarlayarak rengi değiştirme **R**, **G**, veya **B** (kırmızı, yeşil, mavi) sayı düzenleyiciler.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Alfa kanalını** yanındaki numara düzenleyici kullanarak alfa değeri değiştirmek **A**.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Rengi kaynağa dönüştürün** seçilen rengi bir rengi kaynağa dönüştürün. Renk kaynakları renk Kaynaklar sekmesini tıkladığınızda kullanılabilir.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Onaltılık değer** görüntülenen renk onaltılık değerini görüntüleyin.                                                                                 |
|                     ![Belirtme çizgisi 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Gradyan kaydırıcı** yalnızca bir gradyan fırçası seçtiyseniz görünür.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Gelişmiş özellikleri göster** daha az yaygın olarak kullanılan özellikleri kategorilerini görüntüleyin.                                                                      |

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [özellikler panelini](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Ayrıca Bkz.
 [Denetimler ekleme ve bunların davranışlarını değiştirme](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [nesneleri](../designers/animate-objects-in-xaml-designer.md) [şekiller ve yollar çizin](../designers/draw-shapes-and-paths.md) [Visual Studio ve Visual Studio için Blend, XAML tasarlama](../designers/designing-xaml-in-visual-studio.md)
