---
title: Flask Öğreticisi 3. adımda Visual Studio, statik dosyalar ve sayfalar öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle statik dosyaları işleme, uygulamaya sayfaları ekleyin ve şablonu devralma gösterimi bağlamında Flask temel bilgileri bir kılavuz
ms.date: 09/04/2018
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
ms.openlocfilehash: 906c44ca3b1d0771202e78910870d38f9d4fb995
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065031"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>3. adım: statik dosyaları işleme, sayfalar eklemek ve şablonu devralma kullanın

**Önceki adımda: [görünümleri ile bir Flask uygulaması oluşturma ve sayfa şablonları](learn-flask-visual-studio-step-02-create-app.md)**

Bu öğreticinin önceki adımlarında müstakil HTML tek bir sayfayla en az bir Flask uygulaması oluşturulacağını öğrendiniz. Modern web uygulamaları, ancak genellikle birçok sayfaları oluşan ve olun tutarlı bir stil ve davranışı sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları.

Bu adımda, şunların nasıl yapılır:

> [!div class="checklist"]
> - Hızlı bir şekilde uygun Demirbaş kod ile farklı türdeki yeni dosyaları eklemek için Visual Studio öğe şablonları kullanın (adım 3 - 1)
> - Kod (adım 3-2, isteğe bağlı) statik dosyaları işleme
> - (3-3. adım) uygulamaya ek sayfalar ekleme
> - (Adım 3-4) sayfalar arasında kullanılan bir üst bilgi ve gezinti çubuğu oluşturmak için şablon devralma kullanın

## <a name="step-3-1-become-familiar-with-item-templates"></a>3-1. adım: öğe şablonları ile aşina

Bir Flask uygulaması geliştirirken, genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyaları ekleyin. Her dosya türü için (diğer dosyaları ister *web.config* dağıtımı için ihtiyacınız olan), Visual Studio'nun sağladığı uygun [öğe şablonları](python-item-templates.md) başlamanıza yardımcı olmak için.

Kullanılabilir şablonlar görmek için Git **Çözüm Gezgini**, select öğesi oluşturmak istediğiniz klasörü sağ tıklatın **Ekle** > **yeni öğe**:

