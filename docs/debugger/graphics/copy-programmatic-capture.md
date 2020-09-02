---
title: Kopyala (Programlı yakalama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895960"
---
# <a name="copy-programmatic-capture"></a>Kopyalama (Programlı Yakalama)
Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.

## <a name="syntax"></a>Söz dizimi

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametreler
 `szNewVSGLog` Yeni grafik günlük dosyasının dosya adı.

## <a name="remarks"></a>Açıklamalar
 Grafik bilgilerini yeni bir dosyaya kopyalamak için bazı grafik bilgilerini zaten yakalamış olmanız gerekir; Aksi takdirde hiçbir şey olmaz.