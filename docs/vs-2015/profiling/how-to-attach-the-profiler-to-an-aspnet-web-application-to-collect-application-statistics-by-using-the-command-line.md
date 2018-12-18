---
title: 'Nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplamak için bir ASP.NET Web uygulamasına Profiler ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bed31651ca52097675c9584091b618ea8757192
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762445"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Uygulama İstatistikleri Verileri Toplamak için bir ASP.NET Web Uygulamasına Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir ASP.NET Web uygulamasına profil oluşturucu örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçları.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme, komut satırı profil araçlarıyla özel yordamlar gerektirir. Bkz: [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Bir ASP.NET Web uygulamasından performans verilerini toplamak için uygun ortam değişkenleri başlatılmalıdır ve profil oluşturma için Web sunucusunu yapılandırmak için ASP.NET Web uygulamasını barındıran bilgisayarın yeniden başlatılması gerekiyor.  

 Daha sonra Web sitenizi barındıran ASP.NET işçi işlemine profil oluşturucuyu iliştirin. Profil Oluşturucu uygulamaya eklendiğinde, duraklatma ve veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sona erdirmek için profil oluşturulmuş uygulamadan ayrılması ve profil oluşturucu açıkça kapatılmalıdır. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.  

## <a name="starting-the-profiler-and-attaching-to-an-aspnet-web-application"></a>Profiler'ı başlatıp bir ASP.NET Web uygulamasına ekleme  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profiler bir ASP.NET Web uygulamasına eklemek  

1. Bir komut istemi penceresi açın.  

2. Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   -   **/globalsampleon** örnekleme sağlar.  

   -   **/samplelineoff** toplanan verilerin belirli kaynak kod satırlarına atamayı devre dışı bırakır. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.  

3. Bilgisayarı yeniden başlatın.  

4. Profil oluşturucuyu başlatın. Türü:**VSPerfCmd** [/start](../profiling/start.md)**: örnek** [/output](../profiling/output.md)**:**`OutputFile`[`Options`]  

   - **/Start:sample** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçenekler herhangi birini kullanabilirsiniz **/start:sample** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                        Açıklama                                                                                                                                                        |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                   ASP.NET çalışan işlemine sahip hesabın etki alanı ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir.                    |
   |              [/ crosssession](../profiling/crosssession.md)              | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                         Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                       İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır.                                                                                       |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.                                                                                          |


5. Normal yolla ASP.NET Web uygulaması başlatın.  

6. Profil oluşturucuyu ASP.NET işçi işlemine iliştirin. Türü:**VSPerfCmd** [/ ekleme](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:**`Version`]  

   -   `PID` ASP.NET işçi işlemin işlem Kimliğini belirtir; `ProcName` işçi işlemin adını belirtir. Windows Görev Yöneticisi'nde, işlem kimliklerini ve isimlerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

   -   Varsayılan olarak, performans verisi her 10.000.000 durdurulmamış işlemci saat örneklenen döngüsü. Yaklaşık saniyede 100 adet 1GH işlemcide budur. Aşağıdakilerden birini belirtebileceğiniz **VSPerfCmd** seçenekleri saat döngüsü aralığı değiştirmek veya farklı örnekleme olayı belirtmek için.  

   |Örnek olay|Açıklama|  
   |------------------|-----------------|  
   |[/ Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığı tarafından belirtilen durdurulmamış saati döngüleri sayısını değiştirir `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Örnekleme olay sayfa hataları değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasında sayfa hatalarının sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Örnekleme olayını, işletim sisteminin çekirdeğine (syscalls) işlemden sisteme çağrı yapmak değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasındaki çağrıların sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ Sayaç](../profiling/counter.md) **:** `Config`|İşlemci performans sayacı ve belirtilen aralık için örnekleme olay ve aralığını değiştirir `Config`.|  
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Ortak dil çalışma zamanı bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profilini (CLR) sürümünü belirtir.|  

   -   **targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profiline CLR'nin sürümünü belirtir. İsteğe bağlı.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Uygulama çalışırken kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz **VSPerfCmd.exe** seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) tarafından belirtilen işlem için veri toplamayı `PID`.|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** tarafından belirtilen işlem için veri toplamaya başlar `PID` veya işlem adı (ProcName). **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için kapatma [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını ve ardından Internet Information Services (IIS) **IISReset** kapatmak için komut [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi. Çağrı **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız.  

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler. Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.  

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdakilerden birini yapın:  

    -   Tür **VSPerfCmd / detach**  

         veya  

    -   Kapat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi.  

2.  Profil oluşturucuyu kapatın. Türü:**VSPerfCmd**  [ /Shutdown](../profiling/shutdown.md)  

3.  (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfCmd /globaloff**  

4.  Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)



