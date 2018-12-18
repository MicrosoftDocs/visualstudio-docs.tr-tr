---
title: Django Öğreticisi 2. adımda Visual Studio, görünümleri ve şablonların öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle bir uygulama oluşturma ve görünümleri ve şablonlar kullanma adımları bağlamında Django temel bilgileri bir kılavuz.
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
ms.openlocfilehash: dade4ee20aec654a32fac6904cca121c2ea726e6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058551"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2. adım: görünümleri ve şablonların bir Django uygulaması oluşturma

**Önceki adımda: [Visual Studio'nun proje ve çözüm oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Şu ana kadar Visual Studio projesini bileşenleridir yalnızca site düzeyi bir Django sahip olduğunuz *proje*, bir veya daha fazla Django çalıştırabilirsiniz *uygulamaları*. Sonraki adım, ilk uygulamanızı tek bir sayfayla oluşturmaktır.

Bu adımda, daha fazla bilgi için nasıl:

> [!div class="checklist"]
> - Tek bir sayfayla bir Django uygulaması oluşturma (Adım 2 - 1)
> - Django projesi (Adım 2-2) uygulamayı çalıştırma
> - HTML (Adım 2-3) kullanarak görünüm işlemek
> - Django sayfası şablonu (Adım 2-4) kullanarak görünüm işlemek

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>2-1. adım: bir varsayılan yapı ile uygulama oluşturma

Bir Django uygulaması belirli bir amaç için ilgili dosyaları içeren ayrı bir Python paketidir. Django projesi yansıtan bir web ana bilgisayarı bir tek etki alanı adı ayrı giriş noktalarından herhangi bir sayıda verebilen olgu herhangi bir sayıda uygulamaları içerebilir. Örneğin, www.contoso.com için tek bir uygulama, support.contoso.com için ikinci bir uygulama ve docs.contoso.com için üçüncü bir uygulama bir Django projesi için bir etki alanı contoso.com gibi içerebilir. Bu durumda, Django projesi site düzeyinde URL Yönlendirme ve ayarları işler (içinde kendi *urls.py* ve *settings.py* dosyaları), her uygulama kendi ayrı stil ve iç aracılığıyla davranışını varken Yönlendirme, görünümler, modelleri, statik dosyalar ve yönetim arabirimi.

Bir Django uygulaması genellikle standart bir dosya kümesi ile başlar. Visual Studio öğe şablonları aynı amaca hizmet eder bir tümleşik menü komutu ile birlikte bir Django projesi içinde bir Django uygulaması başlatılamadı sağlar:

- : Şablonları **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Django 1.9 uygulama** şablon, uygulama adı belirtin **adı** alan ve seçim **Tamam**.

- Tümleşik komut: içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **Django uygulaması**. Bu komut için bir ad ister ve Django 1.9 uygulaması oluşturur.

    ![Bir Django uygulaması eklemek için menü komutu](media/django/step02-add-django-app-command.png)

Her iki yöntemi kullanarak, "HelloDjangoApp" adı ile bir uygulama oluşturun. Sonuç, aşağıdaki tabloda açıklanan öğeleri içeren bu ada sahip, projenizdeki bir klasördür.

![Çözüm Gezgini'nde Django uygulama dosyaları](media/django/step02-django-app-in-solution-explorer.png)

| Öğe | Açıklama |
| --- | --- |
| **\_\_init\_\_.py** | Uygulamayı bir paket olarak tanımlayan dosya. |
| **Geçişleri** | Django ile hizalamak için veritabanını güncelleştiren komut dosyaları depolayan bir klasör için modelleri değiştirir. Geçerli modelleri eşleşmesi Django'nın Geçiş Araçları veritabanının önceki bir sürümüne sonra gerekli değişiklikleri uygulayın. Modellerinizi üzerinde odaklanma tutun migrations'ı kullanma ve temel alınan veritabanı şemasını işlemek Django olanak tanır. Geçişler, 6. adımda ele alınmıştır; şimdilik yalnızca klasörü içeren bir  *\_ \_init\_\_.py* dosyası (klasörü kendi Python paketini tanımlar gösterir). |
| **Şablonları** | Django sayfası şablonlarını içeren tek bir dosya için bir klasör *index.html* uygulama adıyla eşleşen bir klasör içinde. (Visual Studio 2017 15.7 ve önceki sürümlerinde, dosyanın doğrudan altında bulunan *şablonları* ve adım 2-4 bildirir, bir alt klasör oluşturun.) İçine bir sayfayı dinamik olarak oluşturmak için bilgi görünümleri ekleyebilirsiniz HTML bloklarını şablonlardır. Şablon "değişkenler," gibi sayfa `{{ content }}` içinde *index.html*, bu makalenin ilerleyen bölümlerinde (2. adım) açıklandığı gibi dinamik değerler için yer tutucular olan. Genellikle Django uygulamaları, uygulama adıyla eşleşen bir alt klasöre yerleştirerek, şablon için bir ad alanı oluşturun. |
| **Admin.PY** | Uygulamayı genişletmek Python dosyası yönetim arabirimi (6. adıma bakın), temel ve bir veritabanındaki verileri düzenlemek için kullanılır. Başlangıçta, bu dosya yalnızca deyimi içerir `from django.contrib import admin`. Varsayılan olarak, Django Django projesinin girişleri aracılığıyla standart bir yönetim arabirimi içerir *settings.py* uncommenting mevcut girişlere göre açabilirsiniz dosyasını *urls.py*. |
| **Apps.PY** | (Bu tablodan sonraki, aşağıya bakın) uygulaması için bir yapılandırma sınıfı tanımlayan bir Python dosyası. |
| **models.PY** | Veri nesneleri, işlevleri, görünümleri uygulamanın temel veritabanıyla etkileşim tarafından tanımlanan modelleridir (6. adıma bakın). Django veritabanı bağlantı katmanı sağladığından uygulamalar kendilerini bu ayrıntılarla ilgilendiriyor gerekmez. *Models.py* dosya bir varsayılan Modellerinizi oluşturulacağı yerdir ve başlangıçta yalnızca deyimi içeren `from django.db import models`. |
| **Tests.PY** | Temel yapısını birim testleri içeren bir Python dosyası. |
| **Views.PY** | Genellikle, web bir HTTP isteğini alıp bir HTTP yanıt sayfaları düşüncelerinizi görünümleridir. Görünümleri genellikle web tarayıcıları nasıl görüntüleneceğini bildiğiniz HTML olarak işlemenizi, ancak bir görünüm mutlaka (Ara formu gibi) görünür olmak zorunda değildir. Bir görünümü olan sorumluluğundadır tarayıcıya göndermek için HTML oluşturmak için bir Python işlevi tarafından tanımlanır. *Views.py* dosya bir varsayılan görünüm oluşturulacağı yerdir ve başlangıçta yalnızca deyimi içeren `from django.shortcuts import render`. |

İçeriğini *app.py* adı "HelloDjangoApp" kullanırken aşağıdaki gibi görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Soru: bir Django uygulaması Visual Studio'da uygulama oluşturma komut satırında yapılan çağrılardan farklı oluşturuyor?

Yanıt: Çalışan **Ekle** > **Django uygulaması** komut veya kullanarak **Ekle** > **yeni öğe** bir Django uygulaması Şablon ile aynı Django komut dosyaları üretir `manage.py startapp <app_name>`. Visual Studio'da uygulama oluşturmanın avantajı, uygulama klasörü ve tüm dosyalar projeye otomatik olarak tümleştirilir içindir. Aynı Visual Studio komut, projenizdeki herhangi bir sayıda uygulamaları oluşturmak için kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>2-2. adım: uygulamayı Django projeden çalıştırın

Visual Studio'da proje yeniden çalıştırmanız gerekirse bu noktada (araç çubuğu düğmesini kullanarak veya **hata ayıklama** > **hata ayıklamayı Başlat**), yine de varsayılan sayfayı görürsünüz. Bir uygulamaya özgü sayfa tanımlama ve uygulama Django projeye eklemek gerektiği için hiçbir uygulama içeriği görünür:

1. İçinde *HelloDjangoApp* klasörü Değiştir *views.py* aşağıdaki, "Index" adlı bir görünümü tanımlayan kodu eşleştirmek için:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. İçinde *BasicProject* (oluşturulmuş 1. adım), klasör değiştirme *urls.py* en az (tutabilirsiniz yönergeli açıklamaları isterseniz) aşağıdaki kodu eşleştirmek için:

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Belirli bir site göreli URL'ler için hangi Django yönlendirir görünümleri her URL deseni açıklar (diğer bir deyişle, aşağıdaki bölümü `https://www.domain.com/`). İlk giriş `urlPatterns` , normal ifade ile başlayan `^$` site kökü için yönlendirme "/". İkinci girdi `^home$` özellikle yönlendiren "/ home". Herhangi bir sayıda üretim aynı görünüme sahip olabilir.

1. İleti yeniden görmek için projenizi çalıştırarak **Merhaba, Django!** Görünümü tarafından tanımlandığı şekilde. İşiniz bittiğinde, sunucunun durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuzda değişiklikler yaptık ve başarıyla sınanmıştır olduğundan, kaynak denetimine yaptığınız değişiklikleri kaydedin ve gözden geçirmek için harika bir zaman sunulmuştur. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden kaydetmeye uygun sürelerinin anımsatmak ve tekrar bu bölüme bakın.

1. Gider değişiklikleri düğmesi (aşağıda daire içinde) Visual Studio alt taraftaki seçin **Takım Gezgini**.

    ![Visual Studio durum çubuğunda kaynak denetim değişikliklerini düğmesine](media/django/step02-source-control-changes-button.png)

1. İçinde **Takım Gezgini**"ilk Django uygulaması oluşturma gibi" bir işleme iletisi girin ve seçin **tümünü işle**. İşleme tamamlandığında, bir ileti görürsünüz **işleme \<karma > yerel olarak oluşturuldu. Değişikliklerinizi sunucuyla paylaşmak için Eşitleme'yi tıklatın.** Değişiklikleri uzak depoya itme isteyip istemediğinizi seçin **eşitleme**, ardından **anında iletme** altında **giden işlemeler**. Ayrıca, uzak göndermeden önce birden çok yerel işlemeleri birikebilir.

    ![Uzak Ekip Gezgini'nde yürütmeler gönderin](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Soru: Yönlendirme dizeleri için önce 'r' öneki nedir?

Yanıt: 'R' ön ek Python dizesinde "ham", dize içindeki herhangi bir karakter kaçış değil Python bildirir anlamına gelir. Normal ifadeler çok sayıda özel karakterler kullanmak için 'r' öneki kullanarak bu dizelerin içeriyorsa, bir dizi değerinden okumak kolaylaştırır '\\' kaçış karakterleri.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Soru: Neler ^ ve $ karakterlerini, URL yönlendirme girişleri anlamına gelir?

Yanıt: URL desenleri tanımlayan normal ifadelerde ^ "satırın" anlamına gelir ve $, "yeniden URL'leri olduğu site köküne göreli satırın sonuna" anlamına gelir (aşağıdaki bölümü `https://www.domain.com/`). Normal ifade `^$` etkili bir şekilde anlamına gelir "blank" ve bu nedenle tam URL ile eşleşen `https://www.domain.com/` (hiçbir şey site köküne eklenen). Desen `^home$` tam olarak eşleşen `https://www.domain.com/home/`. (Django kullanmaz sondaki / desen eşleştirme.)

Sonunda $ bir normal ifadede kullanmıyorsanız, olduğu gibi `^home`, URL deseni ile eşleşen sonra *herhangi* "home", "Ev ödevleri", "yerimizle" ve "home192837" gibi "home" ile başlayan URL.

Deneyin gibi çevrimiçi araçları farklı normal ifadeleriyle denemeler yapmak için [regex101.com](https://regex101.com) adresindeki [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>2-3. adım: HTML kullanarak görünüm işlemek

`index` Şu ana kadar sahip olduğunuz işlevi *views.py* sayfası için bir düz metin HTTP yanıt başka bir şey oluşturur. Çoğu gerçek web sayfaları, doğal olarak, genellikle canlı verileri bir araya getiren zengin HTML sayfaları ile yanıt verir. İçeriği dinamik olarak oluşturmak için gerçekten bir işlevi kullanarak bir görünüm tanımlamak için birincil nedenidir.

Çünkü bağımsız değişkeni `HttpResponse` yalnızca bir dize ise, bir dize içinde istediğiniz herhangi bir HTML'kurmak oluşturabilirsiniz. Basit bir örnek olarak, değiştirin `index` işlevini aşağıdaki kodla (varolan tutma `from` deyimleri), sayfayı yenileyin her zaman, güncelleştirilen dinamik içerik kullanarak bir HTML yanıtını oluşturur:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Gibi bir ileti yeniden görmek için projeyi Çalıştır "**Django Merhaba!** Pazartesi, 16 Nisan 2018 16:28:10 üzerinde ". Güncelleştirme zamanı ve içeriğin her bir istekle üretiliyor onaylamak için sayfayı yenileyin. İşiniz bittiğinde, sunucunun durdurun.

> [!Tip]
> Bir kısayolu project durdurup kullanmaktır **hata ayıklama** > **yeniden** menü komutu (**Ctrl**+**kaydırma**  + **F5**) veya **yeniden** hata ayıklama araç çubuğu düğmesi:
>
> ![Visual Studio'da hata ayıklama araç çubuğundan yeniden başlatın](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>2-4. adım: bir sayfası şablonu kullanarak görünüm işlemek

HTML kod oluşturma için çok küçük sayfaları düzgün çalışır, ancak sayfaları daha karmaşık hale geldikçe genellikle "sayfa şablonları, ardından eklediğiniz" sayfanızın (birlikte, CSS ve JavaScript dosyalarına yapılan başvurular) statik HTML parçaları dinamik korumak istediğiniz kod tarafından oluşturulan içerikleri. Önceki bölümde, yalnızca tarih ve saat `now.strftime` çağrıdır dinamik, diğer tüm içerik sayfası şablonunda yerleştirilebileceğini anlamına gelir.

Django sayfası şablonu tarafından makaleyle "değişkenler" adı verilen değiştirme belirteçlerin herhangi bir sayı içeren HTML bloğudur `{{` ve `}}`, olarak `{{ content }}`. Django'nın şablon oluşturma modülü kodda sağlayan dinamik içerik değişkenleri sonra değiştirir.

Aşağıdaki adımlarda, şablonların kullanımı gösterilmektedir:

1. Altında *BasicProject* Django projeyi içeren klasörü açın *settings.py* dosya ve uygulama adı, "HelloDjangoApp" ekleyin `INSTALLED_APPS` listesi. Listeye uygulama ekleme, Django projesi içeren bir uygulama bu ada sahip bir klasör olduğunu bildirir:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Ayrıca *settings.py*, emin olun `TEMPLATES` nesnesini içeren yüklü bir uygulamanın şablonlarında aramak için Django bildirir (varsayılan olarak dahil), aşağıdaki satır *şablonları* klasörü:

    ```json
    'APP_DIRS': True,
    ```

1. İçinde *HelloDjangoApp* açık klasör *templates/HelloDjangoApp/index.html* sayfa şablon dosyası (veya *templates/index.html* VS 2017 15.7 ve önceki sürümler), tek bir değişken içeren gözlemleyin `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. İçinde *HelloDjangoApp* açık klasör *views.py* değiştirin `index` işlevi kullanan aşağıdaki kodla `django.shortcuts.render` yardımcı işlevi. `render` Yardımcısı sayfasında şablonları ile çalışma için basitleştirilmiş bir arabirim sağlar. Var olan tüm tuttuğunuzdan emin olun `from` deyimleri.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    İlk bağımsız değişkeni `render`görebileceğiniz gibi uygulamanın içinde şablon dosyasına göreli yol tarafından izlenen istek nesnesi *şablonları* klasör. Bir şablon dosyası destekliyorsa, görünüm için uygun olarak adlandırılır. Üçüncü bağımsız değişkeni `render` şablon başvurduğu değişkenlerin bir sözlük ise. Sözlükte nesneleri içerir, bu şablon bir değişkende durumda başvurabilir `{{ object.property }}`.

1. Projeyi çalıştırın ve çıktıyı gözlemleyin. Şablon çalıştığını gösteren adım 2-2 görülen benzer bir ileti görmeniz gerekir.

    Ancak, HTML olarak kullandığınız gözlemleyin `content` özelliği, çünkü yalnızca düz metin olarak işler `render` işlevi otomatik olarak bu HTML atlar. Kaçış otomatik ekleme saldırılarına karşı yanlışlıkla güvenlik açıklarını önlemeye: geliştiriciler genellikle bir sayfadan giriş toplayın ve şablon yer tutucu aracılığıyla başka bir değer olarak kullanın. Kaçış Ayrıca, yeniden HTML sayfası şablonu ve kodunun dışında tutmak en iyi olduğunu anımsatıcı işlevi görür. Neyse ki, bu ek değişkenleri oluşturmak üzere basit ayıklamadır gerektiğinde. Örneğin, değiştirme *index.html* ile *şablonları* sayfa başlığı ve tutar sayfa şablonunun tüm biçimlendirme ekler aşağıdaki biçimlendirme eşleştirmek için:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Ardından yazma `index` işlevi sayfa şablonundaki tüm değişkenlerin değerlerini sağlamak için aşağıdaki gibi görüntüleyin:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Sunucusunu durdurmak ve projeyi yeniden başlatın ve sayfa artık doğru şekilde işlediğinden inceleyin:

    ![Şablon kullanarak çalışan uygulama](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15.7 ve önceki: son adım olarak, bir ad alanı oluşturur ve projeye eklemek diğer uygulamalarla olası çakışmaları ortadan kaldırır, uygulama, aynı adlı bir alt klasör içine şablonlarınızı taşıyın. (VS 2017'de 15,8 + şablonlarında sizin için otomatik olarak bunu.) Diğer bir deyişle, bir alt klasöre oluşturma *şablonları* adlı *HelloDjangoApp*, taşıma *index.html* o alt klasörü içine ve değiştirme `index` görüntülemek başvurmak için işlevi Şablonun yeni yolu *HelloDjangoApp/index.html*. Ardından projeyi çalıştırın, sayfanın düzgün bir şekilde oluşturulduğunu doğrulayın ve sunucuyu durdur.

1. Kaynak denetimi ve uzak deponuz isterseniz altında açıklandığı gibi güncelleştirmek için değişikliklerinizi işleyin [2 2. adım](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: şablonların ayrı bir dosyada olmam gerekir mi?

Yanıt: şablonları genellikle ayrı HTML dosyalarında korunsa de satır içi şablonu kullanabilirsiniz. Ayrı bir dosya kullanarak, ancak işaretleme ve kod arasında NET bir ayrım sağlamak için önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: şablonları .html dosya uzantısını kullanmalıdır?

Yanıt: *.html* sayfa şablon dosyaları için uzantısıdır tamamen isteğe bağlı ikinci bağımsız değişkeni dosyasında tam göreli yolunu her zaman belirttikleri `render` işlevi. Ancak, Visual Studio (ve diğer Düzenleyiciler) genellikle kod tamamlama ve sözdizimi coloration ile gibi özellikler size *.html* şablonları sayfasında olgu ağır dosyaları olmayan kesinlikle HTML.

Aslında, Django projesi ile çalışırken, Visual Studio otomatik olarak düzenlediğiniz HTML dosyası aslında bir Django şablonudur algılar ve bazı otomatik tamamlama özellikleri sağlar. Örneğin, başlattığınızda bir Django sayfası şablonu yorum yazmak `{#`, Visual Studio otomatik olarak size kapatma `#}` karakter. **Yorum seçimi** ve **seçimi işletilir satıra çevir** komutları (üzerinde **Düzenle** > **Gelişmiş** menü ve araç çubuğundaki) Ayrıca şablon açıklamaları yerine HTML Yorumlarını kullanın.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: Proje çalıştırabilir, şablon bulunamayan bir hata görüyorum. Ne oldu?

Yanıt: şablon bulunamıyor hatalar görürseniz, Django proje için uygulama eklediğinizden emin olun *settings.py* içinde `INSTALLED_APPS` listesi. Bu giriş olmadan uygulamanın aramak için Django bilemezsiniz *şablonları* klasör.

### <a name="question-why-is-template-namespacing-important"></a>Soru: Şablon namespacing neden önemlidir?

Yanıt: Başvurulan bir şablon için Django göründüğünde `render` işlevi, göreli yol ile eşleşen bulduğu ilk ne olursa olsun dosyasını kullanır. Aynı klasör yapılarını için şablonları kullanın. aynı projede birden fazla Django uygulamaları varsa, tek bir uygulama, yanlışlıkla başka bir uygulamadan şablon kullanacağınız olasıdır. Bu tür hataları önlemek için her zaman uygulamanın altında bir alt klasör oluşturun *şablonları* tüm yinelemeyi önlemek üzere bir uygulama adıyla eşleşen bir klasör.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları işleme, sayfalar eklemek ve şablonu devralma kullanın](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Django uygulamanız yazma, bölüm 1 - görünümleri](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Daha fazla Django şablonları, örneğin içerir ve özellikleri devralma için bkz: [Django şablonu dil](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Normal ifade eğitimle inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
