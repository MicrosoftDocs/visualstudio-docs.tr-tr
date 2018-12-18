---
title: C++ için Microsoft birim testi çerçevesi ile C / C++ için birim testleri yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: gewarren
manager: douge
ms.openlocfilehash: 180f970f35ed0bb3de70ba3a7b7b47dbe656ddf7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904051"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>C++ için Microsoft Birim Testi Çerçevesi ile C/C++ için Birim Testleri Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da C++ ile yazılmış yönetilmeyen kod için birim testleri oluşturabilirsiniz. Yönetilmeyen kod, bazen yerel kod da adlandırılır.  
  
 Aşağıdaki yordam, başlamanıza yardımcı önemli bilgiler içerir. Sonraki bölümlerde ayrıntılı adımları açıklayan bir kılavuz sağlar.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Yönetilmeyen bir kodu DLL için birim testleri yazma  
  
1.  Kullanım **yerel Test projesi** testleriniz için ayrı bir Visual Studio projesi oluşturmak üzere şablonu.  
  
     Proje bazı örnek test kodunu içerir.  
  
2.  DLL test projesi için erişilebilir hale getirir:  
  
    -   `#include` bir `.h` DLL'nin harici olarak erişilebilen işlevlerin bildirimleri içeren dosya.  
  
         `.h` Dosya, işlev bildirimi ile işaretlenen içermelidir `_declspec(dllimport)`. Alternatif olarak, yöntemlerini DEF dosyası kullanarak dışa aktarabilirsiniz. Daha fazla bilgi için [içeri ve dışarı aktarma](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).  
  
         Birim testlerinizin test edilen DLL öğesinden dışarı aktarılan işlevleri erişebilirsiniz.  
  
    -   DLL projesi test projesinin başvuruları ekleyin:  
  
         İçinde **özellikleri** test projesinde, genişletme **ortak özellikler**, **çerçeve ve başvurular**ve **Başvuru Ekle**.  
  
3.  Test projesinde, test sınıflarında oluşturun ve aşağıdaki şekilde TEST makroları ve onay sınıfı kullanarak test yöntemleri:  
  
    ```cpp  
    #include "stdafx.h"  
    #include <CppUnitTest.h>  
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    TEST_CLASS(TestClassName)  
    {  
    public:  
      TEST_METHOD(TestMethodName)  
      {  
        // Run a function under test here.  
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());  
      }  
    }  
    ```  
  
    -   `Assert` bir test sonucunu doğrulamak için kullanabileceğiniz çeşitli statik işlevler içerir.  
  
    -   `LINE_INFO()` Parametresi isteğe bağlıdır. Durumlarda hiç PDB dosyası olduğunda, hata konumunu belirlemek test Çalıştırıcısı izin verir.  
  
    -   Kurulum ve temizleme test yöntemleri de yazabilirsiniz. Daha fazla bilgi için tanımını açın `TEST_METHOD` makro ve CppUnitTest.h açıklamaları okuma  
  
    -   Test sınıflarında iç içe olamaz.  
  
4.  Test Gezgini testleri çalıştırmak için kullanın:  
  
    1.  Üzerinde **görünümü** menüsünde seçin **diğer Windows**, **Test Gezgini**.  
  
    2.  Visual Studio çözümü oluşturun.  
  
    3.  Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
    4.  Herhangi bir testi Test Gezgini'nde daha ayrıntılı incelemek için:  
  
        1.  Bir hata iletisi ve yığın izlemesi gibi daha fazla ayrıntı görmek için test adı seçin.  
  
        2.  Test adı, test kodu veya hata konumuna gitmek için (örneğin çift tıklayarak) açın.  
  
        3.  Bir test için kısayol menüsünde **hata ayıklama, seçili Test** hata ayıklayıcıda testi çalıştırmak için.  
  
##  <a name="walkthrough"></a> İzlenecek yol: Test Gezgini ile yönetilmeyen DLL geliştirme  
 Kendi DLL geliştirmek için bu kılavuzda uyarlayabilirsiniz. Asıl adımlar aşağıdaki gibidir:  
  
