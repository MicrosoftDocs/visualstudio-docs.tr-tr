---
title: IDebugAsyncOperation::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793937"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Başlamak zaman uyumsuz işlemi neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `padocb`  
 Bu işlemden durum olaylarını alır geri çağırma arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_UNEXPECTED`|Bir işlem zaten beklemede.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem neden `IDebugSyncOperation::Execute` zaman uyumsuz olarak alınan iş parçacığında çağrılacak `IDebugSyncOperation::GetTargetThread`. Bu yöntem yalnızca hata ayıklayıcı iş parçacığının içinden çağrılmalıdır; Aksi takdirde, işlemi tamamlanana kadar bu döndürmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Idebugasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)