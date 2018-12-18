---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794291"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Kullanarak eklenen karakter aralığı döndürür `IDebugDocumentHelper::AddDeferredText` özgün ana belgedeki yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwTextStartCookie`  
 [in] Metnin başlangıç konumunu temsil eden ana bilgisayar tarafından tanımlanan tanımlama bilgisi.  
  
 `pcharText`  
 [içinde out] Bir karakterin metin arabelleği. Bu parametre ise bu yöntem karakter döndürmüyor `NULL`.  
  
 `pstaTextAttr`  
 [içinde out] Karakter özniteliği arabellek. Bu parametre ise bu yöntem öznitelikleri döndürmüyor `NULL`.  
  
 `pcNumChars`  
 [içinde out] Döndürülen karakter/özniteliklerinin gerçek sayısını gösterir. Bu parametre, bu yöntemi çağırmadan önce sıfır olarak ayarlanması gerekir.  
  
 `cMaxChars`  
 [in] Döndürülecek karakterlerin sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Yöntem uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem döndürebilir `E_NOTIMPL`, ana bilgisayar arama `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Bu yöntem, özgün belgeden metni döndürür. Ana bilgisayar düzenlemeler veya belgeye diğer değişiklikleri izlemek değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenthost arabirimi](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR numaralandırması](../../winscript/reference/source-text-attr-enumeration.md)