---
title: 'İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af82d74c0e0a0446b759a06a9e874a39fc57b6fd
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672529"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama
  Konak denetimlerinin ve VSTO eklentisi projeleri Windows Forms denetimlerinde verileri bağlayabilirsiniz. Bu kılavuzda, Microsoft Office Excel çalışma sayfasına denetimler ekleme ve çalışma zamanında verilere denetimler bağlama gösterilmektedir.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Ekleme bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma zamanında denetim.

- Oluşturma bir <xref:System.Windows.Forms.BindingSource> , denetim bir veri kümesinin bir örneğine bağlanır.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Çalışan bir SQL Server 2005 veya SQL Server 2005 olan Express örneğine erişim `AdventureWorksLT` bağlı örnek veritabanı. İndirebileceğiniz `AdventureWorksLT` veritabanını [CodePlex Web sitesinde](http://go.microsoft.com/fwlink/?LinkId=115611). Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

    -   SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: veritabanı (SQL Server Management Studio) ekleme](/sql/relational-databases/databases/attach-a-database).

    -   Komut satırını kullanarak bir veritabanı eklemek için bkz: [nasıl yapılır: SQL Server Express için bir veritabanı dosyası iliştirmek](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 İlk adım, bir Excel VSTO eklentisi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1.  Adlı bir Excel VSTO eklentisi projesi oluşturun **ekleneceğinin veritabanından**, Visual Basic kullanarak veya C#.

     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio açılır `ThisAddIn.vb` veya `ThisAddIn.cs` ekler ve dosya **ekleneceğinin veritabanından** için proje **Çözüm Gezgini**.

## <a name="create-a-data-source"></a>Bir veri kaynağı oluşturun
 Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Yazılan veri kümesi projesine eklemek için

1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.

2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

3. Tıklayın **veritabanı**ve ardından **sonraki**.

4. Varolan bir bağlantınız varsa `AdventureWorksLT` veritabanı, bu bağlantıyı seçin ve tıklayın **sonraki**.

    ' A tıklayıp **yeni bağlantı**ve **Bağlantı Ekle** yeni bir bağlantı oluşturmak için iletişim kutusu. Daha fazla bilgi için [yeni bağlantı ekleme](../data-tools/add-new-connections.md).

5. İçinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.

6. İçinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** seçip **adres (SalesLT)**.

7. **Son**'a tıklayın.

    *AdventureWorksLTDataSet.xsd* dosya eklendiğinde **Çözüm Gezgini**. Bu dosya, aşağıdakileri tanımlar:

   - Adlı bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet`. Bu veri kümesi içeriğini temsil eden **adres (SalesLT)** AdventureWorksLT veritabanında tablo.

   - Adlı bir TableAdapter `AddressTableAdapter`. Bu TableAdapter okuyup veri yazmak için kullanılan `AdventureWorksLTDataSet`. Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu izlenecek yolda, bu nesnelerin her ikisi de kullanır.

## <a name="create-controls-and-bind-controls-to-data"></a>Denetimleri oluşturma ve verilere denetimler bağlama
 Bu kılavuz <xref:Microsoft.Office.Tools.Excel.ListObject> denetim seçili kullanıcı çalışma kitabını açar açmaz tablodaki tüm verileri görüntüler. Liste nesnesi kullanan bir <xref:System.Windows.Forms.BindingSource> kontrol veritabanına bağlanmak için.

 Denetimlere veri bağlama hakkında daha fazla bilgi için bkz: [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Liste nesnesi, veri kümesi ve tablo bağdaştırıcısı eklemek için

1.  İçinde `ThisAddIn` sınıfı, görüntülemek için aşağıdaki denetimleri bildirin `Address` tablosu `AdventureWorksLTDataSet` veri kümesi.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2.  İçinde `ThisAddIn_Startup` yöntemi, veri kümesi başlatıp bilgileriyle DataSet'i doldurmak için aşağıdaki kodu ekleyin `AdventureWorksLTDataSet` veri kümesi.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3.  Aşağıdaki kodu ekleyin `ThisAddIn_Startup` yöntemi. Bu, çalışma genişleten bir ana bilgisayar öğesi oluşturur. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4.  Aralık oluşturmak ve eklemek <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5.  Liste nesnesine Bağla `AdventureWorksLTDataSet` kullanarak <xref:System.Windows.Forms.BindingSource>. Liste nesnesine bağlamak istediğiniz sütun adlarını geçirin.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Eklenti test
 Excel'i açtığınızda <xref:Microsoft.Office.Tools.Excel.ListObject> denetim veriyi görüntüler `Address` tablosu `AdventureWorksLTDataSet` veri kümesi.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisi test etmek için

-   Tuşuna **F5**.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim `addressListObject` çalışma sayfasında oluşturulur. Aynı anda, adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` ve <xref:System.Windows.Forms.BindingSource> adlı `addressBindingSource` projeye eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject> Bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı dataset nesnesine.

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
- [Office çözümlerine genel bakış yerel veritabanı dosyaları kullanma](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)