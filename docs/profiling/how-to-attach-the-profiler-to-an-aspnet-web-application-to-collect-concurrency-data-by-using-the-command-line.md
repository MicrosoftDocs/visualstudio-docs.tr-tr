---
title: Cncurrency verileri toplamak için bir ASP.NET uygulamasına profil oluşturucu ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c806150acf8fb37ab7e3fd36a879a6c1273b015a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063363"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için bir ASP.NET web uygulamasına profil oluşturucu ekleme
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir ASP.NET uygulamasına profil oluşturucu ekleme ve işlem ve iş parçacığı eşzamanlılık verileri toplamak için profil oluşturma araçları komut satırı araçları.  

 Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* Visual Studio yükleme dizininin alt. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturmayı komut isteminde kullanmak için Araçlar yolunu PATH ortam değişkenlerine eklemeniz gerekir **komut istemi** penceresinde veya komutun kendisindeki ekleyin. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Eşzamanlılık verileri toplamak için Web sitenizi barındıran ASP.NET işçi işlemine profil oluşturucuyu iliştirin. Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturma oturumunu sona erdirmek için profil oluşturucu artık uygulamaya bağlı gerekir ve Profiler açıkça kapatılmalıdır. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemelisiniz.  

## <a name="attach-the-profiler"></a>Profil Oluşturucu ekleme  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek  

1. Aşağıdaki komutu yazarak profil oluşturucuyu başlatın:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) seçeneği kaynak çekişmesi verisini toplamak için profil oluşturucuyu başlatır.  

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.  

     Herhangi bir seçenek ile aşağıdaki tabloda kullanabileceğiniz **/start** seçeneği.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` | Profil oluşturucuya erişim verilebilmesi için hesabın kullanıcı adını ve isteğe bağlı etki alanını belirtir. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. Ayrı bir toplanan ETW olayları (. *etl*) dosyası. |


2. Normal yolla ASP.NET uygulaması başlatın.  

3. Aşağıdaki komutu yazarak ASP.NET çalışan sürecine profil oluşturucu ekleme:**VSPerfCmd / ekleme:** `PID` [**/targetclr:**`Version`]  

   -   `PID` bir ASP.NET işçi işlemine adını veya Kimliğini belirtir. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

   -   [/ targetclr](../profiling/targetclr.md) **:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profiline ortak dil çalışma zamanı (CLR) sürümünü belirtir. Bu parametre isteğe bağlıdır.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Uygulama çalışırken kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Denetleme veri toplama işlemi tarafından program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplayabilir.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki tabloda gösterilen VSPerfCmd seçenek çiftlerini başlatın ve veri toplamayı durdur. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) veri toplama işlemi için işlem kimliği (`PID`) belirtir.|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** işlem için veri toplamaya başlar, işlem kimliği (`PID`) veya işlem adı (*ProcName*) belirtir. **/ detach** belirlenmiş bir işlem için belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Eşzamanlılık yöntemi ile profili çağırılarak veya ASP.NET çalışan sürecin yeniden başlatılarak tarafından oluşturulan bir uygulamadan veri toplamayı durdurabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırmak **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu kapatarak veya bir komut istemine aşağıdakileri yazarak bağlantısını kesin:  

     **VSPerfCmd / detach**  

2.  Bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu kapatın:  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Ayrıca bkz.  
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil oluşturma VSPerfASPNETCmd ile hızlı web sitesi](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)