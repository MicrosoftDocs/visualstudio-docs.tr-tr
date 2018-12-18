---
title: Iremotedebugapplicationex arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794975"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx Arabirimi
Çalışan bir uygulama temsil eder. Bir işletim sistemi işlemi karşılık gelecek şekilde gerekmez. Genellikle, bir hata ayıklayıcısı hata ayıklama için bir uygulama hedefler. Hata ayıklama işlem yöneticisi, genellikle uygulama nesnesi uygular.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IRemoteDebugApplicationEx` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Ana bilgisayar uygulaması için işlem kimliği döndürür.|  
|GetHostMachineName|Ana bilgisayar uygulamasını çalıştıran bilgisayarın adını döndürür.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Hata ayıklayıcı yerelleştirme için dili ayarlar.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Hata ayıklayıcı tek adımlı moduna zorlar.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Break komutu iptal eder.|  
|SetProxyBlanketAndAddRef|Windows 95 tabanlı işletim sistemlerinden uzaktan hata ayıklama ile uyumluluğu sağlamak için bir hata ayıklayıcı nesnesi için bir proxy üzerinde COM güvenlik bilgilerini güncelleştirir.|  
|ReleaseFromSetProxyBlanket|SetProxyBlanketAndAddRef gelen AddRef serbest bırakır.|