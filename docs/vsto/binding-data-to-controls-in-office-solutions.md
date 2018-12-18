---
title: Office çözümlerinde denetimlere veri bağlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b5d7a52e4f8b9e6c9741d3b62bc18b2d4cb66f7
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248026"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Office çözümlerinde denetimlere veri bağlama
  Windows Forms denetimlerine bağlayabilirsiniz ve *konak denetimlerini* Microsoft Office Word belgesi veya Microsoft Office Excel çalışma sayfasındaki denetimleri otomatik olarak verileri görüntülemek için bir veri kaynağı. Verileri, uygulama düzeyinde hem belge düzeyi projeler denetimlere bağlayabilirsiniz.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Konak denetimleri, Word ve Excel nesne modellerinde gibi Word içerik denetimleri ve Excel aralıkları adlı nesneler genişletin. Daha fazla bilgi için [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
 Konak denetimlerinin ve Windows Forms kullanan her ikisini de destekler Windows Forms veri bağlama modelini *basit veri bağlama* ve *karmaşık veri bağlama* veri kümeleri ve veri tabloları gibi veri kaynaklarına. Windows Forms veri bağlama modeli hakkında tam bilgi için bkz. [ve Windows Forms veri bağlama](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![video bağlantı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [nasıl yaparım? Veritabanı verileri Excel'de mı tüketiliyor? ](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>Basit veri bağlama  
 Denetim özelliği, bir veri tablosunda bir değer gibi bir tek veri öğesine bağlandığında basit veri bağlama yok. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolünde bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> bir veri kümesi alanına bağlanabilir özelliği. Alanın veri kümesinde değişirse, adlandırılmış aralık değeri de değişir. Tüm denetimleri dışında konak <xref:Microsoft.Office.Tools.Word.XMLNodes> denetlemek, basit veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Word.XMLNodes> Koleksiyonu denetimidir ve bu nedenle veri bağlamayı desteklemez.  
  
 Basit veri bağlama için bir konak denetimi gerçekleştirmek için ekleme bir <xref:System.Windows.Forms.Binding> için `DataBindings` denetiminin özelliği. A <xref:System.Windows.Forms.Binding> nesne denetimin özellik değeri ve bir veri öğesinin değeri arasında basit bağlama temsil eder.  
  
 Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğini bir belge düzeyi projede bir veri öğesi.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Basit veri bağlama gösteren izlenecek yollar için bkz. [izlenecek yol: Belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) için belge düzeyi projesi ve [izlenecek yol: VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) VSTO eklentisi projesi için.  
  
## <a name="complex-data-binding"></a>Karmaşık veri bağlama  
 Karmaşık veri bağlama denetimi özelliği gibi birden çok sütun bir veri tablosunda birden fazla veri öğesine bağlı olduğunda bulunmaktadır. <xref:Microsoft.Office.Tools.Excel.ListObject> Excel karmaşık veri bağlamayı destekleyen yalnızca konak denetimi için denetim. Ayrıca gibi karmaşık veri bağlamayı destekleyen çok sayıda Windows Forms denetimleri vardır <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 Karmaşık veri bağlama gerçekleştirmek için ayarlanmış `DataSource` karmaşık veri bağlama tarafından desteklenen bir veri kaynağı nesnesi denetimin özellik. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> özelliği <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, bir veri tablosunda birden fazla sütuna bağlanabilir. Tüm verileri veri tablosundaki görünür <xref:Microsoft.Office.Tools.Excel.ListObject> denetim ve veri tablosu değişiklikleri veri olarak <xref:Microsoft.Office.Tools.Excel.ListObject> de değişir. Karmaşık veri bağlama için kullanabileceğiniz veri kaynaklarının listesi için bkz. [Windows Forms tarafından desteklenen veri kaynakları](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Data.DataSet> iki <xref:System.Data.DataTable> nesneleri ve bir tabloları verilerle doldurur. Ardından kod bağlar <xref:Microsoft.Office.Tools.Excel.ListObject> verileri içeren tablo. Bu örnek, bir Excel belge düzeyi projesi içindir.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Karmaşık veri bağlamayı gösteren izlenecek yollar için bkz. [izlenecek yol: Belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) için belge düzeyi projesi ve [izlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) VSTO eklentisi projesi için.  
  
## <a name="display-data-in-documents-and-workbooks"></a>Belgeler ve çalışma kitaplarındaki verileri görüntüle  
 Belge düzeyinde projelerde kullanabileceğiniz **veri kaynakları** penceresinde kolayca belge veya çalışma kitaplarına verilere bağlı denetimler eklemek için kullandığınız, Windows Forms için aynı şekilde. Kullanma hakkında daha fazla bilgi için **veri kaynakları** penceresinde görmek [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md).  
  
### <a name="drag-controls-from-the-data-sources-window"></a>Denetimler veri kaynakları penceresinden sürükleme  
 Bir nesne üzerine sürüklediğinizde bir denetim belgede oluşturulur **veri kaynakları** penceresi. Oluşturulan denetim türü, tek bir veri sütununu veya birden çok sütun veri bağlama bağlıdır.  
  
 Excel için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi, tek tek her alan için çalışma sayfasındaki oluşturulur ve <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, birden çok satır ve sütunları içeren her bir veri aralığı için oluşturulur. Tabloyu seçerek bu varsayılanı değiştirmek ya da, alan **veri kaynakları** penceresini açın ve ardından açılır listeden farklı bir denetim seçme.  
  
 A <xref:Microsoft.Office.Tools.Word.ContentControl> denetim belgeye eklenir. İçerik denetimi türü, seçilen alanın veri türüne bağlıdır.  
  
### <a name="bind-data-in-document-level-projects-at-design-time"></a>Tasarım zamanında belge düzeyinde projelerde veri bağlama  
 Aşağıdaki konular, tasarım zamanında veri bağlama örnekleri gösterir:  
  
-   [Nasıl yapılır: Çalışma sayfalarını veritabanı verileriyle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Nasıl yapılır: Belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Nasıl yapılır: Belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Nasıl yapılır: Belgeleri hizmet verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Nasıl yapılır: Çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="bind-data-in-vsto-add-in-projects"></a>VSTO eklentisi projelerinde veri bağlama  
 Projelerinde, VSTO eklentisi, yalnızca çalışma zamanında denetimler ekleyebilirsiniz. Aşağıdaki konular, çalışma zamanında veri bağlama örnekleri gösterir:  
  
-   [İzlenecek yol: VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="update-data-that-is-bound-to-host-controls"></a>Konak denetimleri ilişkili verileri güncelleştirme  
 Veri bağlama veri kaynağı ve konak kontrolü arasında iki yönlü veri güncelleştirme içerir. Basit veri bağlama, veri kaynağındaki değişiklikleri otomatik olarak ana bilgisayar denetimi yansıtılır, ancak veri kaynağını güncelleştirmek için açık çağrı konak kontrolü değişiklikler gerektirir. Başka bir veri bağlama alan değişikliklerinden eşlik sürece bazı durumlarda, bir veri bağlama alan değişiklikleri kabul nedenidir. Örneğin, iki alan, geçerlilik süresi için diğeri yıllardır deneyiminin olabilir. Deneyimi yaş aşamaz. Bir kullanıcı yaşı 50'den güncelleştirilemiyor 25'i ve ardından 30 deneyiminden 10 sürece isterse, aynı anda değişiklik yapar. Bu sorunu çözmek için güncelleştirmeleri açıkça kod tarafından gönderilen kadar basit veri bağlama ile alanlarını güncelleştirilmez.  
  
 Basit veri bağlamayı etkinleştirmek konak denetimleri veri kaynağını güncelleştirmek için güncelleştirmeleri bellek içi veri kaynağına göndermeniz gerekir (aşağıdaki gibi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>) ve arka uç veritabanı çözümünüzü kullanıyorsa.  
  
 Karmaşık veri bağlama işlemini kullanma gerçekleştirdiğinizde açıkça bellek içi veri kaynağını güncelleştirmek gerekmez <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi. Bu durumda, değişiklikler, bellek içi veri kaynağına ek kod olmadan otomatik olarak gönderilir.  
  
 Daha fazla bilgi için [nasıl yapılır: Bir konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl Yaparım Veritabanı verileri Excel'de mı tüketiliyor?](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)    
 [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Verileri önbelleğe](../vsto/caching-data.md)   
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)  
  
  