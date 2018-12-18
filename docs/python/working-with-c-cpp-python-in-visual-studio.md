---
title: Python için C++ uzantıları yazma
description: Visual Studio, CPython ve PyBind11 karışık mod hata ayıklama da dahil olmak üzere, kullanarak Python için C++ uzantısı oluşturma için kullanılan bir kılavuz.
ms.date: 11/19/2018
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
ms.openlocfilehash: 437cd7f926465b4a9c4986f0eeb4b30e53936895
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053483"
---
# <a name="create-a-c-extension-for-python"></a>Python için C++ uzantısı oluşturma

C++ (veya C) yazılmış modüller, alt düzey işletim sistemi özelliklerine erişimi etkinleştirmek için de bir Python yorumlayıcısı yeteneklerini genişletmek için yaygın olarak kullanılır. Üç birincil modül türü vardır:

- Hızlandırıcı modülleri: Python yorumlanan bir dil olduğundan, belirli kod parçaları c++'ta daha yüksek performans için yazılabilir.
- Sarmalayıcı modülleri: Python'dan kullanımı kolay olan daha fazla bir "Pythonic" API'yi kullanıma sunmak veya Python kodu için var olan C/C++ arabirimleri kullanıma sunar.
- Alt düzey sistem erişim modülleri: CPython çalışma zamanı, işletim sistemi ya da temel alınan donanım düşük düzeyli özelliklerine erişmek için oluşturuldu.

Bu makalede, hiperbolik tanjantı hesaplar ve Python kodu çağıran CPython için C++ uzantısı modülü oluşturma sürecinde size yol gösterir. İlk yordam aynı yordamı C++'da uygulama göreli performans kazancı göstermek için Python uygulanır.

Bu makalede, Python için C++ kullanılabilir hale getirmek için iki yol da gösterilmektedir:

- Standart CPython uzantıları açıklandığı gibi [Python belgeleri](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), C++ 11, kolaylık sağlaması nedeniyle önerilir.

