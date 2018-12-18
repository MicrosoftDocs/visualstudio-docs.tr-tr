---
title: Test Gezgini ile test güdümlü geliştirme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3303f45006fd0f85d2e11434043091d3f72b469e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062916"
---
# <a name="quickstart-test-driven-development-with-test-explorer"></a>Hızlı Başlangıç: temelli geliştirme, Test Gezgini ile Test

Kodunuz pek çok aşama aşama geliştirme düzgün çalışmasını tutmaya yardımcı olmak için birim testleri oluşturmanızı öneririz. Bazı üçüncü taraflar tarafından geliştirilen dahil olmak üzere birim testleri yazmak için kullanabileceğiniz birkaç çerçeve vardır. Bazı test çerçeveleri, farklı dillerde veya platformlarda test için özel hazırlanmıştır. Test Gezgini bu çerçevelerin herhangi birinde yapılan birim testleri için tek bir arabirim sağlar. En sık kullanılan çerçeveler için bağdaştırıcılar bulunmaktadır ve diğer çerçeveler için kendi bağdaştırıcılarınızı yazabilirsiniz.

 Test Gezgini Visual Studio'nun önceki sürümlerinde bulunan test pencerelerinin yerini almıştır. Yararları şunlardır:

-   .NET, yönetilmeyen kod, veritabanı ve diğer tür testleri tek bir arabirim kullanarak çalıştırın.

-   Kullanım birim test framework NUnit gibi tercih ettiğiniz veya MSTest çerçeveleri.

-   Gereksinim duyduğunuz tüm bilgileri tek bir pencerede bakın.

## <a name="use-test-explorer"></a>Test Gezgini'ni kullanın
 ![Birim Test Gezgini gösterme tümünü Çalıştır düğmesi](../test/media/unittestexplorer-beta-.png)

### <a name="to-run-unit-tests-by-using-test-explorer"></a>Test Gezgini'ni kullanarak birim testlerini çalıştırmak için

1. Tercih ettiğiniz test çerçevelerini kullanan birim testleri oluşturun.

    Örneğin, bir test oluşturmak için MSTest Framework'ü kullanır:

   1.  Bir test projesi oluşturun.

        İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** veya **Visual C++** ve ardından **Test**.

        Seçin **birim testi projesi**.

   2.  Her birim testini bir yöntem gibi yazın. Her test yönteminin önüne `[TestMethod]` özniteliği.

2. Bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, paralel test yürütme ile Aç ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

3. Menü çubuğunda, **Test** > **birim testlerini Çalıştır** > **tüm testleri**.

    Çözüm derlenir ve testler.

    Test Gezgini açılır ve sonuçları özetini görüntüler.

   **Testlerin tam bir listesini görmek için:** Seç **Tümünü Göster** herhangi bir kategoride.

   **Bir test sonucunun ayrıntılarını görmek için:** , Ayrıntılar bölmesinde özel durum iletileri gibi ayrıntıları görüntülemek için Test Gezgini'nde testi seçin.

   **Bir testin koduna gitmek için:** Test Gezgini'nde teste çift tıklayın ya da seçin **testi Aç** kısayol menüsünde.

   **Bir testte hata ayıklamak için:** bir veya daha fazla testin kısayol menüsünü açın ve ardından **seçilen Testlerde Hata Ayıkla**.

> [!IMPORTANT]
> Görüntülenen sonuçlar en son çalıştırılanlar içindir. Renkli sonuç çubuğu, yalnızca çalışan testlerin sonuçlarını gösterir. Örneğin, birkaç testi çalıştırırsanız ve bunlardan bazıları başarısız ve sonra da sadece başarılı olan testleri çalıştırın, ardından sonuçlar çubuğunun tamamı yeşil olur.


> [!NOTE]
> Hiçbir test görünmüyorsa, Test Gezgini'ni kullandığınız test çerçevesine bağlanmak için bir bağdaştırıcı yüklediğinizden emin olun. Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md).


##  <a name="walkthrough-using-unit-tests-to-develop-a-method"></a>İzlenecek yol: birim testlerini bir yöntemi geliştirmek için kullanma.
 Bu kılavuzda Microsoft birim testi çerçevesini kullanarak C# içinde test edilmiş bir yöntem geliştirmeyi göstermektedir. Bunu diğer dillere ve NUnit gibi diğer test çerçevelerini kullanmak için kolayca uyarlayabilirsiniz. Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md).

### <a name="create-the-test-and-method"></a>Testi ve yöntemi oluşturma

1. Bir Visual C# sınıf kitaplığı projesi oluşturun. Bu proje, teslim etmek istediğimiz kodu içerecek. Bu örnekte, adlı `MyMath`.

2. Bir Test projesi oluşturun.

   -   İçinde **yeni proje** iletişim kutusunda seçin **Visual C#** > **Test** seçip **birim testi projesi**.

        ![Yeni kod ve test projeleri](../test/media/unittestexplorerwalk1.png)

3. Temel bir test yöntemi yazın. Belirli bir giriş için elde edilen sonucu doğrulayın:

   ```csharp

   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult,
         delta: expectedResult / 100);
   }
   ```

