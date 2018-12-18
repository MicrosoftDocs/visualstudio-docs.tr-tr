---
title: "Hızlı Başlangıç: Python web uygulaması oluşturmak için Visual Studio'yu kullanın."
description: Bu hızlı başlangıçta, Visual Studio ve Flask framework python'da basit web uygulaması oluşturmak için kullanın.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a4ef6ebbbce03dce7105b49100c9c8f50c44e5e4
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159808"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Hızlı Başlangıç: Visual Studio kullanarak ilk Python web uygulamanızı oluşturma

Bu 5-10 dakikalık bir giriş Visual Studio'ya bir Python IDE olarak, Flask framework tabanlı basit bir Python web uygulaması oluşturun. Ayrık'aracılığıyla projenin oluşturduğunuz yardımcı adımlar Visual Studio temel özellikleri hakkında bilgi edinin.

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ücretsiz yüklemek için. Yükleyicide seçtiğinizden emin olun **Python geliştirme** iş yükü.

## <a name="create-the-project"></a>Projeyi oluşturma

Aşağıdaki adımlar, uygulama için bir kapsayıcı görevi gören boş bir proje oluşturur:

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan seçin **Dosya > Yeni > Proje**.

1. İçinde **yeni proje** iletişim kutusunda, sağ üst köşedeki arama alanına "Python Web projesi" girin, **Web projesi** ortadaki listeyi proje "HelloPython" gibi bir ad verin ve ardından seçin**Tamam**.

    ![Python Web Seçili proje ile yeni proje iletişim kutusu](media/quickstart-python-00-web-project.png)

    / Python proje şablonları görmüyorsanız, İptal **yeni proje** iletişim kutusu ve üst menü çubuğundan seçin **Araçlar > araçları ve özellikleri Al** açmak için **Visual Studio Yükleyici**. Seçin **Python geliştirme** iş yükü, ardından **Değiştir**.

    ![Python geliştirme iş yüküyle Visual Studio](../python/media/installation-python-workload.png)

1. Yeni Proje açılır **Çözüm Gezgini** sağ bölmede. Proje, bu noktada, başka hiçbir dosya içerdiği için boştur.

    ![Yeni oluşturulan boş projeyi gösteren Çözüm Gezgini](media/quickstart-python-01-empty-project.png)

**Soru: Proje Visual Studio için Python uygulaması oluşturmanın avantajı nedir?**

**Yanıt**: Python uygulamaları, genellikle yalnızca klasörleri ve dosyaları kullanılarak tanımlanır, ancak uygulamalar daha büyük hale gelir ve belki de JavaScript web uygulamaları için otomatik olarak oluşturulan dosyaları içeren vb. gibi bu basit bir yapıya sıkıcı hale gelebilir. Visual Studio projesi Bu karmaşıklığı yönetmenize yardımcı olur. Proje (bir *.pyproj* dosyası) kaynak ve projenizle ilişkili içerik dosyalarını tanımlar, her dosya için yapı bilgisi içerir, kaynak denetimi sistemleriyle tümleştirmeyi bilgilerini korur ve yardımcı olur mantıksal bileşenler uygulamanıza düzenleyin.

**Soru: "Çözüm" nedir Çözüm Gezgini'nde gösterilen?**

**Yanıt**: Visual Studio çözümü için ilgili projeleri bir veya daha fazla grup halinde yönetmenize yardımcı olan bir kapsayıcı ve projeye özgü olmayan yapılandırma ayarları depolar. Bir çözümde proje ayrıca birbirlerine başvurabilir, (bir Python uygulaması) sağlayacak şekilde çalışan tek bir proje, otomatik olarak (örneğin, Python uygulaması içinde kullanılan C++ uzantısı) ikinci bir proje oluşturur.

## <a name="install-the-flask-library"></a>Flask kitaplığını yükle

