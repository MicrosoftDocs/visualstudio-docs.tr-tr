---
title: Profıler_heap_object yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796520"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT Yapısı
Yığın nesneleri toplanan tarafından temsil [Iactivescriptprofilercontrol3::enumheap yöntemi](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|objectID|[Profıler_heap_object_ıd türü](../../winscript/reference/profiler-heap-object-id-type.md)|Yığın nesnesi kimliği.|  
|externalObjectAddress|[Profıler_external_object_address türü](../../winscript/reference/profiler-external-object-address-type.md)|JavaScript yığın dışında bir C++ ayrılmış bir nesne gibi bir nesne dış nesne adresi.|  
|typeNameId|[Profıler_heap_object_name_ıd türü](../../winscript/reference/profiler-heap-object-name-id-type.md)|Yığın nesnesi türü adı Kimliğini alınan [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Yalnızca tek bir `externalObjectAddress` veya `typeName` bağlı olarak mevcut `flags` değeri.|  
|bayraklar|[Profıler_heap_object_flags numaralandırması](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Yığın nesnesi ile ilgili temel bilgileri içeren bayraklar.|  
|optionalInfoCount|USHORT|Sayısı [profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md) yığın nesne için kullanılabilen kaydeder.|