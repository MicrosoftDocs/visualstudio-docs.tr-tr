---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793439"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Geçerli belge sürümü benzersiz olarak tanımlayan ana bilgisayar tarafından tanımlanan bir dize alır. İlgili belge (Not Defteri ile düzenlenmekte olan HTML sayfası izlemesinde) Windows komut dosyası kapsamı dışında değiştiyse, komut dosyası altyapısı bu betiği yüklenen sonraki sefer yeniden derlemeye zorlama kalıcı durumunu birlikte kaydedebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrVersionString`  
 [out] Belge ana bilgisayar tarafından tanımlanan sürüm dizesi adresidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `S_OK` başarılı olursa ya da `E_NOTIMPL` bu yöntem desteklenmiyorsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `E_NOTIMPL` döndürülür, komut dosyası altyapısı varsayalım betik belgeyle eşit olduğunu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)