Python Web uygulamalarında hemen her zaman birçok kullanılabilir Python kitaplıkları yönlendirme web isteklerini ve yanıtlarını şekillendirme gibi alt düzey ayrıntıları işlemek için kullanın. Bu amaç için Visual Studio, çeşitli web apps, biri bu hızlı başlangıçta kullanmak için şablonları sağlar.

Burada, "Bu proje için Visual Studio kullanan varsayılan genel ortama" Flask kitaplığını yüklemek için aşağıdaki adımları kullanın.

1. Genişletin **Python ortamları** proje için varsayılan ortam görmek için proje düğümü.

    ![Varsayılan ortamı gösteren Çözüm Gezgini](media/quickstart-python-02-default-environment.png)

1. Ortam sağ tıklayıp **Python paketini Yükle**. Bu komut açılır **Python ortamları** penceresinde **paketleri** sekmesi.

1. Arama alanına "flask" girin ve seçin **pip, Pypı flask yükleme**. Sizden yönetici ayrıcalıkları kabul edin ve gözlemleyin **çıkış** ilerleme için Visual Studio penceresinde. (Bir komut istemi packages klasörünü genel ortam için bir korumalı alanı içinde bulunduğu yükseltme olur için ister *C:\Program Files*.)

    ![Pip kullanılarak Flask kitaplık yükleme](media/quickstart-python-03-install-package.png)

