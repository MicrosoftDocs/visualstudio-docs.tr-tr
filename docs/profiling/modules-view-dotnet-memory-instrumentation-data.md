---
title: Modüller görünümü - .NET bellek izleme verileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a0dd74f25ed5dc7f76b9d35ae3d2d9833f8e4ab8
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255531"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modüller görünümü - .NET bellek izleme verileri
.NET bellek ayırma verileri izleme metodunu kullanarak toplanan modülleri görünümünü profil Çalıştır yürütüldü modüller tarafından bellek ve zamanlama verileri gruplandırır. Profil oluşturma verilerini modülü işlevler için modülü düğümünün altında listelenir.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|İşlev veya modül adı.|  
|**İşlev satır numarası**|Bu işlev kaynak dosyadaki başlangıç satır sayısı.|  
|**Çağrı sayısı**|Bu işlev veya modül yapılan çağrılar toplam sayısı.|  
|**Kaynak dosya**|Bu işlev tanımını içeren kaynak dosyası.|  
|**Modül adı**|İşlevi içeren modülü adı.|  
|**Modül yolu**|İşlevi içeren modülü yolu.|  
|**İşlem kimliği**|İşlemi çalıştırmak profil oluşturma kimliği (PID).|  
|**İşlem adı**|İçinde modül veya işlevi yürütülmekte olan işlemin adı.|  
|**Zaman özel araştırma ek yükü**|Bu işlev veya modül nedeniyle araçları için ek yükü süresi.|  
|**Zaman dahil araştırması ek yükü**|Bu işlev veya modül ve araçları nedeniyle alt işlevleri için ek yükü süresi.|  
  
## <a name="net-memory-values"></a>.NET bellek değerleri  
 Bir işlevin dahil .NET bellek değerleri sayısını (ayırmaları) ve boyutunu (bayt) işlevi ve onun alt işlevleri tarafından oluşturulan nesneleri gösterir.  
  
 Özel bellek değerleri sayısını ve boyutunu işlevi tarafından ve onun alt işlevleri tarafından oluşturulan nesneleri gösterir.  
  
 (Bunlar dahil) ve özel bellek modülün dahil toplamı ve özel bellek değerleri modüldeki işlevlerin değerlerdir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Kapsayıcı ayırmaları**|-Bir işlev için işlev tarafından oluşturulan nesneleri toplam sayısı. Bu işlev tarafından çağrılan işlevler tarafından oluşturulan nesneleri içerir.<br />-Modül en az bir işlev yürütülürken bir modül için bir profil çalışmasını nesne sayısı ayrılan. Bu sayı, modül işlevlerine gelen çağrıları tarafından oluşturulan işlevlerinde ayrılan nesneleri içerir.|  
|**Kapsayıcı ayırmaları %**|Profil çalışmasını ayrılan tüm nesneleri yüzdesi modülü ya da işlevin kapsayıcı ayırmaları yoktu.|  
|**Özel ayırmaları**|-Bir işlev, işlev kodunu işlev gövdesine yürütülmekte olan yükleyen oluşturulan nesne sayısı için (diğer bir deyişle, ne zaman işlevi çağrı yığını üstünde olduğu). Bu sayı işlev tarafından adı veriliyordu işlevlerinde oluşturulan nesneleri içermez.<br />-Bir modül için özel ayırmaları modülündeki işlevlerin toplamı.|  
|**Özel ayırmaları %**|Profil çalışmasını ayrılan tüm nesneleri yüzdesi modülü ya da işlevin özel ayırmaları yoktu.|  
|**Özel bayt sayısı**|-(Diğer bir deyişle, işlev çağrı yığını üstünde olduğu zaman) için bir işlev, işlev kodunu işlevinde yürütülmekte olan yükleyen ayrılan belleğin bayt sayısı toplam gövde. Bu sayı, işlevin adı veriliyordu işlevlerinde ayrılan bayt içermez.<br />-Bir modül için modülündeki işlevler tarafından ayrılan özel bayt toplamını.|  
|**Özel bayt %**|Profil çalışmasını ayrılan tüm bayt yüzdesi modülü, işlev, satır veya yönerge özel bayt yoktu.|  
|**Kapsayıcı bayt**|-Bir işlev için işlev tarafından ayrılan bayt sayısı. Bu sayı, işlevin adı veriliyordu işlevlerinde ayrılan bayt içerir.<br />-Modül en az bir işlev yürütülürken bir modül için bir çalışmasını profil ayrılan bayt sayısı ayrılan. Bu sayı modül işlevleri tarafından adı veriliyordu tüm işlevlerinde oluşturulan nesneleri içerir.|  
|**Kapsayıcı bayt %**|Profil çalışmasını ayrılan tüm bayt yüzdesi modülü ya da işlevin kapsayıcı bayt yoktu.|  
  
## <a name="elapsed-inclusive-values"></a>Geçen dahil değerleri  
 Çağrı yığınındaki bir işlevi olan süresi geçen dahil değerleri gösterir. Zaman harcanan zamanın alt işlevleri ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarını içerir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen dahil süre**|-Bir işlev için işlevinde harcanan süre. Bu alt işlevlerinde ve bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içerir.<br />-Bir modül için en az bir işlev modülü çağrı yığınındaki olduğu süre.|  
