---
title: Profıler_heap_object_scope_lıst yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796445"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST Yapısı
Bu yapı, yalnızca işlev nesneleri ile ilişkilidir. Kapsam listesinden Kapatılmak üzere işlevi kapsamların her kapsam her verilen kapsam değişkenleri temsil eden bir ilişkili özellik listesini yığın nesnesiyle olduğu bir liste olarak temsil eder. Bazı durumlarda, kapsam kullanılamayabilir nesneleri ve özellik listesi yalnızca kendi dizine adları kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|count|UINT|Kapsam sayısı|  
|kapsamlar|[Profıler_heap_object_ıd türü](../../winscript/reference/profiler-heap-object-id-type.md)|Kapsamları dizisi.|