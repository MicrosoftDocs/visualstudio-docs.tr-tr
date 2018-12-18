---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3912e823a6e6ee32488fcda94616aef414d3d22
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775309"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman etkileşim profili oluşturma, zaman uyumlu yürütme sürelerini hakkında ek bilgi sağlayan [!INCLUDE[vstecado](../includes/vstecado-md.md)] içinde bir veya daha fazla veritabanı ile iletişim kuran çok katmanlı uygulamaların işlevlerini çağırır.  
  
 **Windows 8 ve Windows Server 2012**  
  
 Masaüstü uygulamalarını Windows 8 ve Windows Server 2012 uygulamalar üzerinde katman etkileşim verileri toplamak için izleme metodunu kullanmanız gerekir. Windows Store uygulamaları katman etkileşim verileri toplama desteklenmiyor.  
  
 **Visual Studio sürümleri**  
  
 Katman etkileşim profili oluşturma toplanacak kullanarak [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Ancak, katman etkileşimli profil oluşturma veri yalnızca görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] ve [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Uzak makinede ipucu verileri toplama**  
  
 Uzak makinede katman etkileşim verileri toplamak için kopyalamanız gereken **vs\_profil oluşturucu\_**_\<Platform >_ **\_**  _\<Dil >_**.exe** dosya _VSInstallDir %_**tools\performance Tools\Setups**klasöründe bir Visual Studio uzak bilgisayara makine ve yükleyin. Profil oluşturma araçları kullanamazsınız [Visual Studio uzak Araçları](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) paketini indirin.  
  
 **İpucu raporları**  
  
 Katman etkileşim verileri yalnızca içinde görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] IDE. Dosya tabanlı katman etkileşim raporlar aracılığıyla [VSPerfReport](../profiling/vsperfreport.md) kullanılabilir değil.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile Katman etkileşim verileri ekleme  
 VSPerfASPNETCmd komut satırı aracı, profil oluşturma araçlarında kullanılabilir işlevlerin erişmenizi sağlar. VSPerfCmd kullanılarak toplanan verileri profil oluşturma için katman etkileşim eklemek için kullanmanız gerekir **VSPerfCLREnv** katman etkileşim verileri sağlayan ayarlayın ve ortam değişkenlerini kaldırmak için yardımcı programı. Belirttiğiniz seçenekleri ve veri toplamak için gerekli yordamlarda, profil uygulamanın türüne bağlıdır.  
  
### <a name="profiling-stand-alone-applications"></a>Bağımsız uygulamaların profilini oluşturma  
 Katman etkileşim verileri zaman uyumlu yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılmaz bir uygulamaya eklemek için [!INCLUDE[vstecado](../includes/vstecado-md.md)] SQLServer veritabanına aramalar kullan **VSPerfClrEnv /InteractionOn** ortam değişkenlerini ayarlamak için seçeneği ve **VSPerfClrEnv /InteractionOff** bunları kaldırma seçeneği.  
  
 Aşağıdaki örnekte, bir Windows masaüstü uygulaması izleme metodunu kullanarak profili ve katman etkileşim verileri toplanır.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Windows masaüstü uygulaması örnek profili oluşturma  
  
1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. Tıklayın **Başlat**, işaret **tüm programlar**, gelin ve ardından **Donatılar**. Sağ **komut istemi**ve ardından **yönetici olarak çalıştır**.  
  
2. .NET profil oluşturma ve ipucu ortamı değişkenlerini başlatın. Aşağıdaki komutları yazın:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Profil oluşturucuyu başlatın. Şu komutu yazın:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Uygulama VSPerfCmd ile başlayın. Şu komutu yazın:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Profil oluşturma verilerini toplamak için uygulama çalışma ve uygulama normal şekilde kapatın.  
  
6. İpucu ortam değişkenlerini temizleyin. Şu komutu yazın:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Daha fazla bilgi için [profil oluşturma tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Profil oluşturma hizmetleri  
 Dahil olmak üzere profil hizmetlerine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamaları, **VSPerfClrEnv /GlobalInteractionOn** ortam değişkenlerini ayarlamak için seçeneği ve **VSPerfClrEnv /GlobalInteractionOff** bunları kaldırma seçeneği.  
  
 Zaman profil gibi hizmetler [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları, genellikle gerekecek oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatın.  
  
 Aşağıdaki örnekte, instrumenation yöntemini kullanarak bir Windows hizmeti profili ve katman etkileşim verileri toplanır.  
  
##### <a name="profiling-a-windows-service-example"></a>Bir Windows Hizmeti örnek profili oluşturma  
  
1. Gerekirse, hizmeti yükleyin.  
  
2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. Tıklayın **Başlat**, işaret **tüm programlar**, gelin ve ardından **Donatılar**. Sağ **komut istemi**ve ardından **yönetici olarak çalıştır**.  
  
3. .NET profil oluşturma ortamı değişkenlerini başlatın. Şu komutu yazın:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. İpucu ortamı değişkenlerini başlatın. Aşağıdaki komutu yazın  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.  
  
6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.  
  
7. Profil oluşturucuyu başlatın. Şu komutu yazın:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. Gerekirse, hizmeti başlatın.  
  
9. Hizmete profil oluşturucu iliştirin. Şu komutu yazın:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Hizmet çalışma ve profil oluşturma verisi toplar.  
  
11. Profil oluşturucuyu durdurun. Şu komutu yazın:  
  
     `vsperfcmd /detach`  
  
12. .NET ve ipucu profil oluşturma ortam değişkenlerini temizleyin. Şu komutu yazın:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Temizlenmiş ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.  
  
    Daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
    [ASP.NET Web Uygulamalarında Profil Oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile Katman etkileşim verileri ekleme  
 VSPerfASPNETCmd komut satırı aracı profiline bir kolayca sağlayan [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları. İle karşılaştırıldığında **VSPerfCmd** komut satırı aracı seçenekleri sınırlı, hiçbir ortam değişkenlerini ayarlamak sahip ve bilgisayarın yeniden başlatılması gerekli değildir. Bu işlevlerin VSPerfASPNETCmd katman etkileşim verileri koleksiyonu olağanüstü kolaylaştırır.  
  
 VSPerfASPNETCmd ile tarafından toplanan veriler profil oluşturma için katman etkileşim eklemek için Ekle **/İpucu** komut satırı seçeneği. Örneğin, katman etkileşim verileri toplamak için şu komut satırını kullanın. bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasını izleme metodunu kullanarak:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 VSPerfASPNETCmd hakkında daha fazla bilgi için bkz: [VSPerfASPNETCmd ile Hızlı Web sitesi profil](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).



