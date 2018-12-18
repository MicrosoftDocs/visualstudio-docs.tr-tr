---
title: Visual Studio, 5. adım, kimlik doğrulaması Django öğreticide bilgi edinin
titleSuffix: ''
description: Visual Studio projeleri, Django Web projesi şablonları tarafından sağlanan özel kimlik doğrulama özelliklerimiz bağlamında Django temel bilgileri bir kılavuz.
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
ms.openlocfilehash: 77cc7816a1a05e3b6a883416225717679dd5661b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064079"
---
# <a name="step-5-authenticate-users-in-django"></a>5. adım: Django kullanıcıların kimlik doğrulaması

**Önceki adımda: [tam Django Web projesi şablonunu kullanma](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Kimlik doğrulama web apps için ortak bir gereksinimi olduğundan, "Django Web projesi" şablonu temel kimlik doğrulaması akışı içerir. (Bu öğreticinin 6. adımında açıklanan "Yoklamalar Django Web projesi" şablonu da aynı akışı içerir.) Django projesi şablonlardan birini kullanırken, Visual Studio kimlik doğrulaması için gerekli olan tüm modülleri Django projesinin içerir. *settings.py*.

Bu adımda şunları öğrenirsiniz:

> [!div class="checklist"]
> - Visual Studio şablonları sağlanan kimlik doğrulama akışı kullanma (adım 5 - 1)

## <a name="step-5-1-use-the-authentication-flow"></a>5-1. adım: kimlik doğrulaması akışı kullanın

Aşağıdaki adımlar, kimlik doğrulaması akışı alıştırma ve söz konusu olan proje bölümlerini açıklar:

1. Henüz yönergelerini uyguladığınızdan varsa *readme.html* dosyasında bir süper kullanıcı (Yönetici) hesabı oluşturmak, bunu şimdi yapmak için proje kök dizini.

1. Visual Studio kullanarak uygulamayı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**). Uygulama tarayıcıda görüntülenir, mesajının görüntülendiğini görün **oturum** sağ üst kısmındaki gezinti çubuğunda üzerinde görünür.

    ![Django Web projesi uygulama sayfasında oturum açma denetimi](media/django/step05-login-control.png)

1. Açık *templates/app/layout.html* ve mesajının görüntülendiğini görün `<div class="navbar ...>` ögesinin etiketi `{% include app/loginpartial.html %}`. `{% include %}` Etiketi eklenen dosyanın içeriği bu noktada içeren şablondaki sütunlarından Django'nın şablon oluşturma sistemi bildirir.

1. Açık *templates/app/loginpartial.html* ve koşullu etiketi kullanma `{% if user.is_authenticated %}` ile birlikte bir `{% else %}` etiketi olup olmadığını kullanıcı kimliğini doğrulamasından bağlı olarak farklı kullanıcı Arabirimi öğeleri oluşturmak için:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Kullanıcı uygulamayı ilk kez başlattığınızda doğrulandığı Bu şablon kodunu yalnızca "Oturum Aç" bağlantısı "login" göreli yoluna işler. Belirtilmiş *urls.py* (gösterildiği bir önceki bölümdeki), bu rota eşlendiği `django.contrib.auth.views.login` görünümü. Bu görünümü, aşağıdaki verileri alır:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Burada, `template_name` şablon için oturum açma sayfasında, bu durumda tanımlayan *templates/app/login.html*. `extra_context` Özelliği, şablona verilen varsayılan bağlam verileri eklenir. Son olarak, `authentication_form` ile oturum açma bilgilerini kullanmak için bir form sınıf belirtir; şablon olarak görünür `form` nesne. Varsayılan değer `AuthenticationForm` (gelen `django.contrib.auth.views`); Visual Studio Proje şablonu, bunun yerine uygulamanın tanımlanan bir form kullanır *forms.py* dosyası:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Gördüğünüz gibi bu form sınıfın türetildiği `AuthenticationForm` ve özellikle yer tutucu metin eklemek için kullanıcı adı ve parola alanları geçersiz kılar. Visual Studio şablonu bu büyük olasılıkla parola gücü doğrulaması ekleme gibi formunu özelleştirmek istediğiniz varsayımına açık kodu içerir.

