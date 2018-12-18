---
title: FIELD_KIND | Microsoft Docs
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
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60622f96550445070d89c239e2d1ca5a37184e73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816807"
---
# <a name="fieldkind"></a>FIELD_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yer alan türünü belirten bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```csharp  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## <a name="members"></a>Üyeler  
 FIELD_KIND_TYPE  
 Alan yalnızca bir tür olduğunu gösterir.  
  
 FIELD_KIND_SYMBOL  
 Alan türü, adı ve diğer bilgileri ile bir simge olduğunu gösterir.  
  
 FIELD_TYPE_PRIMITIVE  
 Alanın bir temel veri türü olduğunu gösterir.  
  
 FIELD_TYPE_STRUCT  
 Alan bir yapı olduğunu gösterir.  
  
 FIELD_TYPE_CLASS  
 Alanın bir sınıf olduğunu gösterir.  
  
 FIELD_TYPE_INTERFACE  
 Alan bir arabirim olduğunu gösterir.  
  
 FIELD_TYPE_UNION  
 Alanın bir birleşim olduğunu gösterir.  
  
 FIELD_TYPE_ARRAY  
 Alan bir dizi olduğunu gösterir.  
  
 FIELD_TYPE_METHOD  
 Alan bir yöntem olduğunu gösterir.  
  
 FIELD_TYPE_BLOCK  
 Alanın bir blok olduğunu gösterir.  
  
 FIELD_TYPE_POINTER  
 Alan bir işaretçi olduğunu gösterir.  
  
 FIELD_TYPE_ENUM  
 Alan listelenmiş veri türü olduğunu gösterir.  
  
 FIELD_TYPE_LABEL  
 Alanın bir etiketi gösterilir.  
  
 FIELD_TYPE_TYPEDEF  
 Alan için bir typedef olduğunu gösterir.  
  
 FIELD_TYPE_BITFIELD  
 Alanın bir bit alanı olduğunu gösterir.  
  
 FIELD_TYPE_NAMESPACE  
 Alan için bir ad alanı olduğunu gösterir.  
  
 FIELD_TYPE_MODULE  
 Alanın bir modül olduğunu gösterir.  
  
 FIELD_TYPE_DYNAMIC  
 Alan dinamik olduğunu gösterir.  
  
 FIELD_TYPE_PROP  
 Alanın bir özellik olduğunu gösterir.  
  
 FIELD_TYPE_INNERCLASS  
 Alanın bir iç sınıf olduğunu gösterir.  
  
 FIELD_TYPE_REFERENCE  
 Alanın başvuru olduğunu gösterir.  
  
 FIELD_TYPE_EXTENDED  
 Daha sonraki kullanımlar için ayrılmıştır.  
  
 FIELD_SYM_MEMBER  
 Alanın bir üyesi olduğunu gösterir.  
  
 FIELD_SYM_LOCAL  
 Alan yerel olduğunu gösterir.  
  
 FIELD_SYM_PARAMETER  
 Alanın bir parametre olduğunu gösterir.  
  
 FIELD_SYM_THIS  
 Alan "Bu" işaretçiyi olduğunu gösterir.  
  
 FIELD_SYM_GLOBAL  
 Alan genel olduğunu gösterir.  
  
 FIELD_SYM_PROP_GETTER  
 Alan özelliklerini alan gösterir.  
  
 FIELD_SYM_PROP_SETTER  
 Alan özelliklerini ayarlar gösterir.  
  
 FIELD_SYM_EXTENDED  
 Daha sonraki kullanımlar için ayrılmıştır.  
  
 FIELD_KIND_MASK  
 Alan türleri için bir maske gösterir.  
  
 FIELD_TYPE_MASK  
 Alan türleri için bir maske gösterir.  
  
 FIELD_SYM_MASK  
 Sembol bilgisi için bir maske gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrısından döndürülen [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi.  
  
 Bu alanın türünü bağlı olarak [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) üzerinde çağrılabilir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminin daha belirli bir form arabirimi. Örneğin, varsa [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürür `FIELD_TYPE_METHOD`, ardından çağırabilirsiniz `QueryInterface` miyim üzerinde`DebugField` almak için [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

