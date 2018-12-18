---
title: IDebugDocumentHelper::AddDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794717"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Verilen metni kullanılabilir, ancak karakterleri sağlamaz yardımcı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cChars`  
 [in] Eklemek için (Unicode) karakter sayısı.  
  
 `dwTextStartCookie`  
 [in] Metnin başlangıç konumunu temsil eden ana bilgisayar tarafından tanımlanan tanımlama bilgisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Yöntemi başarısız oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, doğru bildirimleri ve boyutu bilgileri oluşturmak yardımcıyı verirken gerekene kadar eklemek için karakterleri sağlama erteleme konak sağlar. `dwTextStartCookie` Metnin başlangıç konumunu temsil eden konak tarafından tanımlanan bir tanımlama bilgisi parametresidir. Sonraki çağrılar `IDebugDocumentText::GetText` bu tanımlama bilgisi sağlamanız gerekir. Örneğin, DBCS metinde temsil eden bir ana bilgisayar, tanımlama bilgisi bayt uzaklığı olabilir.  
  
 Varsayılır tek bir çağrı `IDebugDocumentText::GetText` karakterleri birden çok çağrılardan alabilirsiniz `AddDeferredText`. Yardımcı sınıfları ayrıca birden çok kez aynı ertelenmiş karakter aralığı için isteyebilir.  
  
> [!NOTE]
>  Çağrılar `AddDeferredText` çağrıları ile karma değil `AddUnicodeText` veya `AddDBCSText`. Bu gerçekleşirse, `E_FAIL` döndürülür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenthelper arabirimi](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)