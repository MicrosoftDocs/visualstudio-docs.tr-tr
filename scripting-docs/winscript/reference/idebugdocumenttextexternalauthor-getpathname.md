---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794477"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Belgenin tam yolunu ve dosya adını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbstrLongName`  
 [out] Tam yol ve dosya adını içeren dize.  
  
 `pfIsOriginalFile`  
 [out] Yol ve dosya adı bakın, belirten Boole değeri için özgün belgeye.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Kaynak dosya oluşturulamıyor veya belirledi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belgenin tam yolunu ve dosya adını döndürür.  
  
 Varsa `pfIsOriginalFile` FALSE, yol ve dosya adında `pbstrLongName` yeni oluşturulan bir geçici dosyasına bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenttextexternalauthor arabirimi](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)