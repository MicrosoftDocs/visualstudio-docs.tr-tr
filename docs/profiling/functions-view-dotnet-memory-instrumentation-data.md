---
title: İşlevler görünümü - .NET bellek izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d48393a2d160e3691069a4b5f86dd814b63d935d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237688"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>İşlevler görünümü - .NET bellek izleme verileri
İşlevler görünümü izleme metodunu kullanarak toplanan .NET bellek ayırma profil oluşturma verileri, profil oluşturma çalışması sırasında bellek tahsis işlevleri listeler. Bir işlev satır ayırma ve işlev için zamanlama verileri sayısı ve boyutu bildirir.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlev adresi.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|  
|**Kaynak dosya**|Bu işlev tanımını içeren kaynak dosyası.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Zaman özel araştırma ek yükü**|Araçları nedeniyle bu işlev için ek süre. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve araçları nedeniyle alt işlevleri için ek yükü süresi. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlevin dahil .NET bellek değerleri sayısını (ayırmaları) ve boyutunu (bayt) işlevi ve onun alt işlevleri tarafından oluşturulan nesneleri gösterir.  
  
 Özel bellek değerleri sayısını ve boyutunu işlevi tarafından ve onun alt işlevleri tarafından oluşturulan nesneleri gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsayıcı ayırmaları**|Bu işlev ve bu işlev tarafından çağrılan işlevler oluşturulan nesneleri toplam sayısı.|  
|**Kapsayıcı ayırmaları %**|Profil çalışmasını ayrılan tüm nesneleri yüzdesi bu işlevin kapsayıcı ayırmaları yoktu.|  
|**Özel ayırmaları**|İşlev kodu işlev gövdesine edildi yürütülürken oluşturulan nesneleri toplam sayısı. Bu sayı, bu işlev tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içermez.|  
|**Özel ayırmaları %**|Profil çalıştırdığınızda oluşturulan tüm nesneler yüzdesi bu işlevin özel ayırmaları yoktu.|  
|**Kapsayıcı bayt**|Bu işlev ve bu işlev tarafından çağrılan işlevler ayrılan belleğin bayt sayısı.|  
|**Kapsayıcı bayt %**|Profil çalışmasını ayrılan tüm bayt bellek yüzdesi bu işlevin kapsayıcı bayt yoktu.|  
|**Özel bayt sayısı**|Bu işlev tarafından ayrılan ancak tarafından işlev olmayan belleğin bayt sayısı, bu işlev tarafından adı veriliyordu.|  
|**Özel bayt %**|Profil çalışmasını ayrılan tüm bayt bellek yüzdesi bu işlevin özel bayt yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman harcanan zamanın alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|Toplam bu işleve yapılan tüm çağrıların dahil süre geçti.|  
|**Geçen dahil süre %**|Bu işlevin dahil geçen süre harcandığını profil Çalıştır toplam geçen dahil süre yüzdesi.|  
|**Ortalama dahil geçen zaman**|Ortalama bu işlev çağrısının dahil süre geçti.|  
|**Max geçen dahil süre**|En fazla bu işlev çağrısının dahil zaman geçti.|  
|**Min (bunlar dahil) geçen zaman**|En düşük bu işlev çağrısının dahil süre geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Bir işlev, doğrudan çağrı yığını üstünde yürütme süresi geçen özel değerleri gösterir. Zaman zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içerir ancak harcanan zamanın alt işlevlerde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|Toplam bu işleve yapılan tüm çağrıların özel zaman geçti.|  
|**Özel geçen süre %**|Toplam geçen özel zaman bu işlevin harcandığını profil Çalıştır toplam geçen özel zaman yüzdesi.|  
|**Ortalama özel geçen zaman**|Ortalama bu işlev çağrısının özel zaman geçti.|  
|**Max geçen özel süre**|En fazla bu işlev çağrısının özel zaman geçti.|  
|**Min özel geçen zaman**|En düşük düzeyde, bu işlev çağrısının özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ancak alt işlevlerde harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|Bu işlev yapılan tüm çağrıların toplam uygulama dahil süresi.|  
|**Uygulama dahil süresi %**|Bu işlev toplam uygulama dahil süresi içinde harcandığını profil Çalıştır toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama uygulama dahil süresi**|Bu işlev için bir çağrı ortalama uygulama dahil saati.|  
|**En fazla uygulama dahil süresi**|Bu işlev için bir çağrı en fazla uygulama dahil saati.|  
|**Min uygulama dahil süresi**|Bu işlev çağrısının minimum uygulama dahil süresi.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler işlevi doğrudan çağrı yığını üstünde yürütülmekte olan süreyi belirtir. Ya da alt işlevlerde harcanan zamanın içermez süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|Bu işlev tüm çağrıları toplam uygulama özel saati.|  
|**Uygulama özel süresi %**|Bu işlev toplam uygulama özel zamanında harcandığını profil Çalıştır toplam geçen özel zaman yüzdesi.|  
|**Ortalama uygulama özel süresi**|Bu işlev için bir çağrı ortalama uygulama özel saati.|  
|**En fazla uygulama özel süresi**|Bu işlev için bir çağrı en fazla uygulama özel saati.|  
|**Min uygulama özel süresi**|Bu işlev için bir çağrı minimum uygulama özel saati.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler görünümü](../profiling/functions-view-instrumentation-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)