---
title: Profıler_heap_object_optıonal_ınfo yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e231484b48bf2741281644c746b448fd6f657b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "24796364"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO Yapısı
Yığın nesneleri hakkında isteğe bağlı bilgileri temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|bilgi türü|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE Sabit Listesi](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|İsteğe bağlı bilgi türü.|  
|prototip|[PROFILER_HEAP_OBJECT_ID Türü](../../winscript/reference/profiler-heap-object-id-type.md)|Yığın nesnesinin prototipini nesnesinin kimliği.|  
|functionName|LPCWSTR|Yığın nesnesinin işlev adı.|  
|elementAttributesSize|UINT|Yığın nesnesinin öğesi özniteliklerini boyutu.|  
|elementTextChildrenSize|UINT|Yığın nesnesinin metin alt boyutu.|  
|KapsamListesi|[PROFILER_HEAP_OBJECT_SCOPE_LIST Yapısı](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Yığın nesnesinin kapsam listesi.|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP Yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Yığın nesnenin iç özellik.|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Yığın nesnesinin adı özelliklerin listesi.|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Yığın nesnesinin dizin özelliklerin listesi.|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Yığın nesnesinin ilişkileri listesi.|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Yığın nesnesinin olaylarının bir listesi.|