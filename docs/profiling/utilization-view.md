---
title: Kullanım Görünümü | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 223535ef0b90869db191327abc7a757b5b79ae6b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677226"
---
# <a name="utilization-view"></a>Kullanım Görünümü
**Kullanım görünümü** CPU, GPU ve geçerli bir işlem tarafından kullanılan diğer sistem kaynaklarını hakkındaki bilgileri görüntüler (seçin **Çözümle** > **eşzamanlılık Görselleştirici** eşzamanlılık görselleştiricisi'ni başlatmak için). Bu analiz edilen işlem, işlem, sistem işlemi ve zaman içinde sistem üzerinde çalışan diğer işlemler tarafından ortalama Çekirdek kullanımını gösterir. Hangi belirli çekirdek herhangi bir zamanda etkin göstermez. Örneğin, iki çekirdek her belirli bir süre için yüzde 50 kapasitesine çalıştırıyorsanız, bu görünüm kullanılan bir mantıksal çekirdek gösterir. Görünüm, profil oluşturma süresi kısa süre parçalara bölerek oluşturulur. Her bir kesim için ortalama mantıksal çekirdekler üzerinde bu zaman aralığı boyunca yürütülen işlem iş parçacıklarının sayısını grafik çizer.  
  
 ![CPU Kullanımı görünümü](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 Zamanında (x ekseni) ve hedef işlem, işlem ve sistem işlemi tarafından kullanılan ortalama mantıksal çekirdek grafiğini gösterir. (Boşta Çekirdek Boşta işlemi gösterilmektedir. Sistem iş adına diğer işlemleri gerçekleştirebilen Windows işlemde işlemidir.) Kullanımı, kalan tüm çekirdek sistem hesabına çalışan kalan işlemler.  
  
 Mantıksal çekirdek sayısı, y ekseninde gösterilir. Windows, mantıksal çekirdek (örneğin, Hyper-Threading) donanım eşzamanlı çoklu iş parçacığı destek değerlendirir. Bu nedenle, çekirdek başına iki donanım iş parçacıklarının destekleyen bir dört çekirdekli işlemciye sahip bir sistem bir sekiz mantıksal-çekirdek sistem olarak görünür. Bu çekirdek görünümüne de geçerlidir. Daha fazla bilgi için [çekirdek görünümü](../profiling/cores-view.md).  
  
 GPU Etkinlik Grafiği, zaman içinde kullanılan DirectX altyapıları sayısını gösterir.  DMA paket işliyorsa altyapının kullanılır.  Grafiğin belirli DirectX altyapısı (örneğin, 3B altyapısı, Video altyapısı ve diğerleri) göstermez.  
  
## <a name="purpose"></a>Amaç  
 Eşzamanlılık görselleştiricisi kullandığınızda kullanım görünümü performans araştırmalar için başlangıç noktası olarak öneririz. Zaman içinde bir uygulamada eşzamanlılık derecesini genel bir bakış sağladığından, hızlı bir şekilde performans ayarlama gerektiren alanlarını tanımlayacak şekilde veya paralelleştirme kullanabilirsiniz.  
  
 Performans ayarlama ilgileniyorsanız beklentilerinizi karşılamıyor davranışını tanımlamak çalışıyor olabilir. Ayrıca aramanız varlığı ve mantıksal CPU çekirdeği düşük kullanımına sahip bölgelerin neden. Ayrıca CPU ve GPU arasında kullanım düzenlerini arıyor olabilirsiniz.  
  
 Bir uygulama paralelleştirmek içinde ilgileniyorsanız, yürütme ya da CPU bağımlı alanlarını veya burada CPU kullanmıyorsanız alanları için büyük olasılıkla bakıyorsunuz.  
  
 CPU bağımlı alanlar yeşil şunlardır. Grafik uygulaması seri ise kullanılan bir çekirdek gösterir.  
  
 Burada CPU kullanmıyorsanız gri alanlardır. Bu uygulamanın boşta olduğu noktaları veya diğer CPU bağımlı iş ile çakışan tarafından paralellik olanaklarını sağlayan gerçekleştirme engelleme g/ç temsil edebilir.  
  
 İlgilendiğiniz bir davranış bulduğunuzda, bu bölgede seçerek yakınlaştırma yapabilirsiniz. Size yakınlaştırma sonra iş parçacıkları görünümü ya da daha ayrıntılı analiz için çekirdekler görünümü geçebilirsiniz.  
  
 C++ AMP veya DirectX kullanarak GPU kullanıyorsanız, GPU kullanımı veya GPU beklenmedik bir şekilde boşta olduğu alanları motorlarında sayısını tanımlanmasına ilginizi çekebilir.  
  
## <a name="zoom"></a>Yakınlaştır  
 CPU kullanım grafiği veya GPU Etkinlik Grafiği yakınlaştırmak için bir bölüm seçin veya grafiğe yukarıda yakınlaştırma kaydırıcı aracını kullanın. Diğer görünümlerle geçiş yakınlaştırma ayarını devam ettirir. Yeniden uzaklaştırmak için yakınlaştırma kaydırıcı aracını kullanın. Kullanarak ayrıca yakınlaştırabilirsiniz **Ctrl**+**kaydırma**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)   
 [Çekirdekler görünümü](../profiling/cores-view.md)