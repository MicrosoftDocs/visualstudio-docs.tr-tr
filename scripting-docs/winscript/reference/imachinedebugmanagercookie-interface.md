---
title: Imachinedebugmanagercookie arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795041"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie Arabirimi
Benzer şekilde `IMachineDebugManager` arabirimi, `IMachineDebugManagerCookie` arabirimi hata ayıklama tanımlama bilgilerini destekler.  
  
 Bu arabirim (ile birlikte `IDebugCookie` arabirimi) betiğinin hata ayıklayıcı bu komut dosyalarını izlemek, gerek kalmadan bir komut dosyası hata ayıklayıcı işlem çalıştırılmasına izin verin.  
  
 Bir komut dosyası hata ayıklayıcısı çağırır `IDebugCookie::SetDebugCookie` yöntemi üzerinde işlem hata ayıklama Yöneticisi (PDM). Ardından, yöntemleri kullanılarak PDM eklemek veya kaldırmak için veya gelen Makine Hata Ayıklama Yöneticisi (MDM), bir komut dosyası uygulama için herhangi bir istek yanı sıra bu tanımlama bilgisi gönderir `IMachineDebugManagerCookie` arabirimi. MDM, ardından her hata ayıklayıcı dışında bu tanımlama bilgisi varsa bir değişikliğin bildirir.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IMachineDebugManagerCookie` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Çalışan bir uygulamaya ekler uygulama listesi.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Çalışan uygulamalar geçerli listesinin bir numaralandırıcı döndürür.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Bir uygulamanın çalışmasını kaldırır uygulama listesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imachinedebugmanager arabirimi](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Idebugcookie arabirimi](../../winscript/reference/idebugcookie-interface.md)