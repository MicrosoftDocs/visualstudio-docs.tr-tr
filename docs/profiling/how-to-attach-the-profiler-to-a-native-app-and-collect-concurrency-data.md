---
title: Bir yerel uygulamaya profil oluşturucu ekleme ve eşzamanlılık verileri toplama
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: ef2c5a7cbd21cba8b60944c2e3f45e4af05e630a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067051"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: yerel bir bağımsız uygulamaya profil oluşturucu ekleme ve komut satırını kullanarak eşzamanlılık verileri toplama
Bu makalede nasıl kullanılacağını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalışan yerel bir (C/C++) tek başına uygulamaya profil oluşturucu ekleme ve toplamak için profil oluşturma araçları komut satırı araçlarının iş parçacığı Çekişme verisi.  
  
> [!NOTE]
>  Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* Visual Studio yükleme dizininin alt. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu PATH ortam değişkenlerine eklemeniz gerekir **komut istemi** penceresinde veya komutun kendisindeki ekleyin. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Profil Oluşturucu uygulamaya bağlı durumdayken, duraklatma ve veri koleksiyonu devam ettirin. Profil oluşturma oturumunu sona erdirmek için Profiler artık uygulamaya bağlı gerekir ve Profiler açıkça kapatılmalıdır.  
  
## <a name="attach-the-profiler-to-a-running-native-application"></a>Çalışan yerel bir uygulamaya profil oluşturucu ekleme  
  
#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Profil oluşturucuyu çalışan yerel bir uygulamaya eklemek için  
  
1.  Bir komut isteminde aşağıdaki komutu yazın:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**  
  
     Aşağıdaki tabloda seçeneklerden herhangi birini kullanabilirsiniz **/start:concurrency** seçeneği.  
  
    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`Username`|Profil oluşturucuya erişim verilebilmesi için hesabın kullanıcı adını ve isteğe bağlı etki alanını belirtir.|  
    |[/ crosssession](../profiling/crosssession.md)|Etkinleştirir işlemleri diğer oturum açılışlarında profil oluşturma.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Profil oluşturma sırasında Tahsil edilecek bir olay izleme için Windows (ETW) olayı belirtir. ETW olayları ayrı (.etl) dosyasında toplanır.|  
  
2.  Profil Oluşturucu hedef uygulama için aşağıdaki komutu yazarak ekleyin:  
  
     **VSPerfCmd**[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`}  
  
     `PID` hedef uygulamanın işlem Kimliğini belirtir. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.  
  
## <a name="control-data-collection"></a>Veri toplamayı denetleme  
 Hedef uygulama çalışırken, kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Denetleme veri toplama işlemi tarafından program yürütmenin, uygulamanın başlatılması ya da kapatılması gibi özel bir bölümü için veri toplayabilir.  
  
#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak  
  
-   Aşağıdaki tabloda seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.  
  
    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) veri toplama işlemi için işlem kimliği (`PID`) belirtir.|  
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** işlem için veri toplamaya başlar, işlem kimliği (`PID`) veya işlem adı (*ProcName*) belirtir. **/ detach** belirlenmiş bir işlem için belirtilen işlem veya tüm işlemler için veri toplamayı durdurur.|  
  
## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme  
 Profil oluşturma oturumunu sona erdirmek için Profil Oluşturucu veri toplamıyor olmalıdır. Uygulamayı kapatarak veya çağırarak örnekleme yöntemiyle profili bir uygulamadan veri toplamayı durdurabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırmak **VSPerfCmd/shutdown** profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatırsınız.  
  
#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için  
  
1.  Hedef uygulamadaki profil oluşturucuyu kapatarak veya aşağıdaki komutu yazarak bağlantısını kesin:  
  
     **VSPerfCmd / detach**  
  
2.  Aşağıdaki komutu yazarak profil oluşturucuyu kapatın:  
  
     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)