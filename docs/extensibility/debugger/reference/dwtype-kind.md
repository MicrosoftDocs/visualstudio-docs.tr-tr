---
title: dwTYPE_KIND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4339c18f7aa745c8b741c0a431b6073300ff145b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841773"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Yorumlama türünü belirten bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 TYPE_KIND_METADATA  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) birleşim olarak yorumlanabilir bir [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) yapısı.  
  
 TYPE_KIND_PDB  
 `TYPE_INFO` Birleşim olarak yorumlanabilir bir [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) yapısı.  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO` Birleşim olarak yorumlanabilir bir [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu sabit listesi değerlerini görünür `dwKind` alanını [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısı ve nasıl yorumlanacağını belirlemek için kullanılan `type` birleşim üyesi. `TYPE_INFO` Yapısı için bir çağrı tarafından döndürülen [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)