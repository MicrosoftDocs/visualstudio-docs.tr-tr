---
title: Bellek verileri toplamak için bir .NET hizmetine profil oluşturucu ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bd51a323ca369b30dcba32d3f480756d3e95f1f6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052734"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için bir .NET hizmetine profil oluşturucu ekleme
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] iliştirme için profil oluşturma araçları komut satırı araçlarını bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ve bellek verileri toplamak. Bellek ayırmalarının sayısı ve boyutu hakkında veri toplayabilir ve ayrıca, bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Bellek verileri toplamak için bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hizmeti kullandığınız [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) hizmeti barındıran bilgisayardaki uygun ortam değişkenlerini başlatmak üzere. Bilgisayarın, profil oluşturma için yapılandırılmak üzere yeniden başlatılması gerekir.  

 Daha sonra [VSPerfCmd](../profiling/vsperfcmd.md) profil oluşturucuyu hizmet işlemine eklemek için araç. Profiler servise bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.  

## <a name="attach-the-profiler"></a>Profil Oluşturucu ekleme  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Profil oluşturucuyu bir .NET Framework servisine eklemek  

1. Gerekirse, hizmeti yükleyin.  

2. Bir komut istemi penceresi açın.  

3. Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**} [**/samplelineoff**]  

   - Seçenekler **/globalsamplegclife** ve **/globalsamplegclife** toplanacak bellek verilerinin türünü belirtin. Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.  

     **/globalsamplegc**  
     Bellek ayırma verilerinin toplanmasını etkinleştirir.  

     **/globalsamplegclife**  
     Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.  

   - **/Samplelineoff** seçeneği, kaynak kod satır sayısı veri koleksiyonunu devre dışı bırakır.  

4. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.  

5. Gerekirse, hizmeti başlatın.  

6. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu yolunu PATH ortam değişkenine ekleyin.  

7. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd**[/start](../profiling/start.md) **: örnek**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:sample** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Bir veya daha fazla aşağıdaki seçeneklerle kullanabileceğiniz **/start:sample** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle hizmetler için gereklidir.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | İşlemin sahibi olan hesabının etki alanını ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Hizmetin altında çalıştığı oturum açma hesabının kullanıcı adını ve isteğe bağlı etki alanını belirtir. Oturum açma hesabın, Windows Hizmet Denetimi Yöneticisi'nde hizmetin Farklı Oturum Aç sütununda listelenir. |
   | [/ crosssession&#124;cs](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır. |


8. Hizmete profil oluşturucu iliştirin. Tür:  

    **VSPerfCmd**[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]    

   -   İşlem kimliğini veya hizmetin işlem adını belirtin. Windows Görev Yöneticisi'nde, işlem kimliklerini ve isimlerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

   -   **targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profiline ortak dil çalışma zamanı (CLR) sürümünü belirtir. İsteğe bağlı.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hizmet çalışırken kullanabileceğiniz *VSPerfCmd.exe* durdurmak ve Profil Oluşturucu veri dosyasına verilerin yazılmasını başlatmak için Seçenekler. Veri toplamanın denetlenmesi, program yürütmenin, uygulamanın başlatılması veya kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |**/ ekleme:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ ekleme** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Hizmeti durdurarak veya çağırarak örnekleme yöntemiyle profili oluşturulmuş bir uygulamadan verilerin toplanmasını durdurabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdakilerden birini yapın:  

    -   Hizmeti durdurun.  

         veya  

    -   Tür **VSPerfCmd / detach**  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd/Shutdown**  

3.  (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfClrEnv /globaloff**  

4.  Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Profil hizmetler](../profiling/command-line-profiling-of-services.md)   
 [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)