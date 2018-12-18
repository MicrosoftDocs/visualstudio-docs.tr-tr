---
title: 'Nasıl yapılır: bağımsız bir .NET Framework bileşenini izleme ve komut satırını kullanarak Profiler ile bellek verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6e2191469d313aca8506ccc86ddc6ab096f8e390
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842150"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Nasıl yapılır: tek başına bir .NET Framework bileşenini izleme ve komut satırını kullanarak profil oluşturucu ile bellek verileri toplama
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .exe veya .dll gibi tek başına bir uygulamanın bir .NET Framework bileşenini izleme Profil Araçları komut satırı araçlarını kullanarak dosya ve profil oluşturucuyu kullanarak bellek bilgiler toplayabilir.  

> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* Visual Studio yükleme dizininin alt. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  


 Araçlar yöntemini kullanarak bir .NET Framework bileşeni bellek verileri toplamak için kullandığınız [VSInstr.exe](../profiling/vsinstr.md) aracını bileşenin belgelenmiş bir sürümünü oluşturmak için ve [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) Profil oluşturma ortamı değişkenlerini başlatmak için aracı. Ardından kullanarak profil oluşturucuyu başlatın *VSPerfCmd.exe* aracı.  

 Araçlı bileşen yürütüldüğünde, bellek verileri bir veri dosyasına otomatik olarak toplanır. Duraklatma ve profil oluşturma oturumu sırasında veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sona erdirmek için hedef uygulamayı kapatın ve açıkça profil oluşturucuyu kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.  

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek  

1. Bir komut istemi penceresi açın.  

2. Kullanım **Vsınstr** aracı hedef uygulamanın belgelenmiş bir sürümünü oluşturmak için.  

3. .NET Framework'te profil oluşturma ortamı değişkenlerini başlatın. Tür:  

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}  

   -   **/Tracegc** ve **/tracegclife** seçenekleri sadece bellek ayırma verilerini toplamak için veya hem bellek ayırma hem de nesne ömür verilerini toplamak için ortam değişkenlerini başlatın.  

       |Seçenek|Açıklama|  
       |------------|-----------------|  
       |**/tracegc**|Yalnızca bellek ayırma verilerinin toplanmasını etkinleştirir.|  
       |**/tracegclife**|Hem bellek ayırma ve nesne yaşam verisi toplanmasını etkinleştirir.|  

4. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd çalıştığından/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: izleme** seçeneği profil oluşturucuyu başlatır.  

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma verilerinin konumunu ve adını belirtir (. *Vsp*) dosyası.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **çalıştığından** seçeneği.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Profilli işlemin sahibi olan hesabının etki alanı ve kullanıcı adını belirtir. Bu seçenek, yalnızca oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi kullanıcı adı sütununda listelenir **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. Bu seçenek, başka bir oturumda uygulama çalışıyorsa gereklidir. Oturum tanımlayıcısı listelenen **oturum kimliği** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri toplamayı başlatmak için duraklatıldı, ekleme **/globaloff** seçeneğini **/start** komut satırı. Kullanım **/globalon** profil oluşturmayı devam ettirmek için. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   | [/ Sayaç](../profiling/counter.md) **:** `Config` | Config içerisinde belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [Olayları](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. Ayrı bir toplanan ETW olayları (. *etl*) dosyası. |


5. Hedef uygulama komut istemi penceresinden başlatın.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hedef uygulama çalışırken, kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplamayı (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Araçlı bileşeni çalıştıran uygulamayı kapatın ve sonra çağrı **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamayı kapatın.  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd/Shutdown**  

3.  (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfCmd / kapatma**  

## <a name="see-also"></a>Ayrıca bkz.  
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)