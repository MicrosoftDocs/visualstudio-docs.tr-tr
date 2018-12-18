---
title: Iactivescriptprofilerheapenum::getoptionalınfo yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793499"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo Metodu
Belirtilen nesne üzerindeki isteğe bağlı bilgileri alır (döndürülen yığın nesneler kümesinden [Iactivescriptprofilercontrol3::enumheap yöntemi](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Döndürülen nesnelerin atanan döndürülen bellek boş değil. Bunun yerine, çağırmalıdır [Iactivescriptprofilerheapenum::freeobjectandoptionalınfo yöntemi](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `heapObject`  
 [Profıler_heap_object yapısı](../../winscript/reference/profiler-heap-object-structure.md) ilişkin bilgiler.  
  
 `celt`  
 Sayısı [profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md) yapıları dönün.  
  
 `optionalInfo`  
 [out] Bir dizi [profıler_heap_object_optıonal_ınfo yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md) yapıları için belirtilen nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT.