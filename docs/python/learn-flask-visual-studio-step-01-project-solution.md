---
title: Flask Öğreticisi 1. adımda Visual Studio, Flask temel bilgileri öğrenin
titleSuffix: ''
description: Önkoşullar, Git ve sanal ortamları dahil olmak üzere Visual Studio projeleri, bağlamında Flask temel bilgileri bir kılavuz.
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
ms.openlocfilehash: 0603c1b8dcabc37631c7a52e11cfa964331010d8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066645"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Öğretici: Visual Studio'da Flask web çerçevesi ile çalışmaya başlama

[Flask](http://flask.pocoo.org/) URL yönlendirmeyi ve sayfa işleme için temel sağlayan bir basit Python web uygulamaları için bir çerçevedir.

Form doğrulaması, veritabanı Özet, kimlik doğrulama ve benzeri gibi özellikleri doğrudan sağlamadığından, Flask "micro" framework çağrılır. Gibi özellikleri yerine Flask olarak adlandırılan özel Python paketleri tarafından sağlanan *uzantıları*. Böylece Flask kendisi bir parçası olup olmadıklarını gibi görünürler uzantıları Flask ile sorunsuz şekilde tümleştirin. Örneğin, Flask kendisi bir sayfa şablon altyapısı sağlamaz. Şablon oluşturma Bu öğreticide gösterildiği gibi Jinja ve Jade, gibi uzantıları tarafından sağlanır.

Bu öğreticide, şunların nasıl yapılır:

> [!div class="checklist"]
> - (1. adım) "Boş Flask Web projesi" şablonu kullanarak bir Git deposunda bir temel Flask projesi oluşturma
> - Bir sayfa ile bir Flask uygulaması oluşturma ve bir şablonu (2. adım) kullanarak bu sayfa işleme
> - Statik dosyaları işleme, sayfalar eklemek ve şablonu devralma (3. adım) kullanın
> - Birden çok sayfaları ve duyarlı tasarım (4. adım) ile bir uygulama oluşturmak için Flask Web projesi şablonunu kullanma
> - Polls – Flask Web projesi şablonu, çeşitli depolama seçenekleri (Azure depolama, MongoDB veya bellek) kullanan bir yoklama uygulaması oluşturmak için kullanın.

Bu adımları boyunca üç ayrı projeler içeren tek bir Visual Studio çözümü oluşturun. Visual Studio ile birlikte gelen farklı Flask proje şablonlarını kullanarak bir proje oluşturun. Aynı çözümdeki projeleri tutarak, kolayca geri ve İleri karşılaştırma için farklı dosyalar arasında geçiş yapabilirsiniz.

> [!Note]
> Bu öğreticide farklıdır [Flask hızlı](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) içeren daha kapsamlı başlayan fiyatlarla proje şablonları farklı Flask kullanmak için kendi projeleriniz için işaret edecek şekilde nasıl, Flask hakkında daha fazla de öğrenin. Örneğin, proje şablonları otomatik olarak Flask paketi bir proje oluştururken yüklemek yerine, paketi hızlı başlangıç bölümünde gösterildiği gibi el ile yüklemek için gerek.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017'de Windows aşağıdaki seçeneklerle:
  - **Python geliştirme** iş yükü (**iş yükü** yükleyici sekmede). Yönergeler için [Visual Studio'da Python yükleme desteği](installing-python-support-in-visual-studio.md).
  - **Git için Windows** ve **Visual Studio için GitHub uzantısı** üzerinde **tek tek bileşenler** sekmesinde altında **kod Araçları**.

Ayrıntılar, bu öğreticide ele gelen değişiklik gösterebilir Flask proje şablonları Visual Studio için Python Araçları'nın tüm eski sürümleri dahildir.

Python geliştirme Visual Studio şu anda Mac için desteklenmiyor Mac ve Linux üzerinde kullanma [Python uzantı Visual Studio code'da](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1. adım: Visual Studio'nun proje ve çözüm oluşturma

1. Visual Studio'da **dosya** > **yeni** > **proje**"Flask" için arama yapın ve seçin **boş Flask Web projesi**  şablonu. (Şablon da altında bulunan **Python** > **Web** sol taraftaki listede.)

    ![Boş bir Flask Web projesi için Visual Studio'da yeni proje iletişim kutusu](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlara (önceki grafikte gösterildiği gibi) aşağıdaki bilgileri girin ve ardından **Tamam**:

    - **Adı**: Visual Studio projenin adını ayarlayın **BasicProject**. Bu ad Flask projesi için de kullanılır.
    - **Konum**: Visual Studio çözüm ve proje oluşturmak bir konum belirtin.
    - **Çözüm adı**: kümesine **LearningFlask**, bu çözüm için uygun birden çok proje için bir kapsayıcı olarak Bu öğreticide.
    - **Çözüm için dizin oluştur**: bırakın (varsayılan) olarak ayarlayın.
    - **Yeni Git deposu oluşturma**: çözüm oluşturduğunda, Visual Studio yerel bir Git deposu oluşturur, böylece (varsayılan olarak temizleyin olan) bu seçeneği belirleyin. Bu seçeneği görmüyorsanız, Visual Studio 2017 Yükleyicisi'ni çalıştırın ve ekleme **Git için Windows** ve **Visual Studio için GitHub uzantısı** üzerinde **tek tek bileşenler** sekmesi altında **kod Araçları**.

1. Kısa bir süre sonra Visual Studio, bir iletişim bildiren ile ister **dış paketleri bu proje gerektirir** (aşağıda gösterilmiştir). Şablonun içerdiği için bu iletişim kutusu görünür bir *requirements.txt* en son Flask 1.x paketini başvuran dosya. (Seçmek **gerekli paketleri Göster** tam bağımlılıkları görmek için.)

    ![Komut istemi bildiren proje dış paketleri gerektiriyor](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Seçeneğini **ben bunları kendim yükler**. Size kısa süre içinde kaynak denetiminden hariç tutuldu emin olmak için sanal ortamı oluşturun. (Ortam her zaman oluşturulabilir *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2. adım: Git denetimleri incelemek ve uzak bir depoyu Yayımla

Seçtiğiniz çünkü **yeni Git deposu Oluştur** içinde **yeni proje** iletişim kutusunda, projeyi zaten yerel kaynak denetimine oluşturma işlemi tamamlandıktan hemen sonra. Bu adımda, Visual Studio'nun Git denetimleriyle planladığınızdan ve **Takım Gezgini** kaynak denetimiyle çalışma penceresi.

1. Visual Studio ana penceresinde alt köşesine Git denetimleri inceleyin. Soldan sağa, bu denetimlerin gönderilmemiş işlemeler, kaydedilmemiş değişiklikler, deponun ve güncel dalınızın adını göster:

    ![Visual Studio penceresinde Git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > Seçmezseniz **yeni Git deposu Oluştur** içinde **yeni proje** iletişim kutusunda, Git denetimlerini göster yalnızca bir **kaynak denetimine Ekle** yerel oluşturan komutu Depo.
    >
    > ![Ekleme kaynak denetimi Visual Studio'da görünür bir depo oluşturduysanız değil](media/tutorials-common/step01-git-add-to-source-control.png)

1. Değişiklikleri düğmeyi seçin ve Visual Studio açar, **Takım Gezgini** penceresinde **değişiklikleri** sayfası. Yeni oluşturulan projeye zaten kaynak denetimi otomatik olarak kabul edilen olduğundan tüm bekleyen değişiklikleri görmüyorum.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda gönderilmemiş işlemeler düğmeyi seçin (yukarı ok ile **2**) açmak için **eşitleme** sayfasını **Takım Gezgini**. Yerel bir depo olduğundan, sayfa depo farklı uzak depoya yayımlamak için kolay seçenekler sunar.

    ![Takım Gezgini penceresini gösteren Git deposu için kullanılabilir seçenekleri kaynak denetimi](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için hangi hizmetin seçebilirsiniz. Bu öğreticide burada öğreticinin tamamlanmış örnek kodu korunur, GitHub kullanımı gösterilmiştir [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) depo.

1. Herhangi bir seçerken **Yayımla** denetimleri **Takım Gezgini** daha fazla bilgi için ister. Örneğin, Bu öğretici için örnek yayımlarken, havuz ilk olarak, bu durumda oluşturulması gerekiyordu **uzak depoya itme** seçeneği, deponun URL'si ile kullanıldı.

    ![Var olan bir uzak depoya gönderilirken için Takım Gezgini penceresi](media/flask/step01-push-to-github.png)

    Varolan bir depo yoksa **GitHub Yayımla** ve **Azure DevOps için anında iletme** seçenekleri sağlar, doğrudan Visual Studio içinde oluşturun.

1. Bu öğreticide çalışırken, düzenli aralıklarla denetimlerini işlemeyi ve göndermeyi değişiklikler Visual Studio kullanarak önleminizi. Bu öğretici size uygun noktalarda anımsatır.

> [!Tip]
> İçinde hızlıca gezinmek için **Takım Gezgini**, üst seçin (okuyan **değişiklikleri** veya **anında iletme** yukarıdaki resimlerdeki) kullanılabilir sayfalarının açılır menüsünü görmek için.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: Kaynak denetiminden bir proje başına kullanmanın bazı avantajları nelerdir?

Yanıt: Öncelikle, özellikle uzak bir depo da kullanıyorsanız, en başından itibaren kaynak denetimini kullanarak projenizin bir normal site dışında yedekleme sağlar. Bir proje üzerinde yalnızca koruma aksine bir yerel dosya sistemi kaynak denetimi ayrıca tam değişiklik geçmişini ve kolay tek bir dosyayı veya tüm proje önceki durumuna geri döndürme olanağı sağlar. Bu değişiklik geçmişini gerilemeleri (test hatalarını) nedenini belirlemeye yardımcı olur. Ayrıca, kaynak denetimi birden çok kişinin üzerinde çalışıyorsanız bir proje yönettiği gibi üzerine yazar ve çakışma çözümü sağlar gereklidir. Son olarak, temelde bir Otomasyon biçimi olan kaynak denetimi, iyi derlemeleri otomatikleştirme, test ve yayın yönetimi için ayarlar. DevOps için bir proje kullanarak ilk adımı gerçekten olduğu ve engelleri girişe kadar düşük olduğundan, gerçekten başına kaynak denetiminden kullanmamak için bir neden yoktur.

Daha fazla açıklaması için kaynak denetimi Otomasyonu olarak bkz [gerçekte kaynak: DevOps, rol depolarda](https://msdn.microsoft.com/magazine/mt763232), bir makale MSDN magazine'de mobil uygulamalar için yazılan, web uygulamaları için de geçerlidir.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Visual Studio otomatik-yeni bir proje uygulamadan gelen önleyebilirim?

Cevap: Evet. Otomatik Tamamlama devre dışı bırakmak için Git **ayarları** sayfasını **Takım Gezgini**seçin **Git** > **genel ayarları**temizleyin Etiketli seçeneği **değişiklikleri Birleştirmeden sonra varsayılan olarak**, ardından **güncelleştirme**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>1-3. adım: sanal ortam oluşturma ve kaynak Denetimi'nden çıkar

Projeniz için kaynak denetimi yapılandırdığınıza göre sanal ortamı gerektiren proje gerekli Flask paketlerini oluşturabilirsiniz. Ardından **Takım Gezgini** ortamın klasör, kaynak denetiminden hariç tutmak için.

1. İçinde **Çözüm Gezgini**, sağ **Python ortamları** düğümünü seçip alt **sanal ortama ekleme**.

    ![Çözüm Gezgini'nde sanal ortam komut ekleme](media/flask/step01-add-virtual-environment-command.png)

1. Bir **sanal ortama ekleme** iletişim kutusu açılır, iletisini ile **requirements.txt dosyasını bulduk.** Bu ileti, Visual Studio, sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![Sanal ortama Ekle iletişim kutusu requirements.txt iletisi](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Seçin **Oluştur** Varsayılanları kabul etmek için. (İsterseniz, sanal ortamın adı yalnızca alt klasörünü adını değiştiren değiştirebilirsiniz ancak `env` standart bir kuraldır.)

1. Visual Studio indirmeleri ve paketleri, yani Flask ve bağımlılıkları için 100'den fazla klasörlerdeki binlerce dosyalarla ilgili genişletme yükler için yönetici ayrıcalıkları onayı istenirse, sonra birkaç dakika bekleyin. Visual Studio ilerleme durumunu görebilirsiniz **çıkış** penceresi. Beklerken, soru bölümlerde düşünerek. Flask'ın bağımlılıkları açıklamasını üzerinde görebilirsiniz [Flask yükleme](http://flask.pocoo.org/docs/1.0/installation/#installation) sayfa (flask.pcocoo.org).

1. Visual Studio Git denetimlere (durum çubuğunda) değişiklik göstergesini seçin (gösteren **99&#42;**) açan **değişiklikleri** sayfasını **Takım Gezgini**.

    Sanal ortam oluşturma, değişiklikleri yüzlerce içinde getirildi, ancak siz (veya herhangi başka bir proje kopyalama) ortamdan her zaman yeniden oluşturabilirsiniz çünkü bunların hiçbirine kaynak denetiminde eklemeniz gerekmez *requirements.txt*.

    Sanal ortam hariç tutmak için sağ **env** klasörü ve select **bu yerel öğeleri Yoksay**.

    ![Kaynak denetim değişikliklerini sanal bir ortamda yoksayılıyor](media/flask/step01-ignore-local-items.png)

1. Sanal ortam hariç sonra yalnızca kalan proje dosyasına değişiklikler ve *.gitignore*. *.Gitignore* dosya sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayın

1. Bir işleme iletisi girin ve seçin **tümünü işle** düğmesine ve ardından işlemeler isterseniz, uzak depoya gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden bir sanal ortam oluşturmak istiyorum?

Yanıt: Sanal bir ortama uygulamanızın tam bağımlılıkları ayırmak için harika bir yoludur. Bu yalıtım global Python ortamı içinde çakışmaları önler ve test etme ve işbirliği kolaylık sağlar. Bir uygulama geliştirirken zaman içinde neredeyse şaşmaz biçimde birçok yararlı Python paketlerini getirin. Projeye özgü sanal bir ortamda paketleri tutarak, projenin kolayca güncelleştirebilirsiniz *requirements.txt* kaynak denetimine dahil bu ortamı tanımlayan dosya. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarlar dahil olmak üzere diğer herhangi bir bilgisayar için kopyalanan yalnızca kullanarak ortama yeniden oluşturmak daha kolaydır *requirements.txt* (neden olduğu ortam kaynak denetiminde olması gerekmez). Daha fazla bilgi için [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Kaynak denetimine zaten kararlıdır sanal bir ortama nasıl kaldırırım?

Yanıt: İlk olarak, Düzenle, *.gitignore* klasörü dışlamak için dosya: sonunda açıklamayı içeren bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için yeni bir satır ekleyin `/BasicProject/env`. (Visual Studio dosyayı göstermiyor çünkü **Çözüm Gezgini**, kullanarak doğrudan açmak **dosya** > **açın**  >   **Dosya** menü komutu. Dosyasını da açabilirsiniz **Takım Gezgini**: üzerinde **ayarları** sayfasında **depo ayarları**Git **yoksayma ve öznitelik dosyaları** bölümüne ve ardından **Düzenle** yanındaki bağlantı **.gitignore**.)

İkinci olarak, bir komut penceresi açın, gibi klasöre gidin *BasicProject* sanal ortam klasörü gibi içeren *env*, çalıştırıp `git rm -r env`. Ardından komut satırından bu değişiklikleri işleyebilir (`git commit -m 'Remove venv'`) veya gelen gerçekleştirmeyi **değişiklikleri** sayfasının **Takım Gezgini**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4. adım: ortak kod İnceleme

1. Proje oluşturma işlemi tamamlandıktan sonra çözümü görmek ve proje **Çözüm Gezgini**, projeyi yalnızca iki dosya içeren burada *app.py* ve *requirements.txt*:

    ![Çözüm Gezgini'nde boş Flask proje dosyaları](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Daha önce belirtildiği gibi *requirements.txt* Flask paket bağımlılığı dosyasını belirtir. Bu dosyanın varlığını ilk proje oluştururken bir sanal ortam oluşturmak için davet ' dir.

1. Tek *app.py* dosyası üç parça içerir. İlk bir `import` Flask, bir örneğini oluşturmak için bildirimi `Flask` değişkenine atanan sınıfı `app`ve sonra atayarak bir `wsgi_app` (bir web ana bilgisayara dağıtım yaparken yararlıdır, ancak şu anda kullanılmayan) değişkeni:

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. İkinci bölümü, dosyasının sonunda, belirli konak ve bağlantı noktası değerlerini ortam değişkenlerini (localhost:5555 için varsayarak) alınan Flask geliştirme sunucusu başlar isteğe bağlı kod bitidir:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Üçüncü bir işlev için bir URL atar kod kısa bir bit yönlendirmek, yani işlev URL tarafından tanımlanan kaynağa sağlar olur. Flask'ın kullanarak yönlendirmeler tanımladığınız `@app.route` dekoratör, bağımsız değişken site kökünden göreli URL'sidir. Kodda görebileceğiniz gibi burada işlevi işlemek bir tarayıcı için yeterli olan yalnızca bir metin dizesi döndürür. İzleyen adımları daha zengin HTML sayfaları işleyin.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-name-argument-to-the-flask-class"></a>Soru: Amacı nedir __adı__ Flask sınıfı bağımsız değişken?

Yanıt: Bağımsız değişken uygulamanın modül veya paket adıdır ve Flask şablonları, statik dosyalar ve uygulamaya ait diğer kaynaklar için nereye söyler. Tek bir modülde yer alan uygulamalar için `__name__` her zaman uygun değerdir. Ayrıca, hata ayıklama bilgisi gerektiren uzantılar için de önemlidir. Daha fazla bilgi ve ek bağımsız değişkenler için bkz. [Flask sınıf belgelerini](http://flask.pocoo.org/docs/1.0/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Soru: bir işlev, birden fazla rota dekoratör olabilir mi?

Cevap: Evet, birden fazla yol aynı işlevi hizmet veriyorsa, istediğiniz sayıda dekoratörler kullanabilirsiniz. Örneğin, kullanılacak `hello` işlevi hem de "/" ve "/ hello", aşağıdaki kodu kullanın:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Soru: Flask değişken URL rotaları ve sorgu parametreleri ile nasıl sağlanır?

Yanıt: herhangi bir değişken ile işaretle bir yolda `<variable_name>`, ve Flask değişkeni kullanarak bir adlandırılmış bağımsız değişken işleve geçirir. Değişken, URL yolu veya bir sorgu parametresi olarak bir parçası olabilir. Örneğin, bir yol biçiminde `'/hello/<name>` adlı bir dize bağımsız değişkeni oluşturur `name` işlevi ve kullanarak `?message=<msg>` yolda belirtilen ilişkin değeri ayrıştırır "iletisi =" sorgu parametresi ve olarak işleve geçirir `msg`:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Türü değiştirmek için değişken ile önek `int`, `float`, `path` (kabul eden klasör adları açıklamak üzere eğik çizgi), ve `uuid`. Ayrıntılar için bkz [değişken kuralları](http://flask.pocoo.org/docs/1.0/quickstart/#variable-rules) Flask belgelerinde.

Sorgu parametreleri aracılığıyla da `request.args` özelliği, özellikle ile `request.args.get` yöntemi. Daha fazla bilgi için [istek nesnesi](http://flask.pocoo.org/docs/1.0/quickstart/#the-request-object) Flask belgelerinde.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Ben diğer paketler yüklendikten sonra Visual Studio requirements.txt dosyasını bir sanal ortam oluşturabilir?

Cevap: Evet. Genişletin **Python ortamları** düğümünün sanal ortamınıza sağ tıklatın ve seçin **Generovat requirements.txt** komutu. Bu komutu düzenli olarak kullanmak için iyi ortamı değiştirin ve değişiklikleri işleme *requirements.txt* kaynak denetimine bağımlı bu ortamda herhangi bir kod değişikliği birlikte. Bir yapı sunucusunda sürekli tümleştirmeyi ayarlama, ortamı değiştirmek her dosya ve değişiklikleri oluşturmanız gerekir.

## <a name="step-1-5-run-the-project"></a>1-5. adım: projeyi Çalıştır

1. Visual Studio'da **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** (araç çubuğunda gördüğünüz bir tarayıcı farklılık gösterebilir):

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/tutorials-common/run-web-server-toolbar-button.png)

1. Ya da komut bir rastgele bağlantı noktası numarası için bağlantı noktası ortam değişkenine atar ve ardından çalışan `python app.py`. Kod, Flask'ın geliştirme sunucusu içinde bu bağlantı noktasını kullanarak uygulamayı başlatır. Visual Studio diyorsa **hata ayıklayıcı başlatılamadı** sahip herhangi bir başlangıç dosyası hakkında bir ileti ile sağ **app.py** içinde **Çözüm Gezgini** seçip  **Başlangıç dosyası olarak ayarla**.

1. Sunucuyu başlatır görüntüleyen sunucu günlüğü'nü açın bir konsol penceresi görürsünüz. Visual Studio sonra tarayıcının otomatik olarak açılır `http://localhost:<port>`, burada tarafından işlenen ileti görmeniz gerekir `hello` işlevi:

    ![Flask projesi varsayılan görünüm](media/flask/step01-first-run-success.png)

1. İşiniz bittiğinde, konsol penceresini kapatarak veya kullanarak sunucuyu Durdur **hata ayıklama** > **hata ayıklamayı Durdur** Visual Studio'daki komutu.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Projenin Python menüdeki hata ayıklama menü komutları ve sunucu komutlarını kullanarak arasındaki fark nedir?

Yanıt: ek olarak **hata ayıklama** menü komutları ve araç çubuğu düğmeleri kullanarak da başlatabilirsiniz **Python** > **Server'i** veya **Python** > **Run hata ayıklama sunucusu** projenin bağlam menüsü komutları. Her iki komutu çalıştıran sunucunun yerel URL'sini (localhost:port) görebileceğiniz bir konsol penceresi açın. Ancak, bu URL ile bir tarayıcı el ile açmalısınız ve hata ayıklama sunucuda otomatik olarak Visual Studio hata ayıklayıcı başlatılamıyor. Kullanmak isterseniz, bir hata ayıklayıcı için çalışan işlemi daha sonra ekleyebilirsiniz **hata ayıklama** > **iliştirme** komutu.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Flask projesi aynı dosyada kod sayfası ve başlatma kodunu içerir. Bu iki sorunlar ayırmak için ve ayrıca şablonları kullanarak HTML ve veri ayırmak için idealdir.

> [!div class="nextstepaction"]
> [Görünümleri ve şablonların ile bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Flask hızlı](http://flask.pocoo.org/docs/1.0/quickstart/) (flask.pocoo.org)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
