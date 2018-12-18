---
title: Idebugstackframesniffer arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794195"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer Arabirimi
Bir bileşen tarafından bilinen mantıksal yığın çerçeveleri numaralandırmak için bir yol sağlar. Komut dosyası motorları, genellikle bu arabirimi uygular. Bu arabirim tüm yığın çerçeveleri bulmak için işlemi hata ayıklama Yöneticisi kullanır, belirli bir iş parçacığı ile ilişkilendirilmiş.  
  
> [!NOTE]
>  Hata ayıklayıcı ilgi iş parçacığı içinde bu arabirimden çağırır. Komut dosyası altyapısı, geçerli iş parçacığının tanımlamak ve uygun bir numaralandırıcı döndürür.  
  
## <a name="methods"></a>Yöntemler  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugStackFrameSniffer` arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Yığın çerçevelerinin geçerli iş parçacığı için bir numaralandırıcı döndürür.|