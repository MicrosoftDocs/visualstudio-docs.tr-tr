---
title: 'İzlenecek yol: bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanma | Microsoft Docs'
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
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: gewarren
manager: douge
ms.openlocfilehash: f3dca876e777e8f40773ca42b05fece1c22fe33e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843047"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>İzlenecek Yol: Bir Veri Kaynağı Tanımlamak için Yapılandırma Dosyası Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir birim testi için app.config dosyasında tanımlanan bir veri kaynağı kullanılması gösterilmektedir. Tarafından kullanılan bir veri kaynağı tanımlayan bir app.config dosyası oluşturma hakkında bilgi edineceksiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> sınıfı. Bu izlenecek yolda gösterilen görevler aşağıdakileri içerir:  
  
-   Bir app.config dosyası oluşturuluyor.  
  
-   Özel yapılandırma bölümü tanımlama.  
  
-   Bağlantı dizeleri tanımlama.  
  
-   Veri kaynaklarını tanımlama.  
  
-   Verilere erişme kaynakları kullanarak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> sınıfı.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için şunlara ihtiyacınız olacak:  
  
-   Visual Studio Enterprise  
  
-   Microsoft Access veya Microsoft Excel verilerini test yöntemlerini en az biri için sağlamak için.  
  
-   Bir test projesi içeren bir Visual Studio çözümü.  
  
## <a name="create-the-appconfig-file"></a>App.config dosyasını oluşturma  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>Projeye bir app.config dosyası eklemek için  
  
