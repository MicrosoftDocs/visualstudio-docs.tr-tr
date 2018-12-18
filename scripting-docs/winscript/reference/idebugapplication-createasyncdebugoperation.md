---
title: IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793814"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Belirtilen zaman uyumlu hata ayıklama işlemi zaman uyumsuz erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `psdo`  
 [in] Zaman uyumlu hata ayıklama işlemi nesnesi.  
  
 `ppado`  
 [out] Zaman uyumsuz hata ayıklama işlemi nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem açıkça hata ayıklayıcı iş parçacığı ile Eşitleme yapmadan ifadeleri zaman uyumsuz olarak değerlendirilecek dil altyapısı sağlar. Daha fazla bilgi için bkz: [Idebugsyncoperation arabirimi](../../winscript/reference/idebugsyncoperation-interface.md) ve [Idebugasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [Idebugsyncoperation arabirimi](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Idebugasyncoperation arabirimi](../../winscript/reference/idebugasyncoperation-interface.md)