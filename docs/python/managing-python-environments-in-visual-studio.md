---
title: Python ortamları ve yorumlayıcılarını yönetin
description: Genel, sanal yönetmek için Python ortamları penceresi ve Python yorumlayıcılarını ve paketleri yükleme ve Visual Studio projelerine ortamları atama conda ortamları kullanın.
ms.date: 12/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 887776b3a3f1275b97b2abee26c4613d8aad39fc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063224"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Oluşturma ve Visual Studio'da Python ortamlarını yönetme

Bir Python *ortam* conda ortamları ise, Python kodunu çalıştırma ve içeren genel, sanal bir bağlamı. Bir ortam yorumlayıcıyı, bir kitaplık (genellikle Python standart kitaplığı) ve yüklü paketleri kümesi oluşur. Bu bileşenler birlikte hangi dil yapıları ve söz dizimi geçerli olduğunu belirler hangi işletim sistemi işlevselliği erişebilir ve hangi paketler kullanabilirsiniz.

Windows üzerinde Visual Studio'da kullandığınız **Python ortamları** ortamlarını yönetin ve yeni projeler için varsayılan olarak, bu makalede açıklanan şekilde penceresi. Diğer yönleri ortamlar, aşağıdaki makaleler de bulunur:

- Verilen herhangi bir proje için yapabilecekleriniz [belirli bir ortam seçin](selecting-a-python-environment-for-a-project.md) yerine varsayılan kullanın.

