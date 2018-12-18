---
title: Arayan - Aranan görünümü - çakışma verileri | Microsoft Docs
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
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e226cb5a44923e73d64a9374eb1d170e18d2428
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797617"
---
# <a name="caller--callee-view----contention-data"></a>Arayan / Aranan görünümü - çakışma verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri çakışma bilgilerini görüntüler. Arayan/Aranan görünümü üç Kılavuzlar içerir.  
  
 **Geçerli işlev** Orta kılavuzda görüntülenir ve seçili işlev çakışma bilgilerini gösterir. İşlev için tüm engelleyici Çekişme değerlerini içerir.  
  
 **Geçerli işlevi çağırmış işlevler** üst kılavuz görüntülenir ve seçili (geçerli) işlevinin değerlere işlevler bireysel Katkıları çağıranın (üst) gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz görüntülenir ve alt işlevi geçerli işlev tarafından çağrıldığında seçili işlev işlevlerini (alt) çağrılan çakışma bilgilerini gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Türü**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Dışlamalı engellenme süresi**|-Geçerli işlev için bu işlev, işlev gövdesinde kod yürütürken gelen engellendiği zaman. İşlev tarafından çağırılan işlevlerdeki engellenme süresi dahil değildir.<br />-Çağıran işlev için bu işlev geçerli işlev çağrıldığında oluşan geçerli işlevin dışlamalı engellenme süresi kısmı.<br />-Çağrılan işlev için bu işlev, bu işlev geçerli işlev tarafından çağrıldığında, kendi kod yürütme engellendi zaman. Alt işlevlerinde çağrılan işlev tarafından çağırılan engellenme süresi dahil değildir.|  
|**Dışlamalı engellenme süresi yüzdesi**|Dışlamalı engellenme süresi için bu işlevi bu bağlamda, profil oluşturma çalışması içindeki tüm engellenme süresinin yüzdesi.|  
|**Dışlamalı Çekişmeler**|-Geçerli işlev için bu işlev, işlev gövdesinde kod yürütürken gelen engellendi sayısı. İşlev tarafından çağrılan işlevler oluşan çakışmaları dahil edilmez.<br />-Çağıran işlev için bu işlev geçerli işlev çağrıldığında oluşan geçerli işlevin dışlamalı Çekişme sayısı.<br />-Çağrılan işlev için bu işlev, bu işlev geçerli işlev tarafından çağrıldığında işlev gövdesinde kod yürütürken gelen engellendi sayısı. Çağrılan işlev tarafından çağırılan işlevlerdeki oluşan çakışmaları dahil edilmez.|  
|**Dışlamalı Çekişme yüzdesi**|Profil çalıştıran tüm çekişmelerin yüzdesi için bu işlevi bu bağlamda dışlamalı çekişmeler yoktu.|  
|**İşlev adresi**|İşlev adresi veya belirteci.|  
|**İşlev adı**|İşlev tam adı.|  
|**Kapsamlı engellenme süresi**|-Geçerli işlev için bu işlev ya da bu işlev tarafından çağrılmış işlevlerin yürütülmesini engellendiği zaman. Geçerli işlev tarafından çağrılan işlevler engellenme süresi dahildir.<br />-Bir çağıran işlevin için kapsamlı bir kısmı bu işlev geçerli işlev çağrıldığında oluşan geçerli işlevin zaman engelledi.<br />-Bu işlev veya bir işlev tarafından çağırılan işlev, bu işlev geçerli tarafından çağrıldığında yürütülmesini engellenmiş olan zaman için çağrılan işlev, işlev. Engellenme süresi çağrılan işlev tarafından çağrılan işlevler dahil edilmiştir.|  
|**Kapsamlı engellenme süresi yüzdesi**|Kapsamlı engellenme süresi için bu işlevi bu bağlamda, profil oluşturma çalışması içindeki tüm engellenme süresinin yüzdesi.|  
|**Kapsamlı Çekişmeler**|-Geçerli işlev için bu işlev veya bir işlev tarafından çağrılmış işlevlerin yürütülmesini engellendi sayısı. İşlev tarafından çağrılan işlevler oluşan çakışmaları dahil edilir.<br />-Çağıran işlev için bu işlev geçerli işlev çağrıldığında oluşan geçerli işlevin kapsamlı Çekişme sayısı.<br />-Çağrılan işlev için bu işlev veya bir işlev tarafından çağrılmış işlevlerin yürütülmesini geçerli işlev tarafından bu işlev çağrıldığında engellendi sayısı. Çağrılan işlev tarafından çağırılan işlevlerdeki oluşan çakışmaları dahil edilir.|  
|**Kapsamlı Çekişme yüzdesi**|Profil çalıştıran tüm çekişmelerin yüzdesi için bu işlevi bu bağlamda dışlamalı çekişmeler yoktu.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**İşlem kimliği**|Çekişme oluştuğu işlemin işlem kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü](../profiling/caller-callee-view.md)   
 [Arayan / Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)



