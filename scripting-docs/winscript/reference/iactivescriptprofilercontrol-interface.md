---
title: Iactivescriptprofilercontrol arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793496"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl Arabirimi
Profil oluşturma destekler komut dosyası altyapısı tarafından uygulanır. Genellikle, uygulayan bir nesne `IActiveScriptProfilerControl` de uygulayan [IActiveScript](../../winscript/reference/iactivescript.md) arabirimi. Bu durumda, bir tanıtıcı elde edebilirsiniz `IActiveScriptProfilerControl` çağırarak arabirim `IUnknown::QueryInterface` nesnesi üzerinde yöntemi. Arabirim durdurma ve komut dosyası altyapısı profil başlatma için gereken yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Komut dosyası altyapısı profil başlatır.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Profil oluşturucu komut dosyası altyapısı olay maskesi ayarlar.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Komut dosyası altyapısı profil durdurur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası profil oluşturucu arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)