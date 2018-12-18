---
title: Eşzamanlılık görselleştiricisi | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05ed2edd453cd9e267a32bfdd5d9a6b0ad6a7ac3
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220670"
---
# <a name="concurrency-visualizer"></a>Eşzamanlılık Görselleştiricisi
> [!NOTE]
>  Eşzamanlılık görselleştiricisi, Visual Studio için isteğe bağlı bir uzantısıdır. Eşzamanlılık görselleştiricisi ve Eşzamanlılık Görselleştirici toplama araçları aşağıdaki bağlantılardan birini indirin:  
> 
> - İndirme [Visual Studio 2017 için eşzamanlılık görselleştiricisi](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) uzantısı.  
> - İndirme [Visual Studio 2015 için eşzamanlılık görselleştiricisi](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) uzantısı.  
>   -   İndirme [Eşzamanlılık Görselleştirici toplama araçları Visual Studio 2015 için](http://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) komut satırından Visual Studio 2015 için eşzamanlılık görselleştiricisi içinde görüntüleyebilirsiniz izlemeleri topladığınız sağlar. Visual Studio yüklü olmayan bilgisayarlarda aracı kullanılabilir.  
  
 Çok iş parçacıklı uygulamanızın nasıl çalıştığını görmek için eşzamanlılık görselleştiricisi'ni kullanabilirsiniz. Eşzamanlılık görselleştiricisi'ndeki Görünüm, sistemin bir bütün olarak programınızdaki iş parçacıkları arasındaki geçici ilişkiyi gösteren grafik, tablo ve metinsel veri sağlar. Performans sorunları, CPU Tıkanıklığı, iş parçacığı Çekişme, çapraz çekirdek iş parçacığı geçişi, eşitleme gecikmeleri, DirectX etkinliği, çakışan I/O alanları ve diğer bilgileri bulmak için eşzamanlılık görselleştiricisi'ni kullanabilirsiniz. Görünümler, yığın ve kaynak kodu çağırmak için kendi grafik çıktısına bağlanarak üzerinde çalışabilir veri sağlar.  

> [!NOTE]
>  Eşzamanlılık görselleştiricisi Web projelerini desteklemez.  
  
 Eşzamanlılık görselleştiricisi dayanan [olay izleme için Windows](http://go.microsoft.com/fwlink/?LinkId=234579) işlevselliği.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kullanım Görünümü](../profiling/utilization-view.md)|Görüntüleme ve tüm işlemciler arasında sistem etkinliğini çözümleme açıklar.|  
|[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)|Programınızdaki iş parçacıkları arasındaki etkileşimler analiz edilmesi anlatılmaktadır.|  
|[Çekirdekler Görünümü](../profiling/cores-view.md)|Çekirdekler arasında iş parçacığı geçişinin analiz edilmesi anlatılmaktadır.|  
|[Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Birçok ortak deseni açıklar ve bunların eşzamanlılık görselleştiricisi içinde nasıl görüneceğini gösterir.|  
|[Visual Studio blogunda paralel geliştirme](http://go.microsoft.com/fwlink/?LinkId=235385)|Eşzamanlılık görselleştiricisi için ipuçları ve en iyi yöntemler sağlar.|  
|[Performans Raporu Görünümleri](../profiling/performance-report-views.md)|Visual Studio profil oluşturma araçları görünümleri ve raporlar için başvuru bilgileri sağlar.|  
|[Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)|Eşzamanlılık Görselleştiricisindeki ek bilgileri görüntülemek için kaynak kodunuzun açıklar.|  
|[Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Eşzamanlılık görselleştiricisi komut satırı yardımcı programının (CVCollectionCmd.exe) toplamak ve Visual Studio olmayan makinelerdeki izlemeleri işlemek için nasıl kullanılacağını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio profil oluşturma](../profiling/index.md)  
 [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
