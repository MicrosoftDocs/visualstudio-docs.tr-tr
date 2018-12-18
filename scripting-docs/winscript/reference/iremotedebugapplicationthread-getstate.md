---
title: IRemoteDebugApplicationThread::GetState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795089"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Bu iş parçacığı durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pState`  
 [out] Aşağıdaki iş parçacığı durumu bayrakları birleşimi:  
  
|Sabit|Değer|Açıklama|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|İş parçacığı çalışıyor.|  
|THREAD_STATE_SUSPENDED|0x00000002|İş parçacığı askıya alınır.|  
|THREAD_BLOCKED|0x00000004|İş parçacığı engellendi.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|İş parçacığı dışında içeriktir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu iş parçacığı durumunu alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iremotedebugapplicationthread arabirimi](../../winscript/reference/iremotedebugapplicationthread-interface.md)