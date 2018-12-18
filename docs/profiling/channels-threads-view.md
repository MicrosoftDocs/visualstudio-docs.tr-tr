---
title: Kanallar (iş parçacıkları görünümü) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42b1baeec4543cb56d1e2320f26c9457dd7aac80
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34269134"
---
# <a name="channels-threads-view"></a>Kanallar (iş parçacıkları görünümü)
Eşzamanlılık görselleştiricisi kanalları dört tür gösterir: iş parçacığı kanalları, disk kanalları, işaret kanalları ve GPU kanalları.  
  
## <a name="thread-channels"></a>İş parçacığı kanalları  
 Bir iş parçacığı kanal rengini tek iş parçacığı tarafından iş parçacığı durumu gösterir. Kanal adına duraklattığınızda, verilen iş parçacığı için başlangıç işlevi görüntülenir. Eşzamanlılık görselleştiricisi iş parçacığı çeşitli türlerde algılar. En yaygın tür aşağıdaki tabloda gösterilmiştir.  
  
|||  
|-|-|  
|Ana iş parçacığı|Uygulama başlangıç iş parçacığı.|  
|Çalışan iş parçacığı|Uygulama Ana iş parçacığı tarafından oluşturulan bir iş parçacığı.|  
|CLR iş parçacığı|Ortak dil çalışma zamanı tarafından (CLR) oluşturuldu işçi iş parçacığı.|  
|Hata ayıklayıcı Yardımcısı|Visual Studio hata ayıklayıcısı tarafından oluşturuldu işçi iş parçacığı.|  
|ConcRT iş parçacığı|Microsoft Eşzamanlılık Çalışma Zamanı Modülü tarafından oluşturulan bir iş parçacığı.|  
|GDI iş parçacığı|Varsayılmaktadır tarafından oluşturulan bir iş parçacığı.|  
|OLE/RPC iş parçacığı|Bir RPC çalışan iş parçacığı oluşturulmuş bir iş parçacığı.|  
|RPC iş parçacığı|RPC iş parçacığı olarak oluşturulmuş bir iş parçacığı.|  
|Winsock iş parçacığı|Winsock iş parçacığı olarak oluşturulmuş bir iş parçacığı.|  
|İş parçacığı havuzu|CLR iş parçacığı havuzu tarafından oluşturulan bir iş parçacığı.|  
  
## <a name="disk-channels"></a>Disk kanalları  
 Disk kanalları bilgisayardaki fiziksel sürücüleri karşılık gelir. Okuma ve yazma işlemleri için ayrı kanalları sistem üzerindeki her fiziksel sürücü olmadığı için her iki kanal içerir. Disk numaralarını çekirdek aygıt adlara karşılık gelir. Bir disk kanal yalnızca diskte etkinliği olup olmadığını gösterilir.  
  
## <a name="marker-channels"></a>İşaretçi kanalları  
 İşaretçi kanalları, uygulama ve kullandığı kitaplıkları tarafından oluşturulan olayları karşılık gelir. Örneğin, görev paralel kitaplığı, paralel Desen kitaplığı ve C++ AMP işaretleyici olarak görüntülenen olayları oluşturur. Her işaret kanal kanal açıklama yanında görüntülenen bir iş parçacığı kimliği ile ilişkilidir. Olayı oluşturan iş parçacığı kimliği tanımlar. Kanal açıklaması, olaylar oluşturulan olay Windows için izleme (ETW) sağlayıcısı adını içerir. Kanal olaylarından görüntülerse [eşzamanlılık görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md), seri adı da görüntülenir.  
  
## <a name="gpu-channels"></a>GPU kanalları  
 GPU kanalları sistemde DirectX 11 etkinliği hakkında bilgi görüntüleyin.  Grafik kartı ile ilişkili her DirectX altyapısı ayrı bir kanalı vardır.  Tek tek parçaları DMA paket işleme harcadığı zamanı temsil eder.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İş Parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)