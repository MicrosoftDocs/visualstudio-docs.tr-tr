---
title: Iactivescriptsitedebug arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793520"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug Arabirimi
Akıllı ana uygulama `IActiveScriptSiteDebug` belge yönetimi gerçekleştirmek ve hata ayıklamaya katılmak için arabirim. `IActiveScriptSite` Nesnesi genellikle uygulaması sağlar `IActiveScriptSiteDebug` arabirimi. Bu yapıldığında, çağrı `IActiveScriptSite::QueryInterface` elde etmek için yöntemi `IActiveScriptSiteDebug` arabirimi.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IActiveScriptSiteDebug` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Temsilci seçme için dil altyapısı tarafından kullanılan `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Bu komut dosyasını site ile ilişkili hata ayıklama uygulama nesnesi döndürür.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Hangi komut dosyası altında belgeleri eklenmelidir uygulama düğümünü alır.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Çalışma zamanı hataların nasıl işleneceğini belirlemek bir akıllı ana bilgisayar sağlar.|