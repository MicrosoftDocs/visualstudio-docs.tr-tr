---
title: Profıler_heap_object_relatıonshıp_flags numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796358"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS Numaralandırması
Bir yığın nesnesi bir nesne ilişkisinde işaret olup olmadığını temsil eden bayrakları bir alıcı veya ayarlayıcı yöntemidir. Kullanılan [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) profıler_heap_object_relatıonshıp_flags değeri belirtildiğinde yöntemi `enumFlags` parametresi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Bir nesne ilişkisinde işaret Bu yığın nesnesi bir alıcı veya ayarlayıcı yöntemi olarak tanımlanamadı.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Bir nesne ilişkisinde işaret yığın nesnesi bir alıcı yöntemidir. Bu bilgiler, yüksek 2 bayt (16 bit) depolanacak [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) alan.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Bir nesne ilişkisinde işaret yığın nesnesi ayarlayıcı yöntemidir. Bu bilgiler, yüksek 2 bayt (16 bit) depolanacak `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` alan.|