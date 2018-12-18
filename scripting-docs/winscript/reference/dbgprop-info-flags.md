---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377815adc7751841e2a2a3bb2f4dc8b51beecdea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941288"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Belirtmek için kullanılan `DebugPropertyInfo` alanları  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Üyeler  
 DBGPROP_INFO_NAME  
 Başlatır `bstrName` alan.  
  
 DBGPROP_INFO_TYPE  
 Başlatır `bstrType` alan.  
  
 DBGPROP_INFO_VALUE  
 Başlatır `bstrValue` alan.  
  
 DBGPROP_INFO_FULLNAME  
 Başlatır `bstrFullName` alan.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Başlatır `dwAttrib` alan.  
  
 DBGPROP_INFO_DEBUGPROP  
 Başlatır `pDebugProp` içeren alan bir `IDebugProperty` arabirimi.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Varsa, bu nesne türü için değer alanını otomatik olarak genişletilmiş değeri içermesi gerektiğini belirtir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Debugpropertyınfo yapısı](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)