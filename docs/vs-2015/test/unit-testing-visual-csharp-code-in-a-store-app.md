---
title: Visual C# kod bir Store uygulaması birim testi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: ae41a5a646860526cbc5b3f6e3c04bfbf7612e2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901560"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Visual C# kod bir Store uygulaması birim testi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, Visual C# sınıfı için birim testleri bir Windows Store uygulaması oluşturmanın yollarından biri açıklanır. Rooter sınıfı, belirsiz bellek sınırı teorik, hesaplama bir tahminini verilen bir sayının kare kökünü hesaplayan bir işlevi uygulayarak gösterir. Matematik uygulama ardından eğlenceli bir kullanıcıya göstermek için bu işlevi kullanabilirsiniz matematik ile yapılabilir şeyler.  
  
 Bu konu, birim testi geliştirmede ilk adım olarak kullanma işlemini gösterir. Bu yaklaşım önce test ettiğiniz sistemde belirli bir davranış doğrulayan bir test yöntemi yazın ve ardından testin başarılı olması kod yazacaksınız. Aşağıdaki yordamlar sırasına göre değişiklikler yaparak, bu strateji ilk Yazımdan sonra birim testleri yazma ve test etmek istediğiniz kod tersine çevirebilirsiniz.  
  
 Bu konuda ayrıca tek bir Visual Studio çözümü de ayrı projeler için birim testleri ve test etmek istediğiniz DLL oluşturur. Doğrudan DLL projede birim testleri de içerebilir veya birim testleri ve DLL için ayrı çözümler oluşturabilirsiniz.  
  
