---
title: 'Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için yerel bir hizmete Profiler ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9e9810eb445abfb64f6674278687f0d8ef1ec3db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876119"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için bir yerel hizmete profil oluşturucu ekleme
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları komut satırı araçlarının profil oluşturucuyu bir yerel (C/C++) eklemek ve işlem ve iş parçacığının eşzamanlılık verilerinin örnekleme yöntemini kullanarak toplamak.  

> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* Visual Studio yükleme dizininin alt. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturmayı komut isteminde kullanmak için Araçlar yolunu PATH ortam değişkenlerine eklemeniz gerekir **komut istemi** penceresinde veya komutun kendisindeki. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profiler servise bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturma oturumunu sona erdirmek için profil oluşturucu artık servise bağlı gerekir ve Profiler açıkça kapatılmalıdır.  

## <a name="attach-the-profiler"></a>Profil Oluşturucu ekleme  
 Bir yerel hizmete profil oluşturucu ekleme için kullandığınız **VSPerfCmd/start** ve **/ ekleme** ve profil oluşturucuyu başlatıp hedeflenen uygulamaya eklemek için Seçenekler. Belirtebileceğiniz **/start** ve **/ ekleme** ve onların kendi seçenekleri de tek bir komut satırı. Ayrıca ekleyebilirsiniz **/globaloff** hedef uygulamanın başlatıldığı sırada veri toplamayı duraklatma seçeneğinin. Daha sonra **/globalon** veri toplamaya başlamak için.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Bir yerel hizmete profil oluşturucuyu eklemek için  

1. Hizmet çalışmıyorsa, hizmeti başlatın.  

2. Profil oluşturucuyu aşağıdakileri komut istemine yazarak başlatın:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` ad ve profil oluşturma veri (.vsp) dosyasının konumunu belirtir.  

     Herhangi bir seçenek ile aşağıdaki tabloda kullanabileceğiniz **/start** seçeneği.  

   > [!NOTE]
   >  Çoğu hizmetlerinde **/user** ve **/crosssession** seçeneği.  

   | Seçenek | Açıklama |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` | Profil oluşturucuya erişim verilebilmesi için hesabın kullanıcı adını ve isteğe bağlı etki alanını belirtir. |
   | [/ crosssession](../profiling/crosssession.md) | Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır. |


3. Profil Oluşturucu, bir komut isteminde aşağıdaki komutu yazarak hizmete ekleyin:  

    **VSPerfCmd / ekleyin:** `PID`  

    `PID` işlem kimliği veya hedef uygulamanın işlem adını belirtir. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  

## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hedef uygulama çalışırken, dosyasına verilerin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Denetleme veri toplama işlemi tarafından program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplayabilir.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  

-   Aşağıdaki tabloda seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) veri toplama işlemi için işlem kimliği (`PID`) belirtir.|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** işlem için veri toplamaya başlar, işlem kimliği (`PID`) veya işlem adı (*ProcName*) belirtir. **/ detach** belirlenmiş bir işlem için belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|  

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Hizmeti durdurarak veya çağırarak eşzamanlılık yöntemi ile profili bir yerel hizmetten veri toplamayı durdurabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırmak **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  

1.  Hedef uygulamadaki profil oluşturucuyu Hizmeti durdurarak veya bir komut isteminde aşağıdaki komutu yazarak bağlantısını kesin:  

     Tür **VSPerfCmd / detach**  

2.  Bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu kapatın:  

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)