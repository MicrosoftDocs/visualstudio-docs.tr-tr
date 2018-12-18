---
title: Ijsdebugdatatarget::gettlsvalue yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794519"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue Metodu
Ayıklanacak iş parçacığı, iş parçacığı yerel depolaması (TLS) yuvasındaki belirtilen TLS dizin değeri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Okunacak hedef işlemde çalışan iş parçacığı.  
  
 `tlsIndex`  
 [in] Hedef işlemin TlsAlloc işlevi çağrıldığında ayrıldı TLS dizini.  
  
 `pValue`  
 [out] İş parçacığının TLS yuvasında saklanan işaretçi ölçekli değeri. Hedef iş parçacığı 32 bit ise, bu değer üst 32-bit sıfır olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Her iş parçacığı bir işlemin her TLS dizin için kendi yuva vardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)