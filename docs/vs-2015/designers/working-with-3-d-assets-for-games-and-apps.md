---
title: Oyunlar ve uygulamalar için 3B varlıklarla çalışma | Microsoft Docs
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
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bdf19958ec7b3cfe72ee00ea84e0e23724a51458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265245"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oluşturmak veya 3B modeller, dokuları ve gölgelendiricileri DirectX tabanlı oyunlar ve uygulamalar için değiştirmek için kullanabileceğiniz araçlar.  
  
## <a name="directx-app-development-in-visual-studio"></a>Visual Studio'da DirectX uygulaması geliştirme  
 DirectX uygulaması, programlama mantığı, DirectX API ve üst düzey gölgelendirme dili (HLSL) programları, zengin, etkileşimli bir multimedya deneyimi sunmak için ses ve 3B görsel varlıklar genellikle birleştirir.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başka bir aracı kullanmak için IDE'den çıkmadan görüntü ve dokuları, 3B modeller ve gölgelendiriciler ile çalışmak için kullanabileceğiniz araçlar içerir. Visual Studio Araçları, özellikle oluşturmak için uygun *yer tutucu* kodu test veya üretime hazır varlıkları komisyon önce ve inceleme ve üretime hazır değiştirmeye yönelik prototipleri oluşturmak için kullanabileceğiniz, varlıkları Uygulamanızı hata ayıklama işlemi yaparken varlıklar.  
  
 İle çalışmak varlıkların türleri hakkında daha fazla bilgi aşağıdadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="images-and-textures"></a>Görüntü ve dokuları  
 Görüntü ve dokuları rengi ve oyunlar ve uygulamalar, görsel ayrıntıları sağlayın. 3B grafikler, çeşitli biçimlerde, türleri ve geometriler farklı kullanımlarını desteklemek için doku gelir. Örneğin, normal haritalar için daha ayrıntılı aydınlatma, 3B modeller piksel başına yüzey normal değerler sağlayın ve küp eşlemlerinin sky kutulama, yansıma ve küresel doku eşleme gibi kullanımlar için her yöne doku sağlayın. Doku, farklı ayrıntı düzeyleri en verimli işleme desteklemek için mip eşlemeleri sağlayabilir ve farklı renk kanalı ve renk sıralamalarının destekleyebilir. Dokular grafik az ayrılmış bellek kaplar ve gpu erişimi dokular daha verimli bir şekilde yardımcı sıkıştırma biçimlerinin çeşitli içinde depolanabilir.  
  
 Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görüntü ve dokuları birçok ortak türlerini ve biçimlerini çalışmak için görüntü Düzenleyicisi.  
  
### <a name="3-d-models"></a>3B modeller  
 3B modeller, boşluk ve Şekil oyunlar ve uygulamalar oluşturun. En düşük düzeyde, 3B noktaları konumunu modelleri kodlama — olarak bilinen *köşeler*— çizgiler veya üçgenler model şeklini temsil eden tanımlamak için verileri dizinleme birlikte. Ek veriler bu köşelerde ile ilişkili olabilir — örneğin, renk bilgilerini, normal vektörleri veya uygulamaya özel öznitelikler. Her model nesnesi genelinde öznitelikleri de tanımlayabilirsiniz — Örneğin, hangi gölgelendirici nesnenin yüzeyi veya hangi doku uygulandığı görünümünü hesaplamak için kullanılır.  
  
 Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3-b ile çalışmak için Model Düzenleyicisi ortak çeşitli biçimlerde modeller.  
  
### <a name="shaders"></a>Gölgelendiricileri  
 Gölgelendiricileri grafik işlemci birimi (GPU) üzerinde çalışan küçük, etki alanına özgü programlardır. Gölgelendiricileri belirlemek nasıl 3B modeller içine ekrandaki dönüştürülür şekiller ve bu şekiller her pikselin nasıl renklendirilmiştir. Gölgelendirici oluşturma ve nesneyi oyunlarda veya uygulamalarda uygulama nesnesi benzersiz bir görünüm verebilirsiniz.  
  
 Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gölgelendirici tasarım gölgelendirici grafik tabanlı bir araçtır, HLSL programlama bilmeden özel görsel efektler oluşturmak için Tasarımcısı.  
  
> [!NOTE]
>  DirectX programlama ile başlama hakkında daha fazla bilgi için bkz. [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). DirectX tabanlı bir uygulamanın hatalarını ayıklama hakkında daha fazla bilgi için bkz. [grafik tanılama (DirectX grafik hata ayıklama)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DirectX, 2B ve 3B varlıkları işlemek için kullanır. DirectX 11 Oluşturucu ya da Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) yazılım oluşturucusu seçebilirsiniz. DirectX 11 Oluşturucu, DirectX 11 ve DirectX 10 GPU üzerinde yüksek performanslı, Donanım hızlandırmalı işleme sağlar. WARP Oluşturucu varlıklarınızı çok çeşitli bilgisayarlar çalışma emin olmaya yardımcı olur; bu modern grafik donanımının sahip olmayan bilgisayarlar ve grafik donanımının tümleşik bilgisayarları içerir. WARP hakkında daha fazla bilgi için bkz: [Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) Kılavuzu](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Dokularla ve Görüntülerle Çalışma](../designers/working-with-textures-and-images.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokular ve görüntüler ile çalışmak için.|  
|[3B Modelleriyle Çalışma](../designers/working-with-3-d-models.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3B modellerle çalışmak için.|  
|[Gölgelendiricilerle Çalışma](../designers/working-with-shaders.md)|Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oluşturmak ve özel gölgelendirici efektleri değiştirmek için gölgelendirici Tasarımcısı.|  
|[Oyunlarda veya Uygulamalarda 3B Varlıklar Kullanma](../designers/using-3-d-assets-in-your-game-or-app.md)|Oyunlarda veya uygulamalarda görüntü Düzenleyicisi, Model düzenleyiciyi veya gölgelendirici Tasarımcısı kullanarak oluşturduğunuz varlıkları kullanmayı açıklar.|



