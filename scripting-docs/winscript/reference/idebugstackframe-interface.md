---
title: Idebugstackframe arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794414"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame Arabirimi
İş parçacığı yığında mantıksal yığın çerçevesi temsil eder. Çağrı `IDebugStackFrame::QueryInterface` elde etmek için yöntemi `IDebugExpressionContext` ifade windows değerlendirme ve izleme sağlayan arabirim.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugStackFrame` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Yığın çerçevesi ile ilişkili geçerli kod bağlamını döndürür.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Yığın çerçevesi kısa veya uzun metinsel açıklaması döndürür.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Dil kısa veya uzun metinsel açıklaması döndürür.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Bu yığın çerçevesi ile ilişkili iş parçacığı döndürür.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Özellik tarayıcısı geçerli çerçevenin döndürür.|