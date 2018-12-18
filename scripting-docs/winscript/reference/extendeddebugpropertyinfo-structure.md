---
title: Extendeddebugpropertyınfo yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62b9f3b5877f7919a57e9747355276e438240796
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888911"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo Yapısı
Genişletir `DebugPropertyInfo` yapısı ile genişletilmiş özelliği nitelemek için ek üyeler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Üyeler  
 `dwValidFields`  
 Hangi alanların başlatılır belirtmek için kullanılan bir listelenmiş veri türü.  
  
 `bstrName`  
 Bir bağlam içinde özellik adı.  
  
 `bstrType`  
 Özelliği, biçimlendirilmiş dize olarak yazın.  
  
 `bstrValue`  
 Özellik değeri olarak biçimlendirilmiş bir dize.  
  
 `bstrFullName`  
 Özelliğin tam adı.  
  
 `dwAttrib`  
 Hata ayıklama özellik öznitelikleri için bayrakları belirtir bir sabit listesi.  
  
 `pDebugProp`  
 `IDebugProperty` Bunun için karşılık gelen nesne `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Dağıtım kimliği.  
  
 `nType`  
 Genişletilmiş özellik türü.  
  
 `varValue`  
 VARIANT sığabilen, genişletilmiş özellik değeri.  
  
 `plbValue`  
 Özellik değerinin gerçek veri baytı.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` Bunun için karşılık gelen nesne `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Debugpropertyınfo yapısı](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Idebugproperty arabirimi](../../winscript/reference/idebugproperty-interface.md)   
 [Idebugextendedproperty arabirimi](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)