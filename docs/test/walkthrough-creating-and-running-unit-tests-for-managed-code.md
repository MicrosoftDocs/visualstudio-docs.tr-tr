---
title: Yönetilen kod için birim testleri oluşturma ve çalıştırma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 13488619b38f5fd974d793d56f6a8d8cf86f15c1
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469119"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>İzlenecek yol: Yönetilen kod için birim testleri oluşturma ve çalıştırma

Bu makalede, oluşturma işleminde, çalışan, adımları ve bir dizi birim özelleştirme yönetilen kod ve Visual Studio için Microsoft birim test çerçevesini kullanarak testleri **Test Gezgini**. Geliştirilmekte olan bir C# projesi ile başlayın, kodunu, testleri çalıştırmak ve sonuçları inceleyin testleri oluşturun. Daha sonra proje kodunu değiştirin ve testleri yeniden çalıştırın.

> [!NOTE]
> Bu izlenecek yol, yönetilen kod için Microsoft birim testi çerçevesini kullanır. **Test Gezgini** testleri üçüncü parti birim için bağdaştırıcıları olan test çerçevelerini çalıştırabilirsiniz **Test Gezgini**. Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)

Bir komut satırından testleri çalıştırma hakkında daha fazla bilgi için bkz: [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="prerequisites"></a>Önkoşullar

- Banka projesi. Bkz: [birim testleri oluşturmak için örnek proje](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Test etmek için bir proje oluşturun

1. Visual Studio'yu açın.

2. Üzerinde **dosya** menüsünde **yeni** > **proje**.

   **Yeni proje** iletişim kutusu görüntülenir.

3. Altında **yüklü şablonlar**, tıklayın **Visual C#**.

4. Uygulama türleri listesinde tıklayın **sınıf kitaplığı**.

5. İçinde **adı** kutusuna **banka** ve ardından **Tamam**.

   Yeni Banka projesi oluşturulur ve görüntülenen **Çözüm Gezgini** ile *Class1.cs* dosyası Kod Düzenleyicisi'nde açın.

   > [!NOTE]
   > Varsa *Class1.cs* olduğu değil, Kod Düzenleyicisi'nde açın, dosyayı çift tıklatın *Class1.cs* içinde **Çözüm Gezgini** açın.

6. Kaynak kodundan kopyalama [birim testleri oluşturmak için örnek proje](../test/sample-project-for-creating-unit-tests.md)ve özgün içeriklerini *Class1.cs* kopyalanmış kod ile.

7. Dosyayı Farklı Kaydet *BankAccount.cs*.

8. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

Artık banka olarak adlandırılan bir projeniz var. Bu, test etmek için kaynak kodu ve bunu test etmek için Araçlar içerir. BankAccountNS, Banka için ad alanı, ortak sınıf BankAccount, aşağıdaki yordamlarda test edeceğiniz yöntemleri içerir.

Bu makalede, testler banka yöntemine odaklanır. Bir hesaptan para çekildiğinde yöntemi çağrılır. Yöntemin tanımı aşağıda verilmiştir:

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

1. Üzerinde **dosya** menüsünde **Ekle** > **yeni proje**.

2. İçinde **yeni proje** iletişim kutusunda **yüklü**, genişletme **Visual C#** ve ardından **Test**.

3. Şablonlar listesinden **birim testi projesi**.

4. İçinde **adı** kutusuna `BankTests`ve ardından **Tamam**.

   **BankTests** projesi eklenir **banka** çözüm.

5. İçinde **BankTests** projesi, bir başvuru ekleyin **banka** proje.

   İçinde **Çözüm Gezgini**seçin **başvuruları** içinde **BankTests** proje ve ardından **Başvuru Ekle** bağlam menüsünden.

6. İçinde **başvuru Yöneticisi** iletişim kutusunda **çözüm** iade edin **banka** öğesi.

## <a name="create-the-test-class"></a>Test sınıfı oluşturun

Doğrulamak için bir test sınıfı oluşturun `BankAccount` sınıfı. Kullanabileceğiniz *UnitTest1.cs* proje şablonu tarafından oluşturulan dosya, ancak dosyaya verin ve daha açıklayıcı adlar sınıfı. Dosyayı yeniden adlandırarak, tek bir adımda yapabilirsiniz **Çözüm Gezgini**.

### <a name="rename-a-class-file"></a>Bir sınıf dosyasını yeniden adlandırma

İçinde **Çözüm Gezgini**seçin *UnitTest1.cs* BankTests projesindeki dosya. Bağlam menüsünden **Yeniden Adlandır**ve ardından dosyayı yeniden adlandır *BankAccountTests.cs*. Seçin **Evet** kod öğesi için tüm başvuruları yeniden adlandırmak isteyip istemediğinizi soran bir iletişim kutusundaki `UnitTest1` projedeki.

Bu adım için sınıfın adını değiştirir `BankAccountTests`. *BankAccountTests.cs* dosyası artık şu kodu içerir:

```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement-to-the-project-under-test"></a>Kullanarak bir ekleme test altındaki projeye deyimi

Ayrıca bir `using` tam adı kullanmadan test altındaki projeye çağırmak için sınıfa deyimi. Sınıf dosyasının en üstüne ekleyin:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Test sınıfı gereksinimleri

Bir test sınıfı için minimum gereksinimleri şunlardır:

- `[TestClass]` Özniteliği, kod herhangi sınıflar, Test Gezgini'nde de çalıştırmak istediğiniz birim test yöntemlerini içeren Microsoft birim testi çerçevesi ile yönetilen için gereklidir.

- Test Gezgini'nin çalıştırmasını istediğiniz her test yönteminin olmalıdır `[TestMethod]` özniteliği.

Sahip olmadığınız diğer birim testi projesi sınıflarda olabilir `[TestClass]` özniteliği ve diğer yöntemler bulunabilir sahip olmayan test sınıflarında `[TestMethod]` özniteliği. Diğer sınıfları ve yöntemleri test yöntemlerinizde kullanabilirsiniz.

## <a name="create-the-first-test-method"></a>İlk test yöntemini oluştur

Bu yordamda, birim testi davranışını doğrulamak için yöntem yazacaksınız `Debit` yöntemi `BankAccount` sınıfı. `Debit` Yöntemi bu makalede daha önce gösterilmiştir.

Denetlenmesi gereken en az üç davranış vardır:

- Çağırılıyorsa yöntem bir <xref:System.ArgumentOutOfRangeException> borç tutarı bakiyeden büyükse.

- Çağırılıyorsa yöntem bir <xref:System.ArgumentOutOfRangeException> borç tutarını küçükse sıfır.

- Yöntemi, Borç tutarını geçerliyse, hesap bakiyeniz borç tutarını çıkarır.

> [!TIP]
> Varsayılan silebilirsiniz `TestMethod1` yöntemi bu izlenecek yolda kullandığından olmaz.

### <a name="to-create-a-test-method"></a>Bir test yöntemi oluşturmak için

İlk testi, geçerli bir tutarın (diğer bir deyişle, bir hesap bakiyesinden ve sıfırdan küçük) doğru bir tutar hesaptan testimizde doğrular. Aşağıdaki yöntemi ekleyin `BankAccountTests` sınıfı:

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Yöntem oldukça basittir: yeni bir ayarlar `BankAccount` nesnesi bir Başlangıç bakiyesi ve geçerli bir süre sonra çeker. Kullandığı <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> bitiş bakiyesini beklendiği gibi olduğunu doğrulamak için yöntem.

### <a name="test-method-requirements"></a>Test yöntemi gereksinimleri

Bir test yönteminin aşağıdaki gereksinimleri karşılaması gerekir:

- İle donatılmış `[TestMethod]` özniteliği.

- Döndürür `void`.

- Parametrelere sahip olamaz.

## <a name="build-and-run-the-test"></a>Derleme ve test çalıştırma

1. Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

   Herhangi bir hata varsa **Test Gezgini** görünür **Not** listelenen **çalıştırılmamış testler** grubu.

   > [!TIP]
   > Varsa **Test Gezgini** başarılı bir oluşturmadan sonra görünmüyorsa, şunu seçin **Test** menüde ardından **Windows**ve ardından **TestGezgini**.

2. Seçin **tümünü Çalıştır** testi çalıştırmak için. Test çalışırken pencerenin en üstündeki durum çubuğunda bir animasyon görünür. Testler başarısız olursa test çalışmasının sonunda, tüm test yöntemleri geçerse yeşil veya Kırmızı çubuk kapatır.

3. Bu durumda, test başarısız olur. Test yöntemi taşınır **başarısız testler** grubu. Yöntemini seçin **Test Gezgini** pencerenin alt kısmındaki ayrıntılarını görüntülemek için.

## <a name="fix-your-code-and-rerun-your-tests"></a>Kodunuzu düzeltin ve testlerinizi yeniden çalıştırın

### <a name="analyze-the-test-results"></a>Test sonuçlarını çözümleme

Test sonucu hatayı açıklayan bir ileti içerir. İçin `AreEqual` yöntemi, bir ileti görüntüler beklenenle ( **beklenen\<*değer* >**  parametresi) ve hangi gerçekten alındı ( **Gerçek\<*değer* >** parametresi). Azaltmak için Bakiye bekleniyordu ancak bunun yerine, mevzuatı miktarına göre artar.

Birim testi bir hata ortaya çıkardı: mevzuatı miktarı *eklenen* olmalıydı hesap bakiyesine *çıkartılır*.

### <a name="correct-the-bug"></a>Hatayı düzeltin

Hatayı düzeltmek için satırı değiştirin:

```csharp
m_balance += amount;
```

İle:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Testi yeniden çalıştırın

İçinde **Test Gezgini**, seçin **tümünü Çalıştır** ve testi yeniden çalıştırın. Test başarılı oldu ve test taşınır belirtmek için kırmızı/yeşil çubuk yeşile **başarılı testler** grubu.

## <a name="use-unit-tests-to-improve-your-code"></a>Kodunuzu geliştirmek için birim testleri kullanın

Bu bölümde, analiz, birim testi geliştirmenin ve yeniden düzenleme düzenlemenin yinelemeli işleminin üretim kodunuzu daha sağlam ve verimli hale getirmek nasıl yardımcı olabileceğini açıklar.

### <a name="analyze-the-issues"></a>Sorunları Çözümle

Geçerli bir süre içinde doğru çıkarılır onaylamak için bir test yöntemi oluşturduğunuz `Debit` yöntemi. Şimdi, çağırılıyorsa yöntem doğrulayın bir <xref:System.ArgumentOutOfRangeException> borç tutarını geçerli olduğunda:

- Bakiye büyüktür veya
- sıfırdan küçük.

### <a name="create-the-test-methods"></a>Test yöntemleri oluşturun

Borç tutarını olduğunda doğru davranış sıfırdan doğrulamak için bir test yöntemi oluşturun:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Kullanım <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> doğru özel durumun oluşturulmasını onaylamak için özniteliği. Öznitelik, testin başarısız olmasına neden olan bir <xref:System.ArgumentOutOfRangeException> oluşturulur. Daha fazla genel oluşturmasına, test altındaki yöntemi geçici olarak değiştirirseniz <xref:System.ApplicationException> borç tutarını küçüktür, sıfır test düzgün şekilde davranan&mdash;diğer bir deyişle, işlem başarısız olur.

Çekilen miktarın bakiyeden büyük olduğunu test etmek için aşağıdaki adımları uygulayın:

1. Adlı yeni bir test yöntemi oluşturun `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Kopyalama yöntemi gövdesinden `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` yeni yönteme.

3. Ayarlama `debitAmount` bakiyeden büyük bir sayı.

### <a name="run-the-tests"></a>Testleri çalıştırın

İki test yöntemlerini çalıştıran, testler doğru bir şekilde çalıştığını gösterir.

### <a name="continue-the-analysis"></a>Çözümlemeye devam edin

Bununla birlikte, son iki test yöntemi ayrıca vericidir. Ya da test çalıştırdığınızda, test altındaki yöntemin içindeki hangi koşulun Exception'a olamazsınız. Bir negatif borç tutarını veya bakiyeden büyük bir miktarını, iki koşul ayrım yapma, bazı şekilde testlerinde güveninizi artırın.

Test altındaki yöntemi yeniden bakın ve her iki koşullu deyimin kullandığına dikkat edin bir `ArgumentOutOfRangeException` yalnızca oluşturucu bağımsız değişken olarak bir parametre adını alır:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Çok daha zengin bilgi raporlarının bir oluşturucu kullanabilirsiniz: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> adını bağımsız değişken, bağımsız değişken değeri ve kullanıcı tanımlı bir ileti içerir. Bu oluşturucuyu kullanarak test altındaki yöntemi yeniden düzenleyebilirsiniz. Daha da iyi genel olarak kullanılabilen tür üyelerini hataları belirlemek için kullanabilirsiniz.

### <a name="refactor-the-code-under-test"></a>Test altındaki kodu yeniden düzenleyin

İlk olarak, sınıf kapsamındaki hata iletileri için iki sabiti tanımlayın. Bu sınıf testten BankAccount yerleştirin:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ardından, iki koşullu ifadeler değiştirin `Debit` yöntemi:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Test yöntemlerini yeniden düzenleme

Kaldırma `ExpectedException` test metodu özniteliği ve bunun yerine, oluşan özel durumları yakalamalı ve onun ilişkili ileti doğrulayın. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Yöntemi, iki dizeyi karşılaştırın olanağı sağlar.

Şimdi, `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` şuna benzeyebilir:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Değişiyorsa, yeniden yaz ve yeniden Çözümle

Test altındaki yöntemin içindeki bir hata varsa varsayar ve `Debit` yöntemi bile throw değil bir <xref:System.ArgumentOutOfRangeException>, nevermind doğru iletiyi özel durumu ile çıktı. Şu anda test yöntemi, bu durumda işlemiyor. Varsa `debitAmount` değeri geçerlidir (diğer bir deyişle, değerinden Bakiye ama sıfırdan büyükse), böylece onay asla harekete hiçbir özel durum yakalandı. Henüz test yöntemi geçirilir. Test yöntemi özel durum oluşturmazsa başarısız istediğinden bu iyi değildir.

Bu, test yönteminde bir hatadır. Sorunu çözmek için ekleme bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> nerede hiçbir özel durum durumu işlemek için test yönteminin sonunda onay.

Ancak sınama gösterir, test artık *başarısız* doğru özel durum yakalandığında. `catch` Bloğu özel durumu yakalar, ancak yöntemi yürütmeye devam eder ve yeni başarısız <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> onay. Bu sorunu çözmek için ekleme bir `return` deyiminden sonra `StringAssert` içinde `catch` blok. Testi yeniden çalıştırmak bu sorunu düzelttik onaylar. Son sürümü `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` şöyle görünür:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Test kodu yapılan iyileştirmeler, daha sağlam ve bilgilendirici test yöntemlerimiz olmasını sağladı. Ancak daha da önemlisi, test edilen kod'bunlar da gelişmiştir.
