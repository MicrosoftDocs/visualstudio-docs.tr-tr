---
title: EXCEPTION_STATE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1032be313c6be8c71799ea493e82c03fd9e96ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818256"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Özel durum durumu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Üyeler  
 EXCEPTION_NONE  
 Özel durumda Dur değil.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Özel durum sırasında ilk Açmadığınızda durdurun. Bir özel durum olayı açıklayan bu bayrağı özel durum olayı bir ilk fırsat özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Özel durum ikinci tetikleyicisinin tetikleme adresindeki durdurun. Bir özel durum olayı açıklayan özel durum olayı bir ikinci şans özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Bir kullanıcı modu özel ilk tetikleyicisinin tetikleme adresindeki durdurun. Bir özel durum olayı açıklayan özel durum olayı, kullanıcı ilk fırsat özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Bir kullanıcı modu özel durum yakalanmadı durdur. Bir özel durum olayı açıklayan özel durum olayı bir yakalanmayan kullanıcı modu özel durum olayı olduğunu gösterir.  
  
 EXCEPTION_STOP_ALL  
 Hiçbir özel durdurun. Bir özel durum olayı açıklayan kurulurken kullanılmaz.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Bir özel durum olayı açıklayan özel durum gelen ettirilemez gösterir.  
  
 EXCEPTION_CODE_SUPPORTED  
 Özel durum kodu, destekleyici sahip olduğunu gösterir. Bir özel durum görüntülenmesinde kullanılan  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Özel durum kodunu onaltılık olarak görüntüleneceğini belirtir. Bir özel durum görüntülenmesinde kullanılır.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Özel durum kodu JustMyCode desteklediğini belirtir. Bir özel durum görüntülenmesinde kullanılır.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Yönetilen kod hata ayıklayıcı özel durumlarını işlemelidir gösterir. Aksi durumda kümesi, varsayılan hata ayıklayıcı özel durumları işler. Bu geçirilir [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) yöntemi ve kullanılan değil [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısı.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 ESKİ, KULLANMAYIN.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 ESKİ, KULLANMAYIN.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 ESKİ, KULLANMAYIN.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 ESKİ, KULLANMAYIN.  
  
## <a name="remarks"></a>Açıklamalar  
 Olarak kullanılan `dwState` üyesi [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısı, özel durum ve ne hakkında yapılabilir durumunu göstermek için.  
  
 Bu değerleri de geçirilen [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) tüm özel durumları durumunu ayarlamak için yöntemi.  
  
 Bu bayraklar bir bit düzeyinde OR ile birleştirilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)