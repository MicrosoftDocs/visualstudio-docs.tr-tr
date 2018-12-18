---
title: Ijsdebug::openvirtualprocess yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794363"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess Yöntemi
Yeni bir sanal işlemin nesnesi oluşturmak için kullanılan Üreteç yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `processId`  
 [in] Hata ayıklayıcısını için işlem kimliği'ni kullanın.  
  
 `runtimeJsBaseAddress`  
 [in] JavaScript çalışma zamanı hedef işlemine yükledi temel adres.  
  
 `pDataTarget`  
 [in] Hata ayıklayıcı, sorgu işleminin durumu için sağlanan arabirim.  
  
 `ppProcess`  
 [out] Yeni bir hata ayıklama işlemi nesnesi  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="remarks"></a>Açıklamalar  
 Jscript9diag ve Jscript9 eşleşmiyorsa E_JsDEBUG_MISMATCHED_RUNTIME döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebug arabirimi](../../winscript/reference/ijsdebug-interface.md)