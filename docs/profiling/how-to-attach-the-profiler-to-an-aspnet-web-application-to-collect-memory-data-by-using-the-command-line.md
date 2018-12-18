---
title: Bellek verileri toplamak için bir ASP.NET uygulamasına profil oluşturucu ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7f5c592733cc43101cb5cf022caf84892a55af7a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052964"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için bir ASP.NET web uygulamasına profil oluşturucu ekleme
Bu makalede nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] iliştirme için profil oluşturma araçları komut satırı araçlarını bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması ve toplama veri sayısı ve boyutu, .NET Framework bellek ayırmaları hakkında. Ayrıca, .NET Framework bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.  

> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Performans verileri toplamak için bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması kullanmalıdır [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) barındıran bilgisayardaki uygun ortam değişkenlerini başlatmak üzere [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması. Ardından Web sunucusu profil oluşturma için yapılandırmak için bilgisayarı yeniden başlatmanız gerekir.  

 Daha sonra [VSPerfCmd.exe](../profiling/vsperfcmd.md) iliştirme için aracı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sitenizi barındıran çalışan işlemi. Profil Oluşturucu uygulamaya eklendiğinde, duraklatma ve veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sona erdirmek için profil oluşturucu artık uygulamaya bağlı gerekir ve profil oluşturucu açıkça kapatılmalıdır. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.  

## <a name="attach-the-profiler"></a>Profil Oluşturucu ekleme  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profil oluşturucuyu bir ASP.NET web uygulamasına eklemek  

1. Bir komut istemi penceresi açın.  

2. Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  

   -   Seçenekler **/globalsamplegc** ve **/globalsamplegclife** toplanacak bellek verilerinin türünü belirtin.  

        Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.  

       |Seçenek|Açıklama|  
       |------------|-----------------|  
       |**/globalsamplegc**|Bellek ayırma verilerinin toplanmasını etkinleştirir.|  
       |**/globalsamplegclife**|Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.|  

   -   Seçenek **/samplelineoff** toplanan verilerin belirli kaynak kod satırlarına atamayı devre dışı bırakır. Bu seçenek belirtilmişse, veri işlev düzeyinde atanır.  

3. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.  

4. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu path ortam değişkenini ayarlayın.  

5. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd**[/start](../profiling/start.md) **: örnek**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:sample** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | ASP.NET çalışan işlemine sahip hesabın etki alanı ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Profil oluşturucunun hata vermeden önce başlatmak beklenecek saniye sayısını belirtir. Varsa `Interval` belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döndürür. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır. |


6. Başlangıç [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] normal şekilde Web uygulaması.  

7. İliştirme [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi. Tür:  

    **VSPerfCmd**[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]    

   - İşlem Kimliği `(PID)` işlem Kimliğini veya hizmetin işlem adını belirtir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

   - **/ targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profiline ortak dil çalışma zamanı (CLR) sürümünü belirtir.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Uygulama çalışırken, Profil Oluşturucu veri dosyasına verilerin yazılmasını kullanarak durdurmayla ve veri toplamayı kontrol edebilirsiniz **VSPerfCmd.exe** seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) tarafından belirtilen işlem için veri toplamayı `PID`.|  
    |**/ ekleme:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/ ekleme** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu Web uygulamasından ayrılmış olması gerekir. Yeniden başlatarak örnekleme yöntemiyle profili bir uygulamadan verilerin toplanmasını durdurabilirsiniz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlem veya çağırarak **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1. Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdaki adımlardan birini gerçekleştirin:  

   - Tür **VSPerfCmd** [/ detach](../profiling/detach.md)  

      veya  

   - Kapat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemi. Tür:  

     **IISReset/stop**  

2. Profil oluşturucuyu kapatın. Tür:  

    **VSPerfCmd/Shutdown**  

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:  

    **VSPerfCmd /globaloff**  

4. Bilgisayarı yeniden başlatın. Gerekirse, Internet Information Services (IIS) yeniden başlatın. Tür:  

    **IISReset/Start**  

## <a name="see-also"></a>Ayrıca bkz.  
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)