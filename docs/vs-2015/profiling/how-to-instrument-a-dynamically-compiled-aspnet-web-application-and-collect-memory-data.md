---
title: 'Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET Web izleme Profiler komut satırını kullanarak uygulama ve bellek verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccdf566de19a193bf7dfca58831c7a7be2734619
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790792"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil Oluşturucu Komut Satırını Kullanarak Dinamik Olarak Derlenmiş bir ASP.NET Web Uygulamasını İzleme ve Bellek Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ayrıntılı .NET bellek ayırma ve nesne yaşam süresi verilerini dinamik olarak derlenmiş toplamak için profil oluşturma araçları komut satırı araçlarının [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını izleme profili oluşturma yöntemi kullanarak.  

> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64 bit bilgisayarlarda araçların 64-bit hem 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Performans verileri toplamak için bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını etkinleştirmek için hedef uygulamanın web.config dosyasını değiştirme [VSInstr.exe](../profiling/vsinstr.md) dinamik olarak derlenmiş uygulama dosyaları araç haline getirmek için aracı. Daha sonra [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) barındıran sunucuyu yapılandırmak için aracı [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması ve uygun ortam değişkenlerini ayarlayarak .NET bellek profili oluşturmayı etkinleştirin ve ardından bilgisayarı yeniden başlatın.  

 Verileri toplamak için profil oluşturucuyu başlatın ve ardından hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. İlgili verileri topladıktan sonra uygulamayı kapatabilir, Internet Information Services (IIS) çalışan işlemi kapatın ve sonra profil oluşturucuyu kapatın.  

 Web.config dosyasını ve Web sunucusu profil oluşturma işinizi tamamladıktan sonra özgün durumlarına geri yükleyin.  

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web uygulaması ve Web sunucusunu yapılandırma  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web uygulaması ve Web sunucusunu yapılandırmak için  

1.  Hedef uygulamanın web.config dosyasını değiştirin. Bkz: [nasıl yapılır: araç için Web.Config dosyalarını değiştirme ve dinamik olarak derlenmiş ASP.NET Web uygulamalarının profilini](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  

2.  Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.  

3.  Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

     **VSPerfClrEnv /globaltracegc**  

     veya  

     **VSPerfClrEnv /globaltracegclife**  

    -   **/globaltracegc** bellek ayırma verilerinin toplanmasını etkinleştirir.  

    -   **/globaltracegclife** bellek ayırma verilerinin ve nesne yaşam verisi toplamayı etkinleştirir.  

4.  Bilgisayarı yeniden başlatın.  

## <a name="running-the-profiling-session"></a>Profil oluşturma oturumu çalıştırma  

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET Web uygulamasının profilini çıkarmak için  

1. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd** [/start](../profiling/start.md) **: izleme** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - **Çalıştığından** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **çalıştığından** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                          Açıklama                                                                                                                                                          |
   |-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Sahibi olan hesabının isteğe bağlı etki alanı ve kullanıcı adını belirtir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi. Bu seçenek, oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. Adı, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir. |
   |              [/ crosssession](../profiling/crosssession.md)              |              Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. Bu seçenek, başka bir oturumda uygulama çalışıyorsa gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**.               |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                                 Profil Oluşturucu veri koleksiyonu duraklatıldı başlatır. Kullanım [/globalon](../profiling/globalon-and-globaloff.md) profil oluşturmayı devam ettirmek için.                                                                                                 |
   |           [/ Sayaç](../profiling/counter.md) **:** `Config`            |                                                                                Belirtilen sayaç işlemci performans bilgilerini toplar `Config`. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir.                                                                                 |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                           Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.                                                                                                                           |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                         İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır.                                                                                         |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                           Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.                                                                                            |


2. Başlangıç [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] normal şekilde Web uygulaması.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, Profil Oluşturucu veri dosyasına verilerin yazılmasını kullanarak durdurmayla ve veri toplamayı kontrol edebilirsiniz **VSPerfCmd.exe** seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|  

-   Ayrıca **VSPerfCmd.exe**[/mark](../profiling/mark.md) veri dosyasına bir profil oluşturma işareti eklemek için seçeneği. **/Mark** komut tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı bir metin dizesi ekler. İşaretler profil oluşturucu raporlar ve veri görünümlerindeki verilere filtre için kullanılabilir.  

## <a name="ending-the-profiling-session"></a>Profil Araçları oturumunu sonlandırma  
 Profil oluşturma oturumunu sona erdirmek için hedef kapatmak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, Internet Information Services (IIS), profilli işlemin durdurun ve sonra profil oluşturucuyu kapatın durdurun. Ardından, IIS'yi yeniden başlatın.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Kapat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması.  

2.  Kapat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi tarafından Internet Information Services (IIS) sıfırlanıyor. Tür:  

     **IISReset/stop**  

3.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd**  [ /Shutdown](../profiling/shutdown.md)  

4.  IIS'yi yeniden başlatın. Tür:  

     **IISReset/Start**  

## <a name="restoring-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme  
 Tüm profil oluşturma işlemini tamamladıktan sonra web.config dosyasını değiştirin, profil oluşturma ortam değişkenlerini temizleyin ve sunucuyu geri yüklemek için bilgisayarı yeniden başlatın ve [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] özgün durumlarına uygulama.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için  

1.  Özgün dosyanın bir kopyasını web.config dosyasını değiştirin.  

2.  (İsteğe bağlı). Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfCmd /globaloff**  

3.  Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET Bellek Verisi Görünümleri](../profiling/dotnet-memory-data-views.md)



