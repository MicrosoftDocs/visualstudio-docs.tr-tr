---
title: Iactivescriptprofilercontrol5::enumheap2 yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793493"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 Yöntemi
Arabirim döndürür ([Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) ilişkili betik altyapısı bağlamında GC yığın nesneleri üzerinden yinelemek için kullanılabilecek.  
  
 Toolkit ya da ya da hata ayıklama modunda bu yöntemi çağırın. Kullanıcı Arabirimi iş parçacığı boşta olduğunda bu yöntem çağrılmalıdır. Betik altyapısı dışında karşı yöntemi çağrıldıktan sonra hiçbir işlem gerçekleştirilmelidir [Iactivescriptprofilerheapenum::Next yöntemi](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) kadar [Iactivescriptprofilerheapenum::Next yöntemi](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)S_FALSE döndürür veya [Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) arabirim işaretçisi yayımlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 enumFlags  
 Bir nesne ilişkisinde işaret bir nesne hakkında ek bilgi sunulup sunulmadığını belirten değer. Ek bilgi işaret nesnesi bir alıcı veya ayarlayıcı yöntemi olup olmadığını gösterebilir. Daha fazla bilgi için bkz: [profıler_heap_enum_flags numaralandırması](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Döndürür [Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yığın numaralandırması başarıyla tamamlandı.|  
|`E_OUTOFMEMORY`|Yığın numaralandırması gerçekleştirmek yeterli bellek yoktu.|  
|`E_FAIL`|Bir iç hata oluştu.|