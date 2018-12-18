---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793997"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Engellemek geçerli iş parçacığının neden olur ve IDE hata ayıklayıcı kesme noktası bir bildirim gönderir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `br`  
 [in] Break nedeni.  
  
 `pbra`  
 [out] Hata ayıklayıcı uygulama çıktığında yapılacak eylem.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dil alt yapısı bir kesme noktası isabet bir iş parçacığı bağlamında bu yöntemi çağırır. Bu yöntem, geçerli iş parçacığının engeller ve IDE hata ayıklayıcı bir kesme noktası bildirim gönderir. Hata ayıklayıcı uygulama çıktığında `pbra` parametresi, hangi eylemin yapılacağını belirtir.  
  
> [!NOTE]
>  Dil altyapısı yığını listeleme gibi çerçeveleri veya kesme sırasında ifadeleri değerlendirme görevleri gerçekleştirmek için iş parçacığı tarafından çağrılabilir.  
  
 Bu yöntem neden `IApplicationDebugger::onHandleBreakPoint` çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON numaralandırması](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION numaralandırması](../../winscript/reference/breakresumeaction-enumeration.md)