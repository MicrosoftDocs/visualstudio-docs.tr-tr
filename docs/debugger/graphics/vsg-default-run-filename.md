---
description: Grafik günlük dosyasının varsayılan dosya adını tanımlar.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf80b34ed496f06b4051a6e6a9d7d771885e1e45
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232472"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Grafik günlük dosyasının varsayılan dosya adını tanımlar.

## <a name="syntax"></a>Sözdizimi

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametreler
 `filename` Grafik bilgileri programlı olarak yakalanarak grafik günlük dosyasına varsayılan olarak verilen dosya adı.

## <a name="value"></a>Değer
 Grafik günlük dosyasının dosya adını temsil eden bir dize sabit değeri. Varsayılan olarak, L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Açıklamalar
 Önişlemci sembolü `DONT_SAVE_VSGLOG_TO_TEMP` tanımlanmışsa, dosya adı yakalanan uygulamanın geçerli dizinine göre değişir veya mutlak bir yoldur; Aksi takdirde, kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol olamaz.

 Tanımlı dosya adını değiştirmek için, programınıza dahil etmeden önce yeniden tanımlamanız gerekir `vsgcapture.h` .

## <a name="example"></a>Örnek
 Bu örnek, yakalama dosyasının varsayılan dosya adının nasıl değiştirileceğini gösterir:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Ayrıca bkz.
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
