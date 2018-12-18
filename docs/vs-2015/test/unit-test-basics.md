---
title: Birim testi temel bilgileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.UnitTest.CreateUnitTest
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62a451b1004a6e93980d7fb594781e661b06246d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863632"
---
# <a name="unit-test-basics"></a>Birim Testi Temelleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod oluşturma ve birim testleri çalıştırarak beklendiği gibi çalışıp çalışmadığını denetleyin. Birim test, test edebilirsiniz ayrık test edilebilir davranışları programınızın işlevlerini olarak tek tek bölümlere ayırmak denir *birimleri*. Visual Studio Test Gezgini, birim testleri çalıştırmak ve Visual Studio'da sonuçlarını görüntülemek için esnek ve verimli bir yol sağlar. Visual Studio için Microsoft birim test çerçeveler yönetilen ve yerel kod için yükler. Kullanım bir *birim testi çerçevesi* birim testleri oluşturmak için bunları çalıştırmak ve bu testlerin sonuçları rapor. Kodunuzun düzgün çalışıp çalışmadığını test etmek için değişiklik yaptığınız zaman yeniden çalıştır birim testleri. Visual Studio Enterprise'ı kullandığınızda, her derleme sonrasında testleri otomatik olarak çalıştırabilir.  
  
 Yazılım geliştirme iş akışınızın bir parçası olduğunda birim testi kodunuzun kalitesini üzerinde en büyük etkiye sahiptir. Bir işlev veya diğer blok uygulama kodu yazdığınız hemen ardından standart, sınır ve giriş verisi hatalı durumda yanıt kodu davranışını doğrulayın ve kod tarafından yapılan açık veya örtülü varsayımlar kontrol birim testleri oluşturun. İle *test güdümlü geliştirme*, birim testleri tasarım belgeleri ve işlevsel özellikleri kullanmak için kod yazmadan önce birim testleri oluşturun.  
  
 Test projelerini hızla oluşturmak ve kodunuzdan test yöntemleri veya ihtiyaç duyduğunuz gibi el ile testler oluşturun. .NET kodunuzu keşfetmek için Intellitest kullandığınızda, test verileri ve birim testleri paketi oluşturabilirsiniz. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Hakkında bilgi edinin [kodunuz için birim testleri oluşturma](http://msdn.microsoft.com/library/dn823749.aspx).  
  
 Test Gezgini, Test Gezgini eklentisi arabirimleri uyguladıysanız birim testi çerçevelerini üçüncü taraf ve açık kaynak da çalıştırabilirsiniz. Birçok Visual Studio Uzantı Yöneticisi ve Visual Studio Galerisi aracılığıyla bu çerçevesini ekleyebilirsiniz. Bkz: [üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)  
  
-   [Hızlı başlangıçlar](#BKMK_Quick_starts)  
  
-   [MyBank çözümü örneği](#BKMK_The_MyBank_Solution_example)  
  
-   [Birim test projesi oluşturmak ve test yöntemleri](#BKMK_Creating_the_unit_test_projects)  
  
-   [Testlerinizi yazma](#BKMK_Writing_your_tests)  
  
-   [Testleri Test Gezgini'nde çalıştırma](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Testleri görüntülemek ve çalıştırmak](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)  
  
##  <a name="BKMK_Unit_testing_overview"></a> Birim test genel bakış  
  
###  <a name="BKMK_Quick_starts"></a> Hızlı başlangıçlar  
 Doğrudan kodlama içine alan birim testine giriş için aşağıdaki konulardan birine bakın:  
  
-   [İzlenecek yol: Yönetilen Kod için Birim Testleri Oluşturma ve Çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)  
  
-   [Hızlı Başlangıç: Test Gezgini ile Test Güdümlü Geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)  
  
-   [Yerel kod Test Gezgini ile birim testi](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)  
  
##  <a name="BKMK_The_MyBank_Solution_example"></a> MyBank çözümü örneği  
 Bu konu başlığında, kullandığımız adlı kurgusal bir uygulamanın geliştirilmesi `MyBank` örnek olarak. Bu konudaki açıklamaları izlemek için gerçek kod gerekmez. Test yöntemlerini C# dilinde yazılmış ve yönetilen kod için Microsoft birim testi Çerçevesi'ni kullanarak, ancak kavramlardan kolayca diğer dillerde ve çerçevelerde aktarılır.  
  
 ![MyBank çözüm](../test/media/ute-mybanksolution.png "UTE_MyBankSolution")  
  
 Bizim için bir tasarım ilk denemesini `MyBank` uygulama ayrı bir hesap ve kendi banka işlemleri temsil eden bir hesapları bileşen ve toplama ve yönetmek için işlevleri temsil eden bir veritabanı bileşeni içerir Bireysel hesaplar.  
  
 Oluşturduğumuz bir `MyBank` iki proje içeren bir çözümü:  
  
- `Accounts`  
  
- `BankDb`  
  
  Bizim ilk denemesini tasarlama `Accounts` proje içeren bir hesap, ortak işlevsellik ürünü ve hesabı ve bir sınıf varlıklar geri alınmasının gibi hesabının herhangi bir türde belirten bir arabirim hakkındaki temel bilgileri tutmak için bir sınıf Çek hesabı temsil eden arabirimden türetilmiş. Aşağıdaki kaynak dosyaları oluşturarak hesapları projeleri başlamadan:  
  
- `AccountInfo.cs` hesabınız için temel bilgileri tanımlar.  
  
- `IAccount.cs` bir standardı tanımlar `IAccount` havale ve varlıklar bir hesaptan geri alma ve hesap bakiyesi almak için yöntemleri dahil olmak üzere, hesap için arabirim.  
  
- `CheckingAccount.cs` içeren `CheckingAccount` uygulayan sınıf `IAccounts` Çek hesabı için arabirim.  
  
  Çek Hesabı hesabından yapmanız gereken, bir şey çekilen miktarın bakiyeden hesap bakiyesinden daha az olduğundan emin olmaktır deneyiminden biliyoruz. Biz geçersiz kılmak için `IAccount.Withdaw` yönteminde `CheckingAccount` denetleyen ve bu koşul için bir yöntem. Yöntem şuna benzeyebilir:  
  
```csharp  
  
public void Withdraw(double amount)  
{  
    if(m_balance >= amount)  
    {  
        m_balance -= amount;  
    }  
    else  
    {  
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")  
    }  
}  
  
```  
  
 Biz bazı koda sahip olduğunuza göre bunu test etmek için zamanı geldi.  
  
##  <a name="BKMK_Creating_the_unit_test_projects"></a> Birim test projesi oluşturmak ve test yöntemleri  
 Genellikle, kod birim testi saptamalar ve birim testi projesi oluşturmak hızlı olur. Veya, gereksinimlerinize bağlı olarak el ile testleri ve birim testi projesi oluşturmak tercih edebilirsiniz.  
  
 **Birim testi projesi oluşturma ve birim testi saptamaları**  
  
1. Kod Düzenleyicisi penceresi, sağ tıklatın ve seçin **birim testleri Oluştur** bağlam menüsünden.  
  
    ![Bağlam menüsü düzenleyici penceresinde görüntüleme](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")  
  
2. Birim testleri oluşturma veya oluşturmak için kullanılan değerleri değiştirmek için Varsayılanları kabul etmek için Tamam'a tıklayın ve ad birim test projesi ve birim testlerini. Varsayılan olarak, birim test yöntemlerini için eklenen kodu seçebilirsiniz.  
  
    ![Sağ&#45;Düzenleyicisi'nde ve birim testleri Oluştur seçin](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")  
  
3. Birim test Saplamaları sınıfındaki tüm yöntemler için yeni bir birim test projesi oluşturulur.  
  
    ![Birim testlerini oluşturulan](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")  
  
4. Bilgi edinmek için artık ileriye gitmek nasıl [kodu için birim test yöntemlerini ekleyin](#BKMK_Writing_your_tests) anlamlı birim sınamanız ve kodunuzu sınamanız eklemek isteyebileceğiniz herhangi bir ek birim test yapma.  
  
   **Birim test projesi ve birim testi el ile oluşturma**  
  
   Birim testi projesi genellikle tek bir kod proje yapısını yansıtır. Adlı iki birim testi projelerini eklediğiniz MyBank örnekte `AccountsTests` ve `BankDbTests` için `MyBanks` çözüm. Test proje adı isteğe bağlı, ancak standart bir adlandırma kuralı benimseyen iyi bir fikirdir.  
  
   **Birim testi projesi çözüme eklemek için:**  
  
5. Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje** (klavye Ctrl + Shift + N).  
  
6. Yeni Proje iletişim kutusunda, genişletme **yüklü** düğümü, test projeniz için kullanın ve ardından istediğiniz dili seçin **Test**.  
  
7. Microsoft birim testi çerçevelerini birini kullanmak üzere, **Birim Test projesi** proje şablonları listesinden. Aksi takdirde, kullanmak istediğiniz test çerçevesi biriminin proje şablonu seçin. Sınanacak `Accounts` proje örneğimiz, proje garip gelse `AccountsTests`.  
  
   > [!WARNING]
   >  Tüm üçüncü taraf ve açık kaynak birim testi çerçevelerini bir Visual Studio Proje şablonu sağlar. Bir proje oluşturma hakkında daha fazla bilgi için framework belgeye başvurun.  
  
8. Birim test projenizde örneğimizde hesapları projesi için test edilen kod projesine bir başvuru ekleyin.  
  
    Kod projesine bir başvuru oluşturmak için:  
  
   1.  Çözüm Gezgini'nde projeyi seçin.  
  
   2.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.  
  
   3.  Başvuru Yöneticisi iletişim kutusunu açın **çözüm** düğümünü seçip **projeleri**. Kod proje adını seçin ve iletişim kutusunu kapatın.  
  
   Her birim testi projesi kod projesinde sınıfların adlarını yansıtan sınıfları içerir. Bizim örneğimizde `AccountsTests` proje aşağıdaki sınıfları içerebilir:  
  
-   `AccountInfoTests` sınıfı için birim test yöntemlerini içeren `AccountInfo` sınıfını `BankAccount` proje  
  
-   `CheckingAccountTests` sınıfı için birim test yöntemlerini içeren `CheckingAccount` sınıfı.  
  
##  <a name="BKMK_Writing_your_tests"></a> Testlerinizi yazma  
 Birim testi çerçevesi kullandığınız ve Visual Studio IntelliSense birim testleriniz için bir kod projesi için kod yazma aracılığıyla size yol gösterir. Test Gezgini'nde de çalıştırmak için çoğu çerçeveleri, birim test yöntemlerini tanımlamak için özel öznitelikler eklemeniz gerekir. Çerçeveleri ayrıca bir yol sağlar; genellikle aracılığıyla deyimleri ya da yöntem öznitelikleri assert — test yöntemi başarılı olup olmadığını belirtmek için. Diğer öznitelikleri sınıf başlatma ve her bir test yöntemi ve her test yönteminin sonra ve sınıf yok önce çalıştırılır kaldırma yöntemleri önce isteğe bağlı kurulum yöntemlerle belirleyin.  
  
 AAA (Düzenle, eylem, onay) düzeni, test edilen bir yöntem için birim testleri yazma genel bir yoludur.  
  
- **Yerleştir** bölümü bir birim test yöntemi, nesneleri başlatır ve yöntemi testten geçirilen verileri değerini ayarlar.  
  
- **Yasası** bölüm düzenlenmiş parametrelerle test altındaki yöntemi çağırır.  
  
- **Assert** bölümü, test altındaki yöntem eylem beklendiği gibi çalıştığını doğrular.  
  
  Sınanacak `CheckingAccount.Withdraw` yöntemi Bizim örneğimizde, biz iki test yazabilirsiniz: standart yöntemin davranışını doğrular ve birden çok bakiyesi olan bir mevzuatı başarısız olacağını doğrular. İçinde `CheckingAccountTests` sınıfı, biz aşağıdaki yöntemleri ekleyin:  
  
```csharp  
[TestMethod]  
public void Withdraw_ValidAmount_ChangesBalance()  
{  
    // arrange  
    double currentBalance = 10.0;  
    double withdrawal = 1.0;  
    double expected = 9.0;  
    var account = new CheckingAccount("JohnDoe", currentBalance);  
    // act  
    account.Withdraw(withdrawal);  
    double actual = account.Balance;  
    // assert  
    Assert.AreEqual(expected, actual);  
}  
  
[TestMethod]  
[ExpectedException(typeof(ArgumentException))]  
public void Withdraw_AmountMoreThanBalance_Throws()  
{  
    // arrange  
    var account = new CheckingAccount("John Doe", 10.0);  
    // act  
    account.Withdraw(20.0);  
    // assert is handled by the ExpectedException  
}  
  
```  
  
 Unutmayın `Withdraw_ValidAmount_ChangesBalance` açık bir kullanan `Assert` test yönteminin geçer veya başarısız olursa belirlemek için deyimi sırada `Withdraw_AmountMoreThanBalance_Throws` kullanır `ExpectedException` test yönteminin başarısını belirlemek için öznitelik. Güvenli bir birim test çerçevesi test yöntemleri try/catch deyimleri sarmalar. Çoğu durumda, bir özel durum yakalandığında test yöntemi başarısız olur ve özel durum yok sayılır. `ExpectedException` Özniteliği test yöntemi, belirtilen özel durum oluşturulursa geçmesine neden olur.  
  
 Microsoft birim testi çerçevelerini hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
-   [Yönetilen Kod için Microsoft Birim Testi Çerçevesi ile .NET Framework için Birim Testleri Yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [C++ için Microsoft Birim Testi Çerçevesi ile C/C++ için Birim Testleri Yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
## <a name="set-timeouts-for-unit-tests"></a>Birim testleri için zaman aşımını ayarlayın  
 Bir bireysel test yönteminde bir zaman aşımı ayarlamak için:  
  
```csharp  
[TestMethod]  
[Timeout(2000)]  // Milliseconds  
public void My_Test()  
{ ...  
}  
```  
  
```vb  
  
```  
  
 İzin verilen maksimum zaman aşımını ayarlamak için:  
  
```csharp  
[TestMethod]  
[Timeout(TestTimeout.Infinite)]  // Milliseconds  
public void My_Test ()  
{ ...  
}  
```  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Testleri Test Gezgini'nde çalıştırma  
 Test projesi oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünür değilse seçin **Test** Visual Studio menüsünde **Windows**ve ardından **Test Gezgini**.  
  
 ![Birim Test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Test Gezgini varsayılan görünümünü çalıştırma, yazma ve testlerinizi yeniden çalıştırın gibi sonuçları gruplarında görüntüler. **başarısız testler**, **başarılı testler**, **Atlanan testler** ve  **Testleri Çalıştır**. Bu gruba tüm bunları testleri görüntüler görünümünü açmak için bir grup başlığı seçebilirsiniz.  
  
 Ayrıca, arama kutusuna genel düzeyde eşleşen metin veya önceden tanımlanmış filtrelerden birini seçerek herhangi bir görünümde testlere filtre uygulayabilirsiniz. Herhangi bir zamanda herhangi bir seçimi testler çalıştırabilirsiniz. Bir test çalıştırması sonuçlarını hemen Gezgini penceresinin en üstündeki geçer/başarısız çubuğunda görünür. Bir test yönteminin sonucunun ayrıntılarını test seçtiğinizde görüntülenir.  
  
###  <a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a> Testleri görüntülemek ve çalıştırmak  
 Test Gezgini araç çubuğu, keşfedin, düzenlemek ve ilginizi çeken testler yardımcı olur.  
  
 ![Test Gezgini araç çubuğundan testleri](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
 Seçebileceğiniz **tümünü Çalıştır** tüm testleri çalıştırmak veya **çalıştırma** bir alt kümesini Çalıştırılacak testleri seçmek için. Sonra bir test kümesini çalıştırmak, test çalışmasının özetini Test Gezgini penceresinin en altında görüntülenir. Bu testin ayrıntılarını alt bölmede görüntülemek için bir test seçin. Seçin **testi Aç** kaldırabilir bağlam menüsünü (klavye: F12) seçilen test için kaynak kodunu görüntülemek için.  
  
 Paralel test yürütme ile bireysel testler herhangi bir sırada çalıştırılan engelleyen bağımlılık varsa, açma ![ALIŞTIR&#95;parallelicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon küçük") araç çubuğundaki iki durumlu düğme. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.  
  
###  <a name="BKMK_Running_tests_after_every_build"></a> Her derleme sonrasında Testleri Çalıştır  
  
> [!WARNING]
>  Her derleme yalnızca Visual Studio Enterprise'da desteklendikten sonra birim testleri çalıştırma.  
  
|||  
|-|-|  
|![Yapıdan sonra çalıştırmak](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Her bir yerel oluşturmadan sonra birim testlerinizi çalıştırmak için tercih **Test** standart menüsünde **oluşturmadan sonra Testleri Çalıştır** Test Gezgini araç çubuğundaki.|  
  
###  <a name="BKMK_Filtering_and_grouping_the_test_list"></a> Test listesini gruplandırma ve filtreleme  
 Çok sayıda test varsa, belirtilen dizeyle listeyi filtrelemek için Test Gezgini arama kutusuna yazabilirsiniz. Filtre etkinliğiniz filtre listeden seçerek daha fazla kısıtlayabilirsiniz.  
  
 ![Arama filtre kategorisi](../test/media/ute-searchfilter.png "UTE_SearchFilter")  
  
|||  
|-|-|  
|![Test Gezgini Grup düğmesi](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Kategoriye göre testlerinizi gruplamak için seçin **Group By** düğmesi.|  
  
 Daha fazla bilgi için [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)  
  
## <a name="qa"></a>SORU- CEVAP  
 **S: nasıl birim testleri debug?**  
  
 **Y:** testleriniz için hata ayıklama oturumu başlatmak için kullanım Test Gezgini. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:  
  
1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.  
  
   > [!NOTE]
   >  Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.  
  
2. Test Gezgini'nde test yöntemlerini seçin ve ardından **seçilen Testlerde Hata Ayıkla** kısayol menüsünden.  
  
   Hakkında daha ayrıntılı bilgi edinin [birim testleri hata ayıklama](../debugger/debugging-in-visual-studio.md).  
  
   **S: TDD kullanıyorum varsa nasıl miyim kod benim testlerden oluşturun?**  
  
   **Y:** kullanım proje kodunuzu sınıflar ve yöntemler oluşturmak için IntelliSense. Sınıf çağıran bir test yöntemi veya oluşturmak istediğiniz yöntemi bir deyim yazma ve çağrının altında IntelliSense menüsünü açın. Bir yeni sınıf oluşturucusuna çağrı ise seçin **yeni tür oluşturma** menüsünden ve kod projenize bir sınıf eklemek için sihirbazı izleyin. Bir yöntem çağrısı ise seçin **yeni metot Oluştur** IntelliSense menüsünde.  
  
   ![Yöntem Saplaması IntelliSense menü oluşturmak](../test/media/ute-generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")  
  
   **Testi çalıştırmak için giriş olarak birden çok veri kümesi Al birim testleri oluşturabilirim miyim?**  
  
   **Y:** Evet. *Veri tabanlı test yöntemleri* , bir tek birim test yöntemi ile bir aralıktaki değerleri test olanak tanır. Kullanım bir `DataSource` test etmek istediğiniz değişken değerleri veri kaynağını seçin ve bu tablo belirten test yöntemini içeren özniteliği.  Yöntem gövdesinde, satır değerlerini kullanarak değişkenlere atamak `TestContext.DataRow[` *ColumnName* `]` dizin oluşturucu.  
  
> [!NOTE]
>  Yalnızca yönetilen kod için Microsoft birim testi çerçevesini kullanarak yazma yöntemleri test etmek için bu yordamları uygulayın. Farklı bir framework kullanıyorsanız, eşdeğer bir işlevselliği için framework belgelerine bakın.  
  
 Örneğin, gereksiz bir yönteme eklediğimiz varsayın `CheckingAccount` adlı sınıfı `AddIntegerHelper`. `AddIntegerHelper` iki tamsayı ekler.  
  
 İçin veri odaklı bir test oluşturmak için `AddIntegerHelper` yöntemi, ilk oluştururuz adında bir Access veritabanı `AccountsTest.accdb` ve adlı bir tablo `AddIntegerHelperData`. `AddIntegerHelperData` Tablo eklenmesi, birinci ve ikinci işlenenden belirtmek için sütunları ve beklenen sonuç belirtmek için bir sütun tanımlar. Size bir dizi satır uygun değerlerle doldurun.  
  
```csharp  
  
[DataSource(  
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",   
    "AddIntegerHelperData"  
)]  
[TestMethod()]  
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()  
{  
    var target = new CheckingAccount();  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.AddIntegerHelper(x, y);  
    Assert.AreEqual(expected, actual);  
}  
  
```  
  
 Öznitelikli yöntem, tablodaki her satır için bir kez çalışır. Test Gezgini yinelemeleri başarısız yöntemi için test hatası bildirir. Test sonuçları ayrıntılar bölmesine yöntemi, her veri satırının geçer/başarısız durumu yöntemi gösterir.  
  
 Daha fazla bilgi edinin [veri temelli birim testlerini](../test/how-to-create-a-data-driven-unit-test.md).  
  
 **Birim testlerimi benim kodumu ne kadarı test görüntüleyebilir miyim?**  
  
 **Y:** Evet. Visual Studio kod kapsamı Aracı'nı kullanarak birim testleriniz tarafından gerçekten edildiğini kodunuzun miktarını belirleyebilirsiniz. Yerel ve yönetilen diller ve Birim Test çerçevesi tarafından çalıştırılabilir tüm birim testi çerçevelerini desteklenir.  
  
 Kod kapsamı Seçili testler ya da bir çözümdeki tüm testleri çalıştırabilirsiniz. Kod Kapsamı Sonuçları penceresi satır, işlevi, sınıf, ad alanı ve modül tarafından uygulanan ürünün kodu bloklarının yüzdesini görüntüler.  
  
 Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için tercih **testleri** Visual Studio menüsünde seçip **kod kapsamını analiz etme**.  
  
 Kapsama sonuçlarını kod kapsamı Sonuçları penceresinde görüntülenir.  
  
 ![Kod kapsamı sonuçlarını](../test/media/ute-codecoverageresults.png "UTE_CodeCoverageResults")  
  
 Daha fazla bilgi edinin [kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .  
  
 **S: ben yöntemleri dış bağımlılıkları olan kodumu test edebilirim?**  
  
 **Y:** Evet. Visual Studio Enterprise yüklüyse, Microsoft Fakes ile yönetilen kod için birim testi çerçevelerini kullanarak yazdığınız test yöntemleri kullanılabilir.  
  
 Microsoft Fakes, dış bağımlılıklar için yedek sınıflar oluşturmak için iki yaklaşım kullanır.  
  
1. *Saptamalar* hedef bağımlılık sınıfının üst arabirimden türetilmiş yedek sınıflar oluşturun. Hedef sınıfın ortak sanal yöntemler için saptama yöntemleri yerine kullanılabileceği.  
  
2. *Dolgular* yerine dolgu yöntemi sanal olmayan yöntemler için bir hedef yöntem çağrısına yöneltmektir için çalışma zamanı Araçları'nı kullanın.  
  
   Her iki yaklaşım test yönteminde istediğiniz davranışını belirtmek için bağımlılık yöntemine yönelik çağrılar, oluşturulan temsilcileri kullanın.  
  
   Daha fazla bilgi edinin [birim test yöntemlerini Microsoft Fakes ile izole](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
   **S: diğer birim testi çerçevelerini birim testleri oluşturmak için kullanabilir miyim?**  
  
   **Y:** Evet, bu adımları [bulun ve diğer çatıları Yükle](../test/install-third-party-unit-test-frameworks.md). Visual Studio'yu yeniden başlatmanızın ardından, birim testleri oluşturmak için çözümü yeniden açın ve yüklü Framework burada seçin:  
  
   ![Diğer yüklü birim testi çerçevesini seçin](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")  
  
   Seçili olan altyapıda kullanarak, birim test Saplamaları oluşturulur.



