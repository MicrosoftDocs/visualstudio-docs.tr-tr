---
title: ProcessOn ve ProcessOff | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ebad6b1491fd599f27e98b0f61e12017434ffe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761020"
---
# <a name="processon-and-processoff"></a>ProcessOn ve ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ProcessOff** ve **ProcessOn** alt komutları duraklatma ve komut satırı profil oluşturma oturumu içinde belirtilen işlem için profil oluşturmayı sürdürün. **ProcessOff** profil oluşturma işlemi durdurur ve **ProcessOn** işlemi profil oluşturmaya başlar.  
  
 Çoğu durumda, belirttiğiniz **ProcessOn** veya **ProcessOff** yalnızca bir VSPerfCmd.exe seçenek olarak komut satırı, ancak aynı zamanda ile birleştirilebilir **GlobalOn**, **GlobalOff**, **ThreadOn**, ve **ThreadOff** alt komutları.  
  
 **ProcessOn** ve **ProcessOff** alt komutları etkileşimde **GlobalOn** ve **GlobalOff** veri denetimi komutları komut satırı profil oluşturma oturumunu, tüm işlemler için koleksiyonda ve **ThreadOn** ve **ThreadOff** belirtilen iş parçacığı için veri toplamayı kontrol alt komutları.  
  
 **ProcessOff** ve **ProcessOn** alt komutları da profil oluşturucu API işlevleri tarafından yönetilen işlemi Başlat/Durdur sayısını etkiler.  
  
- **ProcessOff** hemen işlem Başlat/Durdur sayısı 0 olarak ayarlar ve bu nedenle profil oluşturma duraklatır.  
  
- **ProcessOn** hemen işlem Başlat/Durdur sayısı 1 olarak ayarlar ve bu nedenle sürdürür profil oluşturma.  
  
  Daha fazla bilgi için [Profil Araçları API'leri](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `PID`  
 Başlatma veya durdurma işlemini tamsayı tanımlayıcısı. İşlem kimlikleri, Windows Görev Yöneticisi'nin İşlemler sekmesinde listelenir.  
  
## <a name="required-subcommands"></a>Gerekli bir alt komutları  
 Yok.  
  
## <a name="valid-subcommands"></a>Geçerli alt komutları  
 **ProcessOn** ve **ProcessOff** de aşağıdaki komutları içeren komut satırlarında belirtilebilir.  
  
 **Başlat:** `Method`  
 Komut satırı profil oluşturma oturumu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **Başlat:** `AppName`  
 Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profili oluşturma başlar.  
  
 **Ekleme:** `PID`  
 Belirtilen işlem profil oluşturma başlar.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Durdurur veya komut satırı profil oluşturma oturumu içinde tüm işlemler için profil oluşturmaya başlar.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Durdurur veya belirtilen iş parçacığı (yalnızca izleme metodunu) için profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, **ProcessOff** alt uygulama başlatma için profil oluşturma verilerini toplamak için kullanılır.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



