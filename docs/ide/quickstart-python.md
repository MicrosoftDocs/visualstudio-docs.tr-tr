---
title: 'Hızlı başlangıç: Visual Studio ile Python web uygulaması oluşturma'
titleSuffix: ''
description: Bu hızlı başlangıçta, Python 'da basit bir Web uygulaması oluşturmak için Visual Studio ve Flask çerçevesini kullanırsınız.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom:
- vs-acquisition
- SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: a94d28b6f9cb2aa9ee870dd6c4cc914e09b6efee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386260"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Hızlı başlangıç: Visual Studio kullanarak ilk Python web uygulamanızı oluşturma

Bu 5-10 dakikalık bir Python IDE olarak Visual Studio 'ya giriş, Flask çerçevesini temel alan basit bir Python web uygulaması oluşturacaksınız. Projeyi, Visual Studio 'nun temel özellikleri hakkında bilgi edinmenize yardımcı olan ayrık adımlarla oluşturursunuz.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın. Yükleyicide, **Python geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın. Yükleyicide, **Python geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Aşağıdaki adımlar, uygulama için kapsayıcı görevi gören boş bir proje oluşturur:

::: moniker range="vs-2017"
1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **dosya > yeni > proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, sağ üst köşedeki arama alanına "Python web projesi" yazın, ortadaki listede **Web projesi** ' ni seçin, projeye "hellopython" gibi bir ad verin ve ardından **Tamam**' ı seçin.

    ![Python web projesi seçiliyken yeni proje iletişim kutusu](media/quickstart-python-00-web-project.png)

    Python proje şablonlarını görmüyorsanız, **Visual Studio yükleyicisi** çalıştırın, **daha fazla** > **Değiştir**' i seçin, **Python geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Yeni proje sağ bölmedeki **Çözüm Gezgini** açılır. Başka dosya içermediğinden proje bu noktada boştur.

    ![Yeni oluşturulan boş projeyi gösteren Çözüm Gezgini](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio 2019 ' i açın.
2. Başlangıç ekranında **Yeni proje oluştur**' u seçin.
3. **Yeni proje oluştur** iletişim kutusunda, üstteki arama alanına "Python web" yazın, ortadaki listede **Web projesi** ' ni seçin ve ardından **İleri**' yi seçin:

    ![Python web projesi seçiliyken yeni bir proje ekranı oluştur](media/quickstart-python-00-web-project-2019a.png)

    Python proje şablonlarını görmüyorsanız, **Visual Studio yükleyicisi** çalıştırın, **daha fazla** > **Değiştir**' i seçin, **Python geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Aşağıdaki **yeni projeyi Yapılandır** iletişim kutusunda, **Proje adı** için "Merhaba Python" yazın, bir konum belirtin ve **Oluştur**' u seçin. ( **Çözüm adı** , **Proje adı** ile eşleşecek şekilde otomatik olarak ayarlanır.)

    ![Yeni proje iletişim kutusunu yapılandırın](media/quickstart-python-00-web-project-2019b.png)

5. Yeni proje sağ bölmedeki **Çözüm Gezgini** açılır. Başka dosya içermediğinden proje bu noktada boştur.

    ![Yeni oluşturulan boş projeyi gösteren Çözüm Gezgini](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Soru: bir Python uygulaması için Visual Studio 'da proje oluşturmanın avantajı nedir?**

**Cevap**: Python uygulamaları genellikle yalnızca klasör ve dosyalar kullanılarak tanımlanmıştır, ancak bu basit yapı, uygulamalar daha büyük hale gelir ve belki de otomatik olarak oluşturulan dosyalar, Web uygulamaları için JavaScript vb. dahil olmak üzere eklenebilir. Visual Studio projesi bu karmaşıklığın yönetilmesine yardımcı olur. Proje ( *. pyproj* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her bir dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur.

**Soru: Çözüm Gezgini ' de gösterilen "Çözüm" nedir?**

**Cevap**: bir Visual Studio çözümü, bir veya daha fazla ilgili projeyi grup olarak yönetmenize yardımcı olan bir kapsayıcıdır ve bir projeye özgü olmayan yapılandırma ayarlarını depolar. Bir çözümdeki projeler aynı zamanda bir proje (Python uygulaması) çalıştıran ikinci bir proje (Python uygulamasında kullanılan C++ uzantısı gibi) otomatik olarak oluşturur.

## <a name="install-the-flask-library"></a>Flask kitaplığını yükler

Python 'da Web Apps neredeyse her zaman, Web isteklerini yönlendirme ve yanıtları şekillendirme gibi alt düzey ayrıntıları işlemek için kullanılabilen birçok Python kütüphanesinin birini kullanır. Bu amaçla, Visual Studio, bu hızlı başlangıçta daha sonra kullanacağınız web uygulamaları için çeşitli şablonlar sağlar.

Burada, Flask kitaplığını Visual Studio 'nun bu proje için kullandığı varsayılan "genel ortama" yüklemek için aşağıdaki adımları kullanın.

::: moniker range="vs-2017"
1. Projenin varsayılan ortamını görmek için, projedeki **Python ortamları** düğümünü genişletin.

    ![Varsayılan ortamı gösteren Çözüm Gezgini](media/quickstart-python-02-default-environment.png)

2. Ortama sağ tıklayın ve **Python paketini yükler**' i seçin. Bu komut, **paketler** sekmesinde **Python ortamları** penceresini açar.

3. Arama alanına "Flask" yazın ve **Pypı 'den PyPI 'den pypi**'yi seçin. Yönetici ayrıcalıklarına yönelik tüm istemleri kabul edin ve devam etmek için Visual Studio 'daki **Çıkış** penceresini inceleyin. (Genel ortamın paketler klasörü, *C:\Program Files* gibi bir korumalı alan içinde bulunduğunda yükseltme istemi olur.)

    ![PIP yüklemesi kullanarak Flask kitaplığı yükleme](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Projenin varsayılan ortamını görmek için, projedeki **Python ortamları** düğümünü genişletin.

    ![Varsayılan ortamı gösteren Çözüm Gezgini](media/quickstart-python-02-default-environment-2019.png)

2. Ortama sağ tıklayın ve **Python paketlerini Yönet...** seçeneğini belirleyin. Bu komut, **Packages (PyPI)** sekmesindeki **Python ortamları** penceresini açar.

3. Arama alanına "Flask" yazın. Arama kutusunun altında **Flask** görünürse, bu adımı atlayabilirsiniz. Aksi takdirde, **Çalıştır komutunu seçin: PIP Install Flask**. Yönetici ayrıcalıklarına yönelik tüm istemleri kabul edin ve devam etmek için Visual Studio 'daki **Çıkış** penceresini inceleyin. (Genel ortamın paketler klasörü, *C:\Program Files* gibi bir korumalı alan içinde bulunduğunda yükseltme istemi olur.)

    ![PIP yüklemesi kullanarak Flask kitaplığı yükleme](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Yüklendikten sonra, kitaplık **Çözüm Gezgini** ortamda görünür, bu da Python kodunda bunu kullanabileceğiniz anlamına gelir.

    ::: moniker range="vs-2017"
    ![Flask kitaplığı yüklendi ve Çözüm Gezgini ' de gösteriliyor](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Flask kitaplığı yüklendi ve Çözüm Gezgini ' de gösteriliyor](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Geliştiriciler genel ortama yüklemek yerine genellikle belirli bir proje için kitaplıkların yükleneceği bir "sanal ortam" oluşturur. Visual Studio şablonları genellikle bu seçeneği, [hızlı başlangıç-şablon kullanarak bir Python projesi oluşturma](../python/quickstart-02-python-in-visual-studio-project-from-template.md)' da anlatıldığı şekilde sunar.

**Soru: diğer kullanılabilir Python paketleri hakkında nereden daha fazla bilgi edinebilirim?**

**Cevap**: [Python paket dizinini](https://pypi.org/)ziyaret edin.

## <a name="add-a-code-file"></a>Kod dosyası Ekle

Artık en az bir Web uygulaması uygulamak için bir Python kodu eklemek için hazırsınız.

1. **Çözüm Gezgini** projeye sağ tıklayın ve **> yeni öğe Ekle**' yi seçin.

1. Görüntülenen iletişim kutusunda **boş Python dosyası**' nı seçin, *app.py* olarak adlandırın ve **Ekle**' yi seçin. Visual Studio dosyayı bir düzenleyici penceresinde otomatik olarak açar.

1. Aşağıdaki kodu kopyalayın ve *app.py*'e yapıştırın:

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

1. **> yeni öğe Ekle** Iletişim kutusunun Python sınıfı, Python paketi, Python birimi testi, *web.config* dosyaları ve daha fazlası dahil olmak üzere bir Python projesine ekleyebileceğiniz birçok farklı dosya türünü görüntülediğini fark etmiş olabilirsiniz. Genel olarak, bu öğe şablonları, çağrıldıkları gibi, yararlı demirbaş kod ile hızlı bir şekilde dosya oluşturmanın harika bir yoludur.

**Soru: Flask hakkında nereden daha fazla bilgi edinebilirim?**

**Cevap**: [Flask hızlı](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)başlangıcı ile başlayan Flask belgelerine başvurun.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Çözüm Gezgini** 'de *app.py* öğesine sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin. Bu komut, uygulamayı çalıştırırken Python 'da başlatılacak kod dosyasını tanımlar.

    ::: moniker range="vs-2017"
    ![Çözüm Gezgini bir proje için başlangıç dosyası ayarlanıyor](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Çözüm Gezgini bir proje için başlangıç dosyası ayarlanıyor](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' i seçin. Ardından **Hata Ayıkla** sekmesini seçin ve **bağlantı noktası numarası** özelliğini olarak ayarlayın `4449` . Bu adım, Visual Studio 'Nun `localhost:4449` `app.run` , koddaki bağımsız değişkenlerle eşleşecek şekilde bir tarayıcı başlattığında emin olmanızı sağlar.

3. Dosyalarda yapılan değişiklikleri kaydeden ve uygulamayı çalıştıran hata ayıklama > hata ayıklama **olmadan Başlat** ' ı seçin (**CTRL** + **F5**).

4. **Https: \/ /localhost: 4449 içinde çalışan** iletinin bulunduğu bir komut penceresi görünür ve `localhost:4449` "Merhaba, Python!" iletisini gördüğünüz konuma bir tarayıcı penceresi açması gerekir GET isteği, komut penceresinde 200 durumu ile de görüntülenir.

    Bir tarayıcı otomatik olarak açılmadığından, seçtiğiniz tarayıcıyı başlatın ve adresine gidin `localhost:4449` .

    Yalnızca komut penceresinde Python etkileşimli kabuğu ' nu görürseniz veya bu pencere ekranda yanıp sönmüyorsa, yukarıdaki 1. adımda başlangıç dosyası olarak *app.py* ' ı ayarlamış olduğunuzdan emin olun.

5. `localhost:4449/hello`Kaynağın dekoratörü 'nin de çalışıp çalışmadığını sınamak için öğesine gidin `/hello` . Yine, GET isteği komut penceresinde 200 durumuyla görüntülenir. Diğer bir URL 'YI deneyebilirsiniz ve komut penceresinde 404 durum kodu gösterdiklerinden emin olmanız önerilir.

6. Uygulamayı durdurmak için komut penceresini kapatın, ardından tarayıcı penceresini kapatın.

**Soru: hata ayıklama olmadan Başlat komutu ve hata ayıklamayı başlatma arasındaki fark nedir?**

**Cevap**: uygulamayı [Visual Studio hata ayıklayıcısı](../python/debugging-python-in-visual-studio.md)bağlamında çalıştırmak için **Start Debugging** komutunu kullanın. böylece kesme noktaları ayarlayabilir, değişkenleri inceleyebilir ve kod satırınızın sonuna kadar ilerlemenize izin verin. Hata ayıklamayı mümkün kılan çeşitli kancalar nedeniyle uygulamalar hata ayıklayıcıda daha yavaş çalışabilir. **Hata ayıklama olmadan Başlat**, bunun aksine uygulamayı doğrudan komut satırından çalıştırmuş gibi, hata ayıklama bağlamı olmadan çalıştırır ve ayrıca, otomatik olarak bir tarayıcı başlatır ve proje özellikleri **hata ayıklama** sekmesinde belirtilen URL 'ye gider.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 'da ilk Python uygulamanızı çalıştırırken Tebrikler, Visual Studio 'Yu Python IDE olarak kullanma hakkında biraz bilgi edindiniz!

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service dağıtma](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu hızlı başlangıçta izlediğiniz adımlar oldukça geneldir, büyük olasılıkla otomatikleştirilmesi ve otomatik olması gerektiğini tahmin etmeniz gerekir. Bu Otomasyon, Visual Studio proje şablonlarının rolüdür. Hızlı başlangıç-Bu makalede, ancak daha az adımla bir Web uygulaması oluşturan bir örnek için [şablon kullanarak bir Python projesi oluşturun](../python/quickstart-02-python-in-visual-studio-project-from-template.md) .

Etkileşimli pencere, hata ayıklama, veri görselleştirme ve git ile çalışma dahil olmak üzere Visual Studio 'da Python hakkında daha kapsamlı bir öğreticiye devam etmek için [Öğreticiye gidin: Visual Studio 'Da Python kullanmaya başlayın](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Visual Studio 'Nun sunabileceği daha fazlasını araştırmak için aşağıdaki bağlantıları seçin.

- [Visual Studio 'Da Python web uygulaması şablonları](../python/python-web-application-project-templates.md)hakkında bilgi edinin.
- [Python hata ayıklama](../python/debugging-python-in-visual-studio.md) hakkında bilgi edinin
- Genel olarak [Visual STUDIO IDE](../get-started/visual-studio-ide.md) hakkında daha fazla bilgi edinin.
