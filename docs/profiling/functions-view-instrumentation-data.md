---
title: İşlevler görünümü - izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7787e974b093156b27b2ace4353e94db05063d7d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238231"
---
# <a name="functions-view---instrumentation-data"></a>İşlevler görünümü - izleme verileri
İşlevler rapor görünümü profil oluşturma verileri işlevi adlarına göre listeler.  
  
## <a name="general"></a>Genel  
 Genel sütunları görünümü satırı işlevinde tanımlayın.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev adresi**|İşlev adresi.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işleve yapılan çağrıların toplam sayısı.|  
|**Kaynak dosya**|Bu işlev için tanım içeriyor kaynak dosya.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İşlemin adı.|  
|**Zaman özel araştırma ek yükü**|Bu işlev süredir yükü, araçları tarafından kaynaklanır. Bu ek yükü işlevin adı veriliyordu işlevlerinde içermez. Araştırma yükünü tüm özel sürelerinden çıkarılır.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev ve onun alt işlevleri için ek yükü süresi, araçları tarafından kaynaklanır. Ek yükü işlevin adı veriliyordu işlevleri dahil edin. Araştırma yükü tüm kapsayıcı sürelerinden çıkarılır.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman adı veriliyordu işlevlerinde işlevi ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın tarafından harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|Toplam bu işleve yapılan tüm çağrıların dahil süre geçti.|  
|**Geçen dahil süre %**|Bu işlevin dahil geçen süre harcandığını profil Çalıştır toplam geçen dahil süre yüzdesi.|  
|**Ortalama dahil geçen zaman**|Ortalama bu işlev çağrısının dahil süre geçti.|  
|**Max geçen dahil süre**|En fazla bu işlev çağrısının dahil zaman geçti.|  
|**Min (bunlar dahil) geçen zaman**|En düşük bu işlev çağrısının dahil süre geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 İşlev çağrı yığını üstünde olduğu zaman bir işlev kodu işlev gövdesine başka bir deyişle, yürütülmekte olan, süresi geçen özel değerleri gösterir. Zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir, ancak bu harcanan zamanın işlevin adı veriliyordu işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|Toplam bu işleve yapılan tüm çağrıların özel zaman geçti.|  
|**Özel geçen süre %**|Toplam geçen özel zaman bu işlevin harcandığını profil Çalıştır toplam geçen özel zaman yüzdesi.|  
|**Ortalama özel geçen zaman**|Ortalama bu işlev çağrısının özel zaman geçti.|  
|**Max geçen özel süre**|En fazla bu işlev çağrısının özel zaman geçti.|  
|**Min özel geçen zaman**|En düşük düzeyde, bu işlev çağrısının özel süre.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ancak harcanan zamanın işlevin adı veriliyordu işlevleri dahil edin.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|Bu işlev yapılan tüm çağrıların toplam uygulama dahil süresi.|  
|**Uygulama dahil süresi %**|Bu işlev toplam uygulama dahil süresi içinde harcandığını profil Çalıştır toplam geçen dahil zamanı yüzdesi.|  
|**Ortalama uygulama dahil süresi**|Bu işlev için bir çağrı ortalama uygulama dahil saati.|  
|**En fazla uygulama dahil süresi**|Bu işlev için bir çağrı en fazla uygulama dahil saati.|  
|**Min uygulama dahil süresi**|Bu işlev çağrısının minimum uygulama dahil süresi.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerler işlevi doğrudan çağrı yığını üstünde yürütülmekte olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ve bu harcanan zamanın işlevin adı veriliyordu işlevlerinde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|Bu işlev tüm çağrıları toplam uygulama özel saati.|  
|**Uygulama özel süresi %**|Bu işlev toplam uygulama özel zamanında harcandığını profil Çalıştır toplam geçen özel zaman yüzdesi.|  
|**Ortalama uygulama özel süresi**|Bu işlev için bir çağrı ortalama uygulama özel saati.|  
|**En fazla uygulama özel süresi**|Bu işlev için bir çağrı en fazla uygulama özel saati.|  
|**Min uygulama özel süresi**|Bu işlev için bir çağrı minimum uygulama özel saati.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlevler görünümü](../profiling/functions-view-sampling-data.md)   
 [İşlevler görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [İşlevler görünümü - izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)