---
title: IntelliTrace tek başına toplayıcıyı kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dfdcb3e273e3e2c7b957a78280511980fa9c93fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905317"
---
# <a name="using-the-intellitrace-stand-alone-collector"></a>IntelliTrace tek başına toplayıcıyı kullanma
**IntelliTrace collector** IntelliTrace Tanılama verilerini uygulamalarınız için üretim sunucularına ya da diğer ortamlarda hedef makinede Visual Studio yüklemeden ve değiştirmeden toplamanıza olanak tanır. Sistem ortam hedefleyin. IntelliTrace collector, web, SharePoint, WPF ve Windows Forms uygulamaları üzerinde çalışır. Veri toplama işiniz bittiğinde kaldırmak için toplayıcıyı silmeniz yeterlidir.

 IntelliTrace'i çalışırken izleyin: [toplama ve analiz etme (kanal 9 videosu) hata ayıklama için üretimde IntelliTrace verilerini](http://go.microsoft.com/fwlink/?LinkID=251851)

> [!NOTE]
>  Ayrıca web ve SharePoint uygulamaları kullanarak uzak makinelerde çalışan için aynı IntelliTrace verisi toplayabilir **Microsoft Monitoring Agent** içinde **izleme** modu.
>
>  Aracısı'nı çalıştırarak performansı ile ilgili olayları IntelliTrace verisi toplayabilir **İzleyici** modu. **İzleyici** modu olan küçük bir performans etkisi **izleme** modu veya **IntelliTrace collector**. Yüklendiğinde Microsoft Monitoring Agent hedef sistemin ortam değiştirir. Bkz: [Microsoft Monitoring Agent'ı kullanarak](../debugger/using-the-microsoft-monitoring-agent.md).

 **Gereksinimler**

- .NET framework 3.5, 4 veya 4.5

