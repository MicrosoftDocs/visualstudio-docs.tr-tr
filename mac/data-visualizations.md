---
title: Hata ayıklama - veri görselleştirmeleri
description: Hata ayıklama, programlama, ortak ve gerekli bir parçasıdır. Mac için Visual Studio kolay hata ayıklama yapmak için özellikleri içeren tam bir paketi içerir. Bu makalede, hata ayıklayıcı'daki nesneleri inceleyerek görüntülenebilir farklı veri görselleştirmeleri bakar.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 896fa055c536f9f3ee693773ad4f4ae0edd7e7fe
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349445"
---
# <a name="data-visualizations"></a>Veri görselleştirmeleri

Mac için Visual Studio kullanıcı Arabirimi hata ayıklama sırasında görselleştirmelerin bir değişken, alan veya özellik değerlerini sağlayan, hata ayıklayıcı desteği içerir. Bu veri görselleştiriciler veri genişletilmiş bir sürümünü gösterir ve örneğin bir renk yapı rengini gösteren bilinen yapıları, geliştiricilerin sağlar.

Hata ayıklama, görselleştiriciler **yerel** doldurma değeri sağında kullanıcı satırın geldiğinde görüntülenen Önizleme simgesine tıklayarak görüntülenebilir:

![Yerel paneli](media/data-visualizations-image9.png)

Mac için Visual Studio'da hata ayıklama sırasında aşağıdaki listede kullanılabilir yeni görselleştirmeler birçoğu arar

## <a name="point"></a>Noktası
Bir nokta/noktayı gösteren PointF veya CGPoint iOS ve Mac, hata ayıklama panelinde X ve Y değerleri gösteren bir tanımlama grubu şu şekilde işlenir:

![Noktası Görselleştirme](media/data-visualizations-image10.png)

## <a name="size"></a>Boyut
Bir boyut/SizeF veya CGSize iOS ve Mac bir dikdörtgen işlenir. Çizildiğinde bir boyut 250 büyüdükçe kadar ölçeklendirme piksel, bu noktada, ayarlayacaktır dikdörtgen en büyük boyut 250 piksel:

[Görselleştirme boyutu](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Dikdörtgen
Bir dikdörtgen/RectangleF veya CGRect iOS ve Mac, boyutları ve özgün görüntüler. Benzer şekilde boyutu, çizildiğinde bir boyut 250 büyüdükçe kadar ölçeklendirme px:

![Dikdörtgen Görselleştirme](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinatı
Koordinatları merkezine sabitlenmiş konumunu bir haritada çizilir:

[Koordinat Görselleştirme](media/data-visualizations-image13.png)

## <a name="color"></a>Renk
Bu renk Önizleme, RGBA bileşenleri, Hue doygunluğu açıklık değerleri ve rengini onaltılık değerini gösteren UIColor CGColor ve renk özellikleri görüntüler:

![Renk Görselleştirme](media/data-visualizations-image14.png)

## <a name="images"></a>Görüntüler

Medya en fazla 250 olan bir maksimum boyut için ölçeklendirme işlenecek, piksel ve görüntü 250 aştığında uyacak şekilde ayarlanacaktır piksel:

![Görüntü Görselleştirme](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bezier eğrileri

Görselleştiriciyi görüntüleyecek bir `NSBezierPath`:

![Bezier eğrisi Görselleştirme](media/data-visualizations-image16.png)

## <a name="string"></a>Dize

100'den az karakter dizesi, bir önizleme olmadan tam görüntülenir. Uzun dizeler tam önizleme olarak görüntülenir. Dizeleri düzenlenebilir ve görselleştiricisi Önizleme veya dize değeri aşağıda gösterilen Düzenleyicisi'nde düzenlenmesi dize değeri sağlayan bir düzenleme düğmesi eşlik:

![Dize Görselleştirme](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Küçük dizeleri:
![Küçük dize Görselleştirme](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Orta uzunluklu dizeler:
![Orta dize Görselleştirme](media/data-visualizations-image19.png)

### <a name="editor"></a>Düzenleyen:

![Düzenleyici Görselleştirme](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable tüm değerleri sıralar; değerlerin her birinin tıklayarak görüntülenebilir **Göster** değerleri düğmesi. IEnumerable seçeneği gibi nesnelerin değerlerini görüntülemez `Array`, `ArrayList`, `List<>`, `Dictionary<,>` bunlar kendi hata ayıklama görselleştiricileri sahip.

![IEnumerable Görselleştirme](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Diğer Görselleştiriciler

Kendi satır içi görselleştiriciler de bazı diğer türleri aşağıda listelenmiştir:

![Diğer Görselleştirme](media/data-visualizations-image23.png)

*   **Temel Türler**
    *   Bu basit türü ham değeri gösterir.
*   **Sabit listesi**
    *   Bu numaralama türü niteleyici olmayan alan değeri görüntüler.
*   **Tanımlama grubu**
    *   (,) Biçiminde görüntülenir
*   **Null**
    *   "Null" değerini gösterir.
*   **URL**
    *   Bu tıklanabilir köprü görüntüler.
*   **IntPtr**
    *   Bu IntPtr bir sayının onaltılık gösterimini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenleri Otolar ve yerel öğeler pencerelerinde (Windows için Visual Studio) denetleyin](/visualstudio/debugger/autos-and-locals-windows)
- [(Windows için Visual Studio) görselleştiricide dizelerini görüntüle](/visualstudio/debugger/string-visualizer-dialog-box)