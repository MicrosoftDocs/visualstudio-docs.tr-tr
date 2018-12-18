---
title: Js_property_attrıbutes listelemesi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796286"
---
# <a name="jspropertyattributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES Listelemesi
Bir özelliğin özniteliklerini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Üyeler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Özellik öznitelikleri yok.|  
|`JS_PROPERTY_HAS_CHILDREN`|Özellik alt öğesi yok.|  
|`JS_PROPERTY_FAKE`|Özelliği "[yöntemleri]" gibi sahte bir düğümü temsil eder.|  
|`JS_PROPERTY_METHOD`|Özelliği bir yöntemdir.|  
|`JS_PROPERTY_READONLY`|Salt okunur bir özelliktir.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Özelliği yerel WinRT nesnesine bir işaretçidir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows komut dosyası arabirimleri başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)