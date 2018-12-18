---
title: Idebugthreadcall arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794237"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall Arabirimi
`IDebugThreadCall` Arabirimi iş parçacıkları arası çağrılar ile bir bileşen tarafından uygulanan genellikle `IDebugThread` işlem hata ayıklama Yöneticisi (PDM) tarafından sağlanan uygulama dizimi.  
  
 PDM çağrıları `IDebugThreadCall` istenen iş parçacığı arabiriminde ve `IDebugThreadCall` arabirimi istediğiniz uygulamayı çağrısı gönderir. `IDebugThreadCall` Arabirimi parametrelerinde uygun dön geçirilen parametre bilgileri çevirir.  
  
 `IDebugThreadCall` Ücretsiz iş parçacıklı bir nesne bir arabirimdir.  
  
## <a name="methods"></a>Yöntemler  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugThreadCall` arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Başka bir iş parçacığında kodu çalıştırmak için çağrıları işler.|