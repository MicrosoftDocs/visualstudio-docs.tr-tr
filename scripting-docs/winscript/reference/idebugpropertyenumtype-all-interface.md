---
title: Idebugpropertyenumtype_all arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794198"
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All Arabirimi
`IDebugPropertyEnumType` Arabirimleri, böylece her biri kendi IID'leri bir filtre olarak geçirilebilir tanımlanan `IDebugProperty::EnumMembers` uygun Numaralandırıcı isteyen oluştu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Adı açıklayan bir metin dizesi döndürür|  
  
 Aşağıdaki arabirimleri devralınmalıdır `IDebugPropertyEnumType_All`, ve hiçbir ek yöntemleri vardır.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)