---
title: Modüller görünümü - Çekişme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f9ad65a81820e37c01d55a0ddba441dd30977b4
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256064"
---
# <a name="modules-view---contention-data"></a>Modüller görünümü - çakışma verileri
Profil oluşturma verileri örneklenen modülleri göre gruplandırılmış eşzamanlılık verileri çakışma verileri modülleri görünümünü görüntüler. Her modül hiyerarşik bir köküdür. Çekişme olayları meydana geldiği modülündeki işlevlerin modülü düğümünün altında listelenir.  
  
 Diğer bir deyişle, bir çakışma olayı meydana geldiğinde kendi kod işlevi çalıştırıldığında işlevi çağrı yığını, kaynak satırları ve yürütülmekte adresleri işlevi düğümü altında listelenen yönerge üstündeki oluştu. Çizgi veya yönerge yürütülürken zaman veri kaynak satırı veya bir yönerge işaretçisi için toplanan olduğundan (bunlar dahil) ve özel değerler her zaman satır verileri ve yönerge verileri için aynıdır.  
  
 Aşağıdaki tabloda çakışma verileri modülleri görünümünü sütunlardaki değerleri açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Özel engellenen süresi**|-Bir işlev için bu işlevi işlev gövdesine kod yürütmek engellendi zaman. İşlevin adı veriliyordu işlevlerinde engellenen süresi dahil değildir.<br />-Bir modül için özel engellenen zaman modülündeki işlevlerin toplamı.<br />-Bir satır veya bir yönerge, zaman için bu satırı veya yönerge yürütülmesini engellendi.|  
|**Özel engellenen süresi %**|-Bir işlev veya bir modül için profil çalıştıran tüm engellenen zaman yüzdesi bu işlev veya modül özel engellenen süresini oluştu.<br />-Bir satır veya bir yönerge, profil çalıştırmada tüm engellenen zaman bu satırı veya yönerge yürütülmesini engellendi yüzdesi için.|  
|**Özel çekişmeleri**|-Bir işlev için bu işlevi işlev gövdesine kod yürütmek engellendi sayısı. İşlevin adı veriliyordu işlevlerinde çekişmeleri dahil edilmez.<br />-Bir modül için özel çekişmeleri modülündeki işlevlerin toplamı.<br />-Bir satır veya bu satırı veya yönerge yürütülmesini engellendiğini bir yönerge sayısı için.|  
|**Özel çekişmeleri %**|-Bir işlev veya bir modül için profil çalıştıran tüm çekişmeleri yüzdesi bu işlevin veya modülü özel çekişmeleri yoktu.<br />-Bir satır veya bir yönerge için profil çalıştıran tüm çekişmeleri yüzdesi bu satırı veya yürütülmesini yönerge engellenen çekişmeleri yoktu.|  
|**Dahil engellenen süre**|-Bir işlev için bu işlevi veya bu işlev tarafından çağrılan işlev yürütülmesini engellendi zaman.<br />-Bir modül için bu modülü en az bir hangi işlevinden engellenen zamanında toplamını yığında oluştu.<br />-Bir satır veya bir yönerge, zaman için bu satırı veya yönerge yürütülmesini engellendi.|  
|**Kapsayıcı engellenen süresi %**|-Bir işlev veya bir modül için profil çalıştıran tüm engellenen zamanın yüzde olarak bu işlev veya modül (bunlar dahil) engellenen süresini oluştu.<br />-Bir satır veya bir yönerge için profil oluşturma tüm engellenen zamanın yüzde olarak çalıştırın, bu satırı veya yönerge yürütülmekte olan içinde.|  
|**Kapsayıcı çekişmeleri**|-Bir işlev için bu işlevi veya bu işlev tarafından çağrılan işlev yürütülmesini engellendi sayısı.<br />-Bir modül için hangi en az bir işlevde bu modülden çekişmeleri sayısı yığında oluştu.<br />-Bir satır veya bu satırı veya yönerge yürütülmesini engellendiğini bir yönerge sayısı için.|  
|**Kapsayıcı çekişmeleri %**|-Bir işlev veya bir modül için profil çalıştıran tüm çekişmeleri yüzdesi bu işlevin veya modül (bunlar dahil) çekişmeleri yoktu.<br />-Bir satır veya bir yönerge için profil oluşturma tüm engellenen zamanın yüzde olarak çalıştırın, bu satırı veya yönerge yürütülmekte olan içinde.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Modül adı**|İşlev, satır veya yönerge işaretçisi içeren modülü adı.|  
|**Modül yolu**|Modül, işlev, satır veya yönerge işaretçisi içeren modülü yolu.|  
|**Ad**|Modül veya işlev adı.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Modüller görünümü](../profiling/modules-view.md)   
 [Modüller görünümü - izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü](../profiling/modules-view-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-sampling-data.md)