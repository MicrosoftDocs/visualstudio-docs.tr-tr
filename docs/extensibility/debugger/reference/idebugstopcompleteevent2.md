---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119256"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Bir programı durdurulduğunda hata ayıklama altyapısı (DE) oturum hata ayıklama Yöneticisi (SDM) Bu isteğe bağlı bir olay gönderebilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar

Bu arabirim, Visual Studio 2005 ile sunulmuştur. Önceki sürümlerde, zaman uyumsuz durdurma desteklememektedir.

[Durdur](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) birden çok işlem ya da çok program senaryolarda SDM tarafından çağrılır. Bir program SDM durdurma olay gönderdiğinde, SDM çok durdurmak için diğer programları ister.

Durma zaman uyumsuz olarak bir programı durdurdu SDM bildirmek için kullanılır. SDM yorumlayıcı hata ayıklama altyapının için yararlıdır bildiren, bazen kod hata ayıklaması içinde çalıştığı program, bunu [durdurmak](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) zaman uyumlu olarak tamamlanamıyor. Hata ayıklama altyapısı bu zaman uyumsuz bildirim uygulamadığınız isteyip istemediğini, döndürmesi gerekir `S_ASYNC_STOP` gelen [durdurmak](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Gereksinimler

Başlık: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll