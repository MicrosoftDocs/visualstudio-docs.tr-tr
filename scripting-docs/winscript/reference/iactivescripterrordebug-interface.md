---
title: Iactivescripterrordebug arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793319"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug Arabirimi
Derleme zamanı hataları ve çalışma zamanı özel durumları için belge bağlam bilgilerini sağlar. `IActiveScriptError::QueryInterface` Yöntemi destekler `IActiveScriptErrorDebug` arabirimi.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IActiveScriptError`, `IActiveScriptErrorDebug` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Bu hata için belge bağlamı sağlar.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Çalışma zamanı hataları için geçerli olan yığın çerçevesi sağlar.|