---
title: Ijsdebugframe arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795038"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame Arabirimi
Bir yığın çerçevesini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[Ijsdebugframe::evaluate yöntemi](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Bu yığını çerçevesi bağlamında bir ifadenin değerlendirin.|  
|[Ijsdebugframe::getdebugproperty yöntemi](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Özellik tarayıcısı Bu yığın çerçevesi için döndürür.|  
|[Ijsdebugframe::getdocumentpositionwithıd yöntemi](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Bu kullanıcı düzeyinde belge yığın çerçevesinde geçerli konumunu döndürür.|  
|[Ijsdebugframe::getdocumentpositionwithname yöntemi](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Bu kullanıcı düzeyinde belge yığın çerçevesinde geçerli konumunu döndürür.|  
|[Ijsdebugframe::GetName yöntemi](../../winscript/reference/ijsdebugframe-getname-method.md)|Yığın çerçevesi kolay kullanılan adını alır.|  
|[Ijsdebugframe::getreturnaddress yöntemi](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|'Start' itildiği dönüş adresi alır (GetStackRange bakın) çerçeve.|  
|[Ijsdebugframe::getstackrange yöntemi](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Mantıksal JavaScript yığın çerçevesi mutlak bir adres aralığını döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)