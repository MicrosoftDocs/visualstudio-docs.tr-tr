---
title: 'İzlenecek yol: Belge düzeyi projede karmaşık veri bağlama'
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
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6886908f01ceaeb36ed83ba0970ef250873d69c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841890"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>İzlenecek yol: Belge düzeyi projede karmaşık veri bağlama
  Bu izlenecek yol, bir belge düzeyi projede karmaşık veri bağlama ilişkin temel bilgileri gösterir. Alanları Northwind SQL Server veritabanındaki birden çok hücre Microsoft Office Excel çalışma sayfasındaki bağlayabilirsiniz.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Veri kaynağı, çalışma kitabı projenize ekleme.  
  
- Çalışma sayfasına verilere bağlı denetimler ekleme.  
  
- Veri değişiklikleri veritabanına geri kaydediliyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   SQL Server Northwind örnek veritabanı ile bir sunucu erişim.  
  
-   SQL Server veritabanına yazma ve okuma izni.  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 İlk adım, bir Excel çalışma kitabı projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **karmaşık veri bağlaması**. Sihirbazda **yeni belge oluşturma**.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **karmaşık veri bağlaması** için proje **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
 Kullanım **veri kaynakları** penceresinin bir türü belirtilmiş veri kümesi projenize ekleyin.  
  
### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1. Varsa **veri kaynakları** penceresi görünür değilse, bunu, menü çubuğundan seçme görüntüleyebilir **görünümü** > **diğer Windows**  >   **Veri kaynakları**.  
  
2. Seçin **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3. Seçin **veritabanı** ve ardından **sonraki**.  
  
4. Northwind örnek SQL Server veritabanıyla kurulan veri bağlantısı seçin veya yeni bir bağlantı kullanarak eklemek **yeni bağlantı** düğmesi.  
  
5. Bağlantı seçili veya oluşturulduktan sonra tıklayın **sonraki**.  
  
6. Seçili olduğunda görüntüleyeceği bağlantı kaydetme seçeneğini ve ardından temizlemek **sonraki**.  
  
7. Genişletin **tabloları** düğümünde **veritabanı nesnelerinin** penceresi.  
  
8. Yanındaki onay kutusunu işaretleyin **çalışanlar** tablo.  
  
9. **Son**'a tıklayın.  
  
   Sihirbaz ekler **çalışanlar** tablo **veri kaynakları** penceresi. Projenize görünür olan bir türü belirtilmiş veri kümesi de ekler **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Bir çalışma sayfası görüntüler **çalışanlar** çalışma kitabını açtığınızda tablo. Kullanıcılar, verilerde değişiklik yapabilir ve ardından bir düğmeye tıklayarak bu değişiklikleri veritabanına geri kaydedin mümkün olacaktır.  
  
 Çalışma tablosuna otomatik olarak bağlamak için ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasından denetimine **veri kaynakları** penceresi. Kullanıcı değişiklikleri kaydetmek için seçeneği vermek için ekleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu**.  
  
#### <a name="to-add-a-list-object"></a>Bir liste nesnesi eklemek için  
  
1.  Doğrulayın **My karmaşık veri Binding.xlsx** Visual Studio tasarımcıda açık çalışma kitabı ile **Sayfa1** görüntülenir.  
  
2.  Açık **veri kaynakları** penceresi ve select **çalışanlar** düğümü.  
  
3.  Görüntülenen açılan oka tıklayın.  
  
4.  Seçin **ListObject** aşağı açılan listesinde.  
  
5.  Sürükleme **çalışanlar** hücre tabloya **A6**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> adlı Denetim `EmployeesListObject` hücresinde oluşturulan **A6**. Aynı anda bir <xref:System.Windows.Forms.BindingSource> adlı `EmployeesBindingSource`, bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> örnek projeye eklenir. Denetimin bağlı <xref:System.Windows.Forms.BindingSource>, sırayla bağlı <xref:System.Data.DataSet> örneği.  
  
### <a name="to-add-a-button"></a>Bir düğme eklemek için  
  
1. Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ekleme bir <xref:System.Windows.Forms.Button> hücre denetimi **A4** çalışma sayfası.  
  
   Sonraki adım çalışma sayfası açıldığında düğmeye metin eklemektir.  
  
## <a name="initialize-the-control"></a>Denetimi başlatmak  
 Düğmeye metin eklemek <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> olay işleyicisi.  
  
### <a name="to-initialize-the-control"></a>Denetimi başlatmak için  
  
1. İçinde **Çözüm Gezgini**, sağ **Sheet1.vb** veya **Sheet1.cs**ve ardından **Kodu Görüntüle** kısayol menüsünde.  
  
2. Aşağıdaki kodu ekleyin `Sheet1_Startup` b metnini ayarlamak için yöntemi`utton`.  
  
    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3. Yalnızca C# için eklemek için bir olay işleyicisi <xref:System.Windows.Forms.Control.Click> olaya `Sheet1_Startup` yöntemi.  
  
    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
   Şimdi işlemek için kod ekleyin <xref:System.Windows.Forms.Control.Click> düğmesinin olayı.  
  
