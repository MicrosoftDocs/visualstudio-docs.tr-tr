---
title: Engelleme zamanı Profil raporu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93288759ebcea6fd88777feeb1764ac41c57acc4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865797"
---
# <a name="blocking-time-profile-report"></a>Engelleme zamanı Profil raporu
Profil raporlarını engelleme her kategorisi (örneğin, "G/ç" veya "Eşitleme") belirli çağrı yığınlarını engelleme zamanı veri toplama sağlayın. Önalım raporu geçerli işlem önalım örneklerinin birlikte etkisiz işlemleri listeler. Engelleme Profil raporu oluşturmak için araç engelleme API çağrıları toplar ve bunları çağrı yığınlarını ağacının toplanır. Bu raporlarda gösterilen verileri geçerli zaman aralığı, gizli dizileri ve uygulanabilir aşağıdaki iki filtre olarak değişir:  
  
- Yalnızca kendi kodum seçtiyseniz bir düzey altındaki kullanıcı kodunun yanı sıra kullanıcı koduna sahip yığın çerçevelerini sunulur.  
  
- Gürültü azaltma değeri ayarlarsanız, belirtilen sıklıkta atlanır daha az olan yığınları Harmanlanmış.  
  
  Engelleme zamanı için harcanan kod satırının bulmak için herhangi bir çağrı ağacını giriş genişletin. Kendi kısayol menüsünde bir giriş kaynağı olan satırını bulun, seçin **kaynağı görüntüle**. Bu bir kısayol menüsünde, çağıran kod satırı bulunacak seçin **çağrı siteleri görünümünü**. Yalnızca bir çağrı sitesini kullanılabilir, komut vurgulanan satırlık bir kod için çağrı sitesini bağlanır. Birden çok çağrı siteleri varsa, komutu bir girişi seçin ve ardından bir iletişim kutusu açılır **kaynağa Git** vurgulanan çağrı sitesini bulmaya düğmesi. Genellikle en iyi örnek, en çok zaman veya her ikisi de çağrı sitedeki kaynak kodunu görüntülemek en kullanışlıdır.  
  
## <a name="blocking-time-report-columns"></a>Engelleme zamanı Rapor sütunları  
 Aşağıdaki tabloda her engelleme zamanı rapor için sütunları gösterir.  
  
|Sütun adı|Açıklama|  
|-----------------|-----------------|  
|**Ad**|İşlev adı çağrı yığınının her düzeyi.|  
|**Örnekler**|Görünür zaman aralığı için engelleme çağrısının örnek sayısı.|  
|**Kapsamlı engelleme süresi**|Engelleme çağrı yığını ağacı Bu düzey için toplanan tüm yığınları için harcanan zamanı toplamı. Dışlamalı engelleme süresi Bu işlevin ve tüm alt düğümlerin dışlamalı engelleme süresi toplamı kapsamlı sayıdır.|  
|**Dışlamalı engelleme süresi**|Sırasında bu harcanan toplam engelleme zamanı işlev çağrı yığınının en düşük düzeydir. Yüksek dışlamalı engelleme süresi olan bir benzersiz çağrı yığını girdisi, ilgilendiğiniz bir işlevi olabilir.|  
|**API/bekleme kategorisi**|Çağrı yığınının en alt düzeyinde işlevler için yalnızca gösterilir. Engelleme çağrı imzası tanınan burada engelleme API adı sağlanır. İmza tanınmıyorsa çekirdek tarafından raporlanan bilgileri sağlanır.|  
|**Ayrıntıları**|İşlev tam adı. Kullanılabilir olduğunda bu satır sayısını içerir.|  
  
### <a name="synchronization"></a>Eşitleme  
 Eşitleme rapor, eşitleme ve her çağrı yığınının kez engelleme toplama engelleme segmentleri sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [eşitleme zamanı](../profiling/synchronization-time.md)  
  
### <a name="sleep"></a>Uyku  
 Uyku rapor uyku harcanan zaman için öznitelikli zaman ve her bir çağrı yığınını toplama engelleme sürelerinin engellemek için sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [uyku zaman](../profiling/sleep-time.md).  
  
### <a name="io"></a>G/Ç  
 G/ç rapor g/ç ve her çağrı yığınının kez engelleme toplama engelleme segmentleri sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [g/ç zamanı (iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Bellek yönetimi  
 Bellek yönetimi raporu, bellek yönetimi işlemleri ve her çağrı yığınının kez engelleme toplama engelleme segmentleri sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [bellek yönetimi zamanı](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Önalım  
 Önalım raporu geçerli işlem örneklerinin sayısını birlikte etkisiz işlemleri listeler.  Her işlem, geçerli işlemdeki iş parçacıkları yerine belirli dizileri görüntülemek ve iş parçacığı başına önalım örneklerinin dökümünü görüntülemek için genişletebilirsiniz. Bu engelleme rapor diğerlerine göre daha az eyleme dönüştürülebilir çünkü önalım işleminizi üzerinde genellikle uygulanan işletim sistemi tarafından kodunuzda bir sorundan değil. Daha fazla bilgi için [Önalım zamanı](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>UI işleme  
 UI işleme rapor UI işleme bloklarını ve her çağrı yığınının kez engelleme toplama engelleme segmentleri engellemek için sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [UI işleme zamanı](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İş Parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)