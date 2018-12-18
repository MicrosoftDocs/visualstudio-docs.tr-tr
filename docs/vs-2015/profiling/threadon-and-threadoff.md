---
title: ThreadOn ve ThreadOff | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e908da955258bfef5d66187bc974b6e051a48ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789180"
---
# <a name="threadon-and-threadoff"></a>ThreadOn ve ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **ThreadOff** ve **ThreadOn** alt komutları şüpheli işlem yöntemini kullanan komut satırı profil oluşturma oturumunda kullanılabilir yalnızca. **ThreadOff** ve **ThreadOn** duraklatma ve sürdürme belirtilen iş parçacığı profil oluşturma. **ThreadOff** iş parçacığı profil oluşturmayı durdurur ve **ThreadOn** iş parçacığı profil oluşturmaya başlar.  
  
 Çoğu durumda, belirttiğiniz **ThreadOn** veya **ThreadOff** yalnızca bir VSPerfCmd.exe seçenek olarak komut satırı, ancak aynı zamanda ile birleştirilebilir **GlobalOn**, **GlobalOff**, **ProcessOn**, ve **ProcessOff** alt komutları.  
  
 **ThreadOn** ve **ThreadOff** alt komutları etkileşimde **GlobalOn** ve **GlobalOff** veri denetimi komutları komut satırı profil oluşturma oturumunu, tüm işlemler için koleksiyonda ve **ProcessOn** ve **ProcessOff** belirtilen işlem için veri toplamayı kontrol alt komutları.  
  
 **ThreadOff** ve **ThreadOn** alt komutları da profil oluşturucu API işlevleri tarafından yönlendirilen iş parçacığı Başlat/Durdur sayısını etkiler.  
  
- **ThreadOff** hemen iş parçacığı Başlat/Durdur sayısı 0 olarak ayarlar ve bu nedenle profil oluşturma duraklatır.  
  
- **ThreadOn** hemen iş parçacığı Başlat/Durdur sayısını 1 olarak ayarlar ve bu nedenle sürdürür profil oluşturma.  
  
  Daha fazla bilgi için [Profil Araçları API'leri](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `TID`  
 İş parçacığı başlatmak veya durdurmak için tamsayı tanımlayıcısı.  
  
## <a name="valid-options"></a>Geçerli seçenekler şunlardır:  
 **ThreadOn** ve **ThreadOff** de aşağıdaki komutları içeren komut satırlarında belirtilebilir.  
  
 **Başlat:** `Method`  
 Komut satırı profil oluşturma oturumu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Durdurur veya komut satırı profil oluşturma oturumu içinde tüm işlemler için profil oluşturmaya başlar.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Durdurur veya belirtilen işlem için profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, **ThreadOff** alt, böylece yalnızca uygulama başlangıç verileri toplanır, profil oluşturma veri toplamayı durdurmak için kullanılır.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



