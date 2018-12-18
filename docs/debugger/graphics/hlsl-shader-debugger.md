---
title: HLSL gölgelendirici hata ayıklayıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27db26a732ec53b81aed4807f4aec546e1bc7f1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825731"
---
# <a name="hlsl-shader-debugger"></a>HLSL Gölgelendirici Hata Ayıklayıcısı
Visual Studio grafik Çözümleyicisi, HLSL hata ayıklayıcısı, HLSL gölgelendirici kodunun uygulamanızın gerçek koşullar altında nasıl çalıştığını anlamanıza yardımcı olur.  
  
 HLSL hata ayıklayıcısı şudur:  
  
 ![HLSL hata ayıklama kullanarak izleyin ve çağrı yığını windows. ](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>HLSL hata ayıklayıcısını anlama  
 HLSL hata ayıklayıcısı, gölgelendirici kodunuzda ortaya çıkan sorunları anlamanıza yardımcı olur. HLSL kodunda hata ayıklama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diğer dillerde yazılmış kodlarda hata ayıklamaya benzer — Örneğin, C++, C# veya Visual Basic. Aynı diğer dillere hata ayıklaması yaparken olduğu gibi, değişkenlerin içeriğini inceleyebilir, kesim noktaları ayarlayabilir, kodda adım adım ilerleyebilir ve çağrı yığınına yaklaşabilirsiniz.  
  
 Gpu'lar yüzlerce iş parçacığı üzerinde eşzamanlı olarak gölgelendirici kod çalıştırarak yüksek performans elde etmek için ancak HLSL hata ayıklayıcısı tüm bu bilgileri anlamlı yardımcı olacak şekilde sunmak için diğer grafik Çözümleyicisi araçları ile birlikte çalışacak şekilde tasarlanmıştır . Grafik Çözümleyicisi, bir grafik günlüğüne kaydedilmiş bilgileri kullanarak yakalanan kareleri yeniden oluşturur; HLSL hata ayıklayıcısı, gölgelendirici kod çalıştırması gibi GPU yürütmesini gerçek zamanlı olarak izlemez. Graf günlüğü çıktının herhangi bir bölümünü yeniden oluşturmak için yeterli bilgi içerdiğinden ve grafik analizi sağladığından tam piksel ve bir hatanın oluştuğu yerde olay yardımcı olabilecek Araçlar saptamak için HLSL hata ayıklayıcısı yalnızca tam gölgelendirici benzetimini yapması gerekir İlgilendiğiniz iş parçacığı. Başka bir deyişle, gölgelendiricinin çalışması, iç çalışmalarının tam görünümde olduğu CPU üzerinde benzetilebilir. Bu da, HLSL hata ayıklayıcısına CPU benzeri bir hata ayıklama deneyimi kazandırır.  
  
 Ancak, HLSL hata ayıklayıcısı şu an için aşağıdaki bakımlardan sınırlıdır:  
  
- HLSL hata ayıklayıcısı Düzenle ve devam et modunu desteklemez, ancak için gölgelendirici değişiklikleri yapın ve ardından sonuçları görmek için bir çerçeve yeniden oluşturun.  
  
- Bir uygulamanın ve gölgelendirici kodunun hatalarını aynı anda ayıklamak mümkün değildir. Ancak, bunlar arasında geçiş yapabilirsiniz.  
  
- İzle penceresine değişkenler ve kayıtlar ekleyebilirsiniz, ancak ifadeler desteklenmez.  
  
  Yine de, HLSL hata ayıklayıcısı başka bir yöntemle sağlanabilecek olandan daha iyi ve daha CPU benzeri bir hata ayıklama deneyimi sağlar.  
  
## <a name="hlsl-shader-edit--apply"></a>HLSL gölgelendirici Düzenle ve Uygula  
 HLSL gölgelendirici hata ayıklayıcısı Düzenle ve devam et CPU hata ayıklayıcı alınmasına izin durumu gölgelendirici GPU yürütme modeli sağlamasına izin yapan aynı şekilde desteklemiyor. Bunun yerine, HLSL hata ayıklayıcısı, HLSL kaynak dosyaları düzenleyin ve ardından sağlayan Uygula & Düzenle destekler **Uygula** değişikliklerinizin etkisini görmek için bir çerçeve yeniden oluşturmak. Değiştirilen gölgelendirici kodunuz projenizin özgün HLSL kaynak dosya bütünlüğünü korumak için ayrı bir dosyada depolanır, ancak Değişikliklerinizi yaptıktan sonra seçebileceğiniz **kopyalayın...**  değişiklikleri projenize kopyalamak için. Bu özelliği kullanarak hızlı bir şekilde hataları içeren gölgelendirici kodunda gezinmek ve pahalı yeniden oluşturma ve yakalama adımlarını iş akışı hata ayıklama, HLSL ortadan kaldırın.  
  
## <a name="hlsl-disassembly"></a>HLSL ayrıştırma  
 HLSL gölgelendirici hata ayıklayıcısı, HLSL kaynak kod listenin sağındaki HLSL gölgelendirici derleme listesini sağlar.  
  
## <a name="debugging-hlsl-code"></a>HLSL kodunda hata ayıklama  
 HLSL hata ayıklayıcısı ardışık düzen aşamaları veya piksel geçmişi windows erişebilirsiniz.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>HLSL hata ayıklayıcısını Grafik Ardışık Düzen Aşamaları penceresinden başlatmak için  
  
1.  İçinde **grafik ardışık düzen aşamaları** penceresi, hata ayıklamak istediğiniz gölgelendirici ile ilişkili ardışık düzen aşamasını bulun.  
  
2.  Ardışık Düzen aşamasının başlığının altındaki seçin **hata ayıklamayı Başlat**, küçük yeşil bir ok görünür.  
  
    > [!NOTE]
    >  HLSL hata ayıklayıcısına bu giriş noktası, karşılık gelen aşamanın yalnızca ilk gölgelendirici iş parçacığında (yani işlenen ilk köşe veya piksel) hata ayıklar. Piksel geçmişi bu gölgelendirici aşamalarının diğer iş parçacıklarına erişmek için kullanabilirsiniz.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>HLSL hata ayıklayıcısını Grafik Piksel Geçmişi'nden başlatmak için  
  
1. İçinde **grafik piksel geçmişi** penceresi, hata ayıklamak istediğiniz gölgelendirici ile ilişkili çizim çağrısını genişletin. Her bir çizim çağrısı birden fazla temel öğeye karşılık gelebilir.  
  
2. Çizim çağrısı ayrıntılarında, elde edilen renk katkısı gölgelendirici kodunda bir hata olduğunu gösteren bir temel öğeyi genişletin. Hata olduğunu ortaya koyan birden fazla temel öğe varsa, soruna tanı koymayı zorlaştırabilecek hata birikiminden kaçınmak için bu duruma işaret eden ilk temel öğeyi seçin.  
  
3. Hata ayıklamak temel öğe ayrıntılarında yüklememeyi **köşe gölgelendiricisi** veya **piksel gölgelendiricisi**. Piksel gölgelendiricisinin doğru olduğu, ancak köşe gölgelendiricisinin kendisine yanlış sabitler aktarması nedeniyle yanlış renk katkısı ürettiğinden şüphelendiğiniz durumlarda, köşe gölgelendiricisi için hata ayıklama uygulayın. Aksi durumlarda piksel gölgelendiricisi için hata ayıklama uygulayın.  
  
    Seçilen gölgelendiricinin sağında, seçin **hata ayıklamayı Başlat**, küçük yeşil bir ok görünür.  
  
   > [!NOTE]
   >  HLSL hata ayıklayıcısına bu giriş noktası, ya seçilen çizim çağrısına, temel öğeye ve seçtiğiniz piksele karşılık gelen piksel gölgelendiricisi iş parçacığına ya da sonuçları çizim çağrısı, temel öğe ve seçmiş olduğunuz piksel tarafından ilişkilendirilen köşe gölgelendiricisi iş parçacıklarına hata ayıklama uygular. Köşe gölgelendiricileri durumunda, köşe gölgelendiricisi ayrıntılarını genişleterek giriş noktasını belirli bir köşeye kadar iyice daraltabilirsiniz.  
  
   HLSL hata ayıklayıcısı, gölgelendirici hatalarını ayıklamaya yönelik kullanma hakkında daha fazla örnek için bkz: [örnekler](graphics-diagnostics-examples.md) veya izlenecek yollar bağlantılı ayrıca bölümünde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Köşe gölgeleme nedeniyle nesnelerin eksikliği](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [İzlenecek yol: Gölgeleme nedeniyle çıkan oluşturma hatalarını ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [İzlenecek Yol: Hesaplayıcı Gölgelendiricisinde Hata Ayıklamak İçin Grafik Tanılamayı Kullanma](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)