---
title: Kanalları Yönet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c5727b8bc294ae28f48a6e1fc3194b258b9555
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844441"
---
# <a name="manage-channels"></a>Kanalları Yönet
İçinde **iş parçacıkları görünümü** belirli modelleri incelemek için Eş zamanlılık Görselleştirici kanallar işleminiz için düzenleyebilirsiniz. Kanallar sıralama, yukarı ve Aşağı Taşı ve gizlemek veya göstermek.  
  
## <a name="sort-by"></a>Sıralama ölçütü  
 Sıralama ölçütü denetim iş parçacıklarının geçerli yakınlaştırma düzeyi temelinde farklı ölçütlere göre sıralamak için kullanabilirsiniz. Bu, özellikle için belirli bir desene ararken kullanışlıdır. Bu ölçüte göre sıralama yapabilirsiniz:  
  
|Ölçütleri|Tanım|  
|--------------|----------------|  
|Başlangıç Zamanı|İş parçacığı tarafından başlangıç zamanları sıralar. Varsayılan sıralama düzeni budur.|  
|Bitiş Zamanı|İş parçacığı tarafından bitiş zamanları sıralar.|  
|Yürütme|İş parçacıklarının yürütülmesine harcanan zamanın yüzde olarak göre sıralar.|  
|Eşitleme|İş parçacıklarını eşitleme harcanan zamanın yüzde olarak göre sıralar.|  
|G/Ç|İş parçacığı içinde (veri okuma ve yazma) g/ç harcanan zamanın yüzde olarak göre sıralar.|  
|Uyku|İş parçacığı uyku modunda harcanan zamanın yüzde olarak göre sıralar.|  
|Disk belleği|İş parçacığı, disk belleği harcanan zamanın yüzde olarak göre sıralar.|  
|Önalım|İş parçacığı önalımı harcanan zamanın yüzde olarak göre sıralar.|  
|UI işleme|İş parçacığı kullanıcı arabirimi işlenmesinde harcanan zamanın yüzde olarak göre sıralar.|  
  
## <a name="move-selected-channel-up-or-down"></a>Seçilen kanalı yukarı veya aşağı taşıma  
 Bir kanal listede yukarı veya aşağı taşımak için bu denetimleri kullanabilirsiniz. Örneğin, diğer, belirli bir desene ya da bir iş parçacıkları arası ilişki incelemenize yardımcı olacak yanındaki ilgili kanalları getirin.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Seçilen kanal üstüne veya altına taşıyın  
 Belirli bir desene inceleyin veya başkalarının incelediğinizde bazı kanallar dışına taşımak, seçilen kanallar üst ya da listenin alt kısmına taşıyabilirsiniz.  
  
## <a name="hide-selected-channels"></a>Seçilen kanalları Gizle  
 Kanallar gizlemek bu denetim seçin. Bir iş parçacığı, yönetilen işlem ömrü için yüzde 100 eşitleme ise başka bir iş parçacığı analiz ederken Örneğin, size gizlemek.  
  
> [!NOTE]
>  Bir iş parçacığını gizleme ayrıca etkin göstergede ve profil raporlarda gösterilen hesaplama zamandan kaldırır.  
  
## <a name="show-all-channels"></a>Tüm kanalları Göster  
 Bu denetim etkin olduğunda bir veya daha fazla kanallar gizlidir. Seçerseniz, tüm gizli öğeleri gösterilir ve saat hesaplamaları için döndürülür.  
  
## <a name="move-markers-to-top"></a>Üst taşıma işaretleyicileri  
 Bir izleme işaret olayları içeriyorsa, zaman çizelgesi başına işaret kanalları taşımak için bu komutu kullanabilirsiniz. Göreli sıralarına korunur.  
  
## <a name="group-markers-by-thread"></a>İş parçacığı tarafından Grup işaretçileri  
 Bir izleme işaret olayları içeriyorsa, Grup işaret kanalları işaret olayları üretilen iş parçacığı altında bu komutu kullanabilirsiniz.  Disk kanalları kanal listenin üst kısmına taşınır ve GPU kanalları altına taşınır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yakınlaştırma Denetimi (iş parçacıkları görünümü)](../profiling/zoom-control-threads-view.md)   
 [Ölçüm modu açık/kapalı](../profiling/measure-mode-on-off.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)