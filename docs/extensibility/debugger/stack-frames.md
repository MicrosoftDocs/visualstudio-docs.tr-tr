---
title: Yığın çerçeveleri | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir yığın çerçevesinin tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898558"
---
# <a name="stack-frames"></a>Yığın çerçeveleri
Hata ayıklayıcı mimarisinde *yığın çerçevesi*:

- , Bir iş parçacığının Yürütme bağlamını sağlayan bir yığın soyutlamasıdır. Bir iş parçacığı her zaman bir işlev içinde yürütülür. Yığın çerçevesi, işlevin yerel değişkenlerini ve bağımsız değişkenlerini barındırır. Visual Studio ile hata ayıklamak için, hata ayıklaması yapılan dilin veya ortamın yığın çerçevelerini desteklemesi gerekir.

- Hem tanımlayabilir hem de tanımlayabilir ve ilişkili iş parçacığını döndürebilir. Yığın çerçevesi, geçerli yönerge işaretçisini ve ilişkili belgeleri ve ifade değerlendirme bağlamlarını temsil eden kod bağlamını de döndürebilir.

- , Yerel değişkenlerin ve bağımsız değişkenlerin adını, türünü ve değerini tanımlayan ve çeşitli IDE hata ayıklama pencereleri içinde görüntülenen özelliklere sahiptir.

- , Genellikle bir hata ayıklama altyapısı (DE) veya sanal makine tarafından bir iş parçacığı yürütmenin sonucu olarak oluşturulan bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
