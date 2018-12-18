---
title: IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794255"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Yardımcıya belirli bir aralıktaki karakterleri verilen betik altyapısı tarafından işlenen bir betik bloğu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ulCharOffset`  
 [in] Betik bloğu başlangıç konumu.  
  
 `cChars`  
 [in] Betik bloğundaki karakter sayısı.  
  
 `pas`  
 [in] Bu komut dosyası bloğunda komut dosyası altyapısı.  
  
 `fScriptlet`  
 [in] Betik bloğundaki bir kod parçacığı olup olmadığını belirten bayrak.  
  
 `pdwSourceContext`  
 [out] Betik bloğu için kaynak bağlamı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kendi belgeleri katıştırılmış komut dosyası blokları içerdiğinde bir akıllı ana bilgisayar bu yöntemi kullanabilirsiniz. Diğer diller için katıştırılmış betikler kendi kod içerdiğinde, bir dil altyapısı bu yöntemi kullanabilirsiniz.  
  
 Betik altyapısı, tüm söz dizimi renklendirme ve kod bağlam aramaları için betik bloğundaki sorumludur.  
  
 `DefineScriptBlock` Metin eklendikten sonra yöntemi'nin çağrılabilir (örneğin, kullanarak `IDebugDocumentHelper::AddDBCSText` yöntemi) ancak önce betik bloğu Ayrıştırılan (örneğin, kullanarak `IActiveScriptParse ::ParseScriptText` yöntemi).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugdocumenthelper arabirimi](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)