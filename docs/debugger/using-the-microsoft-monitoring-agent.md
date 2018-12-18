---
title: Microsoft Monitoring Agent'ı kullanarak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3146de7efb7db567149b7741f2868a932f8476ac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842072"
---
# <a name="using-the-microsoft-monitoring-agent"></a>Microsoft İzleme Aracısı’nı kullanma
Kullanarak IIS ile barındırılan ASP.NET web uygulamaları ve SharePoint 2010 ya da 2013 uygulamalarını hatalar, performans sorunlarını ve diğer sorunlar için yerel olarak izleyebilirsiniz **Microsoft Monitoring Agent**. Tanılama olaylarını aracıdan bir IntelliTrace günlük (.iTrace) dosyasına kaydedebilirsiniz. Ardından tüm Visual Studio tanılama araçları ile ilgili sorunlar hata ayıklamak için Visual Studio Enterprise (ancak Professional veya Community sürümlerini değil) oturum açabilirsiniz. Aracısı'nı çalıştırarak IntelliTrace Tanılama verilerini ve yöntemi verilerini de toplayabilirsiniz **izleme** modu. Microsoft Monitoring Agent ile tümleştirilebilir [Application Insights](/azure/application-insights/) ve [System Center Operation Manager](/previous-versions/system-center/system-center-2012-R2/hh205987(v=sc.12)). Yüklendiğinde Microsoft Monitoring Agent hedef sistemin ortam değiştirir.  
  
> [!NOTE]
>  Hedef ortamı değiştirmeden kullanarak uzak makinelerde web, SharePoint, WPF ve Windows Form uygulamaları için IntelliTrace Tanılama ve yöntemi verileri toplayabilir **IntelliTrace collector**. Tek başına toplayıcıyı Microsoft Monitoring Agent çalışan daha büyük bir performans etkisi olur **İzleyici** modu. Bkz: [IntelliTrace collector kullanarak](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 System Center 2012 kullanıyorsanız, sorunlarla ilgili uyarı almak ve kayıtlı IntelliTrace günlük dosyalarının bağlantılarını içeren Team Foundation Server iş öğeleri oluşturmak için Microsoft İzleme Aracısı'nı İşlem Yöneticisi ile birlikte kullanın. Ardından, bu iş öğelerini daha ayrıntılı hata ayıklama için başkalarına atayabilirsiniz. Bkz: [Operations Manager'ı geliştirme süreçleri ile tümleştirme](/previous-versions/system-center/system-center-2012-R2/jj614609(v=sc.12)) ve [Microsoft İzleme Aracısı ile izleme](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).  
  
 Başlamadan önce oluşturulan ve dağıtılan kod için eşleşen kaynağa ve sembollere sahip olup olmadığınızı kontrol edin. Bu, hata ayıklamaya ve IntelliTrace günlüğünde tanılama olaylarını taramaya başladığınızda doğrudan uygulama koduna gitmenizi sağlar. [Yapılarınızı ayarlayın](../debugger/diagnose-problems-after-deployment.md) ve böylece Visual Studio otomatik olarak bulabilir ve dağıtılan kodunuzla eşleşen kaynağı açın.  
  