- Oluşturma ve Python projeleri için sanal ortamları kullanma hakkında daha fazla bilgi için bkz [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Bir ortamda paketleri yüklemek isterseniz, başvurmak [paketleri sekmesinde başvuru](python-environments-window-tab-reference.md#packages-tab).

- Başka bir Python yorumlayıcısını yükleyerek için bkz: [yüklemeniz Python yorumlayıcılarını](installing-python-interpreters.md). İndir ve ana hat bir Python dağıtım için bir yükleyici çalıştırın, genel olarak, Visual Studio yeni yükleme ve ortam görünür olduğunu algılar **Python ortamları** penceresi ve projeleri için seçilebilir.

Visual Studio'da Python yeniyseniz, aşağıdaki makaleler de genel arka planından sunar:

- [Visual Studio'da Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio'da Python desteğini yükleme](installing-python-support-in-visual-studio.md)

> [!Note]
> Ortamlar için yalnızca bir klasörü kullanılarak olarak açıldığında bir Python kodu yönetemez **dosya** > **açık** > **klasör** komutu. Bunun yerine, [varolan koddan bir Python projesi oluşturma](quickstart-01-python-in-visual-studio-project-from-existing-code.md) ortamı özellikleri Visual Studio'nun yararlanabilmek için.

## <a name="the-python-environments-window"></a>Python ortamları penceresi

*(Bu bölümde gösterilen ekran görüntüleri, Visual Studio 15,8 temsil eder. "Farklı bir kullanıcı Arabirimi Visual Studio sürümünüze bağlı olarak görebilirsiniz.)*

Visual Studio bildiği ortamlar görüntülenir **Python ortamları** penceresi. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

- Seçin **görünümü** > **diğer Windows** > **Python ortamları** menü komutu.
- Sağ **Python ortamları** bir proje için düğüm **Çözüm Gezgini** seçip **tüm Python ortamları görüntüleme**:

    ![Çözüm Gezgini görünümü tüm ortamları komutu](media/environments-view-all.png)

Her iki durumda da **Python ortamları** penceresi görünür yanı sıra **Çözüm Gezgini**:

![Python ortamları penceresi](media/environments-default-view.png)

Visual Studio kayıt defterini kullanarak yüklü genel ortamlar için görünür (aşağıdaki [CESARETLENDİRİCİ 514](https://www.python.org/dev/peps/pep-0514/)), yanı sıra sanal ortamları ve conda ortamları (bkz [çeşitli ortamlarda](#types-of-environments)). Listenin beklenen bir ortamda görmüyorsanız bkz [el ile bir ortamı tanımlamanız](#manually-identify-an-existing-environment).

Listeden bir ortam seçin, Visual Studio çeşitli özellikler ve o ortama ait komutları görüntüler **genel bakış** sekmesi. Örneğin, yukarıdaki görüntüde Yorumlayıcı'nın konumunun gördüğünüz *C:\Python36-32*. Sayfanın alt kısmında dört komuttan **genel bakış** sekmesini yorumlayıcı ile çalışan bir komut istemi açın. Daha fazla bilgi için [Python ortamları penceresi Sekme Başvurusu - genel bakış](python-environments-window-tab-reference.md#overview-tab).

Farklı sekmelere gibi geçmek için ortamları listesinin altındaki açılır listede kullanmak **paketleri**, ve **IntelliSense**. Bu sekme ayrıca açıklanan [Python ortamları penceresi sekme başvurusu](python-environments-window-tab-reference.md).

Bir ortam seçerek onun için herhangi bir projeyi değiştirmez. Kalın listesinde gösterilen varsayılan, tüm yeni projeler için Visual Studio kullanan bir ortamdır. Farklı bir ortama yeni projeleri ile kullanmak için **varsayılan ortama yeni projeler için bunu yap** komutu. Bir proje bağlamında, her zaman belirli bir ortama seçebilirsiniz. Daha fazla bilgi için [bir proje için bir ortam seçin](selecting-a-python-environment-for-a-project.md).

Listelenen her bir ortamın sağda açılan bir denetimdir bir **etkileşimli** penceresi bu ortam için. (Visual Studio 2017 15.5 ve önceki sürümlerinde, başka bir denetimi bu ortam için IntelliSense veritabanı yenileyen görünür. Bkz: [ortamları penceresi sekme başvurusu](python-environments-window-tab-reference.md#intellisense-tab) veritabanı hakkındaki ayrıntılar için.)

> [!Tip]
> Genişlettiğinizde **Python ortamları** penceresinde yetecek kadar geniş bir irdelemesi çalışmak daha kullanışlı bulabilirsiniz ortamlarınızda görünümünü alın.
>
> ![Python ortamları penceresi Genişletilmiş Görünümü](media/environments-expanded-view.png)

> [!Note]
> Visual Studio sistem site paketleri seçeneği uyar olsa da, bunu Visual Studio içinden gelen değiştirmek için bir yol sağlamaz.

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Microsoft Virtual Academy) videoyu](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (2 dk. 35s) Visual Studio'da Python ortamlarında.|

### <a name="what-if-no-environments-appear"></a>Peki ortamı yok görünüyor?

Ortam görünüyorsa, standart konumda herhangi bir Python yüklemelerini algılamak Visual Studio başarısız anlamına gelir. Örneğin, edebilirsiniz Visual Studio 2017 yüklü, ancak Python iş yükü için yükleyici seçenekleri tüm yorumlayıcı seçeneklerinde temizlenir. Benzer şekilde, Visual Studio 2015 veya önceki bir sürümünü yüklemiş olabilirsiniz ancak yorumlayıcıyı el ile yüklenmedi (bkz [yüklemeniz Python yorumlayıcılarını](installing-python-interpreters.md)).

Python yorumlayıcısı bilgisayarınızda yüklü, ancak Visual Studio (herhangi bir sürüm) değil, algılayabilir, ardından kullanmak biliyorsanız **+ özel** konumuna el ile belirtmek için komutu. Sonraki bölüme bakın [el ile bir ortamı tanımlamanız](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio güncelleştirmeleri Python 2.7.11'i için yükleyicileri python.org gelen kullanarak 2.7.14 yükseltme gibi mevcut bir yorumlayıcı algılar. Eski ortam yükleme işlemi sırasında kaybolur **Python ortamları** yerinde güncelleştirme görünmeden önce listesi.
>
> Ancak, el ile yorumlayıcıyı ve dosya sistemi kullanılarak ortam taşırsanız, Visual Studio yeni konuma bilemezsiniz. Daha fazla bilgi için [yorumlayıcıyı taşıma](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Çeşitli ortamlarda

Visual Studio çalışabilir ile küresel, sanal ve conda ortamları.

#### <a name="global-environments"></a>Genel ortam

Her bir Python yükleme (örneğin, Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0, vs. bkz [yüklemeniz Python yorumlayıcılarını](installing-python-interpreters.md)) kendi tutar *genel ortam*. Her ortam, belirli bir Python yorumlayıcısı, kendi standart kitaplığı, bir dizi önceden yüklenmiş paketler ve bu ortamda etkinleştirilen yüklerken herhangi bir ek paket oluşur. Genel bir ortama bir paket yükleme o ortamı kullanarak tüm projeleri için kullanılabilir yapar. Ortam dosya sisteminin korumalı alanında bulunuyorsa, (içinde *c:\program files*, örneğin), sonra da paketleri yüklemek için yönetici ayrıcalıkları gerekiyor.

Genel ortamları, bilgisayardaki tüm projeleri için kullanılabilir. Visual Studio'da bir proje için başka bir özellikle seçmediğiniz sürece, tüm projeler için kullanılan varsayılan olarak genel bir ortam seçin. Daha fazla bilgi için [bir proje için bir ortam seçin](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Sanal ortamlar

Genel bir ortamda çalışmaya başlamak için kolay bir yolu olsa da, bu ortamda zaman içinde farklı projeler için yüklediğiniz birçok farklı paketleriyle dağınık hale gelecektir. Bu tür dağınıklığı tam olarak bir yapı sunucusu veya web sunucusu üzerinde ayarladığınız ortam türü belirli bir paket bilinen sürümleriyle kümesinde bir uygulamayı sınamanız zorlaştırır. İki proje uyumsuz paketler veya aynı paketin farklı sürümlerini gerektiğinde çakışmaları da meydana gelebilir.

Bu nedenle geliştiriciler genellikle oluşturma bir *sanal ortam* için bir proje. Bir sanal ortam, belirli bir yorumlayıcı bir kopyasını içeren bir proje klasörüdür. Sanal ortam etkinleştirdiğinizde, yüklediğiniz tüm paketler yalnızca söz konusu ortamın alt klasörüne yüklenir. Ardından söz konusu ortamdaki bir Python programını çalıştırdığınızda, yalnızca bu belirli paketleri karşı çalıştığını bildirin.

Visual Studio, bir sanal ortam için bir proje oluşturmak için doğrudan desteği sağlar. Örneğin, içeren bir projeyi açarsanız bir *requirements.txt*, veya bu dosyayı içeren bir şablondan bir proje oluşturun, Visual Studio otomatik olarak bir sanal ortam oluşturacak ve bu bağımlılıkların yüklemek ister .

Açık bir proje içinde herhangi bir zamanda yeni bir sanal ortam oluşturabilirsiniz. İçinde **Çözüm Gezgini**, proje düğümünü genişletin, sağ **Python ortamları**ve "Sanal ortam Ekle"'i seçin Daha fazla bilgi için [sanal ortam Oluştur](selecting-a-python-environment-for-a-project.md#create-a-virtual-environment).

Visual Studio ayrıca sağlar oluşturmak için bir komutu bir *requirements.txt* ortamında diğer bilgisayarlar üzerinde yeniden kolaylaştıran bir sanal ortamda dosyasından. Daha fazla bilgi için [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Conda ortamları

Conda ortam biridir kullanılarak oluşturulan `conda` aracı veya tümleşik conda Yönetimi'nde Visual Studio 2017 sürüm 15.7 ve üzeri. (Anaconda veya Miniconda gerektirir; Visual Studio yükleyicisi anaconda kullanılabilir, bkz: [yükleme - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

1. Seçin **+ conda ortam Oluştur** içinde **Python ortamları** açılır penceresinde bir **yeni conda ortam Oluştur** sekmesinde:

    ![Yeni bir conda ortamı için sekmesinde oluşturun](media/environments-conda-1.png)

1. Ortamda için bir ad girin **adı** alanında, temel bir Python yorumlayıcısı içinde seçin **Python** alan ve seçim **Oluştur**.

1. **Çıkış** penceresi oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleri ile yeni bir ortam için ilerleme durumunu gösterir:

    ![Conda ortam oluşturma başarılı](media/environments-conda-2.png)

1. Visual Studio içinde herhangi bir ortam üzerinde açıklandığı gibi bir proje için bir conda ortamı etkinleştirebilir [bir proje için bir ortam seçin](selecting-a-python-environment-for-a-project.md).

1. Ortamınıza paketleri yüklemek için kullanın [paketleri sekmesinde](python-environments-window-tab-reference.md#packages-tab).

> [!Note]
> Conda ortamları ile en iyi sonuçları almak için conda 4.4.8 kullanın veya üzeri (conda sürümleri Anaconda sürümlerinden farklı). Anaconda 5.1, Visual Studio 2017 Yükleyicisi'nden yükleyin.

Conda ortamları depolandığı, conda sürümü ve diğer bilgileri görmek için şunu çalıştırın `conda info` bir Anaconda komut isteminde (diğer bir deyişle, Anaconda yolu olduğu bir komut istemi):

```cli
conda info
```

Conda ortam klasörlerinizi şu şekilde görünür:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Conda ortamları içeren bir proje depolanmadığından bunlar genel ortamlara benzer şekilde davranır. Örneğin, conda ortamına yeni bir paket yükleme, paketin bu ortam kullanarak tüm projeleri için kullanılabilir hale getirir.

İçin Visual Studio 2017 sürüm 15.6 ve önceki sürümleri, kendisine altında açıklandığı gibi manuel olarak işaret ederek conda ortamları kullanabilirsiniz [el ile bir ortamı tanımlamanız](#manually-identify-an-existing-environment).

Visual Studio 2017 sürüm 15.7 ve üzeri conda ortamları otomatik olarak algılar ve bunları görüntüler **Python ortamları** sonraki bölümde açıklandığı gibi penceresi.

## <a name="manually-identify-an-existing-environment"></a>El ile bir ortamı tanımlayın

(Visual Studio 2017 sürüm 15.6 ve önceki conda ortamları dahil olmak üzere) standart olmayan bir konumda yüklü olduğu bir ortamı tanımlamak için aşağıdaki adımları kullanın:

1. Seçin **+ özel** içinde **Python ortamları** açılır penceresinde **yapılandırma** sekmesinde:

    ![Yeni özel bir ortam için varsayılan görünüm](media/environments-custom-1.png)

1. Ortamda için bir ad girin **açıklama** alan.

1. Girin veya gözatın (kullanarak **...** ) yorumlayıcıda yoluna **ön ek yolu** alan.

1. Visual Studio bu konuma (örneğin, yol conda ortamı için aşağıda gösterilen) bir Python yorumlayıcısı algılarsa, bağlayabileceğinizi **otomatik algıla** komutu. Seçme **otomatik algıla** kalan alanları tamamlar. Bu alanları el ile tamamlayabilirsiniz.

    ![Otomatik Algıla komutu etkinleştirme](media/environments-custom-2.png)

    ![Otomatik Algıla kullandıktan sonra ortamı alanlarının tamamlama](media/environments-custom-3.png)

1. Alanları istediğiniz değerleri içeren bir kez seçin **Uygula** yapılandırmayı kaydetmek için. Artık Visual Studio içindeki diğer gibi ortam kullanabilirsiniz.

1. El ile tanımlanan ortam kaldırmanız gerekirse, seçin **Kaldır** komutunu **yapılandırma** sekmesi. Bu seçenek otomatik olarak algılanan ortamları sağlamaz. Daha fazla bilgi için [yapılandırma sekmesinden](python-environments-window-tab-reference.md#configure-tab).

## <a name="fix-or-delete-invalid-environments"></a>Düzeltme ya da geçersiz ortamları silme

Visual Studio, bir ortam için kayıt defteri girdileri bulur, ancak yorumlayıcı yolu geçersiz sonra **Python ortamları** penceresi bir üstü çizili yazı tipi adıyla gösterir:

![Geçersiz bir ortam gösteren Python ortamları penceresi](media/environments-invalid-entry.png)

Korumak istediğiniz ortam düzeltmek için önce kendi Yükleyicisi'nin kullanmayı deneyin **onarım** işlem. Yükleyicileri standart Python 3.x, örneğin, bu seçenek içerir.

Bir ortam düzeltmek için Onar seçeneğini yok veya geçersiz bir ortam kaldırmak için doğrudan kayıt defterini değiştirmek için aşağıdaki adımları kullanın. Visual Studio otomatik olarak güncelleştirir **Python ortamları** kayıt defterinde değişiklik yaptığınız zaman penceresi.

1. Çalıştırma *regedit.exe*.
1. Gidin **HKEY_LOCAL_MACHINE\SOFTWARE\Python** 32-bit yorumlayıcılar için veya **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** 64-bit yorumlayıcılar için. IronPython için aranacak **IronPython** yerine.
1. Dağıtım yapınızla eşleşen düğümünü **PythonCore** CPython için veya **ContinuumAnalytics** Anaconda için. IronPython için sürüm numarası düğümünü genişletin.
1. Altındaki değerleri inceleyin **InstallPath** düğüm:

    ![Tipik bir CPython yüklemesi için kayıt defteri girişleri](media/environments-registry-entries.png)

    - Ortam bilgisayarınızda hala devam ediyorsa, değiştirin **ExecutablePath** doğru konuma. Ayrıca düzeltmek **(varsayılan)** ve **WindowedExecutablePath** değerleri gerektiği şekilde.
    - Ortam artık bilgisayarınızda varsa ve ondan kaldırmak istediğiniz **Python ortamları** penceresinin üst düğümü Sil **InstallPath**, gibi **3.6** Yukarıdaki görüntüde.

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için Requirements.txt dosyasını kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
