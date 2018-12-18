---
title: Visual C# koduna birim testi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 76c20fb987bb1380cb4d3f00e078aac81f26e89f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064860"
---
# <a name="unit-testing-visual-c-code"></a>Visual C# koduna birim testi

Bu makalede bir UWP uygulamasındaki Visual C# sınıfı için birim testleri oluşturma yöntemlerinden biri açıklanır. Rooter sınıfı, belirsiz bellek sınırı teorik, hesaplama bir tahminini verilen bir sayının kare kökünü hesaplayan bir işlevi uygulayarak gösterir. Matematik uygulama ardından eğlenceli bir kullanıcıya göstermek için bu işlevi kullanabilirsiniz matematik ile yapılabilir şeyler.

Bu makalede, birim testi geliştirmede ilk adım olarak kullanma işlemini gösterir. Bu yaklaşım önce test ettiğiniz sistemde belirli bir davranış doğrulayan bir test yöntemi yazın ve ardından testin başarılı olması kod yazacaksınız. Aşağıdaki yordamlar sırasına göre değişiklikler yaparak, bu strateji ilk Yazımdan sonra birim testleri yazma ve test etmek istediğiniz kod tersine çevirebilirsiniz.

Bu makalede ayrıca tek bir Visual Studio çözümü de ayrı projeler için birim testleri ve test etmek istediğiniz DLL oluşturur. Doğrudan DLL projede birim testleri de içerebilir veya birim testleri ve DLL için ayrı çözümler oluşturabilirsiniz.

## <a name="create-the-solution-and-the-unit-test-project"></a>Çözüm ve birim testi projesi oluşturma

1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

2. İçinde **yeni proje** iletişim kutusunda **yüklü** > **Visual C#** ve **Windows Evrensel**. Ardından **boş uygulama** proje şablonları listesinden.

3. Projeyi adlandırın `Maths` emin **çözüm için dizin oluştur** seçilir.

4. İçinde **Çözüm Gezgini**, çözüm adı seçin, **Ekle** kısayol menüsünden seçin **yeni proje**.

5. İçinde **yeni proje** iletişim kutusunda **yüklü**, ardından **Visual C#** ve **Windows Evrensel**. Ardından **birim testi uygulaması (Evrensel Windows)** proje şablonları listesinden.

