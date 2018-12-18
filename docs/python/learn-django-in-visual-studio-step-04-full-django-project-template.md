---
title: Django Öğreticisi 4. adımda Visual Studio, web projesi şablonu öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle Django Web projesi şablonu tarafından sağlanan özellikler bağlamında Django temel bilgileri bir kılavuz.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 865a0368933fa0a66728afaead6677cbeca84834
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065467"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>4. adım: tam Django Web projesi şablonunu kullanma

**Önceki adımda: [statik dosyaları sunmak, sayfalar eklemek ve şablonu devralma kullanın](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

"Boş Django Web projesi" şablonu Visual Studio'da bağlı bir uygulama oluşturarak Django temelleri incelediniz, "Django Web projesi" şablon tarafından üretilen irdelemesi uygulamayı kolayca anlayabilir.

Bu, artık. adım:

> [!div class="checklist"]
> - "Django Web projesi" şablonu kullanarak bir irdelemesi Django web uygulaması oluşturma ve proje yapısını inceleyin (adım 4 - 1)
> - Proje şablonu tarafından oluşturulan taban sayfası şablondan devralır üç sayfası oluşur sayfası şablonları ve görünümleri anlayın ve, jQuery ve önyükleme (4-2. adım) gibi statik JavaScript kitaplıklarını kullanır
> - (4-3. adım) şablonu tarafından sağlanan URL yönlendirmeyi anlama

Şablon 5. adımda bahsedilen temel kimlik doğrulaması da sağlar.

## <a name="step-4-1-create-a-project-from-the-template"></a>4-1. adım: bir şablondan bir proje oluşturma

1. Visual Studio'da Git **Çözüm Gezgini**, sağ **LearningDjango** daha önce Bu öğretici ve seçme içinde oluşturulan çözüm **Ekle**  >   **Yeni proje**. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, seçin **dosya** > **yeni** > **proje** yerine.)

1. Yeni Proje iletişim kutusunda, aramak ve seçmek **Django Web projesi** şablonu, "DjangoWeb" proje arayın ve seçin **Tamam**.

1. Şablonu yeniden içerdiğinden bir *requirements.txt* dosya, Visual Studio bu bağımlılıkların yükleneceği sorar. Seçeneğini **sanal bir ortama yükleme**hem de **sanal ortama ekleme** iletişim kutusunda **Oluştur** Varsayılanları kabul etmek için.

1. Visual Studio sanal ortam kurma tamamlandıktan sonra görüntülenen yönergeleri izleyin *readme.html* Django süper kullanıcı (diğer bir deyişle, bir yönetici) oluşturmak için. Yalnızca Visual Studio projesini sağ tıklayın ve **Python** > **Django yetkili kullanıcısı oluşturma** komutunu ve ardından yönergeleri izleyin. Uygulamanın kimlik doğrulama özellikleri denemek, kullandığınız kullanıcı adı ve parolayı kaydettiğinizden emin olun.

1. Ayarlama **DjangoWeb** proje bu projeye sağ tıklayarak Visual Studio çözümü için varsayılan olarak **Çözüm Gezgini** seçerek **başlangıç projesi olarak ayarla** . Gösterilen başlangıç projesi içinde hata ayıklayıcısını başlattığınızda nelerin çalıştırılacağını kalın.

    ![Başlangıç projesi olarak DjangoWeb projeyi gösteren Çözüm Gezgini](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Seçin **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** server çalıştırmak için araç çubuğunda:

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama hakkında ev ve kişi, hangi gezinti çubuğunda kullanma arasında gezinmek üç sayfa vardır. Bir veya iki uygulamanın farklı kısımlarını incelemek için dakika alın. Uygulamada kimlik doğrulaması yapmak için **oturum** komutu, daha önce oluşturduğunuz süper kullanıcı kimlik bilgilerini kullanın.

    ![Django Web projesi uygulamasının tam tarayıcı görünümü](media/django/step04-full-app-desktop-view.png)

1. "Django Web projesi" şablonu ile oluşturulan uygulama için mobil form faktörleri kapsar esnek Düzen önyükleme kullanır. Bu yanıt verdiğini görmek için bir dar görünüm tarayıcıya dikey olarak içerik işler ve gezinti çubuğunda bir menü simgesine dönüşür şekilde boyutlandırın:

    ![Django Web projesi uygulamasının mobil (dar) görünümü](media/django/step04-full-app-mobile-view.png)

1. İzleyen bölümlerde için uygulamayı bırakabilirsiniz.

    Uygulamayı durdurmak istiyorsanız ve [değişiklikleri kaynak denetimine](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), ilk açın **değişiklikleri** sayfasını **Takım Gezgini**, sanal ortam (klasörünü sağ tıklatın büyük olasılıkla **env**) seçip **bu yerel öğeleri Yoksay**.

### <a name="examine-what-the-template-creates"></a>Hangi şablon oluşturur inceleyin

En geniş kapsamlı düzeyinde "Django Web projesi" şablonu aşağıdaki yapısını oluşturur:

- Proje kökündeki dosyaları:
  - *Manage.PY*, Django yönetim yardımcı programı.
  - *DB.sqlite3*, varsayılan bir SQLite veritabanıdır.
  - *Requirements.txt* Django bağımlılık içeren 1.x.
  - *Readme.HTML*, projeyi oluşturduktan sonra Visual Studio içinde görüntülenen bir dosya. Önceki bölümde belirtildiği gibi uygulama için bir süper kullanıcı (Yönetici) hesabı oluşturmak için buradaki yönergeleri izleyin.
- *Uygulama* klasör görünümleri, modelleri, testleri, forms, şablonları ve (4-2. adım) statik dosyaları dahil olmak üzere tüm uygulama dosyaları içerir. Genellikle bu klasör daha farklı bir uygulama adı kullanacak şekilde yeniden adlandırın.
- *DjangoWeb* tipik Django proje dosyaları (Django projesinde) klasör içerir:  *\_ \_init\_\_.py*,  *Settings.PY*, *urls.py*, ve *wsgi.py*. Proje şablonunu kullanarak *settings.py* uygulama ve veritabanı dosyası için zaten yapılandırıldı ve *urls.py* rotaları oturum açma formu dahil olmak üzere tüm uygulama sayfaları için zaten yapılandırıldı.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasındaki bir sanal ortam paylaşmayı mümkün mü?

Cevap: Evet, ancak büyük olasılıkla farklı projelerde zaman içinde farklı paketleri kullanın ve bu nedenle, paylaşılan bir sanal ortam bunu kullanan tüm projeler için tüm paketleri içermelidir tanıma ile bunu.

Bununla birlikte, mevcut bir sanal ortam kullanmak için aşağıdakileri yapın:

1. Visual Studio'da bağımlılıkları yüklemek isteyip istemediğiniz sorulduğunda seçin **ben bunları kendim yükler** seçeneği.
1. İçinde **Çözüm Gezgini**, sağ **Python ortamları** düğümünü seçip alt **var olan sanal ortama ekleme**.
1. Gidin ve sanal ortam içeren klasörü seçin ve ardından **Tamam**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>4-2. adım: görünümleri anlayın ve sayfa proje şablonu tarafından oluşturulan şablonlar

Projeyi çalıştırdığınızda gözlemleyin gibi uygulamayı üç görünüm içerir: hakkında ev ve başvurun. Bu görünümler için kod bulunan *uygulama/görünümler* klasör. Her görünüm işlevi yalnızca çağırır `django.shortcuts.render` yoluyla bir şablon ve basit bir sözlük nesnesi. Örneğin, hakkında sayfası tarafından işlenir `about` işlevi:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Şablonlar, uygulamanın bulunur *şablonları/uygulama* klasörü (ve genellikle yeniden adlandırmak istediğiniz *uygulama* gerçek uygulamanızın adı için). Temel şablon *layout.html*, en kapsamlı olduğundan. Bu, tüm gerekli statik dosyaları (JavaScript ve CSS) gösterir, diğer geçersiz kılma sayfaları ve "betik" adlı başka bir bloğu sağlar "içerik" adlı bir bloğu tanımlar. Aşağıdaki parçalarını açıklamalı *layout.html* bu belirli alanları göster:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Tek tek sayfa şablonları *about.html*, *contact.html*, ve *index.html*, her bir temel şablon genişletme *layout.html*. *About.HTML* kolayıdır ve gösterir `{% extends %}` ve `{% block content %}` etiketler:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.HTML* ve *contact.html* aynı yapısını kullanın ve "içerik" bloğundaki daha uzun bir içerik sağlayın.

İçinde *şablonları/uygulama* klasördür ayrıca dördüncü sayfada *login.html*, birlikte *loginpartial.html* içine duruma *layout.html*kullanarak `{% include %}`. Bu şablon dosyalarını, kimlik doğrulaması 5. adımında ele alınmıştır.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Soru: Can {% block %} ve {% endblock Django sayfası şablonunda %} girintili?

Yanıt: belki de bunları uygun üst öğeleri içinde hizalamak için blok etiketlerini Girintile Evet, Django şablonların düzgün çalışır. Bunlar nereye yerleştirileceğini NET bir şekilde görmenize olanak tanıyan Visual Studio Proje şablonu tarafından oluşturulan şablonların girintili değil.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>4-3. adım: şablon tarafından oluşturulan URL yönlendirmeyi anlama

Django projenin *urls.py* "Django Web projesi" şablon tarafından oluşturulan dosya, aşağıdaki kodu içerir:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

İlk üç URL desenleri için doğrudan eşleme `home`, `contact`, ve `about` uygulamanın görünümlerde *views.py* dosya. Desenler `^login/$` ve `^logout$`, diğer el, uygulama tarafından tanımlanan görünümleri yerine yerleşik Django görünümlerini kullanın. Çağrıları `url` yöntemi görünümünü özelleştirmek için ek verileri de içerir. 5. adım, bu çağrılar keşfediyor.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Soru: projedeki neden "hakkında" URL deseni kullanan oluşturduğum, ' ^ hakkında ' yerine ' ^ $' burada gösterildiği gibi?

Yanıt: Normal ifadede sonunda '$' eksikliği pek çok proje şablonu sürümlerinde basit bir gözetim alınamadı. Mükemmel "hakkında" adlı bir sayfa için URL deseni çalışır, ancak sondaki ' $' URL deseni ayrıca URL'lerle eşleşir hakkında django ="gibi", "about09876", "aboutoflaughter" ve bu nedenle üzerinde. Sondaki '$' ile eşleşen bir URL deseni oluşturmak için burada gösterilen *yalnızca* "hakkında".

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Django kullanıcıların kimlik doğrulaması](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Web uygulamasını Azure App Service'e dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Django uygulamanız yazma, Bölüm 4 - formlar ve görünümler genel](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
