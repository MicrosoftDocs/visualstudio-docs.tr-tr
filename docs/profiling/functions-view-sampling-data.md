---
title: İşlevler görünümü - örnekleme veri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9084aad27d14825f4b3d0a648f0880d4db329c78
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237500"
---
# <a name="functions-view---sampling-data"></a>İşlevler görünümü - örnekleme verileri
Örnekleme profili yöntemi için işlevleri rapor görünümü Çalıştır profili oluşturma sırasında örneklenen işlevleri listeler.  
  
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
|**Kapsayıcı örnekleri**|Bu işlev yürütülürken toplanan örnek toplam sayısını; diğer bir deyişle, bu işlev çağrı yığınındaki olduğu zaman, toplanan örnek sayısı. Bu işlev tarafından çağrılan işlevler yürütülürken toplanan örnek sayısını içerir.|  
|**Kapsayıcı örnekleri %**|Profil çalıştıran tüm örneklerini yüzdesi bu işlevin kapsayıcı örnekleri yoktu.|  
|**Özel örnekleri**|Bu işlev gövdesi kodda yürütülürken toplanan örnek toplam sayısını; diğer bir deyişle, bu işlev üst kısmında çağrı yığını zaman oluştu. Bu işlev tarafından çağrılan işlevler toplanan örnekleri dahil edilmez.|  
|**Özel örnekleri %**|Profil çalıştıran tüm örneklerini yüzdesi bu işlev özel örnekleri yoktu.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü - izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)