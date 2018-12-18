---
title: Iactivescriptprofilercontrol3::enumheap yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793454"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap Yöntemi
Arabirim döndürür ([Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) ilişkili betik altyapısı bağlamında GC yığın nesneleri üzerinden yinelemek için kullanılabilecek.  
  
 Toolkit ya da ya da hata ayıklama modunda bu yöntemi çağırın. Kullanıcı Arabirimi iş parçacığı boşta olduğunda bu yöntem çağrılmalıdır. Betik altyapısı dışında karşı yöntemi çağrıldıktan sonra hiçbir işlem gerçekleştirilmelidir [Iactivescriptprofilerheapenum::Next yöntemi](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) kadar [Iactivescriptprofilerheapenum::Next yöntemi](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)S_FALSE döndürür veya [Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) arabirim işaretçisi yayımlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 ppEnum  
 [out] Döndürür [Iactivescriptprofilerheapenum arabirimi](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT.