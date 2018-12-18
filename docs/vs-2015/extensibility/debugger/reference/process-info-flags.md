---
title: PROCESS_INFO_FLAGS | Microsoft Docs
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
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 453c976ec4dd1c0c0b1c1e67592f840c17a9ac9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726793"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Açıklayan veya bir işlem özelliklerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Üyeler  
 PIFLAG_SYSTEM_PROCESS  
 İşlem bir sistem işlemi olduğunu gösterir.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Hata ayıklayıcı tarafından ayıklanmakta olan işlemi belirtir. Olabilir bir [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklayıcı veya bazı diğer hata ayıklayıcı, örneğin, WinDbg olabilir.  
  
 PIFLAG_PROCESS_STOPPED  
 İşlem durdurulur gösterir. Yalnızca şu durumlarda geçerli `PIFLAG_DEBUGGER_ATTACHED` ayrıca belirtilir. Kullanılabilir [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve daha sonra.  
  
 PIFLAG_PROCESS_RUNNING  
 İşlemin çalışmadığını gösterir. Yalnızca şu durumlarda geçerli `PIFLAG_DEBUGGER_ATTACHED` ayrıca belirtilir. Kullanılabilir [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve daha sonra.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin kullanılan `Flags` üyesi [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısı.  
  
 Bu bayrak bit düzeyinde ile birleştirilebilir `OR`.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

