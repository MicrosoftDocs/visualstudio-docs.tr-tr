---
title: IIS için Python Web Apps 'i yapılandırma
description: Python web uygulamalarını bir Windows sanal makinesinden Internet Information Services çalışacak şekilde yapılandırma.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 40411f47e7deda48b04ac4efb9bb9bc18688989a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839116"
---
# <a name="configure-python-web-apps-for-iis"></a>IIS için Python Web Apps 'i yapılandırma

Windows bilgisayarda Internet Information Services (IIS) Web sunucusu olarak kullanırken ( [Azure 'Daki Windows sanal makineler](/azure/architecture/reference-architectures/n-tier/windows-vm)dahil), Python uygulamaları IIS 'nin Python kodunu düzgün bir şekilde işleyebilmesi için *web.config* dosyalarında belirli ayarları içermesi gerekir. Bilgisayarın kendisi de, Web uygulamasının gerektirdiği tüm paketlerle birlikte Python 'un yüklü olması gerekir.

> [!Note]
> Bu makale daha önce Windows üzerinde Azure App Service Python yapılandırma kılavuzunu içeriyordu. Bu senaryoda kullanılan Python uzantıları ve Windows Konakları, Linux üzerinde Azure App Service kullanım dışı bırakılmıştır. Daha fazla bilgi için bkz. [Python uygulamalarını Azure App Service (Linux) Ile yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md). Ancak önceki makale, [Python uzantılarıyla Windows üzerinde App Service yönetirken](managing-python-on-azure-app-service.md)hala kullanılabilir.

## <a name="install-python-on-windows"></a>Windows üzerinde Python’ı yükleme

Bir Web uygulamasını çalıştırmak için, Python [yorumlayıcıları](installing-python-interpreters.md)'nı oluşturma bölümünde açıklandığı gibi, önce gerekli Python sürümünüzü doğrudan Windows ana makinesine yüklemeniz gerekir.

`python.exe`Sonraki adımlar için yorumlayıcı konumunu kaydedin. Kolaylık olması için, bu konumu PATH ortam değişkeniniz için ekleyebilirsiniz.

## <a name="install-packages"></a>Paketleri yükler

Adanmış bir konak kullanırken, uygulamanızı sanal bir ortam yerine çalıştırmak için genel Python ortamını kullanabilirsiniz. Buna uygun olarak, bir komut isteminde çalıştırarak uygulamanızın tüm gereksinimlerini genel ortama yükleyebilirsiniz `pip install -r requirements.txt` .

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>web.config Python yorumlayıcıya işaret etmek için ayarla

Uygulamanızın *web.config* dosyası, Windows ÜZERINDE çalışan IIS (7 +) Web sunucusuna httpplatform (önerilen) veya FastCGI aracılığıyla Python isteklerini nasıl işleyeceğinizi bildirir. Visual Studio sürümleri 2015 ve öncesi, bu değişiklikleri otomatik olarak yapar. Visual Studio 2017 ve üstünü kullanırken *web.config* el ile değiştirmeniz gerekir.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü, yuva bağlantılarını doğrudan bir tek başına Python işlemine geçirir. Bu geçiş, istediğiniz herhangi bir Web sunucusunu çalıştırmanıza izin verir, ancak yerel bir Web sunucusu çalıştıran bir başlatma betiği gerektirir. Komut dosyasını `<httpPlatform>` *web.config* öğesinde belirtirsiniz; burada `processPath` öznitelik, site uzantısının Python yorumlayıcısını ve `arguments` özniteliği, betiğinizi ve sağlamak istediğiniz bağımsız değişkeni gösterir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

`HTTP_PLATFORM_PORT`Burada gösterilen ortam değişkeni, yerel sunucunuzun localhost bağlantıları için dinlemesi gereken bağlantı noktasını içerir. Bu örnek ayrıca, isterseniz başka bir ortam değişkeninin nasıl oluşturulacağını gösterir `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>FastCGI işleyicisini yapılandırma

FastCGI, istek düzeyinde çalışacak bir arabirimdir. IIS, gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemde çalışan bir WSGI uygulamasına iletir.

Bunu kullanmak için, önce [pypi.org/Project/wfastcgi/](https://pypi.io/project/wfastcgi)sitesinde açıklandığı gibi wfastcgı paketini yükleyip yapılandırın.

Daha sonra, *python.exe* ve *wfastcgi.py* için tam yolları içerecek şekilde uygulamanızın *web.config* dosyasını değiştirin `PythonHandler` . Aşağıdaki adımlar, Python 'un *c:\python36-32* 'e yüklendiğini ve uygulama kodunuzun *c:\home\site\wwwroot*; yolunda olduğunu varsayar. yollarınız için uygun şekilde ayarlayın:

1. `PythonHandler` *web.config* girişi, yol Python yüklemesi konumuyla eşleşecek şekilde değiştirin (tam Ayrıntılar Için bkz. [ııs yapılandırma başvurusu](https://www.iis.net/configreference) (iis.net)).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. `<appSettings>` *web.config* bölümünde, için anahtarlar ekleyin `WSGI_HANDLER` `WSGI_LOG` (isteğe bağlı) ve `PYTHONPATH` :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Bu `<appSettings>` değerler, uygulamanız için ortam değişkenleri olarak kullanılabilir:

    - Değeri, `PYTHONPATH` ücretsiz olarak genişletilebilir, ancak uygulamanızın kökünü içermelidir.
    - `WSGI_HANDLER` uygulamanızdan bir WSGI uygulaması Importable öğesine işaret etmelidir.
    - `WSGI_LOG` isteğe bağlıdır, ancak uygulamanızda hata ayıklama için önerilir.

1. `WSGI_HANDLER` *web.config* girişi, kullanmakta olduğunuz çerçeveye uygun şekilde ayarlayın:

    - **Şişe**: aşağıda gösterildiği gibi parantezleri yazdığınızdan emin olun `app.wsgi_app` . Bu, nesne bir işlev olduğu için (bkz. *app.py*) bir değişken değil, bu gereklidir:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: değeri, `WSGI_HANDLER` `<project_name>.app` `<project_name>` projenizin adıyla eşleşen olacak şekilde değiştirin. `from <project_name> import app` *Runserver.py* içindeki ifadeye bakarak tam tanımlayıcıyı bulabilirsiniz. Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılmışsa, giriş şu şekilde görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Docgo**: docgo projeleri için *web.config* için iki değişiklik yapılması gerekir. İlk olarak, `WSGI_HANDLER` değeri olarak değiştirin `django.core.wsgi.get_wsgi_application()` (nesne *wsgi.py* dosyasında bulunur):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, öğesinin altına aşağıdaki girişi ekleyin, bunu `WSGI_HANDLER` `DjangoAzurePublishExample` projenizin adıyla değiştirin:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Yalnızca docgo uygulamaları**: docgo projesinin *Settings.py* dosyasında, SITE URL 'sini veya IP adresini `ALLOWED_HOSTS` aşağıda gösterildiği gibi ekleyin ve ' 1.2.3.4 ' i, URL 'niz veya IP adresiniz ile değiştirin:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    URL 'niz diziye eklenemedi **' ' HTTP_HOST üst bilgisindeki/geçersiz hata ile başarısız oldu: ' \<site URL\> '. \<site URL\>ALLOWED_HOSTS için ' ' eklemeniz gerekebilir.**

    Dizi boş olduğunda, Docgo 'nun otomatik olarak ' localhost ' ve ' 127.0.0.1 ' olarak izin verdiğini, ancak üretim URL 'nizi eklemenin bu özellikleri kaldırdığına bakın. Bu nedenle, *Settings.py*'in ayrı geliştirme ve üretim kopyalarını sürdürmek veya çalışma süresi değerlerini denetlemek için ortam değişkenlerini kullanmak isteyebilirsiniz.

## <a name="deploy-to-iis-or-a-windows-vm"></a>IIS 'ye veya Windows VM 'ye dağıtma

Projenizdeki doğru *web.config* dosyası ile, **Çözüm Gezgini**, projenin bağlam menüsündeki **Yayımla** komutunu kullanarak ve IIS **, FTP, vb.** seçeneklerini belirleyerek IIS çalıştıran bilgisayara yayımlayabilirsiniz. Bu durumda, Visual Studio yalnızca proje dosyalarını sunucuya kopyalar; Tüm sunucu tarafı yapılandırmadan sorumlu olursunuz.
