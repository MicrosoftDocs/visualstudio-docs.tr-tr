---
title: Bir Visual C++ DLL'ye UWP uygulamaları için test etme
ms.date: 02/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- uwp
author: mikeblome
ms.openlocfilehash: 4081fae86b41a9bf8b925bf84d403b3be6628294
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068373"
---
# <a name="how-to-test-a-visual-c-dll"></a>Bir Visual C++ DLL'ye test etme

Bu konuda, C++ için birim testleri Microsoft Test Çerçevesi ile Evrensel Windows Platformu (UWP) uygulamaları için C++ DLL için oluşturma yöntemlerinden biri açıklanmaktadır. RooterLib DLL, belirsiz bellek sınırı teorik, hesaplama bir tahminini verilen bir sayının kare kökünü hesaplayan bir işlevi uygulayarak gösterir. DLL ardından eğlenceli bir kullanıcı gösteren bir UWP uygulamasında eklenebilir matematik ile yapılabilir şeyler.

 Bu konuda birim testi geliştirmede ilk adım olarak kullanma işlemini gösterir. Bu yaklaşım önce test ettiğiniz sistemde belirli bir davranış doğrulayan bir test yöntemi yazın ve ardından testin başarılı olması kod yazacaksınız. Aşağıdaki yordamlar sırasına göre değişiklikler yaparak, bu strateji ilk Yazımdan sonra birim testleri yazma ve test etmek istediğiniz kod tersine çevirebilirsiniz.

 Bu konuda ayrıca tek bir Visual Studio çözümü de ayrı projeler için birim testleri ve test etmek istediğiniz DLL oluşturur. Doğrudan DLL projede birim testleri de içerebilir veya ayrı çözümler için birim testleri oluşturabilirsiniz ve. DLL. Bkz: [mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) kullanmak için hangi yapı ilişkin ipuçları için.

##  <a name="Create_the_solution_and_the_unit_test_project"></a> Çözüm ve birim testi projesi oluşturma

1.  Üzerinde **dosya** menüsünde seçin **yeni** > **yeni proje**.

2.  Yeni Proje iletişim kutusunda Genişlet **yüklü** > **Visual C++** ve **Windows Evrensel**. Ardından **birim testi uygulaması (Evrensel Windows)** proje şablonları listesinden.

