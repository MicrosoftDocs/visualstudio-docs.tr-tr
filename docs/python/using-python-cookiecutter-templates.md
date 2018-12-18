---
title: CookieCutter şablonları Python ile kullanma
description: Visual Studio şablonları Python kodu için keşfetmek ve bu şablonlardan projeler oluşturmak için grafik Cookiecutter uzantısını da destekler.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6ca47c1410fd11c32cbce95b9adc5a62c6c26dcf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057197"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter uzantısını kullanma

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları keşfedin, şablon seçeneklerini giriş ve projeleri ve dosyaları oluşturmak için bir grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ile eklemiştir ve Visual Studio'nun önceki sürümlerinde ayrı olarak yüklenebilir.

Cookiecutter gerektirir Python 3.3 veya üzeri (32 bit veya 64-bit) veya 3 4.2 veya üzeri Anaconda (32 bit veya 64-bit). Visual Studio, uygun bir Python yorumlayıcısı kullanılabilir durumda değilse bir uyarı görüntüler. Visual Studio çalışırken bir Python yorumlayıcısını yükleyerek tıklatmak **giriş** yeni yüklenen yorumlayıcı algılamak için Cookiecutter araç çubuğunda. (Bkz [Python ortamları](managing-python-environments-in-visual-studio.md) genel ortamlar hakkında daha fazla bilgi için.)

Yüklendikten sonra seçin **görünümü** > **Cookiecutter Explorer** kendi penceresini açmak için:

