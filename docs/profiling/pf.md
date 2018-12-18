---
title: PF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c86ce1c828ff3f090ce675aeed03a4911a55544
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258976"
---
# <a name="pf"></a>PF
*VSPerfCmd.exe* **PF** seçeneği sayfa hataları örneklenen profil olayını ayarlar ve bir örnekleme aralığı 10 varsayılan sayfa hatalarının sayısı isteğe bağlı olarak değişir.  
  
> [!NOTE]
>  **PF** 64-bit sistemlerinde kullanılamaz.  
  
**PF** de içeren bir komut satırında yalnızca kullanılabilir **başlatma** veya **Attach** seçeneği.  
  
 Varsayılan olarak, örnekleme olay durdurulamaz harici işlemci saat döngüsü için ayarlanır ve örnekleme aralığı 10,000,000 için ayarlanır. **Zamanlayıcı**, **PF**, **Sys**, ve **sayaç** seçenekleri örnek olay ve örnekleme aralığı ayarlamanıza olanak sağlar. **GC** seçeneği her ayırma ve atık toplama olay .NET bellek verileri toplar. Bir komut satırında bu seçenekler yalnızca biri belirtilebilir.  
  
 Örnekleme olay ve örnekleme aralığı yalnızca ilk komut içeren satırı ayarlanabilir bir **başlatma** veya bir **Attach** seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Events`  
 Bir örnekleme aralığı içinde sayfa hatası olaylarının sayısını belirten bir tamsayı değeri. Varsa `Events` belirtilmezse, aralığı 10 olarak ayarlandı.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **PF** yalnızca aşağıdaki seçeneklerden birini içeren bir komut satırında belirtilebilir.  
  
 **Başlat:** `AppName`  
 Profil Oluşturucu ve AppName tarafından belirtilen uygulamayı başlatır.  
  
 **Ekle:** `PID`  
 Profil Oluşturucu AppName tarafından belirtilen işlem ekler.  
  
## <a name="invalid-options"></a>Geçersiz seçenekleri  
 Aşağıdaki seçenekler aynı komut satırında belirtilemez **PF**.  
  
 **Zamanlayıcı**[**:**`Cycles`]  
 Ayarlar işlemci saatinin örnekleme olaya geçiş yapar ve isteğe bağlı olarak örnekleme aralığı ayarlar `Cycles`. Varsayılan süreölçerini 10,000,000 ' dir.  
  
 **Sys**[**:**`Events`]  
 İşletim sistemi çekirdeği (syscalls) profili uygulamasından çağrıları örnekleme olay ayarlar ve isteğe bağlı olarak örnekleme aralığı ayarlar `Events`. Varsayılan Sys aralığı 10'dur.  
  
 **Sayaç:** `Name`[`,Reload`[`,FriendlyName`]]  
 Sayaç tarafından belirtilen CPU performans örnekleme olay ayarlar `Name` ve örnekleme aralığı ayarlar `Reload`.  
  
 **GC**[**:**{**ayırma**&#124;**ömrü**}]  
 .NET bellek verileri toplar. Varsayılan olarak (**ayırma**), her bellek ayırma etkinlikte toplanan veriler. Zaman **ömrü** parametresi belirtilmişse, veri her atık toplama etkinlikte de toplanır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, sayfa hataları için profil oluşturma örnek olayı ayarlayabilirsiniz ve örnekleme aralığı 20 sayfa hataları gösterilmektedir.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Hizmetleri](../profiling/command-line-profiling-of-services.md)