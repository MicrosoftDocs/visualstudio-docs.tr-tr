---
title: R ile verileri Görselleştirme
description: Visual Studio'da çizim windows kullanarak, R programlarından verileri çizmek nasıl.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: f44ba213defef153acd2f5d1ef247bb093448263
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238390"
---
# <a name="create-visual-data-plots-with-r"></a>Görsel veri çizimleri R ile oluşturma

Çizim, bir veri Bilimcisi'nın iş akışı anahtar bir parçasıdır. R araçları için Visual Studio (RTVS)'da, tüm çizim etkinlik bu anahtar etkinlik verimliliğinizi artırmak için tasarlanmış bir veya daha fazla çizim windows çevresinde toplanır.

![Kahramanı görüntü çizme](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![video kamera simgesine film](../install/media/video-icon.png "bir videoyu izleyin") | [(Youtube.com) bir video izlemek](https://www.youtube.com/watch?v=ZTbKmz5RSgY) (2 m 02s) R ile Çizdirmek üzerinde. |

## <a name="the-plot-window"></a>Çizim penceresi

Çizimler, burada her çizim tarafından oluşturulur bir dizi bir çizim penceresi tutan bir `plot` komutu. Örneğin, kullanarak `plot(1:100)` bir zaten mevcut değilse yeni bir çizim penceresi oluşturur:

![1 ile 100 doğrusal çizim](media/plotting-1-to-100.png)

Teknik olarak konuşarak, R `plot` komutları işleme çıktılarını bir R grafik cihazına; bir çizim penceresi her çizim penceresi aygıt numarası verilen neden olan bir R grafik cihaz içeriğini oluşturur.

Çizim windows Visual Studio projeleri bağımsızdır ve yük ve projeleri kapatın gibi açık kalır.

Bir çizim oluşturma kullanır "active" çizim penceresinde herhangi önceki kaydetme çizim, çizim geçmişi (bkz [çizim geçmişi](#plot-history)). Örneğin, `plot(100:1)` ve ilk çizim aşağıya doğru satır ile değiştirilir.

Diğer tüm Visual Studio windows gibi. Özel düzenler çizim penceresi destekler (bkz [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md). Çizim windows Visual Studio çerçevesinde farklı konumlarda yerleşik, o çerçevesinde yeniden boyutlandırılmış veya tamamen bağımsız yeniden boyutlandırma için çerçeve dışında çekilen. 

Bir çizim penceresi her zaman yeniden boyutlandırma en iyi kalite görüntü sağlamak için çizim yeniden oluşturur. Tipik olarak bir çizim çizim bir dosyaya veya bir sonraki bölümde açıklanan komutları kullanarak Pano dışarı aktarmadan önce yeniden boyutlandırma istersiniz.

## <a name="plot-window-commands"></a>Çizim penceresi komutları

Çizim pencerenin araç çoğunu aracılığıyla da uygulanabilir komutların tutan **R Araçları** > **çizimleri** menüsü.

| Düğme | Komut | Açıklama | 
| --- | --- | --- |
| ![Yeni çizim penceresi düğmesi](media/plotting-toolbar-01-new-plot-window.png) | Yeni bir çizim penceresi | Ayrı çizim pencere kendi geçmişi ile oluşturur. Bkz: [birden çok çizim windows](#multiple-plot-windows). |
| ![Çizim penceresi düğmesini etkinleştirin](media/plotting-toolbar-02-activate-plot-window.png) | Çizim pencereyi etkinleştir | Etkin pencereyi, bu nedenle bu sonraki geçerli çizim penceresi ayarlar `plot` komutları pencereye işlenir. Bkz: [birden çok çizim windows](#multiple-plot-windows). Bkz: [birden çok çizim windows](#multiple-plot-windows). |
| ![Çizim Geçmişi penceresini düğmesi](media/plotting-toolbar-03-plot-history.png) | Çizim Geçmiş penceresi | Küçük resim olarak gösterilen geçmişinde tüm çizimleri ile bir pencere açılır. Bkz: [çizim geçmişi](#plot-history). |
| ![Çizim geçmişi düğmeleri](media/plotting-toolbar-04-plot-history-arrows.png) | Önceki/sonraki çizim |  Önceki veya sonraki çizim geçmişinde gider. Ctrl + Alt + F11 (önceki) ve Ctrl + Alt + F12 (İleri) geçmişini de gidebilirsiniz. Bkz: [çizim geçmişi](#plot-history). |
| ![Görüntü Farklı Kaydet düğmesi](media/plotting-toolbar-05-save-as-image.png)| Resim olarak Kaydet | İçin bir dosya adı ister ve geçerli çizim (penceresi içeriği, pencere boyutunu) bir görüntü dosyasına kaydeder. Kullanılabilir biçimleri `.png`, `.jpg`, `.bmp`, ve `.tif`. |
| ![PDF Farklı Kaydet düğmesi](media/plotting-toolbar-06-save-as-pdf.png)| PDF olarak Kaydet | Geçerli çizim geçerli pencere boyutunu kullanarak bir PDF dosyasına kaydeder. PDF ölçeklendirilir varsa çizim yeniden oluşturmaz. |
| ![Bit eşlem düğmesi olarak Kopyala](media/plotting-toolbar-07-copy-as-bitmap.png)| Bit eşlem olarak Kopyala | Çizim panoya geçerli pencere boyutunu kullanarak bir ızgara bitmap olarak kopyalar. | 
| ![Meta dosyası düğmesi olarak Kopyala](media/plotting-toolbar-08-copy-as-metafile.png)| Meta dosyası olarak Kopyala | Panoya olarak çizim kopyalar bir [Windows Meta dosyası](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). | 
| ![Çizim düğmesini Kaldır](media/plotting-toolbar-09-remove-plot.png)| Çizim Kaldır | Geçerli çizim geçmişinden kaldırır. |
| ![Temizle tüm çizimleri düğmesi](media/plotting-toolbar-10-clear-all-plots.png) | Tüm çizimleri temizleyin | Tüm çizimleri geçmişi (onay ister) kaldırır. |

## <a name="multiple-plot-windows"></a>Birden çok çizim windows

Veri bilimcilerine genellikle birçok farklı veri kümelerindeki birçok çizimleri çalışmak için RTVS sayıda bağımsız çizim windows oluşturmanıza olanak sağlar. Visual Studio çerçevesi içinde veya dışında çerçeve tamamen gibi ancak bu windows sonra düzenleyebilirsiniz. (Bkz [Visual Studio'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) yerleştirme ve windows yeniden boyutlandırma hakkında genel bilgi için.)

Araç çubuğu düğmesini kullanarak yeni bir çizim penceresi oluşturun veya **R Araçları** > **çizimleri** > **yeni çizim pencere**. Yeni bir çizim penceresi hale *etkin* , burada yeni çizimleri işlendiğini olan penceresinin. Etkin pencereyi değiştirmek için kendisine geçiş yapın ve seçin **çizim penceresi etkinleştirme** araç çubuğu düğmesini veya **R Araçları** > **çizer**  >  **Çizim penceresini etkinleştirmek**.

Çizimler, çok, kopyalama veya bunları çizim windows ya da sürükle ve bırak fareyle veya kullanarak kullanarak arasında taşıma anlamına gelir nesneleri bağımsız olan **kopya**, **Kes**, ve **Yapıştır** sağ bağlam komutlarını ve **Düzenle** menüleri.

Sürükle ve bırak için varsayılan davranış kopyasıdır; taşımak için sürükle ve tutarken bırak **Shift** anahtarı.

## <a name="plot-history"></a>Çizim geçmişi

Çizim komutları tüm, bir oturumda Çizdirmek korunur sağlayarak her pencere için çizim geçmişi korunur. Geçmiş gidin, çizim penceresi araç çubuğunda, ok düğmelerini kullanın veya **Ctrl**+**Alt**+**F11** ve **Ctrl** + **Alt**+**F12**. Ayrıca tek çizimleri kaldırın veya araç çubuğu düğmelerini kullanarak yeniden penceresinden tüm çizimleri temizleyin veya **R Araçları** > **çizer** menü komutları.

Çizimler koleksiyonunun tamamını görmek için araç çubuğu düğmesini kullanarak çizim Geçmişi penceresini açın veya **R Araçları** > **çizer** > **çizim Geçmişi penceresini**.
Geçmiş farklı çizim windows (veya aygıt) göre gruplandırılan bu penceresinde görüntülenen çizimleri için küçük bir listesi verilmektedir. Araç çubuğundaki Yakınlaştır düğmeleri kullanarak küçük resimlerin boyutunu değiştirir.

![Çizim Geçmiş penceresi](media/plotting-plot-history-window.png)

Bir çizim ilişkili penceresinde açmak için bu çizim çift tıklayın, seçin ve ardından **Göster çizim** araç çubuğu düğmesini veya sağ tıklatın ve seçin **Göster çizim**. Tek bir öğesini de seçebilirsiniz çizim ve kopyalama, kesme veya sağ bağlamdan silin veya **Düzenle** menüleri.

Çizim geçmişinizi tüm pencereleri arasında ömrü etkileşimli R oturumunuz için kullanım ömrü bağlıdır. R oturumunuz sıfırlama veya çıkmak ve Visual Studio'yu yeniden başlatın, çizim geçmişinizi sıfırlanır.

## <a name="programmatically-manipulate-plot-windows"></a>Çizim windows programsal

Çizim windows R kodundan belirli çizim windows belirlemek için cihazın sayılar kullanılarak programlı olarak yönetebilirsiniz. 

- `dev.list()`: Tüm grafik aygıtları geçerli R oturumunda listeleyin.
- `dev.new()`: Yeni bir grafik cihaz (yeni bir çizim pencere) oluşturun.
- `dev.set(<device number>)`: Etkin grafik aygıtı ayarlayın.
- `dev.off()`: Etkin cihaz silin.