## <a name="save-changes-to-the-database"></a>Değişiklikleri veritabanına kaydetmek  
 Herhangi bir değişiklik yapılmıştır açıkça veritabanına geri kaydedilene kadar yalnızca yerel veri kümesindeki verileri yok.  
  
### <a name="to-save-changes-to-the-database"></a>Değişiklikleri veritabanına kaydetmek için  
  
1.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Click> olayı `button`ve veritabanına geri kümesinde yapılan tüm değişiklikleri kaydetmek için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık verilerin beklendiği gibi göründüğünü ve liste nesnesi verileri işleyebileceğiniz doğrulamak için çalışma kitabınızı test edebilirsiniz.  
  
### <a name="to-test-the-data-binding"></a>Veri bağlamayı test etmek için  
  
-   Tuşuna **F5**.  
  
     Çalışma kitabınızı açtığında, liste nesnesi verilerle doldurulmuş doğrulayın **çalışanlar** tablo.  
  
### <a name="to-modify-data"></a>Verileri değiştirmek için  
  
1.  Bir hücreyi tıklatın **B7**, adı içermelidir **doğan**.  
  
2.  Adı **Anderson**ve tuşuna **Enter**.  
  
### <a name="to-modify-a-column-header"></a>Bir sütun başlığını değiştirme  
  
1.  Sütun başlığını içeren hücreyi tıklatın **LastName**.  
  
2.  Tür **Soyadı**iki sözcükleri arasına bir boşluk içeren ve tuşuna **Enter**.  
  
### <a name="to-save-data"></a>Verileri kaydetmek için  
  
1.  Tıklayın **Kaydet** çalışma sayfasında.  
  
2.  Excel'den çıkın. Tıklayın **Hayır** yaptığınız değişiklikleri kaydetmek isteyip istemediğiniz sorulduğunda.  
  
3.  Tuşuna **F5** projeyi yeniden çalıştırın.  
  
     Liste nesnesinin verilerle doldurulmuş **çalışanlar** tablo.  
  
4.  Dikkat hücresindeki **B7** hala **Anderson**, veri olduğu yapılan ve veritabanına kaydedilmiş değiştirin. Sütun üst bilgisine **LastName** geri özgün biçimlerinde boşluk, çünkü sütun üst bilgisine veritabanına bağlı değil ve çalışma sayfası için yaptığınız değişiklikleri kaydetmedi değiştirildi.  
  
### <a name="to-add-new-rows"></a>Yeni satır eklemek için  
  
1. Liste nesnesi içinde bir hücre seçin.  
  
    Bir yıldız işareti ile listenin en yeni bir satır görüntülenir (**\\***) ilk hücreye yeni bir satır.  
  
2. Aşağıdaki bilgileri boş satır ekleyin.  
  
   |EmployeeID|Soyadı|FirstName|Başlık|  
   |----------------|--------------|---------------|-----------|  
   |10|Aslan|Halil|Satış Yöneticisi|  
  
### <a name="to-delete-rows"></a>Satırları silmek için  
  
-   Sayısı 16 (satır 16) en sol tarafında çalışma sağ tıklayın ve ardından **Sil**.  
  
### <a name="to-sort-the-rows-in-the-list"></a>Listedeki satırlar sıralamak için  
  
1.  Listenin içinde bir hücre seçin.  
  
     Her bir sütun başlığına ok düğmelerini görünür.  
  
2.  Ok düğmesi **Soyadı** sütun başlığı.  
  
3.  Tıklayın **Sıralama artan**.  
  
     Satır son adlarına göre alfabetik olarak sıralanır.  
  
### <a name="to-filter-information"></a>Filtre bilgilerine  
  
1.  Listenin içinde bir hücre seçin.  
  
2.  Ok düğmesi **başlık** sütun başlığı.  
  
3.  Tıklayın **satış temsilcisi**.  
  
     Liste içeren satırları gösterir **satış temsilcisine** içinde **başlık** sütun.  
  
4.  Ok düğmesi **başlık** sütun başlığını tekrar.  
  
5.  Tıklayın **(Tümü)**.  
  
     Filtre kaldırılır ve tüm satırların görünmesini.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, bir tablo, Liste nesnesine bir veritabanında bağlama hakkındaki temel bilgileri gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Böylece çevrimdışı kullanılabilir verileri önbelleğe alın. Daha fazla bilgi için [nasıl yapılır: çevrimdışı veya sunucuda kullanmak için verileri önbelleğe](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Çözümü dağıtın. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
-   Bir alan ve tablo arasında bir ana/ayrıntı ilişkisi oluşturun. Daha fazla bilgi için [izlenecek yol: önbellekteki veri kümesini kullanarak bir ana ayrıntı ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)   
 [İzlenecek yol: Belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  