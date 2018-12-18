---
title: Idebugstackframesnifferex arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794183"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx Arabirimi
Bir bileşen tarafından bilinen mantıksal yığın çerçeveleri numaralandırmak için bir yol sağlar. Komut dosyası motorları, genellikle bu arabirimi uygular. Bu arabirim tüm yığın çerçeveleri bulmak için işlemi hata ayıklama Yöneticisi kullanır, belirli bir iş parçacığı ile ilişkilendirilmiş.  
  
> [!NOTE]
>  Bu arabirime ilgilendiğiniz iş parçacığı içinde çağrılır. Arabirim uygulaması, geçerli iş parçacığının tanımlamak ve uygun bir numaralandırıcı döndürür.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Yığın çerçevelerinin geçerli iş parçacığı için bir numaralandırıcı döndürür.|