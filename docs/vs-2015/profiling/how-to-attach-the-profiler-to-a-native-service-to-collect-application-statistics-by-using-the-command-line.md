---
title: 'Nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplamak için yerel bir hizmete Profiler ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3677f252fc4c7b415173bf7e1c39c459b7c00b9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740935"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Uygulama İstatistikleri Toplamak için bir Yerel Hizmete Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir yerel hizmete profil oluşturucu ekleme ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçları.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64 bit bilgisayarlarda araçların 64-bit hem 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profiler servise bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir.  

## <a name="starting-the-application-with-the-profiler"></a>Profiler ile uygulama başlatılıyor  
 Bir yerel hizmete profil oluşturucu ekleme için kullandığınız **VSPerfCmd.exe**[/start](../profiling/start.md) ve [/ ekleme](../profiling/attach.md) ve profil oluşturucuyu başlatıp hedeflenen uygulamaya eklemek için Seçenekler. Belirtebileceğiniz **/start** ve **/ ekleme** ve onların kendi seçenekleri de tek bir komut satırı. Ayrıca ekleyebilirsiniz [/globaloff](../profiling/globalon-and-globaloff.md) hedef uygulamanın başlatıldığı sırada veri toplamayı duraklatma seçeneğinin. Ardından [/globalon](../profiling/globalon-and-globaloff.md) veri toplamaya başlamak için.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profiler'ı bir yerel servise bağlamak için  

1. Gerekirse, hizmeti başlatın.  

2. Bir komut istemi penceresi açın.  

3. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd /start:sample**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **/Start:sample** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle hizmetler için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                            Açıklama                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |        Profilli işlemin sahibi olan hesabının etki alanı ve kullanıcı adını belirtir. Bu seçenek, yalnızca oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir.         |
   |              [/ crosssession](../profiling/crosssession.md)              | Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. Bu seçenek, başka bir oturumda uygulama çalışıyorsa gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.                                                                              |


4. Hizmete profil oluşturucu iliştirin. Tür:  

    **VSPerfCmd / ekleme:** `PID` [`Sample Event`]  

    `PID` hedef uygulamanın işlem Kimliğini belirtir. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

    Varsayılan olarak, performans verisi her 10.000.000 durdurulmamış işlemci saat örneklenen döngüsü. 10 saniyede bir adet 1GH işlemcide yaklaşık bir kez budur. Saat döngüsü aralığı değiştirmek veya farklı örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.  

   |Örnek olay|Açıklama|  
   |------------------|-----------------|  
   |[/ Timer](../profiling/timer.md) **:** `Interval`|Örnekleme aralığı tarafından belirtilen durdurulmamış saati döngüleri sayısını değiştirir `Interval`.|  
   |[/PF](../profiling/pf.md)[**:**`Interval`]|Örnekleme olay sayfa hataları değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasında sayfa hatalarının sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Örnekleme olayını, işletim sisteminin çekirdeğine (syscalls) işlemden sisteme çağrı yapmak değiştirir. Varsa `Interval` belirtilmemişse, örnekler arasındaki çağrıların sayısını ayarlar. Varsayılan 10'dur.|  
   |[/ Sayaç](../profiling/counter.md) **:** `Config`|İşlemci performans sayacı ve belirtilen aralık için örnekleme olay ve aralığını değiştirir `Config`.|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken kullanabileceğiniz **VSPerfCmd.exe** Profil Oluşturucu veri dosyasına verilerin yazılmasını başlatıp için Seçenekler. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |**/ ekleme:** {`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ ekleme** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/ detach** bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için profil oluşturucunun hizmetten ayrılması ve açıkça kapatılmalıdır. Hizmeti durdurarak veya çağırarak örnekleme yöntemiyle profili bir yerel hizmete ayırabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdakilerden birini yapın:  

    -   Hizmeti durdurun.  

         veya  

    -   Tür **VSPerfCmd / detach**  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd/Shutdown**  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)