![Visual Studio'da yeni öğesi ekleme](media/flask/step03-add-new-item-dialog.png)

Bir şablonu kullanmak için istediğiniz şablonu seçin, dosya için bir ad belirtin ve seçin **Tamam**. Bu şekilde otomatik olarak öğe ekleme dosyası Visual Studio projenize ekler ve kaynak denetimi için değişiklikleri işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Nasıl Visual Studio, öğe şablonları sunmaya bilir?

Yanıt: Visual Studio Proje dosyası (*.pyproj*) bir Python projesi olarak işaretleyen bir proje türü tanımlayıcısı içeriyor. Visual Studio, proje türü için uygun olan öğe şablonları göstermek için bu tür tanımlayıcısı kullanır. Bu şekilde bloblarda her sıralamak için sormadan türleri pek çok proje için Visual Studio öğe şablonları zengin sağlayabilirsiniz.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2. adım: hizmet uygulamanızdan statik dosyalar

Python (herhangi bir çerçeveyi kullanarak) ile oluşturulmuş bir web uygulaması, Python dosyalarınızın her zaman web ana bilgisayarın sunucu üzerinde çalışan ve bir kullanıcının bilgisayarına hiçbir zaman iletilmez. Ana sunucu olarak yalnızca sunar diğer dosyaları, Bununla birlikte, CSS ve JavaScript gibi tarayıcı tarafından özel olarak kullanıldığından-bunlar istenen ne zaman açıktır. Bu tür dosyalar "statik" dosyaları olarak adlandırılır ve Flask bunları otomatik olarak, kod yazmaya gerek sunabilirsiniz. HTML dosyaları içinde Örneğin, yalnızca statik dosyalar projesinde bir göreli yol kullanarak başvurabilirsiniz. Bu adım ilk bölümünde mevcut sayfa şablonunuza bir CSS dosyası ekler.

Statik dosya koddan sunmak için ihtiyacınız olduğunda gibi bir API uç nokta uygulaması Flask adlı bir klasör içinde göreli yollar kullanarak dosyalara başvuruda sayesinde kullanışlı bir yöntem sağlar *statik* (Proje kökündeki). Bu adımda ikinci bölümü, bir basit statik veri dosyası kullanarak bu yöntemi gösterir.

Her iki durumda da altındaki dosyaları düzenleyebilirsiniz *statik* istediğiniz gibi.

### <a name="use-a-static-file-in-a-template"></a>Statik dosya olarak bir şablon kullanma

1. İçinde **Çözüm Gezgini**, sağ **HelloFlask** seçin Visual Studio proje klasöründe **Ekle** > **yeni klasör**ve klasörünü adlandırın `static`.

1. Sağ **statik** klasörü ve select **Ekle** > **yeni öğe**. Görüntülenen iletişim kutusunda, seçmek **stil sayfası** şablonu, dosya adı `site.css`seçip **Tamam**. **Site.css** dosya projesinde görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünmelidir:

    ![Çözüm Gezgini'nde görüldüğü gibi statik dosya yapısı](media/flask/step03-static-file-structure.png)

1. Öğesinin içeriğini değiştirin *site.css* aşağıdaki kodla ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın içeriğini değiştirin *templates/index.html* değiştirir aşağıdaki kod ile dosya `<strong>` ile 2. adımda kullanılan öğe bir `<span>` başvuran `message` stil sınıf. Bu şekilde bir stil sınıfını kullanarak öğeyi stil çok daha fazla esneklik sağlar.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Sonuçları görmek için projeyi çalıştırın. İşiniz bittiğinde uygulamayı durdurun ve isterseniz kaynak denetimi için yaptığınız değişiklikleri kaydedin (açıklandığı şekilde [2. adım](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)).

### <a name="serve-a-static-file-from-code"></a>Statik bir kod dosyasından hizmet

Flask çağrılan bir işlev sağlar `serve_static_file` projenin içinde herhangi bir dosyaya başvurmak için kodundan çağıran *statik* klasör. Aşağıdaki işlem, bir statik veri dosyası döndürür basit bir API uç noktası oluşturur.

1. Henüz yapmadıysanız, oluşturun bir *statik* klasör: içinde **Çözüm Gezgini**, sağ **HelloFlask** seçin Visual Studio proje klasöründe **Ekle** > **yeni klasör**ve klasörünü adlandırın `static`.

1. İçinde *statik* klasöründe adlı statik bir JSON veri dosyası oluşturma *data.json* aşağıdaki içeriklerle (hangi anlamsız örnek veriler):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. İçinde *views.py*, bir işlev döndüren statik veri dosyasını kullanarak yol/api/veri Ekle `send_static_file` yöntemi:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uygulamayı çalıştırın ve statik dosya verdiğini görmek için / api/veri bitiş noktasına gidin. İşiniz bittiğinde uygulamayı durdurun.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: statik dosyaları düzenlemek için tüm kuralları var mı?

Yanıt: Diğer CSS, JavaScript ve HTML dosyaları ekleyebilirsiniz, *statik* klasör ancak istediğiniz. Statik dosyaları düzenlemek için normal bir şekilde adlandırılmış alt klasörlerde oluşturmaktır *yazı tipleri*, *betikleri*, ve *içeriği* (için stil sayfaları ve diğer dosyaları).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Soru: Nasıl URL değişkenleri ve sorgu parametreleri API'si yapabilirim?

Yanıt: 1-4. adım için yanıt bkz [Soru: nasıl Flask değişken URL rotaları ile çalışma ve sorgu parametreleri?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3. adım: uygulama için bir sayfa ekleyin

Uygulamaya başka bir sayfa ekleme aşağıdaki anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın işaretleme için bir şablon ekleyin.
- Gerekli Flask projenin için yönlendirme ekleme *urls.py* dosya.

Aşağıdaki adımları giriş sayfasından, ilgili sayfada bağlantılara ve "HelloFlask" proje "Hakkında" sayfasında ekleyin:

1. İçinde **Çözüm Gezgini**, sağ **şablonları** klasörüne **Ekle** > **yeni öğe**, seçin**HTML sayfası** öğe şablonu, dosya adı `about.html`seçip **Tamam**.

    > [!Tip]
    > Varsa **yeni öğe** komutu görünmezse **Ekle** menüsünde, böylece Visual Studio hata ayıklama modundan çıkar uygulama durduruldu emin olun.

1. Öğesinin içeriğini değiştirin *about.html* aşağıdaki işaretlemeyle (sizin yerine giriş sayfasına açık bağlantı 3-4. adımda basit bir gezinti):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Uygulamanın açın *views.py* adlı bir işlev eklemek ve dosya `about` şablonu kullanan:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Açık *templates/index.html* dosyasını açıp aşağıdaki hemen içinde satır `<body>` hakkında sayfasına bağlantı için öğe (yeniden, bu bağlantıyı 3-4. adımda bir gezinti çubuğuyla değiştirin):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Kullanarak dosyaları kaydetme **dosya** > **Tümünü Kaydet** basın veya menü komutu **Ctrl**+**Shift** + **S**. (Visual Studio'da proje çalıştıran dosyaları otomatik olarak kaydeder gibi teknik olarak, bu adım gerek yoktur. Bununla birlikte, işte hakkında bilgi edinmek için iyi bir komutu bu kadar!)

1. Sonuçları inceleyin ve sayfalar arasında gezinti denetlemek için projeyi çalıştırın. İşiniz bittiğinde uygulamayı durdurun.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Soru: sayfa işlevinin adını Flask için önemli mi?

Yanıt: Hayır, çünkü bu `@app.route` Flask yanıt oluşturmak için işlev çağrıları URL'leri belirleyen dekoratör. Geliştiriciler genellikle yönlendirmek için işlev adıyla eşleşmesi, ancak böyle bir eşleşen gerekli değildir.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4. adım: bir başlık ve gezinti çubuğu oluşturmak için şablon devralma kullanın

Açık Gezinti bağlantıları her sayfada sahip olmak yerine modern web uygulamaları genellikle bir marka başlığı ve en önemli sayfa bağlantılarının, açılır menüler ve benzeri sağlayan bir gezinti çubuğunu kullanın. Üst bilgi ve gezinti çubuğunda aynı olan tüm sayfalara emin olmak için ancak her sayfası şablonu aynı kodu yinelemek istediğiniz yok. Bunun yerine, tek bir yerde tüm sayfaları ortak parçalarını tanımlamak istersiniz.

Flask'ın şablon oluşturma sisteminin (varsayılan olarak Jinja) belirli öğeleri birden çok şablon tarafından yeniden kullanmak için iki yol sağlar: içerir ve devralma.

- *İçerir* başvurulan şablonun söz dizimini kullanarak belirli bir yerde eklediğiniz diğer sayfası şablonları `{% include <template_path> %}`. Dinamik olarak kod yolu değiştirmek istiyorsanız, bir değişken de kullanabilirsiniz. İçeren bir sayfa gövdesinde genellikle paylaşılan şablondaki sayfasında belirli bir konumda çekmek için kullanılır.

- *Devralma* kullanan `{% extends <template_path> %}` başına sayfa şablonunun üzerine sonra başvuran şablon oluşturur paylaşılan, temel bir şablonu belirtin. Devralma, gezinti çubuğunda bir paylaşılan düzeni tanımlamak için yaygın olarak kullanılır ve başvuran şablonlar yalnızca eklemek veya adlı temel şablon, belirli alanları değiştirmek için uygulamanın sayfaları, diğer yapıları *blokları*.

Her iki durumda da `<template_path>` uygulamanın göreli olan *şablonları* klasörü (`../` veya `./` de izin verilir).

Bir temel şablon betimleyen *blokları* kullanarak `{% block <block_name> %}` ve `{% endblock %}` etiketler. Başvuran bir şablon daha sonra aynı blok ada sahip etiketler kullanılıyorsa, blok içeriği, temel şablon geçersiz kılar.

Aşağıdaki adımlarda, devralma gösterilmektedir:

1. Uygulamanın *şablonları* klasöründe yeni bir HTML dosyası oluşturun (kullanarak **Ekle** > **yeni öğe** bağlam menüsü veya **Ekle**  >  **HTML sayfası**) olarak adlandırılan *layout.html*ve içeriğini biçimlendirme ile değiştirin. Bu şablon "içerik" adlı bir bloğu, tüm bu başvuran sayfalar ihtiyacı değiştirin, içerdiğini görebilirsiniz:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
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

1. Değiştirme *templates/index.html* temel şablona başvurun ve içerik bloğu yok saymak için. Devralma kullanarak, bu şablon basit olacağını görebilirsiniz:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Değiştirme *templates/about.html* ayrıca temel şablona başvurun ve içerik bloğu yok saymak için:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları görmek için sunucu çalıştırın. Sunucunun işiniz bittiğinde kapatın.

    ![Gezinti çubuğunu gösteren çalışan uygulama](media/flask/step03-nav-bar.png)

1. Uygulamaya önemli değişiklikler, tekrar iyi birer olmasıdır [kaynak denetimine değişikliklerinizi işleyin](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Tam bir Flask Web projesi şablonunu kullanma](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Web uygulamasını Azure App Service'e dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Daha fazla özellik denetim akışı gibi Jinja şablonları için bkz: [Jinja Şablon tasarımcısı belgeleri](http://jinja.pocoo.org/docs/2.10/templates) (jinja.pocoo.org)
- Kullanma hakkında bilgi `url_for`, bkz: [url_for](http://flask.pocoo.org/docs/1.0/api/?highlight=url_for#flask.url_for) Flask uygulaması nesnesi belgelerine (flask.pocoo.org) içinde
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