- Visual Studio .iTrace dosyalarını açmak için Kurumsal (ancak değil Professional veya Community sürümlerini) bir geliştirme bilgisayarı ya da diğer bilgisayar üzerinde

  > [!NOTE]
  >  Sembol (.pdb) dosyalarını kaydettiğinizden emin olun. IntelliTrace ile hata ayıklamak ve kodunuz içinde adım adım için eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz: [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

  **SSS**

- [Hangi uygulamalar Toplayıcı ile çalışıyor?](#WhatApps)

- [Nasıl kullanmaya başlarım?](#GetStarted)

- [En çok veriyi without slowing down my app nasıl alabilirim?](#Minimizing)

- [IntelliTrace verisini başka nereden alabilirim?](#WhereElse)

##  <a name="WhatApps"></a> Hangi uygulamalar Toplayıcı ile çalışıyor?

-   Internet Information Services (IIS) 7.0, 7.5 ve 8.0 sürümü üzerinde barındırılan ASP.NET Web uygulamaları

-   SharePoint 2010 ve SharePoint 2013 uygulamaları

-   Windows Presentation Foundation (WPF) ve Windows uygulamaları oluşturur.

##  <a name="GetStarted"></a> Nasıl kullanmaya başlarım?

1.  [Toplayıcı yükleyin](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2.  [Toplayıcı dizini için izinleri ayarla](#ConfigurePermissionsRunningCollector)

3.  [Web uygulamaları ve SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet'lerini yükleyin](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4.  [.İTrace dosya dizini için izinleri ayarla](#BKMK_Create_and_Configure_a_Log_File_Directory)

5.  [Bir Web uygulaması ya da SharePoint uygulamasından veri topla](#BKMK_Collect_Data_from_IIS_Application_Pools)

     veya

     [Yönetilen bir uygulamadan veri toplama](#BKMK_Collect_Data_from_Executables)

6.  [Visual Studio Enterprise'da .iTrace dosyasını açın](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Toplayıcı yükleyin

1. Uygulamanızın sunucusunda, örneğin Toplayıcı dizini oluşturun: **C:\IntelliTraceCollector**

2. Toplayıcıyı Microsoft Download Center veya Visual Studio 2013 güncelleştirme 3'ü yükleme klasöründen alın. [Visual Studio 2013 Update 4 için IntelliTrace Collector](https://www.microsoft.com/en-us/download/details.aspx?id=44909)::

   - **Microsoft İndirme Merkezi**:

     1. Yanındaki **IntelliTraceCollector.exe**, seçin **indirme**.

     2. Toplayıcı dizini için IntelliTraceCollector.exe kaydedin, örneğin: **C:\IntelliTraceCollector**

     3. IntelliTraceCollector.exe çalıştırın. Bu Intellitracecollection.cab dosyasını çıkartır.

        \- veya -

   - **Visual Studio yükleme klasörü**:

     1.  Intellitracecollection.cab dosyasını aşağıdaki klasörden kopyalayın:

          **..\Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2.  Intellitracecollection.cab dosyasını Toplayıcı dizinine örneğin yerleştirin: **C:\IntelliTraceCollector**

3. Intellitracecollection.cab dosyasını genişletin:

   1.  Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

   2.  Örneğin, Toplayıcı dizini için Gözat: **C:\IntelliTraceCollector**

   3.  Kullanım **genişletin** nokta dahil, komut (**.**) ıntellitracecollection.cab dosyasını genişletmek için sonunda:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       >  Süre (**.**) yerelleştirilmiş toplama planlarını içeren alt klasörleri korur.

##  <a name="ConfigurePermissionsRunningCollector"></a> Toplayıcı dizini için izinleri ayarla

1.  Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

2.  Windows kullanan **icacls** sunucu yöneticisine Toplayıcı dizini için tam izinleri vermek için komutu. Örneğin:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3.  Bir Web uygulaması ya da SharePoint uygulaması için veri toplamak için:

    1.  IntelliTrace PowerShell cmdlet'lerini, Toplayıcı dizini için tam izinlere çalışacak kişiye verin.

         Örneğin:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2.  Web uygulaması için uygulama havuzu verin ya da SharePoint uygulaması okuma ve yürütme Toplayıcı dizini için izinleri.

         Örneğin:

        -   İçinde bir Web uygulaması için **DefaultAppPool** uygulama havuzu:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        -   Bir SharePoint uygulaması için **SharePoint - 80** uygulama havuzu:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

##  <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Web uygulamaları ve SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet'lerini yükleyin

1.  Uygulamanızın sunucusunda, PowerShell'in etkin olduğundan emin olun. Çoğu Windows Server sürümlerinde, bu özelliği ekleyebilirsiniz **Sunucu Yöneticisi'ni** yönetim aracı.

     ![Sunucu Yöneticisi'ni kullanarak PowerShell ekleme](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2.  IntelliTrace PowerShell cmdlet'lerini yükleyin.

    1.  Yönetici olarak bir PowerShell komut penceresi açın.

        1.  Seçin **Başlat**, **tüm programlar**, **Donatılar**, **Windows PowerShell**.

        2.  Aşağıdaki adımlardan birini seçin:

            -   64-bit işletim sistemlerinde, kısayol menüsünü açın **Windows PowerShell**. Seçin **yönetici olarak çalıştır**.

            -   32 bit işletim sistemlerinde, kısayol menüsünü açın **Windows PowerShell (x86)**. Seçin **yönetici olarak çalıştır**.

    2.  PowerShell komut penceresinde **Import-Module** içeri aktarmak için komutu **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Örneğin:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

##  <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> .İTrace dosya dizini için izinleri ayarla

1. Uygulamanızın sunucusunda, .iTrace dosya dizini, örneğin oluşturun: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Uygulamanızı yavaşlatmayı önlemek için çok etkin değil yerel bir yüksek hızlı disk üzerinde bir konum seçin.
   >   -   .İTrace dosyalarını ve Toplayıcı dosyalarını aynı yere koyabilirsiniz. Ancak, bir Web uygulaması ya da SharePoint uygulaması varsa, buranın uygulamayı barındıran dizin dışında olduğundan emin olun.
   > 
   > [!IMPORTANT]
   > - .İTrace dosya dizinini yalnızca toplayıcıyla çalışması gereken kimliklerle kısıtlayın. Bir .iTrace dosyası, çünkü IntelliTrace method parametrelerine ya da dönüş değeri olarak geçirir her veriyi kaydedebilir veri kullanıcıları, veritabanları, diğer kaynak konumları ve bağlantı dizeleri gibi hassas bilgileri içeriyor olabilir.
   >   -   .İTrace dosyalarını açabilen kişilere hassas verileri görüntüleyebilecek yetkiye sahip olduğunuzdan emin olun. .İTrace dosyaları paylaşırken dikkatli olun. Diğer kişilerin erişim gereksinimi olduğunda dosyaları paylaşılan güvenli bir konuma kopyalayın.

2. Web uygulaması yada SharePoint uygulaması için uygulama havuzlarına .iTrace dosya dizini için tam izinleri verin. Windows kullanabileceğiniz **icacls** komutunu ya da Windows Explorer (veya dosya Gezgini) kullanın.

    Örneğin:

   - Windows ile izinleri ayarlamak için **icacls** komutu:

     - İçinde bir Web uygulaması için **DefaultAppPool** uygulama havuzu:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Bir SharePoint uygulaması için **SharePoint - 80** uygulama havuzu:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       veya

   - Windows Explorer'ı (ya da File Explorer) ile izinleri ayarlamak için:

     1.  Açık **özellikleri** .iTrace dosya dizini için.

     2.  Üzerinde **güvenlik** sekmesini, **Düzenle**, **Ekle**.

     3.  Emin **yerleşik güvenlik esasları** görünür **bu nesne türünü seç** kutusu. Bunu sahip değil, seçerseniz **nesne türlerini** ekleyin.

     4.  Yerel bilgisayarınıza emin görünür **bu konumdan** kutusu. Bunu sahip değil, seçerseniz **konumları** değiştirmek için.

     5.  İçinde **Seçilecek nesne adlarını girin** kutusunda, Web uygulaması ya da SharePoint uygulaması için uygulama havuzunu ekleyin.

     6.  Seçin **Adları Denetle** adı çözümlenemedi. Seçin **Tamam**.

     7.  Uygulama havuzu olduğundan emin olun **tam denetim**.

##  <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Bir Web uygulaması ya da SharePoint uygulamasından veri topla

1.  Veri toplamaya başlamak için bir yönetici olarak PowerShell komut penceresi açın ve şu komutu çalıştırın:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`  *\<PathToCollectionPlan >*  *\<FullPathToITraceFileDirectory >*

    > [!IMPORTANT]
    >  Bu komutu çalıştırdıktan sonra yazın **Y** veri toplamaya başlamak istediğinizi onaylayın.

     Örneğin, bir SharePoint uygulamasından veri toplamak için **SharePoint - 80** uygulama havuzu:

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |||
    |-|-|
    |*ApplicationPool*|Uygulamanızın çalıştığı uygulama havuzunun adı|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir .xml dosyasını bir koleksiyon planı yolu.<br /><br /> Toplayıcı ile birlikte gelen bir planı belirtebilirsiniz. Aşağıdaki planlar Web uygulamaları ve SharePoint uygulamaları için çalışır:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Yalnızca IntelliTrace olayları ve özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere, SharePoint olaylarını toplar.<br />-collection_plan.ASP.NET.trace.xml<br />     Toplanan işlev çağrılarını ve collection_plan.ASP.NET.default.xml içindeki tüm veriler. Bu plan detaylı çözümleme için iyidir ancak uygulamanızı collection_plan.ASP.NET.default.XML planından daha çok yavaşlatabilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için bu planları özelleştirebilir veya kendi planınızı oluşturun. Güvenlik için herhangi bir özel planı Toplayıcı dosyaları ile aynı güvenli konuma yerleştirin. Bkz: [oluşturma ve özelleştirme IntelliTrace koleksiyonu planları](http://go.microsoft.com/fwlink/?LinkId=227871) ve [nasıl alabilirim en çok veriyi without slowing down my app?](#Minimizing) **Not:** varsayılan olarak, .iTrace dosyasının en büyük boyutu 100 MB'dir. .İTrace dosya bu sınıra ulaştığında, Toplayıcı yeni girdiler için yer açmak için dosyanın eski girişlerin siler. Bu sınırı değiştirmek için koleksiyon planının `MaximumLogFileSize` özniteliği. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcının alt klasörlerinde bulabilirsiniz.|
    |*FullPathToITraceFileDirectory*|.İTrace dosya dizini için tam yolu. **Güvenlik Notu:** tam yolu, göreli bir yol sağlar.|

     Toplayıcı uygulama havuzuna bağlanır ve veri toplamaya başlar.

     *Şu anda .iTrace dosyasını açabilir miyim?* Hayır, dosya, veri toplama sırasında kilitli.

2.  Sorunu yeniden oluşturun.

3.  .İTrace dosyasının bir anlık görüntüsünü almak için bu sözdizimini kullanın:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`

4.  Toplama durumunu denetlemek için bu sözdizimini kullanın:

     `Get-IntelliTraceCollectionStatus`

5.  Veri toplamayı durdurmak için şu sözdizimini kullanın:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`

    > [!IMPORTANT]
    >  Bu komutu çalıştırdıktan sonra yazın **Y** veri toplamayı durdurmak istediğinizi onaylamak için. Aksi halde, Toplayıcı, verileri, iTrace toplama dosyası kilitli kalır veya dosya hiç yararlı veri içermeyebilir devam edebilir.

6.  [Visual Studio Enterprise'da .iTrace dosyasını açın](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_Collect_Data_from_Executables"></a> Yönetilen bir uygulamadan veri toplama

1.  Uygulamanızı başlatın ve aynı zamanda veri toplamak için bu sözdizimini kullanın:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Örneğin, adında bir uygulamadan veri toplamak için **MyApp**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |||
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Toplayıcı yürütülebilirinin, IntelliTraceSC.exe tam yolu|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir .xml dosyasını bir koleksiyon planı yolu.<br /><br /> Toplayıcı ile birlikte gelen bir planı belirtebilirsiniz. Aşağıdaki planlar yönetilen uygulamalar için çalışır:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Sadece IntelliTrace olaylarını özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere toplar.<br />-collection_plan.ASP.NET.trace.xml<br />     Toplanan işlev çağrılarını ve collection_plan.ASP.NET.default.xml içindeki tüm veriler. Bu plan detaylı çözümleme için iyidir ancak uygulamanızı collection_plan.ASP.NET.default.XML planından daha çok yavaşlatabilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için bu planları özelleştirebilir veya kendi planınızı oluşturun. Güvenlik için herhangi bir özel planı Toplayıcı dosyaları ile aynı güvenli konuma yerleştirin. Bkz: [oluşturma ve özelleştirme IntelliTrace koleksiyonu planları](http://go.microsoft.com/fwlink/?LinkId=227871) ve [nasıl alabilirim en çok veriyi without slowing down my app?](#Minimizing) **Not:** varsayılan olarak, .iTrace dosyasının en büyük boyutu 100 MB'dir. .İTrace dosya bu sınıra ulaştığında, Toplayıcı yeni girdiler için yer açmak için dosyanın eski girişlerin siler. Bu sınırı değiştirmek için koleksiyon planının `MaximumLogFileSize` özniteliği. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcının alt klasörlerinde bulabilirsiniz.|
    |*FullPathToITraceFileDirectoryAndFileName*|.İTrace dosya dizinine ve .iTrace dosya adı ile tam yolunu **.itrace** uzantısı. **Güvenlik Notu:** tam yolu, göreli bir yol sağlar.|
    |*PathToAppExecutableFileAndFileName*|Yönetilen uygulamanızın yol ve dosya adı|

2.  Uygulamadan çıkarak veri toplamayı durdurun.

3.  [Visual Studio Enterprise'da .iTrace dosyasını açın](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_View_IntelliTrace_Log_Files"></a> Visual Studio Enterprise'da .iTrace dosyasını açın

> [!NOTE]
>  IntelliTrace ile hata ayıklamak ve kodunuz içinde adım adım için eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz: [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

1.  .İTrace dosyasını taşıyın veya Visual Studio Enterprise (ancak değil Professional veya Community sürümlerini) olan bir bilgisayara kopyalayın.

2.  Visual Studio dışında .iTrace dosyasına çift tıklayın veya dosya açma Visual Studio içinde.

     Visual Studio gösterir **IntelliTrace özeti** sayfası. Çoğu bölümde, olayları ve diğer nesneleri gözden geçirebilir, bir öğe seçin ve IntelliTrace ile hata ayıklamaya başlamak bir olayın gerçekleştiği yerde ve. Bkz: [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    >  IntelliTrace ile hata ayıklamak ve kodunuz içinde adım adım için eşleşen kaynak dosyaları ve sembol dosyalarını geliştirme makinenizde olması gerekir. Bkz: [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

##  <a name="Minimizing"></a> Uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?
 Dolayısıyla, uygulamanızın performansı üzerindeki etkisi Intellitrace'in topladığı veriye ve çözümlediği kod üzerinde IntelliTrace pek çok veri toplayabilir. Bkz: [üretim sunucularında IntelliTrace koleksiyonu en iyileştirme](http://go.microsoft.com/fwlink/?LinkId=255233).

 Uygulamanızı yavaşlatmadan en çok veriyi almak için bazı yollar şunlardır:

- Toplayıcı yalnızca bir sorun olduğunu düşündüğünüz veya sorunu yeniden oluşturabileceğinizi düşündüğünüzde çalıştırın.

   Koleksiyonu Başlat, sorunu yeniden oluşturun ve toplama işlemini durdurun. Visual Studio Enterprise'da .iTrace dosyasını açın ve verileri inceleyin. Bkz: [.iTrace dosyasını açın Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- Web uygulamaları ve SharePoint uygulamaları için toplayıcı belirtilen uygulama havuzunu paylaşan her uygulama için veri kaydeder. Bir koleksiyon planı içinde yalnızca tek bir uygulama için modüller belirleyebilirsiniz olsa bile bu aynı uygulama havuzunu paylaşan herhangi bir uygulamayı yavaşlatabilir.

   Toplayıcının diğer uygulamaları yavaşlatmasını önlemek için her uygulamayı kendi uygulama havuzunda barındırın.

- Intellitrace'in veri topladığı toplama planındaki olayları inceleyin. Uygun olmayan veya sizi İlginiz dahilinde olmayan olayları devre dışı bırakmak için toplama planını düzenleyin.

   Bir olayı devre dışı bırakmak için ayarlanmış `enabled` özniteliğini `<DiagnosticEventSpecification>` öğesine `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Varsa `enabled` öznitelik yoksa, olay etkinleştirilmiştir.

   *Bu performansı nasıl iyileştirir?*

  -   Uygulama için uygun olmayan olayları devre dışı bırakarak başlatma süresini azaltabilirsiniz. Örneğin, Windows Workflow kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.

  -   Kayıt defterine erişen ancak kayıt defteri ayarlarında sorun göstermeyen uygulamalar için kayıt defteri olaylarını devre dışı bırakarak hem Başlangıç hem de çalışma zamanı performansını artırabilir.

- Intellitrace'in veri topladığı toplama planındaki modülleri inceleyin. Toplama planını yalnızca ilginizi çeken modülleri içerecek şekilde düzenleyin:

  1. Toplama planını açın. Bulma `<ModuleList>` öğesi.

  2. İçinde `<ModuleList>`ayarlayın `isExclusionList` özniteliğini `false`.

  3. Kullanım `<Name>` her modülü aşağıdakileri biri ile belirtmek için öğe: dosya adı, adında, dize veya ortak anahtar içeren her modülü içermek için dize değeri.

     Örneğin, yalnızca ana Web modülünden Fabrikam Fiber Web uygulamasının veri toplamak için aşağıdakine benzer bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>
  ```

   Adı "Fabrikam" içeren modüllerden veri toplamak için aşağıdakine benzer bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>
  ```

   Kendi ortak anahtar belirteçlerini belirterek modüllerden veri toplamak için aşağıdakine benzer bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>
  ```

   *Bu performansı nasıl iyileştirir?*

   Bu yöntem çağrı bilgisi ve uygulama başladığında ve çalışır olduğunda Intellitrace'in topladığı diğer araç verilerinin miktarını azaltır. Bu veriler şunları yapmanızı sağlar:

  - Veri toplamanın ardından kodda adım adım.

  - Geçirilen ve işlev çağrıları döndürülen değerleri inceleyin.

    *Neden bunun yerine modülleri hariç?*

    Varsayılan olarak ayarlayarak toplama planlarını modülleri hariç `isExclusionList` özniteliğini `true`. Ancak, modüllerin hariç tutulması yine de listenin ölçütlerine uymayan ve, üçüncü taraf veya açık kaynak modüller gibi İlginiz dahilinde olmayan modüllerden veri toplanmasına neden olabilir.

- *Intellitrace'in toplamadığı herhangi bir veri var mı?*

   Evet, performans etkisini azaltmak için IntelliTrace geçirilen ve geçirilen ve yöntemlerden döndürülen en üst düzey nesneler üzerinde yöntemleri ve alanları temel veri türlerinin değerleri için döndürülen ilkel veri türleri değerlerinin veri toplamasını kısıtlar.

   Örneğin, sahip olduğunuz varsayalım. bir `AlterEmployee` kabul eden bir tamsayı yöntem imzası `id` ve `Employee` nesne `oldemployee`:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee` Türü şu öznitelikler bulunur: `Id`, `Name`, ve `HomeAddress`. Arasında bir ilişkilendirme ilişkisi var. `Employee` ve `Address` türü.

   ![Çalışan ve adresi arasındaki ilişkiyi](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Toplayıcı, değerleri kaydeder `id`, `Employee.Id`, `Employee.Name` ve `Employee` döndürülen nesne `AlterEmployee` yöntemi. Toplayıcı hakkında bilgi ancak kaydetmez `Address` değil null olup dışındaki nesne. Toplayıcı ayrıca yerel değişkenler hakkında daha fazla veri kaydetmez `AlterEmployee` yöntemi hangi noktada onların yöntem parametreleri olarak parametre olarak, diğer yöntemler bu yerel değişkenleri kullanmadığınız sürece.

##  <a name="WhereElse"></a> IntelliTrace verisini başka nereden alabilirim?

-   Bir IntelliTrace hata ayıklama oturumu Visual Studio Enterprise, bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).

-   Microsoft Test Yöneticisi'nde bir test oturumdan, bkz: [nasıl yapılır: hata ayıklama zorluklarını çözmeye yardımcı olmak için IntelliTrace verilerini toplama](/visualstudio/test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues).

## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Bloglar
 [IntelliTrace Standalone Collector'ı uzaktan kullanma](http://go.microsoft.com/fwlink/?LinkId=262277)

 [Oluşturma ve IntelliTrace koleksiyonu planları özelleştirme](http://go.microsoft.com/fwlink/?LinkId=227871)

 [Üretim sunucularında IntelliTrace koleksiyonu en iyileştirme](http://go.microsoft.com/fwlink/?LinkId=255233)

 [Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)

### <a name="forums"></a>Forumlar
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)

### <a name="videos"></a>Videolar
 [Kanal 9 videosu: IntelliTrace verilerini toplayıp analiz eden](http://go.microsoft.com/fwlink/?LinkID=251851)
