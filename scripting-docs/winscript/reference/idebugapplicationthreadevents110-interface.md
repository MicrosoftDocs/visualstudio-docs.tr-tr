---
title: Idebugapplicationthreadevents110 arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794036"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 Arabirimi
Daha fazla iş parçacığı olayları ekler. Bu olaylar yalnızca yerel. Diğer bir deyişle, onlara yalnızca süreci içinde abone olabilirsiniz hata ayıklaması, kullanarak [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) bildirmek ve yöntemleri PDM uygulama iş parçacığı nesneleri üzerinde unadvise (nesneleri uygulayan [Idebugapplicationthread Arabirim](../../winscript/reference/idebugapplicationthread-interface.md)). ' Ten gelen iş parçacığı üzerinde oluşur.  
  
> [!IMPORTANT]
>  Bu arabirim PDM v11.0 ve sonraki sürümler tarafından uygulanır. activdbg100.h içinde bulunur.  
  
## <a name="methods"></a>Yöntemler  
 `IDebugActivationThreadEvents110` Arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Idebugapplicationthreadevents110:: OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Çağrı PDM'ın iş parçacığı kullanarak akışına geçiş başladı.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|İş parçacığı bir kesme noktası'na devam ediliyor ve bir kez daha etkin olacaktır.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|İş parçacığı bir kesme noktası için askıya alma ve tam olarak askıya alınmasına iş parçacığı gerektiren çağrıları işleyebilir.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Çağrı PDM'ın iş parçacığı kullanarak akışına geçişi tamamlandı.|