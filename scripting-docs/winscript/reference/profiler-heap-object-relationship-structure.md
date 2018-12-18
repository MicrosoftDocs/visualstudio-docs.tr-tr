---
title: Profıler_heap_object_relatıonshıp yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b992b020c0aa42a6f27e484d55fe89a514c0198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796418"
---
# <a name="profilerheapobjectrelationship-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP Yapısı
Bir yığın nesnesinin bir ilişkiyi temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|RelationshipID|[Profıler_heap_object_name_ıd türü](../../winscript/reference/profiler-heap-object-name-id-type.md)|İlişki kimliği ad alanından [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[Profıler_relatıonshıp_ınfo numaralandırması](../../winscript/reference/profiler-relationship-info-enumeration.md)|İlişki hakkında bilgi.|  
|numberValue|çift|Sayı değeri. Yalnızca tek bir `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` ayarlamak, temel `relationshipInfo` değeri.|  
|stringValue|LPCWSTR|Dize değeri.|  
|objectID|[Profıler_heap_object_ıd türü](../../winscript/reference/profiler-heap-object-id-type.md)|Yığın nesnesi kimliği.|  
|externalObjectAddress|[Profıler_external_object_address türü](../../winscript/reference/profiler-external-object-address-type.md)|Dış nesne adresi.|  
|subString|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO yapısı](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Substring türü hakkında bilgiler.|