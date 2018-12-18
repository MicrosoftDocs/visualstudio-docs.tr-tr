---
title: Flask Öğreticisi 4. adımda Visual Studio, web projesi şablonları öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle Flask Web projesi ve Webový projekt ve Flask/Jade şablonları tarafından sağlanan özellikleri bağlamında Flask temel bilgileri bir kılavuz.
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
ms.openlocfilehash: c072d1187abf463cc2f185946f7e238bb091a534
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051707"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>4. adım: tam Flask Web projesi şablonunu kullanma

**Önceki adımda: [statik dosyaları sunmak, sayfalar eklemek ve şablonu devralma kullanın](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

"Boş Flask uygulaması projesi" şablonu Visual Studio'da bağlı bir uygulama oluşturarak Flask temelleri incelediniz, "Flask Web projesi" şablon tarafından üretilen irdelemesi uygulamayı kolayca anlayabilir.

Bu, artık. adım:

> [!div class="checklist"]
> - "Flask Web projesi" şablonu kullanarak daha kapsamlı bir Flask web uygulaması oluşturma ve proje yapısını inceleyin (adım 4 - 1)
> - Proje şablonu tarafından oluşturulan taban sayfası şablondan devralır üç sayfası oluşur sayfası şablonları ve görünümleri anlayın ve, jQuery ve önyükleme (4-2. adım) gibi statik JavaScript kitaplıklarını kullanır
> - (4-3. adım) şablonu tarafından sağlanan URL yönlendirmeyi anlama

Bu makalede, "Flask Web projesinin Jade şablon oluşturma altyapısı yerine Jinja kullanarak" aynı olan bir uygulamayı hazırlayan "Webový projekt Flask/Jade" şablonu için de geçerlidir. Ek ayrıntılar bu makalenin sonunda bulunur.

## <a name="step-4-1-create-a-project-from-the-template"></a>4-1. adım: bir şablondan bir proje oluşturma

1. Visual Studio'da Git **Çözüm Gezgini**, sağ **LearningFlask** daha önce Bu öğretici ve seçme içinde oluşturulan çözüm **Ekle**  >   **Yeni proje**. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, seçin **dosya** > **yeni** > **proje** yerine.)

1. Yeni Proje iletişim kutusunda, aramak ve seçmek **Flask Web projesi** şablonu, "FlaskWeb" proje arayın ve seçin **Tamam**.

1. Şablonu yeniden içerdiğinden bir *requirements.txt* dosya, Visual Studio bu bağımlılıkların yükleneceği sorar. Seçeneğini **sanal bir ortama yükleme**hem de **sanal ortama ekleme** iletişim kutusunda **Oluştur** Varsayılanları kabul etmek için.

1. Visual Studio sanal ortamını ayarlama işlemi tamamlandıktan sonra ayarlama **FlaskWeb** proje bu projeye sağ tıklayarak Visual Studio çözümü için varsayılan olarak **Çözüm Gezgini** ve seçme **başlangıç projesi olarak ayarla**. Gösterilen başlangıç projesi içinde hata ayıklayıcısını başlattığınızda nelerin çalıştırılacağını kalın.

    ![Başlangıç projesi olarak FlaskWeb projeyi gösteren Çözüm Gezgini](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Seçin **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** server çalıştırmak için araç çubuğunda:

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/flask/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama hakkında ev ve kişi, hangi gezinti çubuğunda kullanma arasında gezinmek üç sayfa vardır. Bir veya iki uygulamanın farklı kısımlarını incelemek için dakika alın. Uygulamada kimlik doğrulaması yapmak için **oturum** komutu, daha önce oluşturduğunuz süper kullanıcı kimlik bilgilerini kullanın.

    ![Flask Web projesi uygulamasının tam tarayıcı görünümü](media/flask/step04-full-app-desktop-view.png)

1. "Flask Web projesi" şablonu ile oluşturulan uygulama için mobil form faktörleri kapsar esnek Düzen önyükleme kullanır. Bu yanıt verdiğini görmek için bir dar görünüm tarayıcıya dikey olarak içerik işler ve gezinti çubuğunda bir menü simgesine dönüşür şekilde boyutlandırın:

    ![Flask Web projesi uygulamasının mobil (dar) görünümü](media/flask/step04-full-app-mobile-view.png)

1. İzleyen bölümlerde için uygulamayı bırakabilirsiniz.

    Uygulamayı durdurmak istiyorsanız ve [değişiklikleri kaynak denetimine](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), ilk açın **değişiklikleri** sayfasını **Takım Gezgini**, sanal ortam (klasörünü sağ tıklatın büyük olasılıkla **env**) seçip **bu yerel öğeleri Yoksay**.

### <a name="examine-what-the-template-creates"></a>Hangi şablon oluşturur inceleyin

"Flask Web projesi" şablon aşağıdaki yapısı oluşturur. İçeriği, önceki adımlarda oluşturduğunuz için oldukça benzerdir. "Flask Web projesi" şablonu daha fazla yapı içerdiği fark *statik* klasörü, jQuery ve Bootstrap için esnek tasarım çünkü içerir. Şablon ayrıca bir ilgili kişi sayfası ekler. Bu öğreticide, önceki adımları izlediğinizden, genel olarak, şablondan her şeyi tanımanız gerekir.

- Proje kökündeki dosyaları:
  - *runserver.PY*, uygulamayı bir geliştirme Sunucusu'nda çalıştırılacak bir komut dosyası.
  - *Requirements.txt* Flask bağımlılık içeren 0.x.
- *FlaskWeb* klasörü tüm uygulama dosyalarını içerir:
  - *\_\_init.PY\_ \_*  uygulama kodu bir Python modülü olarak işaretler, Flask nesnesi oluşturur ve uygulamanın görünümleri alır.
  - *Views.PY* sayfaları işlemek için kod içerir.
  - *Statik* adlı alt klasörde *içeriği* (CSS dosyaları) *yazı tipleri* (yazı tipi dosyaları) ve *betikleri* (JavaScript dosyaları).
  - *Şablonları* klasörünü içeren bir *layout.html* ile birlikte temel şablon *about.html*, *contact.html*, ve  *index.HTML* için belirli bir sayfa her genişletme *layout.html*.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasındaki bir sanal ortam paylaşmayı mümkün mü?

Cevap: Evet, ancak büyük olasılıkla farklı projelerde zaman içinde farklı paketleri kullanın ve bu nedenle, paylaşılan bir sanal ortam bunu kullanan tüm projeler için tüm paketleri içermelidir tanıma ile bunu.

Bununla birlikte, mevcut bir sanal ortam kullanmak için aşağıdakileri yapın:

1. Visual Studio'da bağımlılıkları yüklemek isteyip istemediğiniz sorulduğunda seçin **ben bunları kendim yükler** seçeneği.
1. İçinde **Çözüm Gezgini**, sağ **Python ortamları** düğümünü seçip alt **var olan sanal ortama ekleme**.
1. Gidin ve sanal ortam içeren klasörü seçin ve ardından **Tamam**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>4-2. adım: görünümleri anlayın ve sayfa proje şablonu tarafından oluşturulan şablonlar

Projeyi çalıştırdığınızda gözlemleyin gibi uygulamayı üç görünüm içerir: hakkında ev ve başvurun. Bu görünümler için kod bulunan *FlaskWeb/views.py*. Her görünüm işlevi yalnızca çağırır `flask.render_template` yoluyla bir şablon ve şablona vermek için değerleri için bağımsız değişken listesi. Örneğin, hakkında sayfası tarafından işlenir `about` işlevi (olan dekoratör URL yönlendirmeyi sağlar):

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` Ve `contact` işlevlerdir benzer dekoratörler ve biraz farklı bağımsız değişkenler ile neredeyse aynı.

Şablonlar, uygulamanın bulunur *şablonları* klasör. Temel şablon *layout.html*, en kapsamlı olduğundan. Bu, tüm gerekli statik dosyaları (JavaScript ve CSS) gösterir, diğer geçersiz kılma sayfaları ve "betik" adlı başka bir bloğu sağlar "içerik" adlı bir bloğu tanımlar. Aşağıdaki parçalarını açıklamalı *layout.html* bu belirli alanları göster:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Webový projekt ve Flask/Jade şablonu

Bu makalenin başında belirtildiği gibi Visual Studio "Flask Web projesi" tarafından üretilen için görsel olarak aynı olan bir uygulama oluşturur bir "Webový projekt Flask/Jade" şablonu sağlar. Dekinden daha birleştiren bir dil ile aynı kavramlar uygulayan Jinja uzantısıdır Jade şablon oluşturma altyapısı kullanmasıdır. Özellikle, içine etiketleri yerine anahtar sözcükler Jade kullanan {ayıklaması sınırlayıcıları, örneğin ve CSS stilleri ve anahtar sözcükleri kullanarak HTML öğeleri için başvuru sağlar.

Jade etkinleştirmek için proje şablonu ilk pyjade paketine ekler *requirements.txt*. 

Uygulamanın  *\_ \_init\_\_.py* dosyası için bir satır içerir

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```
İçinde *şablonları* klasöründe gördüğünüz *.jade* yerine dosyaları *.html* şablonları ve görünümlerde *views.py* bu dosyalara başvurmanız kendi çağrıları `flask.render_template`. Aksi takdirde görünümleri kod aynıdır.

Aşağıdakilerden birini açma *.jade* dosyaları daha Sözün ifadesi bir şablonun görebilirsiniz. Örneğin, içeriği işte *templates/layout.jade* "Webový projekt Flask/Jade" şablon tarafından oluşturulan:

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

Ve işte içeriğini *templates/about.jade*, kullanımını gösteren `#{ <name>}` yer tutucu:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Jinja ve Jade sözdizimleri hangisinin sizin için en uygun görmek için denemeler çekinmeyin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Polls – Flask Web projesi şablonu](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [İlk Flask uygulamanızı yazmak, Bölüm 4 - formlar ve görünümler genel](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade GitHib (belgeler) üzerinde](https://github.com/liuliqiang/pyjade) (github.com)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
