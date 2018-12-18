---
title: Bir veritabanına (birden çok tablo) veri kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4e5ca1e9903089cbcc9daf99e8c8d49d170b1c8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388825"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Bir veritabanına (birden çok tablo) veri kaydetme

Uygulama geliştirmede en sık karşılaşılan senaryolardan biri, bir Windows uygulamasındaki bir formdaki verileri görüntülemek, verileri düzenleme ve güncelleştirilmiş veriyi veritabanına geri gönder sağlamaktır. Bu izlenecek yolda kayıtlarını düzenleyin ve değişiklikleri veritabanına geri kaydedin gösterir ve ilgili iki tablodan verileri görüntüleyen bir form oluşturur. Bu örnekte `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.

Çağırarak veritabanına uygulamanızdaki verileri kaydedebilirsiniz `Update` TableAdapter bağdaştırıcısının yöntemi. Tablodan sürüklediğinizde **veri kaynakları** forma, verileri kaydetmek için gereken kod penceresi otomatik olarak eklenir. Bir forma eklenmiş herhangi bir ek tablolar bu kodu el ile eklenmesi gerekir. Bu izlenecek yol, birden fazla tablodan güncelleştirmeleri kaydetmek için kod ekleme işlemi gösterilmektedir.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Yeni bir oluşturma **Windows Forms uygulaması** proje.

-   Oluşturma ve bir veri kaynağı ile uygulamanızda yapılandırma [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png).

-   Ayarı'ndeki öğelerin kullanımını denetler [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window). Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Öğe sürükleyerek veriye bağlı denetimler oluşturma **veri kaynakları** formunuza penceresi.

-   Birkaç kayıt kümesindeki her bir tablodaki değiştirme.

-   Güncelleştirilmiş veri kümesinde veritabanına geri göndermek için kod değiştirme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım oluşturmaktır bir **Windows Forms uygulaması**. Projeye bir ad atamak Bu adımda isteğe bağlıdır, ancak projeyi daha sonra kaydetmek çünkü biz bunu bir ad verin.

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **UpdateMultipleTablesWalkthrough**ve ardından **Tamam**.

     **UpdateMultipleTablesWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-the-data-source"></a>Veri kaynağı oluşturma

Bu adımı kullanarak Northwind veritabanına bir veri kaynağı oluşturur. **veri kaynağı Yapılandırma Sihirbazı**. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

1. Üzerinde **veri** menüsünde **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi açılır.

2. İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

3. Üzerinde **bir veri kaynağı türü seçin** ekranındayken **veritabanı**ve ardından **sonraki**.

4. Üzerinde **veri bağlantınızı seçin** ekranında, aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    -   Seçin **yeni bağlantı** açmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5. Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet**seçin **sonraki**.

7. Üzerinde **veritabanı nesnelerinizi seçin** ekranında, **tabloları** düğümü.

8. Seçin **müşteriler** ve **siparişler** tablolar ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve tablolar görünür **veri kaynakları** penceresi.

## <a name="set-the-controls-to-be-created"></a>Oluşturulacak denetimleri ayarlayın

Bu izlenecek yolda, verileri için `Customers` tablo bir **ayrıntıları** veri görüntüleyen her denetim düzeni. Verilerden `Orders` tablo bir **kılavuz** görüntülenen düzeni bir <xref:System.Windows.Forms.DataGridView> denetimi.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri kaynakları Penceresi'nde öğelerin bırakma türünü ayarlama

1. İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğümü.

2. Üzerinde **müşteriler** düğümünü **ayrıntıları** denetimi değiştirmek için Denetim listesinden **müşteriler** tek denetimleri için tablo. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Verilere bağlı formu oluşturma

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.

1. Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.

     Araç şeridi yanı sıra form üzerindeki verilere bağlı denetimler, tanımlayıcı etiketlerle görünür (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

2. İlgili sürükleyin **siparişler** düğümünden **veri kaynakları** penceresinden **Form1**.

    > [!NOTE]
    > İlgili **siparişler** düğümü altında bulunan **faks** sütun ve bir alt düğüm **müşteriler** düğümü.

     A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. Bir `OrdersTableAdapter` ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.

## <a name="add-code-to-update-the-database"></a>Veritabanını güncellemek için kod ekleyin

Çağırarak veritabanı güncelleştirebilirsiniz `Update` yöntemlerinin **müşteriler** ve **siparişler** TableAdapter bağdaştırıcıları. Varsayılan olarak, bir olay işleyicisi için **Kaydet** düğmesini<xref:System.Windows.Forms.BindingNavigator> veritabanına güncelleştirmeleri göndermek için formun koduna eklenir. Bu yordamı doğru sırayla güncelleştirmeleri göndermek için kod değiştirir. Bu bilgi tutarlılığını hataları oluşturma olanağına ortadan kaldırır. Kod ayrıca hata güncelleştirme çağrısında bir try-catch bloğu içinde sarmalama tarafından işleme uygular. Kod, uygulamanızın ihtiyaçlarına uyacak şekilde değiştirebilirsiniz.

> [!NOTE]
> Anlaşılsın diye, bu izlenecek yol, bir işlem kullanmaz. Ancak, iki güncelleştirilmiyor ya da tabloları ilgili daha fazla işlem içindeki tüm güncelleştirme mantığı içerir. Bir işlem değişiklikleri uygulanmadan önce bir veritabanındaki tüm ilgili değişiklikler başarılı olduğunu garantiler bir işlemdir. Daha fazla bilgi için [işlemler ve eşzamanlılık](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Uygulama güncelleştirme mantığı eklemek için

1. Seçin **Kaydet** düğmesini <xref:System.Windows.Forms.BindingNavigator>. Kod Düzenleyicisi açılır `bindingNavigatorSaveItem_Click` olay işleyicisi.

2. Çağrılacak olay işleyicisinde kodu değiştirin `Update` ilgili TableAdapter yöntemleri. Aşağıdaki kod önce her kullanıcının güncelleştirilmiş bilgilerini tutmak için üç geçici veri tabloları oluşturur <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added>, ve <xref:System.Data.DataRowState.Modified>). Güncelleştirmeleri doğru sırayla çalıştırılır. Kod aşağıdaki gibi görünmelidir:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Uygulamayı test etme

1. Tuşuna **F5**.

2. Veriler her tabloda bir veya daha fazla kayıt için birkaç değişiklik yapalım.

3. Seçin **Kaydet** düğmesi.

4. Değişiklikler kaydedildi doğrulamak için veritabanında değerleri kontrol edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)