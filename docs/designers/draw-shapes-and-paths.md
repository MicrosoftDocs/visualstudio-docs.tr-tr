---
title: Şekiller ve yollar çizin
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97172253a088be86f20fae77fe62d01330a3b801
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513104"
---
# <a name="draw-shapes-and-paths"></a>Şekiller ve yollar çizin

XAML Tasarımcısı'nda bir *şekli* tamamen beklediğiniz. Örneğin: dikdörtgen, daire veya elips. A *yolu* bir şekil daha esnek bir sürümüdür. Yeni şekil için bunları birleştirmek ya da bunları yeniden şekillendirmek gibi şeyler.

Şekiller ve yollar iyi yüksek çözünürlüklü ekranlar için ölçeklendirme vektör grafik kullanın. Vektör grafikleri hakkında daha fazla bilgi edinmek istiyorsanız bkz [vektör grafikleri nelerdir](https://www.youtube.com/watch?v=MoCSwF0n-io) veya [vektör grafikleri](http://www.webopedia.com/TERM/V/vector_graphics.html).

##  <a name="Shape"></a> Bir şekil çizme
 Şekillerde bulabilirsiniz **varlıklar** paneli.

 ![Şekil kategorisini varlıklar paneli](../designers/media/b4_shapes_assetspanel.png)

 İstediğiniz herhangi bir şekil, çalışma yüzeyine sürükleyin. Ardından, ölçeklendirme, döndürmek, taşıyın veya şekil eğriltmek için şeklin üzerinde tutamaçlarını kullanabilirsiniz.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

##  <a name="Path"></a> Bir yol çizin
 Bir dizi bağlantılı çizgiler ve eğrilerdir yoludur. Kullanılamayan, ilginç şekiller oluşturmak için bir yol kullanın **varlıklar** paneli.

 Bir yolu, bir satır, Kalem ve kağıt kullanarak çizebilirsiniz. Bu araçlarda bulabilirsiniz **Araçları** paneli.

 ![Kalem aracı](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Kalem aracı seçenekleri](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Düz çizgi çizme
 Kullanım **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png), veya **satırı** aracı ![Çizgi aracı](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png).

 **Kalem aracıyla** ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 Çalışma yüzeyinde başlangıç noktasını tanımlamak için bir kez tıklayın ve satırın sonuna tanımlamak için yeniden tıklayın.

 **Satırı aracını kullanarak** ![satırı aracı](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 Çalışma yüzeyinde satır başlatmak istediğiniz sürükleyin ve ardından çizginin sona ermesini istediğiniz noktada bırakın.

### <a name="draw-a-curve"></a>Eğri çizme
 Kullanım **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Çalışma yüzeyinde bir satırın başlangıç noktasını tanımlamak tıklayın ve istenen eğri oluşturmak için işaretçiyi sürükleyin için bir kez tıklayın.

 Yolu kapatmak istiyorsanız ilk satırın noktasında tıklayın.

### <a name="change-the-shape-of-a-curve"></a>Eğrinin şeklini değiştirme
 Kullanım **doğrudan seçim** aracı ![doğrudan seçim aracı](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Şekle tıklayın ve ardından eğri şekiller değiştirmek için şekli üzerinde herhangi bir noktaya sürükleyin.

### <a name="draw-a-free-form-path"></a>Serbest form yolu çizme
 Kullanım **kalem** aracı ![Kalem aracı](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 Çalışma yüzeyinde, gerçek bir kalem kullanarak yaptığınız gibi serbest biçimli yolu çizin.

### <a name="remove-part-of-a-path"></a>Yolun bir bölümünü kaldırın
 Kullanım **doğrudan seçim** aracı ![doğrudan seçim aracı](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Silin ve ardından istediğiniz kesimi içeren yolu seçin **Sil** düğmesi.

### <a name="remove-a-point-in-a-path"></a>Bir yolda bir noktası Kaldır
 Kullanım **seçimi** aracı ![seçim aracını](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png)ve **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Kullanım **seçimi** aracı ![seçim aracını](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) yolunu seçin. Ardından, **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) kaldırmak istediğiniz noktayı tıklatın.

### <a name="add-a-point-to-a-path"></a>Bir nokta yolunu Ekle
 Kullanım **seçimi** aracı ![seçim aracını](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png)ve **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Kullanım **seçimi** aracı ![seçim aracını](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) yolunu seçin. Kullanım **kalem** aracı ![Kalem aracı](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) noktası eklemek istediğiniz yola göre herhangi bir yeri tıklatın.

##  <a name="Convert"></a> Bir şekli bir yola Dönüştür
 Bir şekli bir yolu değiştirmek yollarla değiştirmek için şekli bir yola Dönüştür.

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [yolları ile çalışma: bir şekli bir yola dönüştürmek](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

##  <a name="Combine"></a> Yolları Birleştir
 Tek bir yol, yol ve Şekil birleştirebilirsiniz.

 ![Yolları Birleştir](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Birleştirme öncesi iki şekil](../designers/media/b1_1.png)|Birleştirme öncesi iki şekil|![Kesiştir](../designers/media/b1_4.png)|Kesiştir|
|![Örtüşmeyi Dışla](../designers/media/b1_2.png)|Birleştir|![](../designers/media/b1_5.png)|Örtüşmeyi Dışla|
|![Çıkarma](../designers/media/b1_3.png)|Bölme|![](../designers/media/b1_6.png)|Çıkarma|

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [yolları ile çalışma: yolları Birleştir](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

##  <a name="Compound"></a> Bileşik yol Oluştur
 Bileşik yol oluşturduğunuzda, yolların herhangi bir kesişen bölümleri sonuçtan çıkartılır ve sonuçlanan yol en alt yolun görsel özelliklerini kabul eder.

 Bileşik yol oluşturduktan sonra istediğiniz zaman parçalara ayırabilirsiniz.

 ![Bileşik yol Kes](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [yolları ile çalışma: bileşik yol Oluştur](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

##  <a name="Clipping"></a> Bir kırpma yolunu oluşturun
 Bir kırpma yolu, kırpma yolu dışına düşen maskelenmiş nesnenin kısımlarını saklayarak, diğer nesneye uygulanan bir yol veya şekildir.

 ![Kırpma yolu](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.png) [yolları ile çalışma: bir kırpma yolunu oluşturun](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)