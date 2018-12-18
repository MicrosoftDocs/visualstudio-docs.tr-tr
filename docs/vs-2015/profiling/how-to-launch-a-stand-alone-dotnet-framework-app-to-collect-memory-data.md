---
title: 'Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için bağımsız bir .NET Framework uygulamasını Profiler ile başlatma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 207fc9a02be3557341bfad95d6fd32943557478a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757438"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Bellek Verileri Toplamak için Profil Oluşturucu ile Bağımsız bir .NET Framework Uygulamasını Başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir .NET Framework bağımsız (istemci) uygulamasına başlatmak ve bellek verileri toplamak için profil oluşturma araçları komut satırı araçları.  

 Profil oluşturma oturumunu, üç bölümden oluşur:  

-   Profil oluşturucuyu kullanarak uygulama başlatılıyor.  

-   Profil oluşturma verilerinin toplanması.  

-   Profil oluşturma oturumunu sona erdirme.  

> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-application-with-the-profiler"></a>Profiler ile uygulama başlatılıyor  
 Profil oluşturucuyu kullanarak bir hedef uygulamayı başlatmak için kullandığınız **VSPerfCmd.exe/start** ve **/başlatma** profil oluşturucuyu başlatın ve uygulamayı başlatmak için Seçenekler. Belirtebileceğiniz **/start** ve **/başlatma** ve onların kendi seçenekleri bir komut satırında.  

 Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulamanın veri toplamayı durdurmak duraklatmak için Seçenekler. Daha sonra **/globalon** veri toplanmasını başlatmak için.  

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


3. Hedef uygulamayı başlatın. Tür:  

    **VSPerfCmd**[/başlatma](../profiling/launch.md) **:** `appName` **/gc:**{**ayırma**&#124;**yaşam süresi** }[`Options`]    

   - [/Gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` seçeneği, .NET Framework bellek verileri toplamak için gereklidir. Anahtar sözcüğü parametresi bellek ayırma verilerini toplamak için veya hem bellek ayırma hem de nesne ömür verilerini toplamak için etkinleştirilip etkinleştirilmeyeceğini belirtir.  

     |Anahtar sözcüğü|Açıklama|  
     |-------------|-----------------|  
     |**ayırma**|Yalnızca bellek ayırma verisini toplayın.|  
     |**Yaşam süresi**|Hem bellek ayırma ve nesne yaşam süresi verisi toplar.|  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/başlatma** seçeneği.  

   |Seçenek|Açıklama|  
   |------------|-----------------|  
   |[args](../profiling/args.md) **:** `Arguments`|Hedef uygulama için geçirilecek komut satırı bağımsız değişkenleri içeren bir dize belirtir.|  
   |[/ Console](../profiling/console.md)|Hedef komut satırı uygulaması ayrı bir pencerede başlatır.|  
   |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.|  
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Ortak dil çalışma zamanı bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profilini (CLR) sürümünü belirtir.|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz **VSPerfCmd.exe** seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplamayı (`PID`).|  
    |[/ ekleme](../profiling/attach.md) **:** `PID` [/ detach](../profiling/detach.md)|**/ ekleme** tarafından belirtilen işlem için veri toplamaya başlar `PID` (işlem kimliği). **/ detach** tüm işlemler için veri toplamayı durdurur.|  

-   Ayrıca **VSPerfCmd.exe**[/mark](../profiling/mark.md) veri dosyasına bir profil oluşturma işareti eklemek için seçeneği. **/Mark** komut tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı bir metin dizesi ekler. İşaretler, verilere filtre uygulamak için kullanılabilir.  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucu oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucu açıkça kapatılmalıdır. Uygulamayı kapatarak veya çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadaki profil oluşturucuyu ayırabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdaki adımlardan birini gerçekleştirin:  

    -   Hedef uygulamayı kapatın.  

         veya  

    -   Tür **VSPerfCmd / detach**  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET Bellek Verisi Görünümleri](../profiling/dotnet-memory-data-views.md)