|**Geçen dahil süre %**|Çalıştıran profil oluşturma toplam geçen dahil toplam geçen dahil zaman bu modülü veya işlevi için harcanan sürenin yüzdesi.|  
|**Ortalama dahil geçen zaman**|-Bir işlev için ortalama bu işlev çağrısının dahil zaman geçti.<br />-Bir modül için ortalama işlevleri modülünde yapılan tüm çağrıların dahil süre geçti.|  
|**Max geçen dahil süre**|-Bir işlev için en fazla bu işlev çağrısının dahil zaman geçti.<br />-Bir modül için en fazla modül işlevlerde yapılan tüm çağrıların dahil süre geçti.|  
|**Min (bunlar dahil) geçen zaman**|-Bir işlev için en düşük bu modülü veya işlev çağrısının dahil zaman geçti.<br />-Bir modül için en düşük işlevleri modülünde yapılan tüm çağrıların dahil süre geçti.|  
  
## <a name="elapsed-exclusive-values"></a>Geçen özel değerler  
 Bir işlev, doğrudan çağrı yığını üstünde yürütme süresi geçen özel değerleri gösterir. Zaman zaman bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içerir ancak harcanan zamanın alt işlevlerde içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Geçen özel süre**|-Bir işlev için modüle ya da işlevi harcanan süre. Bu bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları içerir ancak alt işlevlerde geçen zamanı dışlar.<br />-İçin modül, modül işlevlerde özel sürelerinin toplamını geçti.|  
|**Özel geçen süre %**|Çalıştıran profil oluşturma toplam geçen özel toplam geçen özel zaman bu modülü veya işlevi için harcanan sürenin yüzdesi.|  
|**Ortalama özel geçen zaman**|-Bir işlev için ortalama bu işlev çağrısının özel zaman geçti.<br />-Bir modül için ortalama işlevleri modülünde yapılan tüm çağrıların özel zaman geçti.|  
|**Max geçen özel süre**|-Bir işlev için en fazla bu işlev çağrısının özel zaman geçti.<br />-Bir modül için en fazla modül işlevlerde yapılan tüm çağrıların özel zaman geçti.|  
|**Min özel geçen zaman**|-Bir işlev için en düşük bu modülü veya işlev çağrısının özel zaman geçti.<br />-Bir modül için en düşük işlevleri modülünde yapılan tüm çağrıların özel zaman geçti.|  
  
## <a name="application-inclusive-values"></a>Uygulama (bunlar dahil) değerleri  
 Uygulama dahil değerler çağrı yığınındaki bir işlevi olan süreyi belirtir. Süresi bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrılarında harcanan zamanın içermez ancak alt işlevlerde harcanan zamanın içermez.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama dahil süresi**|-Bir işlev için işlev çağrılarında harcanan süre. Bu alt işlevlerde geçen süre, ancak İçerik Geçişi ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları dışlar saati içerir.<br />-Bir modül için en az bir işlev modülü işletim sistemi çağrılarında harcanan zamanın hariç olmak üzere çağrı yığınında olduğu süre.|  
|**Uygulama dahil süresi %**|Bu modül ya da işlevin uygulama dahil süresi içinde harcandığını profil Çalıştır toplam geçen dahil süre yüzdesi.|  
|**Ortalama uygulama dahil süresi**|-Bir işlev için bu işlevi çağrısı, ortalama uygulama dahil süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların ortalama uygulama dahil süresi.|  
|**En fazla uygulama dahil süresi**|-Bir işlev için bu işlevi çağrısı, en fazla uygulama dahil süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların en fazla uygulama dahil süresi.|  
|**Min uygulama dahil süresi**|-Bir işlev için bu modülü veya işlev çağrısının minimum uygulama dahil süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların en az uygulama dahil süresi.|  
  
## <a name="application-exclusive-values"></a>Uygulama özel değerler  
 Uygulama özel değerleri modüldeki veya alt işlevlerde geçen zaman hariç işlev harcanan zamanı gösterir. Belirtilen zaman da bağlam anahtarlarının ve girdi/çıktı işlemleri gibi işletim sistemi çağrıları dışlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Uygulama özel süresi**|-Bir işlev için bu işlev çağrıları toplam uygulama özel süre.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların toplam uygulama özel süresi.|  
|**Uygulama özel süresi %**|Bu modül ya da işlevin uygulama özel süresi içinde harcandığını profil Çalıştır toplam geçen özel zaman yüzdesi.|  
|**Ortalama uygulama özel süresi**|-Bir işlev için bu işlevi çağrısı, ortalama uygulama özel süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların ortalama uygulama özel süresi.|  
|**En fazla uygulama özel süresi**|-Bir işlev için bu işlevi çağrısı, en fazla uygulama özel süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların en fazla uygulama özel süresi.|  
|**Min uygulama özel süresi**|-Bir işlev için bu modülü veya işlev çağrısının minimum uygulama özel süresi.<br />-Bir modül için işlevleri modülünde yapılan tüm çağrıların en az uygulama özel süresi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Modüller görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü](../profiling/modules-view-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-sampling-data.md)