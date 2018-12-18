---
title: Çekirdekler görünümü göstergesi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee31b1547f9607f54cc5db9d056b997f071633ff
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691593"
---
# <a name="cores-view-legend"></a>Çekirdekler görünümü göstergesi
Çekirdekler görünümü göstergesi her iş parçacığı tarafından renk ve adını tanımlar. Çapraz çekirdek bağlamı anahtarlar, toplam bağlam anahtarları ve çekirdek arası İçerik Geçişi yüzdesi sayılarını gösteren sütunları içerir. Gösterge satırlarda azalan sırada listeleyin arası çekirdek bağlamı anahtarları sayısı göre sıralanır.  
  
 Zaman Çizelgesi'nde görüntülenen iş parçacığı filtrelemek için göstergede satırları seçin. Yalnızca seçili iş parçacığı zaman çizelgesinde gösterilir. Hiçbir satır seçtiyseniz, tüm satırları zaman çizelgesinde gösterilir.  
  
 Çapraz çekirdek bağlamı aynı mantıksal çekirdeği üzerinde kalır anahtarları'den fazla ek yükü ve performans maliyeti geçer. İçerik geçişi sırasında işlemci yazmaçlar kaydedilir ve geri, işletim sistemi çekirdek kodu yürütülür, çeviri arabelleğinde arabellek girişleri yeniden ve işlemci ardışık düzen temizlendi. Önbellek verilerini başka bir çekirdek bu iş parçacığında için geçerli değil çünkü arası çekirdek bağlamı anahtarları diğer içerik geçişi daha pahalı olabilir. Buna karşılık, bir iş parçacığı üzerine önceden çalıştıran çekirdek bağlamı anahtarlı ise yararlı verileri hala önbelleğinde olduğunu büyük olasılıkla. Çapraz çekirdek bağlamı anahtarları artan iş parçacığını yönetmek girişimleri tarafından benzeşim ve performans düşürülmüş, yoksa bu sorunu gidermek göz önünde bulundurun. İş parçacığı benzeşimini ortadan kaldırarak başlatın ve sonra oluşan geçici çekirdek davranış gözlemleyin.  
  
 Aşağıdaki tabloda gösterge öğelerini açıklar.  
  
|Öğe|Tanım|  
|-------------|----------------|  
|İş parçacığı adı|İş parçacığı rengini önceki çekirdekler zaman çizelgesi ve o iş parçacığı adını gösterir.|  
|Çapraz çekirdek İçerik Geçişi|İçerik Geçişi için bir mantıksal çekirdek ayrıca anahtarlı bir iş parçacığı sayısı. Bir işlemci dökme da aynı çağırmayı kalmak yerine başka bir çapraz arası çekirdek bağlamı anahtarları arasında ayırt etmez.|  
|Toplam İçerik Geçişi|Bağlam toplam sayısı için belirli bir iş parçacığı örnekleme süresi boyunca geçer. Bir iş parçacığı bağlamdan (örneğin, yürütme eşitleme) bir içerik anahtarı her değiştiğinde sayılır.|  
|Çekirdek arası İçerik Geçişi yüzdesi|Yüzde olarak arası çekirdek bağlamı anahtarları toplam bağlam geçişi sayısını tarafından sayısının bölünmesiyle hesaplanır. Daha yüksek bu yüzde, büyük arası çekirdek bağlamı yükü genel etkisini bu belirli iş parçacığı performansına geçer.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Çekirdekler Görünümü](../profiling/cores-view.md)