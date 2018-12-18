---
title: 'İzlenecek Yol: Bir Veri Kaynağı Tanımlamak için Yapılandırma Dosyası Kullanma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d329e1aedb5b81c2be2d52614e4c540ecb8ef8aa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066999"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>İzlenecek yol: bir veri kaynağı tanımlamak için bir yapılandırma dosyası kullanma

Bu izlenecek yol içinde tanımlanan bir veri kaynağı kullanımını gösterir. bir *app.config* birim testi dosyası. Nasıl oluşturulacağını öğreneceksiniz bir *app.config* tarafından kullanılan bir veri kaynağı tanımlayan dosyası <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> sınıfı. Bu izlenecek yolda gösterilen görevler aşağıdakileri içerir:

- Oluşturma bir *app.config* dosya.

- Özel yapılandırma bölümü tanımlama.

- Bağlantı dizeleri tanımlama.

- Veri kaynaklarını tanımlama.

- Verilere erişme kaynakları kullanarak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> sınıfı.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu tamamlamak için gerekenler:

- Visual Studio Enterprise

- Microsoft Access veya Microsoft Excel verilerini test yöntemlerini en az biri için sağlamak için.

- Bir test projesi içeren bir Visual Studio çözümü.

## <a name="add-an-appconfig-file-to-the-project"></a>Bir app.config dosyası projeye ekleyin.

