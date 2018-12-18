---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793298"
---
# <a name="iactivescript"></a>IActiveScript
Komut dosyası altyapısını başlatmak için gereken yöntemleri sağlar. Komut dosyası altyapısı uygulamalıdır `IActiveScript` arabirimi.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Komut dosyası motoru, sizi bilgilendirir [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) ana bilgisayarı tarafından sağlanan site.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Windows komut dosyası altyapısı ile ilişkili site nesnesi alır.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Komut dosyası altyapısı belirtilen bir duruma koyar.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Komut dosyası altyapısı geçerli durumunu alır.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Şu anda yüklü komut dosyaları abandon, durumuna kaybeder ve böylece kapalı bir durumuna girmesini diğer nesnelere sahip herhangi bir arabirim işaretçileri yayın için komut dosyası altyapısı neden olur.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Kök düzeyinde öğesinin adını komut dosyası altyapısı ad alanına ekler.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Ad alanı komut dosyası için tür kitaplığı ekler.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Alır `IDispatch` çalışan komut için arabirim.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Şu anda yürütülen iş parçacığı için bir komut dosyası altyapısı-tanımlı tanımlayıcı alır.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Belirli Microsoft Win32 iş parçacığı ile ilişkili iş parçacığı için bir komut dosyası altyapısı-tanımlı tanımlayıcı alır.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Bir komut dosyası iş parçacığı geçerli durumunu alır.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Çalışan bir komut dosyası iş parçacığının çalışmasını kesintiye uğratır.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Geçerli iş parçacığının hiçbir sitede sahip yüklenen bir komut dosyası altyapısı döndürme geçerli komut dosyası altyapısı (tüm geçerli yürütme durumu), eksi klonlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)