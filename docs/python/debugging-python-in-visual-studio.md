---
title: Python kodunda hata ayıklama
description: Visual Studio için Python kodu, kesme noktaları ayarlama, Adımlama, değerler geçirerek, özel durumlar arama ve etkileşimli pencerede hata ayıklama da dahil olmak üzere zengin hata ayıklama sağlar.
ms.date: 10/10/2018
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
ms.openlocfilehash: 0e4cc2ff43b59fff0aac70d9cc13a0a00662e209
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068441"
---
# <a name="debug-your-python-code"></a>Python kodunuzun hatalarını ayıklama

Visual Studio, Python, çalışan işlemlere, ekleme dahil olmak üzere, ifadeleri değerlendirme için kapsamlı bir hata ayıklama deneyimi sunar **Watch** ve **hemen** windows, yerel inceleniyor değişkenleri, kesme noktaları, / out/üzerinden deyimleri adım **sonraki deyimi Ayarla**ve daha fazlası.

Ayrıca aşağıdaki senaryoya özgü hata ayıklama makalelere bakın:

- [Linux uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- [Python/C++ karışık mod hata ayıklaması](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Microsoft Virtual Academy) videoyu](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) (3 m 32s) hata ayıklama Python tanıtımı için.|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio'da Python, bir proje hata ayıklamayı destekler. Tek başına Python dosyası ile açık Düzenleyicisi'nde sağ seçin **ile hata ayıklama Başlat**, ve Visual Studio genel varsayılan ortam komut dosyasını başlatır (bkz [Python ortamları](managing-python-environments-in-visual-studio.md)) ve bağımsız değişkenler. Ancak daha sonra tam hata ayıklama desteği gerekir.
>
> Ortamı ve bağımsız değişkenleri denetlemek için kolayca yapılır kod projesi oluşturma [mevcut Python'dan kod](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) proje şablonu.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Temel hata ayıklama

Temel hata ayıklama iş akışından kod içerisinde ilerlemeye değerlerini inceleme ve aşağıdaki bölümlerde açıklandığı gibi özel durumları işleme ayarlarını kesme noktaları içerir.

İle hata ayıklama oturumu başlatır **hata ayıklama** > **hata ayıklamayı Başlat** komutu **Başlat** araç çubuğundan veya **F5**anahtarı. Bu Eylemler, projenizin başlangıç dosyasını başlatın (gösterilen kalın **Çözüm Gezgini**) projenin etkin ortam ve komut satırı bağımsız değişkenleri veya içinde belirtilen arama yollarını **proje Özellikleri** (bkz [proje hata ayıklama seçenekleri](#project-debugging-options)). **Visual Studio 2017 sürüm 15.6** ve daha sonra ayarlanmış bir başlangıç dosyası yoksa, sizi uyarır; önceki sürümlerinde çalışan Python yorumlayıcısı ile bir çıktı penceresini açın veya çıkış penceresine kısaca görüntülenir ve kaldırılır. Herhangi bir durumda, uygun dosya sağ tıklayıp **başlangıç dosyası olarak ayarla**.

> [!Note]
> Hata ayıklayıcı her zaman etkin Python ortamı proje için başlar. Ortamı değiştirmek için farklı bir tane aktif üzerinde açıklandığı gibi olun [bir proje için bir Python ortamını seçin](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Kesme noktaları

Program durumunu inceleyebilirsiniz. Bu nedenle işaretli bir noktada kod yürütme kesme noktaları durdurun. Sol kenar boşluğunu Kod Düzenleyicisi'ni veya bir kod satırı sağ tıklatıp seçerek tıklayarak kesme noktası ayarlama **kesme noktası** > **kesme noktası Ekle**. Her satırda bir kesme noktası ile kırmızı bir nokta belirir.

![Visual Studio'da görünen kesme noktaları](media/debugging-breakpoints.png)

Kırmızı nokta veya kod satırına sağ tıklayıp seçerek **kesme noktası** > **Sil kesme noktası** kesme noktası kaldırır. Ayrıca bunu kullanarak kaldırmadan devre dışı **kesme noktası** > **devre dışı kesme noktası** komutu.

> [!Note]
> Bazı kesme noktaları python'da şaşırtıcı diğer programlama dilleriyle hakkında deneyimli olduğunuzu geliştiriciler için olabilir. Herhangi bir üst düzey bir sınıf veya işlev tanımları işlenecek yüklendiğinde Python dosyası çalıştığında, Python tüm yürütülebilir kod dosyasıdır. Bir kesme noktası ayarlarsanız, hata ayıklayıcı kesme bölümü-şekilde bir sınıf bildirimine bulabilirsiniz. Bazen şaşırtıcı olmasına rağmen bu davranışı doğrudur.

Koşullar altında bir kesme noktası, yalnızca bir değişken belirli bir değer veya değer aralığı için ayarlandığında bozucu gibi tetiklenir özelleştirebilirsiniz. Koşulları ayarlama, Kesme noktasının kırmızı nokta sağ tıklayın, seçin **koşul**, ardından ifadeleri Python kodu kullanarak oluşturun. Visual Studio'da bu özellik hakkında tam Ayrıntılar için bkz [kesme noktası durumlarını](../debugger/using-breakpoints.md#breakpoint-conditions).

Koşullar ayarlarken de ayarlayabilirsiniz **eylem** ve çıkış penceresi için yürütmeyi isteğe bağlı olarak otomatik olarak devam günlüğe kaydedilecek iletinin oluşturun. Bir iletiyi günlüğe kaydetmeyi oluşturur ne adlı bir *İzleme noktası* günlüğe kaydetme koduna doğrudan uygulamanıza ekleme olmadan:

![İzleme noktası ile bir kesme noktası oluşturma](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Kodunuz içinde adım adım

Bir kesme noktasında durduruldu sonra kodunuz içinde adım adım veya yeniden kesmeden önce kod bloklarını çalıştırmak için çeşitli yollar vardır. Bu komutlar yerler üst hata ayıklama araç çubuğu dahil olmak üzere, bir süre içinde kullanılabilir **hata ayıklama** menüsünde klavye kısayolları ve Kod Düzenleyicisi'nde sağ bağlam menüsünü (tüm komutları tüm konumları değildir):

| Özellik | Tuş vuruşu | Açıklama |
| --- | --- | --- |
| **Continue** | **F5** | Kod, sonraki kesme noktasına ulaşılıncaya kadar çalışır. |
| **Adımla** | **F11** | Sonraki deyimi çalıştırır ve durdurur. Sonraki ifade bir işlev çağrısı ise, hata ayıklayıcı çağrılan işlevin ilk satırına durdurur. |
| **Üzerinden adımla** | **F10** | (Çalışan tüm kodun) bir işlev çağrısını yapmadan dahil olmak üzere, sonraki deyimi çalıştırır ve herhangi bir dönüş değeri uygulanıyor. Üzerinden Adımlama kolayca hata ayıklama gerekmez işlevleri atlamanızı sağlar. |
| **Dışına adımla** | **Shift**+**F11** | Kod için çağırma deyimine adımları sonra geçerli işlevin sonuna kadar çalışır.  Bu komut, geçerli işlevin geri kalanında hata ayıklamak ihtiyacınız kalmadığında yararlıdır. |
| **İmlece kadar Çalıştır** | **CTRL**+**F10** | Kod Düzenleyicisi'nde şapka konumuna çalıştırır. Bu komut bir parçası olduğundan, hata ayıklamak için ihtiyacınız olmayan kod üzerinde kolayca atlamanızı sağlar. |
| **Sonraki deyimi belirle** | **CTRL**+**Shift**+**F10** | Giriş işareti konumuna kod noktası çalıştırma geçerli değiştirir. Bu komut, gibi bildiğiniz kodu bozuk veya istenmeyen bir yan etkisi üretir, çalıştırılan kodun bir parçasını atlamak sağlar. |
| **Sonraki bildirimi Göster** | **Alt**+**Num****&#42;**| Sonraki deyimi çalıştırmak için döndürür. Bu komut, kodunuzda arıyorsunuz geçici bir çözüm ve hata ayıklayıcı durduğu hatırlamıyorum yararlıdır. |

### <a name="inspect-and-modify-values"></a>Denetleme ve değerleri değiştirme

Hata ayıklayıcıda durdurulduklarında inceleyin ve değişkenlerin değerlerini değiştirin. Ayrıca **Watch** bağımsız değişkenleri yanı sıra özel ifadeleri İzleme penceresinde. (Bkz [değişkenleri denetleyin](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) genel ayrıntılar için.)

Kullanarak bir değeri görüntülemek için **DataTips**, fare düzenleyicisinde herhangi bir değişken yalnızca üzerine gelin. Değeri değiştirmek için tıklayabilirsiniz:

![Visual Studio hata ayıklayıcıda gösteren DataTips](media/debugging-quick-tips.png)

**Otolar** penceresi (**hata ayıklama** > **Windows** > **Otolar**) değişkenleri ve ifadeleri içeriyor, Geçerli deyimi yakın olan. Değer sütunu veya seçin ve ENTER tuşuna çift tıklayabilirsiniz **F2** değerini düzenlemek için:

![Visual Studio hata ayıklayıcısı otomatik değişkenler penceresi](media/debugging-autos-window.png)

**Yereller** penceresi (**hata ayıklama** > **Windows** > **Yereller**) bulunan tüm değişkenleri görüntüler Geçerli kapsam, yeniden düzenlenebilir:

![Visual Studio hata ayıklayıcısını Yereller penceresinde](media/debugging-locals-window.png)

Daha fazla üzerinde kullanma **Otolar** ve **Yereller**, bkz: [Otolar ve yerel öğeler pencerelerinde değişkenleri denetleyin](../debugger/autos-and-locals-windows.md).

**Watch** windows (**hata ayıklama** > **Windows** > **Watch**  >   **1-4 izleyin**) rastgele Python ifadelerini girin ve sonuçları görüntülemeniz olanak sağlar. İfadeler her adım için değerlendirilerek:

![Visual Studio hata ayıklayıcı penceresinde izleyin](media/debugging-watch-window.png)

Daha fazla üzerinde kullanma **izleme**, bkz: [izleme ve QuickWatch pencerelerini kullanarak değişkenler üzerinde bir izleme ayarlama](../debugger/watch-and-quickwatch-windows.md).

Bir dize değeri incelerken (`str`, `unicode`, `bytes`, ve `bytearray` tüm dizeleri bu amaca yönelik olarak kabul edilir), değeri sağ tarafında bir Büyüteç simgesi görünür. Simgeye tıklayarak uzun dizeler için yararlı olan tırnak işareti olmayan bir dize değeri sarmalama ve kaydırmayı, açılan iletişim kutusunda görüntüler. Ayrıca, açılan ok simgesini seçerek, düz metin seçmenizi sağlar HTML, XML ve JSON görselleştirmeler:

![Visual Studio hata ayıklayıcısı görselleştiriciler dize](media/debugging-string-visualizers.png)

HTML, XML ve JSON görselleştirmeler ayrı açılır pencereleri söz dizimi vurgulama ve ağaç görünümleri ile görünür.

### <a name="exceptions"></a>Özel Durumlar

Hata ayıklama sırasında programınızdaki bir hata meydana gelir, ancak bunun için bir özel durum işleyicisi yok, hata ayıklayıcı özel durum noktasında keser:

![Visual Studio hata ayıklayıcı özel durum açılan menüsü](media/debugging-exception-popup.png)

Bu noktada çağrı yığını da dahil olmak üzere program durumunu inceleyebilirsiniz. Ancak, kodunuz içinde adım adım denerseniz, özel durum ya da işlenir veya programınızın çıkar kadar oluşturulan devam eder.

**Hata ayıklama** > **Windows** > **özel durum ayarları** menü komutu genişletin bir penceresi getirir **Python Özel durumlar**:

![Visual Studio hata ayıklayıcısını özel durumlar penceresi](media/debugging-exception-settings.png)

Her özel durum denetimleri için onay kutusunu olmadığını hata ayıklayıcı *her zaman* keser olduğunda ortaya çıkar. Daha sık için belirli bir özel durumun kesmek istediğinizde bu kutuyu işaretleyin.

Kaynak kodunda özel durum işleyicisi bulunamadığında varsayılan olarak, çoğu özel durumların bölün. Bu davranışı değiştirmek için herhangi bir özel durum sağ tıklayın ve değiştirmek **devam yaparken işlenmemiş kullanıcı kodunda** seçeneği. Daha az sıklıkta için bir özel durum kesmek istediğinizde bu kutusunun işaretini kaldırın.

Bu listede görünmeyen bir özel durum yapılandırmak için tıklayın **Ekle** düğmesi ekleyin. Özel durumun tam adı eşleşmelidir.

## <a name="project-debugging-options"></a>Proje hata ayıklama seçenekleri

Varsayılan olarak, hata ayıklayıcı, programınızın standart Python başlatıcısı, hiçbir komut satırı bağımsız değişkenleri ve başka hiçbir özel yollar veya koşullar ile başlatır. Başlangıç seçenekleri, projenize sağ tıklayarak erişilen projenin hata ayıklama özellikleri aracılığıyla değiştirilirse **Çözüm Gezgini**u seçerek **özellikleri**, seçerek **hata ayıklama**  sekmesi.

![Visual Studio hata ayıklayıcısı proje hata ayıklama özellikleri](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Modu seçeneklerini başlatma

| Seçenek | Açıklama |
| --- | --- |
| **Standart Python Başlatıcısı** | CPython, IronPython ve Stackless Python gibi çeşitler uyumludur taşınabilir python'da yazılan kod hata ayıklamayı kullanır. Bu, saf Python kodunda hata ayıklama için en iyi deneyimi sağlar. Çalışan bir eklediğiniz zaman *python.exe* işlem, bu Başlatıcısı kullanılır. Bu Başlatıcı ayrıca sağlar [karışık mod hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) CPython için C/C++ kodu ve Python kodu arasında sorunsuz bir şekilde adım etmenize imkan sağlar. |
| **Web Başlatıcısı** | Varsayılan tarayıcınız başlatma sırasında başlatılır ve şablonları hata ayıklamasını etkinleştirir. Bkz: [Web şablonuna ilişkin hata ayıklama](python-web-application-project-templates.md#debugging) bölümünde daha fazla bilgi için. |
| **Django Web Başlatıcısı** | Aynı Web Başlatıcısı'nı ve yalnızca geriye dönük uyumluluk gösterilir. |
| **IronPython (.NET) Başlatıcısı** | .NET hata ayıklayıcı, IronPython yalnızca hangi çalışır kullanır ancak C# ve VB'nin dahil olmak üzere herhangi bir .NET dil projesine arasında atlamak için izin verir IronPython barındıran çalışan bir .NET işleme eklerseniz bu Başlatıcısı kullanılır. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Çalıştırma Seçenekleri (arama yolları, başlangıç bağımsız değişkenleri ve ortam değişkenlerini)

| Seçenek | Açıklama |
| --- | --- |
| **Arama yolları** | Projenin içinde gösterilen bu değerlerin eşleşmesi **arama yollarını** düğümünde **Çözüm Gezgini**. Burada bu değeri değiştirebilirsiniz, ancak bunu daha kolay olan kullanın **Çözüm Gezgini** klasörlere göz atmanıza olanak tanır ve yolları göreli forma otomatik olarak dönüştürür. |
| **Betik bağımsız değişkenleri** | Bu bağımsız değişkenler komut dosyanızın filename sonra görünen betiğinizi başlatmak için kullanılan komut eklenir. İlk öğe İşte betiğinizi kullanılabilir `sys.argv[1]`olarak ikinci `sys.argv[2]`ve benzeri. |
| **Yorumlayıcı bağımsız değişkenleri** | Bu bağımsız komut dosyanız adının önünde Başlatıcısı komut satırına eklenir. Genel bağımsız değişkenler burada `-W ...` denetimi uyarılar için `-O` biraz programınızı iyileştirmek için ve `-u` arabellekten çıkarılan g/ç kullanılacak. IronPython kullanıcıları geçirmek için bu alan kullanması muhtemel `-X` gibi seçenekleri `-X:Frames` veya `-X:MTA`. |
| **Cesta k İnterpretu** | Geçerli ortam ile ilişkili yolu geçersiz kılar. Değer bir standart yorumlayıcı komut dosyanızı başlatmak için yararlı olabilir. |
| **Ortam Değişkenleri** | Bu çok satırlı metin kutusuna form girişlerini ekleme \<adı > =\<değer >. Bu ayar son olarak, var olan tüm genel ortam değişkenlerini ve sonra üstte uygulandığından `PYTHONPATH` göre ayarlanır **arama yollarını** ayarı, bu el ile bu bulunanlardan herhangi biri diğer değişkenlerini geçersiz kılmak için kullanılabilir. |

## <a name="immediate-and-interactive-windows"></a>Hemen ve etkileşimli windows

Hata ayıklama oturumu sırasında kullanabileceğiniz iki etkileşimli pencere vardır: standart Visual Studio **hemen** penceresinde ve **Python etkileşimli hata ayıklama** penceresi.

**Hemen** penceresi (**hata ayıklama** > **Windows** > **hemen**) hızlı değerlendirmesi için kullanılır Python ifadeleri ve inceleme veya değişkenlerin çalışan bir program içerisinde atama. Bkz: Genel [komut penceresi](../ide/reference/immediate-window.md) makale Ayrıntılar için.

**Python etkileşimli hata ayıklama** penceresi (**hata ayıklama** > **Windows** > **Python etkileşimli hata ayıklama**) olan tam kolaylaştırır gibi daha zengin [etkileşimli REPL](python-interactive-repl-in-visual-studio.md) hata ayıklarken, yazma ve çalıştırma kod dahil olmak üzere kullanılabilir karşılaşırsınız. Standart Python Başlatıcısı'nı kullanarak hata ayıklayıcıda çalışmaya herhangi bir işlem otomatik olarak bağlanır (işlemler de dahil olmak üzere bağlı aracılığıyla **hata ayıklama** > **iliştirme**). Ancak, C/C++ karışık mod hata ayıklaması kullanırken kullanılabilir değilse.

![Python hata ayıklama etkileşimli penceresi](media/debugging-interactive.png)

**Hata ayıklama etkileşimli** penceresi destekleyen ek olarak, özel meta-komutları [standart REPL komutları](python-interactive-repl-in-visual-studio.md#meta-commands):

| Komut | Arguments | Açıklama |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Geçerli deyimden programı çalıştırmaya başlar. |
| `$down`, `$d` | Geçerli çerçeve bir düzey aşağıya yığın izlemesi taşıyın. |
| `$frame` | | Geçerli çerçeve kimliğini görüntüler.
| `$frame` | Çerçeve kimliği | Geçerli çerçevenin belirtilen çerçeve kimliğe geçer.
| `$load` | Komut dosyasını yükler ve tamamlanana kadar yürütür |
| `$proc` |  | Geçerli işlem kimliğini görüntüler. |
| `$proc` | işlem kimliği | Geçerli işlem için belirtilen işlem kimliği geçer. |
| `$procs` | | Şu anda hataları ayıklanan işlemlerin listeler. |
| `$stepin`, `$step`, `$s` | Sonraki işlev çağrısı, eğer mümkünse adımlamayla girin. |
| `$stepout`, `$return`, `$r` | Geçerli işlev dışında adımları. |
| `$stepover`, `$until`, `$unt` | Sonraki işlev deyime çağırın. |
| `$thread` | | Geçerli iş parçacığı kimliğini görüntüler. |
| `$thread` | iş parçacığı kimliği | Geçerli iş parçacığı için belirtilen iş parçacığı kimliği geçer. |
| `$threads` | | Şu anda hataları ayıklanmakta olan iş parçacıkları listeler. |
| `$up`, `$u` | | Yığın izlemeyle uygulamanızda geçerli çerçeve bir düzey yukarı. |
| `$where`, `$w`, `$bt` | Geçerli iş parçacığı çerçevelerini listeler. |

Standart windows gibi hata ayıklayıcı, Not **işlemleri**, **iş parçacıkları**, ve **çağrı yığını** ile eşitlenmemiş **etkileşimli hata ayıklama** penceresi. Etkin işlemi, iş parçacığı veya çerçevede değiştirme **hata ayıklama etkileşimli** penceresi bir hata ayıklayıcı pencereleri etkilemez. Benzer şekilde, etkin işlem, iş parçacığı veya bir hata ayıklayıcı pencerelerinde çerçeve değiştirme etkilemez **hata ayıklama etkileşimli** penceresi.

**Hata ayıklama etkileşimli** penceresine sahip kendi aracılığıyla erişebileceğiniz seçenekleri kümesi **Araçları** > **seçenekleri**  >   **Python Araçları** > **hata ayıklama, etkileşimli Pencere'ye**. Normal aksine **Python etkileşimli** yalnızca biri, her bir Python ortam için ayrı bir örneği var olan bir pencere **hata ayıklama etkileşimli** penceresi ve her zaman için Python yorumlayıcısı kullanır hataları ayıklanan işlem. Bkz: [seçenekleri - hata ayıklama seçenekleri](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Hata ayıklama etkileşimli penceresi seçenekleri](media/debugging-interactive-options.png)

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Eski hata ayıklayıcıyı kullanın

Visual Studio 2017 sürüm 15,8 ve daha sonra bir hata ayıklayıcısı ptvsd sürümüne 4.1 + dayanan kullanın. Ptvsd bu sürümü, Python 2.7 ve Python 3.5 + ile uyumludur. Python 2.6 3.1 için 3.4 kullanıyorsanız veya IronPython, Visual Studio hatayı gösterir **hata ayıklayıcı bu Python ortamı desteklemiyor**:

![Hata ayıklayıcı hata ayıklayıcı kullanırken bu Python ortamı hatası desteklemiyor](media/debugging-experimental-incompatible-error.png)

Bu gibi durumlarda, daha eski hata ayıklayıcı (Visual Studio 2017 sürüm 15.7 ve önceki varsayılan olan) kullanmanız gerekir. Seçin **Araçları** > **seçenekleri** menü komutu, gitmek **Python** > **hata ayıklama**ve seçin **eski hata ayıklayıcısını** seçeneği.

Geçerli ortama (örneğin, önceki 4.0.x sürümü veya uzaktan hata ayıklama için gereken bir 3.x sürümü) ptvsd daha eski bir sürümünü yüklediyseniz Visual Studio bir hata veya uyarı gösterebilir.

Hata **hata ayıklayıcısı paket yüklenemedi**, ptvsd yüklediğiniz görüntülendiğinde 3.x:

![Hata ayıklayıcısı paket hata ayıklayıcı kullanırken yüklenen hata bulunamadı](media/debugging-experimental-version-error.png)

Bu örnekte **eski hata ayıklayıcısını** ayarlamak için **eski hata ayıklayıcısını** seçenek ve hata ayıklayıcıyı yeniden başlatın.

Uyarı **hata ayıklayıcı paketi güncel değil**, önceki bir 4.x sürümünde ptvsd yüklediğiniz görünür:

![Hata ayıklayıcısı paket hata ayıklayıcı kullanırken uyarı güncel değil](media/debugging-experimental-version-warning.png)

> [!Important]
> Ptvsd'ün bazı sürümleri için bir uyarıyı yoksaymak seçebilirsiniz ancak Visual Studio doğru şekilde çalışmayabilir.

Ptvsd yüklemenizi yönetmek için:

1. Gidin **paketleri** sekmesinde **Python ortamları** penceresi.

1. Arama kutusuna "ptvsd" ve ptvsd'ın yüklü sürümü inceleyin:

    ![Python ortamları penceresinde ptvsd sürüm denetimi](media/debugging-experimental-check-ptvsd.png)

1. Sürüm (sürüm, Visual Studio ile birlikte) 4.1.1a9 düşüktür, seçin **X** sağındaki paketin eski sürümü kaldırın. Visual Studio, ardından ile birlikte gelen sürümünü kullanır. (PowerShell kullanarak da kaldırabilirsiniz `pip uninstall ptvsd`.)

1. En yeni sürümü için'ndaki yönergeleri takip ederek ptvsd paket alternatif olarak, güncelleştirebilirsiniz [sorun giderme](#troubleshooting) bölümü.

## <a name="troubleshooting"></a>Sorun giderme

Hata ayıklayıcısı ile sorun yaşarsanız, ilk gibi ptvsd sürümünüzü yükseltin:

1. Gidin **paketleri** sekmesinde **Python ortamları** penceresi.

1. Girin `ptvsd --upgrade` seçip arama kutusuna **komutu çalıştırın: pip install komutunu ptvsd--yükseltme**. (Ayrıca aynı PowerShell komutu kullanabilirsiniz.)

    ![Python ortamları penceresinde ptvsd yükseltme komut vererek](media/debugging-experimental-upgrade-ptvsd.png)

Sorunlar devam ederse lütfen sorunu üzerinde dosya [PTVS GitHub deposu](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Hata ayıklayıcı günlüğü etkinleştir

Bir hata ayıklayıcı sorunu araştırmaya sırasında Microsoft, etkinleştirmek ve tanılama aşamasında yardımcı hata ayıklayıcı günlükleri toplamak için isteyebilir.

Aşağıdaki adımlar, geçerli Visual Studio oturumunda hata ayıklamayı etkinleştir:

1. Visual Studio kullanarak bir komut penceresi açın **görünümü** > **diğer Windows** > **komut penceresi** menü komutu.

1. Aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Hata ayıklamayı başlatmak ve tüm adımları sorununuzu yeniden oluşturmak için gerekli olan aracılığıyla gidin. Bu süre boyunca, hata ayıklama günlükleri görünür **çıkış** penceresinin altında **hata ayıklama bağdaştırıcısı konağı günlüğü**. Ardından, günlükleri pencereden kopyalayın ve bir GitHub sorunu, e-posta, vb. yapıştırın.

    ![Hata ayıklayıcı çıkış penceresinde günlük çıktısı](media/debugger-logging-output.png)

1. Visual Studio kilitleniyor veya aksi halde erişmeye değilsiniz **çıkış** penceresinde, Visual Studio'yu yeniden başlatın, bir komut penceresi açın ve aşağıdaki komutu girin:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Hata ayıklamayı başlatmak ve sorunu yeniden oluşturun. Hata ayıklayıcı günlükleri ardından bulunabilir `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Ayrıca bkz.

Visual Studio hata ayıklayıcı tüm ayrıntılar için bkz. [Visual Studio'da hata ayıklama](../debugger/debugger-feature-tour.md).
