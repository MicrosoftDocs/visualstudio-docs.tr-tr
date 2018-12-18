---
title: "Nasıl yapılır: C++ DLL'leri için birim testleri yazma"
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 9458fd6886243102f6479166fb9df21f9e4869fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877263"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Nasıl yapılır: C++ DLL'leri için birim testleri yazma

Bu izlenecek yolda, önce test yöntemi kullanarak yerel bir C++ DLL geliştirme konusunda açıklanmaktadır. Temel adımlar aşağıdaki gibidir:

1.  [Yerel test projesi oluşturma](#create_test_project). Test projesi, DLL projesi olarak aynı çözüm içinde bulunur.

2.  [Bir DLL projesi oluşturma](#create_dll_project). Bu izlenecek yol, yeni bir DLL oluşturur, ancak mevcut bir DLL sınama yordamını benzer.

3.  [DLL işlevleri testler tarafından görülebilmesi](#make_functions_visible).

4.  [Yinelemeli olarak testleri genişletme](#iterate). Kod geliştirme testleri tarafından kılavuzluk edilir, bir "kırmızı-yeşil-düzenleme" döngüsünde öneririz.

5.  [Başarısız olan Testlerde Hata Ayıkla](#debug). Hata ayıklama modunda testleri çalıştırabilirsiniz.

6.  [Testleri değişmeden tutarken yeniden düzenleme](#refactor). Yeniden düzenleme kod yapısını dış davranışını değiştirmeden geliştirme anlamına gelir. Performans, genişletilebilirlik ve kodun okunabilirliğini geliştirmek için bunu yapabilirsiniz. Davranış değiştirilmemesi niyetini olduğu için kodu yeniden düzenleme değişiklik yapma sırasında testleri değiştirmeyin. Testleri sırasında yeniden düzenleme, hata ekleme sağlanmasına yardımcı olur.

7.  [Kapsamı denetleme](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Birim testleri, kodunuzun daha fazla çalışma daha yararlı olur. Kodunuzun hangi parçalarının testler tarafından kullanılmış olan bulabilir.

8.  [Dış kaynaklara birimlerinden yalıtmak](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Genellikle, bir DLL, diğer DLL'leri, veritabanları ya da uzak alt sistemleri gibi geliştiriyorsunuz sisteminin diğer bileşenlere bağlıdır. Her birim bağımlılıklarını yalıtımdan test kullanışlıdır. Dış bileşenlerin yavaş çalıştırmak testlerini yapabilirsiniz. Geliştirme sırasında diğer bileşenleri eksik olabilir.

##  <a name="create_test_project"></a> Yerel birim testi projesi oluşturma

1.  Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

     İletişim kutusunda, **yüklü** > **şablonları** > **Visual C++** > **Test**.

     Seçin **yerel birim testi projesi** şablonu veya ne olursa olsun yüklü tercih ettiğiniz çerçeve. Google Test veya Boost.Test gibi başka bir şablonu seçerseniz, bazı ayrıntılar farklılık gösterir ancak temel ilkelerini aynıdır.

     Bu kılavuzda, test projesi adlı `NativeRooterTest`.

     ![C++ birim testi projesi oluşturma](../test/media/utecpp01.png)

2.  Yeni projede, inceleme **unittest1.cpp**

     ![Test projesi içeren TEST&#95;sınıfı ve TEST&#95;yöntemi](../test/media/utecpp2.png)

     Şunlara dikkat edin:

    -   Her bir testi kullanılarak tanımlanmış `TEST_METHOD(YourTestName){...}`.

         Geleneksel işlev imzası yazmanız gerekmez. İmza TEST_METHOD makro tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca, test yöntemi hakkında bilgi döndüren statik bir işlev oluşturur. Test Gezgini, yöntem bulmak bu bilgileri sağlar.

    -   Test yöntemleri, sınıflara kullanarak gruplanır `TEST_CLASS(YourClassName){...}`.

         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemlerini belirtilmemiş sırayla çağrılır. Önce ve sonra her bir modül, sınıf veya yöntemi çağıran özel yöntemi tanımlayabilirsiniz.

3.  Testleri Test Gezgini'nde çalıştırma doğrulayın:

    1.  Bazı test kodu ekleyin:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Dikkat `Assert` sınıfı yöntemleri test sonuçlarında doğrulamak için kullanabileceğiniz birkaç statik yöntemler sağlar.

    2.  Üzerinde **Test** menüsünde seçin **çalıştırma** > **tüm testleri**.

         Test derlenir ve çalışır.

         **Test Gezgini** görünür.

         Test altında görünür **başarılı testler**.

         ![Birim Test Gezgini ile bir geçen test](../test/media/utecpp04.png)

##  <a name="create_dll_project"></a> Bir DLL projesi oluşturma

1.  Oluşturma bir **Visual C++** kullanarak proje **Win32 projesi** şablonu.

     Bu izlenecek yolda, proje adı `RootFinder`.

     ![Bir C++ Win32 projesi oluşturma](../test/media/utecpp05.png)

2.  Seçin **DLL** ve **sembolleri dışarı aktarma** Win32 Uygulama Sihirbazı'nda.

     **Sembolleri dışa aktar** seçeneği, dışa aktarılan bir yöntemi bildirmek için kullanabileceğiniz uygun bir makro oluşturur.

     ![DLL ve sembolleri dışarı aktarmak için C++ Proje Sihirbazı](../test/media/utecpp06.png)

3.  Sorumlunun dışa aktarılan bir işlevin bildirmek *.h* dosyası:

     ![Yeni DLL kod projesi ve .h dosyası ile API makroları](../test/media/utecpp07.png)

     Bildirimci `__declspec(dllexport)` DLL dışında görünür olmasını ortak ve korunan üyeleri sınıf neden olur. Daha fazla bilgi için [C++ sınıflarında dllimport ve dllexport kullanma](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4.  Sorumlunun *.cpp* dosya, işlev için en az bir gövdesi ekleyin:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

##  <a name="make_functions_visible"></a> Birkaç DLL projesi için test projesi

1. DLL projesi için test projesinin proje başvurularını ekleyin:

   1.  Test proje özelliklerini açın ve seçin **ortak özellikler** > **çerçeve ve başvurular**.

        ![C++ proje özelliklerini | Çerçeve ve başvurular](../test/media/utecpp08.png)

   2.  Seçin **Yeni Başvuru Ekle**.

        İçinde **Başvuru Ekle** iletişim kutusunda, DLL projesi seçip **Ekle**.

        ![C++ proje özelliklerini | Yeni Başvuru Ekle](../test/media/utecpp09.png)

2. Asıl birim testinde *.cpp* dosya, dahil *.h* DLL kod dosyası:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dışarı aktarılan işlevin kullanan temel bir test ekleyin:

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
      Assert::AreEqual(
         // Expected value:
         0.0,
         // Actual value:
         rooter.SquareRoot(0.0),
         // Tolerance:
         0.01,
        // Message:
        L"Basic test failed",
        // Line number - used if there is no PDB file:
        LINE_INFO());
   }
   ```

4. Çözümü oluşturun.

    Yeni test görünür **Test Gezgini**.

5. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

    ![Birim Test Gezgini &#45; temel testi geçildi](../test/media/utecpp10.png)

   Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.

##  <a name="iterate"></a> Yinelemeli olarak testleri genişletme ve onları geçirin

1.  Yeni bir test ekleyin:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.
    >
    > Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.

2.  Çözümü derleyin ve ardından **Test Gezgini**, seçin **tümünü Çalıştır**.

     Yeni test başarısız olur.

     ![RangeTest başarısız](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.

3.  DLL kodunuzu geliştirmek, böylece yeni test geçer:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4.  Çözümü derleyin ve ardından **Test Gezgini**, seçin **tümünü Çalıştır**.

     Her iki testler başarılı.

     ![Birim Test Gezgini &#45; aralığı testi geçildi](../test/media/utecpp12.png)

    > [!TIP]
    > Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.

##  <a name="debug"></a> Başarısız bir test hatalarını ayıklama

1.  Başka bir test ekleyin:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2.  Çözümü derleyin ve seçin **tümünü Çalıştır**.

3.  Başarısız test açın (veya çift).

     Onaylama başarısız vurgulanır. Hata iletisi ayrıntı bölmesinde görünür **Test Gezgini**.

     ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4.  Testin neden başarısız görmek için işlev adım:

    1.  SquareRoot işlevin başında bir kesme noktası ayarlayın.

    2.  Başarısız test kısayol menüsünde **seçilen Testlerde Hata Ayıkla**.

         Kesme noktasında çalıştırma sona erdiğinde, kodda adım adım.

5.  Geliştirmekte olduğunuz işlev kodu ekleyin:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6.  Artık tüm sınamaları geçmesi.

     ![Tüm testler başarılı](../test/media/ute_ult_alltestspass.png)

> [!TIP]
> Paralel test yürütme ile bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, açma ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.


##  <a name="refactor"></a> Testleri değiştirmeden kodu yeniden düzenleme

1.  SquareRoot işlevi merkezi hesaplamaya kolaylaştırma:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2.  Çözümü derleyin ve seçin **tümünü Çalıştır**, size bir hata oluşturmadığından emin emin olmak için.

    > [!TIP]
    > İyi bir dizi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.
    >
    > Diğer değişikliklerden ayrı düzenlemesi tutun.

## <a name="next-steps"></a>Sonraki adımlar

-   **Yalıtım.** Çoğu DLL'leri, veritabanları ve diğer DLL'leri gibi başka alt sistemlerin bağlıdır. Bu diğer bileşenler genellikle paralel olarak geliştirilir. Birim testinin diğer bileşenleri henüz kullanılabilir değildir; ancak gerçekleştirilmesine izin vermek için sahte yerine olması veya

-   **Yapı doğrulama testleri.** Belirlenen aralıklarda takımınızın yapı sunucusunda gerçekleştirilen testler olabilir. Bu, birkaç takım üyelerinin iş tümleştirildiğinde hatanın değil sağlar.

-   **İade etme sınar.** Bazı testler her ekip üyesi, kod kaynak denetimine iade etmeden önce gerçekleştirilen zorunlu. Genellikle bu yapı doğrulama testlerini eksiksiz bir alt kümesidir.

     En az bir kod kapsamı düzeyini zorunlu kılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma](how-to-use-microsoft-test-framework-for-cpp.md)
- [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
- [İzlenecek yol: Oluşturma ve kullanarak bir dinamik bağlantı kitaplığı (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [İçeri ve dışarı aktarma](/cpp/build/importing-and-exporting)
