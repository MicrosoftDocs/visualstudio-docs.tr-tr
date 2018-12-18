---
title: IDebugDocumentHelper::Init | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794051"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` Yöntemi bir hata ayıklama belge yardımcı bir ad ve başlangıç özniteliklerini ile başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pda`  
 [in] Bu belgeyle ilgili hata ayıklama uygulama.  
  
 `pszShortName`  
 [in] Belgenin kısa adını içeren null ile sonlandırılmış bir dize.  
  
 `pszLongName`  
 [in] Belgenin uzun adını içeren null ile sonlandırılmış bir dize.  
  
 `docAttr`  
 [in] Metin belgesi özniteliklerini belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir ad ve başlangıç özniteliklerini ile hata ayıklama belge yardımcıyı başlatır.  
  
 Bu belge ağacında kadar görünmez `IDebugDocumentHelper::Attach` olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Idebugdocumenthelper arabirimi](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR sabitleri](../../winscript/reference/text-doc-attr-constants.md)