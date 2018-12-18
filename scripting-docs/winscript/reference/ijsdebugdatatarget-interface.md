---
title: Ijsdebugdatatarget arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794939"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget Arabirimi
Erişim ve hedef hata ayıklayıcı işlem durumunu değiştirmek için işlevselliği sağlamak için hata ayıklayıcı tarafından uygulanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[Ijsdebugdatatarget::allocatevirtualmemory yöntemi](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Ayırır ve/veya hedef işleminin sanal adres alanı içinde bellek bölgesi kaydeder.|  
|[Ijsdebugdatatarget::createstackframeenumerator yöntemi](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Yığın çerçeveleri için bir numaralandırıcı oluşturur.|  
|[Ijsdebugdatatarget::FreeVirtualMemory yöntemi](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Serbest bırakır ve/veya hedef işleminin sanal adres alanı içinde bellek bölgesi decommits.|  
|[Ijsdebugdatatarget::getthreadcontext yöntemi](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|İş parçacığı alır bağlamının verilir.|  
|[Ijsdebugdatatarget::gettlsvalue yöntemi](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Ayıklanacak iş parçacığı, iş parçacığı yerel depolaması (TLS) yuvasındaki belirtilen TLS dizin değeri alır.|  
|[Ijsdebugdatatarget::readbstr yöntemi](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|BSTR hata ayıklama hedefi okur.|  
|[Ijsdebugdatatarget::readmemory yöntemi](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Hedef işlemin bellek okur.|  
|[Ijsdebugdatatarget::readnullterminatedstring yöntemi](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Hedef belirtilen sayıda karakteri okur.|  
|[Ijsdebugdatatarget::writememory yöntemi](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Hedef işlemin bellek okur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)