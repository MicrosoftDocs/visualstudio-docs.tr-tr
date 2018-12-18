---
title: Bir tasarımcı kullanarak bir SQL veritabanı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0ef261ec4ea803dcfc42b6151a5c828d5b03811a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860337"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Bir tasarımcı kullanarak bir SQL veritabanı oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tablo ekleme ve SQL Server Express LocalDB içinde yerel veritabanı dosyası oluşturmak için Visual Studio kullanarak sütun tanımlama gibi temel görevleri gerçekleştirebilirsiniz. Bu izlenecek yolu tamamladığınızda, gereken diğer izlenecek yollar için bir yerel veritabanınızı bir başlangıç noktası olacak şekilde kullanarak daha fazla gelişmiş özelliği keşfedebilirsiniz.  
  
 SQL Server Management Studio (ayrı bir indirme) ya da Transact-SQL deyimlerinde kullanarak bir veritabanı oluşturabilirsiniz **SQL Server Nesne Gezgini** Visual Studio'da araç penceresi.  
  
 Bu izlenecek yol boyunca, aşağıdaki görevler hakkında bilgi edineceksiniz:  
  
-   [Bir proje ve yerel veritabanı dosyası oluştur](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [Tablolar, sütunlar, birincil anahtarlar ve yabancı anahtarlar oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [Tabloları verilerle doldurma](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için SQL Server veri araçları sahip olun. Üzerinde **görünümü** menüsünde görmeniz **SQL Server Nesne Gezgini**. Yoksa, Git **Program Ekle veya Kaldır**, tıklayın **Visual Studio 2015**seçin **değişiklik**ve yanındaki kutuyu işaretleyin **SQL Server veri Araçları**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> Bir proje ve yerel veritabanı dosyası oluştur  
  
#### <a name="to-create-a-project-and-a-database-file"></a>Bir proje ve yerel veritabanı dosyası oluşturmak için  
  
1. Adlı bir Windows Forms projesi oluşturun `SampleDatabaseWalkthrough`.  
  
2. Menü çubuğunda, seçin **proje** > **Yeni Öğe Ekle**.  
  
3. Öğe şablonları listesinde, aşağı kaydırın ve **hizmet tabanlı veritabanı**.  
  
    ![Öğe şablonları iletişim kutusunda](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. Veritabanı adı **SampleDatabase**ve ardından **Ekle** düğmesi.  
  
5. Varsa **veri kaynakları** penceresi açık değilse, Shift + Alt + D tuşlarını seçerek veya menü çubuğundan seçerek açın **görünümü** > **diğer Windows**  >  **Veri kaynakları**.  
  
6. İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** bağlantı.  
  
7. İçinde **veri kaynağı Yapılandırma Sihirbazı**seçin **sonraki** düğmesini dört kez varsayılan ayarları kabul edin ve ardından **son** düğmesi.  
  
   Veritabanı için özellikler penceresini açarak bağlantı dizesini ve birincil .mdf dosyasının konumunu görüntüleyebilirsiniz. Veritabanı dosyası proje klasöründe olduğunu görürsünüz.  
  
-   Visual Studio'da **görünümü** > **SQL Server Nesne Gezgini** Bu pencere hala açık değilse. Özellikler penceresini genişleterek açmak **veri bağlantıları** düğüm, Sampledatabase.mdf'nin kısayol menüsünü açarak ve ardından **özellikleri**.  
  
-   Alternatif olarak, seçebileceğiniz **görünümü** > **Sunucu Gezgini**, bu pencere hala açık değilse. Özellikler penceresini genişleterek açmak **veri bağlantıları** düğümü. Sampledatabase.mdf'nin kısayol menüsünü açın ve ardından **özellikleri**.  
  
##  <a name="BKMK_CreateNewTbls"></a> Tablolar, sütunlar, birincil anahtarlar ve yabancı anahtarlar oluşturma  
 Bu bölümde birkaç tablo, her tabloda bir birincil anahtar ve birkaç örnek veri satırı oluşturacaksınız. Sonraki izlenecek yolda, bu bilgilerin uygulamada nasıl görüneceği hakkında bir fikir elde edeceksiniz. Ayrıca, bir tablodaki kayıtların diğer tablodaki kayıtlara nasıl karşılık gelebileceğini belirtmek için yabancı anahtar da oluşturacaksınız.  
  
#### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için  
  
1.  İçinde **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**, genişletme **veri bağlantıları** düğümünü ve ardından **SampleDatabase.mdf**düğümü.  
  
2.  Kısayol menüsünü açın **tabloları**ve ardından **Yeni Tablo Ekle**.  
  
     **Tablo Tasarımcısı** açılır ve oluşturmakta olduğunuz tablodaki tek bir sütunu temsil eden tek bir varsayılan satır içeren bir kılavuz gösterir. Kılavuza satırlar ekleyerek, tabloda sütunlar ekleyeceksiniz.  
  
3.  Kılavuzda, aşağıdaki girişlerin her biri için bir satır ekleyin:  
  
    |Sütun adı|Veri türü|Null'lere izin ver|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|  
    |`CompanyName`|`nvarchar(50)`|False (işaretsiz)|  
    |`ContactName`|`nvarchar (50)`|True (seçili)|  
    |`Phone`|`nvarchar (24)`|True (seçili)|  
  
4.  Kısayol menüsünü açın `CustomerID` satır ve ardından **birincil anahtarı Ayarla**.  
  
5.  Varsayılan satır için kısayol menüsünü açın ve ardından **Sil**.  
  
6.  Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Müşteriler tablosunu adlandırın:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     Bunun gibi bir şey görmeniz gerekir:  
  
     ![Tablo Tasarımcısı](../data-tools/media/raddata-table-designer.png "raddata Tablo Tasarımcısı")  
  
7.  Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.  
  
8.  İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.  
  
     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.  
  
#### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için  
  
1.  Başka bir tablo ekleyin ve sonra aşağıdaki tabloda her giriş için bir satır ekleyin:  
  
    |Sütun adı|Veri türü|Null'lere izin ver|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (işaretsiz)|  
    |`CustomerID`|`nchar(5)`|False (işaretsiz)|  
    |`OrderDate`|`datetime`|True (seçili)|  
    |`OrderQuantity`|`int`|True (seçili)|  
  
2.  Ayarlama **OrderID** birincil anahtar ve ardından varsayılan satırı silin.  
  
3.  Betik bölmesindeki ilk satırı aşağıdaki örnekle eşleşecek şekilde değiştirerek Siparişler tablosunu adlandırın:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.  
  
5.  İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.  
  
     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.  
  
#### <a name="to-create-a-foreign-key"></a>Yabancı anahtar oluşturmak için  
  
1.  Kılavuz sağ tarafında bulunan bağlam bölmesinde, kısayol menüsünü açın **yabancı anahtarlar**ve ardından **yeni yabancı anahtar Ekle**aşağıdaki çizimde gösterildiği gibi.  
  
     ![Tablo Tasarımcısı'nda bir yabancı anahtar ekleme](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  Görüntülenen metin kutusunda, yerine **ToTable** ile `Customers`.  
  
3.  T-SQL bölmesinde son satırı aşağıdaki örnekle eşleşecek şekilde güncelleştirin:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  Sol alt köşesindeki **Tablo Tasarımcısı**seçin **güncelleştirme** düğmesi.  
  
5.  İçinde **veritabanı güncelleştirmelerini Önizle** iletişim kutusunda **veritabanını Güncelleştir** düğmesi.  
  
     Değişiklikleriniz yerel veritabanı dosyasına kaydedildi.  
  
##  <a name="BKMK_Populating"></a> Tabloları verilerle doldurma  
  
#### <a name="to-populate-the-tables-with-data"></a>Tabloları veriyle doldurmak için  
  
1.  İçinde **Sunucu Gezgini** veya **SQL Server Nesne Gezgini**, örnek veritabanları düğümünü genişletin.  
  
2.  Kısayol menüsünü açın **tabloları** düğümünü **Yenile**ve ardından **tabloları** düğümü.  
  
3.  Müşteriler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini Göster**.  
  
4.  En az üç müşteriye istediğiniz verileri ekleyin.  
  
     Müşteri kimliklerini beş karakterli olarak istediğiniz gibi belirtebilirsiniz, ancak en azından bu yordamda daha sonra kullanmak üzere hatırlayabileceğiniz bir kimlik olmalıdır.  
  
5.  Siparişler tablosu için kısayol menüsünü açın ve ardından **tablo verilerini Göster**.  
  
6.  En az üç sipariş için veri ekleyin.  
  
    > [!IMPORTANT]
    >  Tüm sipariş kimlikleri ve sipariş miktarlarının tam sayılar olduğundan ve her müşteri kimliğinin Müşteriler tablosunun CustomerID sütununda belirttiğiniz bir değerle eşleştiğinden emin olun.  
  
7.  Menü çubuğunda, seçin **dosya** > **Tümünü Kaydet**.  
  
8.  Menü çubuğunda, seçin **dosya** > **çözümü Kapat**.  
  
    > [!NOTE]
    >  En iyi uygulama yöntemi olarak, az önce oluşturduğunuz veritabanı dosyasını kopyalayarak ve daha sonra kopyayı diğer bir konuma yapıştırarak ya da kopyaya başka bir ad vererek yedekleyebilirsiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bazı örnek verilerle bir yerel veritabanı dosyasına sahip olduğunuza göre veritabanı görevlerini gösteren izlenecek yollar tamamlayabilirsiniz.

