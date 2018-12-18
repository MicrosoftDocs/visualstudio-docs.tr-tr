---
title: Şekiller ve yollar çizin | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0f59ecbdf9e69093d5c445cdb6d4780eb3b6f86e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188194"
---
# <a name="draw-shapes-and-paths"></a>Şekiller ve yollar çizin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML Tasarımcısı'nda bir *şekli* tamamen beklediğiniz. Örneğin: dikdörtgen, daire veya elips. A *yolu* bir şekil daha esnek bir sürümüdür. Yeni şekil için bunları birleştirmek ya da bunları yeniden şekillendirmek gibi şeyler.  
  
 Şekiller ve yollar iyi yüksek çözünürlüklü ekranlar için ölçeklendirme vektör grafik kullanın. Vektör grafikleri hakkında daha fazla bilgi edinmek istiyorsanız bkz [vektör grafikleri nelerdir](https://www.youtube.com/watch?v=MoCSwF0n-io) veya [vektör grafikleri](http://www.webopedia.com/TERM/V/vector_graphics.html).  
  
 **Bu konuda:**  
  
-   [Bir şekil çizme](#Shape)  
  
-   [Bir yol çizin](#Path)  
  
-   [Bir şekli bir yola Dönüştür](#Convert)  
  
-   [Yolları Birleştir](#Combine)  
  
-   [Bileşik yol Oluştur](#Compound)  
  
-   [Bir kırpma yolunu oluşturun](#Clipping)  
  
##  <a name="Shape"></a> Bir şekil çizme  
 Şekillerde bulabilirsiniz **varlıklar** paneli.  
  
 ![Şekil kategorisini varlıklar panelinde](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")  
  
 İstediğiniz herhangi bir şekil, çalışma yüzeyine sürükleyin. Ardından, ölçeklendirme, döndürmek, taşıyın veya şekil eğriltmek için şeklin üzerinde tutamaçlarını kullanabilirsiniz.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")  
  
##  <a name="Path"></a> Bir yol çizin  
 Bir dizi bağlantılı çizgiler ve eğrilerdir yoludur. Kullanılamayan, ilginç şekiller oluşturmak için bir yol kullanın **varlıklar** paneli.  
  
 Bir yolu, bir satır, Kalem ve kağıt kullanarak çizebilirsiniz. Bu araçlarda bulabilirsiniz **Araçları** paneli.  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")  
  
### <a name="draw-a-straight-line"></a>Düz çizgi çizme  
 Kullanım **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54"), veya **satırı** aracı ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf").  
  
 **Kalem aracıyla** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")  
  
 Çalışma yüzeyinde başlangıç noktasını tanımlamak için bir kez tıklayın ve satırın sonuna tanımlamak için yeniden tıklayın.  
  
 **Satırı aracını kullanarak** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")  
  
 Çalışma yüzeyinde satır başlatmak istediğiniz sürükleyin ve ardından çizginin sona ermesini istediğiniz noktada bırakın.  
  
### <a name="draw-a-curve"></a>Eğri çizme  
 Kullanım **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Çalışma yüzeyinde bir satırın başlangıç noktasını tanımlamak tıklayın ve istenen eğri oluşturmak için işaretçiyi sürükleyin için bir kez tıklayın.  
  
 Yolu kapatmak istiyorsanız ilk satırın noktasında tıklayın.  
  
### <a name="change-the-shape-of-a-curve"></a>Eğrinin şeklini değiştirme  
 Kullanım **doğrudan seçim** aracı ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Şekle tıklayın ve ardından eğri şekiller değiştirmek için şekli üzerinde herhangi bir noktaya sürükleyin.  
  
### <a name="draw-a-free-form-path"></a>Serbest form yolu çizme  
 Kullanım **kalem** aracı ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd").  
  
 Çalışma yüzeyinde, gerçek bir kalem kullanarak yaptığınız gibi serbest biçimli yolu çizin.  
  
### <a name="remove-part-of-a-path"></a>Yolun bir bölümünü kaldırın  
 Kullanım **doğrudan seçim** aracı ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Silin ve ardından istediğiniz kesimi içeren yolu seçin **Sil** düğmesi.  
  
### <a name="remove-a-point-in-a-path"></a>Bir yolda bir noktası Kaldır  
 Kullanım **seçimi** aracı ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")ve **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Kullanım **seçimi** aracı ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") yolunu seçin. Ardından, **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kaldırmak istediğiniz noktayı tıklatın.  
  
### <a name="add-a-point-to-a-path"></a>Bir nokta yolunu Ekle  
 Kullanım **seçimi** aracı ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")ve **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Kullanım **seçimi** aracı ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") yolunu seçin. Kullanım **kalem** aracı ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") noktası eklemek istediğiniz yola göre herhangi bir yeri tıklatın.  
  
##  <a name="Convert"></a> Bir şekli bir yola Dönüştür  
 Bir şekli bir yolu değiştirmek yollarla değiştirmek için şekli bir yola Dönüştür.  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [yolları ile çalışma: bir şekli bir yola dönüştürmek](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
##  <a name="Combine"></a> Yolları Birleştir  
 Tek bir yol, yol ve Şekil birleştirebilirsiniz.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-A338-4ef4-96c5-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1-1.png "B1_1")|Birleştirme öncesi iki şekil|![](../designers/media/b1-4.png "B1_4")|Kesiştir|  
|![](../designers/media/b1-2.png "B1_2")|Birleştir|![](../designers/media/b1-5.png "B1_5")|Örtüşmeyi Dışla|  
|![](../designers/media/b1-3.png "B1_3")|Bölme|![](../designers/media/b1-6.png "B1_6")|Çıkarma|  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [yolları ile çalışma: yolları Birleştir](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
##  <a name="Compound"></a> Bileşik yol Oluştur  
 Bileşik yol oluşturduğunuzda, yolların herhangi bir kesişen bölümleri sonuçtan çıkartılır ve sonuçlanan yol en alt yolun görsel özelliklerini kabul eder.  
  
 Bileşik yol oluşturduktan sonra istediğiniz zaman parçalara ayırabilirsiniz.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8DE5-b10d28f08a84")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [yolları ile çalışma: bileşik yol Oluştur](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
##  <a name="Clipping"></a> Bir kırpma yolunu oluşturun  
 Bir kırpma yolu, kırpma yolu dışına düşen maskelenmiş nesnenin kısımlarını saklayarak, diğer nesneye uygulanan bir yol veya şekildir.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")  
  
 **Kısa bir video izleyin:** ![yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [yolları ile çalışma: bir kırpma yolunu oluşturun](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



