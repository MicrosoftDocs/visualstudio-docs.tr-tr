---
title: Çekirdekler görünümü göstergesi | Microsoft Docs
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
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c00b6ccf56eb9e171fbaf9afdaea1828b5a1325
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783109"
---
# <a name="cores-view-legend"></a>Çekirdekler Görünümü Göstergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekirdekler görünümü göstergesi, renk ve ada göre her bir iş parçacığı tanımlar. Çekirdekler arası bağlam anahtarları, toplam bağlam anahtarları ve çekirdekleri çaprazlayan bağlam anahtarlarının yüzdesi sayılarını gösteren sütunları içerir. Gösterge satırlarda azalan olarak çekirdekler arası bağlam anahtarları sayısına göre sıralanır.  
  
 Satırları zaman çizelgesinde görüntülenen iş parçacıklarının filtrelemek için göstergeyi seçebilirsiniz. Seçili iş parçacıklarını zaman çizelgesinde gösterilir. Hiçbir satır seçtiyseniz, tüm satırları zaman çizelgesinde gösterilir.  
  
 Çekirdekler arası bağlam maliyet ek yükü ve performans, daha fazla aynı mantıksal Çekirdeğinde kalan anahtarlar geçer. İçerik geçişi sırasında işlemci kayıtları kaydedilir ve geri, işletim sistemi çekirdek kod yürütülür, çeviri arabelleğinde arabellek girişleri yüklenene ve işlemci işlem hattı temizlenir. Çekirdekler arası bağlam anahtarları, verileri önbelleğe almak için bu iş parçacığı başka bir çekirdek üzerinde geçerli olmadığından diğer bağlam anahtarları daha pahalı bile olabilir. Buna karşılık, bir iş parçacığı üzerine önceden çalışan çekirdek bağlam anahtarlı ise yararlı verileri önbelleğe hala olduğunu büyük olasılıkla olur. Çekirdekler arası bağlam anahtarları artırılmış iş parçacığını yönetmek denemeleridir benzeşimi ve performansı düştü, bu sorunu gidermek etkinleştirilip etkinleştirilmeyeceğini göz önünde bulundurun. İş parçacığı benzeşimini ortadan kaldırarak başlatın ve sonra elde edilen çekirdek arası davranışını gözlemleyin.  
  
 Aşağıdaki tabloda, gösterge öğeleri açıklar.  
  
|Öğe|Tanım|  
|-------------|----------------|  
|İş parçacığı adı|İş parçacığı rengini önceki çekirdekler zaman çizelgesi ve iş parçacığı adını gösterir.|  
|Çekirdekler arası bağlam anahtarları|İçerik Geçişi için de bir mantıksal çekirdekten diğerine geçiş bir iş parçacığı sayısı. Bir işlemci zar diğerine dışında aynı çağırmayı kalmak yerine çapraz çekirdekler arası bağlam anahtarları arasında ayrım yapmaz.|  
|Toplam bağlam geçişi|İçerik geçişi sırasında örnekleme süresi boyunca belirli bir iş parçacığı için toplam sayısı. Bir iş parçacığı bağlamından (örneğin, yürütme eşitleme) bir içerik anahtarı her değiştiğinde sayılır.|  
|Çekirdekleri Çaprazlayan bağlam anahtarlarının yüzdesi|Çekirdekler arası bağlam geçişleri sayısı, toplam bağlam anahtarları tarafından bölünmesiyle yüzdesi olarak hesaplanır. Daha yüksek bu yüzdesi, daha fazla çekirdekler arası bağlam yükü genel etkisini bu belirli iş parçacığının performansını geçer.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdekler Görünümü](../profiling/cores-view.md)



