---
title: Kanallar (iş parçacıkları görünümü) | Microsoft Docs
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
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: feebccb0905a4e3161484b5c1fe9f0142fa41d53
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743537"
---
# <a name="channels-threads-view"></a>Kanallar (İş Parçacıkları Görünümü)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi kanalları dört tür gösterir: iş parçacığı kanalları, disk kanalları, işaret Kanallar ve GPU kanalları.  
  
## <a name="thread-channels"></a>İş parçacığı kanallar  
 Bir iş parçacığı kanalı, renk, yalnızca bir iş parçacığı tarafından iş parçacığı durumu gösterir. Verilen iş parçacığı için Başlat işlevi, kanal adına duraklattığımda görüntülenir. Eşzamanlılık görselleştiricisi çeşitli türden iş parçacıklarıyla algılar. En yaygın türü aşağıdaki tabloda gösterilmektedir.  
  
|||  
|-|-|  
|Ana iş parçacığı|Uygulama başlangıç iş parçacığı.|  
|Çalışan iş parçacığı|Uygulamanın ana iş parçacığı tarafından oluşturulmuş bir iş parçacığı.|  
|CLR çalışan iş parçacığı|Ortak dil çalışma (CLR) tarafından oluşturulan çalışan iş parçacığı.|  
|Hata ayıklayıcı Yardımcısı|Visual Studio hata ayıklayıcı tarafından oluşturulan çalışan iş parçacığı.|  
|ConcRT iş parçacığı|Microsoft eşzamanlılık çalışma zamanı tarafından oluşturulan bir iş parçacığı.|  
|GDI iş parçacığı|Varsayılmaktadır tarafından oluşturulmuş bir iş parçacığı.|  
|OLE/RPC iş parçacığı|Bir RPC iş parçacığı oluşturulmuş bir iş parçacığı.|  
|RPC iş parçacığı|Bir RPC iş parçacığı oluşturulmuş bir iş parçacığı.|  
|Winsock iş parçacığı|Winsock iş parçacığı oluşturulmuş bir iş parçacığı.|  
|İş parçacığı havuzu|CLR iş parçacığı havuzu tarafından oluşturulmuş bir iş parçacığı.|  
  
## <a name="disk-channels"></a>Disk kanallar  
 Disk kanalları, fiziksel bilgisayardaki sürücüleri karşılık gelir. Okuma ve yazma işlemleri için farklı bir kanal sistem üzerindeki her fiziksel sürücü olduğundan, her sürücü iki kanal içerir. Disk numaralarını çekirdek cihaz adlara karşılık gelir. Bir disk kanal yalnızca diskte etkinliği olup olmadığını gösterilir.  
  
## <a name="marker-channels"></a>İşaret kanallar  
 İşaret kanalları, uygulama ve kullandığı kitaplıkları tarafından oluşturulan olayları karşılık gelir. Örneğin, görev paralel kitaplığı, paralel desenler kitaplığı ve C++ AMP işaretçileri olarak görüntülenen olayları oluşturur. Kanal açıklaması yanında görüntülenen bir iş parçacığı kimliği ile ilişkili her işaret kanalıdır. Olayı oluşturan iş parçacığı kimliği tanımlar. Kanal açıklaması, olaylar için olay izleme Windows (ETW) sağlayıcısı adını içerir. Kanal, olaylarından görüntülerse [eşzamanlılık görselleştiricisi SDK'si](../profiling/concurrency-visualizer-sdk.md), seri adı da görüntülenir.  
  
## <a name="gpu-channels"></a>GPU kanallar  
 GPU kanalları sistemde DirectX 11 etkinliği hakkındaki bilgileri görüntüler.  Grafik kartı ile ilişkili her DirectX altyapısı, ayrı bir kanalı vardır.  Tek tek parçaları DMA paket işlenmesi için harcanan zamanı temsil eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)



