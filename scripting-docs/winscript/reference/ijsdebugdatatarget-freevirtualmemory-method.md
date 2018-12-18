---
title: Ijsdebugdatatarget::FreeVirtualMemory yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794777"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory Yöntemi
Serbest bırakır ve/veya hedef işleminin sanal adres alanı içinde bellek bölgesi decommits.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] Bellek serbest burada hedef işlem içinde adres.  
  
 `size`  
 [in] Kaydettikleri bayt sayısı. Bir bölge belleği serbest bırakmak için bu değer sıfır olmalıdır.  
  
 `freeType`  
 [in] Gerçekleştirmek için ücretsiz işlemi türünü belirtir. Bu genellikle sayfaların belirtilen bölge serbest MEM_RELEASE (0x8000) olur. İşleminden sonra sayfaları boş durumda. MEM_DECOMMIT (0x4000), bunun yerine, serbest bırakmadan sayfaları kaydettikleri için de kullanılabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 VirtualFree Win32 API ek bilgi için bkz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)