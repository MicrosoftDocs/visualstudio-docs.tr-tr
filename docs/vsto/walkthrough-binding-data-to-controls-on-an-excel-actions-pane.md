---
title: 'İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8fbc1baa66dc98b2c5eec27c2a86e0fde3c5e967
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942653"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama
  Bu yönerge, Microsoft Office Excel eylemler bölmesindeki denetimlere veri bağlama gösterir. Bir SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi denetimleri gösterir.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Bir çalışma sayfasına denetimler ekleme.  
  
-   Eylemler bölmesi denetimi oluşturuluyor.  
  
-   Eylemler bölmesi denetimi için veri bağlantılı Windows Forms denetimleri ekleme.  
  
-   Uygulama açıldığında eylemler bölmesini gösterme.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   SQL Server Northwind örnek veritabanı ile bir sunucu erişim.  
  
-   SQL Server veritabanına yazma ve okuma izni.  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Excel çalışma kitabı projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **My Excel eylemler bölmesindeki**. Sihirbazda **yeni belge oluşturma**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **My Excel eylemler bölmesindeki** için proje **Çözüm Gezgini**.  
  
## <a name="add-a-new-data-source-to-the-project"></a>Projeye yeni bir veri kaynağı Ekle  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>Yeni bir veri kaynağı projeye eklemek için  
  
1. Varsa **veri kaynakları** penceresi görünür değilse, menü çubuğundan seçme görüntülemek **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3. Seçin **veritabanı** ve ardından **sonraki**.  
  
4. Northwind örnek SQL Server veritabanıyla kurulan veri bağlantısı seçin veya yeni bir bağlantı kullanarak eklemek **yeni bağlantı** düğmesi.  
  
5. **İleri**'ye tıklayın.  
  
6. Seçili olduğunda görüntüleyeceği bağlantı kaydetme seçeneğini ve ardından temizlemek **sonraki**.  
  
7. Genişletin **tabloları** düğümünde **veritabanı nesnelerinin** penceresi.  
  
8. Yanındaki onay kutusunu işaretleyin **tedarikçileri** tablo.  
  
9. Genişletin **ürünleri** tablosunu seçip **ProductName**, **SupplierID**, **QuantityPerUnit**, ve **UnitPrice**.  
  
10. **Son**'a tıklayın.  
  
    Sihirbaz ekler **tedarikçileri** tablo ve **ürünleri** tablo **veri kaynakları** penceresi. Projenize görünür olan bir türü belirtilmiş veri kümesi de ekler **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Ardından, ekleme bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi ve bir <xref:Microsoft.Office.Tools.Excel.ListObject> ilk çalışma denetimi.  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>NamedRange denetimi ve ListObject denetimi eklemek için  
  
1.  Doğrulayın **My Excel Eylemler Pane.xlsx** Visual Studio tasarımcıda açık çalışma kitabı ile `Sheet1` görüntülenir.  
  
2.  İçinde **veri kaynakları** penceresini genişletin **tedarikçileri** tablo.  
  
3.  Aşağı açılan oka tıklayın **şirket adı** düğümünü ve ardından **NamedRange**.  
  
4.  Sürükleme **şirket adı** gelen **veri kaynakları** hücre penceresine **A2** içinde `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `CompanyNameNamedRange` oluşturulur ve metin \<ŞirketAdı > hücrede görünür **A2**. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `suppliersBindingSource`, bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> projeye eklenir. Denetimin bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı <xref:System.Data.DataSet> örneği.  
  
5.  İçinde **veri kaynakları** penceresinde, aşağı altında sütunları geçmiş **tedarikçileri** tablo. Listenin en altta **ürünleri** tablo; çünkü bir alt öğesidir **tedarikçileri** tablo. Bu seçeneği belirleyin **ürünleri** değil, aynı düzeyde olan bir tablo **tedarikçileri** tablosuna ve sonra görünen açılan oku tıklatın.  
  
6.  Tıklayın **ListObject** sürükleyin ve açılan liste **ürünleri** hücre tabloya **A6** içinde `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim `ProductNameListObject` hücresinde oluşturulan **A6**. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `productsBindingSource` ve tablo bağdaştırıcısı projeye eklenir. Denetimin bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı <xref:System.Data.DataSet> örneği.  
  
7.  İçin C# yalnızca seçin **suppliersBindingSource** bileşeni Tepsi ve değişiklik **değiştiriciler** özelliğini **dahili** içinde **özellikleri**  penceresi.  
  
## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetimler ekleme  
 Ardından, bir birleşik giriş kutusu olan eylemler bölmesi denetimi gerekir.  
  
### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için  
  
1.  Seçin **My Excel eylemler bölmesindeki** projesi **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Eylemler bölmesi denetimi**, adlandırın **ActionsControl**, tıklatıp **Ekle**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Veri bağlantılı Windows Forms denetimleri için Eylemler bölmesi denetimi eklemek için  
  
1.  Gelen **ortak denetimleri** sekmelerin **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ComboBox> Eylemler bölmesi denetimi için denetim.  
  
2.  Değişiklik **boyutu** özelliğini **171, 21**.  
  
3.  Kullanıcı denetimi, birleşik giriş kutusu uyacak şekilde yeniden boyutlandırın.  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Eylemler bölmesi denetimi verilere bağlama  
 Bu bölümde, veri kaynağı ayarlarsınız <xref:System.Windows.Forms.ComboBox> aynı veri kaynağına <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasında denetimi.  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>Veri bağlama denetiminin özelliklerini ayarlamak için  
  
1.  Eylemler bölmesi denetimi sağ tıklayın ve ardından **kodu görüntüle**.  
  
2.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.UserControl.Load> Eylemler Bölmesi Denetimi olayı.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  İçinde C#, bir olay işleyicisi için oluşturmalısınız `ActionsControl`. Bu kodu koyabilirsiniz `ActionsControl` Oluşturucusu. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>Eylemler bölmesini göster  
 Çalışma zamanında denetim ekleme kadar Eylemler bölmesi görünür değildir.  
  
#### <a name="to-show-the-actions-pane"></a>Eylemler bölmesinde göstermek için  
  
1.  İçinde **Çözüm Gezgini**, sağ *ThisWorkbook.vb* veya *ThisWorkbook.cs*ve ardından **Kodu Görüntüle**.  
  
2.  Yeni bir kullanıcı denetimi örneğini oluşturmak `ThisWorkbook` sınıfı.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  İçinde <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> olay işleyicisine `ThisWorkbook`, Eylemler bölmesi denetimi ekleyin.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık belgenizi bir belge açıldığında eylemler bölmesini açar ve denetimleri ana/ayrıntı ilişkisi olduğunu doğrulamak için test edebilirsiniz.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Eylemler bölmesi görünür olduğunu doğrulayın.  
  
3.  Şirket, liste kutusunda seçin. Şirket adı olarak listelendiğini doğrulayın <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi ve ürün ayrıntıları listelendiğini <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi.  
  
4.  Şirket adını doğrulamak için çeşitli şirketlerle seçin ve ürün ayrıntıları uygun şekilde değiştirin.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Word denetimlere veri bağlama. Daha fazla bilgi için [izlenecek yol: Word eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Projeyi dağıtma. Daha fazla bilgi için [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  