---
title: 'Nasıl yapılır: Profiler yerel bir bağımsız uygulamaya profil oluşturucu ekleme ve komut satırını kullanarak uygulama istatistikleri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8818936adde24cdae121a3e1de6c27af3e266af1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749029"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Profil Oluşturucu Komut Satırını Kullanarak Yerel bir Bağımsız Uygulamaya Profil Oluşturucu Ekleme ve Uygulama İstatistikleri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiler çalışmaya yerel tek başına (istemci) uygulamasına ekleyip örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçları.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profil Oluşturucu uygulamaya eklendiğinde, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturma oturumunu sona erdirmek için Profiler artık uygulamaya bağlı gerekir ve Profiler açıkça kapatılmalıdır.  

## <a name="attach-the-profiler"></a>Profiler ekleme  
 Profiler Profiler'ı kullanarak bir hedef uygulamaya iliştirmek için kullandığınız **VSPerfCmd/start** ve **/ ekleme** Profiler'ı başlatıp hedeflenen uygulamaya eklemek için Seçenekler. Belirtebileceğiniz **/start** ve **/ ekleme** ve onların kendi seçenekleri de tek bir komut satırı. Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulamanın başlatıldığı sırada veri toplamayı duraklatma seçeneğinin. Daha sonra **/globalon** veri toplanmasını başlatmak için.  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profiler çalışan bir .NET Framework uygulamasına eklemek için  

1. Bir komut istemi penceresi açın.  

2. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd /start:sample/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: örnek** seçeneği profil oluşturucuyu başlatır.  

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.  

   |                                 Seçenek                                  |                                                                                                                                                     Açıklama                                                                                                                                                     |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                 Profilli işlemin sahibi olan hesabının etki alanı ve kullanıcı adını belirtir. Bu seçenek, yalnızca oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir.                 |
   |              [/ crosssession](../profiling/crosssession.md)              | Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                      Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                                                                                                      |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                    İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır.                                                                                    |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                      Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.                                                                                       |


3. Profil Oluşturucu hedef uygulamaya iliştirin. Tür:  

    **VSPerfCmd**[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [`Sample Event`]    

    `PID` hedef uygulamanın işlem Kimliğini belirtir. `ProcessName` işlemin adını belirtir. Belirttiğiniz gerçekleştiriyorsanız `ProcessName` ve aynı ada sahip birden çok işlem çalışıyorsa, sonuçların tahmin edilemeyeceğine. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

    Varsayılan olarak, performans verisi her 10.000.000 durdurulmamış işlemci saat örneklenen döngüsü. Yaklaşık 100 kez her saniye bir adet 1GH işlemcide budur. Saat döngüsü aralığı değiştirmek veya farklı örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.  

   |Örnek olay|Açıklama|  
   |------------------|-----------------|  
   |[/ Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığı tarafından belirtilen durdurulmamış saati döngüleri sayısını değiştirir `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Örnekleme olay sayfa hataları değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasında sayfa hatalarının sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Örnekleme olayını, işletim sisteminin çekirdeğine (syscalls) işlemden sisteme çağrı yapmak değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasındaki çağrıların sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ Sayaç](../profiling/counter.md) **:** `Config`|İşlemci performans sayacı ve belirtilen aralık için örnekleme olay ve aralığını değiştirir `Config`.|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, başlatmak ve Profil Oluşturucu veri dosyasına veri yazılmasını durdurmak için VSPerfCmd.exe Seçenekleri'ni kullanabilirsiniz. Veri toplama denetlenmesi size program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) tarafından belirtilen işlem için veri toplamayı `PID`.|  
    |[/ ekleme](../profiling/attach.md) **:** `PID` [/ detach](../profiling/detach.md)|**/ ekleme** tarafından belirtilen işlem için veri toplamaya başlar `PID`. **/ detach** tüm işlemler için veri toplamayı durdurur.|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucu oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucu açıkça kapatılmalıdır. Uygulamayı kapatarak veya çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadaki profil oluşturucuyu ayırabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd/shutdown** profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdaki adımları gerçekleştirin.  

    -   Tür **VSPerfCmd / detach**  

         veya  

    -   Hedef uygulamayı kapatın.  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

3.  (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfClrEnv / kapatma**  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)



