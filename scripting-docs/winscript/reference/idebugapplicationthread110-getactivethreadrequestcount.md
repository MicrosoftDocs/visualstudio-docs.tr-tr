---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794039"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
İş parçacığı isteği sayısı, şu anda işlenmekte olan mekanizmaları geçiş PDM'ın iş parçacığından döndürür. Bu sayı genellikle 0 veya 1 ' dir. Bir iş parçacığı çağrı işlemeye başlıyor ancak, iş parçacığı dışında bir zaman uyumlu çağrıyı tetikler veya aksi halde iş parçacığı askıya alır ve yeniden işlenmek üzere gelen çağrıları sağlar ancak sayı daha yüksek olabilir (örneğin, tetikleme tarafından bir [ Iremotedebugapplicationevents arabirimi](../../winscript/reference/iremotedebugapplicationevents-interface.md) hata ayıklayıcı iş parçacığı üzerinde yayınlanan olay).  
  
> [!IMPORTANT]
>  [Idebugapplicationthread110 arabirimi](../../winscript/reference/idebugapplicationthread110-interface.md) PDM v11.0 tarafından uygulanan ve büyük. activdbg100.h içinde bulunur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `puiThreadRequests`  
 [out] İş parçacığı istek sayısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplicationthread110 arabirimi](../../winscript/reference/idebugapplicationthread110-interface.md)