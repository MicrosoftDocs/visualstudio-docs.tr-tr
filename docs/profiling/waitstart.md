---
title: WaitStart | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 059f05d25f1882cd857dd1e39ea40a58a7c5e1d3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571376"
---
# <a name="waitstart"></a>WaitStart
WaitStart seçeneği neden *VSPerfCmd.exe* yalnızca profil oluşturucu başlatıldı başlatıldığında ya da belirtilen sayıda saniye geçtikten sonra dönmek için başlangıç alt komutu. Varsayılan olarak, başlangıç komut hemen döndürür. Başlangıç alt komut profil oluşturucu başlatılırken olmadan döndürürse, bir hata döndürülür. Saniye sayısını belirtilmezse, başlatma komutunun sonsuza kadar bekler.  
  
 Bu profil oluşturucu başlatıldı güvence altına almaya toplu iş dosyalarında WaitStart seçeneği kullanışlıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Seconds`  
 Başlangıç alt komutun dönmeden önce beklenecek saniye sayısı.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 WaitStart seçeneği yalnızca başlangıç alt komutu ile kullanılabilir.  
  
 **Çıktı:** `filename`  
 Çıktı dosyası adını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
 Bu toplu iş dosyası örneği başlatma komutunun başlatmak profil oluşturucu 5 saniye bekler.  
  
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