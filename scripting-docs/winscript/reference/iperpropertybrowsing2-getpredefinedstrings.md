---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915974"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Bu özellik için olası değeri temsil eden dize işaretçilerini sayılan bir dizi liste kutusunu doldurmak çağıranın izin verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dispid`  
 [in] Çağıranın dize listesi isteyen özellik tanımlayıcısı gönderme.  
  
 `pCaStrings`  
 [out] Öğe sayısı ve dize işaretçilerini yöntemi olarak ayrılan dizi adresini içeren sayılan, arayana ayrılan dizi yapısı işaretçisi. Yöntem başarısız olursa, bellek tahsis edilir ve yapısı içeriğini tanımsızdır.  
  
 `pCaCookies`  
 [out] Öğe sayısı ve DWORD yöntemi olarak ayrılan dizi adresini içeren sayılan, arayana ayrılan dizi yapısı işaretçisi. Yöntem başarısız olursa, bellek tahsis edilir ve yapısı içeriğini tanımsızdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Geçerli bir döndürür `HRESULT`, genellikle `S_OK`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IPerPropertyBrowsing2 Arabirimi 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)