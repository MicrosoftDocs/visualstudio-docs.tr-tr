---
title: 'İzlenecek yol: Word eylemler bölmesindeki denetimlere veri bağlama'
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
ms.openlocfilehash: 17daf186920be45a70200cd896a390ab74c4c6d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873896"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>İzlenecek yol: Word eylemler bölmesindeki denetimlere veri bağlama
  Bu yönerge, Word eylemler bölmesindeki denetimlere veri bağlama gösterir. Bir SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi denetimleri gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Eylemler bölmesi veriye bağlanan Windows Forms denetimleri ile oluşturuluyor.  
  
-   Ana/ayrıntı ilişkisi denetimlerinde verileri görüntülemek için kullanma.  
  
-   Uygulama açıldığında eylemler bölmesini göster.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   SQL Server Northwind örnek veritabanı ile bir sunucu erişim.  
  
-   SQL Server veritabanına yazma ve okuma izni.  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Word belgesi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adıyla bir Word belgesi projesi oluşturma **My Word eylemler bölmesindeki**. Sihirbazda **yeni belge oluşturma**.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **My Word eylemler bölmesindeki** için proje **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetimler ekleme  
 Bu kılavuz için veri bağlantılı Windows Forms denetimlerini içeren eylemler bölmesi denetimi gerekir. Bir veri kaynağı projeye ekleyin ve ardından denetimlerden sürükleyin **veri kaynakları** Eylemler bölmesi denetimi için pencere.  
  
### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için  
  
1.  Seçin **My Word eylemler bölmesindeki** projesi **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Eylemler bölmesi denetimi**, adlandırın **ActionsControl**ve ardından **Ekle**.  
  
### <a name="to-add-a-data-source-to-the-project"></a>Bir veri kaynağı projeye eklemek için  
  
1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
   > [!NOTE]  
   >  Varsa **veri kaynaklarını Göster** kullanılabilir değil, Word belgesi tıklayın ve sonra tekrar denetleyin.  
  
2. Tıklayın **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3. Seçin **veritabanı** ve ardından **sonraki**.  
  
4. Northwind örnek SQL Server veritabanıyla kurulan veri bağlantısı seçin veya yeni bir bağlantı kullanarak eklemek **yeni bağlantı** düğmesi.  
  
5. **İleri**'ye tıklayın.  
  
6. Seçili olduğunda görüntüleyeceği bağlantı kaydetme seçeneğini ve ardından temizlemek **sonraki**.  
  
7. Genişletin **tabloları** düğümünde **veritabanı nesnelerinin** penceresi.  
  
8. Yanındaki onay kutusunu işaretleyin **tedarikçileri** ve **ürünleri** tablolar.  
  
9. **Son**'a tıklayın.  
  
   Sihirbaz ekler **tedarikçileri** tablo ve **ürünleri** tablo **veri kaynakları** penceresi. Projenize görünür olan bir türü belirtilmiş veri kümesi de ekler **Çözüm Gezgini**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Veri bağlantılı Windows Forms denetimleri için Eylemler bölmesi denetimi eklemek için  
  
1.  İçinde **veri kaynakları** penceresini genişletin **tedarikçileri** tablo.  
  
2.  Aşağı açılan oka tıklayın **şirket adı** düğüm ve select **ComboBox**.  
  
3.  Sürükleme **CompanyName** gelen **veri kaynakları** Eylemler bölmesi denetimi için pencere.  
  
     A <xref:System.Windows.Forms.ComboBox> denetimi, Eylemler bölmesi denetimi üzerinde oluşturulur. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `SuppliersBindingSource`, bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> bileşen tepsisinde projeye eklenir.  
  
4.  Seçin `SuppliersBindingNavigator` içinde **bileşen** Tepsisi ve ENTER tuşuna **Sil**. Kullanmayacaksınız `SuppliersBindingNavigator` Bu izlenecek yolda.  
  
    > [!NOTE]  
    >  Silme `SuppliersBindingNavigator` tüm için oluşturulan kodun kaldırmaz. Bu kod kaldırabilirsiniz.  
  
5.  Birleşik giriş kutusu etiket ve değişiklik altında olduğu şekilde taşıyın **boyutu** özelliğini **171, 21**.  
  
6.  İçinde **veri kaynakları** penceresini genişletin **ürünleri** tablosunu bir alt öğesi **tedarikçileri** tablo.  
  
7.  Aşağı açılan oka tıklayın **ProductName** düğüm ve select **ListBox**.  
  
8.  Sürükleme **ProductName** Eylemler bölmesi denetimi için.  
  
     A <xref:System.Windows.Forms.ListBox> denetimi, Eylemler bölmesi denetimi üzerinde oluşturulur. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `ProductBindingSource` ve tablo bağdaştırıcısı bileşen tepsisinde projeye eklenir.  
  
9. Liste kutusu etiket ve değişiklik altında olduğu şekilde taşıyın **boyutu** özelliğini **171, 95**.  
  
10. Sürükleme bir <xref:System.Windows.Forms.Button> gelen **araç kutusu** Eylemler bölmesi denetimi ve liste kutusunun yerleştirin.  
  
11. Sağ <xref:System.Windows.Forms.Button>, tıklayın **özellikleri** kısayol menüsünde ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**Ekle**|  
    |**Metin**|**Ekle**|  
  
