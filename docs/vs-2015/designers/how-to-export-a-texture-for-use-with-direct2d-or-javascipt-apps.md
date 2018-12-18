---
title: 'Nasıl yapılır: Direct2D veya JavaScript uygulamaları kullanmak için doku dışa aktarma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2b08760e567f6e000e191703695ee0703da7215
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812146"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Nasıl yapılır: Direct2D veya Javascript Uygulamaları Kullanmak için Doku Dışa Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görüntü içeriği ardışık düzeni, Direct2D'in iç işleme kuralları ile uyumlu dokular oluşturabilir. Bu tür dokular Direct2D kullanan uygulamalar ve JavaScript kullanılarak oluşturulan Windows Store uygulamalarında kullanım için uygundur.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Görüntü içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.  
  
-   Direct2D veya JavaScript uygulamasında kullanabileceğiniz bir doku oluşturmak için görüntü içeriği ardışık yapılandırma.  
  
    -   Bir blok sıkıştırılmış bir .dds dosyası üretin.  
  
    -   Ön çarpımlı alfa oluşturmak.  
  
    -   Mipmap oluşturmayı devre dışı bırakın.  
  
## <a name="rendering-conventions-in-direct2d"></a>Direct2D içindeki işleme kuralları  
 Direct2D bağlamında kullanılan dokular bu Direct2D iç işleme kurallarına uymalıdır:  
  
-   Direct2D ön çarpımlı alfa kullanarak saydamlığı ve yarı saydamlığı uygular. Direct2D ile kullanılan dokular, doku geçirgenlik veya translucency kullanmıyor olsa bile, önceden çoğaltılmış alfa içermesi gerekir. Önceden çoğaltılmış alfa hakkında daha fazla bilgi için bkz. [nasıl yapılır: ön Çarpımlı alfa kullanan doku dışa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   Doku bu blok sıkıştırma biçimlerinden biri kullanılarak .dds biçiminde sağlanmalıdır:  
  
    -   BC1_UNORM sıkıştırma  
  
    -   BC2_UNORM sıkıştırma  
  
    -   BC3_UNORM sıkıştırma  
  
-   Mipmaplar desteklenmiyor.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Direct2D işleme kuralları ile uyumlu olan bir doku oluşturmak için  
  
1. Temel doku ile başlayın. Varolan bir resim yükleyin ya da açıklandığı gibi yeni bir tane oluşturun [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md). .Dds biçimde blok sıkıştırmayı desteklemek için genişliği ve yüksekliği olan boyutu, örneğin, 100 x 100, 128 x 128 veya 256 x 192 gibi dördün katları olan bir doku belirtin. Mipeşlem desteklenmediğinden dokunun kare olması gerekmez ve boyut olarak ikinin kuvveti olması gerekmez.  
  
2. Doku dosyasını yapılandırarak, böylece görüntü içeriği ardışık düzeni tarafından işlenir. İçinde **Çözüm Gezgini**, yeni oluşturduğunuz doku dosyası için kısayol menüsünü açın ve ardından **özellikleri**. Üzerinde **yapılandırma özellikleri**, **genel** sayfasında **öğesi türü** özelliğini **görüntü içeriği ardışık düzeni**. Emin olun **içerik** özelliği **Evet** ve **yapıdan hariç tut** ayarlanır **Hayır**ve ardından  **Uygulama** düğmesi. **Görüntü içeriği ardışık düzeni** yapılandırma özellik sayfası görüntülenir.  
  
3. Çıktı biçimini blok sıkıştırılmış biçimlerden birine ayarlayın. Üzerinde **yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında **sıkıştırma** özelliğini  **BC3_UNORM sıkıştırma (/ compress: BC3_UNORM)**. Diğer BC1, BC2 veya BC3 biçimleri, gereksinimlerinize bağlı olarak seçebilirsiniz. Direct2D şu anda BC4, BC5, BC6 veya bc7 dokularını desteklemiyor. Farklı BC biçimleri hakkında daha fazla bilgi için bkz. [bloğunu sıkıştırma (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
   > [!NOTE]
   >  Belirtilen sıkıştırma biçimi, görüntü içeriği ardışık düzeni tarafından üretilen dosyanın biçimini belirler. Bu farklıdır **biçimi** görüntü kaynak görüntü dosyasının biçimini diskte depolanan gibi belirleyen Düzenleyicisi'nde kaynak görüntü özelliği — diğer bir deyişle, *çalışma biçimi*. Genellikle, sıkıştırılmış bir çalışma biçimi istemezsiniz.  
  
4. Ön çarpımlı alfa kullanan çıktı oluşturmak için görüntü içeriği ardışık yapılandırın. Üzerinde **yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında **ön çarpımlı alfa biçimine Dönüştür** özelliğini **Evet (/ generatepremultipliedalpha)**.  
  
5. Mipmaps oluşturmak değil, görüntü içeriği ardışık düzeni yapılandırın. Üzerinde **yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında **Mips üret** özelliğini**Hayır**.  
  
6. Seçin **Tamam** düğmesi.  
  
   Proje oluşturduğunuzda, görüntü içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden sizin belirttiğiniz çıkış biçimine dönüştürür — dönüştürme ön çarpımlı alfa oluşturulmasını içerir — ve sonuç projenin çıkış dizinine kopyalanır.



