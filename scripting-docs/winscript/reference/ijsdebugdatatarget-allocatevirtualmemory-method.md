---
title: Ijsdebugdatatarget::allocatevirtualmemory yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794675"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory Yöntemi
Ayırır ve/veya hedef işleminin sanal adres alanı içinde bellek bölgesi kaydeder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] Bellek burada kaydedilmiş veya ayrılmış hedef işlem dahilinde adresi. Bu değer genellikle sistem durumu bir adresi seçer, sıfırdır.  
  
 `size`  
 [in] Bayt cinsinden ayrılacak bellek bölgesi boyutu. Sistem otomatik olarak sonraki sayfa sınır yukarı yuvarlar.  
  
 `allocationType`  
 [in] Gerçekleştirmek için ayırma türünü belirtir. Bu genellikle MEM_COMMIT &#124;olur; Ayırır ve tek bir adımda bir ayırma tamamlar MEM_RESERVE (0x3000).  
  
 `pageProtection`  
 [in] Bölge için bellek koruma ayrılması sayfaların. Sayfaları kaydedilmiş, bellek koruma Sabitleri (örneğin, PAGE_READWRITE, PAGE_EXECUTE) herhangi birini belirtebilirsiniz.  
  
 `pAllocatedAddress`  
 [out] Ayrılmış bölge sayfaların temel adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 MEM_RESET kullanılmadığı sürece işlevi sıfır olarak ayırır bellek başlatır. VirtualAlloc Win32 API ek bilgi için bkz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)