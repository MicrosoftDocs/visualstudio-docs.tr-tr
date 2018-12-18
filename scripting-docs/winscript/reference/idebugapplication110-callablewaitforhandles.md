---
title: IDebugApplication110::CallableWaitForHandles | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793760"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Herhangi bir yandan bildirilmesini belirtilen tanıtıcıları bekler bu iş parçacığına gönderilen çağrıları iş parçacıkları arası. Bu yöntem, hata ayıklayıcı iş parçacığından çağrılmalıdır.  
  
> [!IMPORTANT]
>  [Idebugapplication110 arabirimi](../../winscript/reference/idebugapplication110-interface.md) PDM v11.0 tarafından uygulanan ve büyük. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `handleCount`  
 Bekleme tanıtıcıları sayısı.  
  
 `pHandles`  
 Bekleme tanıtıcıları kümesi.  
  
 `pIndex`  
 HRESULT değeri S_OK, dizine olduğunda `pHandles` işaret tutamacı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplication110 arabirimi](../../winscript/reference/idebugapplication110-interface.md)