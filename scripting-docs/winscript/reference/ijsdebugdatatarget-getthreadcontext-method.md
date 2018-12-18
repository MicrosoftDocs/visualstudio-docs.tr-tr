---
title: Ijsdebugdatatarget::getthreadcontext yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794609"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext Metodu
İş parçacığı alır bağlamının verilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Hedef işlemde çalışan iş parçacığı.  
  
 `contextFlags`  
 [in] Bağlam bayrakları belirtir. Bu bağlam ContextFlags alan (daha fazla bilgi için bkz: winnt.h CONTEXT_ALL arayın) ile aynı olur.  
  
 `contextSize`  
 [in] PContext tarafından belirtilen arabellek boyutu.  
  
 `pContext`  
 [out] Platforma özgü içerik yapısı pContext tarafından belirtilen arabellek içine alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugdatatarget arabirimi](../../winscript/reference/ijsdebugdatatarget-interface.md)