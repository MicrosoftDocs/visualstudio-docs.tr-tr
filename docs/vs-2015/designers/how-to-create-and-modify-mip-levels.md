---
title: 'Nasıl yapılır: MIP düzeyleri oluşturma ve değiştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9578fd2bdafeaf8c9a3e9fcd3dd5523b4d8cc7f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184294"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Nasıl yapılır: MIP Düzeyleri Oluşturma ve Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgenin nasıl kullanılacağını gösteren **Resim Düzenleyicisi** oluşturmak ve değiştirmek amacıyla *MIP düzeyleri* doku alanı düzeyi ayrıntı düzeyi (LoD) için.  
  
## <a name="generating-mip-levels"></a>MIP düzeyleri oluşturma  
 *Mipeşlem* işleme hızını arttırmak ve dokulu nesnelerdeki yumuşatma yapıtları önceden hesaplama ve farklı boyutlardaki bir dokunun çeşitli kopyalarını depolayarak azaltmak için kullanılan bir tekniktir. MIP düzeyi olarak bilinen her kopya yarım genişlik ve yükseklik önceki kopyanın ' dir. Doku bir nesnenin yüzeyine işlenirken dokulanan yüzeyin ekran alanı bölgesine en yakın karşılık gelen MIP seviyesi otomatik olarak seçilir. Bu grafik donanımının tutarlı görsel kaliteyi korumak için aşırı boyutlu dokuları filtrelemek zorunda olmadığı anlamına gelir. MIP düzeylerini saklamanın bellek maliyetinin yaklaşık % 33 daha fazla tek başına orijinal dokununkinden olsa da, performans ve görüntü kalitesi kazançları onu haklı çıkarır.  
  
#### <a name="to-generate-mip-levels"></a>MIP düzeyleri oluşturmak için  
  
1.  Bölümünde anlatıldığı gibi temel bir doku ile başlayan [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). En iyi sonuçlar için genişliği ve yüksekliği, örneğin 256, 512, 1024, boyut olarak ikinin kuvveti olan bir doku belirtin ve benzeri.  
  
2.  MIP düzeylerini oluşturun. Üzerinde **resim düzenleyici modu** araç seçin **Gelişmiş**, **Araçları**, **Mips üret**.  
  
     Dikkat **sonraki MIP düzeyine Git** ve **önceki MIP düzeyine Git** düğmeler artık görünür **resim düzenleyici modu** araç çubuğu. Varsa **özellikleri** penceresi görüntüleniyorsa, ayrıca dikkat salt okunur özellikler **MIP düzeyini** ve **Mip düzeyi sayısı** artık görüntü özelliklerinde göründüğüne.  
  
## <a name="modifying-mip-levels"></a>MIP düzeylerini değiştirme  
 Özel efektler elde etmek veya belirli ayrıntı düzeylerinde resim kalitesini artırmak için her MIP düzeyini tek tek değiştirebilirsiniz. Örneğin, dokulu bir nesneye (daha büyük Mesafeler daha küçük MIP düzeylerine karşılık gelir) uzaklıkta farklı bir görünüm verebilirsiniz ya da metin ya da sembol içeren Dokuların daha küçük MIP seviyelerinde bile okunaklı kalmasını sağlayabilirsiniz.  
  
#### <a name="to-modify-an-individual-mip-level"></a>Bir tek tek MIP düzeyini değiştirmek için  
  
1.  Değiştirmek istediğiniz MIP düzeyini seçin. Üzerinde **resim düzenleyici modu** araç kullanımı **sonraki MIP düzeyine Git** ve **önceki MIP düzeyine Git** düğmeleri MIP düzeyleri arasında hareket etmek.  
  
2.  Değiştirmek istediğiniz MIP düzeyini seçtikten sonra diğer MIP düzeylerinin içeriğini değiştirmeden değiştirmek için çizim araçlarını kullanabilirsiniz. Çizim Araçları mevcuttur **Resim Düzenleyicisi** araç çubuğu. Bir aracı seçtikten sonra özelliklerini değiştirebilirsiniz **özellikleri** penceresi. Çizim araçları ve özellikleri hakkında daha fazla bilgi için bkz. [Resim Düzenleyicisi](../designers/image-editor.md).  
  
> [!NOTE]
>  Bireysel MIP seviyelerindeki içeriği değiştirmek gerekmez, — bazı efektler elde etmek için yapabileceğiniz gibi — derleme zamanında kaynak dokudan Mipmap üretmek öneririz. Bu, MIP düzeyinde yapılan değişiklikler diğer düzeylere otomatik olarak yayılmadığından dolayı MIP düzeylerinin kaynak doku ile eşit kalmasını sağlamaya yardımcı olur. Derleme zamanında Mipmap konusunda daha fazla bilgi için bkz. [nasıl yapılır: bir dokuyu dışarı aktarmak, içeren Mipmap'leri](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Temel Doku Oluşturma](../designers/how-to-create-a-basic-texture.md)