4. Yöntemi testten oluşturun.

   1.  İmleci üzerine getirin `Rooter`, kısayol menüsünden seçin **Oluştur** > **yeni türü**.

   2.  İçinde **yeni tür Oluştur** iletişim kutusu, kümesi **proje** sınıf kitaplığı projesi. Bu örnekte olduğu `MyMath`.

   3.  İmleci üzerine getirin `SquareRoot`, kısayol menüsünden seçin **Oluştur** > **metot taslağı**.

5. Birim testini çalıştırın.

   1.  Üzerinde **Test** menüsünde seçin **birim testlerini Çalıştır** > **tüm testleri**.

        Çözüm derlenir ve çalışır.

        Test Gezgini açılır ve sonuçları görüntüler.

        Test altında görünür **başarısız testler**.

6. Testin adını seçin.

    Testin ayrıntıları Test Gezgini'nin alt bölümünde görünür.

7. Altındaki öğeleri seçin **yığın izlemesi** testin başarısız olduğu görmek için.

   ![Birim Test Gezgini başarısız gösteren test edin.](../test/media/unittestexplorerwalkthrough2.png)

   Bu noktada, test ve değiştirecek ve böylece test başarılı bir saplama oluşturdunuz.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Her değişiklikten sonra tüm sınamalardan başarılı olun

1.  İçinde *MyMath\Rooter.cs*, kodunu geliştirin `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2.  Test Gezgini'nde seçin **tümünü Çalıştır**.

     Kod derlenir ve test çalışır.

     Test başarılı olur.

     ![Birim Test Gezgini'nde testi geçiyor gösteriliyor.](../test/media/unittestexplorerwalkthrough3.png)

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Giriş aralığını genişletmek için testler ekleme

1.  Kodunuzun her durumda çalıştığından emin olmak için daha geniş bir girdi değerleri aralığını deneyen testler ekleyin.

    > [!TIP]
    > Geçen var olan testlerden geçilenleri değiştirmekten kaçının. Bunun yerine yeni testler ekleyin. Varolan testleri yalnızca kullanıcı gereksinimleri değiştiğinde değiştirin. Bu ilke, kod genişletmeye çalışırken mevcut işlevselliği kaybetmemenizi sağlamaya yardımcı olur.

     Test sınıfınızda, bir girdi değerleri aralığını çalıştığında şu test ekleyin:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Try a range of values:
      for (double expectedResult = 1e-8;
          expectedResult < 1e+8;
          expectedResult = expectedResult * 3.2)
      {
        RooterOneValue(rooter, expectedResult);
      }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
      double input = expectedResult * expectedResult;
      double actualResult = rooter.SquareRoot(input);
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 1000);
    }
    ```

2.  Test Gezgini'nde seçin **tümünü Çalıştır**.

     İlk test başarılı olsa da yeni test başarısız olur.

     Hata noktasını bulmak için başarısız olan testi seçin ve ardından, Test Gezgini'nin alt bölümünde üst öğesi seçin **yığın izlemesi**.

3.  Neyin yanlış olabileceğini görmek için test altındaki yöntemi inceleyin. İçinde `MyMath.Rooter` sınıfında, kodu yeniden yazın:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4.  Test Gezgini'nde seçin **tümünü Çalıştır**.

     Şimdi iki test geçirin.

#### <a name="add-tests-for-exceptional-cases"></a>Olağanüstü durumlar için testler ekleme

1.  Negatif girişler için bir test ekleyin:

    ```csharp
    [TestMethod]
     public void RooterTestNegativeInputx()
     {
         Rooter rooter = new Rooter();
         try
         {
             rooter.SquareRoot(-10);
         }
         catch (ArgumentOutOfRangeException e)
         {
             return;
         }
         Assert.Fail();
     }
    ```

2.  Test Gezgini'nde seçin **tümünü Çalıştır**.

     Yöntem testte döngüye girer ve el ile iptal edilmelidir.

3.  Seçin **iptal**.

     Test 10 saniye sonra durur.

4.  Yöntem kodunu düzeltin:

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5.  Test Gezgini'nde seçin **tümünü Çalıştır**.

     Tüm testler geçer.

#### <a name="refactor-without-changing-tests"></a>Testleri değiştirmeden yeniden düzenleme

1.  Kodu basitleştirin, ancak testleri değiştirmeyin.

    > [!TIP]
    > A *yeniden düzenleme* daha iyi kod yapmak veya kodu anlamayı kolaylaştırmak için hedeflenen bir değişikliktir. Kod davranışını değiştirmek üzere tasarlanmamıştır ve bu nedenle testler değiştirilmez.
    >
    > Yeniden düzenleme adımları ayrı ayrı işlevselliği genişleten adımlardan gerçekleştirmenizi öneririz. Testlerin değiştirmeden tutmak, yanlışlıkla hataları yeniden düzenleme sırasında oluşturmadığından emin olmanızı sağlar.

    ```csharp
    public class Rooter
    {
      public double SquareRoot(double input)
      {
        if (input <= 0.0)
        {
          throw new ArgumentOutOfRangeException();
        }
        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
          previousResult = result;
          result = (result + input / result) / 2;
          //was: result = result - (result * result - input) / (2*result);
        }
        return result;
      }
    }
    ```

2.  Seçin **çalıştırması**.

     Tüm testler hala başarılı.

     ![Birim Test Gezgini 3 geçen testler gösteriliyor.](../test/media/unittestexplorerwalkthrough4.png)
