---
title: 'Nasıl yapılır: MIP Düzeyleri Oluşturma ve Değiştirme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bdda75e5c8796ccd6e0b1d86b717dbd9bc48926
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924453"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme
Bu belgenin nasıl kullanılacağını gösteren **Resim Düzenleyicisi** oluşturmak ve değiştirmek amacıyla *MIP düzeyleri* doku alanı düzeyi ayrıntı düzeyi (LoD) için.

## <a name="generating-mip-levels"></a>MIP düzeyleri oluşturma
 *Mipeşlem* işleme hızını arttırmak ve dokulu nesnelerdeki yumuşatma yapıtları önceden hesaplama ve farklı boyutlardaki bir dokunun çeşitli kopyalarını depolayarak azaltmak için kullanılan bir tekniktir. MIP düzeyi olarak bilinen her kopya yarım genişlik ve yükseklik önceki kopyanın ' dir. Doku bir nesnenin yüzeyine işlenirken dokulanan yüzeyin ekran alanı bölgesine en yakın karşılık gelen MIP seviyesi otomatik olarak seçilir. Bu grafik donanımının tutarlı görsel kaliteyi korumak için aşırı boyutlu dokuları filtrelemek zorunda olmadığı anlamına gelir. MIP düzeylerini saklamanın bellek maliyetinin yaklaşık % 33 daha fazla tek başına orijinal dokununkinden olsa da, performans ve görüntü kalitesi kazançları onu haklı çıkarır.

#### <a name="to-generate-mip-levels"></a>MIP düzeyleri oluşturmak için

1.  Bölümünde anlatıldığı gibi temel bir doku ile başlayan [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). En iyi sonuçlar için genişliği ve yüksekliği, örneğin 256, 512, 1024, boyut olarak ikinin kuvveti olan bir doku belirtin ve benzeri.

2.  MIP düzeylerini oluşturun. Üzerinde **resim düzenleyici modu** araç seçin **Gelişmiş** > **Araçları** > **Mips üret**.

     Dikkat **sonraki MIP düzeyine Git** ve **önceki MIP düzeyine Git** düğmeler artık görünür **resim düzenleyici modu** araç çubuğu. Varsa **özellikleri** penceresi görüntüleniyorsa, ayrıca dikkat salt okunur özellikler **MIP düzeyini** ve **Mip düzeyi sayısı** artık görüntü özelliklerinde göründüğüne.

## <a name="modifying-mip-levels"></a>MIP düzeylerini değiştirme
 Özel efektler elde etmek veya belirli ayrıntı düzeylerinde resim kalitesini artırmak için her MIP düzeyini tek tek değiştirebilirsiniz. Örneğin, dokulu bir nesneye (daha büyük Mesafeler daha küçük MIP düzeylerine karşılık gelir) uzaklıkta farklı bir görünüm verebilirsiniz ya da metin ya da sembol içeren Dokuların daha küçük MIP seviyelerinde bile okunaklı kalmasını sağlayabilirsiniz.

#### <a name="to-modify-an-individual-mip-level"></a>Bir tek tek MIP düzeyini değiştirmek için

1.  Değiştirmek istediğiniz MIP düzeyini seçin. Üzerinde **resim düzenleyici modu** araç kullanımı **sonraki MIP düzeyine Git** ve **önceki MIP düzeyine Git** düğmeleri MIP düzeyleri arasında hareket etmek.

2.  Değiştirmek istediğiniz MIP düzeyini seçtikten sonra diğer MIP düzeylerinin içeriğini değiştirmeden değiştirmek için çizim araçlarını kullanabilirsiniz. Çizim Araçları mevcuttur **Resim Düzenleyicisi** araç çubuğu. Bir aracı seçtikten sonra özelliklerini değiştirebilirsiniz **özellikleri** penceresi. Çizim araçları ve özellikleri hakkında daha fazla bilgi için bkz. [Resim Düzenleyicisi](../designers/image-editor.md).

> [!NOTE]
>  Bireysel MIP seviyelerindeki içeriği değiştirmek gerekmez, — bazı efektler elde etmek için yapabileceğiniz gibi — derleme zamanında kaynak dokudan Mipmap üretmek öneririz. Bu, MIP düzeyinde yapılan değişiklikler diğer düzeylere otomatik olarak yayılmadığından dolayı MIP düzeylerinin kaynak doku ile eşit kalmasını sağlamaya yardımcı olur. Derleme zamanında Mipmap konusunda daha fazla bilgi için bkz. [nasıl yapılır: mipmap'leri içeren dokuyu dışa aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)