1. Test projenizde zaten varsa bir *app.config* dosya, Git [özel yapılandırma bölümü tanımlaması](#define-a-custom-configuration-section).

2. Test projenize sağ tıklayıp **Çözüm Gezgini**ve ardından **Ekle** > **yeni öğe**.

     **Yeni Öğe Ekle** penceresi açılır.

3. Seçin **uygulama yapılandırma dosyası** şablonu ve tıklatın **Ekle**.

##  <a name="define-a-custom-configuration-section"></a>Özel yapılandırma bölümü tanımlayın

İnceleme *app.config* dosya. En az bir kök öğe ve XML bildirimi de içerir.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Özel yapılandırma bölümü app.config dosyasına eklemek için

1. Kök öğesi *app.config* olmalıdır **yapılandırma** öğesi. Oluşturma bir **configSections** öğesiyle **yapılandırma** öğesi. **ConfigSections** ilk öğe olmalıdır *app.config* dosya.

2. İçinde **configSections** öğesi oluşturmak bir **bölümü** öğesi.

3. İçinde **bölümü** öğesi adlı öznitelik ekleme `name` ve değerini atayın `microsoft.visualstudio.testtools`. Adlı başka bir öznitelik Ekle `type` ve değerini atayın `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`.

**Bölümü** öğesi şuna benzer görünmelidir:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Derleme adı, kullanmakta olduğunuz Microsoft Visual Studio .NET Framework derleme eşleşmesi gerekir. Visual Studio .NET Framework 3.5 kullanıyorsanız sürümü için 9.0.0.0 ayarlayın. Visual Studio .NET Framework 2.0 kullanıyorsanız, sürüm için 8.0.0.0 ayarlayın.

## <a name="define-connection-strings"></a>Bağlantı dizeleri tanımlama

Bağlantı dizelerini veri kaynaklarına erişim için sağlayıcıya özel bilgiler tanımlayın. Bağlantı dizelerini yapılandırma dosyalarında tanımlanan bir uygulama arasında yeniden kullanılabilir veri sağlayıcısı bilgileri sağlar. Bu bölümde, özel yapılandırma bölümünde tanımlanan veri kaynakları tarafından kullanılacak olan iki bağlantı dizesi oluşturun.

### <a name="to-define-connection-strings"></a>Bağlantı dizeleri tanımlamak için

1. Sonra **configSections** öğesi oluşturmak bir **connectionStrings** öğesi.

2. İçinde **connectionStrings** öğesini iki **ekleme** öğeleri.

3. İlk **Ekle** öğesinde şu öznitelikler ve değerler için bir Microsoft Access veritabanına bağlantı oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

İkinci **ekleme** öğesi, aşağıdaki öznitelikleri ve değerleri için bir Microsoft Excel elektronik tablosuna bir bağlantı oluşturun:

|Öznitelik|Değerler|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**ConnectionStrings** öğesi şuna benzer görünmelidir:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Veri kaynaklarını tanımlama

Veri kaynakları bölümü, bir veri kaynağından veri almak için test altyapısı tarafından kullanılan dört öznitelikleri içerir.

- `name` tarafından kullanılan kimliği tanımlar <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> kullanmak için hangi veri kaynağını belirtmek için.

- `connectionString` Bağlantı dizeleri tanımlama bir önceki bölümde oluşturulan bağlantı dizesini tanımlar.

- `dataTableName` Tablo veya testinde kullanmak üzere verileri tutan sayfasını tanımlar.

- `dataAccessMethod` veri kaynağındaki veri değerlerine erişim için teknik tanımlar.

Bu bölümde, bir birim testinde kullanmak üzere iki veri kaynağı tanımlarsınız.

### <a name="to-define-data-sources"></a>Veri kaynakları tanımlamak için

1. Sonra **connectionStrings** öğesi oluşturmak bir **microsoft.visualstudio.testtools** öğesi. Bu bölümde, bir özel yapılandırma bölümü içinde tanımlayın oluşturuldu.

2. İçinde **microsoft.visualstudio.testtools** öğesi oluşturmak bir **veri kaynakları** öğesi.

3. İçinde **veri kaynakları** öğesini iki **ekleme** öğeleri.

4. İlk **ekleme** öğesi, aşağıdaki öznitelikleri ve değerleri için bir Microsoft Access veri kaynağı oluşturun:

|Öznitelik|Değerler|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

İkinci **ekleme** öğesi, aşağıdaki öznitelikleri ve değerleri için bir Microsoft Excel veri kaynağı oluşturun:

|Öznitelik|Değerler|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**Microsoft.visualstudio.testtools** öğesi şuna benzer görünmelidir:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

En son *app.config* dosyası şuna benzer görünmelidir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>App.config dosyasında tanımlanan veri kaynakları kullanan bir birim testi oluşturma

Artık bir *app.config* dosyasında tanımlanan, tanımlanan veri kaynaklarında bulunan verileri kullanan bir birim testi oluşturacağınız *app.config* dosya. Bu bölümde, yapacağız:

- Kaynakları bulunan veri oluşturma *app.config* dosya.

- Veri kaynakları, her veri kaynağı değerleri karşılaştırmak iki test yöntemlerini kullanın.

### <a name="to-create-a-microsoft-access-data-source"></a>Bir Microsoft Access veri kaynağını oluşturmak için

1. Adlı bir Microsoft Access veritabanı oluşturma *testdatasource.accdb*.

2. Bir tablo oluşturun ve adlandırın `MyDataTable` içinde *testdatasource.accdb*.

3. İki alanda oluşturma `MyDataTable` adlı `Arg1` ve `Arg2` kullanarak `Number` veri türü.

4. Beş varlıklara ekleyin `MyDataTable` için aşağıdaki değerlerle `Arg1` ve `Arg2`sırasıyla: (10,50), (3,2) (6,0) (0,8) ve (12312,1000).

5. Kaydet ve veritabanı kapatın.

6. Bağlantı dizesi, veritabanının konumunu gösterecek şekilde değiştirin. Değiştirin `Data Source` veritabanı konumunu gösterecek şekilde.

### <a name="to-create-a-microsoft-excel-data-source"></a>Bir Microsoft Excel veri kaynağı oluşturmak için

1. Adlı bir Microsoft Excel elektronik tablosu oluşturma *data.xlsx*.

2. Adlı bir e-tablosu oluşturmanız `Sheet1` , zaten mevcut değilse *data.xlsx*.

3. İki sütun üst bilgilerini oluşturabilir ve bunları `Val1` ve `Val2` içinde `Sheet1`.

4. Beş varlıklara ekleyin `Sheet1` için aşağıdaki değerlerle `Val1` ve `Val2`sırasıyla: (1,1), (2,2) (3,3) (4,4) ve (5,0).

5. Kaydet ve elektronik kapatın.

6. Bağlantı dizesi, elektronik konumunu işaret edecek şekilde değiştirin. Değiştirin `dbq` elektronik konumunu gösterecek şekilde.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>App.config veri kaynakları kullanarak bir birim test oluşturmak için

1. Birim testi için test projesi ekleyin.

2. Birim testi, otomatik olarak oluşturulan içeriğini aşağıdaki kodla değiştirin:

    ```csharp
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

3. DataSource özniteliği inceleyin. Ayar adları fark *app.config* dosya.

4. Çözümünüzü oluşturun ve MyTestMethod ve MyTestMethod2 testleri çalıştırın.

> [!IMPORTANT]
> Böylece bunlar dağıtım dizinine öğesindeki teste erişilebilir veri kaynakları gibi öğeleri dağıtın.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kod](../test/unit-test-your-code.md)
- [Nasıl yapılır: bir veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md)