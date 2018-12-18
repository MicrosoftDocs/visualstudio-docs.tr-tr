---
title: 'İzlenecek yol: Bir işlemde veri kaydetme'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f9b4fad02b6b0d8324e13d4465f4602c16ce85ba
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305058"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>İzlenecek yol: Bir işlemde veri kaydetme

Bu izlenecek yol kullanarak bir işlemde veri kaydetme gösterilmektedir <xref:System.Transactions> ad alanı. Bu kılavuzda, bir Windows Forms uygulaması oluşturacaksınız. Northwind örnek veritabanındaki iki tablo için bir veri kümesi oluşturmak için veri kaynağı Yapılandırma Sihirbazı'nı kullanacaksınız. Bir Windows forma veri sınırı denetimleri ve veritabanının bir TransactionScope içinde güncelleştirilecek BindingNavigator'ın Kaydet düğmesi için kod değiştireceksiniz ekleyeceksiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. Visual Studio yükleyicisi, SQL Server Express LocalDB parçası olarak yüklenebilir **.NET Masaüstü geliştirmesinden** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Bir Windows Forms uygulaması oluşturma

İlk adım oluşturmaktır bir **Windows Forms uygulaması**.

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **SavingDataInATransactionWalkthrough**ve ardından **Tamam**.

     **SavingDataInATransactionWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma

Bu adımı kullanan **veri kaynağı Yapılandırma Sihirbazı** dayalı bir veri kaynağını oluşturmak için `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

3.  Üzerinde **bir veri kaynağı türü seçin** ekranındayken **veritabanı**ve ardından **sonraki**.

4.  Üzerinde **veri bağlantınızı seçin** aşağıdakilerden birini ekran yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu ve Northwind veritabanına bağlantı oluşturun.

5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** ekranındayken **sonraki**.

7.  Üzerinde **veritabanı nesnelerinizi seçin** ekranında, **tabloları** düğümü.

8.  Seçin `Customers` ve `Orders` tablolar ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve `Customers` ve `Orders` tablolar görünür **veri kaynakları** penceresi.

## <a name="add-controls-to-the-form"></a>Formu için denetimler ekleme

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.

1. İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğümü.

2. Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.

   A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

3. İlgili sürükleyin **siparişler** düğümü (ana **siparişler** düğümü ancak ilgili alt tablo düğümünün altındaki **faks** sütun) aşağıdaki forma  **CustomersDataGridView**.

   A <xref:System.Windows.Forms.DataGridView> formda görünür. Bir `OrdersTableAdapter` ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions derlemesine bir başvuru ekleyin

İşlemleri kullanma <xref:System.Transactions> ad alanı. El ile eklemeniz gerekir. Bu nedenle varsayılan olarak, system.transactions derlemeye bir proje başvurusu eklenmedi.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL dosyasına bir başvuru eklemek için

1.  Üzerinde **proje** menüsünde **Başvuru Ekle**.

2.  Seçin **System.Transactions** (üzerinde **.NET** sekmesinde) ve ardından **Tamam**.

     Bir başvuru **System.Transactions** projeye eklenir.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator'ın saveItem düğmesinde kodu değiştirin

Varsayılan olarak eklenen formunuza bırakılan ilk tablo için kod `click` olayını Kaydet düğmesine <xref:System.Windows.Forms.BindingNavigator>. Herhangi bir ek tablolar güncelleştirmek için kodu el ile eklemeniz gerekir. Bu kılavuz için biz varolan kaydetme kodunun kaydetme yeniden düzenleme düğmenin tıklama olay işleyicisi. Ayrıca belirli bir güncelleştirmeyi işlevi mi satır eklendiğinde veya silindiğinde uygun olarak sağlamak için birkaç hakkında daha fazla yöntem oluşturacağız.

### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kodu Kaydet değiştirmek için

1.  Seçin **Kaydet** düğmesini **CustomersBindingNavigator** (düğme disket simgesi ile).

2.  Değiştirin `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

İlgili veri değişiklikleri mutabık kılma sırasını aşağıdaki gibidir:

-   Alt kayıtları silin. (Bu durumda, kayıtları silme `Orders` tablo.)

-   Üst kayıtlar silin. (Bu durumda, kayıtları silme `Customers` tablo.)

-   Üst kayıtlar ekler. (Bu durumda, kayıtları eklemek `Customers` tablo.)

-   Alt kayıtları ekleyin. (Bu durumda, kayıtları eklemek `Orders` tablo.)

### <a name="to-delete-existing-orders"></a>Mevcut siparişlerin silmek için

-   Aşağıdaki `DeleteOrders` yönteme **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Mevcut müşteriler silmek için

-   Aşağıdaki `DeleteCustomers` yönteme **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için

-   Aşağıdaki `AddNewCustomers` yönteme **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için

-   Aşağıdaki `AddNewOrders` yönteme **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Tuşuna **F5** uygulamayı çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir işlemi kullanarak veri kaydetme](../data-tools/save-data-by-using-a-transaction.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)