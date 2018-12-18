---
title: Bellek verileri toplamak için bir .NET uygulaması için profil oluşturucu ekleme
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a550ac10b5983041da93b0c290877f8e1b1a3720
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051801"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak bellek verileri toplamak için bir .NET Framework bağımsız uygulamasına ekleme

Bu makalede, çalışan bir .NET Framework bağımsız (istemci) uygulamasına profil oluşturucu ekleme ve bellek verileri toplamak için Visual Studio Profil Araçları komut satırı araçlarını kullanmayı açıklar.

> [!NOTE]
> Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* alt [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] yükleme dizini. 64-bit bilgisayarlarda araçların 64-bit hem 32-bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Bir .NET Framework uygulamasına ve bellek verilerini toplamak için eklemek için kullanmanız gerekir [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) hedef uygulama başlamadan önce uygun ortam değişkenlerini başlatmak üzere. Profil Oluşturucu uygulamaya eklendiğinde kullanabileceğiniz *VSPerfCmd.exe* duraklatma ve sürdürme veri toplama için aracı.

Profil oluşturma oturumunu sona erdirmek için profil oluşturucu oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucu açıkça kapatılmalıdır. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profil Oluşturucu ekleme

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlatın. Tür:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - **/Samplegc** ve **/samplegclife** seçenekleri yalnızca bellek ayırma verisini toplayabilir veya hem bellek ayırma hem de nesne ömür verilerini toplamak için etkinleştirilip etkinleştirilmeyeceğini belirtin. Bir ve yalnızca bir seçeneği belirtilmelidir.

        |Seçenek|Açıklamaları|
        |------------|------------------|
        |**/samplegc**|Yalnızca bellek ayırma verisini toplayın.|
        |**/samplegclife**|Hem bellek ayırma ve nesne yaşam süresi verisi toplar.|

    - **/Samplelineoff** seçeneği, kaynak kod satır sayısı veri koleksiyonunu devre dışı bırakır.

3. Profil oluşturucuyu başlatın. Tür:

     **VSPerfCmd /start:sample/Output:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: örnek** seçeneği profil oluşturucuyu başlatır.

   - [/Output](../profiling/output.md)**:** `OutputFile` ile seçeneği gereklidir **/start**. `OutputFile` Profil oluşturma veri (.vsp) dosyasının konumunu ve adını belirtir.

     Aşağıdaki seçeneklerle dilediğinizi kullanabilirsiniz **/start:sample** seçeneği.


     | Seçenek | Açıklama |
     | - | - |
     | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Profilli işlemin sahibi olan hesabının etki alanı ve kullanıcı adını belirtir. Bu seçenek, yalnızca oturum açan kullanıcıdan farklı bir kullanıcı olarak işlem çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesinde kullanıcı adı sütununda listelenir. |
     | [/ crosssession &#124; /cs](../profiling/crosssession.md) | Etkinleştirir, diğer oturumlarda işlemleri profil oluşturma. Bu seçenek, başka bir oturumda uygulama çalışıyorsa gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin İşlemler sekmesinde oturum kimliği sütununda listelenir. **/CS** için bir kısaltma olarak belirtilebilir **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Profil oluşturma sırasında Tahsil edilecek Windows performans sayacı belirtir. |
     | [/automark](../profiling/automark.md) **:** `Interval` | İle kullanma **/wincounter** yalnızca. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. 500 ms varsayılandır. |


4. Gerekirse, hedef uygulama normal şekilde başlatın.

5. Profil Oluşturucu hedef uygulamaya iliştirin. Tür:

     **VSPerfCmd**[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID` hedef uygulamanın işlem Kimliğini belirtir. `ProcessName` işlemin adını belirtir. Belirttiğiniz gerçekleştiriyorsanız `ProcessName` ve aynı ada sahip birden çok işlem çalışıyorsa, sonuçların tahmin edilemeyeceğine. Windows Görev Yöneticisi'nde, işlem kimliklerini çalışan tüm işlemlerin görüntüleyebilirsiniz.

    - **/ targetclr:** `Version` bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profiline ortak dil çalışma zamanı (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hedef uygulama çalışırken kullanarak verinin yazılmasını durdurmayla ve veri toplamayı kontrol edebilirsiniz *VSPerfCmd.exe* seçenekleri. Veri toplama denetimi uygulamayı kapatma veya başlatma gibi program yürütmenin özel bir bölümü için veri toplamanızı sağlar.

### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı durdurmak ve başlatmak

- Aşağıdaki seçenekleri çiftlerini başlatın ve veri toplama işlemini durdurun. Her seçeneği ayrı bir komut satırında belirtin. Veri Toplama'ı, birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/ globalon /globaloff](../profiling/globalon-and-globaloff.md)|Başlar (**/globalon**) veya durdurur (**/globaloff**) tüm işlemler için veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Başlar (**/processon**) veya durdurur (**/processoff**) tarafından belirtilen işlem için veri toplamayı `PID`.|
    |[/ ekleme](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ ekleme** tarafından belirtilen işlem için veri toplamaya başlar `PID` veya işlem adı (ProcName). **/ detach** belirli bir işlem belirtilmezse, belirtilen işlem için veya tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona erdirme

Profil oluşturma oturumunu sona erdirmek için profil oluşturucu oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucu açıkça kapatılmalıdır. Uygulamayı kapatarak veya çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadaki profil oluşturucuyu ayırabilirsiniz **VSPerfCmd / detach** seçeneği. Ardından çağırın **VSPerfCmd/shutdown** profil oluşturucuyu devre dışı bırakırsınız ve profil oluşturma veri dosyasını kapatırsınız. **VSPerfClrEnv / off** komutu profil oluşturma ortam değişkenlerini temizler.

### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Hedef uygulamadaki profil oluşturucuyu ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Tür **VSPerfCmd / detach**

         veya

    - Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Tür:

     **VSPerfCmd** [ /Shutdown](../profiling/shutdown.md)

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleyin. Tür:

     **VSPerfCmd / kapatma**

## <a name="see-also"></a>Ayrıca bkz.

[Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)  
[.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md)