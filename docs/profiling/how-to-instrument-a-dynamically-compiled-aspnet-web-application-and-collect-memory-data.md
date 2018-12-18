---
title: 'Nasıl yapılır: Profiler komut satırını kullanarak dinamik olarak derlenmiş ASP.NET web uygulamasını ve bellek verileri toplamak izleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9c1d908a29d4255401aaad4567b56be16ce467cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862677"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET web uygulamasını izleme ve profil oluşturucu komut satırını kullanarak bellek verileri toplama
Bu konu nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayrıntılı .NET bellek ayırma ve nesne yaşam süresi verilerini dinamik olarak derlenmiş toplamak için profil oluşturma araçları komut satırı araçlarının [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasını izleme profili oluşturma yöntemi kullanarak.  

> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Performans verileri toplamak için bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, değişiklik *web.config* etkinleştirmek için hedef uygulamanın dosya [VSInstr.exe](../profiling/vsinstr.md) dinamik olarak derlenmiş bir işaretleme aracı Uygulama dosyaları. Daha sonra [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) barındıran sunucuyu yapılandırmak için aracı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması ve uygun ortam değişkenlerini ayarlayarak .NET bellek profili oluşturmayı etkinleştirin ve ardından bilgisayarı yeniden başlatın.  

 Verileri toplamak için profil oluşturucuyu başlatın ve ardından hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. İlgili verileri topladıktan sonra uygulamayı kapatabilir, Internet Information Services (IIS) çalışan işlemi kapatın ve sonra profil oluşturucuyu kapatın.  

 Profil oluşturma işinizi tamamladıktan sonra geri yükleme *web.config* dosya ve özgün durumlarına web sunucusu.  

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulaması ve web sunucusunu yapılandırma  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulaması ve web sunucusunu yapılandırmak için  

1.  Değiştirme *web.config* hedef uygulamanın dosya. Bkz: [nasıl yapılır: izleme ve profil dinamik olarak derlenmiş ASP.NET web uygulamaları için web.config dosyalarını değiştirme](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).  

2.  Web uygulamasını barındıran bilgisayarda bir komut istemi penceresi açın.  

3.  Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

     **VSPerfClrEnv /globaltracegc**  

     veya  

     **VSPerfClrEnv /globaltracegclife**  

    -   **/globaltracegc** bellek ayırma verilerinin toplanmasını etkinleştirir.  

    -   **/globaltracegclife** bellek ayırma verilerinin ve nesne yaşam verisi toplamayı etkinleştirir.  

4.  Bilgisayarı yeniden başlatın.  

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumu çalıştırma  

#### <a name="to-profile-the-aspnet-web-application"></a>ASP.NET web uygulamasının profilini çıkarmak için  

1. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd** [/start](../profiling/start.md) **: izleme** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - **Çalıştığından** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma verilerinin konumunu ve adını belirtir (. *Vsp*) dosyası.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **çalıştığından** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Sahibi olan hesabının isteğe bağlı etki alanı ve kullanıcı adını belirtir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi. Bu seçenek, oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. Adı listelenir **kullanıcı adı** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. Bu seçenek, başka bir oturumda uygulama çalışıyorsa gereklidir. Oturum kimliği listelendiğinden **oturum kimliği** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatıldı başlatır. Kullanım [/globalon](../profiling/globalon-and-globaloff.md) profil oluşturmayı devam ettirmek için. |
   | [/ Sayaç](../profiling/counter.md) **:** `Config` | Belirtilen sayaç işlemci performans bilgilerini toplar `Config`. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. Ayrı bir toplanan ETW olayları (. *etl*) dosyası. |


2. Başlangıç [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] normal şekilde web uygulaması.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hedef uygulama çalışırken, Profil Oluşturucu veri dosyasına verilerin yazılmasını kullanarak durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|  

-   Ayrıca **VSPerfCmd.exe**[/mark](../profiling/mark.md) veri dosyasına bir profil oluşturma işareti eklemek için seçeneği. **/Mark** komut tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı bir metin dizesi ekler. İşaretler profil oluşturucu raporlar ve veri görünümlerindeki verilere filtre için kullanılabilir.  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için hedef kapatmak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, Internet Information Services (IIS), profilli işlemin durdurun ve sonra profil oluşturucuyu kapatın durdurun. Ardından, IIS'yi yeniden başlatın.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1. Kapat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması.  

2. Kapat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi tarafından Internet Information Services (IIS) sıfırlanıyor. Tür:  

    **IISReset/stop**  

3. Profil oluşturucuyu kapatın. Tür:  

    **VSPerfCmd**  [ /Shutdown](../profiling/shutdown.md)  

4. IIS'yi yeniden başlatın. Tür:  

    **IISReset/Start**  

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme  
 Tüm profil oluşturma işlemini tamamladıktan sonra değiştirmek *web.config* dosya, profil oluşturma ortam değişkenlerini temizleyin ve sunucuyu geri yüklemek için bilgisayarı yeniden başlatın ve [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] özgün durumlarına uygulama.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yüklemek için  

1.  Değiştirin *web.config* özgün dosyanın bir kopyasını içeren dosya.  

2.  (İsteğe bağlı). Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfCmd /globaloff**  

3.  Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)
