---
title: Formlar arasında veri geçirme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4a0d248f59754d3f46e8fab0e0924c36a80b0d89
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305552"
---
# <a name="pass-data-between-forms"></a>Formlar arasında veri geçirme

Bu izlenecek yolda, verileri bir biçimden diğerine geçirmek için adım adım yönergeler sağlar. Müşteriler ve siparişler tablolarından Northwind kullanarak, bir form kullanıcıların bir müşteri seçmesine izin verir ve Seçilen müşteri siparişleri ikinci bir form görüntüler. Bu izlenecek yol, ikinci formdaki verileri ilk formdan alan bir yöntem oluşturma işlemi gösterilmektedir.

> [!NOTE]
> Bu yönerge, formlar arasında veri iletmek için yalnızca bir yol gösterir. Bir ortak özellik oluşturma verilerle ilk formdan ayarlanabilir veya forma veri almak için ikinci bir oluşturucu oluşturma gibi verileri geçirmek için diğer seçenekleri vardır.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Yeni bir oluşturma **Windows Forms uygulaması** proje.

-   Oluşturma ve yapılandırma ile dataset [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png).

-   Form üzerinde öğelerinden sürüklendiğinde oluşturulacak denetimi seçerek **veri kaynakları** penceresi. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Öğe sürükleyerek veriye bağlı denetim oluşturma **veri kaynakları** forma penceresi.

-   Verileri görüntülemek için bir kılavuz ikinci bir form oluşturuluyor.

-   Belirli bir müşterinin siparişlerini getirilecek TableAdapter sorgu oluşturma.

-   Formlar arasında veri geçirme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1.  SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. Visual Studio yükleyicisi, SQL Server Express LocalDB parçası olarak yüklenebilir **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2.  Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

    1. Visual Studio'da açın **SQL Server Nesne Gezgini** penceresi. (Bir parçası olarak SQL Server Nesne Gezgini yüklü **veri depolama ve işleme** iş yükünü Visual Studio Yükleyicisi'nde.) Genişletin **SQL Server** düğümü. LocalDB Örneğinizde sağ tıklayıp **yeni sorgu**.

       Sorgu Düzenleyicisi penceresi açılır.

    2. Kopyalama [Northwind Transact-SQL betiği](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza. Bu T-SQL betiği, sıfırdan Northwind veritabanı oluşturur ve verilerle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı tamamladıktan ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-app-project"></a>Windows Forms uygulaması projesi oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#**  veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **PassingDataBetweenForms**ve ardından **Tamam**.

     **PassingDataBetweenForms** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-the-data-source"></a>Veri kaynağı oluşturma

1.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.

3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

4.  Üzerinde **veritabanı modeli seçin** sayfasında, **veri kümesi** belirtilir ve ardından **sonraki**.

5.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

6.  Veritabanınız parola gerektiriyorsa ve hassas verileri eklemek için seçeneği etkinse bu seçeneği belirleyin ve ardından **sonraki**.

7.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

8.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.

9. Seçin **müşteriler** ve **siparişler** tablolar ve ardından **son**.

     **NorthwindDataSet** projenize eklenir ve **müşteriler** ve **siparişler** tablolar görünür **veri kaynakları** penceresi.

## <a name="create-the-first-form-form1"></a>İlk formu (Form1) oluşturma

Verilere bağlı kılavuz oluşturabilirsiniz (bir <xref:System.Windows.Forms.DataGridView> denetimi), sürükleyerek **müşteriler** düğümünden **veri kaynakları** forma penceresi.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Form üzerinde bir verilere bağlı kılavuz oluşturmak için

-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.

     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için görünür **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="create-the-second-form"></a>İkinci form oluşturma

Verileri geçirmek için ikinci bir form oluşturun.

1.  Gelen **proje** menüsünde seçin **Windows formu eklemek**.

2.  Varsayılan adı bırakın **Form2**, tıklatıp **Ekle**.

3.  Ana sürükleyin **siparişler** düğümünden **veri kaynakları** penceresinden **Form2**.

     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için görünür **Form2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

4.  Silme **OrdersBindingNavigator** bileşeni Tepsi öğesinden.

     **OrdersBindingNavigator** kaybolur **Form2**.

## <a name="add-a-tableadapter-query"></a>Bir TableAdapter Sorgu Ekle

TableAdapter sorgusu Form1 Seçilen müşteri siparişleri yüklenecek Form2 ekleyin.

1.  Çift **NorthwindDataSet.xsd** dosyası **Çözüm Gezgini**.

2.  Sağ **orderstableadapter bağdaştırıcısına**seçip **Sorgu Ekle**.

3.  Varsayılan seçenek olan bırakın **SQL deyimi kullan**ve ardından **sonraki**.

4.  Varsayılan seçenek olan bırakın **satır döndüren SELECT**ve ardından **sonraki**.

5.  Döndürülecek sorguya bir WHERE yan tümcesi ekleyin `Orders` göre `CustomerID`. Sorgu aşağıdakine benzemelidir:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Veritabanınız için doğru parametre sözdizimini doğrulayın. Örneğin, Microsoft Access, WHERE yan tümcesi şöyle görünmelidir: `WHERE CustomerID = ?`.

6.  **İleri**'ye tıklayın.

7.  İçin **DataTableMethod ad girme**, türü `FillByCustomerID`.

8.  NET **DataTable Döndür** seçeneğini ve ardından **sonraki**.

9. **Son**'a tıklayın.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Verileri geçirmek için Form2 üzerinde bir yöntem oluşturma

1.  Sağ **Form2**seçip **kodu görüntüle** açmak için **Form2** içinde **Kod Düzenleyicisi**.

2.  Aşağıdaki kodu ekleyin **Form2** sonra `Form2_Load` yöntemi:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Veri iletmek ve Form2 görüntülemek için Form1 üzerinde bir yöntem oluşturma

1.  İçinde **Form1**müşteri veri kılavuzu sağ tıklayın ve ardından **özellikleri**.

2.  İçinde **özellikleri** penceresinde tıklayın **olayları**.

3.  Çift **CellDoubleClick** olay.

     Kod Düzenleyicisi görünür.

4.  Yöntem tanımını aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Uygulamayı çalıştırma

-   Tuşuna **F5** uygulamayı çalıştırın.

-   Bir müşteri kaydı çift **Form1** açmak için **Form2** müşterinin sipariş.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, formlar arasında veri geçirme sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

-   Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Verileri yeniden veritabanına kaydetme işlevselliği ekleme. Daha fazla bilgi için [verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)