---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791804"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Şu anda yüklü komut dosyaları abandon, durumuna kaybeder ve böylece kapalı bir durumuna girmesini diğer nesnelere sahip herhangi bir arabirim işaretçileri yayın için komut dosyası altyapısı neden olur. Olay havuzlarını, hemen yürütülen betik metin ve devam etmekte olan makrosu çağrılarını durum değişiklikleri önce tamamlanır (kullanmak [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) çalışan bir komut dosyası iş parçacığının iptal etmek için). Döngüsel başvuru sorunları önlemek için arabirimi yayımlanmadan önce oluşturma ana bilgisayar tarafından bu yöntem çağrılmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|`S_OK`|Başarılı.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı zaten kapatılmış durumda olduğu).|  
|`OLESCRIPT_S_PENDING`|Yöntem başarıyla sıraya alındı, ancak durumu henüz değişmemiştir. Durum değişiklikleri site olduğunda üzerinde geri çağrılması için [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemi.|  
|`S_FALSE`|Yöntem başarılı oldu, ancak komut dosyası zaten kapatılmış.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)