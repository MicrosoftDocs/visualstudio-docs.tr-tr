---
title: 'Nasıl yapılır: komut satırını kullanarak uygulama Istatistikleri toplamak için profil oluşturucuyu bir ASP.NET Web uygulamasına Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c60e63384ab6f391cee1151c8ee20d39ae2e1b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824997"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Uygulama İstatistikleri Verileri Toplamak için bir ASP.NET Web Uygulamasına Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir ASP.NET Web uygulamasına Profiler eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.  

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Bir ASP.NET Web uygulamasından performans verilerini toplamak için, uygun ortam değişkenleri başlatılmalıdır ve Web sunucusunu profil oluşturma için yapılandırmak üzere ASP.NET Web uygulamasını barındıran bilgisayarın yeniden başlatılması gerekir.  

 Ardından, profil oluşturucuyu Web sitenizi barındıran ASP.NET Worker işlemine iliştirebilirsiniz. Profil Oluşturucu uygulamaya eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.  

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş uygulamadan ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.  

## <a name="starting-the-profiler-and-attaching-to-an-aspnet-web-application"></a>Profil oluşturucuyu başlatma ve bir ASP.NET Web uygulamasına Iliştirme  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek için  

1. Bir komut Istemi penceresi açın.  

2. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:  

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]  

   - **/globalsampleon** , örneklemesi sunar.  

   - **/samplelineoff** toplanan verilerin belirli kaynak kodu satırlarına atanmasını devre dışı bırakır. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.  

3. Bilgisayarı yeniden başlatın.  

4. Profil oluşturucuyu başlatın. Tür:**VSPerfCmd** [/Start](../profiling/start.md)**: örnek** [/output](../profiling/output.md)**:** `OutputFile` [ `Options` ]  

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.  

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.  

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                        Açıklama                                                                                                                                                        |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |                   ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.                    |
   |              [/CrossSession](../profiling/crosssession.md)              | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   |    [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                                         Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                                                                                                         |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                                       Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.                                                                                       |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                                         Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.                                                                                          |

5. ASP.NET Web uygulamasını normal şekilde başlatın.  

6. Profil oluşturucuyu ASP.NET Worker işlemine iliştirin. Tür:**VSPerfCmd** [/Attach](../profiling/attach.md)**:**{ `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - `PID` ASP.NET çalışan işleminin işlem KIMLIĞINI belirtir; `ProcName` çalışan işlemin adını belirtir. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.  

   - Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, 1 GH işlemcide saniyede yaklaşık 100 kez olur. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki **VSPerfCmd** seçeneklerinden birini belirtebilirsiniz.  

   |Örnek olay|Description|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|  
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|  
   |[/Counter](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|  
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|  

   - **targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiği zaman profil için CLR sürümünü belirtir. İsteğe bağlı.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Uygulama çalışırken, **VSPerfCmd.exe** seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` **/ProcessOff:**`PID`|Tarafından belirtilen işlem için veri toplamayı başlatır (**/ProcessOn**) veya duraklar (**/ProcessOff**) `PID` .|  
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** , `PID` veya Işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Bir profil oluşturma oturumunu sonlandırmak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını kapatın ve ardından Internet Information Services (IIS) **IISReset** komutunu kullanarak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemini kapatın. Profiler 'ı devre dışı bırakmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın.  

 **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler. Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.  

 **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:  

    - **VSPerfCmd/detach** yazın  

         -veya-  

    - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Çalışan işlemini kapatın.  

2. Profil oluşturucuyu kapatın. Tür:**VSPerfCmd** [/Shutdown](../profiling/shutdown.md)  

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:  

     **VSPerfCmd/globaloff**  

4. Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)
