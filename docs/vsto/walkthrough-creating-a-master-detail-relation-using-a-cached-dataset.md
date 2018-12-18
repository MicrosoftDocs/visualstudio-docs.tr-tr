---
title: 'İzlenecek yol: önbellekteki veri kümesini kullanarak bir ana ayrıntı ilişkisi oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d877eae119c922939ea61007a845e5bd7049076
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933163"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>İzlenecek yol: önbellekteki veri kümesini kullanarak bir ana ayrıntı ilişkisi oluşturma
  Bu izlenecek yol, bir çalışma sayfasına bir ana/ayrıntı ilişkisi oluşturma ve böylece bu çözüm çevrimdışı kullanılabilir verileri önbelleğe alma gösterir.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Bir çalışma sayfasına denetimler ekleme.  
  
-   Bir veri kümesini oluşturan bir çalışma sayfasına önbelleğe alınacak ayarlayın.  
  
-   Kayıtlar arasında gezinmeye olanak sağlamak için kod ekleyin.  
  
-   Projenizi test edin.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   SQL Server Northwind örnek veritabanına erişim. Veritabanı geliştirme bilgisayarınızda veya bir sunucuda olabilir.  
  
-   SQL Server veritabanına yazma ve okuma izni.  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 Bu adımda, bir Excel çalışma kitabı projesi oluşturur.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1. Adlı bir Excel çalışma kitabı projesi oluşturun **My ana öğe-ayrıntı**, Visual Basic veya C# kullanarak. Emin olun **yeni belge oluşturma** seçilir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **My ana öğe-ayrıntı** için proje **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
 Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.  
  
### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3. Seçin **veritabanı** ve ardından **sonraki**.  
  
4. Northwind örnek SQL Server veritabanıyla kurulan veri bağlantısı seçin veya yeni bir bağlantı kullanarak eklemek **yeni bağlantı** düğmesi.  
  
5. Seçtikten veya bir bağlantıyı oluşturduktan sonra tıklayın **sonraki**.  
  
6. Seçili olduğunda görüntüleyeceği bağlantı kaydetme seçeneğini ve ardından temizlemek **sonraki**.  
  
7. Genişletin **tabloları** düğümünde **veritabanı nesnelerinin** penceresi.  
  
8. Seçin **siparişler** tablo ve **sipariş ayrıntıları** tablo.  
  
9. **Son**'a tıklayın.  
  
   Sihirbaz iki tabloya ekler **veri kaynakları** penceresi. Projenize görünür olan bir türü belirtilmiş veri kümesi de ekler **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Bu adımda, ilk çalışma sayfası için bir adlandırılmış aralık, Liste nesnesine ve iki düğme ekleyeceksiniz. İlk olarak, adlandırılmış aralık ve liste nesneden ekleyin **veri kaynakları** penceresi otomatik olarak bir veri kaynağına bağlı olacak şekilde. Düğmelerden ekleyeceğimize **araç kutusu**.  
  
### <a name="to-add-a-named-range-and-a-list-object"></a>Adlandırılmış aralık ve Liste nesnesine eklemek için  
  
1.  Doğrulayın **My ana Detail.xlsx** Visual Studio tasarımcıda açık çalışma kitabı ile **Sayfa1** görüntülenir.  
  
2.  Açık **veri kaynakları** penceresini genişletin **siparişler** düğümü.  
  
3.  Seçin **OrderID** sütun ve sonra görünen açılan oku tıklatın.  
  
4.  Tıklayın **NamedRange** sürükleyin ve açılan liste **OrderID** sütun hücreye **A2**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `OrderIDNamedRange` hücresinde oluşturulan **A2**. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `OrdersBindingSource`, bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> örnek projeye eklenir. Denetimin bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı <xref:System.Data.DataSet> örneği.  
  
5.  Aşağı kaydırın altında sütunları geçmiş **siparişler** tablo. Listenin en altta **sipariş ayrıntıları** tablo; çünkü bir alt öğesidir **siparişler** tablo. Bu seçeneği belirleyin **sipariş ayrıntıları** değil, aynı düzeyde olan bir tablo **siparişler** tablosuna ve sonra görünen açılan oku tıklatın.  
  
6.  Tıklayın **ListObject** sürükleyin ve açılan liste **OrderDetails** hücre tabloya **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim **Order DetailsListObject** hücresinde oluşturulan **A6**ve bağlı <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-two-buttons"></a>İki düğme eklemek için  
  
1. Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ekleme bir <xref:System.Windows.Forms.Button> hücre denetimi **A3** çalışma sayfası.  
  
    Bu düğme adlı `Button1`.  
  
2. Başka bir <xref:System.Windows.Forms.Button> hücre denetimi **B3** çalışma sayfası.  
  
    Bu düğme adlı `Button2`.  
  
   Ardından, veri kümesini önbelleğe alınacak işaretleyin.  
  
## <a name="cache-the-dataset"></a>Veri kümesini önbelleğe al  
 Veri kümesini veri kümesi genel ve ayar yaparak belgede önbelleğe işaretlemek **CacheInDocument** özelliği.  
  
### <a name="to-cache-the-dataset"></a>Veri kümesi önbelleğe almak için  
  
1. Seçin **NorthwindDataSet** bileşen tepsisinde.  
  
2. İçinde **özellikleri** penceresinde değişiklik **değiştiriciler** özelliğini **genel**.  
  
    Önbelleğe alma etkinleştirmeden önce veri kümeleri ortak olmalıdır.  
  
3. Değişiklik **CacheInDocument** özelliğini **True**.  
  
   Sonraki adımda, düğmelerin metin ekleyin ve C# dilinde olay işleyicileri ' bağlamak için kodu ekleyin sağlamaktır.  
  
## <a name="initialize-the-controls"></a>Denetimleri başlatılamıyor  
 Düğme metnini ayarlayın ve ekleme sırasında olay işleyicileri <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> olay.  
  
### <a name="to-initialize-the-data-and-the-controls"></a>Verileri ve denetimleri başlatılamadı  
  
1.  İçinde **Çözüm Gezgini**, sağ **Sheet1.vb** veya **Sheet1.cs**ve ardından **Kodu Görüntüle** kısayol menüsünde.  
  
2.  Aşağıdaki kodu ekleyin `Sheet1_Startup` düğme metnini ayarlamak için yöntemi.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Yalnızca C# için olay işleyicileri düğme için tıklama olayları için ekleme `Sheet1_Startup` yöntemi.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Kayıtlar arasında gezinmeye olanak sağlamak için kod ekleyin  
 Kodu <xref:System.Windows.Forms.Control.Click> Kayıtlarda gezinmek için her düğmesi olay işleyicisi.  
  
### <a name="to-scroll-through-the-records"></a>Kayıtlarda gezinmek için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button1`, geriye doğru Kayıtlarda gezinmek için aşağıdaki kodu ekleyin:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `Button2`, kayıtlar arasında ilerlemek için aşağıdaki kodu ekleyin:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık çalışma kitabındaki verilerin beklendiği gibi göründüğünü ve çözümü çevrimdışı kullanabildiğinizden emin olmak için test edebilirsiniz.  
  
### <a name="to-test-the-data-caching"></a>Verileri önbelleğe almayı test etmek için  
  
1.  Tuşuna **F5**.  
  
2.  Adlandırılmış aralık ve liste nesnesi veri kaynağından alınan verilerle doldurulmuş doğrulayın.  
  
3.  Kayıtları düğmelere tıklayarak gezinin.  
  
4.  Çalışma kitabını kaydedin ve ardından çalışma kitabı ve Visual Studio'yu kapatın.  
  
5.  Veritabanı bağlantısı devre dışı bırakın. Veritabanı bir sunucuda bulunuyorsa, ağ kablosu bilgisayarınızdan çıkarın veya veritabanı geliştirme bilgisayarınızda ise SQL Server hizmetini durdurun.  
  
6.  Excel'i açın ve ardından açın **My ana Detail.xlsx** gelen *\bin* dizin (*\My Master-Detail\bin* Visual Basic'te veya *\My Master-Detail\bin\ hata ayıklama* C#).  
  
7.  Bazı çalışma kesildiğinde normal şekilde çalıştığını görmek için kayıtlar kaydırın.  
  
8.  Veritabanına bağlanın. Veritabanı bir sunucuda bulunuyorsa, bilgisayar ağa yeniden bağlanın veya veritabanı geliştirme bilgisayarınızda ise SQL Server hizmetini başlatın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, çalışma sayfasında ana/ayrıntı veri ilişki oluşturma ve bir veri kümesi önbelleğe alma temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Çözümü dağıtın. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)   
 [Verileri önbelleğe](../vsto/caching-data.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)  
  
  