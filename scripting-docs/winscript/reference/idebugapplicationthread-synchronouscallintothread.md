---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794093"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Çağıran kodu uygulama iş parçacığında çalıştırmak için bir mekanizma sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstcb`  
 [in] Çağrı yapılacak nesne.  
  
 `dwParam1`  
 [in] Geçirilecek ilk parametre `IDebugThreadCall::ThreadCallHandler` yöntemi.  
  
 `dwParam2`  
 [in] Geçirilecek ikinci parametre `IDebugThreadCall::ThreadCallHandler` yöntemi.  
  
 `dwParam3`  
 [in] Geçirilecek üçüncü parametre `IDebugThreadCall::ThreadCallHandler` yöntemi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu metodu çağıran kodu hata ayıklayıcı iş parçacığında çalıştırmak için bir mekanizma sağlar. Genellikle dil motorları ve ana ücretsiz iş parçacıklı nesneler kendi tek iş parçacıklı uygulamalarını üstünde uygulamak için bu yöntemi kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplicationthread arabirimi](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Idebugthreadcall arabirimi](../../winscript/reference/idebugthreadcall-interface.md)