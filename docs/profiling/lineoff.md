---
title: Satır kapalı | Microsoft Docs
description: VSPerfCmd ' nin uygulamayı başlatmak için kullanıldığı zaman satır numarası veri toplamayı devre dışı bırakma seçeneğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a141e713dd03f99db6ce47224c64236a0219cdd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917895"
---
# <a name="lineoff"></a>LineOff
Varsayılan olarak, profil oluşturucu, örnekleme profil oluşturma yöntemini kullanırken kaynak kodu satır numarasını ve satır numarası fark verileri ' ni toplar. VSPerfCmd giriş **kapalı** seçeneği, VSPerfCmd, uygulamayı başlatmak için kullanıldığında satır numarası veri toplamayı devre dışı bırakır. **Satır dışı** belirtildiğinde profil oluşturma verileri işlev düzeyine toplanır.

 Yalnızca **Başlat seçeneğiyle ve** yalnızca profil oluşturucu **başlatma**:**örnek** seçeneğini kullanarak örnekleme için başlatıldığında, **LineOff** özelliğini kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="required-options"></a>Gerekli seçenekler
 **LineOff** seçeneği yalnızca **başlatma** seçeneğini içeren bir komut satırında kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Bu örnek, uygulamayı ve profil oluşturucuyu başlatır ve satır düzeyinde örneklemeyi devre dışı bırakır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
