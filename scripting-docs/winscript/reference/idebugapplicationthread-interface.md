---
title: Idebugapplicationthread arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793940"
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread Arabirimi
Dil motorları ve ana iş parçacığı eşitleme sağlamak ve iş parçacığına özgü hata ayıklama durum bilgilerini saklamak için sağlar. Bu arabirim genişletir `IRemoteDebugApplicationThread` iş parçacığı olmayan uzaktan erişim sağlamak için arabirim.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IRemoteDebugApplicationThread`, `IDebugApplicationThread` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Çağıran kodu uygulama iş parçacığında çalıştırmak için bir mekanizma sağlar.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Bu iş parçacığı şu anda çalışan iş parçacığının olup olmadığını belirler.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Bu iş parçacığı hata ayıklayıcı iş parçacığı olup olmadığını belirler.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Bu iş parçacığı açıklaması ayarlar.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|İş parçacığı durumu açıklamasını ayarlar.|