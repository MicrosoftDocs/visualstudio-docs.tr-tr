---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794633"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Devam eden başka bir iş parçacığı üzerinde bir işlemi iptal eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|İşlem iptal edilemez.|  
|`E_ABORT`|İşlem tamamlanamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama işlemi Yöneticisi başka bir iş parçacığında devam ediyor bir işlemi iptal etmek için hata ayıklayıcı iş parçacığı içinde bu yöntemi çağırır.  
  
 Varsa `InProgressAbort` yöntemi işlemini tamamlayamıyor, döndürür `E_ABORT` mümkün olan en kısa sürede. Bu yöntem döndürebilir `E_NOTIMPL` işlemi iptal edilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugsyncoperation arabirimi](../../winscript/reference/idebugsyncoperation-interface.md)