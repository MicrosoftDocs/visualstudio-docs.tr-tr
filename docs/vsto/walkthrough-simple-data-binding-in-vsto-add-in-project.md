---
title: 'İzlenecek yol: VSTO eklenti projesinde basit veri bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0373bcba5cecbbc47451f3ad050ba0ea44a12246
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672671"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde basit veri bağlama

Konak denetimlerinin ve VSTO eklentisi projeleri Windows Forms denetimlerinde verileri bağlayabilirsiniz. Bu izlenecek yol, bir Microsoft Office Word belgesi için denetimler ekleme ve verileri çalışma zamanında denetimler bağlayabilirsiniz gösterilmektedir.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Bu izlenecek yol aşağıdaki görevleri gösterir:

-   Ekleme bir <xref:Microsoft.Office.Tools.Word.ContentControl> belgeye çalışma zamanında.

-   Oluşturma bir <xref:System.Windows.Forms.BindingSource> , denetim bir veri kümesinin bir örneğine bağlanır.

-   Kayıtlarda gezinmek ve bunları denetimde görüntülemek kullanıcı etkinleştiriliyor.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

-   Çalışan bir SQL Server 2005 veya SQL Server 2005 olan Express örneğine erişim `AdventureWorksLT` bağlı örnek veritabanı. İndirebileceğiniz `AdventureWorksLT` veritabanını [CodePlex Web sitesinde](http://go.microsoft.com/fwlink/?LinkId=115611). Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

    -   SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: veritabanı (SQL Server Management Studio) ekleme](/sql/relational-databases/databases/attach-a-database).

    -   Komut satırını kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: SQL Server Express için bir veritabanı dosyası iliştirmek](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

İlk adım, bir sözcük VSTO eklentisi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1.  Adlı bir sözcük VSTO eklentisi projesi oluşturun **veritabanından belgeleri doldurma**, Visual Basic kullanarak veya C#.

     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio açılır *ThisAddIn.vb* veya *ThisAddIn.cs* ekler ve dosya **veritabanından belgeleri doldurma** için proje **Çözüm Gezgini** .

2.  Projenizin hedeflediği [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], bir başvuru ekleyin *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* derleme. Bu başvuru, program aracılığıyla bu kılavuzda daha sonra belge Windows Forms denetimleri ekleme için gereklidir.

## <a name="create-a-data-source"></a>Bir veri kaynağı oluşturun

Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Yazılan veri kümesi projesine eklemek için

1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.

2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

3. Tıklayın **veritabanı**ve ardından **sonraki**.

4. Varolan bir bağlantınız varsa `AdventureWorksLT` veritabanı, bu bağlantıyı seçin ve tıklayın **sonraki**.

    ' A tıklayıp **yeni bağlantı**ve **Bağlantı Ekle** yeni bir bağlantı oluşturmak için iletişim kutusu. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).

5. İçinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

6. İçinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** seçip **müşteri (SalesLT)**.

7. **Son**'a tıklayın.

    *AdventureWorksLTDataSet.xsd* dosya eklendiğinde **Çözüm Gezgini**. Bu dosya, aşağıdakileri tanımlar:

   - Adlı bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet`. Bu veri kümesi içeriğini temsil eden **müşteri (SalesLT)** AdventureWorksLT veritabanında tablo.

   - Adlı bir TableAdapter `CustomerTableAdapter`. Bu TableAdapter okuyup veri yazmak için kullanılan `AdventureWorksLTDataSet`. Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu izlenecek yolda, bu nesnelerin her ikisi de kullanır.

## <a name="create-controls-and-binding-controls-to-data"></a>Denetimleri ve denetimlere veri bağlama oluşturun

Bu izlenecek yolda veritabanı kayıtlarını görüntüleyen temel arabirimdir ve belgenin içinde oluşturulur. Bir <xref:Microsoft.Office.Tools.Word.ContentControl> tek veritabanı kaydını bir saat ve iki görüntüler <xref:Microsoft.Office.Tools.Word.Controls.Button> denetimleri ve geriye kayıtlarda gezinin olanak tanır. İçerik denetimi kullanan bir <xref:System.Windows.Forms.BindingSource> veritabanına bağlanmak için.

Denetimlere veri bağlama hakkında daha fazla bilgi için bkz: [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Belgede arabirimi oluşturmak için

1.  İçinde `ThisAddIn` sınıfında, aşağıdaki denetimleri görüntülemek ve kaydırmak için bildirin `Customer` tablosu `AdventureWorksLTDataSet` veritabanı.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2.  İçinde `ThisAddIn_Startup` yöntemi, veri kümesini başlatmak, alınan bilgilerle DataSet'i doldurmak için aşağıdaki kodu ekleyin `AdventureWorksLTDataSet` veritabanı.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3.  Aşağıdaki kodu ekleyin `ThisAddIn_Startup` yöntemi. Bu belge genişleten bir ana bilgisayar öğesi oluşturur. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4.  Belgenin başlangıcında birkaç aralıklarını tanımlayın. Bu aralıklar metin ekleme denetimlerini yerleştirin nereye belirleyin.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5.  Arabirimi denetimleri için önceden tanımlanmış aralıkları ekleyin.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6.  İçerik denetimi bağlamak `AdventureWorksLTDataSet` kullanarak <xref:System.Windows.Forms.BindingSource>. İçin C# geliştiricileri için iki olay işleyicileri ekleme <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrol eder.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7.  Veritabanı Kayıtlarda gezinmek için aşağıdaki kodu ekleyin.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Eklenti test

Word'ü açtığınızda, içerik denetimi verileri görüntüleyen `AdventureWorksLTDataSet` veri kümesi. Tıklayarak veritabanı kayıtları arasında kaydırma **sonraki** ve **önceki** düğmeleri.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisi test etmek için

1.  Tuşuna **F5**.

     Adlı bir içerik denetimi `customerContentControl` oluşturulur ve verilerle doldurulur. Aynı anda, adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` ve <xref:System.Windows.Forms.BindingSource> adlı `customerBindingSource` projeye eklenir. <xref:Microsoft.Office.Tools.Word.ContentControl> Bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı dataset nesnesine.

2.  Tıklayın **sonraki** ve **önceki** düğmelerini veritabanı kayıtlarda gezinin.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmet verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [İzlenecek yol: Belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [İzlenecek yol: Belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Office çözümlerine genel bakış yerel veritabanı dosyaları kullanma](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office çözümlerine genel bakış yerel veritabanı dosyaları kullanma](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)