![Cookiecutter ana penceresi](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter iş akışı

İzleyen bölümlerde açıklanan aynıdır, Cookiecutter çalışmak tarama ve bir şablon seçerek, yerel bilgisayarınıza kopyalama seçeneklerini ayarlama ve bu şablondan kod oluşturma işlemi kullanır.

### <a name="browse-templates"></a>Şablonlara göz atın

Cookiecutter giriş sayfasında, aşağıdaki gruplar halinde düzenlenmiş aralarından seçim yapabileceğiniz şablonlarının bir listesi gösterilir:

| Grup | Açıklama |
| --- | --- |
| **Yüklendi** | Yerel bilgisayarınızda yüklü şablonlar. Çevrimiçi bir şablon kullanıldığında, havuz için bir alt otomatik olarak kopyalanmış olan *~/.cookiecutters*. Tuşlarına basarak seçilen yüklü şablon silebilmeniz için **Sil**. |
| **Önerilen** | Şablonlar, önerilen akıştan yüklendi. Varsayılan akış, Microsoft tarafından özenle seçilmiş içeriklerden oluşur. Bkz: [Cookiecutter seçenekleri](#cookiecutter-options) aşağıda akışı özelleştirme ile ilgili ayrıntılar. |
| **GitHub** | GitHub arama sonuçları cookiecutter anahtar sözcüğü. Github'dan sonuçları gelen geri sayfalandırılmış, daha fazla sonuç mevcutsa **yük daha fazla** listesinin sonunda görünür. |
| **Özel** | Arama kutusuna özel bir konuma girdikten sonra bu grupta görünür. Yerel diskinizde GitHub deposunu tam yolunu yazın veya bir klasörün tam yolunu kullanabilirsiniz. |

### <a name="cloning"></a>Kopyalama

Ardından bir şablonu seçtiğinizde **sonraki**, Cookiecutter çalışabilmesi için yerel bir kopyasını getirir.

Bir şablondan seçerseniz **önerilen** veya **GitHub** grupları veya arama kutusuna özel bir URL girin ve bu şablonu seçin, kopyalanan ve yerel bilgisayarınızda yüklü. Bu şablon, Visual Studio'nun önceki bir oturumda yüklediyseniz, otomatik olarak silinir ve en son sürümü kopyalanabilir.

Bir şablondan seçerseniz **yüklü** grubuna veya arama kutusuna bir özel klasör yolu girin ve bu şablonu Visual Studio Şablon Kopyalama olmadan yükler.

> [!Important]
> Cookiecutter Şablonları altındaki tek bir klasöre kopyalanan *~/.cookiecutters*. GitHub kullanıcı adını içermez git deposu adından sonra her alt olarak adlandırılır. Aynı ada sahip farklı yazarların gelen farklı şablonları kopyalarsanız çakışmalar ortaya çıkabilir. Bu durumda, Cookiecutter aynı ada sahip farklı bir şablonla mevcut şablonun üzerine yazılmasını önler. Diğer şablon yüklemek için önce var olan bir silmeniz gerekir.

### <a name="set-template-options"></a>Şablon seçeneklerini ayarlama

Cookiecutter, şablonu yerel olarak yüklendikten sonra diğer seçenekleri yanı sıra dosyaları oluşturmak için kullanılan Cookiecutter istediğiniz belirleyebileceğiniz bir seçenekler sayfası görüntüler:

![Cookiecutter Seçenekleri sayfası](media/cookiecutter-template-options.png)

Her Cookiecutter şablonu kendi seçenekleri kümesi tanımlar ve her biri (önerilen her bir giriş alan metin olarak gösterilir) için varsayılan bir değer belirtir. Genellikle diğer seçenekleri kullanan dinamik değer olduğunda varsayılan değeri bir kod parçacığı olabilir. 

Belirli seçenekler için varsayılan değerleri bir kullanıcı yapılandırma dosyasını özelleştirmek mümkündür. Cookiecutter uzantısını bir kullanıcı yapılandırma dosyası algıladığında, Kullanıcı Yapılandırması'nın varsayılan değerlerle şablonun varsayılan değerleri geçersiz kılar. Bu davranışı içinde ele alınmıştır [Kullanıcı Yapılandırması](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) Cookiecutter belgelerin bölümü.

Şablon sonra kod oluşturma, ek bir çalıştırmak için belirli Visual Studio görevleri belirtiyorsa **tamamlanma ek görevleri çalıştırma** dışında bu görevleri kabul etmek izin veren seçeneği görüntülenir. En yaygın görev bir web tarayıcısı açın, dosyaları düzenleyicide açın, bağımlılıkları yükler ve benzeri için kullanılır.

### <a name="create"></a>Create

Seçeneklerinizi ayarladıktan sonra seçin **Oluştur** (bir uyarı görünür çıkış klasörü boş değilse) kodu oluşturmak için. Şablonun çıkışıyla biliyor ve dosyaların üzerine sorun varsa, uyarıyı yok sayabilirsiniz. Aksi takdirde seçin **iptal**, boş bir klasör belirtin ve sonra el ile oluşturulan dosyalar, boş olmayan çıkış klasörüne kopyalayın.

Dosyalar başarıyla oluşturulduktan sonra Cookiecutter dosyaları açmak için bir seçenek sunar. **Çözüm Gezgini**:

![Cookiecutter gösteren Çözüm Gezgini komutu](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter seçenekleri

Cookiecutter seçenekleri aracılığıyla kullanılabilir **Araçları** > **seçenekleri** > **Cookiecutter**:

![Cookiecutter seçenekleri](media/cookiecutter-tools-options.png)

| Seçenek | Açıklama |
| --- | --- |
| **Önerilen akış URL'si** | Akış önerilen Şablonları konumu. Bir URL veya yerel bir dosyaya bir yolu olabilir. URL varsayılan Microsoft seçkin akışı kullanmak için boş bırakın. Akış karakterleriyle ayrılan şablon konumları, basit bir listesini sağlar. Seçkin akış değişiklik isteğinde bulunmak için bir çekme isteği yapmak [GitHub üzerinde kaynak](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Yardımı Göster** | Cookiecutter pencerenin üst kısmındaki Yardım bilgi çubuğunun görünürlüğünü denetler. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Cookiecutter şablonları Visual Studio için en iyi duruma getirme

Bir Cookiecutter şablonu yazma temel bilgileri için bkz: [Cookiecutter belgeleri](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Cookiecutter uzantısını Visual Studio için Cookiecutter v1.4 için oluşturulan şablonlarını destekler.

Varsayılan şablon değişkenleri işlenmesi (dize veya listesi) veri türüne bağlıdır:

- Dizesi: Değişken adı, değer ve varsayılan değer gösteren bir filigran girmek için metin kutusu etiketi. Araç İpucu metin kutusundaki varsayılan değeri gösterir.
- Listesi: Değişken adı, bir değer seçmek için açılan kutusu etiketi. Araç İpucu birleşik giriş kutusundaki varsayılan değeri gösterir.

Bu işleme hakkında ek meta verilerinde belirterek artırmak mümkündür, *cookiecutter.json* dosyasını Visual Studio'da belirli (ve Cookiecutter CLI tarafından yoksayılır). Tüm özellikleri isteğe bağlıdır:

| Özellik | Açıklama |
| --- | --- |
| Etiketle | Değişken adı yerine bir değişken için Düzenleyici üzerinde görünen belirtir. |
| Açıklama | Bu değişken için varsayılan değer yerine düzenleme denetiminde görünen araç ipucu belirtir. |
| URL | URL gösteren bir araç ipucu ile bir köprü etiketi değiştirir. Köprü metnine tıklayarak, bu URL için kullanıcının varsayılan tarayıcı açılır. |
| Seçici | Bir değişken için düzenleyicinin özelleştirme yapmanıza izin verir. Şu anda desteklenen aşağıdaki Seçici:<ul><li>`string`: Standart metin kutuları, dizeler için varsayılan.</li><li>`list`: Standart Kombo kutusu listeleri için varsayılan.</li><li>`yesno`: Arasında seçim yapma birleşik giriş kutusu `y` ve `n`, dizeleri.</li><li>`odbcConnection`: Metin kutusunda bir **...**  düğme bir veritabanı bağlantısı iletişim kutusunu açar.</li></ul> |

Örnek:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Visual Studio görevleri çalıştırma

Cookiecutter denilen bir özelliği olan *Post-Generate kancaları* dosyalar oluşturulduktan sonra rasgele Python kodu çalıştırmak için sağlar. Esnek olsa da, Visual Studio için kolay erişim izin vermez.

Örneğin, bir dosya Visual Studio düzenleyicisinde veya kendi web tarayıcısında açın ya da sanal bir ortam oluşturun ve paketi gereksinimleri yüklemek ister Visual Studio UI tetiklemek isteyebilirsiniz.

Bu senaryolar izin vermek için Visual Studio genişletilmiş meta verilerinde arar *cookiecutter.json* oluşturulan dosyaları kullanıcı açıldıktan sonra çalıştırılacak komutları açıklayan **Çözüm Gezgini** veya sonra dosyaları mevcut bir projeye eklenir. (Kullanıcı temizleyerek çalışan görevlerin dışında yeniden kaydolmayı seçebilirsiniz **tamamlanma ek görevleri çalıştırma** şablon seçeneklerinde.)

Örnek:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Komutlar adıyla belirtilen ve Visual Studio'nun yerelleştirilmiş yüklenir çalışmaya yerelleştirilmemiş (İngilizce) adı kullanmanız gerekir. Test ve Visual Studio komut adlarını Bul **komut** penceresi.

Tek bir bağımsız değişken olarak geçirmek istiyorsanız, önceki örnekteki gibi bir dize olarak belirtin.

Bağımsız değişken geçirmeniz gerekmez, boş bir dize bırakın veya JSON'dan atlayın:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Birden çok bağımsız değişkeni için bir dizi kullanın. Anahtarlar, anahtarını ve değerini ayrı bağımsız değişkenleriyle bölme ve uygun Alıntısı kullanın. Örneğin:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Bağımsız değişkenler, diğer Cookiecutter değişkenlere başvurabilir. İç Yukarıdaki örneklerde `_output_folder_path` değişkeni oluşturulan dosyalar için mutlak bir yol oluşturmak için kullanılır.

Unutmayın `Python.InstallProjectRequirements` komut dosyaları var olan bir projeye eklerken çalışır. Bu sınırlama komutu Python projede tarafından işlendiğinden var **Çözüm Gezgini**, ve proje hata iletilerini yok **Çözüm Gezgini**  -   **Klasör görünümü**. Sınırlama win gelecek sürümlerinden kaldırılacak umuyoruz (ve daha iyi **klasör görünümü** genel destekler).

## <a name="troubleshooting"></a>Sorun giderme

### <a name="error-loading-template"></a>Hata yükleme şablonu

Geçersiz veri türleri, boolean gibi bazı şablonlar, kullanabilecek kendi *cookiecutter.json*. Bu tür örnekleri için şablon yazarı seçerek raporu **sorunları** şablon bilgi bölmesinde bağlantı.

### <a name="hook-script-failed"></a>Kanca betiği başarısız oldu

Bazı şablonlar Cookiecutter Arabirimiyle uyumlu olmayan oluşturma sonrası betiklerini kullanabilirsiniz. Örneğin, komut dosyaları kullanıcı girişi için bir terminal Konsolu olmaması nedeniyle başarısız sorgu.

### <a name="hook-script-not-supported-on-windows"></a>Windows üzerinde desteklenmeyen komut bağlama

Son betik ise *.sh*, sonra da Windows bilgisayarınızda bir uygulama ile ilişkilendirilmiş olmayabilir. Uyumlu bir uygulama Windows Mağazası'nda bulmak isteyen bir Windows iletişim kutusu görebilirsiniz.

### <a name="templates-with-known-issues"></a>Şablonlar ile ilgili bilinen sorunlar

Hataları kopyalayın:

- **wildfish/cookiecutter-django-crud** (geçersiz karakter `|` alt klasör adı)
- **cookiecutter pyvanguard** (geçersiz karakter `|` alt klasör adı)

Yükleme Hataları:

- **chrisdev/wagtail-cookiecutter-foundation** (bir boolean türünde kullanan *cookiecutter.json*)
- **cookiecutter/quintoandar-android** (şablon klasör)

Hataları çalıştırın:

- **iknite/cookiecutter-ansible-rol** (post kanca betik konsol girdisi gerektirir)
- **benregn/cookiecutter-django-ansible** (Jinja hata)

Kullanan bash (Önemli değil):

- **openstack-dev/cookiecutter**
