---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794579"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Karakter ve/veya bir karakterin aralığı ile ilişkili karakter özniteliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cCharacterPosition`  
 [in] Karakter konumu aralık konumunu başlatın.  
  
 `pcharText`  
 [içinde out] Bir karakterin metin arabelleği. Arabellek tutmak için yeterince büyük `cMaxChars` karakter. Bu parametre NULL ise, yöntem karakter döndürmez.  
  
 `pstaTextAttr`  
 [içinde out] Karakter özniteliği arabellek. Arabellek tutmak için yeterince büyük `cMaxChars` karakter. Bu parametre NULL ise, yöntem öznitelikleri döndürmez.  
  
 `pcNumChars`  
 [içinde out] Döndürülen karakter/özniteliklerinin sayısı. Bu parametre, bu yöntemi çağırmadan önce sıfır olarak ayarlanması gerekir.  
  
 `cMaxChars`  
 [in] Karakter konumu aralık karakter sayısı. Ayrıca en fazla döndürülecek karakter sayısını belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem karakter ve/veya bir karakterin aralığı ile ilişkili karakter özniteliklerini alır. Karakter konumu aralık bir karakterin karakter sayısı ile belirtilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenttext arabirimi](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)