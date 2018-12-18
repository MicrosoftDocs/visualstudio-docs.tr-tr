---
title: GlobalOn ve GlobalOff | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8176f32a6d235a0df1c57b4e5ba9cf6e9268ccb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762587"
---
# <a name="globalon-and-globaloff"></a>GlobalOn ve GlobalOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **GlobalOff** ve **GlobalOn** seçenekleri duraklatma ve komut satırı profil oluşturma oturumu içinde tüm işlemler ve iş parçacıkları için profil oluşturmayı sürdürün.  
  
 Belirtebileceğiniz **GlobalOn** ve **GlobalOff** VSPerfCmd.exe komut satırı veya tek seçenekler de içeren komut satırları içerebilir gibi **Başlat**, **Başlatma**, veya **iliştirme** seçenekleri.  
  
 **GlobalOn** ve **GlobalOff** ile birleştirilebilir **ProcessOn**, **ProcessOff**, **ThreadOn**ve  **ThreadOff** seçenekleri.  
  
 **GlobalOn** ve **GlobalOff** seçenekleri etkileşimde **ProcessOn** ve **ProcessOff** için veri toplamayı kontrol seçenekleri bir işlemi belirtilen ile **ThreadOn** ve **ThreadOff** belirtilen iş parçacığı için veri toplama denetleyen seçenekler.  
  
 **GlobalOff** ve **GlobalOn** seçenekleri, profil oluşturucu API işlevleri tarafından yönetilen Global Başlat/Durdur sayısını da etkiler.  
  
- **GlobalOff** hemen genel Başlat/Durdur sayısını 0 olarak ayarlar ve bu nedenle profil oluşturma duraklatır.  
  
- **GlobalOn** hemen genel Başlat/Durdur sayısını 1 olarak ayarlar ve bu nedenle sürdürür profil oluşturma.  
  
  Daha fazla bilgi için [Profil Araçları API'leri](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="valid-options"></a>Geçerli seçenekler şunlardır:  
 **GlobalOn** ve **GlobalOff** aşağıdaki seçenekleri de içeren komut satırlarında belirtilebilir.  
  
 **Başlat:** `Method`  
 Komut satırı Profil Oluşturucu oturumu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **Başlat:** `AppName`  
 Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profili oluşturma başlar.  
  
 **Ekleme:** `PID`  
 Belirtilen işlem profil oluşturma başlar.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Durdurur veya belirtilen işlem için profil oluşturmaya başlar.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Durdurur veya (yalnızca izleme metodunu) belirtilen işlem için profil oluşturmaya başlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, **GlobalOff** ve **GlobalOn** seçenekleri uygulama başlatma ve kapatma için profil oluşturma verileri toplama önlemek üzere kullanılır.  
  
```  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



