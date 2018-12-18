---
title: 'İzlenecek yol: Oluşturma ve çalıştırma için birim testleri yönetilen kodu | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50d8190f386a4923fd05cbfaec137791bd9f2b5a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874507"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>İzlenecek yol: Yönetilen Kod için Birim Testleri Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol oluşturma, çalıştırma ve yönetilen kod ve Visual Studio Test Gezgini'yle için Microsoft birim testi çerçevesini kullanarak birim testleri bir dizi özelleştirme size adım adım anlatır. Geliştirilmekte olan bir C# projesi ile başlayın, kodunu, testleri çalıştırmak ve sonuçları inceleyin testleri oluşturun. Daha sonra proje kodunu değiştirin ve testi yeniden çalıştırın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
 [İzlenecek yol hazırla](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Birim testi projesi oluşturma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Test sınıfı oluşturun](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
- [Test sınıfı gereksinimleri](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
  [İlk test yöntemini oluştur](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
- [Test yöntemi gereksinimleri](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
  [Derleme ve test çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
  [Kodunuzu düzeltin ve testlerinizi yeniden çalıştırın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
  [Kodunuzu geliştirmek için birim testleri kullanın](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  Bu izlenecek yol, yönetilen kod için Microsoft birim testi çerçevesini kullanır. Test Gezgini testleri Test Gezgini için bağdaştırıcıları olan test çerçevelerini üçüncü parti birim çalıştırabilirsiniz. Daha fazla bilgi için [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)  
  
> [!NOTE]
>  Bir komut satırından testleri çalıştırma hakkında daha fazla bilgi için bkz: [izlenecek yol: komut satırı test yardımcı programını kullanarak](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Banka projesi. Bkz: [birim testleri oluşturmak için proje örnek](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> İzlenecek yol hazırla  
  
1. Visual Studio'yu açın.  
  
2. Üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
    **Yeni proje** iletişim kutusu görüntülenir.  
  
3. Altında **yüklü şablonlar**, tıklayın **Visual C#**.  
  
4. Uygulama türleri listesinde tıklayın **sınıf kitaplığı**.  
  
5. İçinde **adı** kutusuna `Bank` ve ardından **Tamam**.  
  
   > [!NOTE]
   >  "Banka" zaten kullanılıyorsa proje için başka bir ad seçin.  
  
    Yeni Banka projesi oluşturulur ve Çözüm Gezgini'nde Class1.cs dosyası Kod Düzenleyicisi'nde görüntülenir.  
  
   > [!NOTE]
   >  Class1.cs dosyası Kod Düzenleyicisi'nde açık değilse, açmak için Çözüm Gezgini'nde Class1.cs dosyasını çift tıklayın.  
  
6. Kaynak kodundan kopyalama [birim testleri oluşturmak için örnek proje](../test/sample-project-for-creating-unit-tests.md).  
  
7. Orijinal Class1.cs içeriğini koddan değiştirin [birim testleri oluşturmak için örnek proje](../test/sample-project-for-creating-unit-tests.md).  
  
8. Dosyayı BankAccount.cs olarak kaydedin.  
  
9. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
   Artık banka olarak adlandırılan bir projeniz var. Bu, test etmek için kaynak kodu ve bunu test etmek için Araçlar içerir. Banka için ad alanı **BankAccountNS**, genel sınıfını içeren **BankAccount**, aşağıdaki yordamlarda test edeceğiniz yöntemleri.  
  
   Bu hızlı başlangıçta odaklanıyoruz `Debit` yöntemi. Para çekildiğinde banka yöntem çağrılır bir hesap ve aşağıdaki kodu içerir:  
  
```csharp  
// method under test  
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
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Bir birim testi projesi oluşturma  
 **Önkoşul**: yordamdaki adımları [Yönergeyi Hazırla](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde seçin **Ekle**ve ardından **yeni proje...** .  
  
2.  Yeni Proje iletişim kutusunda Genişlet **yüklü**, genişletme **Visual C#** ve ardından **Test**.  
  
3.  Şablonlar listesinden **birim testi projesi**.  
  
4.  İçinde **adı** kutusuna BankTest girin ve ardından **Tamam**.  
  
     **BankTests** projesi eklenir **banka** çözüm.  
  
5.  İçinde **BankTests** projesi, bir başvuru ekleyin **banka** çözüm.  
  
     Çözüm Gezgini'nde seçin **başvuruları** içinde **BankTests** proje ve ardından **Başvuru Ekle...**  bağlam menüsünden.  
  
6.  Başvuru Yöneticisi iletişim kutusunda Genişlet **çözüm** iade edin **banka** öğesi.  
  
##  <a name="BKMK_Create_the_test_class"></a> Test sınıfı oluşturun  
 Doğrulamak için bir test sınıfına ihtiyacımız `BankAccount` sınıfı. Proje şablonu tarafından oluşturulan Unittest1.cs'yi kullanabiliriz, ancak dosyaya verin ve daha açıklayıcı adlar vermeliyiz. Tek bir adımda Çözüm Gezgini'nde dosyayı yeniden adlandırarak yapabiliriz.  
  
 **Bir sınıf dosyasını yeniden adlandırma**  
  
 Çözüm Gezgini içinde BankTests projesindeki UnitTest1.cs dosyasını seçin. Bağlam menüsünden **Yeniden Adlandır**ve ardından dosyayı BankAccountTests.cs olarak yeniden adlandırın. Seçin **Evet** 'UnitTest1' kod öğesi için projedeki tüm başvuruları yeniden adlandırmak isteyip istemediğinizi soran bir iletişim kutusundaki. Bu adım için sınıfın adını değiştirir `BankAccountTest`.  
  
 BankAccountTests.cs dosyası artık şu kodu içerir:  
  
```csharp  
// unit test code  
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
  
 **Kullanarak bir ekleme test altındaki projeye deyimi**  
  
 Biz kullanarak bir ekleyebilirsiniz tam adı kullanmadan test altındaki projeye çağırmak için bize sınıfa deyimi. Sınıf dosyasının en üstüne ekleyin:  
  
```csharp  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Test sınıfı gereksinimleri  
 Bir test sınıfı için en düşük gereksinimler aşağıda verilmiştir:  
  
- `[TestClass]` Özniteliği, kod herhangi sınıflar, Test Gezgini'nde de çalıştırmak istediğiniz birim test yöntemlerini içeren Microsoft birim testi çerçevesi ile yönetilen için gereklidir.  
  
- Test Gezgini'nin çalıştırmasını istediğiniz her test yönteminin olmalıdır `[TestMethod]`özniteliği.  
  
  Sahip olmadığınız diğer birim testi projesi sınıflarda olabilir `[TestClass]` özniteliği ve diğer yöntemler bulunabilir sahip olmayan test sınıflarında `[TestMethod]` özniteliği. Diğer sınıfları ve yöntemleri test yöntemlerinizde kullanabilirsiniz.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> İlk test yöntemini oluştur  
 Bu yordamda, biz birim testi davranışını doğrulamak için yöntem yazacak `Debit` yöntemi `BankAccount` sınıfı. Yöntem yukarıda listelenmiştir.  
  
 Test altındaki yöntemi çözümleyerek, denetlenmesi gereken en az üç davranış olduğu belirleriz:  
  
1. Çağırılıyorsa yöntem bir [üretiliyor] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->) borç tutarı bakiyeden büyükse.  
  
2. Ayrıca `ArgumentOutOfRangeException` borç tutarını küçükse sıfır.  
  
3. Eğer 1 denetimlerinde.) ve 2.) maddelerindeki yöntem hesap bakiyesini tutardan çıkarır.  
  
   İlk testimizde, hesaptan geçerli bir tutarın (birisi hesap bakiyesinden daha az olan ve sıfırdan büyük) doğru bir tutar testimizde doğrulayın.  
  
#### <a name="to-create-a-test-method"></a>Bir test yöntemi oluşturmak için  
  
1. Kullanarak bir ekleme `BankAccountNS;` BankAccountTests.cs dosyasına deyimi.  
  
2. Aşağıdaki yöntemi ekleyin `BankAccountTests` sınıfı:  
  
   ```csharp  
   // unit test code  
   [TestMethod]  
   public void Debit_WithValidAmount_UpdatesBalance()  
   {  
       // arrange  
       double beginningBalance = 11.99;  
       double debitAmount = 4.55;  
       double expected = 7.44;  
       BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
       // act  
       account.Debit(debitAmount);  
  
       // assert  
       double actual = account.Balance;  
       Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
   }  
   ```  
  
   Yöntem oldukça basittir. Yeni bir ayarladığımız `BankAccount` nesnesi bir Başlangıç bakiyesi ve geçerli bir süre sonra geri alma. Yönetilen kod için Microsoft birim test çerçevesi kullandığımız <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> yöntemi, beklediğimiz bitiş bakiyesini olduğundan emin olun.  
  
###  <a name="BKMK_Test_method_requirements"></a> Test yöntemi gereksinimleri  
 Bir test yönteminin aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   Yöntem ile belirtilmiş olmalıdır `[TestMethod]` özniteliği.  
  
-   Yöntem döndürmelidir `void`.  
  
-   Yöntemin parametreleri olamaz.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Derleme ve test çalıştırma  
  
#### <a name="to-build-and-run-the-test"></a>Derleme ve test çalıştırmak için  
  
1.  Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.  
  
     Herhangi bir hata varsa ile birlikte UnitTestExplorer penceresi görünür **Not** listelenen **çalıştırılmamış testler** grubu. Test Explorer başarılı bir oluşturmadan sonra görünmüyorsa seçin **Test** menüde ardından **Windows**ve ardından **Test Gezgini**.  
  
2.  Seçin **tümünü Çalıştır** testi çalıştırmak için. Durum çubuğu test çalışırken pencerenin en üstünde bir animasyon görünür. Testler başarısız olursa test çalışmasının sonunda, tüm test yöntemleri geçerse yeşil veya Kırmızı çubuk kapatır.  
  
3.  Bu durumda, test başarısızdır. Test yöntemi taşınır **başarısız testler**. Grup. Pencerenin alt kısmındaki ayrıntılarını görüntülemek için Test Gezgini'nde yöntemi seçin.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Kodunuzu düzeltin ve testlerinizi yeniden çalıştırın  
 **Test sonuçlarını çözümleme**  
  
 Test sonucu hatayı açıklayan bir ileti içerir. İçin `AreEquals` yöntemi iletiyi görüntüler, ne bekleniyordu ((<strong>beklenen\<*XXX*></strong>parametresi) ve hangi gerçekten alındı ( **Gerçek\<*YYY* >** parametresi). Biz başlangıç bakiyesinden azalmasını bekliyorduk, ancak bunun yerine artırmıştır oranda arttı.  
  
 Debit kodunun, birim testi hata bulma konusunda başarılı olduğunu gösterir. Çekilen miktarın azaltılması, gerektiğinde hesap bakiyesine eklendi.  
  
 **Hatayı düzeltin**  
  
 Hatayı düzeltmek için basitçe satırı değiştirin  
  
```csharp  
m_balance += amount;  
```  
  
 örneklerini şununla değiştirin:  
  
```csharp  
m_balance -= amount;  
```  
  
 **Testi yeniden çalıştırın**  
  
 Test Gezgini'nde seçin **tümünü Çalıştır** ve testi yeniden çalıştırın. Kırmızı/yeşil çubuk yeşile döner ve test taşınır **başarılı testler** grubu.  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Kodunuzu geliştirmek için birim testleri kullanın  
 Bu bölümde, analiz, birim testi geliştirmenin ve yeniden düzenleme düzenlemenin yinelemeli işleminin üretim kodunuzu daha sağlam ve verimli hale getirmek nasıl yardımcı olabileceğini açıklar.  
  
 **Sorunları Çözümle**  
  
 Onaylamak için bir test yöntemi oluşturulduktan sonra geçerli bir tutarın doğru bir şekilde düşürüldüğünü `Debit` yöntemi, biz kapatabilir kalan durumlara bizim orijinal çözümlememizdeki içinde:  
  
1. Çağırılıyorsa yöntem bir `ArgumentOutOfRangeException` borç tutarı bakiyeden büyükse.  
  
2. Ayrıca `ArgumentOutOfRangeException` borç tutarını küçükse sıfır.  
  
   **Test yöntemleri oluşturun**  
  
   Bu sorunları ele almak için bir test yöntemi oluşturmaya bir ilk denemesi umut verici görünüyor:  
  
```csharp  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Kullandığımız <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> doğru özel durumun oluşturulmasını onaylamak için özniteliği. Öznitelik, testin başarısız olmasına neden olan bir `ArgumentOutOfRangeException` oluşturulur. Her iki pozitif ve negatif bir testi çalıştırmadan `debitAmount` değerleri ve geçici olarak bir genel oluşturmasına, test altındaki yöntemi değiştirme <xref:System.ApplicationException> zaman tutarı sıfırdan küçüktür, doğru davrandığını gösterecek. Çekilen miktarın bakiyeden büyük olduğunu test etmek için tüm yapmanız gereken şöyledir:  
  
1. Adlı yeni bir test yöntemi oluşturun `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2. Kopyalama yöntemi gövdesinden `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` yeni yönteme.  
  
3. Ayarlama `debitAmount` bakiyeden büyük bir sayı.  
  
   **Testleri çalıştırın**  
  
   İçin farklı değerlerle iki yöntemi çalıştırmak `debitAmount` testleri yeterince bizim kalan durumlarla işlendiğini göstermektedir. Çalışan üç testi bizim orijinal çözümlememizdeki tüm durumlarda doğru şekilde ele alındığını doğrulayın.  
  
   **Çözümlemeye devam edin**  
  
   Bununla birlikte, son iki test yöntemi ayrıca yorucudur. Şu testler çalıştırılırken test altındaki kodun hangi koşulda oluşturur belirli olamaz. Bazı yolu iki koşul farklılaştırılması yardımcı olacaktır. Olarak düşünme hakkında daha fazla sorun, hangi koşulun ihlâl edildiğini bilmenin bizim güvenle testlerinde artacaktır belirgin olur. Bu bilgiler, ayrıca çok büyük olasılıkla test altındaki yöntemi tarafından oluştuğunda özel durumu işleyen üretim mekanizmasına yardımcı olacaktır. Yöntem tüm endişeleri gidermeye yardımcı olur, daha fazla bilgi üretme ancak `ExpectedException` özniteliği, bu bilgileri sağlayamaz...  
  
   Test altındaki yöntemi yeniden bakarak, her iki koşullu deyimin kullanmak görüyoruz bir `ArgumentOutOfRangeException` adı bağımsız değişkeni bir parametre olarak alan oluşturucu:  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 MSDN Kitaplığı'nın arama aracında bir oluşturucu, çok daha zengin bilgi raporlarının olduğunu keşfedeceksiniz. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` bağımsız değişken, bağımsız değişken değeri ve kullanıcı tanımlı bir ileti adını içerir. Biz bu oluşturucuyu kullanarak test altındaki yöntemi yeniden düzenleyebilirsiniz. Daha da iyi hataları belirlemek için genel olarak kullanılabilen tür üyelerini kullanabiliriz.  
  
 **Test altındaki kodu yeniden düzenleyin**  
  
 Sınıf kapsamındaki hata iletileri için iki sabit ilk tanımlarız:  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Biz, ardından iki koşullu ifadeler değiştirin `Debit` yöntemi:  
  
```csharp  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Test yöntemlerini yeniden düzenleme**  
  
 Bizim test yönteminde, biz öncelikle kaldırmanız `ExpectedException` özniteliği. Bunun yerine oluşan özel durumları yakalamalı ve onu doğru koşul ifadesinde oluşturulduğunu doğrulamalıyız. Ancak biz artık kalan koşullarımızı doğrulamak için iki seçenek arasında karar vermeliyiz. Örneğin `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` yöntemi, biz alabilir aşağıdaki eylemlerden birini:  
  
- Assert, `ActualValue` özelliği özel durumun (ikinci parametresi `ArgumentOutOfRangeException` Oluşturucu) başlangıç bakiyesinden büyük. Bu seçenek, test ederiz gerektirir `ActualValue` özelliği karşı olan özel durumun `beginningBalance` test yönteminin değişken ve ayrıca olduğunu doğrulamayı gerektirir `ActualValue` sıfırdan büyük.  
  
- İletinin (oluşturucunun üçüncü parametresi) içerdiğini `DebitAmountExceedsBalanceMessage` tanımlanan `BankAccount` sınıfı.  
  
  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Bize ilk seçeneğin gerekli olan hesaplamalar olmadan ikinci seçeneği doğrulamak Microsoft birim test çerçevesi yöntemi sağlar.  
  
  Düzeltmenin ikinci denemesi `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` aşağıdaki gibi görünmelidir:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Değişiyorsa, yeniden yaz ve yeniden Çözümle**  
  
 Biz, biz test yöntemlerini farklı değerlerle yeniden test et, aşağıdakilerle karşılaşırız:  
  
1. Assert kullanarak size doğru hata catch, burada `debitAmount` bakiyeden büyük `Contains` onayı geçer, özel durum yok sayılır ve bu nedenle test yöntemi geçirilir. İstediğimiz davranış budur.  
  
2. Biz kullanıyorsanız bir `debitAmount` 0'dan küçük olan, yanlış hata iletisi döndürüldüğünden assert başarısız olur. Biz geçici belirtiyorsak onay ayrıca başarısız olur `ArgumentOutOfRange` test kod yolu altındaki yöntemin içindeki diğer noktada özel durum. Bu çok iyi.  
  
3. Varsa `debitAmount` değerdir geçerli (yani, ama, sıfırdan büyükse bakiyeden küçükse hiçbir özel durum yakalanmaz, yani onay asla yakalanmaz. Test yöntemi geçirilir. Test yöntemi özel durum oluşturmazsa başarısız istediğimizden bu iyi değildir.  
  
   Üçüncü bir olgu, bizim test yönteminde bir hatadır. Sorunu çözmeyi denemek için eklediğimiz bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> nerede hiçbir özel durum durumu işlemek için test yönteminin sonunda onay.  
  
   Ancak çözülüp doğru özel durum yakalandığında testin başarısız olduğunu gösterir. Catch deyimi özel durumu sıfırlar ve yeni onaylama işleminde başarısız yöntem yürütme devam eder. Yeni sorunu gidermek için eklediğimiz bir `return` deyiminden sonra `StringAssert`. Yeniden test yapmak, bizim sorunları düzelttik onaylar. Son `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` aşağıdaki gibi görünür:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 Bu son bölümde, biz test kodumuzu geliştirme çalışmalarımız daha sağlam ve bilgilendirici test yöntemlerimiz olmasını sağladı. Ancak daha da önemlisi, ek olarak yapılan çözümlemeler aynı zamanda test altındaki Projemizin daha iyi kodlama yönlendirdi.



