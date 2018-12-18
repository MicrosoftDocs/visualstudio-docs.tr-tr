---
title: Gölgelendirici Tasarımcısı düğümleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f41d1d3d934ecd85ac36d24d704db561d42faa97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293507"
---
# <a name="shader-designer-nodes"></a>Gölgelendirici Tasarımcısı Düğümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belgelerin bu bölümdeki makaleleri grafik efektleri oluşturmak için kullanabileceğiniz çeşitli gölgelendirici Tasarımcısı düğümleri hakkında bilgiler içerir.  
  
## <a name="nodes-and-node-types"></a>Düğüm ve düğüm türleri  
 Gölgelendirici Tasarımcısı görsel efekt grafik olarak temsil eder. Bu grafikler, özellikle seçilen ve istenen etkiler elde etmek için kesin şekilde bağlı düğümlerden oluşturulur. Her düğüme bir bilgi parçasıdır veya bir matematiksel işlev ve aralarındaki bağlantıları bilgileri sonucu üretmek için graph üzerinden nasıl aktığını temsil eder. Gölgelendirici Tasarımcısı altı farklı bir düğüme türlerinin sağlar — filtreleri, doku düğümleri, parametreleri, sabitleri, yardımcı program düğümleri ve matematik düğümleri — ve birkaç tek tek düğümleri her türe ait. Bu düğüm ve düğüm türleri diğer makalelerden Bu bölümde açıklanan — bu belgenin sonundaki bağlantılara bakın.  
  
## <a name="node-structure"></a>Düğüm yapısı  
 Tüm düğümleri ortak öğeler bileşiminden oluşur. Her düğüm (dışında son rengini düğümü gölgelendirici çıktısını gösterir), sağ taraftaki en az bir çıkış terminal sahiptir. Hesaplamaları veya doku örnekleyici temsil eden düğümler terminaller, sol tarafında giriş, ancak hiçbir giriş terminaller bilgileri temsil eden düğümler var. Bir düğümden diğerine bilgi taşımak için terminaller giriş çıkış terminaller bağlıdır.  
  
### <a name="promotion-of-inputs"></a>Giriş yükseltme  
 Etkili bir oyunun veya uygulamanın içinde kullanılabilir, böylece gölgelendirici Tasarımcısı sonuçta HLSL kaynak kodu oluşturmanız gerekir, gölgelendirici Tasarımcısı düğümleri HLSL kullandığı türü promosyon kurallarını tabi olduğu. Grafik donanımının öncelikle kayan nokta değerleri üzerinde çalıştığından, farklı türler arasında yükseltme yazın — örneğin, `int` için `float`, veya `float` için `double`— seyrek olur. Bunun yerine, grafik donanımının bilgileri aynı anda birden çok parça aynı işlemi kullandığından, farklı türde bir yükseltme, daha kısa bir dizi girişleri boyutunu en uzun giriş uyacak şekilde uzatılmış oluşabilir. Giriş türü üzerinde ve üzerinde işlem nasıl uzatılmış bağlıdır:  
  
-   **Küçük tür bir skaler değer ise:**  
  
     Skaler değerini, daha büyük giriş boyutu eşit olan bir vektörü olarak çoğaltılır. Örneğin, skaler giriş 5.0 (5.0, 5.0, 5.0) vektör haline gelir işlemi ne olursa olsun, bir üç öğeli vektör olduğunda işlemin en büyük giriş.  
  
-   **Daha küçük bir vektör türüdür ve çarpma işlemi (\*, /, % vb.), ardından:**  
  
     Vektör değeri önde gelen büyük giriş boyutu eşit olan bir vektör öğelerinin kopyalanır ve sondaki öğeler 1.0 için ayarlanır. Örneğin, vektör giriş (5.0, 5.0) (5.0, 5.0, 1.0, 1.0) vektör haline gelir, bu çarpılır dört öğeli vektörü ile. Bu üçüncü ve dördüncü öğeleri çıkış çarpma kimliği, 1.0 kullanarak korur.  
  
-   **Daha küçük bir vektör türüdür ve işlem eklenebilir (+,-, vb.), ardından:**  
  
     Vektör değeri önde gelen büyük giriş boyutu eşit olan bir vektör öğelerinin kopyalanır ve sondaki öğeler 0.0 ayarlanır. Örneğin, vektör giriş (5.0, 5.0) (5.0, 5.0, 0.0, 0.0) vektör haline gelir, eklendiğinde için dört öğeli vektör. Bu, çıktının üçüncü ve dördüncü öğeleri 0,0 eklenebilir kimlik kullanarak korur.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Sabit Düğümler](../designers/constant-nodes.md)|Değişmez değerler ve gölgelendirici hesaplamalarında ilişkilendirilmiş köşe durumu bilgileri temsil etmek için kullanabileceğiniz düğümleri açıklar. Köşe durumu ilişkilendirilmiş olduğundan — ve bu nedenle, her bir pikseli farklıdır — sabiti farklı bir sürümünü her piksel gölgelendiricisi örneği alır.|  
|[Parametre Düğümleri](../designers/parameter-nodes.md)|Kamera konumu, malzeme özelliklerine, aydınlatma parametreleri, zaman ve diğer uygulama durumu bilgileri gölgelendirici hesaplamalarında temsil etmek için kullanabileceğiniz düğümleri açıklar.|  
|[Doku Düğümleri](../designers/texture-nodes.md)|Çeşitli doku türleri ve geometri, örnek ve oluşturmak veya doku koordinatları yaygın şekilde dönüştürmek için kullanabileceğiniz düğümleri açıklar.|  
|[Matematik Düğümleri](../designers/math-nodes.md)|Cebirsel gerçekleştirmek için kullanabileceğiniz düğümleri, trigonometrik, mantıksal ve doğrudan HLSL yönergeleri için harita diğer matematiksel işlemler açıklanmaktadır.|  
|[Yardımcı Program Düğümleri](../designers/utility-nodes.md)|Genel aydınlatma hesaplama ve doğrudan HLSL yönergeleri eşlemeyin diğer yaygın işlemler gerçekleştirmek için kullanabileceğiniz düğümleri açıklar.|  
|[Filtre Düğümleri](../designers/filter-nodes.md)|Doku filtreleme ve renk filtreleme yapmak için kullanabileceğiniz düğümleri açıklar.|



