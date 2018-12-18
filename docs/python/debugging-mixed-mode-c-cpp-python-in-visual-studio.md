---
title: Karışık mod hata ayıklaması için Python
description: Eşzamanlı C++ ve ortamlar arasında adımlama, görüntüleme değerleri ve ifadeleri değerlendirme de dahil olmak üzere Visual Studio'da Python hata ayıklayın.
ms.date: 11/12/2018
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
ms.openlocfilehash: 42d413ab8d96ccd5533afe99cffb2c05c8ac7d6f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052241"
---
# <a name="debug-python-and-c-together"></a>Python ve C++ birlikte hata ayıklama

Çoğu normal Python hata ayıklayıcılar, yalnızca Python koduna yönelik hata ayıklamayı destekler. Ancak, uygulamada, platform API'lerini doğrudan çağırmak için yüksek performans veya yeteneği gerektiren senaryolar C veya C++ ile birlikte Python kullanılır. (Bkz [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md) kılavuz.)

Visual Studio sağlayan tümleşik, eşzamanlı karma mod Python ve yerel C/C++ için hata ayıklama seçeneğini koşuluyla **Python yerel geliştirme araçları** seçeneğini **Python geliştirme** Visual Studio Yükleyicisi'nde iş yükü.

> [!Note]
> Karışık mod hata ayıklama kullanılamıyor Visual Studio için Python araçları ile Visual Studio 2015'te ve daha önce 1.x.

Bu makalede açıklandığı gibi karışık mod hata ayıklama özellikleri aşağıdakileri içerir:

- Birleştirilmiş çağrı yığınları
- Python ve yerel kod arasında adımla
- Her iki tür kod içinde kesme noktaları
- Python yerel çerçeveler ve bunun tersi de nesneleri temsillerini bakın
- Python veya C++ projesi bağlamında hata ayıklama

