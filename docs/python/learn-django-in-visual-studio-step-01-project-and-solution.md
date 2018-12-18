---
title: Django öğreticide Visual Studio, 1. adım, Django temel bilgileri öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temel bilgileri bir kılavuz, Django geliştirme için Visual Studio destek gösteren sağlar.
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
ms.openlocfilehash: 549bd552cee0d9b833d1dee36f29f3a36b3f5f07
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061086"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Öğretici: Visual Studio'da Django web çerçevesi ile çalışmaya başlama

[Django](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir bir web geliştirme için tasarlanan yüksek düzeyli bir Python altyapısıdır. Bu öğretici, Django tabanlı web uygulamaları oluşturulmasını kolaylaştırmak için Visual Studio sağlayan proje şablonları bağlamında Django framework açıklar.

Bu öğreticide, şunların nasıl yapılır:

> [!div class="checklist"]
> - (1. adım) "Boş Django Web projesi" şablonu kullanarak bir Git deposunda bir temel Django projesi oluşturma
> - Bir sayfa ile bir Django uygulaması oluşturma ve bir şablonu (2. adım) kullanarak bu sayfa işleme
> - Statik dosyaları işleme, sayfalar eklemek ve şablonu devralma (3. adım) kullanın
> - Django Web projesi şablonu sayfaları ve duyarlı tasarım (4. adım) ile bir uygulama oluşturmak için kullanın
> - Kullanıcılar (5. adım) kimlik doğrulaması
> - Modelleri, veritabanı geçişlerini ve özelleştirmeleri yönetim arabirimi (6. adım) kullanan bir uygulamayı oluşturmak için yoklamalar Django Web projesi şablonu kullanın

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017'de Windows aşağıdaki seçeneklerle:
  - **Python geliştirme** iş yükü (**iş yükü** yükleyici sekmede). Yönergeler için [Visual Studio'da Python yükleme desteği](installing-python-support-in-visual-studio.md).
  - **Git için Windows** ve **Visual Studio için GitHub uzantısı** üzerinde **tek tek bileşenler** sekmesinde altında **kod Araçları**.

Ayrıntılar (özellikle farklı Django framework'ün önceki sürümleriyle) bu öğreticideki açıklanan gelen değişiklik gösterebilir Django proje şablonları da Visual Studio için Python Araçları'nın tüm eski sürümleri dahil edilmiştir.

Python geliştirme Visual Studio şu anda Mac için desteklenmiyor Mac ve Linux üzerinde kullanma [Python uzantı Visual Studio code'da](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio projeleri" ve "Django projeleri"

Django terminolojisinde, bir "Django projesi" uygulamalarının yanı sıra"tam web uygulaması oluşturmak için bir web ana bilgisayarı için dağıttığınız bir veya daha fazla" birkaç site düzeyli yapılandırma dosyalarından oluşur. Django projesi birden fazla uygulama içerebilir ve aynı uygulamanın birden fazla Django projelerinde olabilir.

Django projesi birden fazla uygulamalarının yanı sıra kendi bölümü için bir Visual Studio projesi içerebilir. Bu öğreticide yalnızca bir "projesine" başvuran her basitleştirmek amacıyla, Visual Studio projeye başvuruyor. Web uygulaması "Proje Django" bölümünü gösterir, "Django projesi" özellikle kullanır.

Bu öğretici boyunca her biri tek bir Django uygulaması içeren üç ayrı Django projeler içeren tek bir Visual Studio çözüm oluşturacaksınız. Aynı çözümdeki projeleri tutarak, kolayca geri ve İleri karşılaştırma için farklı dosyalar arasında geçiş yapabilirsiniz.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1. adım: Visual Studio'nun proje ve çözüm oluşturma

Django ile komut satırından çalışırken, genellikle bir proje çalıştırarak başlattığınız `django-admin startproject <project_name>` komutu. Visual Studio'da "Boş Django Web projesi" şablonu kullanarak bir Visual Studio Proje ve çözüm aynı yapısında sağlar.

1. Visual Studio'da **dosya** > **yeni** > **proje**"Django" için arama yapın ve seçin **boş Django Web projesi**  şablonu. (Şablon da altında bulunan **Python** > **Web** sol taraftaki listede.)

    ![Boş Django Web projesi için Visual Studio'da yeni proje iletişim kutusu](media/django/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlara (önceki grafikte gösterildiği gibi) aşağıdaki bilgileri girin ve ardından **Tamam**:

    - **Adı**: Visual Studio projenin adını ayarlayın **BasicProject**. Bu ad Django projesi için de kullanılır.
    - **Konum**: Visual Studio çözüm ve proje oluşturmak bir konum belirtin.
    - **Çözüm**: varsayılan olarak bu denetimi bırakın **yeni çözüm oluşturma** seçeneği.
    - **Çözüm adı**: kümesine **LearningDjango**, bu çözüm için uygun birden çok proje için bir kapsayıcı olarak Bu öğreticide.
    - **Çözüm için dizin oluştur**: bırakın (varsayılan) olarak ayarlayın.
    - **Yeni Git deposu oluşturma**: çözüm oluşturduğunda, Visual Studio yerel bir Git deposu oluşturur, böylece (varsayılan olarak temizleyin olan) bu seçeneği belirleyin. Bu seçeneği görmüyorsanız, Visual Studio 2017 Yükleyicisi'ni çalıştırın ve ekleme **Git için Windows** ve **Visual Studio için GitHub uzantısı** üzerinde **tek tek bileşenler** sekmesi altında **kod Araçları**.

1. Kısa bir süre sonra Visual Studio, bir iletişim bildiren ile ister **dış paketleri bu proje gerektirir** (aşağıda gösterilmiştir). Şablonun içerdiği için bu iletişim kutusu görünür bir *requirements.txt* en son Django 1.x paketini başvuran dosya. (Seçmek **gerekli paketleri Göster** tam bağımlılıkları görmek için.)

    ![Komut istemi bildiren proje dış paketleri gerektiriyor](media/django/step01-requirements-prompt-install-myself.png)

1. Seçeneğini **ben bunları kendim yükler**. Size kısa süre içinde kaynak denetiminden hariç tutuldu emin olmak için sanal ortamı oluşturun. (Ortam her zaman oluşturulabilir *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2. adım: Git denetimleri incelemek ve uzak bir depoyu Yayımla

Seçtiğiniz çünkü **yeni Git deposu Oluştur** içinde **yeni proje** iletişim kutusunda, projeyi zaten yerel kaynak denetimine oluşturma işlemi tamamlandıktan hemen sonra. Bu adımda, Visual Studio'nun Git denetimleriyle planladığınızdan ve **Takım Gezgini** kaynak denetimiyle çalışma penceresi.

1. Visual Studio ana penceresinde alt köşesine Git denetimleri inceleyin. Soldan sağa, bu denetimlerin gönderilmemiş işlemeler, kaydedilmemiş değişiklikler, deponun ve güncel dalınızın adını göster:

    ![Visual Studio penceresinde Git denetimleri](media/django/step01-git-controls.png)

    > [!Note]
    > Seçmezseniz **yeni Git deposu Oluştur** içinde **yeni proje** iletişim kutusunda, Git denetimlerini göster yalnızca bir **kaynak denetimine Ekle** yerel oluşturan komutu Depo.
    >
    > ![Ekleme kaynak denetimi Visual Studio'da görünür bir depo oluşturduysanız değil](media/django/step01-git-add-to-source-control.png)

1. Değişiklikleri düğmeyi seçin ve Visual Studio açar, **Takım Gezgini** penceresinde **değişiklikleri** sayfası. Yeni oluşturulan projeye zaten kaynak denetimi otomatik olarak kabul edilen olduğundan tüm bekleyen değişiklikleri görmüyorum.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/django/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda gönderilmemiş işlemeler düğmeyi seçin (yukarı ok ile **2**) açmak için **eşitleme** sayfasını **Takım Gezgini**. Yerel bir depo olduğundan, sayfa depo farklı uzak depoya yayımlamak için kolay seçenekler sunar.

    ![Takım Gezgini penceresini gösteren Git deposu için kullanılabilir seçenekleri kaynak denetimi](media/django/step01-team-explorer.png)

    Kendi projeleriniz için hangi hizmetin seçebilirsiniz. Bu öğreticide burada öğreticinin tamamlanmış örnek kodu korunur, GitHub kullanımı gösterilmiştir [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) depo.

1. Herhangi bir seçerken **Yayımla** denetimleri **Takım Gezgini** daha fazla bilgi için ister. Örneğin, Bu öğretici için örnek yayımlarken, havuz ilk olarak, bu durumda oluşturulması gerekiyordu **uzak depoya itme** seçeneği, deponun URL'si ile kullanıldı.

    ![Var olan bir uzak depoya gönderilirken için Takım Gezgini penceresi](media/django/step01-push-to-github.png)

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

Projeniz için yapılandırdığınız kaynak denetimi, proje için gerekli Django paketlerini içeren sanal bir ortam oluşturabilirsiniz. Ardından **Takım Gezgini** ortamın klasör, kaynak denetiminden hariç tutmak için.

1. İçinde **Çözüm Gezgini**, sağ **Python ortamları** düğümünü seçip alt **sanal ortama ekleme**.

    ![Çözüm Gezgini'nde sanal ortam komut ekleme](media/django/step01-add-virtual-environment-command.png)

1. Bir **sanal ortama ekleme** iletişim kutusu açılır, iletisini ile **requirements.txt dosyasını bulduk.** Bu ileti, Visual Studio, sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![Sanal ortama Ekle iletişim kutusu requirements.txt iletisi](media/django/step01-add-virtual-environment-found-requirements.png)

1. Seçin **Oluştur** Varsayılanları kabul etmek için. (İsterseniz, sanal ortamın adı yalnızca alt klasörünü adını değiştiren değiştirebilirsiniz ancak `env` standart bir kuraldır.)

1. Visual Studio indirmeleri ve paketleri, yani Django için kadar alt klasörler hakkında birkaç bin dosya içinde genişletme yükler için yönetici ayrıcalıkları onayı istenirse, sonra birkaç dakika bekleyin! Visual Studio ilerleme durumunu görebilirsiniz **çıkış** penceresi. Beklerken, soru bölümlerde düşünerek.

1. Visual Studio Git denetimlere (durum çubuğunda) değişiklik göstergesini seçin (gösteren **99&#42;**) açan **değişiklikleri** sayfasını **Takım Gezgini**.

    Sanal ortam oluşturma, değişiklikleri binin getirildi, ancak siz (veya herhangi başka bir proje kopyalama) ortamdan her zaman yeniden oluşturabilirsiniz çünkü bunların hiçbirine kaynak denetiminde eklemeniz gerekmez *requirements.txt* .

    Sanal ortam hariç tutmak için sağ **env** klasörü ve select **bu yerel öğeleri Yoksay**.

    ![Kaynak denetim değişikliklerini sanal bir ortamda yoksayılıyor](media/django/step01-ignore-local-items.png)

1. Sanal ortam hariç sonra yalnızca kalan proje dosyasına değişiklikler ve *.gitignore*. *.Gitignore* dosya sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayın

1. Bir işleme iletisi girin ve seçin **tümünü işle** düğmesine ve ardından işlemeler isterseniz, uzak depoya gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden bir sanal ortam oluşturmak istiyorum?

Yanıt: Sanal bir ortama uygulamanızın tam bağımlılıkları ayırmak için harika bir yoludur. Bu yalıtım global Python ortamı içinde çakışmaları önler ve test etme ve işbirliği kolaylık sağlar. Bir uygulama geliştirirken zaman içinde neredeyse şaşmaz biçimde birçok yararlı Python paketlerini getirin. Projeye özgü sanal bir ortamda paketleri tutarak, projenin kolayca güncelleştirebilirsiniz *requirements.txt* kaynak denetimine dahil bu ortamı tanımlayan dosya. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarlar dahil olmak üzere diğer herhangi bir bilgisayar için kopyalanan yalnızca kullanarak ortama yeniden oluşturmak daha kolaydır *requirements.txt* (neden olduğu ortam kaynak denetiminde olması gerekmez). Daha fazla bilgi için [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Kaynak denetimine zaten kararlıdır sanal bir ortama nasıl kaldırırım?

Yanıt: İlk olarak, Düzenle, *.gitignore* klasörü dışlamak için dosya: sonunda açıklamayı içeren bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için yeni bir satır ekleyin `/BasicProject/env`. (Visual Studio dosyayı göstermiyor çünkü **Çözüm Gezgini**, kullanarak doğrudan açmak **dosya** > **açın**  >   **Dosya** menü komutu. Dosyasını da açabilirsiniz **Takım Gezgini**: üzerinde **ayarları** sayfasında **depo ayarları**Git **yoksayma ve öznitelik dosyaları** bölümüne ve ardından **Düzenle** yanındaki bağlantı **.gitignore**.)

İkinci olarak, bir komut penceresi açın, gibi klasöre gidin *BasicProject* sanal ortam klasörü gibi içeren *env*, çalıştırıp `git rm -r env`. Ardından komut satırından bu değişiklikleri işleyebilir (`git commit -m 'Remove venv'`) veya gelen gerçekleştirmeyi **değişiklikleri** sayfasının **Takım Gezgini**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4. adım: ortak kod İnceleme

Proje oluşturma işlemi tamamlandıktan sonra ortak Django proje kodu inceleyin (olduğu yeniden CLI komutu tarafından oluşturulan aynı `django-admin startproject <project_name>`).

1. Projenizde köküdür *manage.py*, Visual Studio Proje başlangıç dosyası olarak otomatik olarak ayarlayan Django komut satırı yönetim yardımcı programı. Kullanarak komut satırı yardımcı programını çalıştırın `python manage.py <command> [options]`. Ortak Django görevler için Visual Studio uygun menü komutlarını sağlar. Projeye sağ **Çözüm Gezgini** seçip **Python** listesini görmek için. Bu öğretici sırasında bu komutlardan bazıları karşılaştığınız.

    ![Bir Python Django komutları proje bağlam menüsü](media/django/step01-django-commands-menu.png)

2. Projenizde bir klasör proje ile aynı adlandırılır. Bu temel Django proje dosyalarını içerir:

   - *__init.PY*: Python bu klasör bir Python paketi olduğunu söyler. boş bir dosya.
   - *wsgi.PY*: hizmet projenizi WSGI uyumlu web sunucuları için bir giriş noktası. Genellikle bu dosyanın şu şekilde bırakın-web sunucuları için üretim kancaları sağladığı aynıdır.
   - *Settings.PY*: bir web uygulaması geliştirme sırasında değiştiren Django projesi için ayarları içerir.
   - *URLs.PY*: geliştirme sırasında da değiştirmeniz Django projesi için içindekiler tablosu içerir.

     ![Çözüm Gezgini'nde proje dosyaları Django](media/django/step01-django-project-in-solution-explorer.png)

3. Daha önce belirtildiği gibi Visual Studio şablonu da ekler bir *requirements.txt* dosyası projenize Django paket bağımlılığı belirterek. Bu dosyanın varlığını ilk proje oluştururken bir sanal ortam oluşturmak için davet ' dir.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Ben diğer paketler yüklendikten sonra Visual Studio requirements.txt dosyasını bir sanal ortam oluşturabilir?

Cevap: Evet. Genişletin **Python ortamları** düğümünün sanal ortamınıza sağ tıklatın ve seçin **Generovat requirements.txt** komutu. Bu komutu düzenli olarak kullanmak için iyi ortamı değiştirin ve değişiklikleri işleme *requirements.txt* kaynak denetimine bağımlı bu ortamda herhangi bir kod değişikliği birlikte. Bir yapı sunucusunda sürekli tümleştirmeyi ayarlama, ortamı değiştirmek her dosya ve değişiklikleri oluşturmanız gerekir.

## <a name="step-1-5-run-the-empty-django-project"></a>1-5. adım: boş Django projeyi Çalıştır

1. Visual Studio'da **hata ayıklama** > **hata ayıklamayı Başlat** (**F5**) veya **Web sunucusu** (araç çubuğunda gördüğünüz bir tarayıcı farklılık gösterebilir):

    ![Web sunucusu araç çubuğu düğmesi Visual Studio'da çalıştırın.](media/django/run-web-server-toolbar-button.png)

1. Çalıştıran bir sunucuda anlamına gelir komutu çalıştırılarak `manage.py runserver <port>`, Django'nın yerleşik geliştirme sunucusu başlatır. Visual Studio diyorsa **hata ayıklayıcı başlatılamadı** sahip herhangi bir başlangıç dosyası hakkında bir ileti ile sağ **manage.py** içinde **Çözüm Gezgini** seçip**Başlangıç dosyası olarak ayarla**.

1. Sunucuyu başlatın görüntüler, aynı zamanda sunucu günlüğü'nü açın bir konsol penceresi görürsünüz. Visual Studio otomatik olarak bir tarayıcı açar `http://localhost:<port>`. Ancak, Django projesi hiçbir uygulama olduğundan, Django ne kadar kullandığınız düzgün çalıştığını onaylamak için yalnızca bir varsayılan sayfasını gösterir:

    ![Django projesi varsayılan görünüm](media/django/step01-first-run-success.png)

1. İşiniz bittiğinde, konsol penceresini kapatarak veya kullanarak sunucuyu Durdur **hata ayıklama** > **hata ayıklamayı Durdur** Visual Studio'daki komutu.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Soru: Bir web sunucusu gibi bir çerçeve Django mi?

Cevap: Evet ve Hayır. Django geliştirme amacıyla kullanılan bir yerleşik web sunucusu yok. Bu web sunucusu gibi ne zaman web uygulamasını yerel olarak çalıştırdığınızda neler kullanılır Visual Studio'da hata ayıklama. Ancak, bir web konağına dağıttığınızda, Django bunun yerine ana bilgisayarın web sunucusunu kullanır. *Wsgi.py* modülü Django projesinde, üretim sunucularına takma üstlenir.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Projenin Python menüdeki hata ayıklama menü komutları ve sunucu komutlarını kullanarak arasındaki fark nedir?

Yanıt: ek olarak **hata ayıklama** menü komutları ve araç çubuğu düğmeleri kullanarak da başlatabilirsiniz **Python** > **Server'i** veya **Python** > **Run hata ayıklama sunucusu** projenin bağlam menüsü komutları. Her iki komutu çalıştıran sunucunun yerel URL'sini (localhost:port) görebileceğiniz bir konsol penceresi açın. Ancak, bu URL ile bir tarayıcı el ile açmalısınız ve hata ayıklama sunucuda otomatik olarak Visual Studio hata ayıklayıcı başlatılamıyor. Kullanmak isterseniz, bir hata ayıklayıcı için çalışan işlemi daha sonra ekleyebilirsiniz **hata ayıklama** > **iliştirme** komutu.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Django projesi herhangi bir uygulama içermiyor. Sonraki adımda bir uygulama oluşturduğunuzda. Genellikle daha fazla Django projesi Django uygulamaları ile çalışmak için şu anda çok fazla ortak dosyaları hakkında bilmeniz gerekmez.

> [!div class="nextstepaction"]
> [Görünümleri ve şablonların ile bir Django uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- Django projesi kod: [ilk Django uygulamanızı yazmak, bölüm 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Yönetim yardımcı programı: [django yönetim ve manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Öğretici kaynak kodu github'da: [Microsoft/python-örnek-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
