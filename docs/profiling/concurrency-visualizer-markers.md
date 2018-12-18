---
title: Eşzamanlılık görselleştiricisi işaretleyicileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf07f939a9ce15d2ebca7afb0ee37695fa5fbf98
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220605"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlılık görselleştiricisi işaretleyicileri
Eşzamanlılık görselleştiricisi içinde temsil eden bir uygulama olayları simgeleri işaretleyicileri şunlardır.  Genellikle, bu olayları aşamaları veya bir uygulamadaki oluşum belirlemek için bir uygulama oluşturur.  Olayları, uygulama veya kitaplıkları ve uygulamanın kullandığı çalışma zamanları oluşturulabilir.  
  
## <a name="kinds-of-markers"></a>Tür işaretleyicileri  
 Eşzamanlılık görselleştiricisi işaretleyicileri üç tür uygulama olayları göstermek için kullanır.: işaretler, iletileri ve yayılır.  
  
1.  Kullanım bir *bayrağı* zamanlı uygulamanızda ilgi çekici bir noktası belirtmek için.  Örneğin, bir değişken değeri belirli bir eşiği ulaştı veya bir özel durum oluştu göstermenin bir bayrak kullanabilirsiniz.  
  
2.  A *ileti* de işaretler, fakat bir noktasında günlük stili izleme için kullanabilirsiniz.  Örneğin, ne, izleme ve eşzamanlılık görselleştiricisi içinde görüntülemek için artık bir ileti arama kaydırılabilir bir günlük dosyasına yazılan. Bu veri bir CSV dosyasına aktarmak için eşzamanlılık görselleştiricisi'ni de kullanabilirsiniz.  
  
3.  A *span* uygulamanızda, örneğin, biri, bir aşamaya, zaman aralığını temsil eder.  
  
## <a name="marker-linkage-to-threads"></a>İşaret bağlantı iş parçacıkları  
 Ayrı zaman çizelgesi kanal işaretçileri oluşturan her bir iş parçacığı vardır.  İşaret olayları oluşturmaktan sorumlu bir iş parçacığı Kimliğini yanındaki işaret kanal açıklaması gösterilir.  İşaret kanal sol tarafında gösterilen kimliği, geçerli işlemdeki başka bir iş parçacığı kimliği eşleşir.  
  
## <a name="marker-importance"></a>İşaret önem derecesi  
 İşaretçileri dört önem düzeyinden birine sahip olabilir: Düşük, normal, yüksek ve kritik.  Önem derecesi düzeyine dayalı işaretçileri kaynaklarını filtreleyebilirsiniz.  Örneğin, yalnızca normal veya kritik önemi olan belirli bir kaynaktan işaretçileri görmek istiyorsanız, filtrede yapılandırabilirsiniz [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu. Araç ipucu ve buna bir işaret önemini görüntülenen [işaretçiler raporu](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>İşaret kategorisi  
 Bir işaretleyici kategori grubu aynı kaynaktan geldiği işaret olayları gösterir.  Eşzamanlılık görselleştiricisi renk bayrakları ve yayılma farklı kategorilere ayırmak için kullanır. Eşzamanlılık görselleştiricisi kategorileri belirli olay sağlayıcısı işaret olayları filtrelemek için kullanmak için yapılandırabilirsiniz.  Kullanım [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) filtre yapılandırmak için iletişim kutusu.  
  
## <a name="known-sources-of-markers"></a>İşaretçileri bilinen kaynakları  
 Sağlayıcı için bazı kısıtlamalar aynılarını sürece herhangi bir ETW sağlayıcısı işaretleyicileri oluşturabilirsiniz. Eşzamanlılık görselleştiricisi işaretleyicileri için ek olay kaynakları için dinleyecek şekilde yapılandırabilirsiniz. Varsayılan olarak, bu olay kaynaklarını dinler:  
  
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)  
  
- [Görev Paralel Kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
- [Veri akışı](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
- [Paralel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)  
  
- [Senaryo işaretçisi desteği](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
  İşaretçileri sekmede kullanabileceğiniz [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu, işaretçiler çeşitli kaynaklardan eşzamanlılık görselleştiricisi ve, görüntülenip görüntülenmeyeceğini denetlemenizi önem ve kategoriye göre işaretçiler için filtre uygulayabilirsiniz.  
  
## <a name="markers-from-eventsource"></a>EventSource işaretçilerini  
 Eşzamanlılık görselleştiricisi EventSource olaylarını da görüntüleyebilirsiniz.  Daha fazla bilgi için [görselleştirme EventSource olaylarını işaretleyici olarak](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bayrak işaretleyicileri](../profiling/flag-markers.md)   
 [İleti işaretçileri](../profiling/message-markers.md)   
 [Kapsam işaretleyicileri](../profiling/span-markers.md)   
 [EventSource olaylarını işaretleyici olarak Görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md)