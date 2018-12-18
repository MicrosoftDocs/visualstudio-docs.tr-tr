---
title: Ijsdebugdatatarget::readmemory yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794705"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory Yöntemi
Hedef işlemin bellek okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] Hedef işlemin bellek okunacak temel adres.  
  
 `flags`  
 [in] ReadMemory davranışını denetleme bayraklar.  
  
 `pBuffer`  
 [out] Hedef işlemin adres alanından içeriği alır arabelleği. Üzerinde bu arabellek içeriğini belirtilmeyen hatasıdır.  
  
 `size`  
 [in] İşlemden okunacak bayt sayısı.  
  
 `pBytesRead`  
 [out] Hedef işleminden okunan bayt sayısını gösterir. Başarı JsDebugAllowPartialRead boş olduğunda, bu değer her zaman tam olarak giriş boyutuna eşit olacaktır. JsDebugAllowPartialRead belirtilmişse, başarı, bu değer sıfırdan büyük olacaktır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Başarı ve hata kodlarını döndürür S_OK herhangi bir hata için kullanılır. Adres geçerli değilse E_JsDEBUG_INVALID_MEMORY_ADDRESS döndürür. Daha fazla bilgi için JsDebugAllowPartialRead bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)