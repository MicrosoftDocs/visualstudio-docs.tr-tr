---
title: Iscriptnode arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796289"
---
# <a name="iscriptnode-interface"></a>IScriptNode Arabirimi
Arabirimini uygulayan bir nesneye `IScriptNode` arabirimi bir Web sayfasını temsil eder.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IScriptNode` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Bir nesne hala etkin olup olmadığını gösterir.|  
|[Iscriptnode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Bir alt örneğini ekler `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Bir kod parçacığı bir alt örneğini ekler bir `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Nesne ağacına siler.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Belirtilen dizinde düğümünde olan alt öğesini döndürür.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Bir kod parçacığı konak nesnesi ile ilişkilendirmek için kullanılan uygulama tanımlı bir değer döndürür.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Bir nesne dizinini üst öğenin alt listesinde döndürür.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Geçerli komut dosyası düğüm tarafından kullanılan komut dosyası dilini döndürür.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Alt öğelerinin sayısını döndürür `IScriptNode` nesnesi.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Döndürür `IScriptNode` nesnenin üst nesnesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası yazma arabirimleri](../../winscript/reference/active-script-authoring-interfaces.md)