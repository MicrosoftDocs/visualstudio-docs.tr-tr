---
title: 'İzlenecek yol: Belge düzeyi projede basit veri bağlama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25173e5c4d4aeb02045cf858ae1e093b7a04d2bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824386"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>İzlenecek yol: Belge düzeyi projede basit veri bağlama
  Bu izlenecek yol, bir belge düzeyi projede veri bağlama ilişkin temel bilgileri gösterir. Bir SQL Server veritabanı bir tek veri alanında Microsoft Office Excel adlandırılmış aralıkta bağlıdır. İzlenecek yol, ayrıca tablodaki tüm kayıtları arasında kaydırma olanak tanıyan denetimlerin nasıl ekleneceğini gösterir.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Veri kaynağı için Excel projesi oluşturma.  
  
- Bir çalışma sayfasına denetimler ekleme.  
  
- Veritabanı kayıtları arasında kaydırma.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   SQL Server Northwind örnek veritabanı ile bir sunucu erişim.  
  
-   SQL Server veritabanına yazma ve okuma izni.  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 Bu adımda, bir Excel çalışma kitabı projesi oluşturur.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Adlı bir Excel çalışma kitabı projesi oluşturun **basit veri bağlaması**, Visual Basic kullanarak veya C#. Emin olun **yeni belge oluşturma** seçilir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **basit veri bağlaması** için proje **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
 Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.  
  
### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3. Seçin **veritabanı** ve ardından **sonraki**.  
  
4. Northwind örnek SQL Server veritabanıyla kurulan veri bağlantısı seçin veya kullanan yeni bir bağlantı eklemek **yeni bağlantı** düğmesi.  
  
5. Bağlantı seçili veya oluşturulduktan sonra tıklayın **sonraki**.  
  
6. Seçili olduğunda görüntüleyeceği bağlantı kaydetme seçeneğini ve ardından temizlemek **sonraki**.  
  
7. Genişletin **tabloları** düğümünde **veritabanı nesnelerinin** penceresi.  
  
8. Yanındaki onay kutusunu işaretleyin **müşteriler** tablo.  
  
9. **Son**'a tıklayın.  
  
   Sihirbaz ekler **müşteriler** tablo **veri kaynakları** penceresi. Projenize görünür olan bir türü belirtilmiş veri kümesi de ekler **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Bu kılavuz için iki adlandırılmış aralıklar ve ilk çalışma sayfası üzerindeki dört düğme gerekir. İlk olarak, iki adlandırılmış aralıklarını ekleyin **veri kaynakları** penceresi otomatik olarak bir veri kaynağına bağlı olacak şekilde. Düğmelerden ekleyeceğimize **araç kutusu**.  
  
### <a name="to-add-two-named-ranges"></a>İki adlandırılmış aralıklar eklemek için  
  
1.  Doğrulayın *My basit veri Binding.xlsx* Visual Studio tasarımcıda açık çalışma kitabı ile **Sayfa1** görüntülenir.  
  
2.  Açık **veri kaynakları** penceresini genişletin **müşteriler** düğümü.  
  
3.  Seçin **CompanyName** sütun ve sonra görünen açılan oku tıklatın.  
  
4.  Seçin **NamedRange** sürükleyin ve açılan liste **CompanyName** sütun hücreye **A1**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `companyNameNamedRange` hücresinde oluşturulan **A1**. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `customersBindingSource`, bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> örnek projeye eklenir. Denetimin bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı <xref:System.Data.DataSet> örneği.  
  
5.  Seçin **CustomerID** sütununda **veri kaynakları** penceresinde ve sonra görünen açılan oku tıklatın.  
  
6.  Tıklayın **NamedRange** sürükleyin ve açılan liste **CustomerID** sütun hücreye **B1**.  
  
7.  Başka bir <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `customerIDNamedRange` hücresinde oluşturulan **B1**ve bağlı <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Dört düğme eklemek için  
  
1. Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ekleme bir <xref:System.Windows.Forms.Button> hücre denetimi **A3** çalışma sayfası.  
  
    Bu düğme adlı `Button1`.  
  
2. Adları gösterildiği gibi böylece bu sırayla aşağıdaki hücrelere üç daha fazla düğme ekleyin:  
  
   |Hücre|(Ad)|  
   |----------|--------------|  
   |B3|BUTTON2|  
   |C3|Button3|  
   |D3|Button4|  
  
   Metin ve düğme eklemek için sonraki adımdır C# olay işleyicileri ekleyin.  
  
## <a name="initialize-the-controls"></a>Denetimleri başlatılamıyor  
 Düğme metnini ayarlayın ve ekleme sırasında olay işleyicileri <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olay.  
  
### <a name="to-initialize-the-controls"></a>Denetimleri başlatmak için  
  
1. İçinde **Çözüm Gezgini**, sağ **Sheet1.vb** veya **Sheet1.cs**ve ardından **Kodu Görüntüle** kısayol menüsünde.  
  
2. Aşağıdaki kodu ekleyin `Sheet1_Startup` her düğme metnini ayarlamak için yöntemi.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. Yalnızca C# için olay işleyicileri düğme için tıklama olayları için ekleme `Sheet1_Startup` yöntemi.  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   Şimdi işlemek için kod ekleyin <xref:System.Windows.Forms.Control.Click> olayları düğmelerinin kullanıcı kayıtlarda gözatabilirsiniz.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Kayıtlar arasında gezinmeye olanak sağlamak için kod ekleyin  
 Kodu <xref:System.Windows.Forms.Control.Click> Kayıtlarda gezinmek için her düğmesi olay işleyicisi.  
  
### <a name="to-move-to-the-first-record"></a>İlk kayda taşımak için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button1` düğmesini ve ilk kayda taşımak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Önceki kayda taşımak için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button2` düğme ve bir konuma geri taşımak için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Sonraki kayda taşımak için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button3` düğmesini ve Button3 için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Son kayda için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button4` düğmesini ve son kayda gitmek için aşağıdaki kodu ekleyin:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık çalışma kitabındaki veritabanı kayıtları arasında göz atabilirsiniz emin olmak için test edebilirsiniz.  
  
### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  İlk kayıt hücrelerde göründüğünden emin olun **A1** ve **B1**.  
  
3.  Tıklayın **>** (`Button3`) düğmesine tıklayın ve sonraki kaydın hücresinde göründüğünden emin olun **A1** ve **B1**.  
  
4.  Kaydı beklendiği gibi değiştirir onaylamak için diğer kaydırma düğmelerine tıklayın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, bir veritabanında bir alan için bir adlandırılmış aralık bağlama hakkındaki temel bilgileri gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Böylece çevrimdışı kullanılabilir verileri önbelleğe alın. Daha fazla bilgi için [nasıl yapılır: çevrimdışı veya sunucuda kullanmak için verileri önbelleğe](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Bir tabloda birden fazla sütuna hücreler yerine bir alan bağlayın. Daha fazla bilgi için [izlenecek yol: belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Kullanım bir <xref:System.Windows.Forms.BindingNavigator> denetimi kayıtlarda gezinin. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingNavigator denetimi ile verilerde gezinme](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)   
 [İzlenecek yol: Belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  