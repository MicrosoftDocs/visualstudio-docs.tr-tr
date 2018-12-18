---
title: 'Nasıl yapılır: bir .NET Framework izleme ve Profiler komut satırını kullanarak bellek verileri toplamak | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: eafd91fe97a4e4ceb33b9dc315b8b9d9014d27ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914703"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: bir .NET Framework hizmetini izleme ve profil oluşturucu komut satırını kullanarak bellek verileri toplama
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aracı profil oluşturma araçları komut satırı araçlarını bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ve bellek kullanım verilerini toplamak. Bellek ayırma verisini toplayabilir veya hem bellek ayırma ve nesne yaşam verisi toplayabilir.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
> [!NOTE]
>  Bilgisayar başlatıldıktan sonra hizmeti yeniden başlatılamıyor ise izleme yöntemi ile bir hizmetin profilini oluşturamazsınız, böyle bir hizmet, işletim sistemi başlatıldığında başlar.  
> 
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu Başlat  
 Performans verileri toplamak için bir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hizmeti kullandığınız [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) uygun ortam değişkenlerini başlatmak için araç ve [VSInstr.exe](../profiling/vsinstr.md) aracını belgelenmiş bir oluşturmak için Hizmet ikili dosyasının bir kopyası.  

 Profil oluşturma için yapılandırmak için hizmetini barındıran bilgisayarın yeniden başlatılması gerekir. Hizmet ayrıca el ile ve Hizmet Denetim Yöneticisi'nden başlamalıdır. Ardından profil oluşturucuyu başlatın ve sonra başlatın [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hizmeti.  

 Araçlı bileşen yürütüldüğünde, bellek verileri bir veri dosyasına otomatik olarak toplanır. Duraklatma ve profil oluşturma oturumu sırasında veri koleksiyonu devam ettirin.  

 Profil oluşturma oturumunu sona erdirmek için hizmet kapatın ve açıkça profil oluşturucuyu kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>.NET Framework hizmetinin profilini oluşturmayı başlatmak  

1. Bir komut istemi penceresi açın.  

2. Kullanım **Vsınstr** aracını hizmet ikililerinin belgelenmiş bir sürümünü oluşturmak için.  

3. Hizmet denetimi özgün ikiliyi belgelenmiş sürüm ile değiştirmek için Yöneticisi'ni kullanın. Hizmeti başlatma türünün el ile olarak ayarlandığından emin olun.  

4. Profil oluşturma ortamı değişkenlerini başlatın. Tür:  

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}  

   -   **/globaltracegc** ve **/globaltracegclife** bellek ayırma ve nesne yaşam verilerinin koleksiyonunu etkinleştirin.  

       |Seçenek|Açıklama|  
       |------------|-----------------|  
       |**/globaltracegc**|Yalnızca bellek ayırma verileri toplar.|  
       |**/globaltracegclife**|Bellek ayırma ve nesne yaşam süresi verisi toplar.|  

5. Bilgisayarı yeniden başlatın.  

6. Bir komut istemi penceresi açın.  

7. Profil oluşturucuyu başlatın. Tür:  

    **VSPerfCmd**[/start](../profiling/start.md) **: izleme**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start: Çekişme** seçeneği profil oluşturucuyu başlatır.  

   - **/Output:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.  

   > [!NOTE]
   >  **/User** ve **/crosssession** seçenekleri genellikle hizmetler için gereklidir.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | ASP.NET çalışan işlemine sahip hesabın etki alanı ve kullanıcı adını belirtir. Bu seçenek, oturum açan kullanıcının farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. ASP.NET uygulaması başka bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği listelenen **oturum kimliği** sütunu **işlemleri** Windows Görev Yöneticisi'nin sekmesinde. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Profil oluşturucunun hata vermeden önce başlatmak beklenecek saniye sayısını belirtir. Varsa `Interval` belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döndürür. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Profil Oluşturucu veri toplamayı başlatmak için duraklatıldı, ekleme **/globaloff** seçeneğini **/start** komut satırı. Kullanım **/globalon** profil oluşturmayı devam ettirmek için. |
   | [/ Sayaç](../profiling/counter.md) **:** `Config` | Sayaç Config içerisinde belirtilen işlemci performans bilgileri toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. Ayrı bir toplanan ETW olayları (. *etl*) dosyası. |


8. Gerekirse, hizmeti başlatın.  

9. Hizmete profil oluşturucu iliştirin. Tür:  

     **VSPerfCmd / ekleme:**`PID`&#124;`ProcessName`  

    -   İşlem kimliği veya servisin işlem adını belirtin. Windows Görev Yöneticisi'nde, işlem kimliklerini ve isimlerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hizmet çalışırken dosyasına verilerin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki çiftleri **VSPerfCmd** seçenekleri başlatın ve veri toplamayı durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) işlem kimliği tarafından belirtilen işlem için veri toplama (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Başlar (**/threadon**) veya durdurur (**/threadoff**) veri toplama iş parçacığı kimliği tarafından belirtilen iş parçacığı için (`TID`).|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için kapatın Araçlı bileşenini çalıştıran uygulamayı sonra başlatmak **VSPerfCmd** [/shutdown](../profiling/shutdown.md) profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Servis kontrol yöneticisinden hizmeti durdurun.  

2.  Profil oluşturucuyu kapatın. Tür:  

     **VSPerfCmd/Shutdown**  

3.  Tüm profil oluşturma işlemini tamamladıktan sonra profil oluşturma ortam değişkenlerini temizleyin. Tür:  

     **VSPerfClrEnv /globaloff**  

     Belgelenmiş modülü özgün hali ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.  

4.  Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca bkz.  
 [Profil hizmetler](../profiling/command-line-profiling-of-services.md)   
 [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)