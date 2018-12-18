---
title: LineOff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba5d8c3e2644c94a4e15115661341a34c9e6f761
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845434"
---
# <a name="lineoff"></a>LineOff
Örnekleme profili oluşturma yöntemi kullanırken varsayılan olarak, profil oluşturucu kaynak kodu satır sayısı ve satır numarası uzaklık verilerini toplar. VSPerfCmd **LineOff** seçeneği devre dışı bırakır satır numarası veri toplama VSPerfCmd uygulamayı başlatmak için kullanıldığında. Profil oluşturma verilerini işleve toplanır ne zaman düzey **LineOff** belirtilir.  
  
 Kullanabileceğiniz **LineOff** yalnızca **başlatma** seçeneği ve yalnızca zaman profil oluşturucu örnekleme için kullanarak başlatıldı **Başlat**:**örnek** seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **LineOff** seçeneği içeren bir komut satırında yalnızca kullanılabilir **başlatma** seçeneği.  
  
 **Başlat:** `AppName`  
 Belirtilen uygulamayı başlatır ve profil oluşturma örnekleme yöntemi ile başlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek uygulama ve profil oluşturucu başlatır ve satır düzeyi örnekleme devre dışı bırakır.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Hizmetleri](../profiling/command-line-profiling-of-services.md)