1.  [1. adım: Microsoft İzleme Aracısı'nı ayarlama](#SetUpMonitoring)  
  
2.  [2. adım: uygulamanızı izlemeye başlama](#MonitorEvents)  
  
3.  [3. adım: Kayıtlı olayları kaydetme](#SaveEvents)  
  
##  <a name="SetUpMonitoring"></a> 1. adım: Microsoft İzleme Aracısı'nı ayarlama  
 Uygulamanızı değiştirmeden yerel izleme yapmak için web sunucunuz üzerinde bağımsız aracıyı ayarlayın. System Center 2012 kullanıyorsanız, bkz [Microsoft Monitoring Agent Yükleme](/previous-versions/system-center/system-center-2012-R2/dn465156(v=sc.12)).  
  
###  <a name="SetUpStandaloneMMA"></a> Bağımsız aracıyı ayarlama  
  
1.  Emin olun:  
  
    -   Web sunucunuz çalışıyor [desteklenen Internet Information Services (IIS) sürümleri](/previous-versions/system-center/system-center-2012-R2/dn465154(v=sc.12)).  
  
    -   Web sunucunuzda .NET Framework 3.5, 4 veya 4.5 sürümü var.  
  
    -   Web sunucunuz Windows PowerShell 3.0 veya sonraki bir sürümü çalışıyor. [S: Windows PowerShell 2.0 varsa yapmalıyım?](#PowerShell2)  
  
    -   Web sunucunuz üzerinde, PowerShell komutlarını çalıştırmak ve izleme başlattığınızda uygulama havuzunu geri dönüştürmek için yönetici izinlerine sahipsiniz.  
  
    -   Microsoft İzleme Aracısı'nın önceki sürümlerini kaldırdınız.  
  
2.  [Ücretsiz Microsoft Monitoring Agent'ı indirin](http://go.microsoft.com/fwlink/?LinkId=320384), 32 bit sürümü **MMASetup-i386.exe** veya 64 bit sürümü **MMASetup-AMD64.exe**, web için Microsoft Download Center gelen Sunucu.  
  
3.  İndirdiğiniz yürütebilen dosyayı çalıştırarak yükleme sihirbazını başlatın.  
  
4.  Örneğin, IntelliTrace günlüklerini depolamak için web sunucunuzda güvenli bir dizin oluşturma **C:\IntelliTraceLogs**.  
  
     Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun. Uygulamanızı yavaşlatmayı önlemek için çok etkin değil yerel bir yüksek hızlı disk üzerinde bir konum seçin.  
  
    > [!IMPORTANT]
    >  IntelliTrace günlükleri kişisel ve hassas veriler içerebilir. Bu dizini yalnızca dosyalarla çalışması gereken kimliklerle sınırlayın. Şirketinizin gizlilik ilkelerini denetleyin.  
  
5.  İşlev düzeyinde ayrıntılı izleme yapmak veya SharePoint uygulamalarını izlemek için, web uygulamanızı veya SharePoint uygulamanızı barındıran uygulama havuzuna IntelliTrace günlük dizini için okuma ve yazma izni verin. [S: uygulama havuzu için izinleri nasıl ayarlayabilirim?](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Soru - Yanıt  
  
####  <a name="PowerShell2"></a> S: Windows PowerShell 2.0 varsa yapmalıyım?  
 **Y:** PowerShell 3.0 kullanmanızı öneririz. Aksi halde, PowerShell'i her çalıştırdığınızda Microsoft İzleme Aracısı PowerShell cmdlet'lerini içeri aktarmanız gerekir. Ayrıca, indirilebilen Yardım içeriğine de erişiminiz olmayacaktır.  
  
1.  Açık bir **Windows PowerShell** veya **Windows PowerShell ISE** yönetici olarak bir komut istemi penceresi.  
  
2.  Varsayılan yükleme konumundan Microsoft İzleme Aracısı PowerShell modülünü içeri aktarın:  
  
     **PS C: > Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3.  [TechNet sitesini ziyaret edin](http://technet.microsoft.com/systemcenter/default) en son Yardım içeriğini almak için.  
  
####  <a name="FullPermissionsITLog"></a> S: uygulama havuzu için izinleri nasıl ayarlayabilirim?  
 **Y:** Windows kullanın **icacls** komutunu ya da Windows Explorer (veya dosya Gezgini) kullanın. Örneğin:  
  
- Windows ile izinleri ayarlamak için **icacls** komutu:  
  
  - İçinde bir web uygulaması için **DefaultAppPool** uygulama havuzu:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
  - Bir SharePoint uygulaması için **SharePoint - 80** uygulama havuzu:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
    veya  
  
- Windows Explorer'ı (ya da File Explorer) ile izinleri ayarlamak için:  
  
  1.  Açık **özellikleri** IntelliTrace günlük dizini için.  
  
  2.  Üzerinde **güvenlik** sekmesini, **Düzenle**, **Ekle**.  
  
  3.  Emin olun **yerleşik güvenlik esasları** görünür **bu nesne türünü seç** kutusu. Bunu sahip değil, seçerseniz **nesne türlerini** ekleyin.  
  
  4.  Yerel bilgisayarınıza emin görünür **bu konumdan** kutusu. Bunu sahip değil, seçerseniz **konumları** değiştirmek için.  
  
  5.  İçinde **Seçilecek nesne adlarını girin** kutusunda, web uygulaması ya da SharePoint uygulaması için uygulama havuzunu ekleyin.  
  
  6.  Seçin **Adları Denetle** adı çözümlenemedi. Seçin **Tamam**.  
  
  7.  Uygulama havuzu olduğundan emin olun **okuma & yürütme** izinleri.  
  
##  <a name="MonitorEvents"></a> 2. adım: uygulamanızı izlemeye başlama  
 Windows PowerShell'i [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) start monitoring your App. komutu. System Center 2012 kullanıyorsanız, bkz [Microsoft Monitoring Agent ile Web uygulamalarını izleme](http://technet.microsoft.com/library/dn465157.aspx).  
  
1.  Web sunucunuzda açık bir **Windows PowerShell** veya **Windows PowerShell ISE** yönetici olarak bir komut istemi penceresi.  
  
     ![Windows PowerShell'i yönetici olarak açın](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2.  Çalıştırma [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) start monitoring your App. komutu. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.  
  
     Kısa sözdizimi şu şekildedir:  
  
     **Start-WebApplicationMonitoring** *"\<uygulamaadı >"*  *\<monitoringMode >* *"\<outputPath >"*  *\<UInt32 >* *"\<collectionPlanPathAndFileName >"*  
  
     İşte yalnızca web uygulaması adı ve basit kullanan bir örnek **İzleyici** modu:  
  
     **PS C: > Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" izleme "C:IntelliTraceLogs"**  
  
     İşte IIS yolunu ve hafif kullanan bir örnek **İzleyici** modu:  
  
     **PS C: > Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" izleme "C:IntelliTraceLogs"**  
  
     İzlemeye başladıktan sonra, uygulamalarınız yeniden başlatılırken Microsoft İzleme Aracısı'nın durakladığını görebilirsiniz.  
  
     ![MMA onay ile izleme Başlat](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\<uygulamaadı >"*|IIS içinde web sitesinin yolunu ve web uygulamasının adını belirtin. İsterseniz IIS yolunu da ekleyebilirsiniz.<br /><br /> *"\<IISWebsiteName >\\< IISWebAppName\>"*<br /><br /> veya<br /><br /> **"IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*<br /><br /> Bu yolu IIS Yöneticisi'nde bulabilirsiniz. Örneğin:<br /><br /> ![IIS web sitesi ve web uygulaması yolu](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> Ayrıca [Get-WebSite](http://technet.microsoft.com/library/ee807832.aspx) ve [Get WebApplication](http://technet.microsoft.com/library/ee790554.aspx) komutları.|  
    |*\<monitoringMode >*|İzleme modunu belirtin:<br /><br /> <ul><li>**İzleyici**: özel durum olayları ve performans olayları hakkında olabildiğince az ayrıntı kaydı. Bu mod varsayılan toplama planını kullanır.</li><li>**İzleme**: işlev düzeyi ayrıntıları kaydettiğinizden ya da belirtilen toplama planını kullanarak SharePoint 2010 ve SharePoint 2013 uygulamaları izleyin. Bu mod, uygulamanızın daha yavaş çalışmasına neden olabilir.<br /><br /> <ul><li>[S: uygulama havuzu için izinleri nasıl ayarlayabilirim?](#FullPermissionsITLog)</li><li>[S: uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?](#Minimizing)</li></ul><br />     Bu örnek, bir SharePoint sitesi üzerindeki SharePoint uygulaması için olayları kaydeder:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" izleme "C:\Program Files\Microsoft Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml izleme" "C:\IntelliTraceLogs"**</li><li>**Özel**: Belirtilen özel toplama planını kullanarak özel ayrıntıları kaydedin. İzleme başladıktan sonra toplama planını değiştirirseniz izlemeyi yeniden başlatmanız gerekir.</li></ul>|  
    |*"\<outputPath >"*|IntelliTrace günlüklerinin depolanacağı tam dizin yolunu belirtin. Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun.|  
    |*\<UInt32 >*|IntelliTrace günlüğünün çıkabileceği en büyük boyutu belirtin. IntelliTrace günlüğü için varsayılan en büyük boyut 250 MB'tır.<br /><br /> Günlük bu sınıra ulaştığında, aracı yeni girişlere yer açmak için en eski girişlerin üzerine yazar. Bu sınırı değiştirmek için kullanın **- Maximumfilesizeınmegabytes** seçeneğini veya düzenleme `MaximumLogFileSize` toplama planında özniteliği.|  
    |*"\<collectionPlanPathAndFileName >"*|Toplama planının tam yolunu veya göreli yolunu ve dosya adını belirtin. Bu plan, aracı için ayarları yapılandıran bir .xml dosyasıdır.<br /><br /> Bu planlar aracıyla birlikte gelir ve web uygulamaları ve SharePoint uygulamalarıyla çalışır:<br /><br /> -   **collection_plan.ASP.NET.default.XML**<br />     Yalnızca özel durumlar, performans olayları, veritabanı çağrıları ve Web sunucusu istekleri gibi olayları toplar.<br />-   **collection_plan.ASP.NET.Trace.XML**<br />     Varsayılan toplama planındaki verilere ek olarak işlev düzeyi çağrıları toplar. Bu plan ayrıntılı analiz için iyidir ancak uygulamanızı yavaşlatabilir.<br /><br /> Bu planların yerelleştirilmiş sürümlerini aracının alt klasörlerinde bulabilirsiniz. Ayrıca [bu planları özelleştirebilir veya kendi planlarınızı oluşturabilirsiniz](http://go.microsoft.com/fwlink/?LinkId=227871) uygulamanızı yavaşlatmayı önlemek için. Özel planları aracıyla aynı güvenli konuma yerleştirin.<br /><br /> [S: uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?](#Minimizing)|  
  
     Tam söz dizimi ve diğer örnekler hakkında daha fazla bilgi için çalıştırma **get-help Start-WebApplicationMonitoring-ayrıntılı** komutu veya **get-help Start-WebApplicationMonitoring-örnekler** komutu.  
  
3.  Çalıştırdığınız web uygulamalarında, izlenen tüm durumunu denetlemek için [Al-WebApplicationMonitoringStatus](http://go.microsoft.com/fwlink/?LinkID=313685) komutu.  
  
### <a name="q--a"></a>Soru - Yanıt  
  
####  <a name="Minimizing"></a> S: uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?  
 **Y:** Microsoft İzleme Aracısı çok fazla veri toplayabilir ve toplamasını veriler ve nasıl topladığınıza göre uygulamanızın performansını etkiler. Uygulamanızı yavaşlatmadan en çok veriyi almak için bazı yollar şunlardır:  
  
- Web uygulamaları ve SharePoint uygulamaları için, aracı belirtilen uygulama havuzunu paylaşan her uygulama için veri kaydeder. Bu aynı uygulama havuzunu paylaşan herhangi bir uygulamayı, toplamayı tek bir uygulamanın modüllerine kısıtlamanıza rağmen yavaşlatabilir. Diğer uygulamaları yavaşlatmayı önlemek için, her uygulamayı kendi uygulama havuzunda barındırın.  
  
- Toplama planında aracının veri topladığı olayları gözden geçirin. Uygun olmayan veya sizi İlginiz dahilinde olmayan olayları devre dışı bırakmak için toplama planını düzenleyin. Bu, başlangıç ve çalışma zamanı performansını artırabilir.  
  
   Bir olayı devre dışı bırakmak için ayarlanmış `enabled` özniteliğini `<DiagnosticEventSpecification>` öğesine `false`:  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   Varsa `enabled` öznitelik yoksa, olay etkinleştirilmiştir.  
  
   Örneğin:  
  
  -   Windows Workflow kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.  
  
  -   Kayıt defterine erişen ancak kayıt defteri ayarlarında sorun göstermeyen uygulamalar için kayıt defteri olaylarını devre dışı bırakın.  
  
- Toplama planında aracının veri topladığı modülleri gözden geçirin. Toplama planını yalnızca ilginizi çeken modülleri içerecek şekilde düzenleyin.  
  
   Bu uygulama başladığında ve çalıştığında aracının topladığı yöntem çağrı bilgisi ve diğer araç verisi miktarını azaltır. Bu veriler, hata ayıklarken kod içinde adım adım ilerlemenize ve işlev çağrılarına gönderilen ve bu çağrılardan alınan değerleri gözden geçirmenize yardımcı olur.  
  
  1. Toplama planını açın. Bulma `<ModuleList>` öğesi.  
  
  2. İçinde `<ModuleList>`ayarlayın `isExclusionList` özniteliğini `false`.  
  
  3. Kullanım `<Name>` her modülü aşağıdakileri biri ile belirtmek için öğe: dosya adı, adında, dize veya ortak anahtar içeren her modülü içermek için dize değeri.  
  
     Bu örnek, Fabrikam Fiber web uygulamasının yalnızca ana modülünden veri toplayan bir liste oluşturur:  
  
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
  
   **S: neden değil yalnızca modülleri yerine dışlansın mı?**  
  
   **Y:** varsayılan olarak ayarlayarak toplama planlarını modülleri hariç `isExclusionList` özniteliğini `true`. Ancak bu, yine de üçüncü taraf veya açık kaynak modüller gibi listenin ölçütlerine uymayan veya ilgilenmediğiniz modüllerden veri toplayabilir.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>S: Aracı hangi değerleri toplar?  
 **Y:** performans üzerindeki etkiyi azaltmak için aracı yalnızca şu değerleri toplar:  
  
- Yöntemlere geçirilen ve yöntemlerden döndürülen ilkel veri türleri  
  
- Yöntemlere geçirilen veya yöntemlerden geri döndürülen en üst düzey nesnelerin alanlarındaki ilkel veri türleri  
  
  Örneğin, sahip olduğunuz varsayalım. bir `AlterEmployee` kabul eden bir tamsayı yöntem imzası `id` ve `Employee` nesne `oldemployee`:  
  
  `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
  `Employee` Türü şu öznitelikler bulunur: `Id`, `Name`, ve `HomeAddress`. Arasında bir ilişkilendirme ilişkisi var. `Employee` ve `Address` türü.  
  
  ![Çalışan ve adresi arasındaki ilişkiyi](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
  Aracı `id`, `Employee.Id` ve `Employee.Name` değerlerini ve `Employee` yönteminden döndürülen `AlterEmployee` nesnesini kaydeder. Ancak aracı `Address` nesnesi hakkında, nesnenin null olup olmadığı dışında bilgi kaydetmez. Aracı, ayrıca, `AlterEmployee` yöntemindeki yerel değişkenlerle ilgili olarak, diğer yöntemler bu yerel değişkenleri parametre olarak kullanıp onların yöntem parametresi olarak kaydedilmesini sağlamadığı sürece, veri kaydetmez.  
  
##  <a name="SaveEvents"></a> 3. adım: Kayıtlı olayları kaydetme  
 Bir hata veya performans sorunu bulduğunuzda, kayıtlı olayları bir IntelliTrace günlüğüne kaydedin. Aracı günlüğü yalnızca olay kaydettiyse oluşturur. System Center 2012 kullanıyorsanız, bkz [Microsoft Monitoring Agent ile Web uygulamalarını izleme](http://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Kayıtlı olayları kaydedip izlemeye devam etme  
 IntelliTrace günlüğünü oluşturmak istediğinizde ancak uygulamanızı yeniden başlatmak veya izlemeyi durdurmak istemediğinizde bu adımları izleyin. Aracı, sunucu veya uygulama yeniden başlasa bile izlemeye devam eder.  
  
1. Web sunucunuzda yönetici olarak bir Windows PowerShell komut istemi penceresi açın.  
  
2. Çalıştırma [Checkpoint-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313684) komut IntelliTrace günlüğünün görüntüsünü kaydetmek için:  
  
    **Checkpoint-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- veya -  
  
    **Checkpoint-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Örneğin:  
  
    **PS C:\\> Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
    veya  
  
    **PS C: > Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**  
  
    Daha fazla bilgi için **Checkpoint-WebApplicationMonitoring get-help-ayrıntılı** komutu veya **Checkpoint-WebApplicationMonitoring get-help-örnekler** komutu.  
  
3. Günlüğü güvenli paylaşılan klasöre kopyalayın ve Visual Studio Enterprise (ancak Professional veya Community sürümlerini) sahip bir bilgisayarda oturum açın.  
  
   > [!IMPORTANT]
   >  Kişisel ve hassas veriler içerebileceklerinden, IntelliTrace günlüklerini paylaşırken dikkatli olun. Bu günlüklere erişebilen kişilerin o verileri görme izni olduğundan emin olun. Şirketinizin gizlilik ilkelerini denetleyin.  
  
   **Sonraki:** [Tanıla kaydedilen olayları Visual Studio Enterprise'da](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Kayıtlı olayları kaydedip izlemeyi durdurma  
 Belirli bir sorunu yeniden oluştururken yalnızca tanı bilgilerini almak istediğinizde bu adımları izleyin. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.  
  
1. Web sunucunuzda yönetici olarak bir Windows PowerShell komut istemi penceresi açın.  
  
2. Çalıştırma [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) IntelliTrace günlüğü oluşturmak ve belirli bir web uygulamasını izlemeyi durdurmak için komut:  
  
    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- veya -  
  
    **Webuygulamasınıizlemeyi Durdur "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Veya tüm web uygulamaları izlemeyi durdurmak için:  
  
    **Stop-WebApplicationMonitoring - tüm**  
  
    Örneğin:  
  
    **PS C:\\> Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
    \- veya -  
  
    **PS C:\\> Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**  
  
    Daha fazla bilgi için **Stop-WebApplicationMonitoring get-help-ayrıntılı** komutu veya **Stop-WebApplicationMonitoring get-help-örnekler** komutu.  
  
3. Günlüğü güvenli paylaşılan klasöre kopyalayın ve Visual Studio Enterprise'ı olan bir bilgisayarda oturum açın.  
  
   **Sonraki:** [Tanıla kaydedilen olayları Visual Studio Enterprise'da](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Soru - Yanıt  
  
### <a name="q-where-can-i-get-more-information"></a>S: Nereden daha fazla bilgi edinebilirim?  
  
#### <a name="blogs"></a>Bloglar  
 [Microsoft İzleme Aracısı ile tanışın](https://blogs.msdn.microsoft.com/devops/2013/09/20/introducing-microsoft-monitoring-agent/)  
  
 [Üretim sunucularında IntelliTrace koleksiyonu en iyileştirme](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
#### <a name="forums"></a>Forumlar  
 [Visual Studio tanılama](http://go.microsoft.com/fwlink/?LinkId=262263)
