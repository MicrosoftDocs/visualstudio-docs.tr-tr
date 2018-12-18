---
title: DBGPROP_ATTRIB_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 831f12d11515e6796941b64e114bdc084309b87d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862417"
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
Çeşitli özniteliklerini açıklayan bir `IDebugProperty`. Üyesi `DebugPropertyInfo` yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Üyeler  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Öznitelikleri gösterir.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Belirten değer `DebugPropertyInfo::bstrValue` geçerli değil.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Başvuru veya özelliğin alt sahip olduğunu gösterir.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Değer salt okunur olduğunu gösterir.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Genel erişimi olan bir nesne belirtir.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Özel erişimi olan bir nesne belirtir.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Korumalı Erişim bir nesne belirtir.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Son erişimi olan bir nesne belirtir.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Genel depolama gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Statik depolama gösterir.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Bir özelliği olan nesneyi belirtir.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Sanal depolama gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Nesne türü sabit olduğunu gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Bu yuva eşzamanlı iş parçacığı olduğunu gösterir.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Bu yuva göre kalıcı depolama geçici olduğunu gösterir.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Bu yuva öznitelikleri önceden tanımlanmış bu BITS sunmayan sahip olduğunu gösterir.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Değer bir işlevden dönüş değeri olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bayrak, bir nesnenin alt öğelerini filtrelemek için de kullanılır. Değerleri bir bit düzeyinde OR ile birleştirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo Yapısı](../../winscript/reference/debugpropertyinfo-structure.md)