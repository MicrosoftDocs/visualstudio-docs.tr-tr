---
title: 'Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için bağımsız bir .NET Framework uygulamasını Profiler ile başlatma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caed852f51b6e3442274452564f1ef6807d1adec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803142"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Eşzamanlılık Verileri Toplamak için Bağımsız bir .NET Framework Uygulamasını Başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir .NET Framework bağımsız (istemci) uygulamasına başlatmak ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için profil oluşturma araçları komut satırı araçları  

> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64 bit bilgisayarlarda araçların 64-bit hem 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturma oturumunu sona erdirmek için Profiler artık uygulamaya bağlı gerekir ve Profiler açıkça kapatılmalıdır.  

## <a name="starting-the-application-with-the-profiler"></a>Profiler ile uygulama başlatılıyor  
 Profiler bir .NET Framework hedef uygulamasını başlatmak için VSPerfClrEnv.exe .NET Framework'te profil oluşturma değişkenlerini ayarlamak için kullanın. Ardından VSPerfCmd kullandığınız **/start** ve **/başlatma** Profiler'ı başlatın ve uygulamayı başlatmak için Seçenekler. Belirtebileceğiniz **/start** ve **/başlatma** ve onların kendi seçenekleri de tek bir komut satırı. Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulama başladığında veri toplamayı duraklatma seçeneğinin komut satırına. Daha sonra **/globalon** üzerinde veri toplanmasını başlatmak için ayrı bir komut satırı.  

#### <a name="to-start-an-application-with-the-profiler"></a>Profiler ile bir uygulamayı başlatmak için  

1. Bir komut istemi penceresi açın.  

2. Profil oluşturucuyu başlatın. Tür:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/ Çıkış:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) seçeneği profil oluşturucuyu başlatır.  


     |                                     |                                                                        |
     |-------------------------------------|------------------------------------------------------------------------|
     |       **/Start:concurrency**        | Hem kaynak çekişmesini hem de iş parçacığı yürütme verisi toplamayı etkinleştirir. |
     | **/Start:concurrency, resourceonly** |           Yalnızca kaynak Çekişme verisi toplamayı etkinleştirir.            |
     |  **/Start:concurrency, threadonly**  |             Tek iş parçacığı yürütme veri toplanmasını sağlar.             |


   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:concurrency** seçeneği.  

   |                               Seçenek                               |                                                                  Açıklama                                                                  |
   |--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username` |                       Profil oluşturucuya erişim verilebilmesi için hesabın kullanıcı adını ve isteğe bağlı etki alanını belirtir.                        |
   |           [/ crosssession](../profiling/crosssession.md)            |                                            Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma.                                            |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                   Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                   |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:** `Config`     |   Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.    |


3. Hedef uygulamayı başlatın. Tür:  

    **VSPerfCmd**[/başlatma](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]    

    Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/başlatma** seçeneği.  

   |Seçenek|Açıklama|  
   |------------|-----------------|  
   |[args](../profiling/args.md) **:** `Arguments`|Hedef uygulama için geçirilecek komut satırı bağımsız değişkenleri içeren bir dize belirtir.|  
   |[/ Console](../profiling/console.md)|Hedef komut satırı uygulaması ayrı bir pencerede başlatır.|  
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Ortak dil çalışma zamanı bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profilini (CLR) sürümünü belirtir.|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, VSPerfCmd.exe seçeneklerini kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz. Veri toplama denetlenmesi size program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

1.  Aşağıdaki VSPerfCmd.exe seçenek çiftleri başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** işlem kimliği tarafından belirtilen işlem için veri toplamaya başlar (`PID`) veya işlem adı (ProcName). **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Profili oluşturulan uygulamayı kapatarak veya çağırarak eşzamanlılık verileri toplama işlemini durdurabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırmak **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdakilerden birini yapın.  

    -   Hedef uygulamayı kapatın.  

         veya  

    -   Tür **VSPerfCmd / detach**  

2.  Profil oluşturucuyu kapatın  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık Verileri Toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)



