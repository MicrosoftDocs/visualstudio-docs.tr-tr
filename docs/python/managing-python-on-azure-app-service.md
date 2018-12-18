---
title: (Windows) Azure App Service'te Python'u yapılandırma
description: Nasıl Azure App Service ve yapılandırma web uygulamaları için bu yorumlayıcı düzgün bir şekilde başvurmak için bir Python yorumlayıcısı ve kütüphaneler yükleyin.
ms.date: 10/18/2018
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
ms.openlocfilehash: e21be06c26ec6a15b46ef72c0fe33a35b314c989
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051299"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>(Windows) Azure App Service'te bir Python ortamını kurma

> [!Important]
> Microsoft kullanım dışı Python uzantıları için Windows üzerinde App Service'te doğrudan bir dağıtım için kullanıldığından bu makalede açıklanan şekilde [Linux üzerinde App Service'te](publishing-python-web-applications-to-azure-from-visual-studio.md).

[Azure App Service](https://azure.microsoft.com/services/app-service/) REST API'leri kullanarak kendi istemciler veya olayla tetiklenen işlem tarafından kullanılan bir tarayıcı aracılığıyla erişilen siteleri oldukları olup, hizmet olarak platform sunan web uygulamaları için. App Service uygulamaları uygulamak için Python'ı kullanarak tam olarak destekler.

Azure App Service için özelleştirilebilir Python desteği App Service bir dizi sağlanan *site uzantıları* her Python çalışma zamanını belirli bir sürümünü içerir. Bu makalede açıklandığı gibi bu ortama doğrudan ardından istenen herhangi bir paket yükleyebilirsiniz. App Service ortamında özelleştirerek, web uygulaması projelerinde paketler korumak veya uygulama kodu ile karşıya yüklemeniz gerekmez.

> [!Tip]
> App Service varsayılan olarak Python 2.7 ve Python 3.4: kök klasörleri sunucusuna yüklenmiş olsa da, özelleştirme veya bu ortamlarda paketleri yüklemek ya da kendi varlığını temel bağlı olmalıdır. Bunun yerine, bu makalede açıklandığı gibi sizin denetlediğiniz bir site uzantısı yararlanmalıdır.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Azure portalı üzerinden bir Python sürümünü seçin

1. Web uygulamanız için bir App Service, Azure portalda oluşturun.
1. App Service'nın sayfasında kaydırarak **geliştirme araçları** bölümünden **uzantıları**, ardından **+ Ekle**.
1. İstediğiniz Python sürümünü içeren bir uzantı listesinde aşağı kaydırın:

    ![Azure portal gösteren Python uzantıları](media/python-on-azure-extensions.png)

    > [!Tip]
    > Python daha eski bir sürümü gerekir ve site uzantıları listelendiği görmüyorsanız, yine de Azure Resource Manager üzerinden sonraki bölümde açıklandığı gibi yükleyebilirsiniz.

1. Uzantıyı seçin, yasal koşulları kabul edin ve ardından seçin **Tamam**.
1. Yükleme tamamlandığında, portalda bir bildirim görüntülenir.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Azure Resource Manager aracılığıyla bir Python sürümünü seçin

Bir App Service ile bir Azure Resource Manager şablonu dağıtıyorsanız, site uzantısı, kaynak olarak ekleyin. Özellikle, uzantı iç içe geçmiş bir kaynak olarak görünür (bir `resources` altında nesne `resources`) türüyle `siteextensions` ve adından [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Bir başvuru ekledikten sonra Örneğin `python361x64` (şablonunuz şöyle görünebileceğini Python 3.6.1 x 64), (ihmal bazı özellikler):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Web.config Python yorumlayıcınıza işaret edecek şekilde ayarlayın

Site uzantısı (aracılığıyla, portal veya Azure Resource Manager şablonu) yükledikten sonra sonraki uygulamanızın üzerine *web.config* Python yorumlayıcısının dosya. *Web.config* dosya nasıl, Fastcgı ya da HttpPlatform Python istekleri işleyeceğini hakkında App Service üzerinde çalışan (7 +) IIS web sunucusuna bildirir.

Başlamak site uzantının tam yolu bularak *python.exe*, ardından oluşturup uygun *web.config* dosya.

### <a name="find-the-path-to-pythonexe"></a>Python.exe yolunu bulun

Python site uzantısı altında sunucuda yüklü *d:\home* Python sürümü ve mimarisi için uygun bir klasörde (söz konusu olduğunda bazı eski sürümleri hariç). Örneğin, Python 3.6.1 x64 yüklenir *d:\home\python361x64*. Tam Python yorumlayıcısının yolu ise *d:\home\python361x64\python.exe*.

App Service'inizde belirli yolu görmek için seçin **uzantıları** App Service sayfasında, listeden sonra uzantıyı seçin.

![Azure App Service'te uzantı listesi](media/python-on-azure-extension-list.png)

Bu eylem yolunu içeren uzantının açıklama sayfasını açar:

![Azure App Service'te uzantı ayrıntıları](media/python-on-azure-extension-detail.png)

Yol uzantısı görmekte sorun varsa, el ile konsolunu kullanarak buna bulabilirsiniz:

1. App Service sayfanızda seçin **geliştirme araçları** > **konsol**.
1. Komutu girdikten `ls ../home` veya `dir ..\home` gibi üst düzey uzantıları klasörleri görmek için *Python361x64*.
1. Gibi bir komut girin `ls ../home/python361x64` veya `dir ..\home\python361x64` bunu içerdiğini doğrulamak için *python.exe* ve diğer yorumlayıcı dosyaları.

### <a name="configure-the-fastcgi-handler"></a>Fastcgı işleyici yapılandırın

Fastcgı talep düzeyinde çalışır bir arabirimdir. IIS gelen bağlantıları alır ve her birinde çalışan bir WSGI uygulama isteğini iletir ya da daha kalıcı bir Python işler. [Wfastcgı paket](https://pypi.io/project/wfastcgi) önceden yüklenmiş ve yapılandırılmış her Python site uzantısı ile kolayca kod ekleyerek etkinleştirebilirsiniz *web.config* ister temel bir web uygulaması için aşağıda gösterilen öğeleri Bottle çerçevesi. Unutmayın tam yolları *python.exe* ve *wfastcgi.py* yerleştirilir `PythonHandler` anahtarı:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` Burada bulunmaktadır uygulamanıza kullanılabilir ortam değişkenleri olarak tanımlanan:

- Değeri `PYTHONPATH` genişletilmiş serbestçe ancak uygulamanızın kök içermelidir.
- `WSGI_HANDLER` bir WSGI uygulaması alınabilir, uygulamanızdan işaret etmelidir.
- `WSGI_LOG` İsteğe bağlı ancak uygulamanızın hatalarını ayıklamak için önerilen değerdir. 

Bkz: [azure'a Yayımla](publishing-python-web-applications-to-azure-from-visual-studio.md) hakkında daha fazla ayrıntı için *web.config* içeriği Bottle, Flask ve Django web uygulamaları.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyiciyi yapılandırmanız

HttpPlatform modülü soket bağlantılarının doğrudan tek başına Python işlem geçirir. Bu geçiş, gibi ancak bir yerel web sunucusu çalıştıran bir başlangıç betiği gerektiren herhangi bir web sunucusu çalıştırmanızı sağlar. Betikte belirttiğiniz `<httpPlatform>` öğesinin *web.config*burada `processPath` özniteliği işaret site uzantının Python yorumlayıcısı ve `arguments` özniteliği işaret betiğinizi ve herhangi bir bağımsız değişken için sağlamak istiyorsanız:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

`HTTP_PLATFORM_PORT` Burada gösterilen ortam değişkeni, yerel sunucu, localhost bağlantılarından dinleyecek bağlantı noktasını içerir. Bu örnek ayrıca istenirse, bu durumda, başka bir ortam değişkeni oluşturma işlemini gösterir `SERVER_PORT`.

## <a name="install-packages"></a>Paketleri yükleme

Yüklü bir site uzantısı aracılığıyla Python yorumlayıcısı Python ortamınızı yalnızca bir parçasıdır. Büyük olasılıkla, o ortamda farklı paketleri yüklemeniz gerekir.

Paketler, doğrudan sunucu ortamında yüklemek için aşağıdaki yöntemlerden birini kullanın:

| Yöntemler | Kullanım |
| --- | --- |
| [Azure App Service Kudu Konsolu](#azure-app-service-kudu-console) | Etkileşimli olarak paketleri yükler. Paketleri saf Python olmalıdır veya tekerlekleri yayımlamanız gerekir. |
| [Kudu REST API](#kudu-rest-api) | Paket yüklemesi otomatikleştirmek için kullanılabilir.  Paketleri saf Python olmalıdır veya tekerlekleri yayımlamanız gerekir. |
| Uygulama ile paket | Projenize doğrudan paketleri yüklemek ve uygulamanızın bir parçası değilmiş gibi bunları App Service'e dağıtırsınız. Bağımlılık bağlı olarak sahip olduğunuz ve ne sıklıkta bunları güncelleştirin, bu yöntem giderek bir çalışma dağıtım en kolay yolu olabilir. Olun kitaplıkları sunucuda Python sürümü ile eşleşmesi gerekir, aksi takdirde belirsiz dağıtımdan sonra görüyorsunuz. Site uzantıları tam olarak üzerinde python.org yayımlanan bu sürümler aynıdır App Service'te Python sürümleri, yerel geliştirme için uyumlu bir sürümünü kolayca edinebileceği olduğundan, Bununla birlikte. |
| Sanal ortamlar | Desteklenmez. Bunun yerine, paketleme kullanmak ve ayarlamak `PYTHONPATH` paket konumunu gösterecek şekilde ortam değişkeni. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service Kudu Konsolu

[Kudu konsolunu](https://github.com/projectkudu/kudu/wiki/Kudu-console) uygulama hizmeti sunucusunun ve dosya sistemi doğrudan, yükseltilmiş bir komut satırı erişimi sağlar. Bu, hem bir değerli hata ayıklama aracıdır ve paketlerin yüklenmesi gibi CLI işlemleri sağlar.

1. Açık Kudu Azure portalında App Service sayfanızdan seçerek **geliştirme araçları** > **Gelişmiş Araçlar**, ardından seçerek **Git**. Temel uygulama hizmeti URL'NİZLE dışında aynı olan bir URL bu eylemin gittiği `.scm` eklenir. Örneğin, temel URL'niz `https://vspython-test.azurewebsites.net/` Kudu üzerinde ise `https://vspython-test.scm.azurewebsites.net/` (Bu, yer işareti ekleyebilirsiniz):

    ![Azure App Service için Kudu Konsolu](media/python-on-azure-console01.png)

1. Seçin **hata ayıklama konsoluna** > **CMD** Python yüklemenizi gidin ve ne kitaplıkları zaten var olup konsolunu açın.

1. Tek bir paket yüklemek için:

    a. Paket gibi yüklemek istediğiniz klasöre Python yükleme gidin *d:\home\python361x64*.

    b. Kullanım `python.exe -m pip install <package_name>` paket yükleme.

    ![Azure App Service için Kudu Konsolu aracılığıyla bottle yükleme örneği](media/python-on-azure-console02.png)

1. Dağıttıysanız, bir *requirements.txt* sunucuya uygulamanız için zaten bu gereksinimleri aşağıda gösterildiği gibi yükleyin:

    a. Paket gibi yüklemek istediğiniz klasöre Python yükleme gidin *d:\home\python361x64*.

    b. Komutunu çalıştırın `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Kullanarak *requirements.txt* tam paketinizi ayarlayın, her ikisi de, yerel olarak hem de sunucu yeniden oluşturulması kolay olduğu için önerilir. Konsolunda herhangi bir değişiklik dağıttıktan sonra ziyaret hatırlamak *requirements.txt* ve komutu yeniden çalıştırın.

> [!Note]
> Yoktur C Derleyici App Service, tüm paketler için tekerlek yerel uzantı modüllerini ile yüklemeniz gerekir. Birçok popüler paketleri kendi tekerlekleri sağlar. Olmayan paketleri kullanmak `pip wheel <package_name>` yerel geliştirme bilgisayarınıza ve sitenizde tekerleği yüklersiniz. Bir örnek için bkz. [requirements.txt ile gerekli paketleri yönetme](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Kudu konsolunu Azure portalı üzerinden kullanmak yerine, komutları uzaktan Kudu REST API aracılığıyla komutu göndererek çalıştırabilirsiniz `https://yoursite.scm.azurewebsites.net/api/command`. Örneğin, yükleme için `bottle` paket, aşağıdaki JSON sonrası `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Komutlar ve kimlik doğrulaması hakkında daha fazla bilgi için bkz. [Kudu belgeleri](https://github.com/projectkudu/kudu/wiki/REST-API).

Kimlik bilgilerini kullanarak atabilirsiniz `az webapp deployment list-publishing-profiles` aracılığıyla Azure CLI komutunu (bkz [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Kudu komutları gönderme için bir yardımcı kitaplık kullanılabilir [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
