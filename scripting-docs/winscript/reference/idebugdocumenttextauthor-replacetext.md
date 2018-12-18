---
title: IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa7ef34d035ad89a096414c285b4f66a4f4fa1e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794165"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Belgedeki metin yerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 [in] Konumu değiştirmek için karakter aralığının başlatın.  
  
 `cNumToReplace`  
 [in] Değiştirilecek karakterler sayısı.  
  
 `pcharText[]`  
 [in] Eski karakterlerini değiştirmek için yeni karakterler içeren bir arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem belgedeki metin değiştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenttextauthor arabirimi](../../winscript/reference/idebugdocumenttextauthor-interface.md)