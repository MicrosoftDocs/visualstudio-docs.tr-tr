---
title: Etkin komut dosyası profil oluşturucu sabitleri, numaralandırmaları ve yapıları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792146"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Etkin Komut Dosyası Profil Oluşturucu Sabitleri, Numaralandırmaları ve Yapıları 
Aşağıdaki numaralandırmalar etkin komut dosyası profil oluşturucu arabirimleri tarafından kullanılır.  
  
## <a name="constants-enumerations-and-structures"></a>Sabitler, Listelemeler ve Yapılar  
  
|Sabitler|Açıklama|  
|---------------|-----------------|  
|[Profıler_external_object_address türü](../../winscript/reference/profiler-external-object-address-type.md)|Profil Oluşturucu dış nesne adresi. Kullanılan [profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md) ve [profıler_heap_object_relatıonshıp yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Profıler_heap_object_ıd türü](../../winscript/reference/profiler-heap-object-id-type.md)|Yığın nesnesi kimliği. Kullanılan [profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md)[profıler_heap_object_scope_lıst yapısı](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md)ve [Profıler_heap_object_relatıonshıp yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Profıler_heap_object_name_ıd türü](../../winscript/reference/profiler-heap-object-name-id-type.md)|Yığın nesnesinin adını kimliği. Kullanılan [profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Numaralandırmalar|Açıklama|  
|------------------|-----------------|  
|[Profıler_event_mask numaralandırması](../../winscript/reference/profiler-event-mask-enumeration.md)|Profili olay türlerini belirtir.|  
|[Profıler_heap_enum_flags numaralandırması](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Yığın nesnesi hakkında ek bilgi için bir nesne ilişkisinde işaret olup olmadığını temsil eden bayrakları açıktır. Kullanılan [Iactivescriptprofilercontrol5::enumheap2 yöntemi](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Profıler_heap_object_flags numaralandırması](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Yığın nesnesi ile ilgili temel bilgileri temsil eden bayraklar. Kullanılan [profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Profıler_heap_object_optıonal_ınfo_type numaralandırması](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Farklı türde isteğe bağlı bilgileri temsil eder. Kullanılan [profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Profıler_relatıonshıp_ınfo numaralandırması](../../winscript/reference/profiler-relationship-info-enumeration.md)|İlişki nesnesinde ilgili bilgileri temsil eder. Kullanılan [profıler_heap_object_relatıonshıp yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Profıler_scrıpt_type numaralandırması](../../winscript/reference/profiler-script-type-enumeration.md)|Betik türünü belirtir.|  
  
|Yapılar|Açıklama|  
|----------------|-----------------|  
|[Profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md)|Yığın nesneleri toplanan tarafından temsil [Iactivescriptprofilercontrol3::enumheap yöntemi](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Yığın nesneler hakkında isteğe bağlı bilgileri temsil eder.|  
|[Profıler_heap_object_relatıonshıp yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Bir yığın nesnesinin bir ilişkiyi temsil eder.|  
|[Profıler_heap_object_relatıonshıp_lıst yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Bir yığın nesnesine ait ilişki listesini temsil eder.|  
|[Profıler_heap_object_scope_lıst yapısı](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Bu yapı, yalnızca işlev nesneleri ile ilişkilidir. Kapsam listesinden Kapatılmak üzere işlevi kapsamların her kapsam her verilen kapsam değişkenleri temsil eden bir ilişkili özellik listesini yığın nesnesiyle olduğu bir liste olarak temsil eder. Bazı durumlarda bu kapsamda nesnelerin adları, kullanılamayabilir yalnızca kimlikleri.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO yapısı](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Alt dizeyi türüyle ilgili bilgileri temsil eder.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası profil oluşturucu arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)