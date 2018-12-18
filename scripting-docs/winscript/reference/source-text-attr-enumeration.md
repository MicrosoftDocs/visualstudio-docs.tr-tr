---
title: SOURCE_TEXT_ATTR numaralandırması | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796454"
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR Numaralandırması
Kaynak metnin tek bir karakterinin özniteliklerini açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Değer|Açıklama|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0X0001|Dil anahtar sözcük, örneğin, VBScript anahtar sözcüğü parçası karakterdir `While`.|  
|SOURCETEXT_ATTR_COMMENT|0X0002|Karakter açıklama bloğu bir parçasıdır.|  
|SOURCETEXT_ATTR_NONSOURCE|0X0004|Karakter derlenmiş dil kaynak metni parçası değildir. Örneğin, bir betik bloğu çevreleyen HTML.|  
|SOURCETEXT_ATTR_OPERATOR|0X0008|Karakter dil işleci bir parçasıdır. Örneğin:, aritmetik işleç  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Karakter dil sayısal sabit bir parçasıdır.  Örneğin, sabit 3.14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Karakter dil dize sabiti bir parçasıdır. Örneğin, dize "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Bir işlev blok başlangıcı karakteri gösterir|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, ve `IActiveScriptDebug::GetScriptTextAttributes` yöntemleri sürece her karakter, bir metin özniteliği döndürür:  
  
-   Yöntem SOURCETEXT_ATTR_IDENTIFIER ve SOURCETEXT_ATTR_MEMBERLOOKUP bayrakları; bu durumda döndürebilir GETATTRTYPE_DEPSCAN bayrağı ayarlandığından,  
  
-   Yöntem SOURCETEXT_ATTR_THIS bayrağı; bu durumda döndürebilir GETATTRFLAG_THIS bayrağı ayarlandığından,  
  
-   Yöntem SOURCETEXT_ATTR_HUMANTEXT bayrağı; bu durumda döndürebilir GETATTRFLAG_HUMANTEXT bayrağı ayarlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası hata ayıklayıcı sabitleri, numaralandırmaları ve yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)