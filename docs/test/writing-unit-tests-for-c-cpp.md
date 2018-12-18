---
title: C/C++ için birim testleri yazma
ms.date: 10/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: e19eb3bb421a69c902d9a10f0cdb3c5ac2244a04
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053750"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Visual Studio'da C/C++ için birim testleri yazma

Yazma ve C++ birim testlerinizi çalıştırmak **Test Gezgini** penceresi, diğer dillerde olduğu gibi. Kullanma hakkında daha fazla bilgi için **Test Gezgini**, bkz: [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> C++ için Live Unit Testing, kodlanmış UI testleri ve Intellitest gibi bazı özellikler desteklenmez.

Visual Studio bu C++ test çerçeveleri, gereken ek hiçbir yüklemeleriyle içerir:

- Microsoft birim testi çerçevesi için C++
- Google Test
- Boost.Test
- CTest

Yüklü çerçeveleri yanı sıra, Visual Studio içinde kullanmak istediğiniz her çerçeve için kendi test bağdaştırıcısı yazabilirsiniz. Birim testleriyle bir test bağdaştırıcısı tümleştirebilirsiniz **Test Gezgini** penceresi. Çeşitli üçüncü taraf bağdaştırıcıları bulunur [Visual Studio Market](https://marketplace.visualstudio.com). Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 sürüm 15.7 (Professional ve Enterprise)**

C++ birim testi projeleri desteği [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 sürüm 15.5**

- **Google Test bağdaştırıcısı** varsayılan bileşeni olarak eklenir **C++ ile masaüstü geliştirme** iş yükü. Bir çözüm ekleyebileceğiniz bir proje şablonu olan **Yeni Proje Ekle** çözüm düğümü bağlam menüsünde **Çözüm Gezgini**ve Seçenekler yoluyla yapılandırabileceğiniz **Araçları**  >  **Seçenekleri**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Google Test kullanmak](how-to-use-google-test-for-cpp.md).

- **Boost.Test** varsayılan bileşeni olarak eklenir **C++ ile masaüstü geliştirme** iş yükü. İle tümleşik **Test Gezgini** ancak şu anda proje şablonu yok, bu nedenle onu el ile yapılandırılması gerekir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Boost.Test kullanma](how-to-use-boost-test-for-cpp.md).

- **CTest** desteği ile birlikte [Visual Studio için CMake araçlarını](/cpp/ide/cmake-tools-for-visual-cpp) parçası olan bileşen, **C++ ile masaüstü geliştirme** iş yükü. Ancak, CTest henüz tam olarak tümleşiktir değil **Test Gezgini**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da CTest kullanma](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 veya önceki**

Bağdaştırıcının Google Test ve Boost.Test bağdaştırıcısı uzantıları Visual Studio Market'ten indirebilirsiniz [Boost.Test için Test bağdaştırıcısı](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) ve [Google Test için Test bağdaştırıcısı](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Temel test iş akışı

Aşağıdaki bölümlerde, C++ birim testi başlamanıza yardımcı olmak için temel adımları gösterilmektedir. Temel yapılandırma, Microsoft ve Google Test çerçeveleri için çok benzer. Boost.Test el ile bir test projesi oluşturmanız gerekir.

### <a name="create-a-test-project"></a>Bir test projesi oluşturma

Tanımlanır ve test etmek istediğiniz kodu aynı çözümde bulunan bir veya daha fazla test projeleri içindeki testleri çalıştır. Varolan çözüme yeni bir test projesi eklemek için ndeki çözüm düğümüne sağ **Çözüm Gezgini** ve **Ekle** > **yeni proje**. Sol bölmede seçin **Visual C++ Test** ve merkez bölmesinden proje türlerinden birini seçin. Ne zaman kullanılabilir olan test projeleri aşağıdaki çizimde **C++ ile masaüstü geliştirme** iş yükü yüklenir:

![C++ Test projeleri](media/cpp-new-test-project.png)

### <a name="create-references-to-other-projects-in-the-solution"></a>Çözümdeki diğer projelere başvuruları oluşturma

Test edilecek projedeki işlevlerine erişmek test kodunuzu etkinleştirmek için test projenizde projeye bir başvuru ekleyin. ' Nde test proje düğümüne sağ **Çözüm Gezgini** ve **Ekle** > **başvuru**. Ardından iletişim kutusunda, test etmek istediğiniz projeleri seçin.

![Başvuru ekleme](media/cpp-add-ref-test-project.png)

### <a name="add-include-directives-for-header-files"></a>Ekle #include için üst bilgi dosyaları

Sonra birim sınamanız *.cpp* ekleyin bir `#include` test etmek istediğiniz türleri ve işlevleri bildirme herhangi bir üst bilgi dosyaları yönergesi. Tür `#include "` ve seçmenize yardımcı olması için IntelliSense sonra etkinleşir. Ek üst bilgilere için yineleyin.

![Ekleme yönergelerinde](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Test yöntemleri yazın

> [!NOTE]
> Bu bölüm, C/C++ için Microsoft birim testi çerçevesi için söz dizimini gösterir. Burada belgelenmektedir: [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Google Test belgeleri için bkz. [Google Test öncü](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Boost.Test için bkz: [Boost Test kitaplığı: birim testi çerçevesi](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

*.Cpp* dosyası test projenize bir saptama sınıfı ve kodu test yazma ilişkin bir örnek olarak tanımlanan yöntemi vardır. İmzaları yöntemleri gelen bulunabilir hale TEST_CLASS ve TEST_METHOD makroları kullandığını unutmayın **Test Gezgini** penceresi.

![Ekleme yönergelerinde](media/cpp-write-test-methods.png)

TEST_CLASS ve TEST_METHOD parçası olan [Microsoft Yerel Test çerçevesi](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Test Gezgini** desteklenen diğer çerçeveler test yöntemlerinde benzer şekilde bulur.

Bir TEST_METHOD void döndürür. Bir test sonucu oluşturmak için statik yöntemleri kullanın. `Assert` gerçek sonuçlar, beklenen değer karşı test etmek için sınıf. Aşağıdaki örnekte, varsayalım `MyClass` alan bir oluşturucu sahip bir `std::string`. Oluşturucu beklendiği gibi sınıfı başlatır sınayabiliriz şu şekilde:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

Önceki örnekte, sonucunu `Assert::AreEqual` çağrı, testin başarılı veya başarısız olup olmadığını belirler. Assert sınıfı, beklenen gerçek sonuçlar karşılaştırma için birçok yöntem içerir.

Ekleyebileceğiniz *nitelikler* yöntemleri test sahipleri, öncelik ve diğer bilgileri belirtmek için test etmek için. Ardından bu değerleri sıralama ve Gruplama testler için kullanabileceğiniz **Test Gezgini**. Daha fazla bilgi için [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Testleri çalıştırın

1. Üzerinde **Test** menüsünde seçin **Windows** > **Test Gezgini**. Aşağıdaki çizim bir test projesi olan testleri henüz çalıştırılmamış gösterir.

   ![Test Gezgini testleri çalıştırmadan önce](media/cpp-test-explorer.png)

   > [!NOTE]
   > CTest tümleştirme **Test Gezgini** henüz kullanıma sunulmamıştır. CMake ana menüden CTest testleri çalıştırın.

1. Testlerinizin tümünü penceresinde görünür değilse, onun düğümüne sağ tıklayarak test projesi oluşturmak **Çözüm Gezgini** seçip **derleme** veya **yeniden**.

1. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**, ya da belirli testleri çalıştırmak istediğiniz seçin. Bir test etkin kesme noktaları ile hata ayıklama modunda çalıştırmak dahil, diğer seçenekler için sağ tıklayın. Tüm testleri çalıştırdıktan sonra hangi testleri geçti ve hangilerinin başarısız pencere gösterir:

![Testler çalıştıktan sonra test Gezgini](media/cpp-test-explorer-passed.png)

Başarısız testler için ileti nedenini tanılamaya yardımcı olan ayrıntılar sunar. Başarısız testi sağ tıklatın ve seçin **seçilen Testlerde Hata Ayıkla** hatanın oluştuğu fonksiyona adıma.

Kullanma hakkında daha fazla bilgi için **Test Gezgini**, bkz: [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md).

Birim testi için ilgili en iyi yöntemler için bkz. [birim testi temel bilgileri](unit-test-basics.md)

## <a name="use-codelens"></a>CodeLens kullanın

**Visual Studio 2017 sürüm 15.7 Professional ve Enterprise sürümleri yalnızca**: [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) hızlı bir şekilde kod düzenleyicisinden çıkmadan test birimi durumunu görmenizi sağlar. CodeLens, bir C++ birim testi projesi şu yollardan birinde için başlatabilirsiniz:

- Düzenle ve test projenizi veya çözümünüzü oluşturun.
- Proje veya çözümü yeniden oluşturun.
- Öğesinden test çalıştırma **Test Gezgini** penceresi.

Sonra **CodeLens** başlatıldı, gördüğünüz durumu simgeleri her bir birim testi üzerinde test edin.

![C++ CodeLens simgeler](media/cpp-test-codelens-icons.png)

 Daha fazla bilgi edinmek veya çalıştırmak veya birim testi hata ayıklama için simgesine tıklayın:

![C++ CodeLens çalıştırma ve hata ayıklama](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Ayrıca bkz.

[Birim testi kod](unit-test-your-code.md)
