---
title: Eşzamanlılık görselleştiricisi işaretleyicileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fa2a57d08f2b86fec573f02129a326907e3e3a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790454"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlılık Görselleştiricisi İşaretleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
- [Görev Paralel Kitaplığı (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Veri akışı](http://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Paralel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Eşzamanlılık Çalışma Zamanı](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Senaryo işaretçisi desteği](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](http://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  İşaretçileri sekmede kullanabileceğiniz [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusu, işaretçiler çeşitli kaynaklardan eşzamanlılık görselleştiricisi ve, görüntülenip görüntülenmeyeceğini denetlemenizi önem ve kategoriye göre işaretçiler için filtre uygulayabilirsiniz.  
  
## <a name="markers-from-eventsource"></a>EventSource işaretçilerini  
 Eşzamanlılık görselleştiricisi EventSource olaylarını da görüntüleyebilirsiniz.  Daha fazla bilgi için [görselleştirme EventSource olaylarını işaretleyici olarak](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bayrak işaretleyicileri](../profiling/flag-markers.md)   
 [İleti işaretçileri](../profiling/message-markers.md)   
 [Kapsam işaretleyicileri](../profiling/span-markers.md)   
 [EventSource Olaylarını İşaretleyici Olarak Görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md)



