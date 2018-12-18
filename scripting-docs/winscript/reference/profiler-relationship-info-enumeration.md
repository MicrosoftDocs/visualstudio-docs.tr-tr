---
title: Profıler_relatıonshıp_ınfo numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796334"
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO Numaralandırması
İlişki nesnesinde ilgili bilgileri temsil eder. Kullanılan [profıler_heap_object_relatıonshıp yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Nesne bir sayıdır.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Nesne bir dizedir.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Bir yığın nesnesi nesnesidir.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Nesneyi başka bir deyişle, atık toplama yığında dış, değil.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|BSTR nesnesidir.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|Nesne bir alt dizesidir.|