1. Gittiğinizde oturum açma sayfasına daha sonra uygulama işler *login.html* şablonu. Değişkenleri `{{ form.username }}` ve `{{ form.password }}` işleme `CharField` gelen forms `BootstrapAuthenticationForm`. Bu hizmetler eklemek isterseniz doğrulama hataları ve sosyal oturum açma bilgileri için kullanıma hazır bir öğe göstermek için yerleşik bir bölüm de mevcuttur.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Formu gönderdiğinde, Django kimlik bilgilerinizi (örneğin, süper kullanıcı kimlik bilgileri) kimlik doğrulama girişiminde bulunur. Kimlik doğrulaması başarısız olursa geçerli sayfadaki kalır ancak `form.errors` true olarak ayarlanmış. Kimlik doğrulaması başarılı olursa, Django "İleri" alanında göreli URL gider `<input type="hidden" name="next" value="/" />`, bu durumda olduğu giriş sayfası (`/`).

1. Şimdi ne zaman giriş sayfası işlenen yeniden `user.is_authenticated` özelliği true olduğunda *loginpartial.html* şablon işlenir. Sonuç olarak, gördüğünüz bir **Hello (kullanıcı adı)** ileti ve **oturumunu**. Kullanabileceğiniz `user.is_authenticated` kimlik doğrulamasını denetlemek için uygulamanın diğer bölümlerinde.

    ![Django Web projesi uygulama sayfasında Hello iletisi ve oturum kapatma denetimi](media/django/step05-logoff-control.png)

1. Kimliği doğrulanmış kullanıcının belirli kaynaklara erişmek için yetkili olup olmadığını denetlemek için veritabanından kullanıcı özel izinleri gerekir. Daha fazla bilgi için [Django kimlik doğrulama sistemini kullanarak](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django belgeleri).

1. Süper kullanıcı veya yönetici, özellikle de "/admin/" göreli URL'ler kullanarak yerleşik Django yönetici arabirimi erişmek için yetkili ve "/ Yönetici/doc /". Bu arabirimler etkinleştirmek için aşağıdakileri yapın:

    1. Ortamınıza docutils Python paketini yükleyin. Bunu yapmak için harika bir "docutils" eklemek için yoludur, *requirements.txt* dosya, ardından **Çözüm Gezgini**, projeyi genişletin, **Python ortamları** düğümünü, ardından bir select kullanmakta olduğunuz ortamın sağ **Requirements.txt'ten Yükle**.

    1. Django projenin açın *urls.py* ve varsayılan açıklamaları aşağıdaki girişlerinden kaldırın:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. Django projenin *settings.py* gidin, dosya `INSTALLED_APPS` koleksiyonu ve ekleme `'django.contrib.admindocs'`.

    1. Uygulamayı yeniden başlattığınızda, "/admin/ için" gidebilir ve "/ Yönetici/doc /" ve ek kullanıcı hesapları oluşturma gibi görevleri gerçekleştirebilir.

        ![Django yönetici arabirimi](media/django/step05-administrator-interface.png)

1. Son bölümü kimlik doğrulaması akışı için oturum kapatma. İçinde gördüğünüz gibi *loginpartial.html*, **oturumunu** bağlantı göreli URL'si basitçe bir POST yapar "/ oturum açma", yerleşik görünüm tarafından işlenen `django.contrib.auth.views.logout`. Bu görünümde herhangi bir kullanıcı Arabirimi göstermez ve yalnızca giriş sayfasına gider (gösterildiği gibi *urls.py* için "^ oturum kapatma$" deseni). Oturum kapatma sayfasını görüntülemek istiyorsanız, önce şu şekilde bir "þablon_adý" özelliğini ekleyin ve "next_page" özelliği kaldırmak için URL deseni değiştirin:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Oluşturup *templates/app/loggedoff.html* (minimum) aşağıdaki içeriğe sahip:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Sonuç aşağıdaki gibi görünür:

    ![Eklenen sayfadan oturum](media/django/step05-logged-off-page.png)

1. Tüm işiniz bittiğinde, sunucunun durdurun ve yeniden kaynak denetimi yaptığınız değişiklikleri kaydedin.

### <a name="question-what-is-the-purpose-of-the--csrftoken--tag-that-appears-in-the-form-elements"></a>Soru: Amacı nedir {% csrf_token %} etiket görünür \<form\> öğeleri?

Yanıt: `{% csrf_token %}` etiketi içeren Django'nın yerleşik [siteler arası istek sahteciliği (csrf) koruma](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django belgeleri). Genellikle, POST, PUT ve DELETE isteği gibi yöntemleri bir form içeren herhangi bir öğeye bu etiketi ekleyin. Şablon işleme işlevi (`render`) sonra gerekli korumayı ekler.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Yoklamalar Django Web projesi şablonu kullanın](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Kullanıcı kimlik doğrulaması Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