Bunlar ve diğer yolları arasında bir karşılaştırma altında bulunan [alternatif yaklaşımlar](#alternative-approaches) bu makalenin sonunda.

Bu izlenecek yolda tamamlanmış örnekten bulunabilir [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 ile her ikisini de **C++ ile masaüstü geliştirme** ve **Python geliştirme** varsayılan seçeneklerle yüklü iş yükleri.
- İçinde **Python geliştirme** iş yükü, aynı zamanda için sağdaki kutusunu işaretlemeniz **Python yerel geliştirme araçları**. Bu makalede açıklanan yapılandırmaların çoğu için bu seçeneği ayarlar. (Bu seçenek ayrıca C++ iş yükünü otomatik olarak içerir.)

    ![Python yerel geliştirme araçları seçeneği](media/cpp-install-native.png)

    > [!Tip]
    > Yükleme **veri bilimi ve analitik uygulamalar** iş yükü, Python de içerir ve **Python yerel geliştirme araçları** varsayılan seçeneği.

Daha fazla bilgi için [destekleyen Visual Studio için Python yükleme](installing-python-support-in-visual-studio.md), Visual Studio'nun diğer sürümlerinde kullanma dahil olmak üzere. Python ayrı olarak yüklerseniz, seçtiğinizden emin olun **hata ayıklama sembolleri Yükle** ve **indirme hata ayıklama ikililerini** altında **Gelişmiş Seçenekler** yükleyicisi. Bu seçenek, hata ayıklama derlemesi yapmayı tercih ederseniz gerekli hata ayıklama kitaplıklarını kullanılabilir olmasını sağlar.

## <a name="create-the-python-application"></a>Python uygulaması oluşturma

1. Seçerek Visual Studio'da yeni Python projesi oluşturma **dosya** > **yeni** > **proje**. Seç "Python" için arama **Python uygulaması** şablonu, uygun bir ad ve konum verin ve seçin **Tamam**.

1. C++ ile çalışma gerektiren bir 32 bit Python yorumlayıcısı kullanın (Python 3.6 veya üzeri önerilir). İçinde **Çözüm Gezgini** penceresi Visual Studio'nun proje düğümünü genişletin ve ardından genişletin **Python ortamları** düğümü. Varsayılan olarak 32-bit ortamından görmezseniz (kalın veya ile etiketlenmiş **genel varsayılan**), ardından yönergeleri izleyin [bir proje için bir Python ortamını seçin](selecting-a-python-environment-for-a-project.md). Yüklü bir 32-bit yorumlayıcı yoksa bkz [yüklemeniz Python yorumlayıcılarını](installing-python-interpreters.md).

1. Projenin *.py* dosya, hesaplama (matematik kitaplığı için daha kolay karşılaştırma kullanmadan uygulanan) bir hiperbolik tanjant benchmarks aşağıdaki kodu yapıştırın. El ile bazı deneyimi için kodu girin çekinmeyin [düzenleme özellikleri Python](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Programını kullanarak çalıştırın **hata ayıklama** > **hata ayıklama olmadan Başlat** (**Ctrl**+**F5**) sonuçları görmek için. Ayarlayabileceğiniz `COUNT` çalıştırılması için ne kadar Kıyaslama geçen değiştirmek için değişken. Kıyaslama ele olacak şekilde yaklaşık iki saniye bu kılavuzun amacıyla sayısı ayarlayın.

> [!TIP]
> Kıyaslama çalışırken, her zaman kullanması **hata ayıklama** > **hata ayıklama olmadan Başlat** kodu Visual Studio hata ayıklayıcısı içinde çalışırken sonucunda ek yükten kaçınmak için.

## <a name="create-the-core-c-projects"></a>Çekirdek C++ projeleri oluşturma

"Superfastcode" ve "superfastcode2" adlı iki özdeş C++ projeleri oluşturmak için bu bölümdeki yönergeleri izleyin. Daha sonra Python için C++ kodu kullanıma sunmak için her bir projede farklı yollardan kullanacaksınız.

1. Emin `PYTHONHOME` ortam değişkeninin ayarlı Python yorumlayıcınıza kullanmak istiyorsunuz. Visual Studio'da C++ projeleri gibi dosyalarını bulmak için bu değişkeni güvenin *python.h*, bir Python uzantısı oluşturulurken kullanılır.

1. Çözüme sağ **Çözüm Gezgini** seçip **Ekle** > **yeni proje**. Visual Studio çözümü (Visual Studio için Python kullanmanın avantajlarını biridir) hem Python hem de C++ projeleri birlikte içerebilir.

1. Arama seçin "C++" **boş proje**, "superfastcode" adı belirtin ("superfastcode2" ikinci projesi için) seçip **Tamam**.

    > [!Tip]
    > İle **Python yerel geliştirme araçları** Visual Studio 2017'de yüklü ile başlayabilirsiniz **Python uzantı Modülü** şablon bunun yerine, sahip olduğu zaten yerinde açıklanana çoğunu. Bu kılavuz için boş bir proje ile başlayarak adım adım uzantı modülü oluşturma gösterir. İşlem anladığınızda, zaman zaman şablon kaydeder kendi uzantılarınızı yazma.

1. Sağ tıklayarak bir C++ dosyası içinde yeni proje oluşturma **kaynak dosyaları** düğümünü seçip **Ekle** > **yeni öğe**seçin **C++dosyası**, adlandırın `module.cpp`seçip **Tamam**.

    > [!Important]
    > Bir dosyayla *.cpp* C++ özellik sayfaları'nda aşağıdaki adımları açmak uzantısı gereklidir.

1. C++ projeye sağ **Çözüm Gezgini**seçin **özellikleri**.

1. Üst kısmındaki **özellik sayfaları** görüntülenen iletişim **yapılandırma** için **yapılandırmalarında** ve **Platform** için**Win32**.

1. Aşağıdaki tabloda açıklandığı gibi belirli özellikleri ayarlayın ve ardından **Tamam**.

    | Tab | Özellik | Değer |
    | --- | --- | --- |
    | **Genel** | **Genel** > **hedef adı** | Python'da bir başvurduğu istediğiniz modül adını `from...import` deyimleri. Bu aynı adı için Python modülü tanımlarken, C++'ta kullanın. Modül adı projenin adı kullanmak istiyorsanız, varsayılan değerini bırakın **$(ProjectName)**. |
    | | **Genel** > **hedef uzantısı** | **.pyd** |
    | | **Proje Varsayılanları** > **yapılandırma türü** | **Dinamik kitaplık (.dll)** |
    | **C/C++** > **genel** | **Ek içeren dizinler** | Python'u eklediğinizden *dahil* klasör, bu gibi bir durumda yükleme için uygun şekilde `c:\Python36\include`.  |
    | **C/C++** > **önişlemci** | **Önişlemci tanımları** | Ekleme `Py_LIMITED_API;` (noktalı virgül dahil) dize başlangıcına. Bu tanımı bazı işlevlere Python'dan çağırabilir ve kod Python farklı sürümleri arasında daha taşınabilir hale getirir kısıtlar. |
    | **C/C++** > **kod oluşturma** | **Çalışma Zamanı Kitaplığı** | **Çok iş parçacıklı DLL (/ MD)** (uyarı aşağıya bakın) |
    | **Bağlayıcı** > **genel** | **Ek Kitaplık dizinleri** | Python'u eklediğinizden *libs* içeren klasörü *.lib* Örneğin, yükleme için uygun şekilde dosyaları `c:\Python36\libs`. (İşaret edecek şekilde mutlaka *libs* içeren klasörü *.lib* dosyaları ve *değil* *LIB* içeren klasörü *.py*  dosyalarını.) |

    > [!Tip]
    > Proje Özellikleri'nde C/C++ sekmesini görmüyorsanız, proje, C/C++ kaynak dosyaları tanımlayan hiçbir dosya içermiyor olmasıdır. Olmayan bir kaynak dosyası oluşturursanız, bu durum ortaya çıkabilir bir *.c* veya *.cpp* uzantısı. Örneğin, yanlışlıkla girdiğiniz `module.coo` yerine `module.cpp` yeni öğe iletişim kutusunda daha önce ardından Visual Studio dosyayı oluşturur ancak dosya türü olarak ayarlayıp ayarlamadığını "C / C + kod," olduğu ne C/C++ Özellikleri sekmesi etkinleştirir. Dosyayı yeniden adlandırın bile durum böyle misidentification kalır `.cpp`. Dosya türü düzgün bir şekilde ayarlamak için dosyaya sağ **Çözüm Gezgini**seçin **özellikleri**, ardından **dosya türü** için **C/C++ kodu**.

    > [!Warning]
    > Her zaman **C/C++** > **kod oluşturma** > **çalışma zamanı kitaplığı** seçeneğini **çok iş parçacıklı DLL (/ MD)** olsa bile bir hata ayıklama yapılandırması için bu ayarı olduğundan hata ayıklama olmayan Python ikili dosyaları ile oluşturulur. Ayarlamak için MSDN aboneliğine **hata ayıklama çok iş parçacıklı DLL (/ MDd)** oluşturma seçeneği bir **hata ayıklama** yapılandırma hata üreten **C1189: Py_LIMITED_API, Py_TRACE_REFS, Py_DEBUG ile uyumlu değil ve Py_REF_DEBUG**. Ayrıca, kaldırırsanız `Py_LIMITED_API` derleme hatayı önlemek için Python modülü içe aktarmaya çalışıldığında çöküyor. (Kilitlenme DLL'nin çağrısı içinde olur `PyModule_Create` daha sonra çıktı iletisi ile açıklandığı **önemli Python hata: PyThreadState_Get: geçerli iş parçacığının**.)
    >
    > / MDd seçeneği Python hata ayıklama ikililerini derlemek için kullanılan (gibi *python_d.exe*), ancak bir uzantı DLL'si seçerek hala neden şu yapı hatasıyla `Py_LIMITED_API`.

1. C++ projesini sağ tıklayıp **derleme** yapılandırmalarınızı test etmek için (her ikisi de **hata ayıklama** ve **yayın**). *.Pyd* dosyaları bulunur **çözüm** klasörü altında **hata ayıklama** ve **yayın**, C++ proje klasörünün kendisi değil.

1. C++ proje için aşağıdaki kodu ekleyin *module.cpp* dosyası:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Kodunuzun doğru olduğunu onaylamak için yeniden C++ projesi oluşturun.

1. Zaten yapmadıysanız, aynı içeriğiyle "superfastcode2" adlı ikinci bir proje oluşturmak için yukarıdaki adımları yineleyin.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ projeleri için Python uzantıları için Dönüştür

C++ DLL için Python uzantısı'na yapmak için önce Python türleri ile etkileşim kurmak için verilen yöntemleri değiştirin. Modülüyle modülün yöntemlerin tanımlarını dışarı aktaran bir işlevi eklersiniz.

Aşağıdaki bölümlerde CPython uzantıları ve PyBind11 kullanarak bu adımların nasıl gerçekleştirileceğini açıklamaktadır.

### <a name="cpython-extensions"></a>CPython uzantıları

Python için bu bölümde gösterilen öğeleri üzerinde arka plan için 3.x başvurmak [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) ve özellikle [modülü nesneleri](https://docs.python.org/3/c-api/module.html) python.org üzerinde (Python'dan sürümünüz seçeneğini belirlemeyi unutmayın doğru belgeleri görüntülemek için sağ üst köşedeki aşağı açılan denetim).

Python 2.7 ile çalışıyorsanız, başvuracak [genişletme Python 2.7 C veya C++](https://docs.python.org/2.7/extending/extending.html) ve [taşıma uzantı modüllerini Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. Üst kısmındaki *module.cpp*, dahil *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Değiştirme `tanh_impl` kabul edin ve dönüş türleri Python yöntemi (bir `PyOjbect*`, diğer bir deyişle):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Tanımlayan bir yapı eklemek nasıl C++ `tanh_impl` işlevi için Python sunulur:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Python kodunuzun özellikle kullanırken başvurduğu istediğiniz modülü tanımlayan bir yapı eklemek `from...import` deyimi. (Bu proje özelliklerinde değerle aynı **yapılandırma özellikleri** > **genel** > **hedef adı**.) Aşağıdaki örnekte, "superfastcode" modül adı kullanabileceğiniz anlamına gelir `from superfastcode import fast_tanh` Python çünkü `fast_tanh` içinde tanımlanan `superfastcode_methods`. (Dosya adlarını C++ projesine iç ister *module.cpp*, göz önüne alınmaz.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python modülü adlandırılmalıdır yüklediğinde, çağıran bir yöntem ekleyin `PyInit_<module-name>`burada &lt;modül adı&gt; tam C++ projenin eşleşen **genel** > **hedef Adı** özelliği (diğer bir deyişle, dosya adı ile eşleşen *.pyd* proje tarafından oluşturulan).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Hedef yapılandırma kümesine **yayın** ve C++ kodunuzu yeniden doğrulamak için projeyi derleyin. Hatalarla karşılaşırsanız, bkz. [sorun giderme](#troubleshooting) bölümüne bakın.

### <a name="pybind11"></a>PyBind11

Önceki bölümdeki adımları tamamladıysanız, ortak kod çok sayıda C++ kodu için gerekli modülü yapıları oluşturmak için kullanılan kesinlikle fark. PyBind11 çok daha az kod ile aynı sonuca ulaşmak bir C++ üstbilgi dosyası makrolarındaki işlemini basitleştirir. Bu bölümde gösterilen arka plan bilgileri için bkz [PyBind11 Temelleri](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. PyBind11 yükleme PIP kullanarak: `pip install pybind11` veya `py -m pip install pybind11`.

1. Üst kısmındaki *module.cpp*, dahil *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Sayfanın alt kısmında *module.cpp*, kullanın `PYBIND11_MODULE` makrosu C++ işlevi için giriş noktası tanımlamak için:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Hedef yapılandırma kümesine **yayın** ve C++ kodunuzu doğrulamak için projeyi derleyin. Hatalarla karşılaşırsanız, sorun giderme sonraki bölüme bakın.

### <a name="troubleshooting"></a>Sorun giderme

C++ Modülü aşağıdaki nedenlerden dolayı derleme başarısız:

- Bulunamıyor *Python.h* (**E1696: kaynak dosyası "Python.h" açılamıyor** ve/veya **C1083: açık dosya içeremez: "Python.h": Böyle bir dosya veya dizin**): doğrulayın yolda **C/C++** > **genel** > **ek içerik dizinleri** Python proje özellikleri işaret yüklemenin *dahil* klasör. 6. adım altında bkz [core C++ projesi oluşturma](#create-the-core-c-projects).

- Python kitaplıkları bulunamıyor: doğrulayın yolunda **bağlayıcı** > **genel** > **ek kitaplık dizinleri** projedeki Python yüklemenizi ait özellikler noktalarına *libs* klasör. 6. adım altında bkz [core C++ projesi oluşturma](#create-the-core-c-projects).

- Bağlayıcı hatalarla ilgili için hedef mimari: C++ hedefin proje mimarisi Python yüklemenizi eşleşmesi için değiştirin. Örneğin, C++ proje x64 hedeflediğiniz Python yüklemenizi x86 varsa x86 hedeflemek için C++ projesi değiştirin.

## <a name="test-the-code-and-compare-the-results"></a>Kodu test edin ve sonuçları karşılaştırma

Python uzantıları yapılandırılmış DLL'leri olduğuna göre Python projesinden başvurmak modülleri içeri aktarmak ve kendi yöntemlerini kullanın.

### <a name="make-the-dll-available-to-python"></a>DLL Python için kullanılabilir yap

DLL Python için kullanılabilir hale getirmek için iki yolu vardır.

İlk yöntem, aynı çözüm içinde Python projesi ve C++ projesi varsa çalışır. Git **Çözüm Gezgini**, sağ **başvuruları** Python projesi ve ardından düğümünde **Başvuru Ekle**. Görüntülenen iletişim kutusunda, seçmek **projeleri** sekmesinde, her ikisini de seçin **superfastcode** ve **superfastcode2** projeleri tıklayın ve ardından **Tamam**.

![Superfastcode projeye bir başvuru ekleme](media/cpp-add-reference.png)

Aşağıdaki adımlarda anlatıldığı alternatif bir yöntem de diğer Python projeleri için kullanılabilir hale getirme global Python ortamı modülünü yükler. (Bu nedenle genellikle yapmak için Visual Studio 2017 sürüm 15.5 ve öncesi ortamında IntelliSense tamamlanma veritabanı yenileme gerektirir. Yenileme ayrıca modülü ortamdan kaldırırken gereklidir.)

1. Visual Studio 2017, Visual Studio Yükleyicisi'ni çalıştırın kullanıyorsanız seçin **Değiştir**seçin **tek tek bileşenler** > **derleyiciler, derleme araçları ve çalışma zamanları**  >  **Visual C++ 2015.3 v140 Araç Seti**. Python (Windows için) kendi Visual Studio 2015 (sürüm 14.0) ile oluşturulmuş ve araçlarda uzantı burada açıklanan yöntemi aracılığıyla oluşturulurken kullanılabilir olduğunu bekliyor olduğundan bu adım gereklidir. (Python'un 32 bit sürümünü yükleyip Win32 ve değil x64 DLL hedef gerekebileceğini unutmayın.)

1. Adlı bir dosya oluşturun *setup.py* projeye sağ tıklayıp seçerek C++ projesinde **Ekle** > **yeni öğe**. Ardından **C++ dosyası (.cpp)**, dosya adı `setup.py`seçip **Tamam** (ile dosya adlandırma *.py* Python tanıyacak Visual Studio extension yapar C++ dosyası şablonu kullanarak rağmen). Dosya düzenleyicisinde görüntülendiğinde aşağıdaki kodu genişletme yöntemi için uygun şekilde yapıştırın:

    **CPython Uzantıları (superfastcode Proje):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Bkz: [yapı C ve C++ uzantıları](https://docs.python.org/3/extending/building.html) (python.org) bu betik hakkında bilgi için.

    **PyBind11 (superfastcode2 Proje):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',    
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. *Setup.py* uzantısını kullanarak komut satırından kullanıldığında Visual Studio 2015 C++ araç takımı oluşturmak için Python kodu bildirir. Yükseltilmiş bir komut istemi açın, C++ projesi içeren klasöre gidin (diğer bir deyişle, içeren klasörü *setup.py*) ve aşağıdaki komutu girin:

    ```command
    pip install .
    ```

    veya:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Python'dan DLL çağırma

Şimdi, DLL kullanılabilir Python için önceki bölümde açıklandığı gibi yaptıktan sonra çağırabilirsiniz `superfastcode.fast_tanh` ve `superfastcode2.fast_tanh2` python'dan işlevler kod ve performanslarını Python uygulamaya karşılaştırın:

1. Aşağıdaki satırları ekleyin, *.py* dosya DLL'lerden dışarı yöntemlerini çağırır ve kendi çıkışları görüntülemek için:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Python programını çalıştırın (**hata ayıklama** > **hata ayıklama olmadan Başlat** veya **Ctrl**+**F5**) ve mesajının görüntülendiğini görün C++ yordamları yaklaşık beş ila yirmi kat daha hızlı Python uygulamasını çalıştırın. Normal çıktı aşağıdaki gibi görünür:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Varsa **hata ayıklama olmadan Başlat** komutu devre dışı bırakıldı, Python projeye sağ **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.

1. Artırmayı deneyin `COUNT` daha belirgin farklar için değişken. A **hata ayıklama** derleme C++ modülü de çalışır daha yavaş değerinden bir **yayın** çünkü derleme **hata ayıklama** yapı daha az iyileştirilmiştir ve çeşitli hata denetimleri içerir. Karşılaştırma için bu yapılandırmalar arasında geçiş çekinmeyin.

> [!NOTE]
> Çıkışta, düz bir Python uygulaması hala önemli ölçüde daha hızlı olmasına rağmen PyBind11 uzantısı CPython uzantısı olarak hızlı olmadığını görebilirsiniz. Az miktarda bir C++ arabirimiyle önemli ölçüde kolaylaştırmak için PyBind11 tanıtan çağrı başına ek yükü nedeniyle farktır. Bu çağrı başına fark gerçekten oldukça önemsizdir: test kodu 500.000 kez uzantı işlevleri çağırır çünkü Burada gördüğünüz büyük ölçüde sonuçları bu yükü yapın! Genellikle, bir C++ işlev Önemsiz daha çok daha fazla iş yapar `fast_tanh[2]` ek yükünü önemli değildir, bu durumda, burada kullanılan yöntemleri. Saniye başına binlerce çağıran yöntemleri uyguluyorsanız, ancak CPython yaklaşımı kullanarak daha iyi performans PyBind11 neden olabilir.

## <a name="debug-the-c-code"></a>C++ kod hatalarını ayıklama

Visual Studio hata ayıklama Python ve C++ kodu birlikte destekler. Bu bölümde işlem kullanarak adımları gösterilmektedir **superfastcode** proje; aynı adımlarla **superfastcode2** proje.

1. Python projeye sağ **Çözüm Gezgini**seçin **özellikleri**seçin **hata ayıklama** sekmesine tıklayın ve ardından **hata ayıklama**  >  **Yerel kod hata ayıklamayı** seçeneği.

    > [!Tip]
    > Yerel kodda hata ayıklama etkinleştirdiğinizde program, normal vermeden tamamlandığında hemen Python çıkış penceresine kaybolabilir **devam etmek için herhangi bir tuşa basın** duraklatın. Bir duraklatma zorlamak için ekleme `-i` seçeneğini **çalıştırın** > **yorumlayıcı bağımsız değişkenleri** alanını **hata ayıklama** sekmesinde yerel kodda hata ayıklama etkinleştirdiğinizde . Bu noktada bekler basın için kod bittikten sonra bu bağımsız değişken Python yorumlayıcısı etkileşimli moduna sokar **Ctrl**+**Z** > **girin**  çıkmak için. (Alternatif olarak, Python kodunuzu değiştirme sorun değilse ekleyebileceğiniz `import os` ve `os.system("pause")` programınızı sonunda deyimleri. Bu kod özgün duraklatma istemi çoğaltır.)

1. Seçin **dosya** > **Kaydet** özellik değişiklikleri kaydedin.

1. Derleme yapılandırması ayarlayın **hata ayıklama** Visual Studio araç.

    ![Derleme yapılandırması hata ayıklama için ayarlama](media/cpp-set-debug.png)

1. Kod genellikle hata ayıklayıcıda çalışması daha uzun sürer çünkü değiştirmek isteyebilirsiniz `COUNT` değişkenini, *.py* yaklaşık beş kat daha küçük bir değer dosyasına (örneğin, ondan değiştirin `500000` için `100000`).

1. C++ kodunuzu ilk satırında bir kesme noktası ayarlayın `tanh_impl` yöntemi, ardından hata ayıklayıcıyı başlatma (**F5** veya **hata ayıklama** > **hata ayıklamayı Başlat**). Bu kod çağırıldığında hata ayıklayıcıyı durdurur. Kesme noktasına isabet değil, yapılandırmayı ayarlamak denetleyin **hata ayıklama** ve (otomatik olarak hata ayıklayıcısı başlatılırken gerçekleşmez) proje kaydettiğiniz.

    ![C++ kodunda kesme noktası durduruluyor](media/cpp-debugging.png)

1. Bu noktada C++ kodunuz içinde adım adım, değişkenleri inceleyebilir ve benzeri. Bu özelliklerin ayrıntıları [C++ hata ayıklama ve Python birlikte](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatif yaklaşımlar

Python uzantıları aşağıdaki tabloda açıklandığı gibi oluşturmak için yol çeşitli vardır. İlk iki CPython ve PyBind11 ne bu makaledeki zaten değerlendirildi girişler.

| Yaklaşım | Hasat Yılı | Kullanıcı Temsilcisi | Pro(s) | CON(s) |
| --- | --- | --- | --- | --- |
| C/C++ uzantı modüllerini CPython için | 1991 | Standart Kitaplık | [Kapsamlı belgeler ve öğreticiler](https://docs.python.org/3/c-api/). Toplam denetimi. | Derleme, taşınabilirliği, başvuru yönetimi. Yüksek C bilgi. |
| [PyBind11](https://github.com/pybind/pybind11) (C++ için önerilir) | 2015 |  | Python bağlamaları var olan C++ kodu oluşturmak için basit, yalnızca üstbilgi kitaplığı. Birkaç bağımlılıkları. PyPy uyumluluğu. | Yeni, daha az olgun. Koyu C ++ 11 özelliklerini kullanın. Desteklenen derleyicileri (Visual Studio dahildir) kısa listesi. |
| Cython (Recommnded c) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python benzer. Yüksek oranda olgun. Yüksek performans. | Derleme, yeni söz dizimi, yeni bir araç zinciri. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Neredeyse her C++ derleyicisi ile çalışır. | Kitaplık paketi büyük ve karmaşık; eski derleyicileri için çok sayıda geçici çözümler içerir. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Hiçbir derleme geniş kullanılabilirlik. | Erişim ve C yapıları hantal ve hataya diziyi. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Tek seferde birçok dil için bağlamaları oluşturur. | Python yalnızca hedef ise aşırı yükü. |
| cffi | 2013 | [şifreleme](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Tümleştirme, PyPy uyumluluk kolaylığı. | Yeni, daha az olgun. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | C++ kullanarak cffi benzer. | Daha yeni sürümü, VS 2017 ile ilgili bazı sorunlar olabilir. |  

## <a name="see-also"></a>Ayrıca bkz.

Bu izlenecek yolda tamamlanmış örnekten bulunabilir [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
