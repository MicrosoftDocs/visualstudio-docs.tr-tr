---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbb950947b3f97a4f6d6e9c1461dd2023595058c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775039"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme

Katman etkileşim profili oluşturma, zaman uyumlu yürütme sürelerini hakkında ek bilgi sağlayan [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] içinde bir veya daha fazla veritabanı ile iletişim kuran çok katmanlı uygulamaların işlevlerini çağırır.

**Windows 8 ve Windows Server 2012**

Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar üzerinde katman etkileşim verileri toplamak için izleme metodunu kullanmanız gerekir. UWP uygulamaları katman etkileşim verileri toplama desteklenmiyor.

**Visual Studio sürümleri**

Katman etkileşim profili oluşturma, herhangi bir Visual Studio sürümünü kullanarak toplanabilir. Ancak, yalnızca Visual Studio Enterprise'da katman etkileşimli profil oluşturma veri görüntülenebilir.

**Uzak makinede ipucu veri topla**

Uzak makinede katman etkileşim verileri toplamak için kopyalamanız gereken **vs_profiler\_**_\<Platform >_ **\_**  _\<Dil >_**.exe** dosya _VSInstallDir %_**tools\performance Tools\Setups** klasöründe bir Visual Studio uzak bilgisayara makine ve yükleyin. Profil oluşturma araçları kullanamazsınız [uzaktan hata ayıklama](../debugger/remote-debugging.md) paketini indirin.

**İpucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise'da görüntülenebilir. Dosya tabanlı katman etkileşim raporlar aracılığıyla [VSPerfReport](../profiling/vsperfreport.md) kullanılabilir değil.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile Katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, profil oluşturma araçlarında kullanılabilir işlevlerin erişmenizi sağlar. VSPerfCmd kullanılarak toplanan verileri profil oluşturma için katman etkileşim eklemek için kullanmanız gerekir **VSPerfCLREnv** katman etkileşim verileri sağlayan ayarlayın ve ortam değişkenlerini kaldırmak için yardımcı programı. Belirttiğiniz seçenekleri ve veri toplamak için gerekli yordamlarda, profil uygulamanın türüne bağlıdır.

## <a name="profile-stand-alone-applications"></a>Bağımsız uygulamalar profili

Katman etkileşim verileri zaman uyumlu yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılmaz bir uygulamaya eklemek için [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] SQLServer veritabanına aramalar kullan **VSPerfClrEnv /InteractionOn** ortam değişkenlerini ayarlamak için seçeneği ve **VSPerfClrEnv /InteractionOff** bunları kaldırma seçeneği.

Aşağıdaki örnekte, bir Windows masaüstü uygulaması izleme metodunu kullanarak profili ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-desktop-application-example"></a>Windows masaüstü uygulaması örnek profil

1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. Tıklayın **Başlat**, işaret **tüm programlar**, gelin ve ardından **Donatılar**. Sağ **komut istemi**ve ardından **yönetici olarak çalıştır**.

2. .NET profil oluşturma ve ipucu ortamı değişkenlerini başlatın. Aşağıdaki komutları yazın:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Profil oluşturucuyu başlatın. Şu komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp 
    ```

4. Uygulama VSPerfCmd ile başlayın. Şu komutu yazın:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Profil oluşturma verilerini toplamak için uygulama çalışma ve uygulama normal şekilde kapatın.

6. İpucu ortam değişkenlerini temizleyin. Şu komutu yazın:

    ```cmd
    vsperfclrenv /off
    ```

Daha fazla bilgi için [bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profil hizmetler

Dahil olmak üzere profil hizmetlerine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları, **VSPerfClrEnv /GlobalInteractionOn** ortam değişkenlerini ayarlamak için seçeneği ve **VSPerfClrEnv /GlobalInteractionOff** bunları kaldırma seçeneği.

Zaman profil gibi hizmetler [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları, genellikle gerekecek oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatın.

Aşağıdaki örnekte, bir Windows hizmeti izleme metodunu kullanarak profili ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-service-example"></a>Profili bir Windows hizmeti örneği

1. Gerekirse, hizmeti yükleyin.

2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. Tıklayın **Başlat**, işaret **tüm programlar**, gelin ve ardından **Donatılar**. Sağ **komut istemi**ve ardından **yönetici olarak çalıştır**.

3. .NET profil oluşturma ortamı değişkenlerini başlatın. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. İpucu ortamı değişkenlerini başlatın. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.

7. Profil oluşturucuyu başlatın. Şu komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession 
    ```

8. Gerekirse, hizmeti başlatın.

9. Hizmete profil oluşturucu iliştirin. Şu komutu yazın:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession 
    ```

10. Hizmet çalışma ve profil oluşturma verisi toplar.

11. Profil oluşturucuyu durdurun. Şu komutu yazın:

     `vsperfcmd /detach`

12. .NET ve ipucu profil oluşturma ortam değişkenlerini temizleyin. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Temizlenmiş ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

Daha fazla bilgi için aşağıdaki konulardan birine bakın:

[Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil hizmetler](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile Katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı profiline bir kolayca sağlayan [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları. İle karşılaştırıldığında **VSPerfCmd** komut satırı aracı seçenekleri sınırlı, hiçbir ortam değişkenlerini ayarlamak sahip ve bilgisayarın yeniden başlatılması gerekli değildir. Bu işlevlerin VSPerfASPNETCmd katman etkileşim verileri koleksiyonu olağanüstü kolaylaştırır.

VSPerfASPNETCmd ile tarafından toplanan veriler profil oluşturma için katman etkileşim eklemek için Ekle **/İpucu** komut satırı seçeneği. Örneğin, katman etkileşim verileri toplamak için şu komut satırını kullanın. bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını izleme metodunu kullanarak:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

VSPerfASPNETCmd hakkında daha fazla bilgi için bkz: [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).