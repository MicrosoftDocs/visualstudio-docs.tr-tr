---
title: TableAdapter DBDirect metotlarıyla veri kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ef1860274c9234774b8af42525a0215d9468a858
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304581"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect metotlarıyla veri kaydetme

Bu izlenecek yol, bir TableAdapter DBDirect yöntemleri kullanılarak doğrudan veritabanına karşı SQL deyimleri çalıştırmaya yönelik ayrıntılı yönergeler sağlar. Veritabanı güncelleştirmelerinizi denetime ayrıntılı bir düzeyde bir TableAdapter DBDirect yöntemleri sağlar. Bunları ayrı ayrı çağrı yaparak belirli SQL deyimlerini ve depolanan yordamları çalıştırmak için kullanabileceğiniz `Insert`, `Update`, ve `Delete` uygulamanızın ihtiyaç duyduğu gibi yöntemleri (aşırı yüklenmiş'ın aksine `Update` güncelleştirme gerçekleştirir yöntemi INSERT ve DELETE deyimleri bir çağrıda tüm).

Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:

-   Yeni bir **Windows Forms uygulaması**.

-   Oluşturma ve yapılandırma ile dataset [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png).

-   Denetimin formda öğelerinden sürüklendiğinde oluşturulacak seçin **veri kaynakları** penceresi. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Öğe sürükleyerek veriye bağlı form oluşturma **veri kaynakları** forma penceresi.

-   Doğrudan veritabanına erişmek ve ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için yöntemleri ekleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa,'nden ya da yükleme [SQL Server Express indirme sayfası](https://www.microsoft.com/sql-server/sql-server-editions-express), aracılığıyla veya **Visual Studio yükleyicisi**. İçinde **Visual Studio yükleyicisi**, bir parçası olarak SQL Server Express LocalDB yükleyebilirsiniz **veri depolama ve işleme** iş yükü veya tek bir bileşen olarak.

2. Northwind örnek veritabanı, şu adımları izleyerek yükleyin:

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

4. Projeyi adlandırın **TableAdapterDbDirectMethodsWalkthrough**ve ardından **Tamam**.

     **TableAdapterDbDirectMethodsWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun

Bu adımı kullanan **veri kaynağı Yapılandırma Sihirbazı** dayalı bir veri kaynağını oluşturmak için `Region` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. Üzerinde **veri** menüsünde **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi açılır.

2. İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

3. Üzerinde **bir veri kaynağı türü seçin** ekranındayken **veritabanı**ve ardından **sonraki**.

4. Üzerinde **veri bağlantınızı seçin** ekranında, aşağıdakilerden birini yapın:

    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.

5. Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.

6. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** ekranındayken **sonraki**.

7. Üzerinde **veritabanı nesnelerinizi seçin** ekranında, **tabloları** düğümü.

8. Seçin `Region` tablosuna sağ tıklayıp ardından **son**.

     **NorthwindDataSet** projenize eklenir ve `Region` tablo görünür **veri kaynakları** penceresi.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Verileri görüntülemek için formu için denetimler ekleme

Öğe sürükleyerek veriye bağlı denetimler oluşturmak **veri kaynakları** formunuza penceresi.

Windows form üzerinde veri bağlama denetimleri oluşturmak için ana sürükleyin **bölge** düğümünden **veri kaynakları** forma penceresi.

A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Tek tek TableAdapter DbDirect yöntemleri çağıran düğme eklemek için

1. Üç sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** üzerine **Form1** (aşağıda **RegionDataGridView**).

2. Aşağıdakileri ayarlayın **adı** ve **metin** her düğmesine özellikleri.

    |Ad|Metin|
    |----------|----------|
    |`InsertButton`|**Ekle**|
    |`UpdateButton`|**Güncelleştir**|
    |`DeleteButton`|**Delete**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Veritabanına yeni kayıtlar eklemek için kod eklemek için

1. Seçin **InsertButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.

2. Değiştirin `InsertButton_Click` olay işleyicisi aşağıdaki kod ile:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Veritabanındaki kayıtları güncelleştirmek için kod eklemek için

1. Çift **UpdateButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.

2. Değiştirin `UpdateButton_Click` olay işleyicisi aşağıdaki kod ile:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Kayıtlarını veritabanından silmek için kod eklemek için

1. Seçin **DeleteButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.

2. Değiştirin `DeleteButton_Click` olay işleyicisi aşağıdaki kod ile:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın

-   Seçin **F5** uygulamayı çalıştırın.

-   Seçin **Ekle** düğmesini ve yeni kayıt kılavuzda göründüğünü doğrulayın.

-   Seçin **güncelleştirme** düğmesini ve kayıt kılavuzda güncelleştirildiğini doğrulayın.

-   Seçin **Sil** düğmesini ve kayıt kılavuzdan kaldırıldığını doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlama form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

-   Forma arama işlevselliği ekleme.

-   Seçerek veri kümesine ek tablolar ilave **veri kümesini Yapılandırma Sihirbazı ile** içinden **veri kaynakları** penceresi. İlgili düğümlerin form üzerine sürükleyerek ilgili verileri görüntüleyen denetimler ekleyebilirsiniz. Daha fazla bilgi için [veri kümelerindeki ilişkiler](relationships-in-datasets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)