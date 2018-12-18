---
title: 'Nasıl yapılır: Direct2D veya Javascript Uygulamaları Kullanmak için Doku Dışa Aktarma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c748e8b380da906ca9fb8fc8588efa6ffcc44980
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826390"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Nasıl yapılır: Direct2D veya JavaScript uygulamaları ile kullanmak için doku dışa aktarma

Görüntü içeriği ardışık düzeni, Direct2D'in iç işleme kuralları ile uyumlu dokular oluşturabilir. Bu tür dokular Direct2D kullanan uygulamalar ve JavaScript kullanılarak oluşturulan UWP uygulamalarında kullanım için uygundur.

Bu belgede şu faaliyetler gösterilmiştir:

-   Görüntü içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

-   Direct2D veya JavaScript uygulamasında kullanabileceğiniz bir doku oluşturmak için görüntü içeriği ardışık yapılandırma.

    -   Bir blok sıkıştırılmış oluşturmak *.dds* dosya.

    -   Ön çarpımlı alfa oluşturmak.

    -   Mipmap oluşturmayı devre dışı bırakın.

## <a name="rendering-conventions-in-direct2d"></a>Direct2D içindeki işleme kuralları

Direct2D bağlamında kullanılan dokular bu Direct2D iç işleme kurallarına uymalıdır:

-   Direct2D ön çarpımlı alfa kullanarak saydamlığı ve yarı saydamlığı uygular. Direct2D ile kullanılan dokular, doku geçirgenlik veya translucency kullanmıyor olsa bile, önceden çoğaltılmış alfa içermesi gerekir. Önceden çoğaltılmış alfa hakkında daha fazla bilgi için bkz. [nasıl yapılır: ön Çarpımlı alfa kullanan doku dışa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

-   Doku sağlanması gereken *.dds* bu blok sıkıştırma biçimlerinden birini kullanarak biçimi:

    -   BC1_UNORM sıkıştırma

    -   BC2_UNORM sıkıştırma

    -   BC3_UNORM sıkıştırma

-   Mipmaplar desteklenmiyor.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Direct2D işleme kuralları ile uyumlu olan bir doku oluşturmak için

1. Temel doku ile başlayın. Varolan bir resim yükleyin ya da açıklandığı gibi yeni bir tane oluşturun [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). İçinde blok sıkıştırmayı desteklemek için *.dds* biçimlendirmek, genişlik ve yükseklik olan boyutu, örneğin, 100 x 100, 128 x 128 veya 256 x 192 gibi dördün katları olan bir doku belirtin. Mipeşlem desteklenmediğinden dokunun kare olması gerekmez ve boyut olarak ikinin kuvveti olması gerekmez.

2. Doku dosyasını yapılandırarak, böylece görüntü içeriği ardışık düzeni tarafından işlenir. İçinde **Çözüm Gezgini**, yeni oluşturduğunuz doku dosyası için kısayol menüsünü açın ve ardından **özellikleri**. Üzerinde **yapılandırma özellikleri** > **genel** sayfasında **öğesi türü** özelliğini **görüntü içeriği ardışık düzeni**. Emin olun **içerik** özelliği **Evet** ve **yapıdan hariç tut** ayarlanır **Hayır**ve ardından  **Uygulama** düğmesi. **Görüntü içeriği ardışık düzeni** yapılandırma özellik sayfası görüntülenir.

3. Çıktı biçimini blok sıkıştırılmış biçimlerden birine ayarlayın. Üzerinde **yapılandırma özellikleri** > **görüntü içeriği ardışık düzeni** > **genel** sayfasında **sıkıştırma**özelliğini **BC3_UNORM sıkıştırma (/ compress: BC3_UNORM)**. Diğer BC1, BC2 veya BC3 biçimleri, gereksinimlerinize bağlı olarak seçebilirsiniz. Direct2D şu anda BC4, BC5, BC6 veya bc7 dokularını desteklemiyor. Farklı BC biçimleri hakkında daha fazla bilgi için bkz. [Block sıkıştırma (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Belirtilen sıkıştırma biçimi, görüntü içeriği ardışık düzeni tarafından üretilen dosyanın biçimini belirler. Bu farklıdır **biçimi** görüntü kaynak görüntü dosyasının biçimini diskte depolanan gibi belirleyen Düzenleyicisi'nde kaynak görüntü özelliği — diğer bir deyişle, *çalışma biçimi*. Genellikle, sıkıştırılmış bir çalışma biçimi istemezsiniz.

4. Ön çarpımlı alfa kullanan çıktı oluşturmak için görüntü içeriği ardışık yapılandırın. Üzerinde **yapılandırma özellikleri** > **görüntü içeriği ardışık düzeni** > **genel** sayfasında **Dönüştür Ön çarpımlı alfa biçimine** özelliğini **Evet (/ generatepremultipliedalpha)**.

5. Mipmaps oluşturmak değil, görüntü içeriği ardışık düzeni yapılandırın. Üzerinde **yapılandırma özellikleri** > **görüntü içeriği ardışık düzeni** > **genel** sayfasında **Mipsüret** özelliğini **Hayır**.

6. Seçin **Tamam** düğmesi.

   Proje oluşturduğunuzda, görüntü içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden sizin belirttiğiniz çıkış biçimine dönüştürür — dönüştürme ön çarpımlı alfa oluşturulmasını içerir — ve sonuç projenin çıkış dizinine kopyalanır.