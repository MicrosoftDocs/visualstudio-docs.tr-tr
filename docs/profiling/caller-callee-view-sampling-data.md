---
title: Veri örnekleme arayan - Aranan görünümü - | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b9b740689175f91f4bc69396121da0bed336532
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548716"
---
# <a name="callercallee-view---sampling-data"></a>Arayan/Aranan görünümü - örnekleme verileri
Arayan/Aranan görünümü seçili işlev ve üst ve alt işlevleri için profil bilgilerini görüntüler. Arayan/Aranan görünümü üç kılavuzları içerir.  
  
 **Geçerli işlevi** Orta Kılavuz ve bunun görüntülenen bilgi seçili işlevi için profil oluşturmayı gösterir. Tüm örneklenen işlev çağrıları değerlerini içerir.  
  
 **Geçerli işlevini çağırdı işlevleri** üst kılavuzunda görüntülenir ve seçilen (geçerli) işlevi değerlerine işlevleri (üst) arayan tek tek katkı gösterir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuz ve bunun görüntülenen alt işlevi geçerli bir işlev tarafından çağrıldığında seçili işlevinin bilgi Aranan (alt) işlevleri için profil oluşturmayı gösterir.  
  
> [!NOTE]
>  Gelişmiş güvenlik özellikleri Windows 8 ve Windows Server 2012 Visual Studio profil oluşturucu bu platformlarda toplar şekilde önemli değişiklikler gerekmiştir. UWP uygulamalar için yeni koleksiyon teknikler de gerekir. Bkz: [Windows 8 ve Windows Server 2012 uygulamaların performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**İşlev adı**|İşlev tam adı.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**İşlev adresi**|İşlev adresi.|  
|**Türü**|İşlev Bağlam:<br /><br /> -   **0** -geçerli işlevi<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlevi|  
|**Kök işlev adı**|Geçerli işlevin adı.|  
|**Kapsayıcı örnekleri**|-Geçerli işlevi için bu işlev veya bir alt işlevlerini yürütülmekte olan olsa da, toplanan örnek sayısı.<br />-Çağıran işlev için bu işlev geçerli işlevi çağrıldığında, toplanan dahil geçerli işlevi örnek sayısı.<br />-Çağrılan işlev için geçerli işlevi bu işlev çağrıldığında, toplanmış olan her ikisi de dahil bu işlev örnek sayısı.|  
|**Kapsayıcı örnekleri %**|Profil çalıştıran tüm örneklerini yüzdesi bu işlevin kapsayıcı örnekleri yoktu.|  
|**Özel örnekleri**|-Bu işlev doğrudan yürütülürken için geçerli işlevi, çalışmasını profil örneklerin sayısını toplanan; diğer bir deyişle, bu işlev çağrı yığını en üstünde zaman oluştu. Bu işlev, alt işlevleri yürütülürken toplanan örnek özel sayılar sayılmaz.<br />-Çağıran işlev için bu işlev geçerli işlevi çağrıldığında, toplanan özel geçerli işlevi örnek sayısı.<br />-Çağrılan işlev için geçerli işlevi bu işlev çağrıldığında toplanmış olan bir özel kullanım örnekleri bu işlevin sayısı.|  
|**Özel örnekleri %**|Profil çalıştıran tüm örneklerini yüzdesi bu işlev özel örnekleri yoktu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Arayan/Aranan görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/Aranan görünümü - .NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan/Aranan görünümü - izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)