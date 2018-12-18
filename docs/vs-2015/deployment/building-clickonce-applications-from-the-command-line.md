---
title: Komut satırından ClickOnce uygulamaları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c9a9b2e248e4f10e9b5d3f045c67a9622edd2c2b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220023"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Komut Satırından ClickOnce Uygulamalarını Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], tümleşik geliştirme ortamında (IDE) oluşturulmamış olsa bile, komut satırından projeleri oluşturabilirsiniz. Aslında, ile oluşturulmuş bir projeyi yeniden oluşturabilirsiniz [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yalnızca olan başka bir bilgisayara [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yüklü. Bu, otomatik bir işlem kullanılarak yapı oluşturmanızı sağlar, örneğin, merkezi bir yapı içinde Laboratuvar veya kullanarak, proje oluşturma kapsamı dışında teknikleri Gelişmiş.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>ClickOnce Uygulama dağıtımlarını yeniden oluşturmak için MSBuild kullanma  
 Komut satırında msbuild/target: publish çağırdığınızda, projeyi derlemek ve oluşturmak için MSBuild sistemi söyler. bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yayımlama klasörü uygulaması. Bu seçmeye eşdeğerdir **Yayımla** IDE'de komutu.  
  
 Bu komut, Visual Studio komut istemi ortamı yolunda msbuild.exe yürütür.  
  
 Bir "hedef" bir MSBuild komut işlemek nasıl göstergesidir. Anahtar hedefleri şunlardır: "derleme" hedef ve "Yayımla" hedef. Yapı hedefi yapı seçme eşdeğerdir IDE'de komutu (veya F5 tuşuna basarak). Yalnızca derleme istiyorsanız, yazarak elde edebileceğiniz `msbuild`. Derleme hedefini varsayılan hedef tarafından oluşturulan tüm projeler için olduğundan, bu komut çalışır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Başka bir deyişle, açıkça yapı hedefi belirtmek gerekmez. Bu nedenle, yazmaya `msbuild` yazarak olarak aynı işlem `msbuild /target:build`.  
  
 `/target:publish` Komutu yayımlama hedefi MSBuild'e bildirir. Yayımlama hedefi, yapı hedefine bağlıdır. Bu, yayımlama işlemi oluşturma işlemi üst olduğu anlamına gelir. Örneğin, bir Visual Basic veya C# kaynak dosyaları için bir değişiklik yaptıysanız, karşılık gelen derleme yayımlama işlemi tarafından otomatik olarak yeniden yapılandırılacaktır.  
  
 Tam oluşturma hakkında bilgi [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımı oluşturmak için Mage.exe komut satırı aracını kullanarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimi için bkz: [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Oluşturma ve MSBuild'ı kullanarak temel bir ClickOnce uygulaması oluşturma  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Oluşturma ve bir ClickOnce projeyi yayımlama  
  
1. Tıklayın **yeni proje** gelen **dosya** menüsü. **Yeni proje** iletişim kutusu görüntülenir.  
  
2. Seçin **Windows uygulama** ve adlandırın `CmdLineDemo`.  
  
3. Gelen **derleme** menüsünde tıklatın **Yayımla** komutu.  
  
    Bu adım projeyi oluşturmak için düzgün yapılandırıldığını sağlar bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama dağıtımı.  
  
    Yayınla Sihirbazı görüntülenir.  
  
4. Yayımlama Sihirbazı'nda tıklatın **son**.  
  
    Visual Studio oluşturur ve Publish.htm adlı varsayılan Web sayfası görüntülenir.  
  
5. Projenizi kaydedin ve onu depolandığı klasör konumunu not edin.  
  
   Yukarıdaki adımları oluşturma bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ilk kez yayımlanan bir proje. Artık derleme IDE dışında yeniden oluşturabilirsiniz.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Komut satırından derleme yeniden oluşturmak için  
  
1. Çıkış [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. Windows gelen **Başlat** menüsünde tıklayın **tüm programlar**, ardından **Microsoft Visual Studio**, ardından **Visual Studio Araçları**, ardından **Visual Studio komut istemi**. Bu, geçerli kullanıcının kök klasöründe bir komut istemi açmanız gerekir.  
  
3. İçinde **Visual Studio komut istemi**, geçerli dizini yalnızca yerleşik yukarıda projenin konumunu değiştirin. Örneğin, `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Üretilen mevcut dosyaları kaldırmak için "oluşturmak ve yayımlamak için bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projesi" türü `rmdir /s publish`.  
  
    Bu adım isteğe bağlıdır, ancak yeni dosyalar tüm komut satırı derleme tarafından üretilen sağlar.  
  
5. Türü `msbuild /target:publish`  
  
   Yukarıdaki adımları tam üretecektir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projenizin adlı bir alt uygulama dağıtımı **Yayımla**. CmdLineDemo.Application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi. CmdLineDemo_1.0.0.0 klasörü CmdLineDemo.exe dosyaları CmdLineDemo.exe.manifest ve dosyalarını içeren [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi. Setup.exe olduğundan, varsayılan olarak yüklemek için yapılandırılmış önyükleyici [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. DotNetFX klasörü için yeniden dağıtılabilir dosyaları içeren [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Web üzerinden ya da UNC veya CD/DVD aracılığıyla uygulamanızı dağıtmak için gereken dosya kümesinin tamamını budur.  
  
## <a name="publishing-properties"></a>Yayımlama özellikleri  
 Yukarıdaki yordamlarda uygulama yayımladığınızda, aşağıdaki özellikler, Yayımla Sihirbazı tarafından proje dosyanıza eklenir. Bu özellikleri doğrudan etkilemek nasıl [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama oluşturulur.  
  
 CmdLineDemo.vbproj / CmdLineDemo.csproj içinde:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Proje dosyasının kendisini değiştirmeden komut satırında bu özelliklerden herhangi birini geçersiz kılabilirsiniz. Örneğin, aşağıdaki oluşturacaksınız [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] önyükleyici olmadan uygulama dağıtımı:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Yayımlama özellikleri denetlenir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gelen **Yayımla**, **güvenlik**, ve **imzalama** özellik sayfalarından **Proje Tasarımcısı** . Her Uygulama Tasarımcısı çeşitli özellik sayfalarında ayarlanmış nasıl bir gösterge ile birlikte yayımlama özellikleri açıklaması aşağıda verilmiştir:  
  
- `AssemblyOriginatorKeyFile` oturum açmak için kullanılan anahtar dosyasını belirler, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimleri. Bu anahtarı, tanımlayıcı ad atamak için de kullanılabilir. Bu özellik üzerinde ayarlanır **imzalama** sayfasının **Proje Tasarımcısı**.  
  
  Aşağıdaki özellikler ayarlanır **güvenlik** sayfası:  
  
- **ClickOnce güvenlik ayarlarını etkinleştirme** belirler olmadığını [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirimleri oluşturulur. Bir proje ilk oluşturulduğunda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bildirim oluşturma varsayılan olarak kapalıdır. Sihirbaz, bu bayrak, ilk kez yayımladığınızda üzerinde otomatik olarak açılır.  
  
- **TargetZone** için güven düzeyini belirler, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi. Olası değerler şunlardır: "Internet", "LocalIntranet" ve "Özel". Internet ve LocalIntranet için varsayılan bir izin neden olur, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi. LocalIntranet varsayılandır ve temel tam güven anlamına gelir. Özel belirtir için yalnızca temel App.manifest'i dosyasında açıkça belirtilen izinleri olduğunu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi. Yalnızca güven bilgi tanımları içeren kısmi bir bildirim dosyası app.manifest dosyasıdır. İzinleri yapılandırdığınızda otomatik olarak projenize eklenir gizli bir dosya olan **güvenlik** sayfası.  
  
  Aşağıdaki özellikler ayarlanır **Yayımla** sayfası:  
  
- `PublishUrl` Uygulama IDE içinde yayımlanır burada konumdur. İçine eklenir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi kullanılmazsa `InstallUrl` veya `UpdateUrl` özelliği belirtildi.  
  
- `ApplicationVersion` sürümünü belirtir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. Bu dört basamaklı sürüm numarasıdır. Son basamağı ise bir "*", ardından `ApplicationRevision` derleme zamanında bildirim içine eklenen değeri konur.  
  
- `ApplicationRevision` Düzeltme belirtir. Bu, IDE'de yayımladığınız her zaman yükseltir tamsayıdır. Bu otomatik olarak komut satırında gerçekleştirilen derlemeler için artmaz, dikkat edin.  
  
- `Install` uygulamanın yüklü bir uygulama veya bir çalışma alanından Web uygulaması olup olmadığını belirler.  
  
- `InstallUrl` (gösterilmemiştir), burada, kullanıcılar uygulamayı yükleyecek konumdur. Belirtilmişse bu değer setup.exe önyükleyicisi içine `IsWebBootstrapper` özelliği etkin hale getirilir. Uygulama bildirim if eklenir `UpdateUrl` belirtilmedi.  
  
- `SupportUrl` (gösterilmemiştir) konumu olarak bağlı **Program Ekle/Kaldır** yüklü bir uygulama için iletişim kutusu.  
  
  Aşağıdaki özellikleri ayarlayın **uygulama güncelleştirmeleri** iletişim kutusu, erişilen **Yayımla** sayfası.  
  
- `UpdateEnabled` Uygulama güncelleştirmeleri denetlesin olup olmadığını gösterir.  
  
- `UpdateMode` ön plan güncelleştirmeleri ya da arka plan güncelleştirmeleri belirtir.  
  
- `UpdateInterval` uygulamanın güncelleştirmeleri ne sıklıkla denetlemesi gerektiğini belirtir.  
  
- `UpdateIntervalUnits` belirtir olup olmadığını `UpdateInterval` birimleri saat, gün veya hafta cinsinden bir değerdir.  
  
- `UpdateUrl` (gösterilmemiştir), uygulama güncelleştirmelerini alacağı konumdur. Belirtilmişse bu değer, uygulama bildirimine eklenir.  
  
- Aşağıdaki özellikleri ayarlayın **yayımlama seçeneği** iletişim kutusu, erişilen **Yayımla** sayfası.  
  
- `PublisherName` yüklediğinizde veya uygulamayı çalıştıran gösterilen satırında görüntülenen yayımcı adını belirtir. Yüklü bir uygulama söz konusu olduğunda da klasör adı belirtmeniz kullanıldığı **Başlat** menüsü.  
  
- `ProductName` yüklediğinizde veya uygulamayı çalıştıran gösterilen istemde ürün adını belirtir. Yüklü bir uygulama söz konusu olduğunda, bu da kısayol adı üzerinde belirtmek için kullanılan **Başlat** menüsü.  
  
- Aşağıdaki özellikleri ayarlayın **önkoşulları** iletişim kutusu, erişilen **Yayımla** sayfası.  
  
- `BootstrapperEnabled` setup.exe önyükleyici oluşturulup oluşturulmayacağını belirler.  
  
- `IsWebBootstrapper` setup.exe önyükleyici Web üzerinden veya disk tabanlı modunda çalışıp çalışmadığını belirler.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallUrl, SupportUrl PublishURL ve UpdateURL  
 ClickOnce dağıtımı için dört URL seçenekleri aşağıdaki tabloda gösterilmektedir.  
  
|URL seçeneği|Açıklama|  
|----------------|-----------------|  
|`PublishURL`|ClickOnce uygulamanızı bir Web sitesi için yayımlama durumunda gereklidir.|  
|`InstallURL`|İsteğe bağlı. Yükleme sitesi farklıdır, bu URL seçeneği ayarlamak `PublishURL`. Örneğin, ayarlayabilirsiniz `PublishURL` bir FTP yolu ve kümesi `InstallURL` Web URL.|  
|`SupportURL`|İsteğe bağlı. Destek sitesi farklıdır, bu URL seçeneği ayarlamak `PublishURL`. Örneğin, ayarlayabilirsiniz `SupportURL` şirketinizin Müşteri Destek Web sitesi için.|  
|`UpdateURL`|İsteğe bağlı. Güncelleştirme konumu farklıdır, bu URL seçeneği ayarlamak `InstallURL`. Örneğin, ayarlayabilirsiniz `PublishURL` bir FTP yolu ve kümesi `UpdateURL` Web URL.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



