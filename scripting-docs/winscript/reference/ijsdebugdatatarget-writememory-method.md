---
title: Ijsdebugdatatarget::writememory yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794525"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory Yöntemi
Hedef işlemin bellek okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] Hedef işlemin bellek yazmak üzere temel adres.  
  
 `pMemory`  
 [in] Belirtilen işlem adres alanında yazılacak veriler.  
  
 `size`  
 [in] İşleme yazılacak bayt sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Veri aktarımı oluşmadan önce sistem taban adresi ve belirtilen boyut bellek tüm verilerin yazma erişimi için erişilebilir olduğundan ve erişilebilir durumda değilse, işlevi E_JsDEBUG_INVALID_MEMORY_ADDRESS hata başlatır doğrular.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)