![Visual Studio'da Python için karışık mod hata ayıklama](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | Test ve yerel C modülleri Visual Studio ile hata ayıklama oluşturmaya giriş için bkz. [yakından bakış: yerel modülleri oluşturma](https://youtu.be/D9RlT06a1EI) (youtube.com 9 dk 09s). Video, Visual Studio 2015 ve 2017 için geçerlidir. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Karma mod bir Python projesinde hata ayıklamayı etkinleştir

1. Python projeye sağ **Çözüm Gezgini**seçin **özellikleri**seçin **hata ayıklama** sekmesine tıklayın ve ardından **yerel kod hata ayıklamayı etkinleştir** . Bu seçenek, tüm hata ayıklama oturumları için karma mod sağlar.

    ![Yerel kod hata ayıklamayı etkinleştirme](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Yerel kodda hata ayıklama etkinleştirdiğinizde program, normal vermeden tamamlandığında hemen Python çıkış penceresine kaybolabilir **devam etmek için herhangi bir tuşa basın** duraklatın. Bir duraklatma zorlamak için ekleme `-i` seçeneğini **çalıştırın** > **yorumlayıcı bağımsız değişkenleri** alanını **hata ayıklama** sekmesinde yerel kodda hata ayıklama etkinleştirdiğinizde . Bu noktada bekler basın için kod bittikten sonra bu bağımsız değişken Python yorumlayıcısı etkileşimli moduna sokar **Ctrl**+**Z** > **girin**  çıkmak için.

1. Karışık mod hata ayıklayıcının varolan bir sürece eklerken (**hata ayıklama** > **iliştirme**), kullanın **seçin** açmak için düğmeyi  **Kod türünü seç** iletişim. Ardından **bu tür kodlarda hata ayıklama** seçeneğini ve her ikisi de **yerel** ve **Python** listesinde:

    ![Yerel ve Python kodu türü seçme](media/mixed-mode-debugging-code-type.png)

    Kod türü ayarlarını kalıcı, bunu başka bir işlem için daha sonra NET eklerken karışık mod hata ayıklaması devre dışı bırakmak isterseniz **Python** kod türü.

    Ek olarak ya da onun yerine diğer kod türleri seçmek mümkündür **yerel**. Örneğin, yönetilen uygulamayı CPython barındırıyorsa, hangi içinde Aç yerel uzantı modüllerini kullanır ve kontrol edebilirsiniz, tüm üç hata ayıklamak istediğiniz **Python**, **yerel**, ve **yönetilen**birlikte için birleştirilmiş bir hata ayıklama deneyimini de dahil olmak üzere birleştirilmiş çağrı yığınları ve üç tüm çalışma zamanları arasında adımlama.

1. Karışık modda hata ayıklama için ilk kez başlattığınızda, görebileceğiniz bir **Python sembolleri gerekli** iletişim (bkz [karışık mod hata ayıklaması için semboller](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Verilen herhangi bir Python ortamı için yalnızca bir kez sembolleri yüklemeniz gerekir. Visual Studio 2017 yükleyicisi aracılığıyla Python desteği yüklerseniz, semboller otomatik olarak eklenir.

1. Kaynak kodu standart Python için kendisini hata ayıklama sırasında kullandırmak için şurayı ziyaret edin [ https://www.python.org/downloads/source/ ](https://www.python.org/downloads/source/), sürümünüz için uygun arşiv indirmek ve bir klasöre ayıklayın. Ardından Visual Studio'da bu klasöre işaret ne olursa olsun, belirli dosyaları ister noktası.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Karma mod bir C/C++ projesinde hata ayıklamayı etkinleştir

Visual Studio 2017 (sürüm 15.5 ve üstü) destekleyen bir C/C++ projesi karışık mod hata ayıklama (örneğin, [Python python.org üzerinde açıklandığı gibi başka bir uygulamaya ekleme](https://docs.python.org/3/extending/embedding.html)). C/C++ projesi başlatmak için karışık mod hata ayıklamayı etkinleştirmek için yapılandırma **Python/yerel hata ayıklama**:

1. C/C++ projeye sağ **Çözüm Gezgini** seçip **özellikleri**.
1. Seçin **hata ayıklama** sekmesinde **Python/yerel hata ayıklama** gelen **başlatmak için hata ayıklayıcı**seçip **Tamam**.

    ![Python/yerel hata ayıklayıcı bir C/C++ projesinde seçme](media/mixed-mode-debugging-select-cpp-debugger.png)

Bu yöntemi kullanarak, ayıklanamıyor kullanan *py.exe* Başlatıcısı kendisi, çünkü bu bir alt öğesi olarak çoğaltılır *python.exe* hata ayıklayıcı iliştirilmiş olmaz işlem. Başlatmak istiyorsanız *python.exe* doğrudan bağımsız değişkenlerle değiştirmek **komut** seçeneğini **Python/yerel hata ayıklama** özelliklerine (önceki görüntüde gösterilmiştir) tam yolunu belirtin *python.exe*, ardından bağımsız değişkenleri belirtin **komut satırı bağımsız değişkenlerini**.

### <a name="attaching-the-mixed-mode-debugger"></a>Karışık mod hata ayıklayıcısı ekleniyor

İçin tüm önceki sürümleri, Visual Studio'nun C/C++ projeleri yalnızca yerel hata ayıklayıcı kullandığından, yalnızca Visual Studio'da Python projesi başlatma sırasında doğrudan karışık mod hata ayıklama etkinleştirilir. Ancak, hata ayıklayıcı ayrı olarak eklediğiniz olabilir:

1. C++ proje hata ayıklama olmadan Başlat (**hata ayıklama** > **hata ayıklama olmadan Başlat** veya **Ctrl**+**F5**) .
1. Seçin **hata ayıklama** > **işleme**. Görüntülenen iletişim kutusunda, uygun işlemi seçin ve ardından kullanın **seçin** açmak için düğmeyi **kod türünü seç** seçin iletişim **Python**:

    ![Python hata ayıklayıcısı eklenirken hata ayıklama türü olarak seçme](media/mixed-mode-debugging-attach-type.png)

1. Seçin **Tamam** sonra bu iletişim kutusunu kapatmak için **iliştirme** hata ayıklayıcıyı başlatmak için.
1. Uygun duraklama veya gecikme, hata ayıklayıcının şansı bulamadan hata ayıklamak istediğiniz Python kodu çağıracak değil emin olmak için C++ uygulamasında tanıtmak gerekebilir.

## <a name="mixed-mode-specific-features"></a>Karma mod belirli özellikler

- [Birleştirilmiş çağrı yığını](#combined-call-stack)
- [Python ve yerel kod arasında adımla](#step-between-python-and-native-code)
- [Yerel kodda PyObject değerlerini görüntüleme](#pyobject-values-view-in-native-code)
- [Python kodu yerel değerleri görünümü](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Birleştirilmiş çağrı yığını

**Çağrı yığını** penceresi, hem yerel hem de Python yığın çerçevelerini ikisi arasındaki işaretli geçişleri aralıklı gösterir:

![Karışık mod hata ayıklaması ile birleştirilmiş çağrı yığını](media/mixed-mode-debugging-call-stack.png)

Geçişleri görünür olarak **[harici kod]**, varsa, geçiş yönü belirtmeden **Araçları** > **seçenekleri**  >  **Hata ayıklama** > **genel** > **yalnızca benim kodumu etkinleştir** seçeneği ayarlanır.

Herhangi bir çağrı çerçevesi çift etkin hale getirir ve uygun kaynak kodu, mümkünse açılır. Kaynak kodu kullanılabilir durumda değilse, çerçeve hala etkin hale ve yerel değişkenler inceledi.

### <a name="step-between-python-and-native-code"></a>Python ve yerel kod arasında adımla

Kullanırken **içine adımla** (**F11**) veya **Step Out** (**Shift**+**F11**) komutları karışık mod hata ayıklayıcı kod türü arasındaki değişiklikleri doğru olarak işler. Python C'de uygulandığı bir türün bir yöntemi çağırdığında, örneğin, bir çağrıda yöntemi yerel işlev yöntemi uygulama başlangıcında durdurur Adımlama. Benzer şekilde, ne zaman yerel kod çağrılmakta olan Python kodunda sonuçlanan bazı Python API işlevi çağırır. Örneğin, içine Adımlama bir `PyObject_CallObject` Python'da tanımlanmış bir işlevi değer Python işlevin başında durur. Python'dan yerel Adımlama de desteklenir python'dan çağrılan yerel işlevler için [ctypes](https://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Yerel kodda PyObject değerlerini görüntüleme

Yerel (C veya C++) çerçeve etkin olduğunda, hata ayıklayıcıda yerel değişkenlerini görünmesini **Yereller** penceresi. Yerel Python uzantısı modüller, çoğu bu değişkenlerin türü olan `PyObject` (Bu değer için bir typedef `_object`), ya da (aşağıdaki listeye bakın) diğer birkaç temel Python türler. Karışık mod hata ayıklamada etiketli bir ek alt düğümü bu değerleri sunmak **[Python Görünüm]**. Genişletildiğinde, bu düğüm değişkenin Python gösterimi gösterir, ne bir yerel değişken ederseniz görürsünüz aynı aynı nesneye başvuran bir Python çerçevesinde yoktu. Bu düğümün alt öğeleri düzenlenebilir.

![Yerel öğeler penceresinde Python görüntüle](media/mixed-mode-debugging-python-view.png)

Bu özellik devre dışı bırakmak için herhangi bir yeri sağ **Yereller** penceresi ve iki durumlu **Python** > **Python görünüm düğümlerini Göster** menü seçeneği:

![Yerel öğeler penceresinde Python görünümü etkinleştirme](media/mixed-mode-debugging-enable-python-view.png)

C türleri gösteren **[Python Görünüm]** (etkinse) düğümleri:

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Python Görünüm]**  otomatik olarak kendiniz yazmak türleri için görüntülenmez. Uzantılar için Python yazarken 3.x, bu olmaması genellikle bir sorun değildir herhangi bir nesne sonuçta olduğundan bir `ob_base` türlerinden yukarıda, hangi neden alanını **[Python Görünüm]** görüntülenecek.

Python 2.x, ancak her nesne türü, genellikle üstbilgisi satır içi alanlar koleksiyonu olarak bildirir ve özel yazılan türler arasında ilişkilendirme yok ve `PyObject` tür sistem düzeyinde C/C++ kod. Etkinleştirmek için **[Python Görünüm]** upravit uzly gibi özel türler için *PythonDkm.natvis* dosyası [Python araçları yükleme dizininin](installing-python-support-in-visual-studio.md#install-locations)ve XML için başka bir öğe ekleyin struct C veya C++ sınıfı.

Bir alternatif (ve daha iyi) seçeneği izlemektir [CESARETLENDİRİCİ 3123](https://www.python.org/dev/peps/pep-3123/) ve açık bir `PyObject ob_base;` alan yerine `PyObject_HEAD`, ancak bu her zaman geriye dönük uyumluluk açısından mümkün olmayabilir.

### <a name="native-values-view-in-python-code"></a>Python kodu yerel değerleri görünümü

Benzer şekilde, önceki bölümde, etkinleştirebilirsiniz bir **[C++ Görünüm]** yerel değerlerinin **Yereller** Python çerçeve etkin olduğunda penceresi. Sağ tıklatarak açabilirsiniz, böylece bu özellik varsayılan olarak etkin değildir **Yereller** penceresi ve geçiş **Python** > **C++ görünüm düğümlerini Göster** menüsü seçeneği.

![C++ görünümü Yereller penceresinde etkinleştirme](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ Görünüm]** düğüm C/C++ temelindeki aynı bir yerel çerçeve içinde neleri görür için bir değer için bir gösterimini sağlar. Örneğin, bu örneği gösterir `_longobject` (hangi `PyLongObject` bir TypeDef) bir Python uzun tamsayı ve bunun için yerel sınıflar için türlerini çıkarması çalıştığında kendiniz oluşturdunuz. Bu düğümün alt öğeleri düzenlenebilir.

![Yerel öğeler penceresinde C++ görüntüle](media/mixed-mode-debugging-cpp-view.png)

Bir nesnenin bir alt alan türde ise `PyObject`, veya başka birini desteklenen türleri, bunun ardından bir **[Python Görünüm]** nesne gitmek mümkün hale getirme (Bu gösterimler etkinleştirildiyse) gösterimi düğüm nerede grafikler doğrudan bağlantılar için Python sunulmaz.

Farklı **[Python Görünüm]** nesne türünü belirlemek için Python nesne meta verilerini kullanın, düğümler için benzer şekilde güvenilir bir mekanizma bulunmamaktadır **[C++ Görünüm]**. Genel olarak bakıldığında, verilen bir Python değer (diğer bir deyişle, bir `PyObject` başvuru) hangi C/C++ yapı yedekleme güvenilir bir şekilde belirlemek mümkün değildir. Karışık mod hata ayıklayıcı türü nesnenin türü çeşitli alanlarda bakılarak tahmin etmeye çalışır (gibi `PyTypeObject` tarafından başvurulan alt `ob_type` alan) işlev işaretçi türleri vardır. Bu işlev işaretçileri birini çözümlenebilir bir işlev başvuruyor ve bu işlev varsa bir `self` daha belirli bir tür parametresiyle `PyObject*`, bu tür yedekleme türü olarak kabul edilir. Örneğin, varsa `ob_type->tp_init` aşağıdaki işlevi verilen nesne noktalarda biri:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

hata ayıklayıcı, doğru nesne C türü olduğunu çıkarabilir sonra `FobObject`. Daha kesin bir türden belirlenemiyor ise `tp_init`, bunu diğer alanlara taşır. Bu alanlar türünden türetme kaydedemediği **[C++ Görünüm]** düğüm nesnesi olarak sunan bir `PyObject` örneği.

Her zaman özel yazılan türler için kullanışlı bir gösterimi almak için en az bir özel işlev türü kaydederken kaydedin ve türü kesin belirlenmiş bir kullanmak en iyisidir `self` parametresi. Türlerdir doğal olarak bu gereksinimi karşılayan; Bu durumda, ardından değilse `tp_init` genellikle bu amaçla kullanabileceğiniz en kullanışlı bir giriştir. İşlevsiz bir uygulaması `tp_init` yalnızca var olan bir türü için hata ayıklayıcı türü çıkarımı yalnızca sıfır hemen, yukarıdaki kod örneğinde olduğu gibi geri dönüp etkinleştirebilirsiniz.

## <a name="differences-from-standard-python-debugging"></a>Standart Python hata ayıklama gelen farklar

Karışık mod hata ayıklayıcı kodundan [standart bir Python hata ayıklayıcısının](debugging-python-in-visual-studio.md) bazı ek özellikler sunar ancak Python ile ilgili bazı özellikler eksiktir:

- Desteklenmeyen özellikler: koşullu kesme noktaları **hata ayıklama etkileşimli** penceresi ve platformlar arası uzaktan hata ayıklama.
- **Hemen** penceresi: işlevlerini ve sınırlamalar dahil olmak üzere, sınırlı bir alt kümesi ile kullanılabilir ancak burada listelenir.
- Python sürümleri desteklenir: CPython 2.7 ve 3.3 + yalnızca.
- Visual Studio Shell: Python ile Visual Studio Shell kullanırken (örneğin, tümleşik Yükleyicisi'ni kullanarak yüklediyseniz), Visual Studio C++ projeleri açamıyor ve yalnızca bir temel metin düzenleyici, C++ dosyaları için düzenleme deneyimi olan. Ancak, C/C++ hata ayıklama ve karma mod hata ayıklama tamamen Kabuğu'nda C++ ifade değerlendirmesi hata ayıklayıcı pencerelerinde ve yerel kod içine Adımlama, kaynak kodu ile desteklenir.
- Görüntüleme ve genişletme nesneleri: Python nesneleri görüntülerken **Yereller** ve **Watch** hata ayıklayıcı, araç pencerelerini, karma mod hata ayıklayıcı yalnızca nesnelerin yapısı gösterilmektedir. Otomatik olarak özellikleri değerlendirmek veya hesaplanan öznitelikleri gösterir. İsteğe bağlı olarak koleksiyonları için yalnızca yerleşik koleksiyon türleri için öğeleri gösterir (`tuple`, `list`, `dict`, `set`). Bazı yerleşik koleksiyon türden devralınan sürece özel koleksiyon türlerini koleksiyon olarak görselleştirilmiştir değil.
- İfade değerlendirme: aşağıya bakın.

### <a name="expression-evaluation"></a>İfade değerlendirme

Standart bir Python hata ayıklayıcısının rastgele Python ifadelerinde değerlendirilmesini sağlar **izleme** ve **hemen** pencerelerinin, engellenmediğinde olduğu sürece, hataları ayıklanan işlem kodda, herhangi bir noktada duraklatıldı bir g/ç işlemi veya diğer benzer sistem çağrısı. Karışık mod hata ayıklamada rastgele deyimler yalnızca bir kesme noktası sonra Python kodunda durdurulduğunda veya kodun içine Adımlama değerlendirilebilir. İfadeler, kesme noktasına veya atlama işlemi gerçekleştiği parçacığında değerlendirilebilir.

İfade değerlendirme, yerel kod veya Python kodu nerede Yukarıdaki koşullar (örneğin, bir adım genişletme işleminden sonra veya farklı bir iş parçacığında) uygulanmaz durduğunda, yerel ve genel değişkenler şu anda seçili kapsamdaki erişimle sınırlı Çerçeve, onların alanları erişme ve yerleşik koleksiyon türleri değişmez değerleri ile dizin oluşturma. Örneğin, aşağıdaki ifade (tüm tanımlayıcılar mevcut değişkenler ve uygun tür alanları bakın şartıyla) herhangi bir bağlamda değerlendirilebilir:

```python
foo.bar[0].baz['key']
```

Karışık mod hata ayıklayıcı ayrıca gibi ifadeler farklı çözümleniyor. Tüm üye erişim işlemleri yalnızca doğrudan nesnesinin bir parçası olan alanları bakın (bir girişi gibi kendi `__dict__` veya `__slots__`, veya Python kullanıma sunulan yerel bir yapının bir alan `tp_members`) ve tüm Yoksay `__getattr__`, `__getattribute__`ya da tanımlayıcı mantığı. Benzer şekilde, tüm dizin oluşturma işlemleri Yoksay `__getitem__`ve koleksiyonları iç veri yapılarını doğrudan erişebilirsiniz.

Tutarlılık sağlamak, bu ad çözümleme düzeni, sınırlı bir ifade değerlendirme rastgele ifadeleri geçerli Durma noktasına izin verilip verilmediğini kısıtlamalarıyla eşleşen tüm ifadeler için kullanılır. Tam özellikli bir değerlendirici, doğru Python semantiği zorlamak için kullanılabilir, ifadeyi ayraç içine alın:

```python
(foo.bar[0].baz['key'])
```
