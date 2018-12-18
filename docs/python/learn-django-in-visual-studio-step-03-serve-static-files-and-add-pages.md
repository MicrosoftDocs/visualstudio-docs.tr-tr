---
title: Django Öğreticisi 3. adımda Visual Studio, statik dosyalar ve sayfalar öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle statik dosyaları işleme, uygulamaya sayfaları ekleyin ve şablonu devralma gösterimi bağlamında Django temel bilgileri bir kılavuz
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
ms.openlocfilehash: cfde21f356e35366cfb80b029f918eed0364a7b5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066086"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>3. adım: statik dosyaları işleme, sayfalar eklemek ve şablonu devralma kullanın

**Önceki adımda: [görünümleriyle bir Django uygulaması oluşturma ve sayfa şablonları](learn-django-in-visual-studio-step-02-create-an-app.md)**

Bu öğreticinin önceki adımlarında müstakil HTML tek bir sayfayla en az bir Django uygulaması oluşturulacağını öğrendiniz. Modern web uygulamaları, ancak genellikle birçok sayfaları oluşan ve olun tutarlı bir stil ve davranışı sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları.

Bu adımda, şunların nasıl yapılır:

> [!div class="checklist"]
> - Hızlı bir şekilde uygun Demirbaş kod ile farklı türdeki yeni dosyaları eklemek için Visual Studio öğe şablonları kullanın (adım 3 - 1)
> - (3-2. adım) statik dosyaları sunmak için Django projesi yapılandırma
> - (3-3. adım) uygulamaya ek sayfalar ekleme
> - (Adım 3-4) sayfalar arasında kullanılan bir üst bilgi ve gezinti çubuğu oluşturmak için şablon devralma kullanın

## <a name="step-3-1-become-familiar-with-item-templates"></a>3-1. adım: öğe şablonları ile aşina

Bir Django uygulaması geliştirirken, genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyaları ekleyin. Her dosya türü için (diğer dosyaları ister *web.config* dağıtımı için ihtiyacınız olan), Visual Studio'nun sağladığı uygun [öğe şablonları](python-item-templates.md) başlamanıza yardımcı olmak için.

Kullanılabilir şablonlar görmek için Git **Çözüm Gezgini**, select öğesi oluşturmak istediğiniz klasörü sağ tıklatın **Ekle** > **yeni öğe**:

