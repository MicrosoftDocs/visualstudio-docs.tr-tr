---
title: Kopyalama (ProgramLı Yakalama) | Microsoft Docs
description: Etkin grafik günlüğü (.vsglog) dosyasının içeriğini yeni bir dosyaya kopyalamak için VsgDbg sınıfının Copy yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e4006803364407fed4b837ea992a95429c1db39
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232667"
---
# <a name="copy-programmatic-capture"></a>Kopyalama (Programlı Yakalama)
Etkin grafik günlüğü (.vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.

## <a name="syntax"></a>Sözdizimi

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametreler
 `szNewVSGLog` Yeni grafik günlüğü dosyasının dosya adı.

## <a name="remarks"></a>Açıklamalar
 Grafik bilgilerini yeni bir dosyaya kopyalamak için bazı grafik bilgilerini zaten yakaladığınız gerekir; Aksi takdirde, hiçbir şey olmaz.