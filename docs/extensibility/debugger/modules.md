---
title: Modüller | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir modülün tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40cb7d0c65822fcb6ba4d4ca0132147f62d9286
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054770"
---
# <a name="modules"></a>Modül
Hata ayıklayıcı mimarisi açısından bir *Modül*:

- , Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- , Kendi simgelerini yeniden yükleyebilir ve kendisi tanımlayabilir. Modül açıklamaları IDE 'nin modüller penceresinde görüntülenir.

- , Modülü anlatmak için bir hata ayıklama altyapısı tarafından oluşturulan bir [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
