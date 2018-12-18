---
title: Geliştirme ve Test ortamları için yayımlamak için Windows PowerShell betiklerini kullanarak | Microsoft Docs
description: Windows PowerShell betikleri Visual Studio'dan yayımlamak için geliştirme ve test ortamları kullanmayı öğrenin.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 350ad1910cfdfe20d5b4b9b8d018229c712de547
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621652"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell betiklerini kullanarak geliştirme ve test ortamlarına yayımlama

Visual Studio'da bir web uygulaması oluştururken, daha sonra Azure Web sitenize bir Web uygulamasını Azure App Service veya bir sanal makine olarak yayımlamak için kullanabileceğiniz bir Windows PowerShell Betiği oluşturabilirsiniz. Düzenle ve Windows PowerShell betiğini gereksinimlerinize uydurmak için Visual Studio düzenleyicisinde genişletmek veya betiği var olan yapı, test ve yayımlama betikleriyle ile tümleştirebilirsiniz.

Bu komut dosyalarını kullanarak siteniz geçici kullanım için özelleştirilmiş sürümlerini (geliştirme ve test ortamı olarak da bilinir) sağlayabilirsiniz. Örneğin, sitenizi bir Azure sanal makinesinde veya hazırlama yuvasına bir test paketi çalıştırmak, bir hatayı yeniden oluşturma, önerilen bir değişikliğin hata düzeltmesi, deneme test veya bir tanıtım veya sunum için özel bir ortamı ayarlama için bir Web sitesinde belirli bir sürümü ayarlayabilir. Projenizi yayımlayan bir komut dosyası oluşturduktan sonra gerektiğinde komut dosyasını çalıştırarak aynı ortamlarını veya test için özel bir ortam oluşturmak için web uygulamanızın kendi derlemesiyle betiği çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

