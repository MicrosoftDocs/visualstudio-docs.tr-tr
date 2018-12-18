---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04bc34de6e7ecbc438cfc63ed08c684cf4224366
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917030"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Açıklayan veya bir işlem özelliklerini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
Hata ayıklayıcı tarafından ayıklanmakta olan işlemi belirtir. Olabilir bir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı veya bazı diğer hata ayıklayıcı, örneğin, WinDbg olabilir.

PIFLAG_PROCESS_STOPPED  
İşlem durdurulur gösterir. Yalnızca şu durumlarda geçerli `PIFLAG_DEBUGGER_ATTACHED` ayrıca belirtilir. Visual Studio 2005 ve sonraki sürümlerinde kullanılabilir.

PIFLAG_PROCESS_RUNNING  
İşlemin çalışmadığını gösterir. Yalnızca şu durumlarda geçerli `PIFLAG_DEBUGGER_ATTACHED` ayrıca belirtilir. Visual Studio 2005 ve sonraki sürümlerinde kullanılabilir.

## <a name="remarks"></a>Açıklamalar

İçin kullanılan `Flags` üyesi [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) yapısı.

Bu bayrak bit düzeyinde ile birleştirilebilir `OR`.

## <a name="requirements"></a>Gereksinimler

Üstbilgi: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca Bkz.

[Sabit Listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)