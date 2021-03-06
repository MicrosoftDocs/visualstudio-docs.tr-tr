---
description: Bu arabirim, bir bağlantı noktasının sunucusuna ve bildirim tesislerini erişmek için çeşitli yöntemler sağlar.
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03eb9f8c1bae74f15d295a72b27821d41b8282a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067120"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Bu arabirim, bir bağlantı noktasının sunucusuna ve bildirim tesislerini erişmek için çeşitli yöntemler sağlar.

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, programlara erişmek için hata ayıklama bağlantı noktasını göstermek üzere bu arabirimi uygular. Özel bir bağlantı noktası sağlayıcısı, uzaktan hata ayıklamayı işlediğinde da bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimindeki yöntemlere bir bağımsız değişken bu arabirimi sağlar. [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) çağrısı, bu arabirimi de edinebilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim, [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)içinde tanımlanan yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Bu bağlantı noktasından bağlantı noktası bildirim arabirimini alır.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Bu bağlantı noktasını barındıran sunucunun arabirimini alır.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bu bağlantı noktasının yerel makinede çalışıp çalışmadığını belirler.|

## <a name="remarks"></a>Açıklamalar
 "" Adı `IDebugDefaultPort2` , varsayılan bir bağlantı noktasını temsil etmediği için bir hatalı Nomer 'nin bir bitidir. "IDebugPort3" olarak adlandırılabilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
