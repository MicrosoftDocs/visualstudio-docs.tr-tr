---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 774bef7a3f28c973c9569544556d3033ede0093d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107744"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Çeşitli özniteliklerini açıklar bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) veya bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) arabirimi. Üye [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```csharp  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## <a name="members"></a>Üyeler  
 DBG_ATTRIB_NONE  
 Öznitelikleri gösterir.  
  
 DBG_ATTRIB_ALL  
 Tüm öznitelikleri gösterir.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 Başvuru veya özellik alt sahip olduğunu gösterir.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 Bu nesne için bir kimlik oluşturulduğunu gösterir.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 Bu nesne için bir kimlik oluşturulabilir gösterir.  
  
 DBG_ATTRIB_VALUE_READONLY  
 Değer salt okunur olduğunu gösterir.  
  
 DBG_ATTRIB_VALUE_ERROR  
 Değerin bir hata olduğunu gösterir.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 Değerlendirme bir yan etkisi olduğunu gösterir.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 Bu özellik gerçekten aşırı kapsayıcının olduğunu gösterir.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` Boolean.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` Boolean ve `TRUE`.  
  
 DBG_ATTRIB_VALUE_INVALID  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` geçerli değil.  
  
 DBG_ATTRIB_VALUE_NAT  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` olan "*bir şey*" (NAT). NAT ertelenmiş kurgusal özel durumları gösteren bir kayıt bayrağı Intel 64-bit işlemciler açıklar.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` muhtemelen otomatik genişletilmiş olmuştur.  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 Değerlendirme zaman aşımına uğradı olduğunu gösterir.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 Gösterir değerinde `DEBUG_PROPERTY_INFO::bstrValue` ham dizesi tarafından temsil edilebilir.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 Bu özellik en az bir özel Görüntüleyicisi ilişkili olduğunu gösterir.  
  
 DBG_ATTRIB_ACCESS_NONE  
 Hiçbiri olan bir nesneyi gösteren `public`, `private`, ne de `protected` erişim yazın.  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 Genel erişimi olan bir nesneyi belirtir.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 Özel erişimi olan bir nesneyi belirtir.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 Korumalı Erişim bir nesne gösterir.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 Son erişimi olan bir nesneyi belirtir.  
  
 DBG_ATTRIB_ACCESS_ALL  
 Erişim öznitelikleri ayıklamak için maskesi `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_STORAGE_NONE  
 Belirtilen depolama tür olduğunu gösterir.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 Genel depolama gösterir.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 Statik depolama gösterir.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 Kayıttaki depolama gösterir.  
  
 DBG_ATTRIB_STORAGE_ALL  
 Depolama öznitelikleri ayıklamak için maskesi `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_TYPE_NONE  
 Herhangi bir tür değiştiricisi olduğunu gösterir.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 Nesne türünü sanal olduğunu gösterir.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 Nesne türü sabit olduğunu gösterir.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 Nesne türünü eşitlenir gösterir.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 Nesne türünü volatile olduğunu gösterir.  
  
 DBG_ATTRIB_TYPE_ALL  
 Türü öznitelikleri ayıklamak için maskesi `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_DATA  
 Bu nesne bir veri alanını gösterir.  
  
 DBG_ATTRIB_METHOD  
 Bu nesne bir yöntemi gösterir.  
  
 DBG_ATTRIB_PROPERTY  
 Bu nesnenin bir özelliğini gösterir.  
  
 DBG_ATTRIB_CLASS  
 Bu nesne bir sınıf olduğunu belirtir.  
  
 DBG_ATTRIB_BASECLASS  
 Bu nesne bir taban sınıf olduğunu belirtir.  
  
 DBG_ATTRIB_INTERFACE  
 Bu nesne bir arabirimi gösterir.  
  
 DBG_ATTRIB_INNERCLASS  
 Bu nesne bir iç sınıf olduğunu belirtir.  
  
 DBG_ATTRIB_MOSTDERIVED  
 Bu nesne gösterir '*en çok türetilen*'. Terim "*en çok türetilen*" gerçek nesnenin türünü ve değil, başvuru türü anlamına gelir.  
  
 DBG_ATTRIB_CHILD_ALL  
 Maskesi gösterir `DBG_ATTRIB_DATA` aracılığıyla `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 Nesne kendisiyle ilişkili birden çok özel görüntüleyiciler sahip olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu numaralandırma değerleri için C# derlemesindeki gerçekte tanımlanmadı. Bunun yerine, kaynak dosyanızı tanımları kopyalamanız gerekir.  
  
 Bu bayrakların de bağımsız değişken olarak geçirildiğinde bir nesnedir, örneğin, alt öğeleri filtrelemek için kullanılan [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Değerlerin Bitsel ile birleştirilebilir `OR`.  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Bayrağı bir göstergesi olduğu [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] almak için [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) alanından arabirim [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi ve çağrı [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) özel görüntüleyiciler listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)