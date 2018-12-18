---
title: Öğrenin Flask Öğreticisi 2. adımda Visual Studio, görünümleri ve şablonları
titleSuffix: ''
description: Visual Studio projeleri, özellikle bir uygulama oluşturma ve görünümleri ve şablonlar kullanma adımları bağlamında Flask temel bilgileri bir kılavuz.
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
ms.openlocfilehash: cbdf9232bdff56fa2d244f8baeed2d070dcb37a9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052951"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Adım 2: görünümler ve sayfa şablonları ile bir Flask uygulaması oluşturma

**Önceki adımda: [Visual Studio'nun proje ve çözüm oluşturma](learn-flask-visual-studio-step-01-project-solution.md)**

Bu öğreticinin 1 adımdaki sahip bir sayfa ve tek bir dosyada tüm kodu ile bir Flask uygulaması olur. Gelecekteki geliştirme için izin vermek için kodu yeniden düzenleyin ve şablonların için bir yapı oluşturmak idealdir. Özellikle, kod uygulamanın görünümler için başlangıç kodu gibi diğer yönlerini ayırmak istiyorsunuz.

Bu adımda, daha fazla bilgi için nasıl:

> [!div class="checklist"]
> - Görünüm başlangıç koddan ayırmak için uygulamanın kodu yeniden düzenleme (Adım 2 - 1)
> - (Adım 2-2) sayfa şablon kullanarak görünüm işlemek

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>2-1. adım: daha fazla geliştirme desteği için projeyi yeniden düzenleyin

"Boş Flask Web projesi" şablonu tarafından oluşturulan kodda, tek bir sahip *app.py* başlatma kodunu tek bir görünümde yanı sıra içeren dosya. Daha fazla birden çok görünüm ve şablonlar ile bir uygulama geliştirmek için izin vermek için bu sorunlar ayırmak idealdir.

1. Proje klasörünüzdeki adlı bir uygulama klasör oluşturma `HelloFlask` ('nde projeye sağ **Çözüm Gezgini** seçip **Ekle** > **yeni klasör** .)

2. İçinde *HelloFlask* klasöründe adlı bir dosya oluşturun  *\_ \_init\_\_.py* oluşturan aşağıdaki içeriklerle `Flask` örnek ve uygulamanın görünümleri (sonraki adımda oluşturulan) yükler:

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. İçinde *HelloFlask* klasöründe adlı bir dosya oluşturun *views.py* aşağıdaki içeriğe sahip. Adı *views.py* önemlidir, çünkü kullandığınız `import HelloFlask.views` içinde  *\_ \_init\_\_.py*; çalışma zamanında bir hata görürsünüz adları eşleşmiyor.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Rotaya ve işlevi yeniden adlandırma yanı sıra `home`, bu kod sayfası işleme kodunu *app.py* ve içeri aktarır `app` bölümünde bildirilen nesne  *\_ \_init\_\_.py*.

4. Bir alt klasöre oluşturma *HelloFlask* adlı *şablonları*, hangi kalan boş şimdilik.

5. Projenin kök klasöründe, yeniden adlandırma *app.py* için *runserver.py*ve aşağıdaki kodu eşleşen içeriği yapın:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```
6. Proje yapısı aşağıdaki gibi görünmelidir:

    ![Kodu yeniden düzenlemeye sonra proje yapısı](media/flask/step02-project-structure.png)

7. Seçin **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** (Mayıs gördüğünüz tarayıcısı araç çubuğu düğmesi bir tarayıcı açın ve uygulamayı başlatmak için değişir). Her iki / ve/URL rotaları giriş.

8. Ayrıca, çeşitli bölümlerini kod kesme noktaları ayarlayın ve başlatma sırası izlemek için uygulamayı yeniden başlatın. Örneğin, ilk satır üzerinde bir kesme noktası ayarlamak *runserver.py* ve *HelloFlask\_* init_*.py*ve `return "Hello Flask!"` satırında*views.py*. Sonra uygulamayı yeniden başlatın (**hata ayıklama** > **yeniden**, **Ctrl**+**F5**, ya da aşağıda gösterilen araç çubuğu düğmesi) ve adım adım (**F10**) her bir kesme noktası kullanarak çalıştırın veya kod **F5**.

    ![Visual Studio'da hata ayıklama araç çubuğundan yeniden başlatın](media/debugging-restart-toolbar-button.png)

9. İşiniz bittiğinde uygulamayı durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuzda değişiklikler yaptık ve başarıyla sınanmıştır olduğundan, kaynak denetimine yaptığınız değişiklikleri kaydedin ve gözden geçirmek için harika bir zaman sunulmuştur. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden kaydetmeye uygun sürelerinin anımsatmak ve tekrar bu bölüme bakın.

1. Gider değişiklikleri düğmesi (aşağıda daire içinde) Visual Studio alt taraftaki seçin **Takım Gezgini**.

    ![Visual Studio durum çubuğunda kaynak denetim değişikliklerini düğmesine](media/flask/step02-source-control-changes-button.png)

1. İçinde **Takım Gezgini**, "Yeniden düzenleme kod" gibi bir işleme iletisi girin ve seçin **tümünü işle**. İşleme tamamlandığında, bir ileti görürsünüz **işleme \<karma > yerel olarak oluşturuldu. Değişikliklerinizi sunucuyla paylaşmak için Eşitleme'yi tıklatın.** Değişiklikleri uzak depoya itme isteyip istemediğinizi seçin **eşitleme**, ardından **anında iletme** altında **giden işlemeler**. Ayrıca, uzak göndermeden önce birden çok yerel işlemeleri birikebilir.

    ![Uzak Ekip Gezgini'nde yürütmeler gönderin](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Soru: Ne sıklıkta bir kaynak denetimine işlemesi gerektiğini?

Yanıt: yaptığınız değişiklikler kaynak denetimine bir kayıt bir nokta ve değişiklik günlüğü oluşturur için hangi depoyu gerekirse geri alabilirsiniz. Her işleme için belirli değişiklikleri de incelenebilir. Git işlemeleri pahalı olduğundan, işleme, çok sayıda değişiklikleri tek bir yürütme içine accumulate üzere daha sık kullanılan daha iyidir. NET bir şekilde, tek tek dosyalar her küçük değişiklik yapmanız gerekmez. Tipik bir işleme bir özellik eklerken bu adımda gerçekleştirilen veya bazı kodu yeniden düzenleme bitti gibi bir yapıyı değiştirme yapmanız gerekir. Ayrıca diğer kullanıcılarla takımınız ayrıntı düzeyi için en iyi herkes için işleme inceleyin.

Ne sıklıkta yürüttükten ve iki farklı kaygıları olan ne sıklıkta işlemeler bir uzak depoya gönderin. Uzak depoya göndermeden önce yerel deponuzda birden çok işleme birikebilir. Yeniden yürütme ne sıklıkta nasıl takımınızın depo yönetmek ister şirket bağlıdır.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>2-2. adım: bir sayfayı oluşturmak için şablon kullanma

`home` Şu ana kadar sahip olduğunuz işlevi *views.py* sayfası için bir düz metin HTTP yanıt başka bir şey oluşturur. Ancak, çoğu gerçek web sayfaları, genellikle canlı verileri bir araya getiren zengin HTML sayfaları ile yanıt. Aslında, bir işlevi kullanarak bir görünüm tanımlamak için birincil içerik dinamik olarak oluşturmak için nedenidir.

Görünüm için dönüş değeri bir dize olduğundan, dinamik içerik kullanarak bir dize içinde istediğiniz herhangi bir HTML oluşturabilirsiniz. Ancak, biçimlendirme verilerden ayırmak en iyi olduğu için bir şablonunda biçimlendirmeyi yerleştirin ve kodda verileri tutmak çok daha iyi.

1. Yeni başlayanlar için Düzenle *views.py* satır içi HTML sayfası dinamik içerikler için kullandığı aşağıdaki kodu içerecek:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Uygulamayı çalıştırın ve sayfayı yenileyin birkaç kez tarih/zaman güncelleştirildiğini görmek için. İşiniz bittiğinde uygulamayı durdurun.

1. Bir şablon kullanmak üzere sayfa işleme dönüştürmek için adlı bir dosya oluşturun *index.html* içinde *şablonları* klasöründe aşağıdaki içeriğe sahip olduğu `{{ content }}` bir yer tutucu veya değiştirme (aynı zamanda belirteci adlı bir *Şablon değişkeni*) bir değer kodda sağladığınız:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Değiştirme `home` işlevi kullanmak için `render_template` şablonu yüklemek ve yapılır "içerik" için bir değer sağlamak için yer tutucu adıyla eşleşen bir adlandırılmış bağımsız değişkenini kullanarak. Flask otomatik olarak arar şablonlarında *şablonları* bu klasörüyle ilgili yol şablonu için bu nedenle klasörü:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Bkz: uygulamayı çalıştırma sonuçları ve mesajının görüntülendiğini görün içinde satır içi HTML `content` değil değerini işlemek *olarak* HTML şablon oluşturma altyapısı olduğundan (Jinja) otomatik olarak çıkışları HTML içeriği. Otomatik kaçış yanlışlıkla güvenlik açıklarını ekleme saldırılarına karşı engeller: geliştiriciler genellikle bir sayfadan giriş toplayın ve şablon yer tutucu aracılığıyla başka bir değer olarak kullanın. Kaçış Ayrıca, yeniden HTML kodu dışında tutmak en iyi olduğunu anımsatıcı işlevi görür.

    Buna göre gözden *templates\index.html* her parça veri biçimlendirmesi içinde ayrı yer tutucular içerecek:

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

    Ardından update `home` işlevi için yer tutucu değerlerini sağlamak için:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Yeniden düzgün bir şekilde işlenen çıkışı görmek için uygulamayı çalıştırın.

    ![Şablon kullanarak çalışan uygulama](media/flask/step02-result.png)

1. Kaynak denetimi ve uzak deponuz isterseniz altında açıklandığı gibi güncelleştirmek için değişikliklerinizi işleyin [2-1. adım](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: şablonların ayrı bir dosyada olmam gerekir mi?

Yanıt: şablonları genellikle ayrı HTML dosyalarında korunsa de satır içi şablonu kullanabilirsiniz. Ayrı bir dosya kullanarak, ancak işaretleme ve kod arasında NET bir ayrım sağlamak için önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: şablonları .html dosya uzantısını kullanmalıdır?

Yanıt: *.html* her zaman için ilk bağımsız değişkeni dosyasında tam göreli yolunu tanımlamak için uzantı sayfasında şablon dosyaları için tamamen isteğe bağlı `render_template` işlevi. Ancak, Visual Studio (ve diğer Düzenleyiciler) genellikle kod tamamlama ve sözdizimi coloration ile gibi özellikler size *.html* şablonları sayfasında olgu ağır dosyaları olmayan kesinlikle HTML.

Aslında, Flask projesi ile çalışırken, Visual Studio otomatik olarak düzenlediğiniz HTML dosyası aslında bir Flask şablonudur algılar ve bazı otomatik tamamlama özellikleri sağlar. Örneğin, başlattığınızda bir Flask sayfası şablonu yorum yazmak `{#`, Visual Studio otomatik olarak size kapatma `#}` karakter. **Yorum seçimi** ve **seçimi işletilir satıra çevir** komutları (üzerinde **Düzenle** > **Gelişmiş** menü ve araç çubuğundaki) Ayrıca şablon açıklamaları yerine HTML Yorumlarını kullanın.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: Proje çalıştırabilir, şablon bulunamayan bir hata görüyorum. Ne oldu?

Yanıt: şablon bulunamıyor hatalar görürseniz, Flask proje için uygulama eklediğinizden emin olun *settings.py* içinde `INSTALLED_APPS` listesi. Bu giriş olmadan uygulamanın aramak için Flask bilemezsiniz *şablonları* klasör.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Soru: şablonları daha fazla alt klasörler halinde düzenlenebilir?

Yanıt: Evet, alt klasörler kullanabilir ve göreli yol altında daha sonra başvurmak *şablonları* çağrılarında `render_template`. Bunun yapılması, ad alanları şablonlarınızı için etkili bir şekilde oluşturmak için harika bir yoludur.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları işleme, sayfalar eklemek ve şablonu devralma kullanın](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Flask hızlı başlangıç şablonları oluşturma -](http://flask.pocoo.org/docs/1.0/quickstart/#rendering-templates) (flask.pocoo.org)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
