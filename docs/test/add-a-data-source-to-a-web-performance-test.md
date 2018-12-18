---
title: Web performans testine veri kaynağı ekleme
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6d2ae95883884909641541e0efe6e4efbc7fe06a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065213"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Web performans testine veri kaynağı ekleme

Aynı teste farklı değerler örneğin sağlamak için parametreleri formunuza farklı değerler sağlamak için verileri bağlayın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Web performans testine veri bağlama](../test/media/web_test_databinding_conceptual.png)

Örnek ASP.NET uygulamasını kullanmak için ekleyeceğiz. Üç *.aspx* sayfaları – varsayılan sayfa, kırmızı sayfa ve mavi sayfa. Varsayılan sayfada kırmızı veya mavi ve bir Gönder düğmesi seçmek için bir radyo denetimi vardır. Diğer iki *.aspx* sayfaları çok basittir. Birinin kırmızı adlı bir etiketi vardır ve diğer mavi adlı bir etiketi vardır. Diğer sayfalardan biri görüntüleriz varsayılan sayfada Gönder'i seçtiğinizde. İndirebileceğiniz [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) örnek ya da yalnızca kendi web uygulamanızla birlikte izleyin.

![Test edilecek web uygulamasını çalıştırma](../test/media/web_test_databinding_runwebapp.png)

Çözümünüze web uygulamasına sayfalar arasında gözatar bir web performans testi de içermelidir.

![Web performans testi ile çözüm](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>SQL veritabanı oluşturma

1. Visual Studio Enterprise yoksa, buradan indirebilirsiniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) sayfası.

2. SQL veritabanı oluşturun.

     ![Yeni SQL veritabanı Ekle](../test/media/web_test_databinding_sql_addnewdb.png)

