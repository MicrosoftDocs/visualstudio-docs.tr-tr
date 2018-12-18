---
title: 'Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3a31bac6b3cbd13fcff8c841c9947e8c14f8984a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839771"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme
  Konak kontrolü bir veri kaynağına bağlama ve veri kaynağını denetimi verilerde yapılan değişikliklerle güncelleştirin. Bu işlemde iki ana adım vardır:  
  
1. Bellek içi veri kaynağına denetiminde değiştirilen verileri ile güncelleştirin. Genellikle, bellek içi veri kaynağı, bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya başka bir veri nesnesi.  
  
2. Veritabanı, bellek içi veri kaynağı değiştirilmiş verileri güncelleştirin. Bu seçenek, yalnızca veri kaynağı bir SQL Server veya Microsoft Office Access veritabanı gibi bir arka uç veritabanı bağlıysa geçerlidir.  
  
   Konak denetimleri ve veri bağlama hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md) ve [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="update-the-in-memory-data-source"></a>Bellek içi veri kaynağını güncelleştirme  
 Varsayılan olarak, basit veri bağlama (örneğin, içerik denetimleri bir Word belgesi veya Excel çalışma sayfasındaki bir adlandırılmış aralık denetimi) etkinleştirme konak denetimleri bellek içi veri kaynağına veri değişikliklerini kaydetmeyin. Diğer bir deyişle, son kullanıcı konak kontrolü değeri değiştirir ve ardından bir denetimin dışındaki bir yere gider, yeni değer denetiminde veri kaynağı için otomatik olarak kaydedilmez.  
  
 Verileri veri kaynağına kaydetmek için çalışma zamanında belirli bir olaya yanıt olarak veri kaynağını güncelleştirir kod yazabileceğiniz veya denetiminde değeri değiştiğinde otomatik olarak veri kaynağını güncelleştirmek için denetimi yapılandırabilirsiniz.  
  
 Kaydetmeniz gerekmez <xref:Microsoft.Office.Tools.Excel.ListObject> bellek içi veri kaynağına değiştirir. Bağladığınızda bir <xref:Microsoft.Office.Tools.Excel.ListObject> veri denetimine <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi otomatik olarak yapılan değişiklikleri kaydeder bellek içi veri kaynağına ek kod gerek kalmadan.  
  
### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Çalışma zamanında bellek içi veri kaynağını güncelleştirmek için  
  
-   Çağrı <xref:System.Windows.Forms.Binding.WriteValue%2A> yöntemi <xref:System.Windows.Forms.Binding> nesnesini denetimi veri kaynağına bağlar.  
  
     Aşağıdaki örnek yapılan değişiklikleri kaydeder. bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi veri kaynağı bir Excel çalışma sayfasındaki. Bu örnekte, sahibi olduğunuzu varsayar bir <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `namedRange1` ile kendi <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğe bir veri kaynağında bir alan için.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-update-the-in-memory-data-source"></a>Bellek içi veri kaynağı otomatik olarak güncelleştir  
 Bellek içi veri kaynağı otomatik olarak güncelleştirilir, böylece bir denetim de yapılandırabilirsiniz. Bir belge düzeyi projede kod veya tasarımcı kullanarak bunu yapabilirsiniz. Bir VSTO eklenti projesinde kodu kullanmanız gerekir.  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Kod kullanarak bellek içi veri kaynağı otomatik olarak güncelleştirilecek bir denetimi ayarlama  
  
1. ' In modunu kullanmak <xref:System.Windows.Forms.Binding> nesnesini denetimi veri kaynağına bağlar. Veri kaynağını güncelleştirmek için iki seçenek vardır:  
  
   - Denetim doğrulandığında, veri kaynağını güncelleştirmek için System.Windows.Forms.DataSourceUpdateMode.OnValidation bu özelliği ayarlayın.  
  
   - Denetimin veriye bağlı özelliğinin değeri değiştiğinde veri kaynağını güncelleştirmek için System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged bu özelliği ayarlayın.  
  
     > [!NOTE]  
     >  Word Belge değişikliği veya denetim değişikliği bildirimleri gerçekleştirdiğinden System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged seçeneği Word konak denetimleri için geçerli değildir. Ancak, bu seçenek, Word belgelerine Windows Forms denetimleri için kullanılabilir.  
  
     Aşağıdaki örnek yapılandırır bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetiminde değeri değiştiğinde otomatik olarak veri kaynağını güncelleştirmek için denetimi. Bu örnekte, sahibi olduğunuzu varsayar bir <xref:Microsoft.Office.Tools.Excel.NamedRange> adlı Denetim `namedRange1` ile kendi <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğe bir veri kaynağında bir alan için.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Tasarımcıyı kullanarak bellek içi veri kaynağı otomatik olarak güncelleştirilecek bir denetimi ayarlama  
  
1.  Visual Studio'da Word belgesi veya Excel çalışma kitabını tasarımcıda açın.  
  
2.  Veri kaynağı otomatik olarak güncelleştirmek istediğiniz denetime tıklayın.  
  
3.  İçinde **özellikleri** penceresini genişletin **(DataBindings)** özelliği.  
  
4.  Yanındaki **(Gelişmiş)** özelliği, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton ekran")).  
  
5.  İçinde **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, tıklayın **veri kaynağı güncelleştirme modu** aşağı açılır ve aşağıdaki değerlerden birini seçin:  
  
    -   Denetim doğrulandığında, veri kaynağını güncelleştirmek için seçin **OnValidation'ı**.  
  
    -   Denetimin veriye bağlı özelliğinin değeri değiştiğinde veri kaynağını güncelleştirmek için seçin **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  **OnPropertyChanged** seçeneği çünkü Word Belge değişikliği veya denetim değişikliği bildirimlerini Word konak denetimleri için uygulanmaz. Ancak, bu seçenek, Word belgelerine Windows Forms denetimleri için kullanılabilir.  
  
6.  Kapat **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu.  
  
## <a name="update-the-database"></a>Veritabanını Güncelleştir  
 Bellek içi veri kaynağı bir veritabanıyla ilişkili ise, veri kaynağını değişikliklerle veritabanı güncelleştirmeniz gerekir. Bir veritabanını güncelleştirme hakkında daha fazla bilgi için bkz. [verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md) ve [TableAdapter kullanarak veri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
### <a name="to-update-the-database"></a>Veritabanını güncellemek için  
  
1.  Çağrı <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi <xref:System.Windows.Forms.BindingSource> denetimi.  
  
     <xref:System.Windows.Forms.BindingSource> Veriye bağlı denetim için bir belge veya çalışma kitabı tasarım zamanında eklediğinizde, otomatik olarak oluşturulur. <xref:System.Windows.Forms.BindingSource> Denetim türü belirtilmiş veri kümesi, projenizdeki bağlanır. Daha fazla bilgi için [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     Aşağıdaki kod örneği, projenizin içerdiğini varsaymaktadır bir <xref:System.Windows.Forms.BindingSource> adlı `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Çağrı `Update` projenizde oluşturulan TableAdapter'ın yöntemi.  
  
     Veriye bağlı denetim için bir belge veya çalışma kitabı tasarım zamanında eklediğinizde, TableAdapter otomatik olarak oluşturulur. Yazılmış veri kümesi, projenizdeki, TableAdapter veritabanına bağlanır. Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Aşağıdaki kod örneği, Northwind veritabanındaki Müşteriler tablosunu bağlantı olduğunu ve projenizi adlı bir TableAdapter içeren varsayar `customersTableAdapter` ve adlı bir türü belirtilmiş veri kümesi `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)    
 [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Nasıl yapılır: belgeleri hizmet verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  