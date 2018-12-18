---
title: Profıler_heap_enum_flags numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796388"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS Numaralandırması
Yığın nesnesi hakkında ek bilgi için bir nesne ilişkisinde işaret olup olmadığını temsil eden bayrakları açıktır. Kullanılan [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Bu yığın nesne bir nesne ilişkileri hakkında ek bilgi göstermiyor. Bu yığın nesnesi ile aynı şekilde davranır [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Bu yığın nesne bir nesne ilişkisinde işaret bir nesne bir alıcı veya ayarlayıcı yöntemi olup olmadığına olduğu hakkında bilgi açığa çıkarır. Bu bilgiler, yüksek 2 bayt (16 bit) depolanacak [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) biri olarak alan [profıler_heap_object_relatıonshıp_flags](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) numaralandırma değerleri.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Bu yığın nesne alt dizeyi düzgün görüntülemek için kullanılır.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Bu yığın nesne alt dizeyi düzgün görüntülemek için kullanılır.|