> [!NOTE]
>  Visual Studio Community, Kurumsal. ve Professional birim testi için ek özellikler sağlar.  
> 
> - Bir eklenti bağdaştırıcısı Microsoft Test Gezgini için oluşturduğu tüm üçüncü taraf ve açık kaynak birim testi çerçevesini kullanın. Ayrıca, analiz ve testler için kod kapsamı bilgileri görüntüleyebilirsiniz.  
>   -   Her derlemeden sonra testlerinizi çalıştırın.  
>   -   VS Enterprise Microsoft Fakes, testlerinizi, sistem ve üçüncü taraf işlevselliği için test kodu değiştirerek kendi kodlarına odaklanmasını yardımcı olan yönetilen kod için bir yalıtım çerçevesi de içerir.  
> 
>   Daha fazla bilgi için [doğrulama kodunu kullanarak birim testleri tarafından](http://msdn.microsoft.com/library/dd264975.aspx) MSDN Kitaplığı'nda.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Çözüm ve birim testi projesi oluşturma](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Testleri Test Gezgini'nde çalıştırma doğrulayın](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Matematik projeye Rooter sınıfı Ekle](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Birkaç uygulama projesi için test projesi](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Yinelemeli olarak testleri genişletme ve onları geçirin](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Başarısız bir test hatalarını ayıklama](#BKMK_Debug_a_failing_test)  
  
 [Kodu yeniden düzenleyin](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Çözüm ve birim testi projesi oluşturma  
  
1.  Üzerinde **dosya** menüsünde seçin **yeni**ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **yüklü**, ardından **Visual C#** ve **Windows Store**. Ardından **boş uygulama** proje şablonları listesinden.  
  
3.  Projeyi adlandırın `Maths` emin **çözüm için dizin oluştur** seçilir.  
  
4.  Çözüm Gezgini'nde çözüm adı seçin, **Ekle** kısayol menüsünden seçin **yeni proje**.  
  
5.  İçinde **yeni proje** iletişim kutusunda **yüklü**, ardından **Visual C#** ve **Windows Store** . Ardından **birim testi kitaplığı (Windows Store apps)** proje şablonları listesinden.  
  
     ![Birim testi projesi oluşturma](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")  
  
6.  UnitTest1.cs Visual Studio düzenleyicisinde açın.  
  
    ```csharp  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Aşağıdakilere dikkat edin:  
  
    1.  Her bir testi kullanılarak tanımlanmış `[TestMethod]`. Bir test yöntemi, boş değer döndürmelidir ve parametreye sahip olamaz.  
  
    2.  Test yöntemleri ile donatılmış bir sınıf olmalıdır `[TestClass]` özniteliği.  
  
         Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemlerini belirtilmemiş sırayla çağrılır.  
  
    3.  Önce ve sonra her bir modül, sınıf veya yöntemi çağıran özel yöntemi tanımlayabilirsiniz. Daha fazla bilgi için [birim testlerinde Microsoft.VisualStudio.TestTools.UnitTesting üyelerini kullanma](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) MSDN Kitaplığı'nda.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Testleri Test Gezgini'nde çalıştırma doğrulayın  
  
1.  Bazı test kodunda Ekle `TestMethod1` , **UnitTest1.cs** dosyası:  
  
    ```csharp  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Dikkat `Assert` sınıfı yöntemleri test sonuçlarında doğrulamak için kullanabileceğiniz birkaç statik yöntemler sağlar.  
  
2.  Üzerinde **Test** menüsünde seçin **çalıştırma** seçip **tümünü Çalıştır**.  
  
     Test projesi oluşturur ve çalıştırır. Test Gezgini penceresi görünür ve test altında listelenen **başarılı testler**. Pencerenin alt kısmındaki özeti bölmesinde seçilen test hakkında ek ayrıntılar sağlar.  
  
     ![Test Gezgini](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Matematik projeye Rooter sınıfı Ekle  
  
1.  Çözüm Gezgini'nde **matematik** proje adı. Kısayol menüsünden **Ekle**, ardından **sınıfı**.  
  
2.  Sınıf dosyasının adı `Rooter.cs`  
  
3.  Rooter sınıfa aşağıdaki kodu ekleyin **Rooter.cs** dosyası:  
  
    ```csharp  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     `Rooter` Sınıfı Oluşturucu bildirir ve `SqareRoot` estimator yöntemi.  
  
4.  `SqareRoot` Yöntemdir en az bir uygulama yalnızca, test Kurulum temel yapısını test etmek yeterli.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Birkaç uygulama projesi için test projesi  
  
1. Matematik uygulama başvuru RooterTests projeye ekleyin.  
  
   1.  Çözüm Gezgini'nde **RooterTests** proje ve ardından **Başvuru Ekle...**  kısayol menüsünde.  
  
   2.  Üzerinde **Başvuru Ekle - RooterTests** iletişim kutusunda **çözüm** ve **projeleri**. Ardından **matematik** öğesi.  
  
        ![Matematik projeye bir başvuru ekleyin](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")  
  
2. Kullanarak bir ekleme UnitTest1.cs dosyasını deyimi:  
  
   1.  Açık **UnitTest1.cs**.  
  
   2.  Aşağıdaki bu kod ekleme `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` satırı:  
  
       ```csharp  
       using Maths;  
       ```  
  
3. Rooter işlevini kullanan bir test ekleyin. Aşağıdaki kodu ekleyin **UnitTest1.cpp**:  
  
   ```csharp  
   [TestMethod]  
   public void BasicTest()  
   {  
       Maths.Rooter rooter = new Rooter();  
       double expected = 0.0;  
       double actual = rooter.SquareRoot(expected * expected);  
       double tolerance = .001;  
       Assert.AreEqual(expected, actual, tolerance);  
   }  
  
   ```  
  
4. Çözümü oluşturun.  
  
    Yeni test Test Gezgini'nde görünür **çalıştırılmamış testler** düğümü.  
  
5. Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
    ![Temel Test geçirilen](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Yinelemeli olarak testleri genişletme ve onları geçirin  
  
1.  Yeni bir test ekleyin:  
  
    ```csharp  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.  
    >   
    >  Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.  
  
2.  Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
3.  Test başarısız olur.  
  
     ![RangeTest başarısız](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.  
  
4.  Yeni test geçer, test edilen kod geliştirin. Değişiklik `SqareRoot` işlevi **Rooter.cs** bu:  
  
    ```csharp  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  Çözümü derleyin ve Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
     Üç testi şimdi geçirin.  
  
> [!TIP]
>  Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Başarısız bir test hatalarını ayıklama  
  
1. Başka bir test eklemek **UnitTest1.cs**:  
  
   ```csharp  
   // Verify that negative inputs throw an exception.  
   [TestMethod]  
   public void NegativeRangeTest()  
   {  
       string message;  
       Rooter rooter = new Rooter();  
       for (double v = -0.1; v > -3.0; v = v - 0.5)  
       {  
           try  
           {  
               // Should raise an exception:  
               double actual = rooter.SquareRoot(v);  
  
               message = String.Format("No exception for input {0}", v);  
               Assert.Fail(message);  
           }  
           catch (ArgumentOutOfRangeException ex)  
           {  
               continue; // Correct exception.  
           }  
           catch (Exception e)  
           {  
               message = String.Format("Incorrect exception for {0}", v);  
               Assert.Fail(message);  
           }  
       }  
   }  
  
   ```  
  
2. Test Gezgini'nde seçin **tümünü Çalıştır**.  
  
    Test başarısız olur. Test adı, Test Gezgini'nde seçin. Onaylama başarısız vurgulanır. Hata iletisi, Test Gezgini ayrıntı bölmesinde görünür.  
  
    ![Başarısız NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Testin neden başarısız görmek için işlev adım:  
  
   1.  Başında bir kesme noktası ayarlamak `SquareRoot` işlevi.  
  
   2.  Başarısız test kısayol menüsünde **seçilen Testlerde Hata Ayıkla**.  
  
        Kesme noktasında çalıştırma sona erdiğinde, kodda adım adım.  
  
   3.  Özel durumu yakalamak için Rooter yöntemine kod ekleyin:  
  
       ```csharp  
       public double SquareRoot(double x)  
       {  
           if (x < 0.0)  
           {  
               throw new ArgumentOutOfRangeException();  
       }  
  
       ```  
  
   1.  Test Gezgini'nde seçin **tümünü Çalıştır** test düzeltilmiş yöntemi ve bir regresyon sunulan henüz emin olun.  
  
   Artık tüm sınamaları geçmesi.  
  
   ![Tüm sınamaları geçmesi](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Kodu yeniden düzenleyin  
 **Merkezi hesaplamaya SquareRoot işlevi basitleştirin.**  
  
1.  Sonuç uygulamasını değiştirin  
  
    ```csharp  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Seçin **tümünü Çalıştır** test UIMap'e yeniden işlenmiş yöntemi ve bir regresyon sunulan henüz emin olun.  
  
> [!TIP]
>  Kararlı bir dizi iyi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.  
  
 **Yinelenen kod ortadan kaldırmak için test kodu yeniden düzenleyin.**  
  
 Unutmayın `RangeTest` yöntemi sabit kodları kullanılan dayanıklılık değişkenin paydası `Assert` yöntemi. Aynı dayanıklılık hesaplamayı kullanan ek testleri eklemeyi planlıyorsanız, birden fazla konumda sabit kodlanmış bir değer kullanımını hatalarına neden.  
  
1.  Özel bir yöntem Tolerans değeri hesaplamak ve ardından bu yöntem bunun yerine çağrı Unit1Test sınıfına ekleyin.  
  
    ```csharp  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Seçin **tümünü Çalıştır** UIMap'e yeniden işlenmiş yöntemi test ve hata sunulan henüz emin olun.  
  
> [!NOTE]
>  Bir test sınıfı için bir yardımcı yöntem eklemek, eklemeyin `[TestMethod]` özniteliğini yöntemine. Test Gezgini, çalıştırılacak yöntemi kaydetmez.



