---
title: Bir veritabanı dosyası oluşturma ve Tablo Tasarımcısı kullanma
description: Bu öğretici Visual Studio'daki tablo tasarımcısını kullanarak tablolar ve yabancı anahtarlar bir veritabanına ekleme işlemi açıklanmaktadır. Ayrıca, grafik arabirim üzerinden veri ekleme gösterir.
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c071daeaa1ffe10aa9de995b375e33b76b358da7
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159873"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Bir veritabanı oluşturun ve Visual Studio'da tablo ekleme

Visual Studio, SQL Server Express LocalDB içinde yerel veritabanı dosyası oluşturmak için kullanabilirsiniz. Transact-SQL deyimlerinde yürüterek bir veritabanı oluşturabilirsiniz **SQL Server Nesne Gezgini** Visual Studio'da araç penceresi. Bu konu başlığında, oluşturacağız bir *.mdf* dosya ve tablo tasarımcısını kullanarak tablolar ile anahtarlar ekleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için isteğe bağlı olmalıdır **veri depolama ve işleme** Visual Studio'da yüklü iş yükü. Yüklemek için açık **Visual Studio yükleyicisi** ve **iş yükleri** sekmesi. Altında **Web ve bulut**, seçin **veri depolama ve işleme**. Seçin **Değiştir** düğmesini iş yükünü Visual Studio'ya ekleyin.

## <a name="create-a-project-and-a-local-database-file"></a>Bir proje ve yerel veritabanı dosyası oluştur

1. Adlı bir Windows Forms projesi oluşturun **SampleDatabaseWalkthrough**.

2. Menü çubuğunda, seçin **proje** > **Yeni Öğe Ekle**.

3. Öğe şablonları listesinde, aşağı kaydırın ve **hizmet tabanlı veritabanı**.

     ![Öğe şablonları iletişim kutusu](../data-tools/media/raddata-vsitemtemplates.png)

4. Veritabanı adı **SampleDatabase**ve ardından **Ekle** düğmesi.

### <a name="add-a-data-source"></a>Veri Kaynağı Ekle

1. Varsa **veri kaynakları** penceresi açık değilse, tuşlarına basarak açın **Shift**+**Alt**+**D** veya seçme **Görünümü** > **diğer Windows** > **veri kaynakları** menü çubuğundaki.

1. İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** bağlantı.

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

1. Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı** seçip **sonraki**.

1. Üzerinde **veritabanı modeli seçin** sayfasında **sonraki** (veri kümesi) varsayılanı kabul edin.

1. Üzerinde **veri bağlantınızı seçin** sayfasında **SampleDatabase.mdf** aşağı açılan listede dosya ve ardından **sonraki**.

1. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

1. Bir **veritabanı nesnelerinizi seçin** sayfasında, veritabanı belirten bir ileti, herhangi bir nesne içermiyor göreceksiniz. Seçin **son**.

### <a name="view-properties-of-the-data-connection"></a>Veri bağlantısı özelliklerini görüntüleme

Bağlantı dizesini görüntüleyebileceğiniz *SampleDatabase.mdf* veri bağlantısı Özellikler penceresini açarak dosya:

- Visual Studio'da **görünümü** > **SQL Server Nesne Gezgini** Bu pencere hala açık değilse. Özellikler penceresini genişleterek açmak **veri bağlantıları** düğümü için kısayol menüsünü açarak, *SampleDatabase.mdf*, belirledikten sonra **özellikleri**.

- Alternatif olarak, seçebileceğiniz **görünümü** > **Sunucu Gezgini**, bu pencere hala açık değilse. Özellikler penceresini genişleterek açmak **veri bağlantıları** düğümü. Kısayol menüsünü açın *SampleDatabase.mdf*ve ardından **özellikleri**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tablo tasarımcısını kullanarak tablolar ile anahtarlar oluşturma

Bu bölümde, iki tablo, her bir tabloyu ve birkaç satırlık örnek verileriniz birincil bir anahtar oluşturmak. Ayrıca, bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık gelen belirtmek için yabancı anahtar da oluşturacaksınız.

### <a name="create-the-customers-table"></a>Müşteriler tablosu oluşturma

1. İçinde **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**, genişletme **veri bağlantıları** düğümünü ve ardından **SampleDatabase.mdf**düğümü.

2. Kısayol menüsünü açın **tabloları**ve ardından **Yeni Tablo Ekle**.

     **Tablo Tasarımcısı** açılır ve oluşturmakta olduğunuz tablodaki tek bir sütunu temsil eden tek bir varsayılan satır içeren bir kılavuz gösterir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.

3. Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:

    |Sütun adı|Veri türü|Null'lere izin ver|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|
    |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|
    |`ContactName`|`nvarchar (50)`|True (seçili)|
    |`Phone`|`nvarchar (24)`|True (seçili)|

4. Kısayol menüsünü açın `CustomerID` satır ve ardından **birincil anahtarı Ayarla**.

5. Varsayılan satır için kısayol menüsünü açın ve ardından **Sil**.

6. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Bunun gibi bir şey görmeniz gerekir:

    ![Tablo Tasarımcısı](../data-tools/media/raddata-table-designer.png)

7. Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.

8. İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.

    Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

### <a name="create-the-orders-table"></a>Siparişler tablosu oluşturma

1. Başka bir tablo ekleyin ve sonra aşağıdaki tabloda her giriş için bir satır ekleyin:

    |Sütun adı|Veri türü|Null'lere izin ver|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (işaretsiz)|
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|
    |`OrderDate`|`datetime`|True (seçili)|
    |`OrderQuantity`|`int`|True (seçili)|

2. Ayarlama **OrderID** birincil anahtar ve ardından varsayılan satırı silin.

3. Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Siparişler tablosunu adlandırın:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4. Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.

5. İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.

    Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

### <a name="create-a-foreign-key"></a>Yabancı anahtar oluşturma

1. Kılavuz sağ tarafında bulunan bağlam bölmesinde, kısayol menüsünü açın **yabancı anahtarlar**ve ardından **yeni yabancı anahtar Ekle**aşağıdaki çizimde gösterildiği gibi.

     ![Tablo Tasarımcısı'nda bir yabancı anahtar ekleme](../data-tools/media/foreignkey.png)

2. Görüntülenen metin kutusunda, yerine **ToTable** ile **müşteriler**.

3. T-SQL bölmesinde son satırı aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.

5. İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.

    Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.

## <a name="populate-the-tables-with-data"></a>Tabloları verilerle doldurma

1. İçinde **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**, örnek veritabanları düğümünü genişletin.

2. Kısayol menüsünü açın **tabloları** düğümünü **Yenile**ve ardından **tabloları** düğümü.

3. Müşteriler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini Göster**.

4. Bazı müşteriler için istediğiniz verileri ekleyin.

    Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.

5. Siparişler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini Göster**.

6. Bazı sipariş verileri ekleyin.

    > [!IMPORTANT]
    > Tüm sipariş kimlikleri ve sipariş miktarlarının tam sayılar olduğundan ve her bir müşteri Kimliğini belirtilen bir değerle eşleştiğinden emin olun **CustomerID** Müşteriler tablosundaki sütun.

7. Menü çubuğunda, seçin **dosya** > **Tümünü Kaydet**.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](accessing-data-in-visual-studio.md)