1.  [Yerel Test projesi oluşturma](#unitTestProject). Testler, geliştirmekte olduğunuz DLL ayrı bir projeden de oluşturulur.  
  
2.  [Bir DLL projesi oluşturma](#createDllProject). Bu izlenecek yol, yeni bir DLL oluşturur, ancak mevcut bir DLL sınama yordamını benzer.  
  
3.  [DLL işlevleri testler tarafından görülebilmesi](#coupleProjects).  
  
4.  [Yinelemeli olarak testleri genişletme](#iterate). Kod geliştirme testleri tarafından kılavuzluk edilir, bir "kırmızı-yeşil-düzenleme" döngüsünde öneririz.  
  
5.  [Başarısız olan Testlerde Hata Ayıkla](#debug). Hata ayıklama modunda testleri çalıştırabilirsiniz.  
  
6.  [Testleri değişmeden tutarken yeniden düzenleme](#refactor). Yeniden düzenleme kod yapısını dış davranışını değiştirmeden geliştirme anlamına gelir. Performans, genişletilebilirlik ve kodun okunabilirliğini geliştirmek için bunu yapabilirsiniz. Davranış değiştirilmemesi niyetini olduğu için kodu yeniden düzenleme değişiklik yapma sırasında testleri değiştirmeyin. Testleri sırasında yeniden düzenleme, hata ekleme sağlanmasına yardımcı olur. Bu nedenle bu tür testler yoktu, daha çok daha fazla güvenle değişiklik yapabilirsiniz.  
  
7.  [Kapsamı denetleme](https://msdn.microsoft.com/library/fc8hec9e.aspx). Birim testleri, kodunuzun daha fazla çalışma daha yararlı olur. Kodunuzun hangi parçalarının testler tarafından kullanılmış olan bulabilir.  
  
8.  [Dış kaynaklara birimlerinden yalıtmak](https://msdn.microsoft.com/library/hh549174.aspx). Genellikle, bir DLL, diğer DLL'leri, veritabanları ya da uzak alt sistemleri gibi geliştiriyorsunuz sisteminin diğer bileşenlere bağlıdır. Her birim bağımlılıklarını yalıtımdan test kullanışlıdır. Dış bileşenlerin yavaş çalıştırmak testlerini yapabilirsiniz. Geliştirme sırasında diğer bileşenleri eksik olabilir.  
  
###  <a name="unitTestProject"></a> Yerel birim testi projesi oluşturma  
  
1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
     İletişim kutusunda, **yüklü**, **şablonları**, **Visual C++**, **Test**.  
  
     Seçin **yerel Test projesi** şablonu.  
  
     Bu kılavuzda, test projesi adlı `NativeRooterTest`.  
  
     ![Bir C oluşturma&#43; &#43; birim testi projesi](../test/media/utecpp01.png "UteCpp01")  
  
2.  Yeni projede, inceleme **unittest1.cpp**  
  
     ![Test projesi içeren TEST&#95;sınıfı ve TEST&#95;yöntemi](../test/media/utecpp2.png "UteCpp2")  
  
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
  
    2.  Üzerinde **Test** menüsünde seçin **çalıştırma** , **tüm testleri**.  
  
         Test derlenir ve çalışır.  
  
         Test Gezgini görüntülenir.  
  
         Test altında görünür **başarılı testler**.  
  
         ![Birim Test Gezgini ile bir geçen test](../test/media/utecpp04.png "UteCpp04")  
  
###  <a name="createDllProject"></a> Yönetilmeyen DLL projesi oluşturma  
  
1.  Oluşturma bir **Visual C++** kullanarak proje **Win32 projesi** şablonu.  
  
     Bu izlenecek yolda, proje adı `RootFinder`.  
  
     ![Bir C oluşturma&#43; &#43; Win32 projesi](../test/media/utecpp05.png "UteCpp05")  
  
2.  Seçin **DLL** ve **sembolleri dışarı aktarma** Win32 Uygulama Sihirbazı'nda.  
  
     **Sembolleri dışa aktar** seçeneği, dışa aktarılan bir yöntemi bildirmek için kullanabileceğiniz uygun bir makro oluşturur.  
  
     ![C&#43; &#43; DLL ve sembolleri dışarı aktarmak için Proje Sihirbazı'nı ayarlama](../test/media/utecpp06.png "UteCpp06")  
  
3.  Asıl .h dosyasındaki dışa aktarılan bir işlevin bildirin:  
  
     ![Yeni DLL kod projesi ve .h dosyası API makrolarla](../test/media/utecpp07.png "UteCpp07")  
  
     Bildirimci `__declspec(dllexport)` DLL dışında görünür olmasını ortak ve korunan üyeleri sınıf neden olur. Daha fazla bilgi için [C++ sınıflarında dllimport ve dllexport kullanma](http://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).  
  
4.  Asıl .cpp dosyasında en az bir işlev gövdesi ekleyin:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
###  <a name="coupleProjects"></a> Birkaç DLL projesi için test projesi  
  
1. DLL projesi için test projesinin proje başvurularını ekleyin:  
  
   1.  Test proje özelliklerini açın ve seçin **ortak özellikler**, **çerçeve ve başvurular**.  
  
        ![C&#43; &#43; proje özellikleri &#45; çerçeve ve başvurular](../test/media/utecpp08.png "UteCpp08")  
  
   2.  Seçin **Yeni Başvuru Ekle**.  
  
        İçinde **Başvuru Ekle** iletişim kutusunda, DLL projesi seçip **Ekle**.  
  
        ![C&#43; &#43; proje özellikleri &#45; Yeni Başvuru Ekle](../test/media/utecpp09.png "UteCpp09")  
  
2. Asıl birim test .cpp dosyasında DLL kod .h dosyası şunları içerir:  
  
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
  
    Yeni test, Test Gezgini'nde görünür.  
  
5. Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
    ![Birim Test Gezgini &#45; temel geçirilen Test](../test/media/utecpp10.png "UteCpp10")  
  
   Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.  
  
###  <a name="iterate"></a> Yinelemeli olarak testleri genişletme ve onları geçirin  
  
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
    >  Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.  
    >   
    >  Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.  
  
2.  Çözümü derleyin ve ardından Test Gezgini'nde **tümünü Çalıştır**.  
  
     Yeni test başarısız olur.  
  
     ![RangeTest başarısız](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.  
  
3.  Yeni test geçer, test edilen kod geliştirir:  
  
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
  
4.  Çözümü derleyin ve Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
     Her iki testler başarılı.  
  
     ![Birim Test Gezgini &#45; aralığı geçirilen Test](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    >  Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.  
  
###  <a name="debug"></a> Başarısız bir test hatalarını ayıklama  
  
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
  
     Onaylama başarısız vurgulanır. Hata iletisi, Test Gezgini ayrıntı bölmesinde görünür.  
  
     ![Başarısız NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
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
  
     ![Tüm sınamaları geçmesi](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
>  Paralel test yürütme ile bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, açma ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon küçük") araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.  
  
###  <a name="refactor"></a> Testleri değiştirmeden kodu yeniden düzenleme  
  
1.  SquareRoot işlevi merkezi hesaplamaya kolaylaştırma:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2.  Çözümü derleyin ve seçin **tümünü Çalıştır**, size bir hata oluşturmadığından emin emin olmak için.  
  
    > [!TIP]
    >  İyi bir dizi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.  
    >   
    >  Diğer değişikliklerden ayrı düzenlemesi tutun.  
  
## <a name="next-steps"></a>Sonraki adımlar  
  
-   **Yalıtım.** Çoğu DLL'leri, veritabanları ve diğer DLL'leri gibi başka alt sistemlerin bağlıdır. Bu diğer bileşenler genellikle paralel olarak geliştirilir. Birim testinin diğer bileşenleri henüz kullanılabilir değildir; ancak gerçekleştirilmesine izin vermek için sahte yerine olması veya  
  
-   **Yapı doğrulama testleri.** Belirlenen aralıklarda takımınızın yapı sunucusunda gerçekleştirilen testler olabilir. Bu, birkaç takım üyelerinin iş tümleştirildiğinde hatanın değil sağlar.  
  
-   **İade etme sınar.** Bazı testler her ekip üyesi, kod kaynak denetimine iade etmeden önce gerçekleştirilen zorunlu. Genellikle bu yapı doğrulama testlerini eksiksiz bir alt kümesidir.  
  
     En az bir kod kapsamı düzeyini zorunlu kılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Microsoft.VisualStudio.TestTools.CppUnitTestFramework kullanma](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Yönetilen ve yönetilmeyen kod birlikte çalışabilirliği genel bakış](http://msdn.microsoft.com/library/ms973872.aspx)   
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [İzlenecek yol: Oluşturma ve kullanarak bir dinamik bağlantı kitaplığı (C++)](http://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941)   
 [İçeri ve Dışarı Aktarma](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)



