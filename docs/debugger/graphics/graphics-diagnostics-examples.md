---
title: Grafik tanılama örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6816cced178e6e76a8fe33e37bbb075d1318c999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474310"
---
# <a name="graphics-diagnostics-examples"></a>Grafik Tanılama Örnekleri
Bu örnekler kullanarak işleme sorunları DirectX tabanlı uygulamalarda hata ayıklamak nasıl [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] grafik tanılama.  
  
## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama  
 Uygulamanızda işleme sorunları tanılamak için grafik tanılamayı kullanmadan önce çalışırken uygulamasından grafik bilgilerini yakalama sahip. Grafik bilgilerini yerel olarak çalışan bir uygulama veya bir uzak bilgisayara veya başka bir aygıt üzerinde çalışan bir uygulama yakalanır. Bu izlenecek yollar nasıl el ile veya program aracılığıyla bir uygulamadan grafik bilgilerini yakalayabilir gösterilmektedir:  
  
-   [İzlenecek Yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)  
  
-   [İzlenecek Yol: Grafik Bilgilerini Programla Yakalama](walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Grafik tanılama ARM tabanlı bir cihaz ile kullanma  
 Uzaktan hata ayıklama kullanarak ARM tabanlı bir cihaz üzerinde Direct3D uygulamanızı hata ayıklamak için grafik tanılamayı kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir ARM aygıtıyla kullanım grafik tanılama](how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Grafik bilgilerini tekrar oynatma  
 Çalışan bir uygulamanın grafik bilgilerini yakalama sonra işleme sorunları tanılamak için yakalanan olayları oynatabilirsiniz. Kayıttan yürütmek için geliştirme makinenizde kullanabilirsiniz veya bir uzak makine ya da bağlı cihaz kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Eksik nesneleri hata ayıklama  
 Eksik bir nesne (veya nesneler) deneyimine grafik geliştiriciler en yaygın işleme sorunları biridir. Bu tür sorunlar hataları birkaç farklı türde bir nesne görünüşe göre kayboluyor neden olabileceğinden tanılamak zor olabilir. Eksik nesneleri tipik nedenleri yanlış yapılandırılmış cihaz durumu, nesnenin geometri veya yanlış yapılandırılmış grafik ardışık düzen dönüştürme sorunları olabilir.  
  
 Bu senaryolar, nesneyi neden eksik olduğunu belirlemek ve sorumlu kodu bulmak için grafik tanılama nasıl kullanabileceğiniz gösterilmektedir.  
  
-   [İzlenecek Yol: Cihaz Durumu Nedeniyle Nesnelerin Eksikliği](walkthrough-missing-objects-due-to-device-state.md)  
  
-   [İzlenecek Yol: Köşe Gölgeleme Nedeniyle Nesnelerin Eksikliği](walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [İzlenecek Yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>İşleme hataları hata ayıklama  
 Doğru görünüm olmaması bir nesne (veya nesneler) deneyimine grafik geliştiriciler başka bir yaygın sorun ' dir. Bu tür sorunlar yanlış görünümünü ve onun neden gelen çok belirgin arasında olabilir çünkü tanılamak zor olabilir — yanlış doku bağlama — kadar çok ince — gölgelendirici kod veya beklenmeyen etkileşim gölgelendiriciler arasında bir hata. Bazı sorunlar hataların bir bileşimiyle kaynaklanıyor olabilir.  
  
 Tarafından ikincil gölgelendirici hata nedeniyle bir not şekilde Zarif işleme sorun aşağı izlemek için grafik tanılama nasıl kullanabileceğinizi gösteren bir senaryo aşağıda verilmiştir:  
  
-   [İzlenecek Yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>İşlem gölgelendiriciler hata ayıklama  
 Hatalı sonuçlar üretmek DirectCompute işlem gölgelendirici tekrar hata ayıklamak için grafik tanılamayı kullanabilirsiniz. DirectCompute ile çok sayıda veri öğeleri paralel hesaplamalar için GPU hesaplama gücünü kullanabilirsiniz. Belirli sorun türlerini, GPU kullanılarak birçok kez bile iyi en iyi duruma getirilmiş CPU kodu daha hızlı gerçekleştirebilirsiniz. Ancak, geleneksel hata ayıklayıcıları GPU üzerinde çalışan bir kod algılayamaz. Bu tür bir kod hata ayıklama çoğunlukla satıcıya özgü ve de Visual Studio ile tümleştirmek değil özel araçlar gerektirir. İşlem gölgelendirici hata ayıklama, aralık GPU arasında daha tutarlı hale getirmek için grafik tanılamayı DirectCompute gönderme olayları yakalar — Direct3D işleme olaylarının yanı sıra — böylece sorunları işlem gölgelendirici kodunuzda hata ayıklamak için alıştığınız araçları kullanabilirsiniz.  
  
 Gölgelendiricisinde bir hatadan kaynaklanır benzetimi sorun hata ayıklamak nasıl gösteren bir senaryo için bkz [izlenecek yol: bir işlem gölgelendirici hata ayıklamak için grafik Tanılama'yı kullanarak](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).