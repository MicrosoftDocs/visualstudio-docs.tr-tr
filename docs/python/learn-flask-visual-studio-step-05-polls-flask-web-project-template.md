---
title: Flask Öğreticisi 5. adımında Visual Studio, proje şablonu yoklamalar öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle yoklamalar Flask Web projesi ve polls – Webový projekt Flask/Jade şablonları özelliklerinin bağlamında Flask temel bilgileri bir kılavuz.
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
ms.openlocfilehash: a29e222df2a8443e9d5210c0382125cdc65a814f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066005"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>5. adım: yoklamalar Flask Web projesi şablonunu kullanma

**Önceki adımda: [tam Flask Web projesi şablonunu kullanma](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Visual Studio'nun "Flask Web projesi" şablonu anladım artık "Yoklamalar Flask Web üzerinde aynı kod tabanının yapılar projesi", üçüncü Flask şablonu bakabilirsiniz.

Bu adımda şunların nasıl yapılır:

> [!div class="checklist"]
> - Şablondan proje oluşturma ve veritabanı başlatılamıyor (adım 5 - 1)
> - Veri modelleri (5-2. adım) Anlama
> - Yedekleme veri deposu (5-3. adım) Anlama
> - Yoklama sonuçları ve ayrıntı görünümleri (5-4. adım) Anlama

Visual Studio kullanarak uygulamanın aynısını üretir, ancak Jade uzantı Jinja şablon oluşturma altyapısı için kullanır. "Windows Flask/Jade polls – Webový projekt" şablonu da sağlar. Ayrıntılar için bkz [adım 4 - Flask/Jade Web projesi şablonu](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>5-1. adım: Proje oluşturma

1. Visual Studio'da Git **Çözüm Gezgini**, sağ **LearningFlask** daha önce Bu öğretici ve seçme içinde oluşturulan çözüm **Ekle**  >   **Yeni proje**. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, seçin **dosya** > **yeni** > **proje** yerine.)

1. Yeni Proje iletişim kutusunda, aramak ve seçmek **yoklamalar Flask Web projesi** şablon "FlaskPolls" proje arayın ve seçin **Tamam**.

1. Diğer proje şablonları gibi Visual Studio'da, "Yoklamalar Flask Web projesi" şablonu içeren bir *requirements.txt* dosya, Visual Studio bu bağımlılıkların yükleneceği sorar. Seçeneğini **sanal bir ortama yükleme**hem de **sanal ortama ekleme** iletişim kutusunda **Oluştur** Varsayılanları kabul etmek için. ("Yoklamalar Flask/Jade Web Proje" de pyjade gerektirir; bu şablon, Flask ve bunun yanı sıra azure depolama ve pymongo paketleri gerektirir.)

1. Ayarlama **FlaskPolls** proje bu projeye sağ tıklayarak Visual Studio çözümü için varsayılan olarak **Çözüm Gezgini** seçerek **başlangıçprojesiolarakayarla**. Gösterilen başlangıç projesi içinde hata ayıklayıcısını başlattığınızda nelerin çalıştırılacağını kalın.

1. Seçin **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** server çalıştırmak için araç çubuğunda:

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama hakkında ev ve kişi, üst gezinti çubuğunda kullanma arasında gezinmek üç sayfa vardır. Bir veya iki uygulamanın farklı kısımlarını incelemek için dakika alın (hakkında ve ilgili kişi sayfaları "Flask Web projesi" için çok benzer ve daha ayrıntılı olarak ele değildir).

    ![Polls – Flask Web projesi uygulamasının tam görünümü](media/flask/step06-full-app-view.png)

1. Giriş sayfasında **örnek yoklamalar Oluştur** düğmesi başlatır açıklanan üç farklı yoklamalar uygulamanın veri deposuyla *models/samples.json* sayfası. Varsayılan olarak, uygulama, uygulama her başlatıldığında sıfırlanır (gösterildiği gibi hakkında sayfasında), bir bellek içi veritabanı kullanır. Uygulama, ayrıca bu makalenin sonraki bölümlerinde açıklandığı gibi Azure depolama ve Mongo DB ile çalışmak için kodu içerir.

1. Veri deposu başlattık sonra (kısa tutmak için gezinti çubuğunda ve altbilgi atlanır) giriş sayfasında gösterildiği gibi farklı yoklamalarda oy verebilirsiniz:

    ![Veri deposu başlatıldıktan sonra yoklamalar uygulamasının görünümü](media/flask/step06-polls-initialized.png)

1. Bir yoklama seçerek, belirli seçimlerini görüntüler:

    ![Bir yoklama için oy arabirimi](media/flask/step06-polls-voting-interface.png)

1. Oy sonra uygulama sonuçları sayfası gösterilir ve tekrar oy kullanmanıza olanak sağlar:

    ![Oy sonra Sonuçlar Görünümü](media/flask/step06-polls-results.png)

1. İzleyen bölümlerde için uygulamayı bırakabilirsiniz.

    Uygulamayı durdurmak istiyorsanız ve [değişiklikleri kaynak denetimine](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), ilk açın **değişiklikleri** sayfasını **Takım Gezgini**, sanal ortam (klasörünü sağ tıklatın büyük olasılıkla **env**) seçip **bu yerel öğeleri Yoksay**.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleyin

Önce belirtildiği gibi. neleri kadarını "Yoklamalar Flask Web projesi" şablonu (ve "Windows Flask/Jade polls – Webový projekt" şablonu) oluşturulmuş bir projeyi Visual Studio'daki diğer proje şablonları incelediniz, bilgi sahibi olmanız gerekir. Ek adımlar bu makalede daha önemli değişiklikler ve eklemeler, veri modelleri ve ek görünümler özetler.

## <a name="step-5-2-understand-the-data-models"></a>5-2. adım: veri modelini anlama

Uygulama için veri modellerini yoklama ve tanımlanan seçim adlı Python sınıflardır *modelleri /\_\_init\_\_.py*. Bir yoklama seçim örneklerinin bir koleksiyonunu temsil kullanılabilir yanıtları soru temsil eder. Bir yoklama sayısı (herhangi bir seçim için) oy ve görünümleri oluşturmak için kullanılan istatistiklerini hesaplamak için bir yöntem de tutar:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Bu veri modelleri sonraki adımda açıklanan veri depolarını yedekleme farklı türleriyle çalışmak uygulamanın görünüm sağlayan genel özetlerdir.

## <a name="step-5-3-understand-the-backing-data-stores"></a>5-3. adım: yedekleme veri depoları anlama

"Windows Flask polls – Webový projekt" şablonu ile oluşturulan uygulama, bellek, Azure tablo depolama veya Mongo DB veritabanına bir veri deposuna karşı çalıştırabilirsiniz.

Veri depolama mekanizmasını gibi çalışır:

1. Depo türü aracılığıyla belirtilen `REPOSITORY_NAME` "bellek", "azuretablestore" veya "mongodb" için ayarlanan ortam değişkeni. Bir bit kod *settings.py* varsayılan olarak "bellek" kullanarak adını alır. Yedekleme deposu değiştirmek istiyorsanız, ortam değişkenini ayarlamak ve uygulamayı yeniden başlatmanız gerekir.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *Settings.py* ardından başlatır kod bir `REPOSITORY_SETTINGS` nesne. Azure tablo depolama veya kara DB kullanmak istiyorsanız, önce bu veri depoları başka bir yerde başlatın, ardından gerekir uygulama Mağazası'na nasıl bağlanacaklarını gerekli ortam değişkenlerini ayarlayın:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. İçinde *views.py*, uygulamayı başlatmak için bir Üreteç yöntemi çağıran bir `Repository` veri deposunun adı ve ayarları kullanarak nesne:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` Yöntemi içinde bulunan *models\factory.py*, hangi yalnızca uygun depoyu modülü içe aktarır ve ardından oluşturur bir `Repository` örneği:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Uygulamaları `Repository` her veri deposuna özel bir sınıf içinde bulunabilir *models\azuretablestorage.py*, *models\mongodb.py*, ve *models\memory.py* . Azure depolama uygulaması, azure depolama paketinden kullanır; Mongo DB uygulaması pymongo paketi kullanır. 5-1. adımda da belirtildiği gibi her iki paketi de proje şablonunun içerdiği *requirements.txt* dosya. Ayrıntıları keşfetmek için okuyucu bir alıştırma olarak kalır.

Kısacası, `Repository` sınıfı veri deposu özelliklerini özetler ve uygulama ortam değişkenlerini seçin ve kullanmak için üç uygulamalarının hangi yapılandırmak için çalışma zamanında kullanır.

Bu nedenle isterseniz, aşağıdaki adımları proje şablonu tarafından sağlanan üç değerinden farklı bir veri deposu desteği ekleyin:

1. Kopyalama *memory.py* yeni bir dosya için temel arabirimi olması `Repository` sınıfı.
1. Kullanmakta olduğunuz veri deposunda uygun olarak bu sınıfın uygulaması değiştirin.
1. Değiştirme *factory.py* diğerine eklemek için `elif` çalışmasını eklenen veri deponuz için bir ad tanır ve uygun modülü içe aktarır.
1. Değiştirme *settings.py* başka bir ad tanımak için `REPOSITORY_NAME` ortam değişkeni ve başlatmak için `REPOSITORY_SETTINGS` uygun şekilde.

### <a name="seed-the-data-store-from-samplesjson"></a>Samples.json veri deposundan temel

Uygulama giriş sayfası iletiyi gösterecek şekilde hiçbir anketler, başlangıçta tüm seçilen veri deposu içeren **kullanılabilir hiçbir yoklamalar** ile birlikte **örnek yoklamalar Oluştur** düğmesi. Ancak, düğmeyi seçin, sonra kullanılabilir olup olmadığını yoklar görüntülemek için görünümü değiştirir. Bu anahtar koşullu etiketleri üzerinden gerçekleşir *templates\index.html* (bazı boş satırları verilmemiştir):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

`polls` Şablon değişkeni gelen çağrısından `repository.get_polls`, döndüren bir şey veri deposu başlatılana kadar.

Seçme **örnek yoklamalar Oluştur** düğmesi /seed URL'sine gider. Bu rota için işleyici tanımlanan *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Çağrı `repository.add_sample_polls()` sona eriyor belirli birinde `Repository` seçilen veri deponuz için uygulamaları. Her uygulama çağrıları `_load_samples_json` yöntemi bulunan *modelleri\_\_init\_\_.py* yüklenecek *models\samples.json* dosyası belleğe, ardından gerekli oluşturmak için bu verileri yinelenir `Poll` ve `Choice` veri deposundaki nesne.

Bu işlem tamamlandıktan sonra `redirect('/')` deyiminde `seed` yöntemi giriş sayfasına götürür. Çünkü `repository.get_polls` artık koşullu etiketleri bir veri nesnesi döndürür *templates\index.html* artık yoklamalar içeren bir tablo oluşturur.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Soru: Nasıl bir yeni yoklamalar uygulamaya ekliyor mu?

Yanıt: Proje şablonu aracılığıyla sağlanan uygulama ekleme veya düzenleme yoklamalar için bir özellik içermiyor. Değiştirebileceğiniz *models\samples.json* yeni başlatma verilerini oluşturmak için ancak bunun yapılması veri deposunu sıfırlama anlamına. Düzenleme özellikleri uygulamak için genişletmek gereken `Repository` sınıf arabirimi gerekli oluşturmak için yöntemleri ile `Choice` ve `Poll` örnekleri, bu yöntemleri kullanan ek sayfalarında sonra bir kullanıcı Arabirimi uygulayın.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>5-4. adım: yoklama ayrıntıları ve sonuçları görünümleri anlayın

Çoğu "Yoklamalar Flask Web projesi" ve "Windows Flask/Jade polls – Webový projekt" şablonları tarafından üretilen görünümlerini hakkında ve iletişim için görünümleri gibi sayfa, "Flask Web projesi" (veya "Webový projekt Flask/Jade") şablonu tarafından oluşturulan görünümler, çalıştığınız oldukça benzer ile Bu öğreticide daha önce. Önceki bölümde ayrıca başlatma düğmesini veya yoklamalar listesini göstermek için giriş sayfasına nasıl uygulandığını öğrendiniz.

Burada kalan tek bir yoklama sonuçları görünümünü ve oylama (Ayrıntılar) incelemektir.

Giriş sayfasından bir yoklama seçtiğinizde, uygulama için URL /poll/ gider\<anahtarı\> burada *anahtar* olduğundan anket için benzersiz tanımlayıcısı. İçinde *views.py* gördüğünüz gibi `details` işlevi bu URL hem GET hem de istekleri için yönlendirmeyi işler atanır. Bu kullanarak görebilirsiniz `<key>` URL rota hem hiçbir yolu bu formun aynı işleve eşlenir ve işlevi bu aynı ada sahip bir değişken oluşturur:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Bir yoklama (GET istekleri) göstermek için bu işlevi yalnızca üzerine çağırır *templates\details.html*, yoklama 's yinelenir `choices` dizi, her biri için bir radyo düğmesi oluşturma.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Çünkü **oy** düğmeye sahip `type="submit"`, seçerek oluşturan bir POST isteği geri yönlendirilir aynı URL'ye `details` bir kez daha işlev. Bu kez, ancak bu seçimi form verileri ayıklar ve için /results/ yönlendiren\<seçim\>.

/Results/\<anahtarı\> URL yönlendirileceğini ardından `results` işlevi *views.py*, daha sonra Anket'ın çağıran `calculate_stats` yöntemi ve gösteren *templates\results.html* işleme için:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

*Results.html* şablonu, bölüm yalnızca yoklama 's seçenekleri yinelenir ve her biri için bir ilerleme çubuğu oluşturur:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Visual Studio çözümünüzü kaynak denetimine Bu öğretici boyunca yürüten, artık başka bir işleme yapmak için iyi bir zamandır. Çözümünüzü öğretici kaynak kodu github'da eşleşmelidir: [Microsoft/python-örnek-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Artık Visual Studio'da "Boş Flask Web projesi", "[/Jade] Flask Web projesi" ve "Windows Flask [/Jade] polls – Webový projekt" şablonları tamamen incelediniz. Flask kullanarak şablonları, görünümleri ve yönlendirme gibi tüm temellerini öğrendiğinize göre ve yedekleme veri deposu kullanmayı gördünüz. Artık bir web uygulaması tüm görünümleri ve gereksinim modelleri kendi kullanmaya başlamak mümkün olması gerekir.

Bir web uygulaması geliştirme bilgisayarınızda çalışan uygulamayı müşterileriniz için kullanılabilir hale getirme, tek bir adımdır. Sonraki adımlar, aşağıdaki görevleri şunlardır:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz: [Azure App Service'e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- PostgreSQL, MySQL ve SQL Server'ın (her biri Azure üzerinde barındırılabilir) gibi başka bir üretim düzeyinde veri deposunu kullanan bir depo uygulaması ekleyin. Ayrıca [Python için Azure SDK'sı](azure-sdk-for-python.md) Cosmos DB yanı sıra tablo ve BLOB'ları gibi Azure depolama hizmetleriyle çalışmaya.

- Azure DevOps gibi bir hizmette bir sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. Kaynak denetimi (aracılığıyla Azure depoları veya GitHub ya da başka bir yerde) ile çalışma ek olarak, otomatik olarak yayın için bir önkoşul olarak birim testlerinizi çalıştırmak için bir Azure DevOps projesi yapılandırabilir ve ayrıca işlem hattı için bir hazırlık sunucusu dağıtmak için yapılandırma üretim ortamına dağıtmadan önce ek sınar. Ayrıca, Azure DevOps çözümlerini App Insights gibi izleme ile tümleşir ve Çevik planlama araçları ile tüm döngüyü kapatır. Daha fazla bilgi için [Azure DevOps projesi ile CI/CD işlem hattı oluşturma için Python](/azure/devops-project/azure-devops-project-python?view=vsts) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts).
