---
title: SQL Server R ile tümleştirme
description: Visual Studio oluşturma ve çalıştırma R gelen SQL sorguları ve saklı yordamlar ile çalışmak R özelliği destekler.
ms.date: 06/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 3b9fa1f675754257a2278c7282c45d9816c034cd
ms.sourcegitcommit: 4e605891d0dfb3ab83150c17c074bb98dba29d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36946919"
---
# <a name="work-with-sql-server-and-r"></a>SQL Server ve R ile çalışma

SQL Server için Visual Studio'nun mükemmel desteği veri bilimcilerine R ve SQL veritabanları oluşturmak ve SQL sorguları çalıştırmak için ve saklı yordamlar çalışma olanağı üzerinden çalışmak yardımcı olur.

> [!Note]
> SQL ve R ile birlikte çalışmak için SQL Server veri araçları yüklü olması gerekir:
> - Visual Studio 2017: Visual Studio yükleyicisi çalıştırın ve veri depolama ve SQL Server veri araçları içerir işleme iş yükünü seçin.
> - Visual Studio 2015: yönergelerini izleyin [SQL Server veri araçları indirme](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![video kamera simgesine film](../install/media/video-icon.png "bir videoyu izleyin") | [(Youtube.com) bir video izlemek](https://www.youtube.com/watch?v=n4AYr0QIwdQ) SQL Server ve R (3 m 03s) genel bakış. |

## <a name="create-and-run-sql-queries"></a>SQL sorguları oluşturun ve çalıştırın

RTVS Aradığınız sonuçları elde edene kadar yinelemeli olarak ayrı bir bağlamda SQL sorguları geliştirmek sağlayarak R projelere ekleme SQL sorguları destekler.

Bir SQL sorgu dosyası eklemek için Çözüm Gezgini'nde, Seç'nde projeye sağ **Ekle** > **yeni öğe**seçip **SQL sorgusu** dosya türü:

![SQL sorgusu öğesi için bir proje ekleyin](media/sql-add-item.png)

Bu komut dosyası ve SQL sorguları çalıştırma yeteneğini için IntelliSense sağlar Visual Studio'nun Transact-SQL Düzenleyicisi'nde açar. Bu özellikleri çalışacak şekilde Düzenleyicisi araç çubuğunda Bağlan düğmesini kullanarak bir veritabanına bağlanmak veya bir sorgu çalıştırmayı deneyin gerekir (**Ctrl**+**Shift**+**E** , ayrıca çalıştığı bir seçimde). Her iki durumda da, bağlantı iletişim kutusunu açar:

![SQL Bağlantısı iletişim kutusu](media/sql-connection-dialog.png)

Bağlantı kurulduktan sonra sorguları çalıştırmak ve sonuçları bakın:

![SQL penceresi sorgu sonuçları](media/sql-query-results.png)

Sorgu ve bir sorgu hata ayıklayıcı için yürütme planı görüntüleme gibi diğer özelliklerin çeşitli Transact-SQL Düzenleyicisi'ni destekler.
Daha fazla bilgi için bkz: [Transact-SQL Düzenleyicisi'ni kullanma düzenleme ve komut dosyaları yürütme](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="work-with-sql-server-stored-procedures"></a>SQL Server saklı yordamlar ile çalışma

[SQL Server R Hizmetleri](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) saklı yordamı katıştırmak ve bir T-SQL R kodu çalıştırma (SQL Server 2016 ve üzeri) sağlar. Bir SQL Server bilgisayarında R kodu çalıştırmak, bir SQL sorgusundan döndürülen verileri çalıştırmak ve başka SQL tarafından işlenen veya istemciye döndürülen bir SQL sonuç kümesi oluşturur.

RTVS, aşağıdaki bölümlerde açıklandığı gibi tek bir SQL deyimi içinde SQL ve R kod birleştirmenin aksi yönetilmeleri ve hataya yatkın işlemini basitleştirir:

- [Bir veritabanı bağlantısı Ekle](#add-a-database-connection)
- [Yazma ve SQL saklı yordamı test etme](#write-and-test-a-sql-stored-procedure)
- [SQL saklı yordamı yayımlama](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![video kamera simgesine film](../install/media/video-icon.png "bir videoyu izleyin") | [(Youtube.com) bir video izlemek](https://www.youtube.com/watch?v=dFKIT2OitWQ) bakış R ve SQL saklı yordamları (6 m 09s) için. |

### <a name="add-a-database-connection"></a>Bir veritabanı bağlantısı Ekle

1. Seçin **R Araçları** > **veri** > **veritabanı bağlantı Ekle** ortaya çıkarmak için **bağlantı özelliklerini** iletişim kutusu. Burada belirttiğiniz (Bu durumda SQL Server) veri kaynağının adını, ad sunucusu, kimlik doğrulama modu ve veritabanının adı. Seçin **Bağlantıyı Sına** iletişim kutusunu kapatmadan önce girişinizi doğrulayın.

    ![SQL bağlantı iletişim kutusu](media/sql-connection-string-dialog.png)

1. Seçtiğinizde, bundan sonra **Tamam** geçerli bir bağlantı ile Visual Studio adlı bir bağlantı dizesi oluşturur `dbConnection` yeni *ayarlar. R* dosya. RTVS (çalışır) otomatik olarak kaynakları R betiklerini bağlantısından hemen kullanabilmek için bu dosyayı:

![SQL Settings.R dosyası](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Yazma ve SQL saklı yordamı test etme

Yeni bir SQL saklı yordamı eklemek için projenize sağ tıklayın, seçin **Ekle** > **yeni öğe**seçin **SQL saklı yordamı r** şablonları listesinden bir ad verin ve seçin **Tamam**. Varsayılan dosya adı *SqlSProc.R*; okuma, filename kolaylığı için *StoredProcedure.R* bu bölümün geri kalanında kullanılır. Birden çok saklı yordamlar varsa, her dosyanın benzersiz bir dosya adı olmalıdır.

RTVS saklı yordamı için üç dosyaları oluşturur: bir *. R* R kodunuz için dosyayı bir *. Query.SQL* SQL kod dosyası ve bir *. Template.SQL* iki birleştirir dosya. Bunlar alt olarak iki görünür Çözüm Gezgini'nde ikinci *. R* dosyası:

![Çözüm Gezgini SQL saklı yordamı r görünümünü genişletilmiş](media/sql-solution-explorer-expanded.png)

*. R* dosyası (*StoredProcedure.R* Bu örnekte) burada R kodu yazdığınız şeydir. Varsayılan içeriği şunlardır:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Kısaca, kod olarak adlandırılan bir R dataframe alır `InputDataSet` ve onun sonuçları döndürür `OutputDataSet`, yalnızca çıktı girdisi kopyalama şablon koduna sahip.

> [!Note]
> Bu dataframes adlarını denetlediği `@input_data_1_name` ve `@output_data_1_name` çağrısı parametrelerinde `sp_execute_external_script` sistem saklı yordamı. Bu arama kuralı tasarımını hakkında daha fazla ayrıntı ve bazı kullanım örnekleri için bkz: [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Diğer oluşturulan kod (açıklamaları) kullanan bir küçük test komut dosyası sağlar [RODBC paket](https://cran.r-project.org/web/packages/RODBC/index.html) SQL Server için bir SQL deyimi iletmek için çalıştırın ve bir R dataframe ayarlamak sonucu almak. SQL Server'dan alma etkileşimli olarak R kodunuzu sonucu karşı yazmak için bu test kod kümesi açıklamadan çıkarın.

*. Query.SQL* dosyası (*StoredProcedure.Query.sql* Bu örnekte), yazma ve verileri üreten SQL sorgu test yerdir `InputDataSet`. Bu *.sql* Dosyası Düzenleyicisi tüm olağan Transact-SQL özellikleri sağlar.

İle SQL kodunuzu memnun kaldıysanız sonra sürükleyerek R kodu ile tümleştirmek *.sql* açık Düzenleyicisi üzerine dosya *. R* dosya. Aşağıdaki görüntüde *StoredProcedure.Query.sql* noktaya sürüklenip *StoredProcedure.R* virgülle sonra `sqlQuery(channel, )`:

![R dize değişkeni SQL dosyaya okuma](media/sql-reference-sql-file-from-r.png)

Gördüğünüz gibi bu basit adımı açmak için R kodu otomatik olarak oluşturur. *.sql* dosya, bir dizeye içeriğini okumak ve SQL sunucusuna göndermek için RODBC paketi iletin.

Etkileşimli olarak işleyen yazma R kodu artık `InputDataSet` dataframe istediğiniz gibi. R Kod düzenleyicisinde seçin yalnızca ve göndermeden unutmayın [etkileşimli pencere](interactive-repl-for-r-in-visual-studio.md) basarak **Ctrl**+**Enter**.

*. Template.SQL* dosyası (*StoredProcedure.Template.sql* Bu örnekte), son olarak, SQL saklı yordamı oluşturmak için şablon içerir:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` Yer tutucu içeriğine göre değiştirilir *. R* dosyası (örneğin, *StoredProcedure.R*).
- `_INPUT_QUERY_` Yer tutucu içeriğine göre değiştirilir *. Query.SQL* dosyası (örneğin, *StoredProcedure.Query.sql*).
- Düzen `WITH RESULT SETS` bir saklı yordamdan döndürülen sonuç şeması açıklamak için yan tümcesi. Özellikle sütunlarından tanımlamak `OutputDataSet` saklı yordamı çağırana döndürmek istediğiniz dataframe.

Örneğin, aşağıdaki sorgu için:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Aşağıdaki kullanırsınız `WITH RESULT SETS` dönüş değerlerini veri türlerini belirtmek için yan tümcesi:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>SQL saklı yordamı yayımlama

1. Seçin **R Araçları** > **veri** > **Yayımla ile seçenekleri** menü komutu.
1. Görüntülenen iletişim kutusunda, değiştirmek **Yayımla:** için **veritabanı**, hedef belirtin, seçin **Yayımla**, RTVS oluşturur ve saklı yordam yayımlar ve:

    ![Saklı yordam iletişim yayımlama](media/sql-publish-with-options.png)

1. Bir projedeki tüm depolanmış yordamları yayımlamak için kullanabileceğiniz **R Araçları** > **veri** > **saklı yordamlar yayımlama** de komutu Çözüm Gezgini'nde projeye sağ tıklattığınızda kullanılabilir.

> [!Tip]
> Visual Studio'da açın SQL Server Nesne Gezgini varsa, yayımlanan saklı yordam görünür **programlama** > **saklı yordamlar** veritabanınızın klasör. Ayrıca nesne Gezgini'nden sağ tıklayıp seçerek çalıştırabilirsiniz **yordamı Yürüt**, veya ondan etkileşimli olarak arayarak bir *.sql* sorgu penceresi.