1.  Test projenize bir app.config dosyası zaten varsa, Git [özel yapılandırma bölümü tanımlaması](#DefineCustomConfigurationSection).  
  
2.  Test projenize sağ tıklayıp **Çözüm Gezgini**, işaret **Ekle**ve ardından **yeni öğe**.  
  
     **Yeni Öğe Ekle** penceresi açılır.  
  
3.  Seçin **uygulama yapılandırma dosyası** şablonu ve tıklatın **Ekle**.  
  
##  <a name="DefineCustomConfigurationSection"></a> Özel yapılandırma bölümü tanımlayın  
 App.config dosyasını inceleyin. En az bir kök öğe ve XML bildirimi de içerir.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Özel yapılandırma bölümü app.config dosyasına eklemek için  
  
1. App.config kök öğesi olmalıdır `configuration` öğesi. Oluşturma bir `configSections` öğesiyle `configuration` öğesi. `configSections` App.config dosyasında ilk öğe olmalıdır.  
  
2. İçinde `configSections` öğesi oluşturmak bir `section` öğesi.  
  
3. İçinde `section` öğesi adlı öznitelik ekleme `name` ve eşit bir değer atayın `microsoft.visualstudio.testtools`. Adlı başka bir öznitelik Ekle `type` ve eşit bir değer atayın `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
   `section` Öğesi şuna benzer görünmelidir:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
>  Derleme adı, kullanmakta olduğunuz Microsoft Visual Studio .NET Framework derleme eşleşmesi gerekir. Visual Studio .NET Framework 3.5 kullanıyorsanız sürümü için 9.0.0.0 ayarlayın. Visual Studio .NET Framework 2.0 kullanıyorsanız, sürüm için 8.0.0.0 ayarlayın.  
  
## <a name="define-connection-strings"></a>Bağlantı dizeleri tanımlama  
 Sağlayıcı belirli bilgileri veri kaynaklarına erişim için bağlantı dizelerini tanımlar. Bağlantı dizelerini yapılandırma dosyalarında tanımlanan bir uygulama arasında yeniden kullanılabilir veri sağlayıcısı bilgileri sağlar. Bu bölümde, özel yapılandırma bölümünde tanımlanan veri kaynakları tarafından kullanılacak olan iki bağlantı dizesi oluşturun.  
  
#### <a name="to-define-connection-strings"></a>Bağlantı dizeleri tanımlamak için  
  
1.  Sonra `configSections` öğesi oluşturmak bir `connectionStrings` öğesi.  
  
2.  İçinde `connectionStrings` öğesini iki `add` öğeleri.  
  
3.  İlk `add` öğesinde şu öznitelikler ve değerler için bir Microsoft Access veritabanına bağlantı oluşturun:  
  
|Öznitelik|Değerler|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 İkinci `add` öğesinde şu öznitelikler ve değerler için bir Microsoft Excel elektronik tablosuna bir bağlantı oluşturun:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 `connectionStrings` Öğesi şuna benzer görünmelidir:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama  
 Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört öznitelikleri içerir.  
  
- `name` tarafından kullanılan kimliği tanımlar <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> kullanmak için hangi veri kaynağını belirtmek için.  
  
- `connectionString` Bağlantı dizeleri tanımlama bir önceki bölümde oluşturulan bağlantı dizesini tanımlar.  
  
- `dataTableName` Tablo veya testinde kullanmak üzere verileri tutan sayfasını tanımlar.  
  
- `dataAccessMethod` veri kaynağındaki veri değerlerine erişim için teknik tanımlar.  
  
  Bu bölümde, bir birim testinde kullanmak üzere iki veri kaynağı tanımlayacaksınız.  
  
#### <a name="to-define-data-sources"></a>Veri kaynakları tanımlamak için  
  
1.  Sonra `connectionStrings` öğesi oluşturmak bir `microsoft.visualstudio.testtools` öğesi. Bu bölümde, bir özel yapılandırma bölümü içinde tanımlayın oluşturuldu.  
  
2.  İçinde `microsoft.visualstudio.testtools` öğesi oluşturmak bir `dataSources` öğesi.  
  
3.  İçinde `dataSources` öğesini iki `add` öğeleri.  
  
4.  İlk `add` öğesinde şu öznitelikler ve değerler için bir Microsoft Access veri kaynağı oluşturun:  
  
|Öznitelik|Değerler|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 İkinci `add` öğesinde şu öznitelikler ve değerler için bir Microsoft Excel veri kaynağı oluşturun:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 `microsoft.visualstudio.testtools` Öğesi şuna benzer görünmelidir:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Son app.config dosyasına şuna benzer görünmelidir:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>App.config dosyasında tanımlanan veri kaynakları kullanarak bir birim testi oluşturma  
 Tanımlanan bir app.config dosyası, app.config dosyasında tanımlanan veri kaynaklarında bulunan verileri kullanan bir birim testi oluşturacaksınız. Bu bölümde, yapacağız:  
  
-   App.config dosyasında bulunan veri kaynakları oluşturun.  
  
-   Veri kaynakları, her veri kaynağı değerleri karşılaştırmak iki test yöntemlerini kullanın.  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Bir Microsoft Access veri kaynağını oluşturmak için  
  
1.  Adlı bir Microsoft Access veritabanı oluşturma `testdatasource.accdb`.  
  
2.  Bir tablo oluşturun ve adlandırın `MyDataTable` içinde `testdatasource.accdb`.  
  
3.  İki alanda oluşturma `MyDataTable` adlı `Arg1` ve `Arg2` kullanarak `Number` veri türü.  
  
4.  Beş varlıklara ekleyin `MyDataTable` için aşağıdaki değerlerle `Arg1` ve `Arg2`sırasıyla: (10,50), (3,2) (6,0) (0,8) ve (12312,1000).  
  
5.  Kaydet ve veritabanı kapatın.  
  
6.  Bağlantı dizesi, veritabanının konumunu gösterecek şekilde değiştirin. Değiştirin `Data Source` veritabanı konumunu gösterecek şekilde.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Bir Microsoft Excel veri kaynağı oluşturmak için  
  
1.  Adlı bir Microsoft Excel elektronik tablosu oluşturma `data.xlsx`.  
  
2.  Adlı bir e-tablosu oluşturmanız `Sheet1` , zaten mevcut değilse `data.xlsx`.  
  
3.  İki sütun üst bilgilerini oluşturabilir ve bunları `Val1` ve `Val2` içinde `Sheet1`.  
  
4.  Beş varlıklara ekleyin `Sheet1` için aşağıdaki değerlerle `Val1` ve `Val2`sırasıyla: (1,1), (2,2) (3,3) (4,4) ve (5,0).  
  
5.  Kaydet ve elektronik kapatın.  
  
6.  Bağlantı dizesi, elektronik konumunu işaret edecek şekilde değiştirin. Değiştirin `dbq` elektronik konumunu gösterecek şekilde.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>App.config veri kaynakları kullanarak bir birim test oluşturmak için  
  
1.  Birim testi için test projesi ekleyin.  
  
     Daha fazla bilgi için [oluşturma ve var olan kod için birim testleri çalıştıran](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2.  Birim testi, otomatik olarak oluşturulan içeriğini aşağıdaki kodla değiştirin:  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3.  DataSource özniteliği inceleyin. App.config dosyasında ayarı adlarını not edin.  
  
4.  Çözümünüzü oluşturun ve MyTestMethod ve MyTestMethod2 testleri çalıştırın.  
  
> [!IMPORTANT]
>  Böylece bunlar dağıtım dizinine öğesindeki teste erişilebilir veri kaynakları gibi öğeleri dağıtın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuza birim testi](../test/unit-test-your-code.md)   
 [Oluşturma ve varolan kod için birim testleri çalıştırma](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Uygulamayı test etme](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Nasıl Yapılır: Veri Temelli Birim Testi Oluşturma](../test/how-to-create-a-data-driven-unit-test.md)