![Visual Studio'da yeni öğesi ekleme](media/django/step03-add-new-item-dialog.png)

Bir şablonu kullanmak için istediğiniz şablonu seçin, dosya için bir ad belirtin ve seçin **Tamam**. Bu şekilde otomatik olarak öğe ekleme dosyası Visual Studio projenize ekler ve kaynak denetimi için değişiklikleri işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Nasıl Visual Studio, öğe şablonları sunmaya bilir?

Yanıt: Visual Studio Proje dosyası (*.pyproj*) bir Python projesi olarak işaretleyen bir proje türü tanımlayıcısı içeriyor. Visual Studio, proje türü için uygun olan öğe şablonları göstermek için bu tür tanımlayıcısı kullanır. Bu şekilde bloblarda her sıralamak için sormadan türleri pek çok proje için Visual Studio öğe şablonları zengin sağlayabilirsiniz.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2. adım: hizmet uygulamanızdan statik dosyalar

Python (herhangi bir çerçeveyi kullanarak) ile oluşturulmuş bir web uygulaması, Python dosyalarınızın her zaman web ana bilgisayarın sunucu üzerinde çalışan ve bir kullanıcının bilgisayarına hiçbir zaman iletilmez. Ana sunucu olarak yalnızca sunar diğer dosyaları, Bununla birlikte, CSS ve JavaScript gibi tarayıcı tarafından özel olarak kullanıldığından-bunlar istenen ne zaman açıktır. Bu tür dosyalar "statik" dosyaları olarak adlandırılır ve Django bunları otomatik olarak, kod yazmaya gerek sunabilirsiniz.

Varsayılan olarak uygulama statik dosyaları sunmak için yapılandırılmış bir Django projesi *statik* Django projenin bu satırları sayesinde klasöründe *settings.py*:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

İçinde herhangi bir klasör yapısının kullanarak dosyaları düzenlediğiniz *statik* ister ve sonra dosyalara başvurmak için bu klasörün içinde göreli yollar kullanın. Bu işlem göstermek için aşağıdaki adımları uygulamaya bir CSS dosyası ekleyin ve ardından bu stil kullanmak *index.html* şablonu:

1. İçinde **Çözüm Gezgini**, sağ **HelloDjangoApp** seçin Visual Studio proje klasöründe **Ekle** > **Yeniklasör**ve klasörünü adlandırın `static`.

1. Sağ **statik** klasörü ve select **Ekle** > **yeni öğe**. Görüntülenen iletişim kutusunda, seçmek **stil sayfası** şablonu, dosya adı `site.css`seçip **Tamam**. **Site.css** dosya projesinde görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünmelidir:

    ![Çözüm Gezgini'nde görüldüğü gibi statik dosya yapısı](media/django/step03-static-file-structure.png)

1. Öğesinin içeriğini değiştirin *site.css* aşağıdaki kodla ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın içeriğini değiştirin *templates/HelloDjangoApp/index.html* değiştirir aşağıdaki kod ile dosya `<strong>` ile 2. adımda kullanılan öğe bir `<span>` başvuran `message` stil sınıf. Bu şekilde bir stil sınıfını kullanarak öğeyi stil çok daha fazla esneklik sağlar. (Henüz taşıdıysanız *index.html* içinde alt *şablonları* VS 2017 15.7 kullanırken ve daha önce başvurmak [şablon namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) 2-4. adımda.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Sonuçları görmek için projeyi çalıştırın. İşiniz bittiğinde sunucusunu durdurmak ve isterseniz kaynak denetimi için yaptığınız değişiklikleri kaydedin (açıklandığı şekilde [2. adım](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Soru: {% yük staticfiles %} etiketi? amacı nedir

Yanıt: `{% load staticfiles %}` satır öğeleri gibi statik dosyalar başvuran önce gerekli `<head>` ve `<body>`. Bu bölümde gösterilen örnekte, "staticfiles" kullanmanıza olanak sağlayan olan özel Django şablon etiket kümesine, başvuruyor `{% static %}` sözdizimi statik dosyaya başvurmuyor.  Olmadan `{% load staticfiles %}`, uygulama çalıştığında bir özel durum görürsünüz.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: statik dosyaları düzenlemek için tüm kuralları var mı?

Yanıt: Diğer CSS, JavaScript ve HTML dosyaları ekleyebilirsiniz, *statik* klasör ancak istediğiniz. Statik dosyaları düzenlemek için normal bir şekilde adlandırılmış alt klasörlerde oluşturmaktır *yazı tipleri*, *betikleri*, ve *içeriği* (için stil sayfaları ve diğer dosyaları). Her durumda, bu klasörleri dosyasına göreli yolda unutmayın `{% static %}` başvuruları.

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3. adım: uygulama için bir sayfa ekleyin

Uygulamaya başka bir sayfa ekleme aşağıdaki anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın işaretleme için bir şablon ekleyin.
- Django projenin için gerekli yönlendirme ekleme *urls.py* dosya.

Aşağıdaki adımları giriş sayfasından, ilgili sayfada bağlantılara ve "HelloDjangoApp" proje "Hakkında" sayfasında ekleyin:

1. İçinde **Çözüm Gezgini**, sağ **şablonları/HelloDjangoApp** klasörüne **Ekle** > **yeni öğe**seçin **HTML sayfası** öğe şablonu, dosya adı `about.html`seçip **Tamam**.

    > [!Tip]
    > Varsa **yeni öğe** komutu görünmezse **Ekle** menüsünde, böylece Visual Studio hata ayıklama modundan çıkar Sunucu durduruldu emin olun.

1. Öğesinin içeriğini değiştirin *about.html* aşağıdaki işaretlemeyle (sizin yerine giriş sayfasına açık bağlantı 3-4. adımda basit bir gezinti):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Uygulamanın açın *views.py* adlı bir işlev eklemek ve dosya `about` şablonu kullanan:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Django projenin açın *urls.py* dosyasını açıp aşağıdaki satırı ekleyin `urlPatterns` dizisi:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Açık *templates/HelloDjangoApp/index.html* dosyasını açıp aşağıdaki satırı ekleyin `<body>` hakkında sayfasına bağlantı için öğe (yeniden, bu bağlantıyı 3-4. adımda bir gezinti çubuğuyla değiştirin):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Kullanarak dosyaları kaydetme **dosya** > **Tümünü Kaydet** basın veya menü komutu **Ctrl**+**Shift** + **S**. (Visual Studio'da proje çalıştıran dosyaları otomatik olarak kaydeder gibi teknik olarak, bu adım gerek yoktur. Bununla birlikte, işte hakkında bilgi edinmek için iyi bir komutu bu kadar!)

1. Sonuçları inceleyin ve sayfalar arasında gezinti denetlemek için projeyi çalıştırın. Sunucunun işiniz bittiğinde kapatın.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Soru: "Index" giriş sayfasına bağlantı için kullanarak olan çalıştım, ancak işe yaramadı. Neden?

Yanıt: görünüm işlevi içinde olsa bile *views.py* adlı `index`, Django projesinin desenleri yönlendirme URL *urls.py* dosya dizesiyle eşleşen normal bir ifade içermiyor " dizin". O dizeyi eşleştirilecek desen için başka bir girdi eklemeniz gerekir `^index$`.

Sonraki bölümde gösterildiği gibi çok kullanmak en iyisidir `{% url '<pattern_name>' %}` başvurmak için sayfası şablonu etiketinde *adı* içinde büyük/küçük harf Django oluşturan uygun URL'yi sizin için bir desen,. Örneğin, `<div><a href="home">Home</a></div>` içinde *about.html* ile `<div><a href="{% url 'index' %}">Home</a></div>`. 'Dizin' kullanımını çalışır burada ilk URL deseni çünkü *urls.py* aslında 'dizin' adlı (tarafından virtue, `name='index'` bağımsız değişkeni). 'Ana' İkinci desen başvurmak için kullanabilirsiniz.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4. adım: bir başlık ve gezinti çubuğu oluşturmak için şablon devralma kullanın

Açık Gezinti bağlantıları her sayfada sahip olmak yerine modern web uygulamaları genellikle bir marka başlığı ve en önemli sayfa bağlantılarının, açılır menüler ve benzeri sağlayan bir gezinti çubuğunu kullanın. Üst bilgi ve gezinti çubuğunda aynı olan tüm sayfalara emin olmak için ancak her sayfası şablonu aynı kodu yinelemek istediğiniz yok. Bunun yerine, tek bir yerde tüm sayfaları ortak parçalarını tanımlamak istersiniz.

Django'nın şablon oluşturma sistemi belirli öğeleri birden çok şablon tarafından yeniden kullanmak için iki yol sağlar: içerir ve devralma.

- *İçerir* başvurulan şablonun söz dizimini kullanarak belirli bir yerde eklediğiniz diğer sayfası şablonları `{% include <template_path> %}`. Dinamik olarak kod yolu değiştirmek istiyorsanız, bir değişken de kullanabilirsiniz. İçeren bir sayfa gövdesinde genellikle paylaşılan şablondaki sayfasında belirli bir konumda çekmek için kullanılır.

- *Devralma* kullanan `{% extends <template_path> %}` başına sayfa şablonunun üzerine sonra başvuran şablon oluşturur paylaşılan, temel bir şablonu belirtin. Devralma, gezinti çubuğunda bir paylaşılan düzeni tanımlamak için yaygın olarak kullanılır ve başvuran şablonlar yalnızca eklemek veya adlı temel şablon, belirli alanları değiştirmek için uygulamanın sayfaları, diğer yapıları *blokları*.

Her iki durumda da `<template_path>` uygulamanın göreli olan *şablonları* klasörü (`../` veya `./` de izin verilir).

Bir temel şablon kullanımını engeller betimleyen `{% block <block_name> %}` ve `{% endblock %}` etiketler. Başvuran bir şablon daha sonra aynı blok ada sahip etiketler kullanılıyorsa, blok içeriği bu temel şablonu geçersiz.

Aşağıdaki adımlarda, devralma gösterilmektedir:

1. Uygulamanın *şablonları/HelloDjangoApp* klasöründe yeni bir HTML dosyası oluşturun (kullanarak **Ekle** > **yeni öğe** bağlam menüsü veya **Ekle**  >  **HTML sayfası**) olarak adlandırılan *layout.html*ve içeriğini biçimlendirme ile değiştirin. Bu şablon "içerik" adlı bir bloğu, tüm bu başvuran sayfalar ihtiyacı değiştirin, içerdiğini görebilirsiniz:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Uygulamanın aşağıdaki stilleri ekleme *static/site.css* dosyası (esnek tasarım göstermek bu adımları uygulamayı denemeden değildir; bu yalnızca bir ilgi çekici sonuç üretmek için stillerdir):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Değiştirme *templates/HelloDjangoApp/index.html* temel şablona başvurun ve içerik bloğu yok saymak için. Devralma kullanarak, bu şablon basit olacağını görebilirsiniz:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Değiştirme *templates/HelloDjangoApp/about.html* ayrıca temel şablona başvurun ve içerik bloğu yok saymak için:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları görmek için sunucu çalıştırın. Sunucunun işiniz bittiğinde kapatın.

    ![Gezinti çubuğunu gösteren çalışan uygulama](media/django/step03-nav-bar.png)

1. Önemli değişiklikler uygulamaya yapılan, tekrar iyi birer olmasıdır [kaynak denetimine değişikliklerinizi işleyin](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Tam Django Web projesi şablonunu kullanma](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Web uygulamasını Azure App Service'e dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Django uygulamanız yazma, Bölüm 3 (görünümleri)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Daha fazla özellik denetim akışı gibi Django şablonları için bkz: [Django şablonu dil](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Kullanma hakkında tam bilgi `{% url %}` etiketlemek için bkz: [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) içinde [yerleşik şablon etiketleri ve Django şablonları başvurusu için filtreler](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
