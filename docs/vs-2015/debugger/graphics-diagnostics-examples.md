---
title: Grafik tanılama örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9c4a5f3396992b8bca2756b33b9b6f920d54733
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776128"
---
# <a name="graphics-diagnostics-examples"></a>Grafik Tanılama Örnekleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu örnekler kullanarak DirectX tabanlı uygulamalarda işleme sorunları hatalarını ayıklamak nasıl [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] grafik tanılama.  
  
## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Uygulamanızda işleme sorunlarını tanılamak için grafik Tanılama'yı kullanabilmeniz için önce çalıştığı sırada bir uygulamadan grafik bilgilerini yakalama gerekir. Grafik bilgilerini yerel olarak çalışan bir uygulamadan veya uzak bir bilgisayar veya başka bir cihaz üzerinde çalışan bir uygulamadan yakalanabilir. Bu izlenecek yollar nasıl el ile veya programlama yoluyla bir uygulamadan grafik bilgilerini yakalayabilir gösterilmektedir:  
  
-   [İzlenecek Yol: Grafik Bilgilerini Yakalama](../debugger/walkthrough-capturing-graphics-information.md)  
  
-   [İzlenecek Yol: Grafik Bilgilerini Programla Yakalama](../debugger/walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>ARM tabanlı bir cihazla grafik Tanılama'yı kullanma  
 Uzaktan hata ayıklamayı kullanarak ARM tabanlı bir cihaz üzerinde Direct3D uygulamanızın hatalarını ayıklamak için grafik tanılama kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir ARM cihazla grafik tanılamayı kullanın](../debugger/how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütme  
 Çalışan bir uygulamadan grafik bilgilerini yakalama sonra işleme sorunlarını tanılamak için yakalanan olayları oynatabilirsiniz. Kayıttan yürütme için geliştirme makinenizi kullanabilirsiniz veya bir uzak makine ya da bağlı olduğunuz cihaz kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Eksik nesneleri hata ayıklama  
 Eksik bir nesne (veya nesneler) deneyimine grafik geliştiriciler en yaygın işleme sorunlarını biridir. Bu tür sorunlar, hataları birkaç farklı türde nesneyi görünüşe göre kaybolmasına neden olabilir çünkü tanı koymak güç olabilir. Eksik nesneleri tipik nedenleri yapılandırılmış cihaz durumu, nesnenin geometrisini veya yanlış yapılandırılmış grafik ardışık düzen dönüştürme sorunları olabilir.  
  
 Bu senaryolar, bir nesne neden eksik olduğunu belirlemek ve sorumlu kodu bulmak için grafik tanılama nasıl kullanabileceğinizi gösterir.  
  
-   [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](../debugger/walkthrough-missing-objects-due-to-device-state.md)  
  
-   [İzlenecek Yol: Köşe Gölgeleme Nedeniyle Nesnelerin Eksikliği](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [İzlenecek Yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler](../debugger/walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>İşleme hatalarını ayıklama  
 Doğru görünümü olmaması bir nesne (veya nesneler) grafik geliştiriciler deneyimini başka bir yaygın bir sorundur. Bu tür sorunlar yanlış görünümünü ve bunun nedenini gelen çok belirgin değişebilir olduğundan tanı koymak güç olabilir — yanlış doku bağlama — çok çok hafif — gölgelendirici kodu veya gölgelendiricileri arasındaki etkileşim beklenmeyen bir hata. Bazı sorunların hatalarının bir bileşimiyle kaynaklanıyor olabilir.  
  
 Küçük gölgelendirici hata tarafından neden olmayan şekilde Zarif işleme sorunuyla aşağı izlemek için grafik tanılama nasıl kullanabileceğinizi gösteren bir senaryo aşağıda verilmiştir:  
  
-   [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Hesaplayıcı gölgelendiricilerde hata ayıklama  
 DirectCompute hesaplayıcı gölgelendiricisi hatalı sonuçlar üreten bir çekirdek hata ayıklamak için grafik tanılama kullanabilirsiniz. DirectCompute ile GPU işlem gücüne çok sayıda paralel veri öğeleri üzerinde hesaplamalar gerçekleştirmek için kullanabilirsiniz. Belirli tür sorunları, GPU kullanan birden çok kez daha iyi iyileştirilmiş CPU kod daha hızlı gerçekleştirebilirsiniz. Bununla birlikte, geleneksel hata ayıklayıcılar, GPU üzerinde çalışan kod algılayamaz. Bu türde bir kod hata ayıklama, çoğunlukla satıcıya özgü ve daha iyi Visual Studio ile tümleşebilen değil özel araçlar gerektirir. Bir aralık Gpu'lar, COMPUTE gölgelendirici hata ayıklaması daha tutarlı hale getirmek için grafik tanılama gönderme DirectCompute olayları yakalar; Direct3D işleme olaylarının yanı sıra — böylece sorunları compute gölgelendirici kodunuzda hata ayıklamak için alışık olduğunuz araçları kullanabilirsiniz.  
  
 Bir hesaplayıcı gölgelendiricisinde hata nedeniyle bir simülasyon sorunu çözmeye anlatan bir senaryo için bkz [izlenecek yol: bir işlem Gölgelendiricisinde hata ayıklamak için grafik Tanılama'yı kullanarak](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).



