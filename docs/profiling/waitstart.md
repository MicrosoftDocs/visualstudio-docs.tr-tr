---
title: WaitStart | Microsoft Docs
description: WaitStart seçeneğinin VSPerfCmd.exe Başlat alt komutunun yalnızca profil oluşturucu başlatıldığında veya belirtilen saniye sayısı geçtiğinde dönmesini sağlar.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b8218b04b0c67f2b3b2ebf7ae2fe1209d76461aa
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718765"
---
# <a name="waitstart"></a>WaitStart
WaitStart seçeneği *VSPerfCmd.exe* Başlat alt komutunun yalnızca profil oluşturucu başlatıldığında veya belirtilen saniye sayısı geçtiğinde dönmesini sağlar. Varsayılan olarak start komutu hemen döndürür. Start Sub komutu, profil oluşturucuyu başlatmadan döndürürse bir hata döndürülür. Saniye sayısı belirtilmemişse, Başlat komutu süresiz olarak bekler.

 WaitStart seçeneği, profil oluşturucunun başlatıldığından emin olmak için Batch dosyalarında faydalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametreler
 `Seconds` Başlangıç alt komutundan döndürülmeden önce beklenecek saniye sayısı.

## <a name="required-options"></a>Gerekli seçenekler
 WaitStart seçeneği yalnızca start Sub-komutuyla birlikte kullanılabilir.

 **Çıkış:** `filename` Çıkış dosyası adını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu toplu iş dosyasında, start komutu profil oluşturucunun başlatılması için 5 saniye bekler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
