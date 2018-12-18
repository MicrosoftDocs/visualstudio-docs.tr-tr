---
title: Modüller görünümü - örnekleme veri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97b3289119ec77c191d540285b235bab443ab6f3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256874"
---
# <a name="modules-view---sampling-data"></a>Modüller görünümü - örnekleme verileri
Profil oluşturma verileri örneklenen modülleri göre gruplandırılmış veri görüntüler performans verileri örnekleme modülleri görünümü. Her modül hiyerarşik bir köküdür. Örneklenen işlevleri modülün modül düğümünün altında listelenir.  
  
> [!NOTE]
>  Gelişmiş güvenlik özellikleri Windows 8 ve Windows Server 2012 Visual Studio profil oluşturucu bu platformlarda toplar şekilde önemli değişiklikler gerekmiştir. UWP uygulamalar için yeni koleksiyon teknikler de gerekir. Bkz: [Windows 8 ve Windows Server 2012 uygulamaların performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 İşlev çalıştırıldığında ne zaman örnekleri toplandı (diğer bir deyişle, işlev çağrı yığını üstünde olduğu), yürütülmekte yönerge adreslerini ve kaynak satırları işlevi düğümünün altında listelenir. Çizgi veya yönerge yürütülürken zaman veri kaynak satırı veya bir yönerge işaretçisi için toplanan olduğundan (bunlar dahil) ve özel değerler her zaman satır verileri ve yönerge verileri için aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modül, işlev, satır numarası veya yönerge işaretçisi adresi adı.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlev, satır veya yönerge işaretçisi içeren modülü adı.|  
|**Modül yolu**|Modül, işlev, satır veya yönerge işaretçisi içeren modülü yolu.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Kapsayıcı örnekleri**|-Bir işlev için bu işlev veya bu işlev tarafından çağrıldı bir işlevi yürütmeden; örnek sayısı diğer bir deyişle, çağrı sayısı, bu işlevi içeren örnekleri yığın.<br />-Bir modül için hangi en az bir işlevde modülden örneklerin sayısını yürütülmekte olan.<br />-Bir satır veya yönerge, örnek sayısı için bu satırı veya yönerge yürütürken.|  
|**Kapsayıcı örnekleri %**|-İşlev veya modül için profil çalıştıran tüm örneklerini yüzdesi bu işlev veya modül (bunlar dahil) örnekleri yoktu.<br />-Bir satır veya yönerge için profil oluşturma tüm örneklerini yüzdesi çalıştırın, bu satırı veya yönerge yürütülmekte olan içinde.|  
|**Özel örnekleri**|-Bir işlev için çağrı sayısı, bu işlev doğrudan yürütülmekte olan örnekleri yığın; diğer bir deyişle, bu işlev çağrı yığını üstünde olduğu örnek sayısı.<br />-Bir modül için özel örnekleri modülündeki işlevlerin toplamı.<br />-Bir satır veya yönerge, örnek sayısı için bu satırı veya yönerge yürütürken.|  
|**Özel örnekleri %**|-İşlev veya modül için profil çalıştıran tüm örneklerini yüzdesi bu işlev veya modül özel örnekleri yoktu.<br />-Bir satır veya yönerge için profil oluşturma tüm örneklerini yüzdesi çalıştırın, bu satırı veya yönerge yürütülmekte olan içinde.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Modüller görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü - izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)