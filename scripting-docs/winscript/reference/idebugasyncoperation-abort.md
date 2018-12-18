---
title: IDebugAsyncOperation::Abort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 274f09ae2a8851b897a825c32f18091c2f4250d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793964"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Bir işlem iptal eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|S_OK|Yöntem başarılı oldu.|  
|E_NOTIMPL|İşlem iptal edilemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem genellikle bir yanıt işlemini iptal etmek için hata ayıklayıcı iş parçacığı içinde çağrılır. Bu yöntem neden `InProgressAbort` yöntemi `IDebugSyncOperation` çağrılacak nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)