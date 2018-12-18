---
title: Kanalları yönetme | Microsoft Docs
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
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dba4def686f97bd3169eb5816630c272dc61d8e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726002"
---
# <a name="manage-channels"></a>Kanalları Yönet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde **iş parçacıkları görünümü** belirli desenleri inceleyebilirsiniz için eşzamanlılık görselleştiricisi içinde kanalları süreciniz için düzenleyebilirsiniz. Kanalları sıralamak, yukarı ve aşağı taşıyın ve gizlemek veya göstermek.  
  
## <a name="sort-by"></a>Sıralama ölçütü  
 Sıralama ölçütü denetimi, iş parçacıklarının geçerli yakınlaştırma düzeyini temel alan farklı ölçütlere göre sıralamak için kullanabilirsiniz. Bu, belirli bir desene aranırken özellikle yararlıdır. Bu ölçüte göre sıralama yapabilirsiniz:  
  
|Ölçütleri|Tanım|  
|--------------|----------------|  
|Başlangıç Zamanı|İş parçacığı başlangıç süreleri göre sıralar. Varsayılan sıralama düzenini budur.|  
|Bitiş Zamanı|İş parçacıkları, bitiş zamanına göre sıralar.|  
|Yürütme|İş parçacıkları tarafından yürütme için harcanan sürenin yüzdesi sıralar.|  
|Eşitleme|İş parçacığı eşitleme harcanan sürenin yüzdesi göre sıralar.|  
|G/Ç|İş parçacıkları (veri okuma ve yazma) I/O için harcanan sürenin yüzdesi göre sıralar.|  
|Uyku|İş parçacıkları, uyku modunda harcanan sürenin yüzdesi olarak sıralar.|  
|Disk belleği|İş parçacıkları disk belleği harcanan sürenin yüzdesi göre sıralar.|  
|Önalım|İş parçacıkları önalım harcanan sürenin yüzdesi olarak sıralar.|  
|UI işleme|İş parçacıkları, kullanıcı arabirimi işlenmesinde harcanan sürenin yüzdesi olarak sıralar.|  
  
## <a name="move-selected-channel-up-or-down"></a>Seçilen kanal yukarı veya Aşağı Taşı  
 Bir kanal listede yukarı veya aşağı taşımak için bu denetimleri kullanabilirsiniz. Örneğin, diğer iş parçacıkları arası ilişki ya da belirli bir desene incelemenize yardımcı olmak için yanındaki ilgili kanalları getirin.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Seçilen kanal üstüne veya altına taşıyın.  
 Böylece belirli bir desene inceleyin veya başkalarının incelediğinizde bazı kanalları dışına taşıyın, seçilen kanallar üst veya listenin taşıyabilirsiniz.  
  
## <a name="hide-selected-channels"></a>Seçilen kanallar Gizle  
 Kanalları gizlemek istediğinizde bu denetimi seçin. Bir iş parçacığını ömrü boyunca yönetilen işleminizi yüzde 100 eşitleme ise, diğer iş parçacıklarını analiz ederken gibi gizlemek.  
  
> [!NOTE]
>  Bir iş parçacığını gizleme Ayrıca, etkin açıklama ve profili raporlarda gösterilen hesaplama zamanı kaldırır.  
  
## <a name="show-all-channels"></a>Tüm kanalları Göster  
 Bu denetim, bir veya daha fazla kanal gizlendiğinde etkin değil. Seçerseniz, tüm gizli öğeleri gösterilir ve saat hesaplamaları için döndürülür.  
  
## <a name="move-markers-to-top"></a>İşaretleyicileri en üste Taşı  
 Bir izleme işaret olayları içeriyorsa, işaret kanalları zaman çizelgesi üstüne taşımak için bu komutu kullanabilirsiniz. Kendi göreli sıralarını korunur.  
  
## <a name="group-markers-by-thread"></a>Grup işaretleyicileri iş parçacığına göre  
 Bir izleme işaret olayları içeriyorsa, işaret olayları oluşturan iş parçacığı grubu işaret kanallarda için bu komutu kullanabilirsiniz.  Disk Kanallar, kanal listesinin üstüne taşınır ve GPU kanalları altına taşınır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yakınlaştırma Denetimi (iş parçacıkları görünümü)](../profiling/zoom-control-threads-view.md)   
 [Ölçüm modu açık/kapalı](../profiling/measure-mode-on-off.md)   
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)