6. Açık *UnitTest1.cs* Visual Studio düzenleyicisinde.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
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

   - Her bir testi kullanılarak tanımlanmış <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliği. Bir test yöntemi, boş değer döndürmelidir ve parametreye sahip olamaz.

   - Test yöntemleri ile donatılmış bir sınıf olmalıdır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği.

        Testler çalıştırıldığında, her test sınıfının bir örneği oluşturulur. Test yöntemlerini belirtilmemiş sırayla çağrılır.

   - Önce ve sonra her bir modül, sınıf veya yöntemi çağıran özel yöntemi tanımlayabilirsiniz. Daha fazla bilgi için [MSTest framework birim testleri kullanın](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Testleri Test Gezgini'nde çalıştırma doğrulayın

1. Bazı test kodu içinde TestMethod1 eklemek *UnitTest1.cs* dosyası:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Dikkat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfı yöntemleri test sonuçlarında doğrulamak için kullanabileceğiniz birkaç statik yöntemler sağlar.

2. Üzerinde **Test** menüsünde seçin **çalıştırma** seçip **tümünü Çalıştır**.

   Test projesi oluşturur ve çalıştırır. **Test Gezgini** penceresi görünür ve test altında listelenen **başarılı testler**. **Özeti** pencerenin alt kısmındaki bölmesi, seçilen test hakkında ek ayrıntılar sağlar.

   ![Test Gezgini](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Matematik projeye Rooter sınıfı Ekle

1. İçinde **Çözüm Gezgini**, seçin **matematik** proje adı. Kısayol menüsünden **Ekle**, ardından **sınıfı**.

2. Sınıf dosyasının adı *Rooter.cs*.

3. Rooter sınıfa aşağıdaki kodu ekleyin *Rooter.cs* dosyası:

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

   `Rooter` Sınıfı Oluşturucu bildirir ve `SquareRoot` estimator yöntemi.

4. `SquareRoot` Yöntemdir en az bir uygulama yalnızca, test Kurulum temel yapısını test etmek yeterli.

## <a name="couple-the-test-project-to-the-app-project"></a>Birkaç uygulama projesi için test projesi

1. Matematik uygulama başvuru RooterTests projeye ekleyin.

    1. İçinde **Çözüm Gezgini**, seçin **RooterTests** proje ve ardından **Başvuru Ekle** kısayol menüsünde.

    2. İçinde **Başvuru Ekle - RooterTests** iletişim kutusunda **çözüm** ve **projeleri**. Ardından **matematik** öğesi.

        ![Matematik projeye bir başvuru ekleyin](../test/media/ute_cs_windows_addreference.png)

2. Kullanarak bir ekleme deyimi *UnitTest1.cs* dosyası:

    1. Açık *UnitTest1.cs*.

    2. Aşağıdaki bu kod ekleme `using Microsoft.VisualStudio.TestTools.UnitTesting;` satırı:

       ```csharp
       using Maths;
       ```

3. Rooter işlevini kullanan bir test ekleyin. Aşağıdaki kodu ekleyin *UnitTest1.cs*:

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

   Yeni test görünür **Test Gezgini** içinde **çalıştırılmamış testler** düğümü.

5. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

   ![Temel Test geçildi](../test/media/ute_cpp_testexplorer_basictest.png)

Test ve kod projelerini ayarlama sahiptir ve doğrulandı, kod projesinde işlevleri çalıştırmak testlerini çalıştırabilirsiniz. Şimdi gerçek test ve kod yazmaya başlayabilirsiniz.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Yinelemeli olarak testleri genişletme ve onları geçirin

1. Yeni bir test ekleyin:

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
   > Geçmiş olan testleri değiştirmemenizi öneririz. Bunun yerine, yeni test Ekle, kod testin başarılı olması için güncelleştirin ve ardından başka bir test ekleyin ve benzeri.
   >
   > Kullanıcılarınızın gereksinimlerine değiştirdiğinizde, artık doğru testleri devre dışı bırakın. Yeni testler yazmak ve bunları teker teker artımlı aynı şekilde çalışır duruma getirin.

2. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

3. Test başarısız olur.

   ![RangeTest başarısız](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Hemen yazdıktan sonra her testin başarısız olduğunu doğrulayın. Bu, hiçbir zaman başarısız bir test yazma kolay onlardan yardımcı olur.

4. Yeni test geçer, test edilen kod geliştirin. Değişiklik `SquareRoot` işlevi *Rooter.cs* bu:

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

5. Çözümü derleyin ve ardından **Test Gezgini**, seçin **tümünü Çalıştır**.

   Üç testi şimdi geçirin.

> [!TIP]
> Aynı anda testleri bir ekleyerek kod geliştirin. Tüm testler her yinelemeden sonra başarılı olduğundan emin olun.

## <a name="debug-a-failing-test"></a>Başarısız bir test hatalarını ayıklama

1. Başka bir test eklemek *UnitTest1.cs*:

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

2. İçinde **Test Gezgini**, seçin **tümünü Çalıştır**.

   Test başarısız olur. Test adı seçmenize **Test Gezgini**. Onaylama başarısız vurgulanır. Hata iletisi ayrıntı bölmesinde görünür **Test Gezgini**.

   ![NegativeRangeTests başarısız oldu](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Testin neden başarısız görmek için işlev adım:

    1. Başında bir kesme noktası ayarlamak `SquareRoot` işlevi.

    2. Başarısız test kısayol menüsünde **seçilen Testlerde Hata Ayıkla**.

        Kesme noktasında çalıştırma sona erdiğinde, kodda adım adım.

    3. Özel durumu yakalamak için Rooter yöntemine kod ekleyin:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. İçinde **Test Gezgini**, seçin **tümünü Çalıştır** test düzeltilmiş yöntemi ve bir regresyon sunulan henüz emin olun.

Artık tüm sınamaları geçmesi.

![Tüm testler başarılı](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Kodu yeniden düzenleyin

**Merkezi hesaplamaya SquareRoot işlevi basitleştirin.**

1. Sonuç uygulamasını değiştirin

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Seçin **tümünü Çalıştır** test UIMap'e yeniden işlenmiş yöntemi ve bir regresyon sunulan henüz emin olun.

> [!TIP]
> Kararlı bir dizi iyi birim testi kodu değiştirdiğinizde, yeni hatalar oluşturmadığından emin olmanızı sağlar.

**Yinelenen kod ortadan kaldırmak için test kodu yeniden düzenleyin.**

Unutmayın `RangeTest` yöntemi sabit kodları, paydası `tolerance` geçirilir değişkeni <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemi. Aynı dayanıklılık hesaplamayı kullanan ek testleri eklemeyi planlıyorsanız, birden fazla konumda sabit kodlanmış bir değer kullanımını hatalarına neden.

1. Tolerans değeri hesaplamak için Unit1Test sınıfı özel bir yöntem ekleyin ve ardından bunun yerine bu yöntemi çağırın.

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

2. Seçin **tümünü Çalıştır** UIMap'e yeniden işlenmiş yöntemi test ve hata sunulan henüz emin olun.

> [!NOTE]
> Görüntülenmesini istemediğiniz bir test sınıfı için bir yardımcı yöntem eklerseniz **Test Gezgini**, eklemeyin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini yöntemine.