---
title: Çağrı ağacı görünümü - çakışma verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 003e25121b3761a6e9440dcd4f0885975e0d98c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816469"
---
# <a name="call-tree-view---contention-data"></a>Çağrı Ağacı Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çağrı ağacı görünümü, profili oluşturulan uygulamada geçiş işlev yürütme yollarını görüntüler. Ağacının kökü, uygulama veya bileşen giriş noktasıdır. Her işlev düğümü adlı tüm İşlevler, işlev engellendi sayısı ve diğer iş parçacıkları veya işlemlerdeki sahip bir kaynak için contending çünkü işlevi engellenen süreyi listeler.  
  
 Çağrı ağacı görünümü çağrı ağacında üst işlev tarafından çağrılan işlev örnekleri için değerler. Yüzde değerleri, profil oluşturma çalıştırmasını çakışması toplam sayısı işlev örneği değerine karşılaştırılmasıyla hesaplanır.  
  
## <a name="highlighting-the-execution-hot-path"></a>Yürütme etkin yol vurgulamasını  
 Çağrı ağacı görünümü genişletebilir ve işlem ya da çoğu Çekişme oluşturulan işlev yürütme yolunu vurgulayın.  
  
-   En etkin yol görüntülemek için işlem ya da işlev sağ tıklayın ve ardından **etkin yolu Genişlet**.  
  
## <a name="setting-the-call-tree-root-node"></a>Çağrı ağacı kök düğümü ayarlama  
 Profil oluşturma çalıştırmasını her işlem, bir kök düğüm olarak görünür. Çağrı ağacı görünümü başlangıç düğümünün ayarlamak için başlangıç düğümü olarak ayarlayın ve ardından istediğiniz düğümü **kümesi kök**.  
  
 Kök düğümü ayarladığınızda, Seçili düğüme alt ağacı dışında görünümünden diğer tüm girişleri kaldırın. Kök düğümü özgün düğüme geri sıfırlamak için çağrı ağacı Görünümü'nde sağ tıklayın ve ardından **sıfırlama kök**.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı engellenme süresi**|Bu yürütme yolunu Bu işlevde örneklerini profil oluşturma çalışmasında çalıştırılması engellenen zaman. Süresi alt işlevlerin işlev tarafından çağrılmış engellenme süresi içermez.|  
|**Dışlamalı engellenme süresi yüzdesi**|Dışlamalı engellenme süresi için bu yürütme yolunu Bu işlevde, profil oluşturma çalışması içindeki tüm engellenme süresinin yüzdesi.|  
|**Dışlamalı Çekişmeler**|Bu yürütme yolunu Bu işlevde örneklerinde oluştu çekişmelerin sayısı. Sayı, alt işlevlerin işlev tarafından çağırılan Çekişme içermez.|  
|**Dışlamalı Çekişme yüzdesi**|Dışlamalı Çekişme çağrı ağacında üst işlev tarafından çağrılan örnekleri bu işlevin olan tüm profil oluşturma çalıştırmasını çakışması yüzdesi.|  
|**İşlev adresi**|İşlevin adresi.|  
|**İşlev adı**|İşlev tam adı.|  
|**Kapsamlı engellenme süresi**|Bu yürütme yolunu Bu işlevde örneklerini profil oluşturma çalışmasında çalıştırılması engellenen toplam zaman. İşlev tarafından çağrılan alt işlevlerin engellenme süresi geçen süreyi de içerir.|  
|**Kapsamlı engellenme süresi yüzdesi**|Profil çalıştıran tüm engellenme süresinin yüzdesi bu yürütme yolunu Bu işlevde örnekleri için kapsamlı engellenme süresi oldu.|  
|**Kapsamlı Çekişmeler**|Bu yürütme yolunu Bu işlevde örneklerini engellenen çekişmelerin toplam sayısı. Sayı, alt işlevlerin işlev tarafından çağırılan Çekişme içerir.|  
|**Kapsamlı Çekişme yüzdesi**|Profil çalıştıran tüm çekişmelerin yüzdesi bu yürütme yolunu bu işlevdeki örneklerin kapsamlı çekişmeler yoktu.|  
|**düzeyi**|İşlev çağrısı ağacında düzeyi. Yalnızca VSReport komut satırı raporlarda. Daha fazla bilgi için bkz [VSPerfReport](../profiling/vsperfreport.md).|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view.md)   
 [Çağrı ağacı görünümü - izleme](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Çağrı ağacı görünümü - örnekleme](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view-instrumentation-data.md)   
 [Çağrı Ağacı Görünümü](../profiling/call-tree-view-sampling-data.md)



