---
title: Python Web uygulaması şablonları
description: Visual Studio, Bottle, Flask ve Django çerçeveleri kullanarak Python web uygulamaları için şablonlar sağlar. hata ayıklama yapılandırmaları ve Azure App Service'te yayımlama desteği içerir.
ms.date: 10/29/2018
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
ms.openlocfilehash: 06513030b34f7ab3217210a931722d72a6368ab3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068334"
---
# <a name="python-web-application-project-templates"></a>Python web uygulaması proje şablonları

Visual Studio'da Python Bottle, Flask ve Django çerçeve proje şablonları ve çeşitli çerçeveler işlemek için yapılandırılabilir bir hata ayıklama başlatıcısı aracılığıyla web projelerini geliştirmeyi destekler. Bu şablonlar içeren bir *requirements.txt* gerekli bağımlılıkları bildirmek için dosya. Visual Studio bu paketleri yüklemek için bu şablonlardan birini bir proje oluştururken, ister (bkz [yüklemek proje gereksinimlerini](#install-project-requirements) bu makalenin ilerleyen bölümlerinde).

Genel kullanabilirsiniz **Web projesi** Piramit gibi diğer çerçeveler için şablon. Bu durumda, çerçeve şablonla yüklenir. Bunun yerine, proje için kullanmakta olduğunuz ortamına gerekli paketleri yükleyin (bkz [Python ortamları penceresi - paket sekmesindeki](python-environments-window-tab-reference.md#packages-tab)).

Python web uygulamasını Azure'a dağıtma hakkında daha fazla bilgi için bkz: [Azure App Service'e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Bir proje şablonu kullanın

Bir şablon kullanarak bir proje oluşturma **dosya** > **yeni** > **proje**. Web projeleri için şablonları görmek için seçin **Python** > **Web** iletişim kutusunun sol tarafındaki. Ardından, tercih ettiğiniz bir şablonu seçin, adları sağlamak için projeyi ve çözümü, çözüm dizini ve Git deposu için seçenekleri ayarlayın ve seçin **Tamam**.

![Web apps için yeni proje iletişim kutusu](media/projects-new-project-dialog-web.png)

Genel **Web projesi** şablon, daha önce bahsedilen yalnızca boş bir Visual Studio projesinin hiçbir kod ve Python projesi olması dışında hiçbir varsayım sağlar. İlgili Ayrıntılar için **Azure bulut hizmeti** şablonu görmek [Python için Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md).

Tüm şablonları, Bottle, Flask ve Django web çerçeveleri temel alır ve aşağıdaki bölümlerde açıklandığı gibi üç genel gruplara ayrılır. Bu şablonlardan birini tarafından oluşturulan uygulamaları çalıştırmak ve uygulamayı yerel olarak hata ayıklama için yeterli kodu içerir. Her biri de gerekli sağlar [WSGI uygulama nesnesi](https://www.python.org/dev/peps/pep-3333/) (python.org) üretim web sunucularına ile kullanmak için.

### <a name="blank-group"></a>Boş Grup

Tüm **boş \<framework > Web projesini** şablonları ile daha fazla bir proje oluşturun ya da daha az en az bir ortak kod ve gerekli bağımlılıkları bildirilen bir *requirements.txt* dosya.

| Şablon | Açıklama |
| --- | --- |
| **Boş Bottle Web projesi** | En az bir uygulama oluşturur *app.py* bir ana sayfası ile `/` ve `/hello/<name>` yankılayan sayfa `<name>` çok kısa bir satır içi sayfası şablonu kullanarak. |
| **Boş Django Web projesi** | Bir çekirdek Django site yapısı ancak hiçbir Django uygulamaları ile Django projesi oluşturur. Daha fazla bilgi için [Django şablonları](python-django-web-application-project-template.md) ve [Django adımı 1 bilgi](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Boş bir Flask Web projesi** | Bir tek "Hello World!" ile en az bir uygulama oluşturur. için sayfa `/`. Bu uygulamanın ayrıntılı anlatılan adımları izleyerek sonucunu benzer [hızlı başlangıç: ilk Python web uygulamanızı oluşturmak için Visual Studio](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Ayrıca bkz: [Flask adımı 1 bilgi](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Web grubu

Tüm  **\<Framework > Web projesini** şablonları, seçilen framework bağımsız olarak aynı bir tasarım ile bir başlangıç web uygulaması oluşturma. Uygulamanın giriş, yok yanı sıra bir gezinti çubuğunda ve Bootstrap ile esnek tasarım hakkında ve ilgili kişi sayfaları. Her uygulama statik dosyaları (CSS, JavaScript ve yazı tipleri) sunmak için uygun şekilde yapılandırıldığından ve framework için uygun bir sayfayı şablon mekanizması kullanır.

| Şablon | Açıklama |
| --- | --- |
| **Bottle Web projesi** | Statik dosyalar içerdiği bir uygulama oluşturur *statik* klasörü ve aracılığıyla kod içinde işlenmesini *app.py*. Tek tek sayfaları için yönlendirme kapsanıyorsa *routes.py*ve *görünümleri* klasörü sayfası şablonlarını içerir.|
| **Django Web projesi** | Django projesi ve üç sayfası, kimlik doğrulama desteği ve bir SQLite veritabanı (ancak hiçbir veri modelleri) ile bir Django uygulaması oluşturur. Daha fazla bilgi için [Django şablonları](python-django-web-application-project-template.md) ve [Django adımı 4 bilgi](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Flask Web projesi** | Statik dosyalar içerdiği bir uygulama oluşturur *statik* klasör. Kod *views.py* işleme bulunan Jinja altyapısı kullanarak şablonların yönlendirme *şablonları* klasör. *Runserver.py* dosya başlatma kodunu sağlar. Bkz: [Flask adımı 4 bilgi](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Webový projekt ve Flask/Jade** | Olarak aynı uygulamayla oluşturur **Flask Web projesi** şablon ancak Jade uzantısıyla Jinja şablon oluşturma altyapısı için. |

### <a name="polls-group"></a>Polls – grubu

**Yoklamalar \<framework > Web projesini** şablonları hakkında sorular farklı yoklama üzerinden kullanıcılar oy bir başlangıç web uygulaması oluşturma. Her uygulama yapısını oluşturur **Web** proje şablonları, anketler ve kullanıcı yanıtlar yönetmek için bir veritabanı kullanılacak. Uygun veri modelleri içeren uygulamalar ve sayfa (/ Temel), özel bir uygulama yoklamalar'dan yükleyen bir *samples.json* dosya.

| Şablon | Açıklama |
| --- | --- |
| **Polls – Bottle Webový projekt** | Bir bellek içi veritabanına, MongoDB veya kullanılarak yapılandırılan Azure tablo depolama karşı çalışan bir uygulama oluşturur `REPOSITORY_NAME` ortam değişkeni. Veri modelleri ve veri deposu kod içerdiği *modelleri* klasöründe ve *settings.py* hangi veri deposu kullanıldığını belirlemek için kod dosyası içerir. |
| **Yoklamalar Django Web projesi** | Django projesi ve bir Django uygulaması üç sayfası ve bir SQLite veritabanı oluşturur. Django yönetim arabirimini oluşturun ve anketler yönetmek kimliği doğrulanmış bir yönetici izin vermek için özelleştirmeleri içerir. Daha fazla bilgi için [Django şablonları](python-django-web-application-project-template.md) ve [öğrenin Django adım 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Polls – Flask Web projesi** | Bir bellek içi veritabanına, MongoDB veya kullanılarak yapılandırılan Azure tablo depolama karşı çalışan bir uygulama oluşturur `REPOSITORY_NAME` ortam değişkeni. Veri modelleri ve veri deposu kod içerdiği *modelleri* klasöründe ve *settings.py* hangi veri deposu kullanıldığını belirlemek için kod dosyası içerir. Uygulama sayfası şablonları Jinja altyapısı kullanır. Bkz: [Flask adım 5 öğrenin](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Polls – Webový projekt Flask/Jade** | Olarak aynı uygulamayla oluşturur **yoklamalar Flask Web projesi** şablon ancak Jade uzantısıyla Jinja şablon oluşturma altyapısı için. |

## <a name="install-project-requirements"></a>Projenizin gereksinimlerini yükleyin

Çerçeveye özgü şablondan bir proje oluştururken, pip kullanarak gerekli paketleri yüklemenize yardımcı olması için bir iletişim kutusu görüntülenir. Ayrıca kullanmanızı öneririz bir [sanal ortam](selecting-a-python-environment-for-a-project.md#use-virtual-environments) doğru bağımlılıklar dahil olacak şekilde, web projeleri için yayımladığınızda, web sitesi:

![Yükleyen iletişim için bir proje şablonu paketleri gerekli](media/template-web-requirements-txt-wizard.png)

Kaynak denetimi kullanıyorsanız, bu ortamda yalnızca kullanılarak yeniden oluşturulabilir gibi genellikle sanal ortam klasörü atlarsanız *requirements.txt*. Bir klasörü dışlamak için en iyi yolu ilk seçmektir **ben bunları kendim yükler** yukarıda gösterilen isteminde sonra otomatik tamamlama sanal ortamı oluşturmadan önce devre dışı bırakın. Ayrıntılar için bkz [öğrenin Django Öğreticisi - 1-2 ve 1-3 adımları](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) ve [öğrenin Flask Öğreticisi - 1-2 ve 1-3 adımları](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Microsoft Azure App Service'e dağıtım yaparken, Python sürümünü seçin. bir [site uzantısı](https://aka.ms/PythonOnAppService) ve paketleri el ile yükleyin. Ayrıca, Azure App Service gerçekleştirdiğinden **değil** paketleri otomatik olarak yüklemeniz bir *requirements.txt* dosya Visual Studio'dan dağıtıldığında, yapılandırma ayrıntılarını izleyin [aka.ms/ PythonOnAppService](https://aka.ms/PythonOnAppService).

Microsoft Azure bulut Hizmetleri *mu* Destek *requirements.txt* dosya. Bkz: [Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md) Ayrıntılar için.

## <a name="debugging"></a>Hata Ayıklama

Bir web projesi için hata ayıklama başladığında, Visual Studio rastgele bir bağlantı noktası üzerinde bir yerel web sunucusu başlatır ve bu adresi ve bağlantı noktası için varsayılan tarayıcınızı açar. Ek seçenekleri belirlemek için projeye sağ tıklayın, **özellikleri**seçip **Web Başlatıcısı** sekmesinde:

![Genel web şablonu için Web Başlatıcısı özellikleri](media/template-web-launcher-properties.png)

İçinde **hata ayıklama** Grup:

- **Arama yolları**, **betik bağımsız değişkenleri**, **yorumlayıcı bağımsız değişkenleri**, ve **cesta k İnterpretu**: Bu seçenekler aynıdır [normal hata ayıklama](debugging-python-in-visual-studio.md).
- **Başlatılacak URL**: tarayıcınızda açılır URL'sini belirtir. Varsayılan `localhost`.
- **Bağlantı noktası numarası**: URL (bir otomatik olarak varsayılan Visual Studio seçer) hiçbiri belirtilmediği takdirde kullanılacak bağlantı noktası. Bu ayar varsayılan değerini geçersiz kılmanıza da olanak sağlar. `SERVER_PORT` şablonları tarafından kullanılan yerel hata ayıklama sunucunun dinlediği bağlantı noktasını yapılandırmak için ortam değişkeni.

Özelliklerinde **sunucu komutu Çalıştır** ve **Server komutu hata ayıklama** (ikinci görüntüde gösterilen aşağıda) grupları belirlemek web sunucusuna nasıl başlatılır. Birçok geçerli projenin dışında bir betik gerektirdiğinden, betiği buraya yapılandırılabilir ve başlangıç modülünün adı, parametre olarak geçirilebilir.

- **Komut**: Python betiğini olabilir (*\*.py* dosyası), bir modül adı (gibi `python.exe -m module_name`), veya tek satırlık bir kod (gibi `python.exe -c "code"`). Aşağı açılan değer, bu tür barındırılmasını gösterir.
- **Bağımsız değişkenler**: şu bağımsız değişkenler, aşağıdaki komut komut satırında geçirilir.
- **Ortam**: yeni satır ile ayrılmış bir listesini \<adı > =\<değer > ortam değişkenlerini belirtme çiftleri. Bu değişkenler, bağlantı noktası numarası ve arama yolları gibi ortam değiştirebilir ve bu nedenle bu değerler yazabilir tüm özellikleri sonra ayarlanır.

MSBuild söz dizimine sahip herhangi bir proje özelliği veya ortam değişkeni örneğin belirtilebilir: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` Başlangıç dosyasının göreli yoludur ve `{StartupModule}` başlangıç dosyası alınabilir adıdır. `$(SERVER_HOST)` ve `$(SERVER_PORT)` tarafından ayarlanan normal ortam değişkenleri **başlatılacak URL** ve **bağlantı noktası numarası** özellikleri, otomatik olarak ya da **ortam** özelliği.

> [!Note]
> Değerler **sunucu komutu Çalıştır** ile kullanılan **hata ayıklama** > **Start Server** komutu veya **Ctrl** + **F5**; değerler **Server komutu hata ayıklama** grubu ile kullanılan **hata ayıklama** > **hata ayıklama sunucusu Başlat** komut veya **F5**.

### <a name="sample-bottle-configuration"></a>Örnek Bottle yapılandırma

**Bottle Web projesi** şablonu gerekli yapılandırma yaptığı ortak kod içerir. Ancak, bu durumda aşağıdaki ayarları kullanarak yüklü uygulamayı başlatın, içeri aktarılan bottle uygulaması bu kodu içermeyebilir `bottle` Modülü:

- **Server komutu çalıştırarak** Grup:
  - **Komut**: `bottle` (Modülü)
  - **Bağımsız değişkenler**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Sunucu komut hata ayıklama** Grup:
  - **Komut**: `bottle` (Modülü)
  - **bağımsız değişkenler** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload` Seçeneği, Visual Studio hata ayıklama için kullanırken önerilmez.

### <a name="sample-pyramid-configuration"></a>Örnek Piramit yapılandırma

Piramit uygulamaları, kullanılarak şu anda en iyi oluşturulur `pcreate` komut satırı aracı. Uygulama oluşturulduktan sonra bunu kullanarak içeri aktarılabilir [ **mevcut Python'dan kod** ](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) şablonu. Bunu yaptıktan sonra seçin **Genel Web projesi** özelleştirme seçeneklerini yapılandırmak için. Bu ayarlar Piramit sırasında sanal bir ortama yüklü olduğu varsayılmıştır `..\env`.

- **Hata ayıklama** Grup:
  - **Sunucu bağlantı noktası**: 6543 (veya her yapılandırılan *.ini* dosyaları)

- **Server komutu çalıştırarak** Grup:
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Bağımsız değişkenleri: `Production.ini`

- **Sunucu komut hata ayıklama** Grup:
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Bağımsız değişkenleri: `Development.ini`

> [!Tip]
> Büyük olasılıkla yapılandırmanız gereken **çalışma dizini** projenizin özellik çünkü Piramit uygulamalar genellikle proje kökünün altındaki bir klasör.

### <a name="other-configurations"></a>Diğer yapılandırmalar

Ayarları paylaşma veya başka bir framework ayarlarını talebinde bulunmak isterseniz, açmak istediğiniz başka bir Framework varsa bir [github'da sorun](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Azure bulut hizmeti için bir proje Dönüştür

**Microsoft Azure bulut hizmeti projesine Dönüştür** komutu (aşağıdaki görüntüde) bir bulut hizmeti projesini çözümünüze ekler. Bu projenin, kullanılacak sanal makineler ve hizmetler için yapılandırma ve dağıtım ayarları içerir. Kullanım **Yayımla** ; bulut Hizmetleri dağıtmak için bulut projesi komutunu **Yayımla** Python projedeki komutu, Web siteleri için hala dağıtır. Daha fazla bilgi için [Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md).

![Microsoft Azure bulut hizmeti projesi komutu için Dönüştür](media/template-web-convert-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Python öğesi şablonları başvurusu](python-item-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
