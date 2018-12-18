---
title: 'Nasıl yapılır: bir veri temelli birim testi oluşturma | Microsoft Docs'
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
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: eeb7efb0c7faa9a2493cfd3f91f6cc4e72408f4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889366"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Nasıl Yapılır: Veri Temelli Birim Testi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen kod için Microsoft birim testi çerçevesini kullanarak bir veri kaynağından test yönteminde kullanılan değerleri almak için bir birim test yöntemi ayarlayabilirsiniz. Yöntemi, tek bir yöntemi kullanarak giriş çeşitli test kolaylaştırır veri kaynağındaki her satır için sırayla çalıştırılır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Test altındaki yöntemi](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
- [Veri kaynağı oluşturma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
- [Test sınıfı için bir TestContext ekleme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
- [Test yönteminin yazma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
  -   [DataSourceAttribute belirtme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
  -   [Verilere erişmek için TestContext.DataRow kullanma](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
- [Test çalıştırma ve sonuçları görüntüleme](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
  Veri temelli birim testi oluşturma, aşağıdaki adımları içerir:  
  
1.  Test yöntemi kullanan değerleri içeren bir veri kaynağı oluşturun. Veri kaynağı, testi çalıştıran makinede kayıtlı herhangi bir tür olabilir.  
  
2.  Özel bir ekleme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> alan ve ortak `TestContext` özelliğini test sınıfı.  
  
3.  Bir birim test yöntemi oluşturun ve ekleme bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> için özniteliği.  
  
4.  Kullanma <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> bir testte kullanılacak değerleri almak için dizin oluşturucu özelliği.  
  
##  <a name="BKMK_The_method_under_test"></a> Test altındaki yöntemi  
 Örneğin, biz oluşturduğunuzu varsayalım:  
  
1. Bir çözüm olarak `MyBank` kabul eder ve farklı hesap türlerinin hareketlerini işler.  
  
2. Bir projede `MyBank` adlı `BankDb` , hesapları için işlemleri yönetir.  
  
3. Bir sınıfa `Maths` içinde `DbBank` herhangi bir işlem bankaya avantajlı olduğundan emin olmak için matematiksel işlevler gerçekleştiren bir proje.  
  
4. Bir birim test projesi adlı `BankDbTests` davranışını test etmek için `BankDb` bileşeni.  
  
5. Bir birim testi sınıf adı verilen `MathsTests` davranışını doğrulamak için `Maths` sınıfı.  
  
   Biz bir yöntemde sınayacak `Maths` bir döngü kullanarak iki tamsayı ekler:  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> Veri kaynağı oluşturma  
 Sınanacak `AddIntegers` yöntemi oluştururuz parametreleri ve döndürülecek beklediğiniz toplamı için değer aralığını belirten bir veri kaynağı. Bizim örneğimizde, biz adlı bir Sql Compact veritabanı oluşturma `MathsData` ve adlı bir tablo `AddIntegersData` aşağıdaki sütun adlarını ve değerlerini içeren  
  
|İlksayı|İkincisayı|TOPLA|  
|-----------------|------------------|---------|  
|0|1.|1.|  
|1.|1.|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Test sınıfı için bir TestContext ekleme  
 Birim test çerçevesi oluşturur bir `TestContext` veri tabanlı test için veri kaynağı bilgilerini depolamak için nesne. Framework, ardından bu nesne değeri olarak ayarlar `TestContext` oluştururuz özelliği.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 Test yönteminizde aracılığıyla verilere `DataRow` dizin oluşturucu özelliği `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Test yönteminin yazma  
 Test yöntemi için `AddIntegers` oldukça basittir. Veri kaynağındaki her satır için diyoruz `AddIntegers` ile **İlksayı** ve **İkincisayı** sütun değerleri parametreler ve dönüş değeri ile karşılaştırarak doğrulayacağız **toplam**sütun değeri:  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 Unutmayın `Assert` yöntemi içeren bir ileti görüntüler `x` ve `y` başarısız bir yineleme değerleri. Varsayılan olarak onaylanan değerler `expected` ve `actual`, testin başarısız Ayrıntılar zaten dahil edilmiştir.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> DataSourceAttribute belirtme  
 `DataSource` Özniteliği test yönteminde veri kaynağı ve kullandığınız tablonun adı için bağlantı dizesini belirtir. Bağlantı dizesindeki gördüğü bilgiler, kullandığınız veri kaynağı türüne bağlı olarak farklılık gösterir. Bu örnekte, bir SqlServerCe veritabanı kullandık.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 DataSource özniteliği üç Oluşturucusu vardır.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Bir parametre ile bir oluşturucu, çözüm için app.config dosyasında depolanan bağlantı bilgilerini kullanır. *DataSourceSettingsName* bağlantı bilgilerini belirten yapılandırma dosyasında Xml öğesi adı.  
  
 App.config dosyasını kullanarak birim testinin kendisi için değişiklik yapmadan veri kaynağının konumunu değiştirmenize izin verir. Bir app.config dosyası oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [izlenecek yol: bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 `DataSource` Oluşturucu iki parametre ile veri kaynağı ve test yöntemi için veri içeren bir tablo adı için bağlantı dizesini belirtir.  
  
 Bağlantı dizelerini veri kaynağı türü türüne bağlıdır, ancak veri sağlayıcı değişmez adını belirten bir sağlayıcı öğesi içermelidir.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Verilere erişmek için TestContext.DataRow kullanma  
 Verilere erişmek için `AddIntegersData` tablo, kullanın `TestContext.DataRow` dizin oluşturucu. `DataRow` olan bir <xref:System.Data.DataRow> nesne için sütun değerlerini dizini veya sütun adlarına göre alıyoruz. Değerleri nesneler olarak döndürdüğünden, bunları uygun türe dönüştürmeniz gerekir:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Test çalıştırma ve sonuçları görüntüleme  
 Bir test yönteminin yazma işlemini tamamladığınızda, test projesi oluşturun. Test yöntemini Test Gezgini penceresinde görünür **çalıştırılmamış testler** grubu. Test Gezgini çalıştırma, yazma ve testlerinizi yeniden çalıştırın gibi sonuçları gruplarında görüntüler. **başarısız testler**, **başarılı testler**, ve **çalıştırılmamış testler**. Seçebileceğiniz **tümünü Çalıştır** tüm testleri çalıştırmak veya seçmek için **Çalıştır...**  bir alt kümesini Çalıştırılacak testleri seçmek için.  
  
 Testiniz çalışırken Explorer'ın üstündeki test sonuçları çubuğunda bir animasyon görünür. Testler başarısız olursa test çalışmasının sonunda, tüm testler başarılı değilse yeşil veya Kırmızı çubuk olacaktır. Test Gezgini penceresinin altındaki ayrıntılar bölmesi test çalıştırmasının bir özeti görüntülenir. Bu testin ayrıntılarını alt bölmede görüntülemek için bir test seçin.  
  
 Çalıştırdıysanız `AddIntegers_FromDataSourceTest` yöntemi örneğimizde sonuçlar çubuğunun kırmızıya döner ve test yönteminin taşınır **başarısız testler** verilerden tekrarlayan yöntemlerden herhangi birini başarısız kaynağı, veri odaklı bir test başarısız olur. Veri odaklı bir başarısız test Test Gezgini penceresinde seçin, Ayrıntılar bölmesinde verileri satır dizini tarafından tanımlanan her yineleme sonuçları görüntülenir. Bizim örneğimizde, göründüğü `AddIntegers` algoritması negatif değerler doğru şekilde işlemiyor.  
  
 Ne zaman test altındaki yöntemi düzeltildi ve yeniden test sonuçları çubuk yeşile döner ve test yönteminin taşınır **geçirilen Test** grubu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Nasıl yapılır: birim testi oluşturma ve çalıştırma](http://msdn.microsoft.com/en-us/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Kodunuza birim testi](../test/unit-test-your-code.md)   
 [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)   
 [Yönetilen Kod için Microsoft Birim Testi Çerçevesi ile .NET Framework için Birim Testleri Yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)



