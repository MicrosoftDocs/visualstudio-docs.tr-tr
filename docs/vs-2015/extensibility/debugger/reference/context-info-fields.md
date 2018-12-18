---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
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
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5169ff103b823067d64c58a3f6223220f67a3d52
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734221"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir bellek bağlamı hakkında almak için hangi bilgilerin belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Üyeler  
 CIF_MODULEURL  
 Başlat/kullanım `bstrModuleUrl` alanını [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısı.  
  
 CIF_FUNCTION  
 Başlat/kullanım `bstrFunction` alanını `CONTEXT_INFO` yapısı.  
  
 CIF_FUNCTIONOFFSET  
 Başlat/kullanım `posFunctionOffset` alanını `CONTEXT_INFO` yapısı.  
  
 CIF_ADDRESS  
 Başlat/kullanım `bstrAddress` alanını `CONTEXT_INFO` yapısı.  
  
 CIF_ADDRESSOFFSET  
 Başlat/kullanım `bstrAddressOffset` alanını `CONTEXT_INFO` yapısı.  
  
 CIF_ALLFIELDS  
 Başlat/tüm alanları kullanmak `CONTEXT_INFO` yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerleri bir parametresine geçirilir [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) hangi alanları göstermek için yöntemi [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısı olan başlatılacak.  
  
 Bu bayraklar Ayrıca hangi alanları göstermek için kullanılan `CONTEXT_INFO` yapısı, kullanılan ve geçerli yapısı döndürülür.  
  
 Bu değerleri bir bit düzeyinde OR ile birleştirilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