1. Yüklendikten sonra kitaplık ortamda görünür **Çözüm Gezgini**, yapabileceğiniz anlamına gelir bunu Python kodu kullanın.

    ![Flask kitaplığının yüklü ve Çözüm Gezgini'nde gösteriliyor](media/quickstart-python-04-package-installed.png)

> [!Note]
> Genel bir ortamda kitaplıklarını yüklemek yerine, geliştiricilerin, belirli bir projenin kitaplıklarını yüklemek "sanal ortam" genellikle oluşturun. Visual Studio şablonları bölümünde açıklandığı gibi bu seçenek genellikle teklif [hızlı başlangıç - şablon kullanarak bir Python projesi oluşturma](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Soru: Burada kullanılabilen diğer Python paketleri hakkında daha fazla bilgi?**

**Yanıt**: Ziyaret [Python paket dizini](https://pypi.org/).

## <a name="add-a-code-file"></a>Bir kod dosyası Ekle

Python kodu en az bir web uygulamasını uygulamak için biraz eklemek artık hazırsınız.

1. Projeye sağ **Çözüm Gezgini** seçip **Ekle > Yeni öğe**.

1. Görüntülenen iletişim kutusunda, seçmek **boş Python dosyası**, adlandırın *app.py*seçip **Ekle**. Visual Studio, düzenleyici penceresinde dosya otomatik olarak açılır.

1. Aşağıdaki kodu kopyalayın ve yapıştırın *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Fark etmiş **Ekle > Yeni öğe** diğer türlerde dosyaları Python sınıfı, bir Python paketi, bir Python birim testi dahil olmak üzere bir Python projeye Ekle iletişim kutusu görüntüler *web.config* dosyaları ve daha fazlası. Genel olarak, adlı gibi bu öğe şablonları dosyaları yararlı Demirbaş kod ile hızlı bir şekilde oluşturmak için harika bir yol sağlar.

**Soru: Flask hakkında nereden bilgi edinebilirim?**

**Yanıt**: İle başlayarak, Flask belgelerine başvurun [Flask hızlı](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart).

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Sağ *app.py* içinde **Çözüm Gezgini** seçip **başlangıç dosyası olarak ayarla**. Bu komut, uygulamayı çalıştırırken Python'da başlatmak için kod dosyası tanımlar.

    ![Çözüm Gezgini'nde bir proje için başlangıç dosyası ayarı](media/quickstart-python-05-set-as-startup-file.png)

2. Projeye sağ **Çözüm Gezgini** seçip **özellikleri**. Ardından **hata ayıklama** ayarlayın ve sekme **bağlantı noktası numarası** özelliğini `4449`. Visual Studio ile bir tarayıcı başlatır, bu adım sağlar `localhost:4449` eşleştirilecek `app.run` koddaki bağımsız değişkenler.

3. Seçin **hata ayıklama > hata ayıklama olmadan Başlat** (**Ctrl**+**F5**), dosyaları değişiklikleri kaydeder ve uygulamayı çalıştırır.

4. İletinin bir komut penceresi görünür "* çalışan <https://localhost:4449/>", ve bir tarayıcı penceresi açılmalıdır `localhost:4449` iletisini gördüğünüz yerde "Hello, Python!" GET isteği, durumu 200 olan komut penceresinde de görünür.

    Bir tarayıcı otomatik olarak açılmazsa, tercih ettiğiniz tarayıcıyı başlatın ve gidin `localhost:4449`.

    Yalnızca Python etkileşimli Kabuk komut penceresinde görürseniz veya o pencereyi kısaca ekranda yanıp, ayarladığınız olun *app.py* yukarıdaki 1. adımda başlangıç dosyası olarak.

5. Gidin `localhost:4449/hello` , test etmek için dekoratör `/hello` kaynak de çalışır. Komut penceresinde durumu 200 olan yeniden GET isteği görüntülenir. 404 durum kodu komut penceresinde Göster görmek için bazı diğer URL'sini de deneyin çekinmeyin.

6. Uygulamayı durdurmak için komut penceresini kapatın, ardından tarayıcı penceresini kapatın.

**Soru: Hata ayıklama olmadan Başlat komutu ve hata ayıklamayı Başlat arasındaki fark nedir?**

**Yanıt**: Kullandığınız **hata ayıklamayı Başlat** bağlamında uygulamayı çalıştırmak için [Visual Studio hata ayıklayıcısını](../python/debugging-python-in-visual-studio.md), kesme noktaları ayarlamanıza olanak sağlayan, değişkenleri inceleyebilir ve satır kodunuzda adım adım. Uygulamalar, hata ayıklama mümkün kılan çeşitli kancaları nedeniyle hata ayıklayıcıda yavaş çalışabilir. **Hata ayıklama olmadan Başlat**, buna karşılık, komut satırından, hiçbir hata ayıklama içeriğini çalıştırdıysanız gibi doğrudan uygulama çalışır ve da otomatik olarak bir tarayıcı başlatır ve belirtilen proje özelliklerinde URL'sine gider  **Hata ayıklama** sekmesi.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'yu bir Python IDE kullanma hakkında biraz öğrendiğinize göre ilk Python uygulamanızı Visual Studio'dan içinde çalıştırma Tebrikler!

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service'e dağıtma](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu hızlı başlangıçta uyguladığınız adımları oldukça geneldir çünkü olabilir ve otomatik hale getirilmelidir büyük olasılıkla tahmin. Bu otomasyon, Visual Studio Proje şablonları rolüdür. Git aracılığıyla [hızlı başlangıç - şablon kullanarak bir Python projesi oluşturma](../python/quickstart-02-python-in-visual-studio-project-from-template.md) benzeyen bir web uygulaması oluşturan bir örnek için bu makalede, ancak daha az adım ile oluşturulmuş.

Visual Studio'da Python etkileşimli penceresinde kullanma dahil olmak üzere, hata ayıklama, veri görselleştirme üzerinde bir irdelemesi öğreticisiyle devam edin ve Git ile çalışma geçtikleri [Öğreticisi: Visual Studio'da Python ile çalışmaya başlama](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Daha fazla sunmak Visual Studio sahip olduğunu keşfetmek için aşağıdaki bağlantıları seçin.

- Hakkında bilgi edinin [Python web uygulaması şablonları Visual Studio'da](../python/python-web-application-project-templates.md).
- Hakkında bilgi edinin [Python hata ayıklama](../python/debugging-python-in-visual-studio.md)
- Daha fazla bilgi edinin [Visual Studio IDE](../get-started/visual-studio-ide.md) genel.