12. Denetimleri sığdırmak için kullanıcı denetimi yeniden boyutlandırın.  
  
## <a name="set-up-the-data-source"></a>Veri kaynağını Ayarla  
 Veri kaynağı'kurmak için kod ekleyin. <xref:System.Windows.Forms.UserControl.Load> verilerle denetimin doldurmaya Eylemler Bölmesi Denetimi olayı <xref:System.Data.DataTable>, ayarlayıp <xref:System.Windows.Forms.Binding.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> her denetimin özelliklerini.  
  
### <a name="to-load-the-control-with-data"></a>Denetim verileri ile yüklemek için  
  
1.  İçinde <xref:System.Windows.Forms.UserControl.Load> olay işleyicisine `ActionsControl` sınıfında, aşağıdaki kodu ekleyin.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  C# dilinde olay işleyicisine eklemelisiniz <xref:System.Windows.Forms.UserControl.Load> olay. Bu kodu koyabilirsiniz `ActionsControl` çağrısından sonra bir oluşturucu `InitializeComponent`. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>Veri bağlama denetimleri özelliklerini ayarlamak için  
  
1.  Seçin `CompanyNameComboBox` denetimi.  
  
2.  İçinde **özellikleri** penceresinde sağındaki düğmeye tıklayın **DataSource** özelliği ve select **suppliersBindingSource**.  
  
3.  Sağındaki düğmeye tıklayın **DisplayMember** özelliği ve select **CompanyName**.  
  
4.  Genişletin **DataBindings** özelliği sağındaki düğmeye tıklayın **metin** özelliği ve select **hiçbiri**.  
  
5.  Seçin `ProductNameListBox` denetimi.  
  
6.  İçinde **özellikleri** penceresinde sağındaki düğmeye tıklayın **DataSource** özelliği ve select **productsBindingSource**.  
  
7.  Sağındaki düğmeye tıklayın **DisplayMember** özelliği ve select **ProductName**.  
  
8.  Genişletin **DataBindings** özelliği sağındaki düğmeye tıklayın **SelectedValue** özelliği ve select **hiçbiri**.  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>Bir tabloya veri eklemek için bir yöntem ekleyin  
 Sıradaki görev ilişkili denetimlerden verileri okumak ve, Word belgesinde bir tabloyu doldurmak sağlamaktır. İlk olarak, tablo başlıklarında biçimlendirmek için bir yordam oluşturma ve ardından eklemek `AddData` oluşturmak ve bir Word tabloyu biçimlendirmek için yöntemi.  
  
### <a name="to-format-the-table-headings"></a>Tablo üst bilgilerinden biçimlendirmek için  
  
1.  İçinde `ActionsControl` sınıfı, tablo üst bilgilerinden biçimlendirmek için bir yöntem oluşturun.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>Tablo oluşturmak için  
  
1.  İçinde `ActionsControl` sınıfı, bir zaten varsa ve veri Eylemler bölmesinden tabloya ekleyin. bir tablo oluşturacaksınız bir yöntem yazmaktır.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Metin bir sözcük tablosuna eklemek için  
  
1.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine **Ekle** düğmesi.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  C# için bir olay işleyicisi oluşturmanız gerekir <xref:System.Windows.Forms.Control.Click> düğmesinin olayı.  Bu kodu koyabilirsiniz <xref:System.Windows.Forms.UserControl.Load> olay işleyicisine `ActionsControl` sınıfı.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>Eylemler bölmesini göster  
 Denetimler için eklendikten sonra Eylemler bölmesinde görünür hale gelir.  
  
### <a name="to-show-the-actions-pane"></a>Eylemler bölmesinde göstermek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisDocument.vb** veya **ThisDocument.vb**ve ardından **Kodu Görüntüle** kısayol menüsünde.  
  
2.  En üstündeki denetimin yeni bir örneğini oluşturma `ThisDocument` aşağıdaki örnekteki gibi görünüyor. böylece sınıf.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Kodu <xref:Microsoft.Office.Tools.Word.Document.Startup> olay işleyicisine `ThisDocument` böylece aşağıdaki örnekteki gibi görünüyor.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık belgenizi bir belge açıldığında eylemler bölmesinde görüntülendiğini doğrulamak için test edebilirsiniz. Test için ana/ayrıntı ilişkisi eylemler bölmesindeki denetimlere ve verilerin bir sözcük doldurulduğundan emin olun tablosundan **Ekle** düğmesine tıklandığında.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Eylemler bölmesi görünür olduğunu doğrulayın.  
  
3.  Birleşik giriş kutusunda şirketi seçin ve doğrulayın öğeleri **ürünleri** liste kutusunu değiştirme.  
  
4.  Bir ürün seçin, **Ekle** eylemler bölmesindeki ve ürün ayrıntıları sözcük tablosuna eklendiğini doğrulayın.  
  
5.  Ek ürünler çeşitli şirketlerden ekleyin.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, Word eylemler bölmesindeki denetimlere veri bağlama hakkındaki temel bilgileri gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Excel'de denetimlere veri bağlama. Daha fazla bilgi için [izlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Projeyi dağıtma. Daha fazla bilgi için [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  