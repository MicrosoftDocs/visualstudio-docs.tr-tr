---
title: Kullanıcı (VSPerfCmd) | Microsoft Docs
description: Kullanıcı seçeneğinin profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını nasıl belirttiğinde öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886008"
---
# <a name="user-vsperfcmd"></a>Kullanıcı (VSPerfCmd)
**Kullanıcı** seçeneği, profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin **işlemler** sekmesinde Kullanıcı adı sütununda listelenir.

 **Kullanıcı** seçeneği, yalnızca **Başlangıç** seçeneğini de içeren bir komut satırında belirtilebilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Domain` Kullanıcının etki alanının adı.

 `UserName` Kullanıcının adı.

## <a name="required-options"></a>Gerekli seçenekler
 **Kullanıcı** seçeneği yalnızca **Başlangıç** seçeneğiyle birlikte kullanılabilir.

 **Başlangıç:** `Method` Profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, **Kullanıcı** seçeneğinin kullanımını gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
