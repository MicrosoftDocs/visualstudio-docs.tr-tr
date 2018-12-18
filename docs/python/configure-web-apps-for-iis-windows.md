---
title: IIS için Python web uygulamalarını yapılandırma
description: Internet Information Services ile bir Windows sanal makinesinden çalıştırmak için Python web uygulamaları nasıl yapılandıracağınızı öğrenmek.
ms.date: 12/06/2018
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
ms.openlocfilehash: 8de69c64cac5c841867f5d993395e5ab380625eb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062910"
---
# <a name="configure-python-web-apps-for-iis"></a>IIS için Python web uygulamalarını yapılandırma

Bir web sunucusu bir Windows bilgisayarda Internet Information Services (IIS) kullanırken (dahil olmak üzere [azure'da Windows sanal makineleri](/azure/architecture/reference-architectures/n-tier/windows-vm), Python uygulamaları, belirli ayarları içermelidir, *web.config* IIS'nin düzgün Python kodu işleyebilmek için dosyalar. Bilgisayar da Python web uygulamasının herhangi bir paket ile birlikte yüklü olması gerekir.

> [!Note]
> Bu makalede daha önce Windows üzerinde Azure App Service'te Python yapılandırmaya yönelik yönergeler içeriyor. Python uzantıları ve bu senaryoda kullanılan Windows ana bilgisayarları, Linux üzerinde Azure App Service ile değiştiriliyor bırakılmıştır. Daha fazla bilgi için [(Linux) Azure App Service'e yayımlama Python uygulamaları](publishing-python-web-applications-to-azure-from-visual-studio.md). Önceki makalede ancak hala kullanılabilir [Python uzantıları ile Windows üzerinde App Service'ı yönetme](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Windows üzerinde Python'ı yükleyin

Bir web uygulamasını çalıştırmak için önce gerekli Python sürümünüz doğrudan Windows ana makinede üzerinde açıklandığı gibi yüklemeniz [yüklemeniz Python yorumlayıcılarını](installing-python-interpreters.md).

Kayıt konumunu `python.exe` yorumlayıcı sonraki adımlar için. Kolaylık olması için bu konuma PATH ortam değişkeninize ekleyebilirsiniz.

## <a name="install-packages"></a>Paketleri yükleme

Ayrılmış bir konak kullanırken, bir sanal ortam yerine uygulamanızı çalıştırmak için global Python ortamı kullanabilirsiniz. Buna uygun olarak, tüm uygulamanızın gereksinimlerini genel ortamına yalnızca çalıştırarak yükleyebilirsiniz `pip install -r requirements.txt` bir komut isteminde.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Web.config Python yorumlayıcınıza işaret edecek şekilde ayarlayın

Uygulamanızın *web.config* dosya nasıl, Fastcgı ya da HttpPlatform Python istekleri işleyeceğini hakkında Windows üzerinde çalışan (7 +) IIS web sunucusuna bildirir. Visual Studio 2017'yi kullanarak, değiştirmelisiniz *web.config* el ile. Bir sonraki bölümde açıklandığı gibi Visual Studio 2015 değişiklikler yapar.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyiciyi yapılandırmanız

HttpPlatform modülü soket bağlantılarının doğrudan tek başına Python işlem geçirir. Bu geçiş, gibi ancak bir yerel web sunucusu çalıştıran bir başlangıç betiği gerektiren herhangi bir web sunucusu çalıştırmanızı sağlar. Betikte belirttiğiniz `<httpPlatform>` öğesinin *web.config*burada `processPath` özniteliği işaret site uzantının Python yorumlayıcısı ve `arguments` özniteliği işaret betiğinizi ve herhangi bir bağımsız değişken için sağlamak istiyorsanız:

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

`HTTP_PLATFORM_PORT` Burada gösterilen ortam değişkeni, yerel sunucu, localhost bağlantılarından dinleyecek bağlantı noktasını içerir. Bu örnek ayrıca istenirse, bu durumda, başka bir ortam değişkeni oluşturma işlemini gösterir `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Fastcgı işleyici yapılandırın

Fastcgı talep düzeyinde çalışır bir arabirimdir. IIS gelen bağlantıları alır ve her birinde çalışan bir WSGI uygulama isteğini iletir ya da daha kalıcı bir Python işler.

Bunu kullanmak için ilk yükleme ve wfastcgı paketi üzerinde açıklandığı gibi yapılandırın [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Ardından, uygulamanızın değiştirme *web.config* dosyanın tam yollarını içerecek şekilde *python.exe* ve *wfastcgi.py* içinde `PythonHandler` anahtarı. Aşağıdaki adımlarda, Python yüklenir varsayılır *c:\python36-32* ve uygulama kodunuzun olan *c:\home\site\wwwroot*; cihazınızdaki yollar için uygun şekilde ayarlayın:

1. Değiştirme `PythonHandler` girişi *web.config* Python yükleme konumu yolu eşleşmesi (bkz [IIS yapılandırma başvurusu](https://www.iis.net/configreference) (IIS.NET) hakkında tam Ayrıntılar için).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. İçinde `<appSettings>` bölümünü *web.config*, anahtarları Ekle `WSGI_HANDLER`, `WSGI_LOG` (isteğe bağlı) ve `PYTHONPATH`:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Bunlar `<appSettings>` değerler uygulamanıza kullanılabilir ortam değişkenleri olarak:

    - Değeri `PYTHONPATH` genişletilmiş serbestçe ancak uygulamanızın kök içermelidir.
    - `WSGI_HANDLER` bir WSGI uygulaması alınabilir, uygulamanızdan işaret etmelidir.
    - `WSGI_LOG` İsteğe bağlı ancak uygulamanızın hatalarını ayıklamak için önerilen değerdir.

1. Ayarlama `WSGI_HANDLER` girişi *web.config* framework için uygun şekilde kullanmakta olduğunuz:

    - **Bottle**: sonra parantez sahip olduğunuzdan emin olun `app.wsgi_app` aşağıda gösterildiği gibi. Bir işlev, nesne olduğu için bu gereklidir (bkz *app.py*) bir değişken yerine:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: değişiklik `WSGI_HANDLER` değerini `<project_name>.app` burada `<project_name>` projenizin adıyla aynıdır. Bakarak tam tanımlayıcısını bulabilirsiniz `from <project_name> import app` deyiminde *runserver.py*. Örneğin, proje "FlaskAzurePublishExample" ise, giriş şu şekilde görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: iki değişiklik için gereken *web.config* Django projeler için. İlk olarak değiştirmek `WSGI_HANDLER` değerini `django.core.wsgi.get_wsgi_application()` (nesne *wsgi.py* dosyası):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, için aşağıda şu girişi ekleyin `WSGI_HANDLER`, değiştirmeyi `DjangoAzurePublishExample` projenizin adı:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Yalnızca Django uygulamaları**: içinde Django projesinin *settings.py* site URL'si, etki alanı ya da IP adresi ekleyin `ALLOWED_HOSTS` aşağıda gösterildiği gibi '1.2.3.4' URL veya IP adresi ile doğal değiştirme:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Hatalı dizi sonuçlarını URL'nizi ekleme hatası **DisallowedHost / geçersiz HTTP_HOST başlığı: '\<site URL'si\>'. Eklemeniz gerekebilir '\<site URL'si\>' ALLOWED_HOSTS için.**

    Boş bir dizidir, Django 'localhost' ve '127.0.0.1' otomatik olarak tanır, ancak bu özellikler, üretim URL'si ekleme kaldırır unutmayın. Bu nedenle ayrı geliştirme ve üretim korumak isteyebilirsiniz, kopyalar için *settings.py*, veya çalışma zamanı değerlerini denetlemek için ortam değişkenlerini kullanın.

## <a name="deploy-to-iis-or-a-windows-vm"></a>IIS veya bir Windows VM dağıtın

Doğru ile *web.config* dosyasını kullanarak IIS çalıştıran bilgisayara yayımlayabilirsiniz projenizde, **Yayımla** projenin bağlam menüsünden komutunu **ÇözümGezgini**ve seçeneğini belirleyerek **IIS, FTP, vb.**. Bu durumda, Visual Studio sunucusuna yalnızca proje dosyalarını kopyalar; Tüm sunucu tarafı yapılandırması için sorumlu olursunuz.
