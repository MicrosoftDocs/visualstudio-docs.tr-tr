---
title: 'Nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplama ve Profiler ile bağımsız bir uygulama başlatma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0d06026eda41b5c7f340655bf316c2818b0bbed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765341"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil Oluşturucu ile Bağımsız bir Uygulama Başlatma ve Komut Satırını Kullanarak Uygulama İstatistikleri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tek başına (istemci) uygulamasına başlatmak ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçları.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme, komut satırı profil araçlarıyla özel yordamlar gerektirir. Bkz: [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)  

 Profil oluşturucu komut satırı araçlarını kullanmak için yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Visual Studio komut penceresinden Visual Studio'nun yüklü bir makinede profil oluşturma araçları çalıştırabilirsiniz.  

1.  Profil oluşturma araçlarından çalıştırıyorsanız Visual Studio olduğu bir makineye Visual Studio komut penceresi kümelerini doğru yolları yüklü. Üzerinde **Araçları** menüsünde seçin **VS komut istemi**  

> [!NOTE]
>  Profil Oluşturma Araçlarının komut satırı araçları, Visual Studio yükleme dizini altındaki \Team Tools\Performance Tools alt dizininde yer alır. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-application-with-the-profiler"></a>Profiler ile uygulama başlatılıyor  
 Profil oluşturucuyu kullanarak bir hedef uygulamayı başlatmak için VSPerfCmd kullanın **/start** ve **/başlatma** profil oluşturucuyu başlatın ve uygulamayı başlatmak için Seçenekler. Belirtebileceğiniz **/start** ve **/başlatma** ve onların kendi seçenekleri de tek bir komut satırı.  

 Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulamanın başlatıldığı sırada veri toplamayı duraklatma seçeneğinin. Daha sonra **/globalon** veri toplanmasını başlatmak için.  

#### <a name="to-start-an-application-by-using-the-profiler"></a>Profiler'ı kullanarak bir uygulamayı başlatmak için  

1. Bir komut istemi penceresi açın.  

2. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd /start:sample/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: örnek** seçeneği profil oluşturucuyu başlatır.  

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.  

   |                              Seçenek                              |                                                                  Açıklama                                                                  |
   |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` |                                   Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                   |
   |      [/automark](../profiling/automark.md) **:** `Interval`      | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   |    [/Events](../profiling/events-vsperfcmd.md) **:** `Config`    |   Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.    |


3. Hedef uygulamayı başlatın. Türü:**VSPerfCmd/Launch:** `appName` [`Options`] [`Sample Event`]  

    Bir veya daha fazla aşağıdaki seçeneklerle kullanabileceğiniz **/başlatma** seçeneği.  

   |Seçenek|Açıklama|  
   |------------|-----------------|  
   |[args](../profiling/args.md) **:** `Arguments`|Hedef uygulama için geçirilecek komut satırı bağımsız değişkenleri içeren bir dize belirtir.|  
   |[/ Console](../profiling/console.md)|Hedef komut satırı uygulaması ayrı bir pencerede başlatır.|  

    Varsayılan olarak, performans verisi her 10.000.000 durdurulmamış işlemci saat örneklenen döngüsü. Yaklaşık bir saat 10 saniyede bir 1 GHz işlemci üzerinde budur. Saat döngüsü aralığı değiştirmek veya farklı örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.  

   |Örnek olay|Açıklama|  
   |------------------|-----------------|  
   |[/ Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığı tarafından belirtilen durdurulmamış saati döngüleri sayısını değiştirir `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Örnekleme olay sayfa hataları değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasında sayfa hatalarının sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Örnekleme olayını, işletim sisteminin çekirdeğine (syscalls) işlemden sisteme çağrı yapmak değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasındaki çağrıların sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ Sayaç](../profiling/counter.md) **:** `Config`|İşlemci performans sayacı ve belirtilen aralık için örnekleme olay ve aralığını değiştirir `Config`.|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, Profil Oluşturucu veri dosyasına verilerin yazılmasını kullanarak durdurmayla ve veri toplamayı kontrol edebilirsiniz **VSPerfCmd.exe** seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** tarafından belirtilen işlem için veri toplamaya başlar `PID` veya işlem adı (ProcName). **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucu için profili oluşturulmuş herhangi bir işlem bağlanmalıdır değil ve profil oluşturucu açıkça kapatılmalıdır. Uygulamayı kapatarak veya çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadaki profil oluşturucuyu ayırabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd/shutdown** profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdaki adımlardan birini gerçekleştirin:  

    -   Hedef uygulamayı kapatın.  

         veya  

    -   Tür **VSPerfCmd / detach**  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)



