---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 0ca26ca155f14ada97e432aea044166fbe32eee7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067161"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes ile uygulamanın diğer kısımlarını değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olan *saptamalar* veya *dolgular*. Bunlar, testlerinizin denetimi altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Uygulamanın diğer parçaları çalışmıyor olsa bile, saptamalar ve dolgular kodunuzu test etmenize olanak sağlar.

Fakes iki türde olabilir:

-   A [saplama](#get-started-with-stubs) sınıfı aynı arabirimi uygulayan küçük bir yedekle değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

-   A [dolgu](#get-started-with-shims) çalışma zamanında uygulamanızın derlenmiş kodunu değiştirir, böylece bir belirtilen bir yöntemi çağırmak yerine, testin sağladığı dolgu kodunu çalıştırır. Dolgular çağrıları, .NET derlemeleri gibi değiştiremediğiniz Derlemelerle değiştirmek için kullanılabilir.

![Fakes diğer bileşenleri değiştirin](../test/media/fakes-2.png)

**Gereksinimler**

-   Visual Studio Enterprise
-   Bir .NET Framework projesi

> [!NOTE]
> .NET standard projeleri desteklenmez.

## <a name="choose-between-stub-and-shim-types"></a>Saptama ve Dolgu türü arasında seçin
Genelde bu sınıfları aynı anda geliştirip güncelleştirdiğinizden bir Visual Studio projesini bileşen olarak kabul edebilirsiniz. Projenin çözümünüzdeki diğer projelere veya diğer derlemelere yaptığı çağrılar için saptama ve dolgu kullanmayı deneyebilirsiniz.

Genel bir kılavuzluk sağlaması için, Visual Studio çözümünüzdeki çağrılar için saptamaları ve diğer başvurulan derlemelerde çağrılar için dolgu verilerini kullanın. Bunun nedeni kendi çözümünüzde bileşenleri, saptamaların gerektirdiği şekilde arabirimleri tanımlayarak ayırmanızın iyi bir uygulama olmasıdır. Ancak dış derlemeler gibi *System.dll* onun yerine dolguları kullanmalısınız için ayrı arabirim tanımlarıyla genellikle sağlanmaz.

Diğer değerlendirmeler şunlardır:

**Performans.** Çalışma zamanında kodunuzu yeniden yazdıkları için dolgular daha yavaş çalışır. Saptamalarda bu performans düşüklüğü yoktur ve sanal yöntemler kadar hızlı ilerleyebilirler.

**Statik yöntemler, korumalı türler.** Arayüzleri uygulamak için yalnızca saptamalar kullanabilirsiniz. Bu nedenle saptama türleri statik yöntemler, sanal olmayan yöntemler, korumalı sanal yöntemler, korumalı türlerdeki yöntemler gibi yöntemlerle kullanılamaz.

**Dahili türler.** Saptamalar ve dolgular kullanılabilir derleme özniteliğini kullanarak erişilebilir yapılan dahili türlerle birlikte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.

**Özel yöntemler.** Dolgular, bir yöntem imzasındaki tüm türler görünür durumdaysa çağrıları özel yöntemlerle değiştirebilir. Saptamalar yalnızca görünür yöntemlerle değiştirilebilir.

**Arabirimler ve Özet yöntemler.** Saptamalar, test sırasında kullanılabilecek arayüzlerin ve özet yöntemlerin uygulanmalarını sağlar. Metot gövdeleri olmadığından dolgular, arabirimleri ve Özet yöntemleri izlenemez.

Genel olarak saptama türlerini kod temelindeki bağımlılıkları ayırmak için kullanmanızı öneririz. Bunu bileşenleri arayüzlerin arkasına gizleyerek yapabilirsiniz. Dolgu türleri, test edilebilir API sağlamayan üçüncü taraf bileşenlerden ayırmak için kullanılabilir.

##  <a name="get-started-with-stubs"></a>Saptamalar ile çalışmaya başlama
Daha ayrıntılı bir açıklama için bkz. [birim testi için birbirinden uygulamanızın parçalarını yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1.  **Arabirimleri Ekle**

     Saptamalar kullanmak için test etmek istediğiniz kodu, uygulamanızın içindeki diğer bileşende yer alan sınıflara açıkça başvurmayacak şekilde yazmanız gerekir. "Bileşen" ifadesiyle, birlikte geliştirilen ve güncellenen ve tipik olarak tek Visual Studio projesinde yer alan sınıf veya sınıflar kastedilmektedir. Değişkenler ve parametreler, arabirimler kullanılarak bildirilmelidir ve diğer bileşenlerin örnekleri iletilmeli veya fabrika kullanılarak oluşturulmalıdır. Örneğin, StockFeed uygulamadaki farklı bir bileşende bulunan bir sınıfsa bu hatalı olarak değerlendirilir:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Bunun yerine, başka bir bileşen tarafından uygulanabilecek ve bir saptama tarafından test amaçlarıyla uygulanabilecek bir arabirim tanımlayın:

    ```csharp
    public int GetContosoPrice(IStockFeed feed)
    { return feed.GetSharePrice("COOO"); }

    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2.  **Fakes derlemesi Ekle**

    1.  İçinde **Çözüm Gezgini**, test projesinin başvuru listesini genişletin. Visual Basic'te çalışıyorsanız, seçmelisiniz **tüm dosyaları göster** başvuru listesini görmek için.

    2.  Arabirimin (örneğin IStockFeed) tanımlandığı derleme başvurusunu seçin. Bu başvurunun kısayol menüsünde **Fakes derlemesi Ekle**.

    3.  Çözümü yeniden derleyin.

3.  Testlerinizde saptama örnekleri oluşturun ve yöntemleri için kod sağlayın:

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

    Özel sihir parçası burada sınıftır `StubIStockFeed`. Başvurulan derlemedeki her arabirim için saptama sınıfı Microsoft Fakes mekanizması oluşturur. Saplama sınıfının adı ile arabirimin adından türetilir olan "`Fakes.Stub`" ön ek ve parametre türü adları eklenir.

    Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur. Daha fazla bilgi için [birim testi için birbirinden uygulamanızın parçalarını yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

##  <a name="get-started-with-shims"></a>Dolgu ile çalışmaya başlama
(Daha ayrıntılı bir açıklama için bkz. [uygulamanızı birim testi için diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Bileşeniniz için çağrılar içerdiğini varsayın `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Test sırasında dolgu oluşturmak istediğiniz `Now` özelliği, çünkü gerçek sürüm farklı bir değer her çağrıda kullanışsız biçimde döndürür.

Dolgu verileri kullanmak için uygulama kodunu değiştirmeniz veya belirli bir biçimde yazmanız gerekmez.

1.  **Fakes derlemesi Ekle**

     İçinde **Çözüm Gezgini**, birim testi projenizin başvurularını açın ve sahtesini oluşturmak istediğiniz yöntemi içeren derlemenin başvurusunu seçin. Bu örnekte, `DateTime` sınıfı *System.dll*.  Bir Visual Basic projesindeki başvuruları görmek için **tüm dosyaları göster**.

     Seçin **Fakes derlemesi Ekle**.

2.  **ShimsContext içine dolgu ekleyin**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Dolgu sınıfı adları eklenmesiyle `Fakes.Shim` orijinal tür adının. Parametre adları yöntem adına eklenir. (Herhangi bir derleme başvursuna System.Fakes eklemeniz gerekmez.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Bir örnek yöntemi için dolgu kullanmak üzere `AllInstances` tür adı ve yöntem adı arasında:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Başvurmak için hiçbir 'System.IO.Fakes' derleme yok. Ad alanını dolgu oluşturma işlemi tarafından oluşturulur. Ancak, 'using' veya 'Al' her zamanki şekilde kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için [uygulamanızı birim testi için diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="in-this-section"></a>Bu bölümde
 [Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

 [Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

 [Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
