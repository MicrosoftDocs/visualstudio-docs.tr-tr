---
title: Arayan - Aranan görünümü - çakışma verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f919bd6b3fdad1a9c7412960e14d8c9f4cf5af67
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263156"
---
# <a name="callercallee-view----contention-data"></a>Arayan/Aranan görünümü - çakışma verileri
Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri Çekişme bilgilerini görüntüler. Arayan/Aranan görünümü üç kılavuzları içerir.  
  
 **Geçerli işlevi** Orta kılavuzunda görüntülenir ve seçilen işlevi için Çekişme bilgilerini gösterir. Tüm engelleyici çekişmeleri işlevi için değerleri içerir.  
  
 **Geçerli işlevini çağırdı işlevleri** üst kılavuzunda görüntülenir ve seçilen (geçerli) işlevi değerlerine işlevleri (üst) arayan tek tek katkı gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzunda görüntülenir ve alt işlevi geçerli bir işlev tarafından çağrıldığında işlevleri seçili işlevinin ' % s'Aranan (alt) Çekişme bilgilerini gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Türü**|İşlev Bağlam:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlevi<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Özel engellenen süresi**|-Geçerli işlevi için bu işlev işlev gövdesinde kod yürütmek engellendi zaman. İşlev tarafından çağrılan işlevlerinde engellenen süresi dahil değildir.<br />-Çağıran işlev için özel engellenen zaman bu işlev geçerli işlevi çağrıldığında oluşan geçerli işlevinin kısmı.<br />-Çağrılan işlev için bu işlev bu işlev geçerli işlevi tarafından çağrıldığında, kendi kod yürütmek engellendi zaman. Çağrılan işlev tarafından çağrılan alt işlevlerinde engellenen süresi dahil değildir.|  
|**Özel engellenen süresi %**|Bu işlev bu bağlamda için özel engellenen zamanı çalıştırmak profil tüm engellenen zamanı yüzdesi.|  
|**Özel çekişmeleri**|-Geçerli işlevi için bu işlev işlev gövdesinde kod yürütmek engellendi sayısı. İşlevin adı veriliyordu işlevlerinde oluştu çekişmeleri dahil edilmez.<br />-Çağıran işlev için bu işlev geçerli işlevi çağrıldığında oluşan geçerli işlevinin özel çekişmeleri sayısı.<br />-Çağrılan işlev için bu işlev bu işlev geçerli işlevi tarafından çağrıldığında kod işlev gövdesine yürütme engellendi sayısı. Çağrılan işlev tarafından çağrılan işlevlerinde oluştu çekişmeleri dahil edilmez.|  
|**Özel çekişmeleri %**|Profil çalıştıran tüm çekişmeleri yüzdesi bu işlevi bu bağlamda için özel çekişmeleri yoktu.|  
|**İşlev adresi**|İşlev adresi ya da belirteci.|  
|**İşlev adı**|İşlev tam adı.|  
|**Dahil engellenen süre**|-Geçerli işlevi için bu işlev veya bu işlev tarafından çağrılan işlevler biri yürütülmesini engellendi zaman. Geçerli işlev tarafından çağrılan işlevler engellenen zamanında dahil edilir.<br />-Çağıran işlevi için (bunlar dahil) bölümünü zaman bu işlev geçerli işlevi çağrıldığında oluşan geçerli işlevinin engelledi.<br />-Aranan işlevi için bu işlev veya işlev tarafından çağrıldı işlevleri biri, bu işlev geçerli tarafından çağrıldığında yürütülmesini engellenmiş olan zaman işlev. Çağrılan işlev tarafından çağrılan işlevler engellenen zamanında dahil edilir.|  
|**Kapsayıcı engellenen süresi %**|Bu işlev bu bağlamda için kapsayıcı engellenen zamanı çalıştırmak profil tüm engellenen zamanı yüzdesi.|  
|**Kapsayıcı çekişmeleri**|-Geçerli işlevi için bu işlev veya işlev tarafından çağrılan işlevler biri yürütülmesini engellendi sayısı. İşlevin adı veriliyordu işlevlerinde oluştu çekişmeleri dahil edilir.<br />-Çağıran işlev için (bunlar dahil) çekişmeleri bu işlev geçerli işlevi çağrıldığında oluşan geçerli işlevinin sayısı.<br />-Çağrılan işlev için bu işlev veya işlev tarafından çağrılan işlevler biri, bu işlev geçerli işlevi tarafından çağrıldığında yürütülmesini engellenmiş olan sayısı. Çağrılan işlev tarafından çağrılan işlevlerinde oluştu çekişmeleri dahil edilir.|  
|**Kapsayıcı çekişmeleri %**|Profil çalıştıran tüm çekişmeleri yüzdesi bu işlevi bu bağlamda için özel çekişmeleri yoktu.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|Çekişmeleri meydana geldiği işlemin işlem kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kök işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlar.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/Aranan görünümü](../profiling/caller-callee-view.md)   
 [Arayan/Aranan görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)