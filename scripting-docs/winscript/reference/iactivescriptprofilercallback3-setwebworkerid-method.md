---
title: Iactivescriptprofilercallback3::setwebworkerıd yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793472"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId Yöntemi
Profil Oluşturucu bu profil oluşturma oturumu için kullanılacak çalışan kimliği hakkında uyarır. İşlev sayfa bağlamında yürütülmüyor varsa, bu yöntem çağrılır değil. Değeri `webWorkerId` 1'den başlayarak her çalışan için 1 artar. Kimliği değerlerin dışında bir oturum kararlı ve çalışanları oluşturulduğu sırada yalnızca karşılık üzere tasarlanmamıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `webWorkerId`  
 Web çalışanı kimliği  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri komut dosyası altyapısı tarafından göz ardı edilir.