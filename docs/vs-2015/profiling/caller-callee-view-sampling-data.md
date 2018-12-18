---
title: Arayan - Aranan görünümü - örnekleme verileri | Microsoft Docs
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
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e46befbdd8f727485884197a3cfb284fa5a8cf6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796967"
---
# <a name="caller--callee-view---sampling-data"></a>Arayan / Aranan görünümü - örnekleme verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri için profil bilgilerini görüntüler. Arayan/Aranan görünümü üç Kılavuzlar içerir.  
  
 **Geçerli işlev** Orta Kılavuz ve bunun görüntülenen bilgi seçili işlev için profil oluşturmayı gösterir. İşlev çağrıları tüm örneklenen değerlerini içerir.  
  
 **Geçerli işlevi çağırmış işlevler** üst kılavuz görüntülenir ve seçili (geçerli) işlevinin değerlere işlevler bireysel Katkıları çağıranın (üst) gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz ve bunun görüntülenen geçerli işlev tarafından alt işlev çağrıldığında çağrılan (alt) işlevleri için seçili işlev bilgileri profil oluşturma gösterilmektedir.  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem kimliği**|İşlem, profil oluşturma çalışması Kimliğine (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi içeren modül adı.|  
|**Modül yolu**|İşlevi içeren modül yolu.|  
|**Kaynak dosyası**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlev adı**|İşlev tam adı.|  
|**İşlevin satır numarası**|Satır numarası kaynak dosyada bu işlevin başlangıcı.|  
|**İşlev adresi**|İşlevin adresi.|  
|**Türü**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev|  
|**Kök işlev adı**|Geçerli işlevin adı.|  
|**Kapsamlı örnekler**|-Geçerli işlev için bu işlev veya onun alt işlevlerden birini çağırılma yürütüldüğü karşın, toplanan örnek sayısı.<br />-Çağıran işlev için bu işlev geçerli işlevin çağrıldığı zaman, toplanmış olan kapsamlı örnek geçerli işlevin sayısı.<br />-Çağrılan işlev için bu işlev, bu işlev geçerli işlevin çağrıldığı zaman, toplanmış olan kapsamlı örnek sayısı.|  
|**Kapsamlı örnek yüzdesi**|Profil çalıştıran tüm örneklerin yüzdesi, bu işlevin kapsamlı örnekler yoktu.|  
|**Dışlamalı örnekler**|-Bu işlev doğrudan yürütülürken profil çalışan örnek sayısı geçerli işlev için toplanan; diğer bir deyişle, bu işlev çağrı yığınının başında ne zaman. Bu işlevin alt işlevleri yürütülürken toplanan örnekler dışlamalı sayımlar içinde sayılmaz.<br />-Çağıran işlev için bu işlev geçerli işlevin çağrıldığı zaman, toplanmış olan dışlamalı örnek geçerli işlevin sayısı.<br />-Çağrılan işlev için bu işlev, bu işlev geçerli işlevin çağrıldığı zaman, toplanmış olan özel örnek sayısı.|  
|**Dışlamalı örnek yüzdesi**|Profil çalıştıran tüm örneklerin yüzdesi, bu işlevin dışlamalı örnekler yoktu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)