3. Bir veritabanı projesi oluşturun.

     ![Veritabanından yeni proje oluşturma](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Veritabanı projesine tablo ekleyin.

     ![Veritabanı projesine yeni bir tablo ekleyin](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Tabloya alanlar ekleyin.

     ![Tabloya alanlar ekleyin](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Veritabanı projesini yayımlayın.

     ![Çözüm Gezgini'nden veritabanı projesini yayımlayın](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Veri alanları ekleyin.

     ![Alanlara veri ekleyin](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

## <a name="add-the-data-source"></a>Veri kaynağı ekleme

1. Bir veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

2. Veri kaynağı türü seçin ve adlandırın.

     ![Veritabanı kaynak adı](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Bir bağlantı oluşturun.

     ![Yeni bir bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Bağlantı ayrıntılarını girin.

     ![SQL veritabanı bağlantı özelliklerini girin](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Testiniz için kullanmak istediğiniz tabloyu seçin.

     ![Renk tablosu veri kaynağı olarak ekleyin.](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Tablo teste bağlıdır.

     ![Web performans testine veri kaynağı düğümünü ekleyin](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Testi kaydedin.

## <a name="bind-the-data"></a>Veri bağlama

1. Bağlama **ColorName** alan.

     ![RadioButtonList1 değerine ColorName alanına bağlayın](../test/media/web_test_databinding_sql_binddatasource.png)

2. Açık *Local.testsettings* dosyası **Çözüm Gezgini** seçip **her veri kaynağı satırına bir çalıştırma** seçeneği.

     ![Test ayarları dosyasını düzenleme](../test/media/web_test_databinding_sql_testsettings.png)

3. Web performans testini kaydedin.

## <a name="run-the-test-with-the-data"></a>Testi veri ile çalıştırın.

1. Testi çalıştırın.

     ![Bağlama doğrulamak için web performans testini çalıştırın](../test/media/web_test_databinding_sql_runtest.png)

     İki çalıştırma, her veri satırı için görüntülenir. Çalışma1, sayfa için bir istek gönderir *Red.aspx*, ve çalışma 2 sayfa için bir istek gönderir *Blue.aspx*.

     ![Test çalıştırması sonuçları](../test/media/web_test_databinding_sql_runresults.png)

     Bir veri kaynağına bağlandığınızda, varsayılan yanıt URL'si kuralını ihlal edebilirsiniz. Bu durumda, çalışma 2 hatasına bekleyen kural neden olur *Red.aspx* özgün test kaydı, ancak veri bağlama şimdi sayfasından kendisine yönlendiren *Blue.aspx* sayfası.

2. Silerek doğrulama hatasını düzeltin **yanıt URL'si** doğrulama kuralı ve testi yeniden çalıştırarak.

     ![Yanıt URL doğruma kuralını Sil](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Web performans testi artık veri bağlamayı kullanarak başarılı olur.

     ![Test veri bağlamayı kullanarak başarılı olur.](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Soru - Yanıt

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>S: hangi veritabanlarını bir veri kaynağı olarak kullanabilir miyim?

**Y:** aşağıdakileri kullanabilirsiniz:

- Microsoft SQL Azure.

- Tüm Microsoft SQL Server 2005 veya sonraki sürümü.

- Microsoft SQL Server veritabanı dosyası (SQL Express dahil).

- Microsoft ODBC.

- OLE DB için .NET Framework sağlayıcısını kullanan Microsoft Access dosyası.

- Oracle 7.3, 8i, 9i veya 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>S: bir virgülle ayrılmış değer (CSV) metin dosyası veri kaynağı olarak nasıl kullanabilirim?

**Y:** burada nasıl:

1. Projelerinizin veritabanı yapılarını düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Yeni öğe için veri klasörü Ekle](../test/media/web_test_databinding_foldernewitem.png)

2. Bir metin dosyası oluşturun.

     ![Yeni metin dosyası ColorData.csv adı](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Metin dosyasını düzenleyin ve aşağıdakileri ekleyin:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. İçindeki adımları kullanın [veri kaynağı ekleme](#add-the-data-source), ancak veri kaynağı olarak CSV dosyasını seçin.

     ![Bir ad girin ve CSV dosyası seçin](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>S: var olan CSV dosyam sütun üstbilgilerini içermiyorsa?

**Y:** sütun başlıkları ekleyemezseniz CSV dosyasını veritabanı olarak değerlendirmek için şema açıklama dosyası kullanabilirsiniz.

1. Adlı yeni bir metin dosyası ekleyin *schema.ini*.

     ![Bir schema.ini dosyası ekleme](../test/media/web_test_databinding_schemafile.png)

2. Düzen *schema.ini* verilerinizin yapısını açıklayan bilgileri ekleyecek şekilde dosya. Örneğin, CSV dosyasını tanımlayan bir şema dosyası şuna benzeyebilir:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Teste veri kaynağı ekleyin.

     ![Web performans testine veri kaynağı ekleme](../test/media/web_test_databinding_sql_adddatasource.png)

4. Kullanıyorsanız, bir *schema.ini* dosya öğesini **veritabanı** (CSV dosyası değil) gibi veri kaynağını seçin ve adlandırın.

     ![Veritabanı veri kaynağı ekleme](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Yeni bir bağlantı oluşturun.

     ![Yeni bir bağlantı seçin](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. OLE DB için .NET Framework Veri Sağlayıcısı'nı seçin.

     ![.NET framework OLE DB veri sağlayıcısı seçin](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Seçin **Gelişmiş**.

     ![Gelişmiş'i seçin](../test/media/web_test_databinding_advanced.png)

8. Sağlayıcı özelliği için Microsoft.Jet.OLEDB.4.0'ı seçin ve ardından **genişletilmiş özellikler** metne; HDR = NO.

     ![Gelişmiş özellikleri uygulama](../test/media/web_test_databinding_advancedproperties.png)

9. Şema dosyasının bulunduğu klasörün adını yazın ve bağlantınızı sınayın.

     ![Veri klasörünün yolunu girin](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Kullanmak istediğiniz CSV dosyasını seçin.

     ![Metin dosyasını seçin](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Tamamladıktan sonra CSV dosyası tablo olarak görünür.

     ![Test etmek için eklenen veri kaynağı](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>S: bir XML dosyası veri kaynağı olarak nasıl kullanabilirim?

**Y:** Evet.

1. Projelerinizin veritabanı yapılarını düzenlemek ve bir öğe eklemek için bir klasör oluşturun.

     ![Yeni öğe için veri klasörü Ekle](../test/media/web_test_databinding_foldernewitem.png)

2. Bir XML dosyası oluşturun.

     ![ColorData.xml dosyası ekleme](../test/media/web_test_databinding_additemxmlfile.png)

3. XML dosyasını düzenleyin ve verilerinizi ekleyin:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. İçindeki adımları kullanın [veri kaynağı ekleme](#add-the-data-source), ancak veri kaynağı olarak XML dosyasını seçin.

     ![Bir ad girin ve XML dosyası seçin](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>SOAP kullanan bir web hizmeti isteğine veri bağlama ekleyebilir miyim?

**Y:** Evet, SOAP XML el ile değiştirmeniz gerekir.

1. İstek ağacında ve Özellikler penceresinde web hizmeti isteğini seçin, dize gövdesi özelliğinden üç noktayı (...) seçin.

     ![Web hizmeti dize gövdesi Düzenle](../test/media/web_test_databinding_webservicerequest.png)

2. SOAP'daki değerleri, aşağıdaki sözdizimini kullanarak veri bağlama değerleriyle değiştirin:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Örneğin, aşağıdaki kodu varsa:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Bunu bu değiştirebilirsiniz:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Testi kaydedin.