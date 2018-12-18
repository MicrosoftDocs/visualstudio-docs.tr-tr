---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7575d959c2452a4814c63a7e0293872914832a69
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731058"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama modülü bilgi bayrakları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Üyeler  
 MIF_NONE  
 Alanların yapısında başlatma/kullanın.  
  
 MIF_NAME  
 Başlat/kullanım `m_bstrName` alanındaki [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı.  
  
 MIF_URL  
 Başlat/kullanım `m_bstrUrl` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_VERSION  
 Başlat/kullanım `m_bstrVersion` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_DEBUGMESSAGE  
 Başlat/kullanım `m_bstrDebugMessage` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_LOADADDRESS  
 Başlat/kullanım `m_addrLoadAddress` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_PREFFEREDADDRESS  
 Başlat/kullanım `m_addrPreferredLoadAddress` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_SIZE  
 Başlat/kullanım `m_dwSize` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_LOADORDER  
 Başlat/kullanım `m_dwLoadOrder` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_TIMESTAMP  
 Başlat/kullanım `m_TimeStamp` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_URLSYMBOLLOCATION  
 Başlat/kullanım `m_bstrUrlSymbolLocation` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_FLAGS  
 Başlat/kullanım `m_dwModuleFlags` alanındaki `MODULE_INFO` yapısı.  
  
 MIF_ALLFIELDS  
 Tüm alanlarda başlatma/kullanım `MODULE_INFO` yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerleri bir bağımsız değişken olarak geçirilen [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) hangi alanları göstermek için yöntemi [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı olan başlatılacak.  
  
 Bu değerleri de kullanılan `MODULE_INFO` yapısı hangi alanların kullanılan ve geçerli olduğunu belirtmek için.  
  
 Bu bayrak bit düzeyinde ile birleştirilebilir `OR`.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

