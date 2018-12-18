---
title: Python için Azure bulut hizmeti projesi şablonu
description: Visual Studio, Azure cloud services rol dağıtımı, bağımlılıkları, dahil etme ve sorun giderme Python'da yazılmış için şablonlar sağlar.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 5eafbf0b24e464e81447c0677d53096032343580
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068532"
---
# <a name="azure-cloud-service-projects-for-python"></a>Python için Azure bulut hizmeti projeleri

Visual Studio, Python kullanarak Azure bulut hizmetleri oluşturmaya yardımcı olması için şablonlar başlama sağlar.

A [bulut hizmeti](https://docs.microsoft.com/azure/cloud-services/) oluşur herhangi bir sayıda *çalışan rolleri* ve *web rolleri*, her biri kavramsal olarak ayrı bir görev gerçekleştiren ancak için ayrı olarak çoğaltılabilir arasında ölçeklendirme için gerektiği şekilde sanal makineler. Web rolleri için ön uç web uygulamalarını barındırmak sağlar. Bu tür bir uygulama yazmak için Python ilgili olduğu WSGI destekleyen herhangi bir web çerçevesi kullanılabilir (tarafından desteklenen [Web projesi şablonu](python-web-application-project-templates.md)). Çalışan rolleri, doğrudan kullanıcılar ile etkileşimde uzun süre çalışan işlemler için tasarlanmıştır. Bunlar genellikle olun ile birlikte yüklenir "azure" paketin içindeki paketleri kullanımı [ `pip install azure` ](https://pypi.org/project/azure).

Bu makalede proje şablonu ve diğer destek (önceki sürümlerinde benzer, ancak bazı farklılıklar) Visual Studio 2017'de ilgili ayrıntıları içerir. Python'dan Azure ile çalışma hakkında daha fazla bilgi için ziyaret [Azure Python Geliştirici Merkezi](https://docs.microsoft.com/python/azure/?view=azure-python).

## <a name="create-a-project"></a>Proje oluşturma

1. Yükleme [Visual Studio için Azure .NET SDK'sı](https://visualstudio.microsoft.com/vs/azure-tools/), bulut hizmeti şablonu kullanmak için gereklidir.
1. Visual Studio'da **dosya** > **yeni** > **proje**seçin ve ardından "Azure Python" için arama **Azure bulut Hizmet** listesinden:

    ![Python için Azure bulut projesi şablonu](media/template-azure-cloud-project.png)

1. Eklenecek bir veya daha fazla rol seçin. Bulut projeleri en uygun dilde kolayca uygulamanızı her bir parçasının yazabilmesi farklı dillerde yazılmış rollerini birleştirmeniz. Bu iletişim kutusunu tamamladıktan sonra yeni rolleri projeye eklemek için sağ **rolleri** içinde **Çözüm Gezgini** ve altındaki öğeleri seçin **Ekle**.

    ![Azure bulut proje şablonunda rol ekleme](media/template-azure-cloud-service-project-wizard.png)

1. Tek tek rol projeleri oluşturulduğunda bunlardan birini kullanan bir rolü seçtiyseniz, Django, Bottle veya Flask çerçeveleri gibi ek Python paketlerini yüklemek için istenebilir.

1. Yeni bir rol projenize ekledikten sonra yapılandırma yönergeleri görünür. Yapılandırma değişiklikleri genellikle gereksizdir, ancak gelecekte projelerinizi özelleştirme için yararlı olabilir. Aynı anda birden çok rol eklerken, yalnızca son rolü yönergeleri açık kalmasını unutmayın. Diğer roller için kendi ilgili yönergeler ve sorun giderme ipuçları ancak bulabilirsiniz *readme.mht* rolün kök veya bulunan dosyaları *bin* klasör.

1. Bir projenin *bin* klasör da Python, tüm yükleme dahil olmak üzere uzaktan sanal makineyi yapılandırmak için kullanılan bir veya iki PowerShell betikleri içerir [ *requirements.txt* ](#dependencies) dosya projenizde ve gerekirse IIS ayarı. En yaygın seçenekler başka yöntemlerle de yönetilebilir, ancak dağıtımınız için bu dosyaları istediğiniz gibi düzenleyebilirsiniz (bkz [rol dağıtımı yapılandırma](#configure-role-deployment) aşağıda). Eski yapılandırma betiğini dosyaları kullanılabilir durumda değilse, bunun yerine kullanıldığı gibi bu dosyaları kaldırma öneririz değil.

    ![Çalışan rolü destek dosyaları](media/template-azure-cloud-service-worker-role-support-files.png)

    Bu yapılandırma betiklerini yeni bir projeye eklemek için projeye sağ tıklayın, **Ekle** > **yeni öğe**, ya da seçin **Web rolü destek dosyalarını** veya **Çalışan rolü destek dosyalarını**.

## <a name="configure-role-deployment"></a>Rol dağıtımı yapılandırma

PowerShell betikleri rol projenin *bin* klasörü bu role dağıtımını kontrol ve yapılandırmasını özelleştirmek için düzenlenebilir:

- *ConfigureCloudService.ps1* web ve çalışan rolleri için genellikle yükleyin ve Python sürümünü ayarlama bağımlılıkları yapılandırmak için kullanılır.
- *Launchworker.ps1'i* yalnızca çalışan rolleri için kullanılır ve başlangıç davranışını değiştirmek, komut satırı bağımsız değişkenlerini ekleyin veya ortam değişkenleri eklemek için kullanılır.

Her iki dosya özelleştirme için yönergeler içerir. Temel bulut hizmeti proje için başka bir görev ekleyerek kendi Python sürümünü yükleyebilirsiniz *ServiceDefinition.csdef* ayarı dosyası `PYTHON` değişkenini kendi yüklü *python.exe*(veya eşdeğer) yolu. Zaman `PYTHON` olan ayarlayın, Python Nuget'ten yüklü değil.

Ek yapılandırma şu şekilde gerçekleştirilebilir:

1. Kullanarak paketleri yüklemeniz `pip` güncelleştirerek *requirements.txt* projenizin kök dizindeki dosya. *ConfigureCloudService.ps1* betik dağıtımı bu dosyayı yükler.
1. Ortam değişkenlerini ayarlama değiştirerek, *web.config* dosyası (web rolleri) veya `Runtime` bölümünü, *ServiceDefinition.csdef* dosyası (çalışan rolleri).
1. Komut ve komut satırında değiştirerek bir çalışan rolü için kullanılacak değişkenleri belirtin `Runtime/EntryPoint` bölümünü, *ServiceDefinitions.csdef* dosya.
1. Ana işleyicisi komut dosyası bir web rolü için *web.config* dosya.

## <a name="test-role-deployment"></a>Rol dağıtımı test etme

Rollerinizi yazılırken, bulut hizmeti öykünücüsü kullanarak yerel olarak bulut projenizi test edebilirsiniz. Öykünücü ile Azure SDK Tools dahil edilmiştir ve Azure'a, bulut hizmetinizin yayımlandığında kullanılan ortam sınırlı bir sürümüdür.

Öykünücü başlatmak için önce bulut projenizi olduğundan çözümünüzdeki başlangıç projesine sağ tıklatıp seçerek olun **başlangıç projesi olarak ayarla**. Ardından **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **hata ayıklama** > **olmadan Başlat Hata ayıklama** (**Ctrl**+**F5**).

Öykünücü sınırlamaları nedeniyle bu, Python kodunda hata ayıklama mümkün olmadığını unutmayın. Bu nedenle önerilir debug rolleri bağımsız olarak çalıştırarak ve daha sonra öykünücü yayımlanmadan önce test tümleştirmesi için.

## <a name="deploy-a-role"></a>Bir rol dağıtın

Açmak için **Yayımla** rolü projesi Sihirbazı'nı seçin **Çözüm Gezgini** seçip **derleme** > **Yayımla** gelen ana menü veya projeye sağ tıklayıp seçin **Yayımla**.

Yayımlama işlemi iki aşama gerektirir. İlk olarak, Visual Studio bulut hizmetiniz için tüm rolleri içeren tek bir paket oluşturur. Bu, her rol için bir veya daha fazla sanal makine başlatır ve kaynak dağıtır Azure'a dağıtılan bir pakettir.

Her sanal makineyi etkinleştirir olarak yürütülmeden *ConfigureCloudService.ps1* betik ve tüm bağımlılıklarını yükler. Varsayılan olarak bu betik Python'dan en güncel sürümünü yükler [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) ve belirtilen herhangi bir paket bir *requirements.txt* dosya.

Son olarak, çalışan rolleri yürütme *Launchworker.ps1'i*, başladığı Python betiğinizi çalıştırmak; rolleri başlatma IIS web ve web isteklerini işleme başlayın.

## <a name="dependencies"></a>Bağımlılıkları

Cloud Services *ConfigureCloudService.ps1* betik `pip` Python bağımlılıklar kümesini yüklemek için. Bağımlılıklar adlı bir dosyaya belirtilmelidir *requirements.txt* (değiştirerek özelleştirilebilir *ConfigureCloudService.ps1*). Dosya ile yürütülür `pip install -r requirements.txt` başlatmanın parçası.

Önceden derlenmiş ikili dosyaları C uzantıları ile tüm kitaplıkları sağlamalısınız bulut hizmeti örnekleri C derleyiciler içermez unutmayın.

pip ve bağımlılıklarını yanı sıra, paketleri *requirements.txt*, otomatik olarak yüklenir ve ücrete tabi bant genişliği kullanımı say. Bkz: [gerekli paketleri yönetme](managing-required-packages-with-requirements-txt.md) yönetme ile ilgili ayrıntılar için *requirements.txt* dosyaları.

## <a name="troubleshooting"></a>Sorun giderme

Dağıtımdan sonra web veya çalışan rolü doğru şekilde davranmaz, aşağıdakileri denetleyin:

- Python projenizi içeren bir *bin\\*  klasörle (en az):

  - *ConfigureCloudService.ps1*
  - *Launchworker.ps1'i* (çalışan rolleri için)
  - *PS.cmd*

- Python projenizi içeren bir *requirements.txt* tüm bağımlılıkları (veya alternatif olarak, bir tekerlek dosyaları koleksiyonunu) listeleme dosyası.
- Bulut hizmetinizde uzak masaüstünü etkinleştirme ve günlük dosyalarını inceleyin.
- Günlüklerinde *ConfigureCloudService.ps1* ve *Launchworker.ps1'i* depolanır *C:\Resources\Directory\%Roleıd %. DiagnosticStore\LogFiles* uzak bilgisayardaki klasör.
- Web rolleri yazma ek günlükler yapılandırılmış bir yola *web.config*, yani yolunda `WSGI_LOG` appSetting. Çoğu normal IIS veya Fastcgı günlüğünü de çalışır.
- Şu anda *LaunchWorker.ps1.log* çıkış veya Python çalışanı rolünüz tarafından görüntülenen hataları görüntülemek için tek yolu bir dosyadır.