3.  Projeyi adlandırın `RooterLibTests`; konumu belirtin; çözümünü arlandırın `RooterLib`; emin **çözüm için dizin oluştur** denetlenir.

     ![Çözüm ve proje adını ve konumunu belirtin](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

4.  Yeni projeyi **unittest1.cpp**.

     ![UnitTest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Aşağıdakilere dikkat edin:

    -   Her bir testi kullanılarak tanımlanmış `TEST_METHOD(YourTestName){...}`.

         Geleneksel işlev imzası yazmanız gerekmez. İmza TEST_METHOD makro tarafından oluşturulur. Makro, void döndüren bir örnek işlevi oluşturur. Ayrıca, test yöntemi hakkında bilgi döndüren statik bir işlev oluşturur. Test Gezgini, yöntem bulmak bu bilgileri sağlar.

    -   Test yöntemleri, sınıflara kullanarak gruplanır `TEST_CLASS(YourClassName){...}`.

         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemlerini belirtilmemiş sırayla çağrılır. Önce ve sonra her bir modül, sınıf veya yöntemi çağıran özel yöntemi tanımlayabilirsiniz. Daha fazla bilgi için [Microsoft.VisualStudio.TestTools.CppUnitTestFramework kullanma](how-to-use-microsoft-test-framework-for-cpp.md).

##  <a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Testleri Test Gezgini'nde çalıştırma doğrulayın

1.  Bazı test kodu ekleyin:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Dikkat `Assert` sınıfı yöntemleri test sonuçlarında doğrulamak için kullanabileceğiniz birkaç statik yöntemler sağlar.

2.  Üzerinde **Test** menüsünde seçin **çalıştırma** seçip **tümünü Çalıştır**.

     Test projesi oluşturur ve çalıştırır. **Test Gezgini** penceresi görünür ve test altında listelenen **başarılı testler**. **Özeti** pencerenin alt kısmındaki bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

     ![Test Gezgini](../test/media/ute_cpp_testexplorer_testmethod1.png)

##  <a name="Add_the_DLL_project_to_the_solution"></a> DLL projesi çözüme ekleyin.

1.  İçinde **Çözüm Gezgini**, çözüm adı seçin. Kısayol menüsünden **Ekle**, ardından **Yeni Proje Ekle**.

     ![RooterLib projesi oluşturma](../test/media/ute_cpp_windows_rooterlib_create.png)

2.  İçinde **Yeni Proje Ekle** iletişim kutusunda **DLL (UWP uygulamaları)**.

3.  Aşağıdaki kodu ekleyin *RooterLib.h* dosyası:

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Yorumlar yalnızca dll geliştiriciye ancak herkes tarafından DLL içinde kendi proje başvurusu ifdef bloğu açıklanmaktadır. DLL proje özelliklerini kullanarak, komut satırına ROOTERLIB_EXPORTS sembol ekleyebilirsiniz.

     `CRooterLib` Sınıfı Oluşturucu bildirir ve `SqareRoot` estimator yöntemi.

4.  ROOTERLIB_EXPORTS sembol komut satırına ekleyin.

    1.  İçinde **Çözüm Gezgini**, seçin **RooterLib** proje ve ardından **özellikleri** kısayol menüsünden.

         ![Önişlemci sembolü tanımı Ekle](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2.  İçinde **RooterLib özellik sayfası** iletişim kutusunda **yapılandırma özellikleri**, genişletme **C++** ve **önişlemci**.

    3.  Seçin  **\<Düzenle … >** gelen **önişlemci tanımları** listeleyin ve ardından ekleyin `ROOTERLIB_EXPORTS` içinde **önişlemci tanımları** iletişim kutusu.

5.  Bildirilen işlevlerin en az uygulamaları ekleyin. Açık *RooterLib.cpp* ve aşağıdaki kodu ekleyin:

    ```cpp
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

##  <a name="make_the_dll_functions_visible_to_the_test_code"></a> Dll işlevleri test kodu tarafından görülebilir kılma

1. RooterLib RooterLibTests projeye ekleyin.

   1.  İçinde **Çözüm Gezgini**, seçin **RooterLibTests** proje ve ardından **başvuruları** kısayol menüsünde.

   2.  Üzerinde **RooterLib proje özellikleri** iletişim kutusunda **ortak özellikler** ve **çerçeve ve başvurular**.

   3.  Seçin **Yeni Başvuru Ekle**

   4.  İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** seçip **projeleri**. Ardından **RouterLib** öğesi.

2. RooterLib üstbilgi dosyasına eklenecek *unittest1.cpp*.

   1.  Açık *unittest1.cpp*.

   2.  Bu kod için aşağıdaki ekleme `#include "CppUnitTest.h"` satırı:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. İçeri aktarılan işlevini kullanan bir test ekleyin. Aşağıdaki kodu ekleyin *unittest1.cpp*:

   ```cpp
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
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

    Yeni test görünür **Test Gezgini** içinde **çalıştırılmamış testler** düğümü.

5. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

    ![Temel Test geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

   Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.

##  <a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Yinelemeli olarak testleri genişletme ve onları geçirin

1.  Yeni bir test ekleyin:

    ```cpp
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };
    ```

    > [!TIP]
    > Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.
    >
    > Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.

2.  İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

3.  Test başarısız olur.

     ![RangeTest başarısız](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.

4.  Yeni test geçer, test edilen kod geliştirin. Ekleyin *RooterLib.cpp*:

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
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

5.  Çözümü derleyin ve ardından **Test Gezgini**, seçin **tümünü Çalıştır**.

     Her iki testler başarılı.

> [!TIP]
> Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.


##  <a name="Debug_a_failing_test"></a> Başarısız bir test hatalarını ayıklama

1. Başka bir test eklemek *unittest1.cpp*:

   ```cpp
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };
   ```

2. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

    Test başarısız olur. Test adı seçmenize **Test Gezgini**. Onaylama başarısız vurgulanır. Hata iletisi ayrıntı bölmesinde görünür **Test Gezgini**.

    ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız görmek için işlev adım:

   1.  Başında bir kesme noktası ayarlamak `SquareRoot` işlevi.

   2.  Başarısız test kısayol menüsünde **seçilen Testlerde Hata Ayıkla**.

        Kesme noktasında çalıştırma sona erdiğinde, kodda adım adım.

   3.  Kodu *RooterLib.cpp* istisna yakalamak için:

       ```cpp
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1.  İçinde **Test Gezgini**, seçin **tümünü Çalıştır** test düzeltilmiş yöntemi ve bir regresyon sunulan henüz emin olun.

   Artık tüm sınamaları geçmesi.

   ![Tüm testler başarılı](../test/media/ute_ult_alltestspass.png)

##  <a name="Refactor_the_code_without_changing_tests"></a> Testleri değiştirmeden kodu yeniden düzenleme

1.  Merkezi hesaplamaya basitleştirmek `SquareRoot` işlevi:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2.  Seçin **tümünü Çalıştır** test UIMap'e yeniden işlenmiş yöntemi ve bir regresyon sunulan henüz emin olun.

    > [!TIP]
    > Kararlı bir dizi iyi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.
    >
    > Diğer değişikliklerden ayrı düzenlemesi tutun.
