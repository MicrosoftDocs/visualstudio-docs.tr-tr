---
title: IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57b76f44eeeaad1946d40435c770b0687b82fd17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793742"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Kullanıcı arabirimi hata ayıklayıcı üst belirtilen hata ayıklama belgeye içeren pencere getirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pddt`  
 [in] Hata ayıklayıcı kullanıcı arabiriminde en çok getirmek için belge hata ayıklama.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_INVALIDARG`|Belge bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, kullanıcı arabirimi hata ayıklayıcı üst belirtilen hata ayıklama belgeye içeren pencere getirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iapplicationdebuggeruı arabirimi](../../winscript/reference/iapplicationdebuggerui-interface.md)