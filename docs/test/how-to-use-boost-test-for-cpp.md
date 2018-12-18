---
title: Boost.Test için C++ kullanma
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 65ee2d95d85c657057f7ef4494c19f8b5644513e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063253"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio'da C++ için Boost.Test kullanma

İçinde **Visual Studio 2017 sürüm 15.5** ve Boost.Test test bağdaştırıcısı olarak Visual Studio IDE'ye daha sonra tümleşiktir **C++ ile masaüstü geliştirme** iş yükü.

![Boost.Test için test bağdaştırıcısı](media/cpp-boost-component.png)

Öğeniz yoksa **C++ ile masaüstü geliştirme** iş yükü yüklenmiş, açık **Visual Studio yükleyicisi** seçip **Değiştir**. Seçin **C++ ile masaüstü geliştirme** iş yükü, ardından **Değiştir** düğmesi.

## <a name="install-boost"></a>Boost yükleyin

Boost.Test gerektirir [Boost](http://www.boost.org/)! Boost yüklü değilse, Vcpkg Paket Yöneticisi'ni kullanmanızı öneririz.

1. Konumundaki yönergeleri [Vcpkg: C++ Paket Yöneticisi Windows için](/cpp/vcpkg) vcpkg yükleme (Bu yoksa).

1. Boost.Test dinamik veya statik Kitaplığı'nı yükleyin:

    - Çalıştırma **vcpkg yükleme boost test** Boost.Test dinamik kitaplığını yüklemek için.

       -VEYA-

    - Çalıştırma **vcpkg boost yükleyin-test: x 86 windows statik** Boost.Test statik kitaplığı yüklemek için.

1. Çalıştırma **vcpkg tümleştirme yükleme** Visual Studio şu kitaplıkla yapılandırıp yolları Boost üst bilgiler ve ikili dosyalarını içerir.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>(Visual Studio 2017 sürüm 15.6 ve üzeri) öğe şablonu Ekle

1. Oluşturmak için bir *.cpp* 'nde proje düğümüne sağ tıklayın, testleriniz için dosya **Çözüm Gezgini** ve **Yeni Öğe Ekle**.

   ![Boost.Test öğe şablonu](media/boost_test_item_template.png)

1. Örnek test yöntemi yeni bir dosya içerir. Etkinleştirmek için projenizi derleyin **Test Gezgini** yöntemi bulunacak.

Boost.Test tek üstbilgi çeşidini öğesi şablonu kullanır ancak değiştirebilirsiniz #include tek başına kitaplığı değişken kullanılacak yol. Daha fazla bilgi için [Ekle ekleme yönergelerini](#add-include-directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Bir test projesi (Visual Studio 2017 sürüm 15.5) oluşturma

Visual Studio 2017 sürüm 15.5, önceden yapılandırılmış test proje veya öğe şablonları Boost.Test için kullanılabilir. Bu nedenle, oluşturun ve testlerinizi tutmak için bir konsol uygulama projesi yapılandırmanız gerekir.

1. İçinde **Çözüm Gezgini**çözüm düğümüne sağ tıklayın ve seçin **Ekle** > **yeni proje**.

1. Sol bölmede seçin **Visual C++** > **Windows Masaüstü**ve ardından **Windows konsol uygulaması** şablonu.

1. Projeye bir ad verin ve seçin **Tamam**.

1. Silme `main` işlevi *.cpp* dosya.

1. Boost.Test tek üst bilgi veya dinamik kitaplık sürümünü kullanıyorsanız, Git [Ekle ekleme yönergelerini](#add-include-directives). Statik kitaplık sürümünü kullanıyorsanız, bazı ek yapılandırmalar yapmanız gerekir:

   a. Projeyi dosyasını düzenlemek için önce bunu kaldırın. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve seçin **projeyi**. Ardından proje düğümünü sağ tıklatın ve seçin **Düzenle < adı\>.vcxproj**.

   b. İçin iki satırı ekleyin **Globals** burada gösterildiği gibi özellik grubu:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Kaydet ve Kapat  *\*.vcxproj* dosyasını bulun ve ardından projeyi yeniden yükleyin.

   d. Açmak için **özellik sayfaları**, proje düğümüne sağ tıklayın ve seçin **özellikleri**.

   d. Genişletin **C/C++** > **kod oluşturma**ve ardından **çalışma zamanı kitaplığı**. Seçin **/mtd** için hata ayıklama statik çalışma zamanı kitaplığı veya **/MT** yayın statik çalışma zamanı kitaplığı.

   f. Genişletin **bağlayıcı** > **sistem**. Doğrulayın **alt** ayarlanır **konsol**.

   g. Seçin **Tamam** özellik sayfalarını kapatmak için.

## <a name="add-include-directives"></a>Ekleme yönergelerinde

1. Testinizde *.cpp* dosya, gerekli ekleyin `#include` programınızın türleri ve işlevleri test kodu görünür yapmak için yönergeleri. Genellikle, bir düzey klasör hiyerarşisindeki bir programdır. Yazarsanız `#include "../"`, IntelliSense penceresi görünür ve üst bilgi dosyasının tam yolu seçmenize olanak sağlar.

   ![Ekle #include](media/cpp-gtest-includes.png)

   Tek başına kitaplığı ile kullanabilirsiniz:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Veya, tek üst bilgi sürümüyle kullanın:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Daha sonra tanımlamak `BOOST_TEST_MODULE`.

Aşağıdaki örnek olarak bulunabilir olması test için yeterliyse **Test Gezgini**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Yazma ve testleri çalıştırma

Artık yazmak ve Boost testleri çalıştırmak hazırsınız. Bkz: [Boost test kitaplığı belgeleri](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html) test makrolar hakkında daha fazla bilgi için. Bkz: [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md) kullanarak testlerinizi gruplandırma bulma ve çalıştırma hakkında bilgi için **Test Gezgini**.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)
