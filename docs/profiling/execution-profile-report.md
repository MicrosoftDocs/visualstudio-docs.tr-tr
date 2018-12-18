---
title: Yürütme Profil raporu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa0800bcf6a4fedfbcd8c787b3cca89638e9bcb9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935295"
---
# <a name="execution-profile-report"></a>Yürütme Profil Raporu
Yürütme Profil raporu geleneksel örnekleme profilidir. Örnekleri yaklaşık her milisaniyelik zaman bir iş parçacığı bir mantıksal çekirdek üzerinde çalışıyor ve örnek yığınları birikmiş kümesini harmanlama tarafından eşzamanlılık görselleştiricisi tipik çağrı ağacını oluşturur dönemlerde alınır. Bu tablodaki verileri geçerli zaman aralığını ve gizli dizileri ve uygulanabilir bu filtreler tarafından etkilenebilir:  
  
- Yalnızca kendi kodum seçili ise, yalnızca kullanıcı kodunu ve kullanıcı kodu aşağıda bir düzey olan yığın çerçevelerini gösterilmektedir.  
  
- Gürültü azaltma değeri ayarlarsanız, rapordan çıktıklarında belirtilen sıklıkta filtrelenir daha az olan yığınları Harmanlanmış  
  
  Aşağıdaki tabloda, raporda sütunları gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|Ad|İşlev adı çağrı yığınının her düzeyi.|  
|Kapsamlı örnekler|Çağrı yığını ağacı bu düzeye toplanan tüm yığınları için toplanan örneklerin toplam sayısı. Bu işlev için dışlamalı örnekler ve kapsamlı sayaçları tüm alt düğümlerin toplamını kapsamlı sayıdır.|  
|Dışlamalı örnekler|Bu işlev çağrı yığınının en alt düzeyin olduğu toplanan örneklerin toplam sayısı.|  
|% Dahil|Kapsamlı örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzde iki ondalık basamağa yuvarlanır.|  
|% Özel|Dışlamalı örnekler sütununda gösterilen toplam örneklerin yüzdesi. Yüzde iki ondalık basamağa yuvarlanır.|  
|Ayrıntılar|İşlev tam adı. Kullanılabilir olduğunda bu satır sayısını içerir.|  
  
 Bu raporu tablosu görülebilir [yürütme zamanı (iş parçacıkları görünümü)](../profiling/execution-time-threads-view.md) görünümü.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)