---
title: Basic raporları komut satırından profil oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30361f0f4ae147458252400a5232a657574553d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786775"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Komut Satırından Temel Profil Oluşturma Raporları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, .vsp veya .vsps profil oluşturma veri dosyasından virgülle ayrılmış değer (.csv) raporlarını oluşturan temel VSPerfReport komutlarını açıklar. Tüm rapor seçeneklerinin bir açıklaması için bkz: [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Rapor komutları  
 Belirtilen bir profil oluşturma veri dosyası için bir rapor oluşturmak için aşağıdaki komutlardan birini kullanın.  
  
 **VSPerfReport** `VSPFile` **userrulesdirectory**  
 .Vsp veya .vsps dosyası için kullanılabilir tüm raporlar üretir.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Belirtilen rapor türlerini oluşturur.  
  
 **VSPerfReport** `VSPFile`   **/calltrace**  
 Her veri toplama olayını listeleyen bir rapor oluşturur. Yalnızca Araçlar.  
  
## <a name="summary-report-type-parameters"></a>Rapor tür parametreleri özeti  
 Aşağıdaki tabloda, belirtilen rapor türü seçeneği tarafından oluşturulan raporları açıklar. Raporun sütunları veri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.  
  
|Parametre özeti|Rapor açıklaması|Rapor başvurusu|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|İşlevler arası üst/alt ilişkilerini temsil eder.|-   [Örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)<br />-   [Ölçümlü izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Çakışma verileri](../profiling/caller-callee-view-contention-data.md)|  
|**İşlevi**|Profilleme verisini fonksiyon olarak listeler.|-   [Örnekleme verileri](../profiling/functions-view-sampling-data.md)<br />-   [Ölçümlü izleme verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Çakışma verileri](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Profil oluşturma çalıştırmasını işlevlerin profil oluşturma verilerini ve yürütme yollarını temsil eder.|-   [Ölçümlü izleme verileri](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Örnekleme verileri](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Çakışma verileri](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Profil oluşturma işaretleri yanı sıra profil oluşturma çalışması sırasında toplanan Windows performans sayacı değerlerini listeler.|-   [İşaretler görünümü](../profiling/marks-view.md)|  
|**IP**|Yönerge tarafından profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Çakışma verileri](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Ömür**|Ayrılmış nesnelerin ömrünü listeler.|-   [Nesne ömrü görünümü](../profiling/object-lifetime-view.md)|  
|**Satır**|Kaynak kod satırı tarafından profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/lines-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Çakışma verileri](../profiling/lines-view-contention-data.md)|  
|**Üst bilgi**|Profil oluşturma veri dosyasının başlık bilgileri.|Belirli dosya için.|  
|**Mark**|Profil oluşturma işaretleri profil oluşturma çalıştırmasını toplanmadı.|-   [İşaretler görünümü](../profiling/marks-view.md)|  
|**Module**|Modüller için profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/modules-view-sampling-data.md)<br />-   [Ölçümlü izleme verileri](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Çakışma verileri](../profiling/modules-view-contention-data.md)|  
|**İşlem**|İşlemler için profil oluşturma verilerini listeler.|-   [İşlem görünümü](../profiling/process-view.md)<br />-   [Çakışma verileri](../profiling/process-view-contention-data.md)|  
|**iş parçacığı**|İş parçacıkları için profil oluşturma verilerini listeler.|-   [İşlem görünümü](../profiling/process-view.md)|  
|**Türü**|Ayırma profil oluşturma verileri türe göre listelenmektedir.|-   [Ayırma görünümü](../profiling/dotnet-memory-allocations-view.md)|  
|**Çekişme**|Kaynak çakışmaları.|-   [Kaynak çakışmaları](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Performans kural sorunlarını listeler.|-Checkıd, açıklama ve kural sorununun kaynak kod konumunu listeler.|  
|**ETW**|Olay izleme için Windows (ETW) olayları, profil oluşturma çalışmasında toplanan.|-   [ETW raporu](../profiling/event-tracing-for-windows-etw-report.md)|



