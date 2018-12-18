---
title: 'Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET Web uygulamasını izleme ve ayrıntılı zamanlama verileri Profiler ile komut satırını kullanarak toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: bcc5d167fdd53a597fb171881ae61281c8280c8d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894579"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET web uygulamasını izleme ve komut satırını kullanarak profil oluşturucu ayrıntılı zamanlama verileri toplama

Bu makalede, dinamik olarak derlenmiş için ayrıntılı zamanlama verileri toplamak için Visual Studio Profil Araçları komut satırı araçlarını kullanmayı açıklar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yöntemi profil oluşturma Araçları'nı kullanarak uygulama.

> [!NOTE]
> Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Performans verileri toplamak için bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, değişiklik *web.config* etkinleştirmek için hedef uygulamanın dosya [VSInstr.exe](../profiling/vsinstr.md) dinamik olarak derlenmiş bir işaretleme aracı Uygulama dosyaları. Daha sonra [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) oluşturmayı etkinleştirmek için web sunucusuna uygun ortam değişkenlerini ayarlamak için araç ve ardından bilgisayarı yeniden başlatın.

Profil oluşturucuyu başlatın ve ardından hedef uygulamayı çalıştırın. Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturmayı tamamladığınızda, uygulamayı kapatın, Internet Information Services (IIS) çalışan işlemi kapatın ve sonra profil oluşturucuyu kapatın. Profil oluşturma işinizi tamamladıktan sonra geri yükleme *web.config* dosya ve özgün durumlarına Web sunucusu.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET web uygulaması ve web sunucusunu yapılandırma

1. Değiştirme *web.config* hedef uygulamanın dosya. Bkz: [nasıl yapılır: izleme ve profil dinamik olarak derlenmiş ASP.NET web uygulamaları için web.config dosyalarını değiştirme](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** izleme metodunu kullanarak profil oluşturma sağlar.

4. Bilgisayarı yeniden başlatın.

## <a name="run-the-profiling-session"></a>Profil oluşturma oturumu çalıştırma

1. Bir komut istemi penceresi açın.

2. Profil oluşturucuyu başlatın. Tür:

     **VSPerfCmd**[/start](../profiling/start.md) **: izleme**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **Çalıştığından** seçeneği profil oluşturucuyu başlatır.

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma verilerinin konumunu ve adını belirtir (. *Vsp*) dosyası.

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **çalıştığından** seçeneği.

     > [!NOTE]
     > **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | ASP.NET çalışan işlemine sahip hesabın etki alanı ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi listelenen **kullanıcı adı** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. |
     | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı listelenen **oturum kimliği** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri koleksiyonu duraklatıldı başlatır. Kullanım [/globalon](../profiling/globalon-and-globaloff.md) profil oluşturmayı devam ettirmek için. |
     | [/ Sayaç](../profiling/counter.md) **:** `Config` | Belirtilen işlemci performans sayacından bilgi toplar `Config`. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
     | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
     | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. Ayrı bir toplanan ETW olayları (. *etl*) dosyası. |


3. Başlangıç [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] normal şekilde web uygulaması.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken, Profil Oluşturucu veri dosyasına verilerin yazılmasını kullanarak durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.

- Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|

- Ayrıca **VSPerfCmd.exe**[/mark](../profiling/mark.md) veri dosyasına bir profil oluşturma işareti eklemek için seçeneği. **/Mark** komut tanımlayıcı, bir zaman damgası ve isteğe bağlı kullanıcı tanımlı bir metin dizesi ekler. İşaretler profil oluşturucu raporlar ve veri görünümlerindeki verilere filtre için kullanılabilir.

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme

Profil oluşturma oturumunu sona erdirmek için hedef kapatmak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, profili oluşturulan işlemini durdurun ve sonra profil oluşturucuyu kapatın, IIS'yi sıfırlayın.

1. Kapat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması.

2. Kapat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi tarafından Internet Information Services (IIS) sıfırlanıyor. Tür:

     **IISReset/stop**

3. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)

4. IIS'yi yeniden başlatın. Tür:

     **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Uygulama ve bilgisayar yapılandırmasını geri yükleme

Tüm profil oluşturma işlemini tamamladıktan sonra değiştirmek *web.config* dosya, profil oluşturma ortam değişkenlerini temizleyin ve uygulama ve sunucu profil oluşturmadan önce andaki durumlarına geri yüklemek için bilgisayarı yeniden başlatın.

1. Değiştirin *web.config* özgün dosyanın bir kopyasını içeren dosya.

2. Profil oluşturma ortam değişkenlerini temizleyin. Tür:

     **VSPerfCmd /globaloff**

3. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
[İzleme metodu veri görünümleri](../profiling/instrumentation-method-data-views.md)