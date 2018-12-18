---
title: C++ için Microsoft Birim Testi Çerçevesini Kullanma
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 88265c1ac86b5b1c1cd90ef428c9c2c770d9f2a2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068266"
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Microsoft birim testi çerçevesi Visual Studio'da C++ için kullanın

C++ için Microsoft birim testi çerçevesi varsayılan olarak dahil edilen **C++ ile masaüstü geliştirme** iş yükü.

##  <a name="separate_project"></a> Ayrı bir projede birim testleri yazma

Genellikle, test kodunuzu test etmek istediğiniz kodu aynı çözümde kendi projesi içinde çalıştırın. Ayarlama ve yeni bir test projesi yapılandırma için bkz: [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Aynı projede birim testleri yazma

Bazı durumlarda, örneğin bir DLL içinde aktarılmış işlevlerini test ederken testleri test programı olarak aynı projede oluşturmanız gerekebilir. Aynı projede birim testleri yazmak için:

1. Proje özelliklerini, üst bilgiler ve birim testi için gerekli olan kitaplık dosyalarını içerecek şekilde değiştirin.

   1. İçinde **Çözüm Gezgini**, test programı için proje düğümüne sağ tıklayın ve ardından seçin **özellikleri** > **yapılandırma özellikleri**  >  **VC ++ dizinleri**.

   2. Aşağıdaki satırları aşağı oka tıklayın ve seçin **<Edit>** :


      | Dizin | Özellik |
      |-| - |
      | **Ekleme kodu dizinleri** | **$(VCInstallDir)UnitTest\include;$(IncludePath)** |
      | **Kitaplık dizinleri** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)** |


2. Bir C++ birim testi dosyası ekleyin:

   -   ' Nde proje düğümüne sağ **Çözüm Gezgini** ve **Ekle** > **yeni öğe** > **C++ birim testi**.

## <a name="write-the-tests"></a>Testleri yazma

Tüm *.cpp* test sınıflarında dosyasıyla "CppUnitTest.h" içerir ve kullanarak bir deyim için `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Test projesi için zaten yapılandırıldı. Ayrıca bir ad alanı tanımını içerir ve bir TEST_CLASS başlamanızı sağlayacak bir TEST_METHOD ile başlatıldı. Ad alanı adının yanı sıra adlar parantez içinde sınıf ve metod makroları değiştirebilirsiniz.

Test tamamlandığında özel makroları test modülleri, sınıflar ve yöntemler başlatma ve temizleme işlemini resoures tanımlanır. Bu makrolar, bir sınıf veya yöntemin ilk erişmeden önce ve son bir testi çalıştırdıktan sonra yürütülen kod oluşturur. Daha fazla bilgi için [başlatma ve Temizleme](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup).

Statik yöntemleri kullanın [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) sınıfı test koşulları tanımlayın. Kullanım [Günlükçü](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) sınıfı için ileti yazmak için **çıkış penceresine**. Test yöntemleri için öznitelik Ekle

## <a name="run-the-tests"></a>Testleri çalıştırın

1. Üzerinde **Test** menüsünde seçin **Windows** > **Test Gezgini**.
2. Testlerinizin tümünü penceresinde görünür değilse, onun düğümüne sağ tıklayarak test projesi oluşturmak **Çözüm Gezgini** seçip **derleme** veya **yeniden**.

3. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**, ya da belirli testleri çalıştırmak istediğiniz seçin. Bir test etkin kesme noktaları ile hata ayıklama modunda çalıştırmak dahil, diğer seçenekler için sağ tıklayın.
4. İçinde **çıkış penceresine** seçin **testleri** açılan view iletileri tarafından yazılan aşağı `Logger` sınıfı:

   ![C++ çıkış penceresine sınama iletileri gösterme](media/cpp-test-output-window.png)

## <a name="define-traits-to-enable-grouping"></a>Gruplandırma etkinleştirmek için özellikleri tanımlayın

Nitelikler kategorilere ayırmak ve testleri gruplamak etkinleştiren bir test yöntemleri tanımlayabilirsiniz **Test Gezgini**. Ayırt edici nitelik tanımlamak için `TEST_METHOD_ATTRIBUTE` makrosu. Örneğin, adlı bir ayırt edici nitelik tanımlamak için `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Tanımlanan niteliği birim testlerinizde kullanmak için:

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ ayırt edici öznitelik makroları

Aşağıdaki önceden tanımlanmış nitelikler bulunan `CppUnitTest.h`. Daha fazla bilgi için [Microsoft birim testi çerçevesi için C++ API Başvurusu](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md).

|Makrosu|Açıklama|
|-|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Ayırt edici nitelik tanımlamak için test_method_attrıbute makrosunu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış sahip ayırt edici niteliğini kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikler atamak için önceden tanımlanmış öncelik ayırt edici niteliğini kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: temelli geliştirme, Test Gezgini ile Test](../test/quick-start-test-driven-development-with-test-explorer.md)