* Azure SDK 2.3 veya üstü. Bkz: [Visual Studio indirmeleri](http://go.microsoft.com/fwlink/?LinkID=624384). (Web projeleri için komut dosyaları oluşturmak için Azure SDK'sı gerekmez. Web projeleri, bulut hizmetlerinde değil web rolü için bu özellik kullanılabilir.)
* Azure PowerShell 0.7.4 veya üzeri. Bkz: [Azure PowerShell'i yükleme ve yapılandırma işlemini](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) veya üzeri.

## <a name="additional-tools"></a>Ek araçlar

Ek araçlar ve kaynaklar Azure geliştirme için Visual Studio'da PowerShell ile çalışmak için kullanılabilir. Bkz: [Visual Studio için PowerShell Araçları](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Yayımlama betiklerini oluşturma

Yayımlama betiklerini izleyerek yeni bir proje oluşturduğunuzda, Web sitenizi barındıran bir sanal makine için oluşturabileceğiniz [bu yönergeleri](/azure/virtual-machines/windows/classic/web-app-visual-studio). Ayrıca [oluşturma betikleri web apps için Azure App Service'te yayımlama](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio oluşturan betikler

Visual Studio'nun oluşturduğu adlı bir çözüm düzeyinde klasör **PublishScripts** iki Windows PowerShell dosyaları, sanal makineniz veya Web sitesi ve kullanabileceğiniz işlevler içeren bir modül için bir yayımlama betik içerir komut dosyaları. Visual Studio, ayrıca dağıtmakta olduğunuz projeye ayrıntılarını belirtir JSON biçiminde bir dosya oluşturur.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell komut dosyası yayımlama

Yayımlama betiği, bir Web sitesi veya sanal makine dağıtmak için belirli bir yayımlama adımları içerir. Visual Studio geliştirme için Windows PowerShell renklendirme söz dizimi sağlar. İşlevleri, kullanılabilir ve değişen iş gereksinimlerinize uyacak şekilde betiğinde işlevleri serbestçe düzenleyebileceğiniz yardımcı olur.

### <a name="windows-powershell-module"></a>Windows PowerShell modülü

Visual Studio oluşturan Windows PowerShell modülünü yayımlama komut dosyası kullanan işlevler içerir. Azure PowerShell Bu işlevler, değiştirilecek amaçlanmamıştır. Bkz: [Azure PowerShell'i yükleme ve yapılandırma işlemini](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON yapılandırma dosyası

JSON dosyası oluşturulur **yapılandırmaları** klasörü ve Azure'a dağıtmak için tam olarak hangi kaynakların belirten yapılandırma verilerini içerir. Proje-adı-WAWS-bir sanal makine oluşturduysanız, bir Web sitesi ya da proje adı-VM-dev.json oluşturduysanız dev.json Visual Studio'nun oluşturduğu dosya adıdır. Web sitesi oluşturduğunuzda oluşturulan bir JSON yapılandırma dosyası örneği aşağıdadır. Değerler çoğu kendinden açıklamalıdır. Projenizin adına eşleşmeyebilir için Web sitesi adı, Azure tarafından oluşturulur.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Bir sanal makine oluşturduğunuzda, JSON yapılandırma dosyası aşağıdakine benzer. Bir bulut hizmeti sanal makine için bir kapsayıcı olarak oluşturulur. Sanal makine için yerel makine, Uzak Masaüstü ve Windows PowerShell Web sitesine yayımlamanıza imkan tanıyan Web dağıtımı, uç noktaları yanı sıra genel uç noktaları için HTTP ve HTTPS üzerinden web erişimini içerir.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Yayımlama komut dosyalarını çalıştırdığınızda neler değiştirmek için JSON yapılandırmasını düzenleyebilirsiniz. `cloudService` Ve `virtualMachine` bölümleri gereklidir, ancak silebilirsiniz `databases` ihtiyacınız yoksa bölümü. Visual Studio'nun oluşturduğu varsayılan yapılandırma dosyası boş özellikleri isteğe bağlıdır; varsayılan yapılandırma dosyasında değerleri olan bu özellikleri gereklidir.

Azure'da tek üretim sitesi yerine birden çok dağıtım ortamı (yuvaları bilinir) sahip bir Web sitesi varsa, Web sitesi adını yuva adı JSON yapılandırma dosyasına dahil edebilirsiniz. Örneğin, adında bir Web sitesi varsa **mysite** ve onu adlı yuvasını **test** URI sonra `mysite-test.cloudapp.net`, ancak yapılandırma dosyasında kullanılacak doğru adı mysite(test). Bu, yalnızca Web sitesi yapabilirsiniz ve yuvaları aboneliğinizde zaten mevcut. Yoksa, Web sitesi oluşturma yuvası belirtmeden betiği çalıştırarak, daha sonra Yuvanın oluşturma [Azure portalında](https://portal.azure.com/), ve bundan sonra değiştirilmiş Web sitesi adı ile betiğini çalıştırın. Dağıtım yuvaları için web apps hakkında daha fazla bilgi için bkz. [hazırlık Azure App service'taki web apps için ortamları ayarlama](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Yayımlama komut dosyalarını nasış çalıştıracağını

Önce bir Windows PowerShell Betiği çalıştırılmadı, betiklerin etkinleştirme yürütme ilkesini ayarlamanız gerekir. İlke, kullanıcıların, kötü amaçlı yazılım veya betikleri yürütülürken gerektiren virüsler için güvenlik açığı kullanıyorsanız Windows PowerShell betikleri çalıştırma önlemek için bir güvenlik özelliğidir.

### <a name="run-the-script"></a>Betiği çalıştırın

1. Projeniz için Web dağıtımı paketi oluşturun. Bir Web Dağıtımı Web sitenize veya sanal makine için kopyalamak istediğiniz dosyaları içeren bir sıkıştırılmış arşiv (.zip dosyası) paketidir. Visual Studio Web dağıtımı paketleri için herhangi bir web uygulaması oluşturabilirsiniz.

   ![Oluşturma Web dağıtım paketi](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir Web dağıtım paketi oluşturma](https://msdn.microsoft.com/library/dd465323.aspx). Web dağıtımı paketi oluşturulmasını açıklandığı otomatikleştirebilirsiniz [özelleştirme ve genişletme yayımlama betiklerini](#customizing-and-extending-publish-scripts).

1. İçinde **Çözüm Gezgini**, betik için bağlam menüsünü açın ve ardından **ile PowerShell ISE'yi açın**.
1. Windows PowerShell betikleri, bu bilgisayarda ilk kez çalıştırılıyorsa, yönetici ayrıcalıklarıyla bir komut istemi penceresi açın ve aşağıdaki komutu yazın:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Aşağıdaki komutu kullanarak Azure'da oturum açın.

    ```powershell
    Add-AzureAccount
    ```

    İstendiğinde, kullanıcı adı ve parola girin.

    Bu yöntem, Azure kimlik bilgileri sağlama betiği otomatikleştirin, işe yaramayacağını aklınızda bulundurun. Bunun yerine, kullanmanız `.publishsettings` dosyasının kimlik bilgilerini sağlayın. Komutu, sizin yalnızca bir kez kullanın **Get-AzurePublishSettingsFile** Azure'dan dosyasını indirin ve bundan sonra **Import-AzurePublishSettingsFile** dosya içeri aktarılamıyor. Ayrıntılı yönergeler için bkz. [Azure PowerShell'i yükleme ve yapılandırma işlemini](/powershell/azure/overview).

1. (İsteğe bağlı) Sanal makine gibi Azure kaynaklarını oluşturmak istiyorsanız, veritabanı ve web uygulamanızı yayımlamayı olmadan Web sitesi kullanmak **Yayımla WebApplication.ps1** komutunu **-yapılandırma**bağımsız değişken kümesi için JSON yapılandırma dosyası. Bu komut satırı, hangi kaynakların oluşturulacağını belirlemek için JSON yapılandırma dosyasını kullanır. Diğer komut satırı bağımsız değişkenleri için varsayılan ayarları kullandığından, kaynakları oluşturur, ancak web uygulamanızı yayımlayın değil. Verbose seçeneği olup bitenler hakkında daha fazla bilgi sağlar.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Kullanım **Yayımla WebApplication.ps1** betik çağırma ve web uygulamanızı yayımlamak için aşağıdaki örneklerden birini gösterildiği komutu. Abonelik adı gibi diğer bağımsız değişkenlerden biri için varsayılan ayarları geçersiz kılacak gerekiyorsa paket adı, sanal makine kimlik bilgileri veya veritabanı sunucusu kimlik bilgilerini yayımlama, bu parametreleri belirtebilirsiniz. Kullanım **– ayrıntılı** yayımlama işleminin ilerleme durumu hakkında daha fazla bilgi görmek için Seçenekler.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Bir sanal makine oluşturuyorsanız, komutu aşağıdaki gibi görünür. Bu örnek, birden fazla veritabanı için kimlik bilgilerini belirleme konusunda da gösterir. Bu komut dosyaları oluşturma makineler için SSL sertifikasını bir güvenilir kök yetkilisi değil. Bu nedenle, kullanmanız gerekir **– AllowUntrusted** seçeneği.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Betik, veritabanı oluşturabilirsiniz, ancak veritabanı sunucuları oluşturmaz. Bir veritabanı sunucusu oluşturmak istiyorsanız, kullanabileceğiniz **yeni AzureSqlDatabaseServer** Azure modülündeki işlevi.

## <a name="customizing-and-extending-the-publish-scripts"></a>Yayımlama betiklerini genişletme ve özelleştirme

Yayımlama betiği ve JSON yapılandırma dosyası özelleştirebilirsiniz. Windows PowerShell modülündeki işlevleri **AzureWebAppPublishModule.psm1** değiştirilecek amaçlanmamıştır. Yalnızca farklı bir veritabanı belirtin veya sanal makinenin özelliklerini bazılarını değiştirmek istiyorsanız, JSON yapılandırma dosyasını düzenleyin. Oluşturma ve projenizi sınamayı otomatikleştirmek için betik genişletmek istiyorsanız, içinde işlevi saptamalar uygulayabilirsiniz **Yayımla WebApplication.ps1**.

Projenizi oluşturma otomatikleştirmek için MSBuild'e çağıran kod ekleme `New-WebDeployPackage` Bu kod örneğinde gösterildiği gibi. MSBuild komut yolu, yüklediğiniz Visual Studio sürümüne bağlı olarak farklılık gösterir. Doğru olan yolu almak için bu işlevi kullanabilirsiniz **Get-MSBuildCmd**, bu örnekte gösterildiği gibi.

### <a name="to-automate-building-your-project"></a>Projenizi oluşturma otomatik hale getirmek için

1. Ekleme `$ProjectFile` genel parametre bölümünde parametresi.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copy işlevi `Get-MSBuildCmd` , betik dosyasına.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Değiştirin `New-WebDeployPackage` ile aşağıdaki kod ve satır oluştururken yer tutucularını değiştirin `$msbuildCmd`. Bu kod, Visual Studio 2017 için aynıdır. Visual Studio 2015 kullanıyorsanız, değiştirme **VisualStudioVersion** özelliğini `14.0` (`12.0` Visual Studio 2013 için).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Web uygulamanızı oluşturmak üzere MsBuild.exe kullanın. Yardım almak için MSBuild komut satırı başvurusuna bakın: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=15.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Yapı komut yürütme işlemini Başlat

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Çağrı `New-WebDeployPackage` işlevi bu satırı önce: `$Config = Read-ConfigFile $Configuration` web apps için veya `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` sanal makineleri için.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Özelleştirilmiş betik geçirme kullanarak komut satırından çağırma `$Project` aşağıdaki örnekteki gibi bağımsız değişkeni:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Uygulamanızı testleri otomatikleştirmek için kod ekleyin. `Test-WebApplication`. Satırları açıklama durumundan çıkarın mutlaka **Yayımla WebApplication.ps1** burada bu işlev çağrılır. Bir uygulama sağlamazsanız, el ile Visual Studio ile derleme ve daha sonra Azure'da yayımlamak için publish betiği çalıştırın.

## <a name="publishing-function-summary"></a>Özet yayımlama işlevi
Windows PowerShell komut isteminde kullanabileceğiniz işlevleri için Yardım almak için bir komut kullanın `Get-Help function-name`. Yardımı, parametre Yardımı ve örnekler içerir. Aynı Yardım metnini da betik kaynak dosyalarında olduğu **AzureWebAppPublishModule.psm1** ve **Yayımla WebApplication.ps1**. Yardım ve betik, Visual Studio dilde yerelleştirilmiş.

**AzureWebAppPublishModule**

| İşlev adı | Açıklama |
| --- | --- |
| Add-AzureSQLDatabase |Yeni bir Azure SQL veritabanı oluşturur. |
| Add-AzureSQLDatabases |Visual Studio'nun oluşturduğu JSON yapılandırma dosyası değerlerini Azure SQL veritabanı oluşturur. |
| Add-AzureVM |Bir Azure sanal makinesi oluşturur ve dağıtılan VM URL'sini döndürür. İşlev önkoşulları ayarlar ve sonra çağıran **New-AzureVM** yeni bir sanal makine oluşturmak için (Azure Modülü) işlevi. |
| Add-AzureVMEndpoints |Yeni giriş uç noktaları bir sanal makineye ekler ve sanal makine yeni uç nokta ile döndürür. |
| Ekle-AzureVMStorage |Geçerli abonelikte yeni bir Azure depolama hesabı oluşturur. Hesap adını "benzersiz bir alfasayısal dize tarafından izlenen devtest" ile başlar. İşlev, yeni depolama hesabı adını döndürür. Bir konum veya yeni bir depolama hesabı için bir benzeşim grubu belirtin. |
| Add-AzureWebsite |Belirtilen ad ve konum ile bir Web sitesi oluşturur. Bu işlev çağrıları **New-AzureWebsite** Azure modülündeki işlevi. Abonelik zaten belirtilen ada sahip bir Web sitesi içermiyorsa, bu işlev, Web sitesi oluşturur ve bir Web sitesi nesnesi döndürür. Aksi halde `$null`. |
| Yedekleme aboneliği |Geçerli bir Azure aboneliğinde kaydeder `$Script:originalSubscription` betik kapsamında değişken. Bu işlev, geçerli Azure abonelik kaydeder (ile alınan `Get-AzureSubscription -Current`) ve depolama hesabı ve bu komut dosyası tarafından değiştirildiğinde abonelik (değişkeninde depolanan `$UserSpecifiedSubscription`) ve betik kapsamında, depolama hesabı. Değerleri kaydederek, bir işlev gibi kullanabileceğiniz `Restore-Subscription`, özgün geçerli abonelik ve depolama hesabı, geçerli durumu değiştiyse, geçerli durumuna geri yüklemek için. |
| Find-AzureVM |Belirtilen Azure sanal makine alır. |
| Format-DevTestMessageWithTime |Tarih ve saat için bir ileti ekler. Bu işlev, hata ve ayrıntı akışlara yazılan iletileri için tasarlanmıştır. |
| Get-AzureSQLDatabaseConnectionString |Bir Azure SQL veritabanına bağlanmak için bir bağlantı dizesi birleştirir. |
| Get-AzureVMStorage |Ad deseni ile ilk depolama hesabı adını döndürür "devtest *" (büyük/küçük harfe duyarlı değildir) belirtilen konumda veya benzeşim grubu. Varsa "devtest*" depolama hesabı konumu veya benzeşim grubunda eşleşmiyor, işlev yok sayar. Bir konum veya benzeşim grubu belirtin. |
| Get-MSDeployCmd |MsDeploy.exe aracı çalıştırmak için bir komut verir. |
| New-AzureVMEnvironment |Bulur veya JSON yapılandırma dosyasına değerleri eşleşen Abonelikteki bir sanal makine oluşturur. |
| Publish-WebPackage |MsDeploy.exe kullanır ve bir web paket yayımlama. Kaynakları bir Web sitesine dağıtmak için zip dosyası. Bu işlev, herhangi bir çıktı üretmez. MSDeploy.exe çağrı başarısız olursa, işlev bir özel durum oluşturur. Daha ayrıntılı çıktısını almak için kullanmak **-Verbose** seçeneği. |
| Publish-WebPackageToVM |Parametre değerlerini doğrular ve ardından çağırır **Publish-WebPackage** işlevi. |
| Read-ConfigFile |JSON yapılandırma dosyası doğrular ve seçilen değerlerin bir karma tablo döndürür. |
| Abonelik geri yükleme |Geçerli abonelik için özgün abonelik sıfırlar. |
| Test-AzureModule |Döndürür `$true` yüklü Azure modülü sürüm 0.7.4 ise veya üzeri. Döndürür `$false` Modülü yüklü değil veya önceki bir sürümdür. Bu işlev, hiç parametre yok. |
| Test-AzureModuleVersion |Döndürür `$true` Azure modülünün sürümünü 0.7.4 ise veya üzeri. Döndürür `$false` Modülü yüklü değil veya önceki bir sürümdür. Bu işlev, hiç parametre yok. |
| Test-HttpsUrl |Giriş URL'SİNİN bir System.Uri nesnesi için dönüştürür. Döndürür `$True` URL mutlak ve kendi şeması https ise. Döndürür `$false` URL görelidir kendi şeması HTTPS değil veya Giriş dizesinin bir URL'ye dönüştürülemez. |
| Test-üyesi |Döndürür `$true` bir özellik veya yöntem nesnenin bir üyesi ise. Aksi halde döndürür `$false`. |
| Yazma ErrorWithTime |Geçerli saati ile önek olarak kullanılan bir hata iletisi yazar. Bu işlev çağrıları **biçimi DevTestMessageWithTime** işlevini ileti hata akışına yazmadan önce zaman önüne ekleyin. |
| Yazma HostWithTime |Ana program için bir ileti yazar (**Write-Host**) geçerli saati ile önek. Ana program yazmanın etkin olarak değişir. Çoğu program barındıran Windows PowerShell için standart çıktı bu iletileri yazın. |
| Yazma VerboseWithTime |Geçerli saati ile önek ayrıntılı bir ileti yazar. Çağırır çünkü **Write-Verbose**, iletisini görüntüler yalnızca betik ile çalıştığında **ayrıntılı** parametresi veya **VerbosePreference** tercih içinayarlayın **Devam**. |

**Yayımlama-WebApplication**

| İşlev adı | Açıklama |
| --- | --- |
| Yeni AzureWebApplicationEnvironment |Bir Web sitesi ya da sanal makineyi gibi Azure kaynakları oluşturur. |
| Yeni WebDeployPackage |Bu işlev uygulanmadı. Projenizi yapılandırmak için bu işlevde harcanan komutlar ekleyebilirsiniz. |
| Publish-AzureWebApplication |Bir web uygulamasını azure'da yayımlar. |
| Yayımlama-WebApplication |Oluşturur ve Web uygulamaları, sanal makineler, SQL veritabanları ve depolama hesapları için bir Visual Studio web projesini dağıtır. |
| Test-WebApplication |Bu işlev uygulanmadı. Uygulamanızı test etmek için bu işlevde harcanan komutlar ekleyebilirsiniz. |

## <a name="next-steps"></a>Sonraki adımlar
PowerShell okuyarak komut dosyası oluşturma hakkında daha fazla bilgi [Windows PowerShell ile betik oluşturma](https://technet.microsoft.com/library/bb978526.aspx) ve diğer Azure PowerShell betikleri, [betik Merkezi](https://azure.microsoft.com/documentation/scripts/).
