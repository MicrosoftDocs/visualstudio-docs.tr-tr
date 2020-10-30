---
title: SuspendTracking | Microsoft Docs
description: Geçerli bağlamda izlemeyi askıya alarak MSBuild SuspendTracking için sözdizimi, gereksinimler ve dönüş değeri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048083"
---
# <a name="suspendtracking"></a>SuspendTracking

Geçerli bağlamda izlemeyi askıya alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Döndürülen değer

 İzleme askıya alınmışsa **başarılı** biti ayarlanmış bir **HRESULT** .

## <a name="requirements"></a>Gereksinimler

 **Üstbilgi:** *FileTracker. h*

## <a name="see-also"></a>Ayrıca bkz.

- [ResumeTracking](../msbuild/resumetracking.md)