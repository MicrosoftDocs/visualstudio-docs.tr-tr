---
title: Visual Studio 6. adım, proje şablonu yoklamalar Django öğreticide bilgi edinin
titleSuffix: ''
description: Visual Studio projeleri, özellikle yönetim özelleştirme gibi yoklamalar Django Web projesi şablonu özelliklerinin bağlamında Django temel bilgileri bir kılavuz.
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
ms.openlocfilehash: ecc0637495b484ae06cb0f18e45ba329c7fa3407
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062502"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>6. adım: yoklamalar Django Web projesi şablonu kullanın.

**Önceki adımda: [Django kullanıcıların kimlik doğrulaması](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio'nun "Django Web projesi" şablonu anladım şimdi üçüncü Django şablon "Yoklamalar Django Web aynı kod temeli üzerinde ve bir veritabanı ile çalışmaya gösterir projesi" bakabilirsiniz.

Bu adımda şunların nasıl yapılır:

> [!div class="checklist"]
> - Şablondan proje oluşturma ve veritabanı başlatılamıyor (adım 6 - 1)
> - Veri modelleri (6-2. adım) Anlama
> - Geçerli geçişleri (6-3. adım)
> - Proje şablonu (6-4. adım) tarafından oluşturulan şablonların ve görünümleri anlayın
> - Bir özel yönetim arabirimi (6-5. adım) oluşturma

Bu şablonu kullanılarak oluşturulan bir projeyi izleyerek elde edecekleriniz için benzer [ilk Django uygulamanızı yazma](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) Django belgeleri, öğretici. Web uygulaması yoklamalar görüntülemek ve bunları, anketler yoluyla yönetebileceğiniz bir özel yönetim arabirimini birlikte oylamak kişiler olanak sağlayan bir genel sitesi oluşur. Bu, "Django Web projesi" şablon olarak aynı kimlik doğrulama sistemini kullanır ve aşağıdaki bölümlerdeki Django modelleri olarak keşfedilen uygulama tarafından daha fazla veritabanının kullanılmasını sağlar.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>6-1. adım: projeyi oluşturmak ve veritabanı başlatma

1. Visual Studio'da Git **Çözüm Gezgini**, sağ **LearningDjango** daha önce Bu öğretici ve seçme içinde oluşturulan çözüm **Ekle**  >   **Yeni proje**. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, seçin **dosya** > **yeni** > **proje** yerine.)

1. Yeni Proje iletişim kutusunda, aramak ve seçmek **yoklamalar Django Web projesi** şablon "DjangoPolls" proje arayın ve seçin **Tamam**.

1. Diğer proje şablonları gibi Visual Studio'da, "Yoklamalar Django Web projesi" şablonu içeren bir *requirements.txt* , Visual Studio istemi ister nerede bu bağımlılıkların yükleneceği dosya. Seçeneğini **sanal bir ortama yükleme**hem de **sanal ortama ekleme** iletişim kutusunda **Oluştur** Varsayılanları kabul etmek için.

1. Python sanal ortamı kurma tamamlandıktan sonra görüntülenen yönergeleri izleyin *readme.html* veritabanı başlatmak ve Django süper kullanıcı (diğer bir deyişle, bir yönetici) oluşturun. İlk sağ adımlarla **DjangoPolls** projesi **Çözüm Gezgini**seçin **Python** > **Djangogeçirme** komutunu ve ardından projeyi sağ tıklatın, yeniden seçin **Python** > **Django yetkili kullanıcısı oluşturma** komutunu ve yönergeleri izleyin. (İlk süper kullanıcı oluşturmayı denerseniz, veritabanı henüz başlatılmamış olduğundan bir hata görürsünüz.)

1. Ayarlama **DjangoPolls** proje bu projeye sağ tıklayarak Visual Studio çözümü için varsayılan olarak **Çözüm Gezgini** seçerek **başlangıçprojesiolarakayarla**. Gösterilen başlangıç projesi içinde hata ayıklayıcısını başlattığınızda nelerin çalıştırılacağını kalın.

1. Seçin **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** server çalıştırmak için araç çubuğunda:

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama hakkında ev ve kişi, üst gezinti çubuğunda kullanma arasında gezinmek üç sayfa vardır. Bir veya iki uygulamanın farklı kısımlarını incelemek için dakika alın (hakkında ve ilgili kişi sayfaları "Django Web projesi" için çok benzer ve daha ayrıntılı olarak ele değildir).

    ![Yoklamalar Django Web projesi uygulamasının tam tarayıcı görünümü](media/django/step06-full-app-view.png)

1. Ayrıca seçin **Yönetim** yönetim arabirimini yalnızca yetkili olduğunu göstermek için bir oturum açma ekranı görüntüler Gezinti çubuğundaki bağlantı kimlik doğrulaması yöneticileri. Süper kullanıcı kimlik bilgilerini kullanın ve yönlendirilen "/ admin" sayfasında, bu proje şablonunu kullanarak, varsayılan olarak etkindir.

    ![Yoklamalar Django Web projesi uygulamasının yönetim görünümü](media/django/step06-polls-administrative-interface.png)

1. İzleyen bölümlerde için uygulamayı bırakabilirsiniz.

    Uygulamayı durdurmak istiyorsanız ve [değişiklikleri kaynak denetimine](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), ilk açın **değişiklikleri** sayfasını **Takım Gezgini**, sanal ortam (klasörünü sağ tıklatın büyük olasılıkla **env**) seçip **bu yerel öğeleri Yoksay**.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleyin

Önce belirtildiği gibi. neleri kadarını "Yoklamalar Django Web projesi" şablondan oluşturulmuş bir projeyi Visual Studio'daki diğer proje şablonları incelediniz, bilgi sahibi olmanız gerekir. Ek adımlar bu makalede daha önemli değişiklikler ve eklemeler, veri modelleri ve ek görünümler özetler.

### <a name="question-what-does-the-django-migrate-command-do"></a>Soru: Django geçişi komutu ne işe yarar?

Yanıt: **Django geçişi** komut özellikle çalıştırmaları `manage.py migrate` komut dosyalarını çalıştırır komutu, içinde *uygulama/geçişler* çalıştırmak daha önce yapmadıysanız klasör. Bu durumda, komutu çalıştırır *0001_initial.py* veritabanında gerekli şema ayarlamak için bu klasördeki betiği.

Geçiş betiği tarafından oluşturulan `manage.py makemigrations` uygulamanın tarayan komut *models.py* dosya, veritabanının geçerli durumu için karşılaştırır ve ardından veritabanı şemasına geçirmek için gereken komut dosyalarını oluşturur Geçerli modelleri eşleştirin. Bu özellik, Django güncelleştirin ve Modellerinizi zamanla değiştirme gibi son derece etkilidir. Oluşturma ve geçişin çalıştırılması, modeller ve veritabanı biraz güçlükle eşitleyin.

Bu makalenin devamındaki 6-3. adımda bir geçiş ile çalışır.

## <a name="step-6-2-understand-data-models"></a>6-2. adım: veri modelini anlama

Yoklama ve tercih ettiğiniz adlı uygulama için model tanımlı *app/models.py*. Her türeyen bir Python sınıfıdır `django.db.models.Model` ve yöntemlerini kullanan `models` gibi sınıf `CharField` ve `IntegerField` veritabanı sütunlara eşlemek modelinde alanlarını tanımlamak için.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Gördüğünüz gibi bir yoklama bir açıklama tutar, `text` alan ve bir yayım tarihi içinde `pub_date`. Bu alanlar için yoklama veritabanındaki mevcut yalnızca olanlardır; `total_votes` çalışma zamanında hesaplanan alan.

Seçim bir yoklama ilişkili `poll` alan, bir açıklama içeriyor `text`ve bu seçenek sayısını tutar `votes`. `votes_percentage` Alan çalışma zamanında hesaplanır ve veritabanında bulunamadı.

Alan türlerinin tam listesi `CharField` (sınırlı metin) `TextField` (sınırsız metin), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey`, ve `ManyToMany`. Her alan, gibi bazı özniteliklerini alır. `max_length`. `blank=True` Özniteliği anlamına gelir Bu alan isteğe bağlıdır; olur `null=true` değeri isteğe bağlı olduğu anlamına gelir. Ayrıca bir `choices` veri gösterimini/değer tanımlama grubu, bir dizideki değerleri sınırlar özniteliği. (Bkz [Model alanı referansı](https://docs.djangoproject.com/en/2.0/ref/models/fields/) Django belgelerinde.)

Tam olarak ne inceleyerek veritabanında depolanır onaylayabilirsiniz *db.sqlite3* gibi bir araç kullanarak proje dosyasında [SQLite tarayıcı](https://sqlitebrowser.org/). Veritabanında yabancı anahtar alanı gibi sağladığı bkz `poll` seçenek model olarak depolanan `poll_id`; Django işler eşlemeyi otomatik olarak.

Genel olarak, Django veritabanınızda çalışmak Django sizin adınıza temel alınan veritabanı yönetebilmeniz için özel olarak modelleriyle çalışma anlamına gelir.

### <a name="seed-the-database-from-samplesjson"></a>Çekirdek samples.json veritabanından

Başlangıçta veritabanı hiçbir yoklamalar içerir. Yönetim arabirimini kullanabilirsiniz "/ admin" el ile eklemek için URL yoklar ve ayrıca "/ üretim" sayfasında uygulamanın tanımlanan oy sayısı ile çekirdek veritabanı eklemek için çalışan sitesinde ziyaret edebilirsiniz *samples.json* dosya.

Django projenin *urls.py* eklenen bir URL deseni sahip `url(r'^seed$', app.views.seed, name='seed'),`. `seed` Görünümünde *app/views.py* yükler *samples.json* dosya ve gerekli model nesneleri oluşturur. Django sonra otomatik olarak eşleşen kayıtları temel alınan veritabanında oluşturur.

Kullanımına dikkat edin `@login_required` görünüm için yetki düzeyini belirtmek için dekoratör.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Etkisini görmek için hiçbir anketler, ilk görmek için uygulamayı çalıştırma henüz mevcut. Ardından "/ üretim" URL'sini ziyaret edin ve uygulama giriş sayfasına geri döndüğünde yoklamalar kullanılabilir duruma gelmiş görmeniz gerekir. Yeniden ham inceleyin rahatça *db.sqlite3* dosyası gibi bir araçla [SQLite tarayıcı](https://sqlitebrowser.org/).

![Kapsanan veritabanı içeren yoklamalar Django Web projesi uygulama](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Soru: Veritabanı başlatmak mümkün Django yönetim yardımcı programı kullanıyor mu?

Cevap: Evet, kullanabilirsiniz [django yönetim loaddata komut](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata) uygulamasında dengeli dağıtım sayfası olarak aynı görevi başarmak için. Tam web uygulaması üzerinde çalışırken, bir birleşimi iki yöntemden birini kullanabilirsiniz: bir veritabanı komut satırından başlatmak ve ardından çekirdek sayfada herhangi bir rastgele JSON göndermek bir API'ye burada yerine bağlı olan sabit kodlanmış bir dosya Dönüştür.

## <a name="step-6-3-use-migrations"></a>6-3. adım: geçişler kullanın

Çalıştırdığınızda `manage.py makemigrations` (Visual Studio'da bağlam menüsünü kullanarak) komut projesi oluşturduktan sonra dosyayı Django oluşturan *app/migrations/0001_initial.py* dosya. Bu dosya, ilk veritabanı tablolarını oluşturan bir betik içerir.

Kaçınılmaz olarak Modellerinizi için zaman içinde değişiklik yapacaksınız olduğundan, Django, temel alınan veritabanı şeması bu modelleri ile güncel tutmanızı kolaylaştırır. Genel iş akışı aşağıdaki gibidir:

1. ' Deki modellerde değişiklik, *models.py* dosya.
1. Visual Studio'da projeye sağ **Çözüm Gezgini** seçip **Python** > **Django olun geçişleri** komutu. Daha önce açıklandığı gibi bu komut, komut oluşturur. *uygulama/migrations* veritabanı geçerli durumunu yeni duruma geçirmek için.
1. Betikler için asıl veritabanını uygulamak için projeyi tekrar sağ tıklayıp **Python** > **Django geçişi**.

Taşı komutunu çalıştırdığınızda, hangi geçişleri gerekli Django uygular, verilen herhangi bir veritabanı için hangi geçişleri uygulanmış olan Django izler. Yeni, boş bir veritabanı oluşturursanız, örneğin, Taşı komutunu çalıştırma ile geçerli Modellerinizi güncel her geçiş öncesinde bir betik uygulayarak taşır. Birden çok model değişiklikleri yapın ve geliştirme bilgisayarında geçişleri oluşturmak, benzer şekilde, daha sonra toplu geçişlerin üretim veritabanınız üretim sunucunuzda Taşı komutunu çalıştırarak uygulayabilirsiniz. Django son üretim veritabanı geçişi bu yana oluşturulan geçiş betikleri yeniden uygulanır.

Bir model değiştirme etkisini görmek için aşağıdaki adımları deneyin:

1. İsteğe bağlı Yazar alanı, yoklama modele eklemek *app/models.py* sonra aşağıdaki satırı ekleyerek `pub_date` isteğe bağlı eklemek için alan `author` alan:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Dosyayı kaydedin ve ardından sağ **DjangoPolls** projesi **Çözüm Gezgini** seçip **Python** > **Django geçiş yapın**  komutu.
1. Seçin **proje** > **tüm dosyaları göster** yeni oluşturulan betikte görmek için komutu **geçişler** adı ile başlayan klasör  **002_auto_**. Dosya ve seçin, sağ tıklama **projeye dahil et**. Ardından seçebilirsiniz **proje** > **tüm dosyaları göster** yeniden orijinal görünüme geri yüklemek için. (Ayrıntılar için aşağıda ikinci soru bu adımı bakın.)
1. İsterseniz, Django önceki modeli durumundan yeni durum değişikliği nasıl komutlar incelemek için bu dosyayı açın.
1. Visual Studio projeyi tekrar sağ tıklayıp **Python** > **Django geçişi** veritabanına değişiklikleri uygulamak için.
1. İstenirse, veritabanı değişikliği onaylamak için uygun bir görüntüleyicisinde açın.

Genel olarak, Django'nın taşıma özelliğini, hiçbir zaman veritabanı şemanızı el ile yönetmeniz, anlamına gelir. Yalnızca değişiklik modellerinize, geçiş betikleri oluşturmak ve bunları Taşı komutu ile uygulayabilirsiniz.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Soru: modelleri için değişiklikleri yaptıktan sonra Taşı komutunu çalıştırma unutursam ne olur?

Yanıt: model veritabanında nedir eşleşmiyorsa, Django uygun özel durumlar ile çalışma zamanında başarısız olur. Örneğin, önceki bölümde gösterilenle model değişikliği geçirmek, parantezi unutsanız bile bir hata görürsünüz **sütun yok: app_poll.author**:

![Ne zaman model değişikliği geçişi yapılmamış gösterilen hata](media/django/step06-exception-when-forgetting-to-migrate.png)biçimindeki telefon numarasıdır.

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Soru: Django olun geçişleri çalıştırdıktan sonra Çözüm Gezgini yeni oluşturulan Göster komut neden olmaz mı?

Yanıt: ancak, yeni oluşturulan komut dosyalarını mevcut *uygulama/geçişler* klasör uygulanır çalıştırırken **Django geçişi** komutu, bunlar görünmez otomatik **çözümü Explorer** çünkü bunlar Visual Studio projesine eklendiniz değil. Onları görünür yapmak için önce seçin **proje** > **tüm dosyaları göster** menü komutu ya da aşağıdaki görüntüde gösterilen araç çubuğu düğmesi. Bu komut neden **Çözüm Gezgini** projeye eklemediniz öğeleri için bir noktalı anahat simgesini kullanarak proje klasöründen tüm dosyaları göster. Seçin ve eklemek istediğiniz dosyaların sağ **projeye dahil et**, hangi de içeren bunları sonraki işlemenizin ile kaynak denetimi.

![Çözüm Gezgini'nde proje komutu dahil](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Soru: hangi geçişleri Taşı komutunu çalıştırmadan önce uygulanacak görebilirim?

Cevap: Evet, kullanın [django yönetim showmigrations komut](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>6-4. adım: görünümleri anlayın ve sayfa proje şablonu tarafından oluşturulan şablonlar

Çoğu "Yoklamalar Django Web projesi" şablonu tarafından oluşturulan görünümlerini hakkında ve iletişim için görünümleri gibi sayfaları, "Django Web projesi" şablonu ile oluşturulan görünümleri, çalıştığınız ile Bu öğreticide daha önce çok benzerdir. Nedir uygulama giriş sayfası olarak bazı modelleri, kullanın yapmasıdır Yoklamalarda oy ve yoklama sonuçları görüntülemek için sayfa eklendi.

Başlangıç olarak, ilk satır Django projesinin `urlpatterns` içindeki dizi *urls.py* dosyasıdır daha fazlasını basit bir uygulama görünümüne yönlendirme. Bunun yerine, uygulamanın kendi çeker *urls.py* dosyası:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*App/urls.py* dosya biraz daha ilginç yönlendirme kod (Açıklama eklenen) içeriyorsa:

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Burada kullanılan daha karmaşık normal ifadeleri bilmiyorsanız ifadesine yapıştırabilirsiniz [regex101.com](https://regex101.com/) düz bir dilde bir açıklama. (Eğik çizgi kaçış gerekecektir `/` bir ters eğik çizgi ekleyerek `\` daha önce; kaçışı nedeniyle python'da gerekmez `r` ön ek dizesi "ham" anlamına gelir).

Django, söz dizimi içinde `?P<name>pattern` adlı bir grup oluşturur `name`, hangi geçirilen bağımsız değişkenler olarak göründükleri sırayla için görünümler. Daha önce gösterilen kod `PollsDetailView` ve `PollsResultsView` adlandırılmış bağımsız değişken almak `pk` ve `app.views.vote` adlandırılmış bağımsız değişken alan `poll_id`.

Görünümlerin birçoğu görünümü işlevinde yalnızca doğrudan başvuruların olmadığından atabilirsiniz *app/views.py*. Bunun yerine, çoğu bir sınıf türetildiği, aynı dosya içinde başvurmak `django.views.generic.ListView` veya `django.views.generic.DetailView`. Taban sınıfları sağlar `as_view` ele yöntemleri bir `template_name` şablonunu belirlemek için bağımsız değişken. `ListView` Giriş sayfasını, kullanılan temel sınıf ayrıca bekliyor bir `queryset` verileri içeren özellik ve `context_object_name` değişken adı şablonda, verileri bu durumda başvurmak istediğiniz özelliğiyle `latest_poll_list`.

İnceleyebilirsiniz artık `PollListView` giriş sayfası için tanımlanan şu şekilde de *app/views.py*:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Burada yapmış olan Görünüm (yoklama) çalışır ve geçersiz kılmalar modeli tanımlamak için `get_context_data` ekleme yöntemi `title` ve `year` bağlamı için değer.

Şablon setinin (*templates/app/index.html*) aşağıdaki gibidir:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Kısacası, şablon yoklama nesneleri listesini alan `latest_poll_list`ve yoklama 's kullanarak her anket bağlantısını içeren bir tablo satırının oluşturmak için bu listeyi gezinir `text` değeri. İçinde `{% url %}` etiketi, "app:detail" içinde url deseni başvurduğu *app/urls.py* ", kullanarak ayrıntılı" adlı `poll.id` bağımsız değişken olarak. Bu parametrenin etkisi, Django uygun desenini kullanarak, bir URL oluşturur ve bağlantısını kullanan ' dir. Bu bit geleceği anlamına gelir, bu URL deseni dilediğiniz zaman ve oluşturulan bağlantılar otomatik olarak değiştirebileceğiniz eşleşecek şekilde güncelleştirin.

`PollDetailView` Ve `PollResultsView` sınıfları *app/views.py* (burada gösterilmiyor) neredeyse aynı konum `PollListView` oldukları türetilmesi dışında `DetailView` yerine. Kendi ilgili şablonları *app/templates/details.html* ve *app/templates/results.html* uygun alanları çeşitli HTML denetimleri içinde modelleri ardından yerleştirebilirsiniz. Benzersiz bir parçada *details.html* olduğundan anket seçenekleri içinde bulunan bir HTML formu gönderildiğinde /vote URL'sine bir POST yapar. Daha önce görüldüğü gibi bu URL deseni yönlendirilir `app.views.vote`, gerçekleştirilen gibi (Not `poll_id` yeniden yönlendirme, bu görünüm için kullanılan normal ifadeyi adlandırılmış bir grupta olan bağımsız değişkeni):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Burada, görünüm kendi karşılık gelen bir şablonu diğer sayfalar gibi yok. Bunun yerine, 404 (birisi "oy/1a2b3c" gibi bir URL girer ihtimale) yoklama yoksa gösteren seçili yoklama doğrular. Ardından, oylayan seçimi yoklama için geçerli olduğundan emin olur. Aksi takdirde, `except` blok yalnızca bir hata iletisi ile yeniden Ayrıntılar sayfasını işler. Seçimi geçerliyse, görünüm oyu hesaplar ve sonuçları sayfasına yönlendirir.

## <a name="step-6-5-create-a-custom-administration-interface"></a>6-5. adım: özel yönetim arabirimi oluşturma

Son "Yoklamalar Django Web projesi" şablonu varsayılan Django yönetim arabirimini, 6-1. adım altında bu makalede daha önce gösterildiği gibi özel uzantılara parçalarıdır. Kullanıcı ve Grup Yönetimi, ancak hiçbir şey için daha fazla varsayılan arabirimi sağlar. Polls – proje şablonu de yoklamalar yönetmenize olanak tanıyan özellikler ekler.

İlk olarak, URL desenleri Django projesinin *urls.py* sahip `url(r'^admin/', include(admin.site.urls)),` ; varsayılan olarak dahil "Yönetim/doc" düzeni de dahil ancak kılınmıştır.

Uygulama, ardından dosyayı içeren *admin.py*, dahil edilmesi sayesinde yönetim arabirimini ziyaret ettiğinizde, Django otomatik olarak çalışan `django.contrib.admin` içinde `INSTALLED_APPS` dizisi *settings.py*. Bu dosyayı kod proje şablonu tarafından sağlanan aşağıdaki gibidir:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Gördüğünüz gibi `PollAdmin` sınıf türetilir `django.contrib.admin.ModelAdmin` ve adları kullanarak kendi alan sayısı özelleştirir `Poll` yönettiği modeli. Bu alanlar üzerinde açıklanmıştır [ModelAdmin seçenekleri](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) Django belgelerinde.

Çağrı `admin.site.register` sonra o sınıfın modeline bağlar (`Poll`) ve yönetim arabirimi içerir. Genel sonuç, aşağıda gösterilmiştir:

![Yoklamalar Django Web projesi uygulamasının yönetim görünümü](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Visual Studio çözümünüzü kaynak denetimine Bu öğretici boyunca yürüten, artık başka bir işleme yapmak için iyi bir zamandır. Çözümünüzü öğretici kaynak kodu github'da eşleşmelidir: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Artık Visual Studio'da "Boş Django Web projesi", "Django Web projesi" ve "Yoklamalar Django Web projesi" şablonları tamamen incelediniz. Django görünümleri ve şablonlar kullanma gibi tüm temellerini öğrendiğinize göre ve yönlendirme, kimlik doğrulaması ve veritabanı modelleri kullanarak denedikten. Artık tüm görünümleri ve gereksinim modelleri ile kendi web uygulaması oluşturma olanağına olmalıdır.

Bir web uygulaması geliştirme bilgisayarınızda çalışan uygulamayı müşterileriniz için kullanılabilir hale getirme, tek bir adımdır. Sonraki adımlar, aşağıdaki görevleri şunlardır:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz: [Azure App Service'e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- 404 sayfa adlı bir şablon oluşturarak özelleştirme *templates/404.html*. Varsa, Django, varsayılanın yerine bu şablonu kullanır. Daha fazla bilgi için [hata görünümleri](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) Django belgelerinde.

- Birim testleri yazmak *tests.py*; Visual Studio Proje şablonları için başlangıç noktası sağlar ve daha fazla bilgi bulunabilir [ilk Django uygulamanız bölüm 5 - test yazıyor](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) ve [Django içinde test](https://docs.djangoproject.com/en/2.0/topics/testing/) Django belgelerinde.

- Uygulama, PostgreSQL, MySQL ve SQL Server'ın (her biri Azure üzerinde barındırılabilir) gibi bir üretim düzeyinde veri deposuna SQLite değiştirin. Üzerinde açıklandığı [SQLite kullanıldığı durumlar](https://www.sqlite.org/whentouse.html) (sqlite.org) SQLite düşük ile 100 bin isabet sayısı günde en fazla orta düzeyde trafiğe sahip siteler için düzgün çalışır, ancak daha yüksek birimleri için önerilmez. Ayrıca tek bir bilgisayara limited, bu nedenle onu kullanılamaz Yük Dengeleme ve coğrafi çoğaltma gibi herhangi bir çok sunuculu senaryo. Diğer veritabanlarını Django'nın desteği hakkında daha fazla bilgi için bkz: [Veritabanı Kurulumu](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Ayrıca [Python için Azure SDK'sı](azure-sdk-for-python.md) tablo ve BLOB'ları gibi Azure depolama hizmetleriyle çalışmaya.

- Azure DevOps gibi bir hizmette bir sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. Kaynak denetimi (aracılığıyla Azure depoları veya GitHub ya da başka bir yerde) ile çalışma ek olarak, otomatik olarak yayın için bir önkoşul olarak birim testlerinizi çalıştırmak için bir Azure DevOps projesi yapılandırabilir ve ayrıca işlem hattı için bir hazırlık sunucusu dağıtmak için yapılandırma üretim ortamına dağıtmadan önce ek sınar. Ayrıca, Azure DevOps çözümlerini App Insights gibi izleme ile tümleşir ve Çevik planlama araçları ile tüm döngüyü kapatır. Daha fazla bilgi için [Azure DevOps projesi ile CI/CD işlem hattı oluşturma için Python](/azure/devops-project/azure-devops-project-python?view=vsts) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts).
