---
title: Konak öğelerine ve denetimlerine genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48ce311a767d68ce1402961d2ddf4cf8b673637c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937505"
---
# <a name="host-items-and-host-controls-overview"></a>Konak öğelerine ve denetimlerine genel bakış
  Konak denetimlerinin ve konak öğelerinin programlama modeli için Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan Office çözümlerini sağlamaya yardımcı türleridir. Konak denetimlerinin ve konak öğelerinin Microsoft Office Word ve Microsoft Office Excel, COM, Windows Forms denetimleri gibi yönetilen nesnelerle etkileşim gibi daha fazla alan nesne modelleri ile etkileşim kurma olun.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Konak öğeleri  
 Konak öğeleri, üst nesne modeli hiyerarşi Office projelerinde türlerdir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word ve Excel çözümleri için aşağıdaki konak öğelerini tanımlar:  
  
- <xref:Microsoft.Office.Tools.Word.Document>  
  
- <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
- <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
  Bu türlerinin her biri yerel olarak adlandırılan Word veya Excel nesne modelinde, var olan bir nesneyi genişletir bir *yerel Office nesne*. Örneğin, <xref:Microsoft.Office.Tools.Word.Document> konak öğesi genişletir <xref:Microsoft.Office.Interop.Word.Document> Word için birincil birlikte çalışma derlemesi içinde tanımlanan nesne.  
  
  Konak öğeleri genellikle karşılık gelen Office nesnelerinde ile aynı temel işlevlere sahip, ancak aşağıdaki özelliklerle geliştirilmiştir:  
  
- Konak denetimlerinin ve Windows Forms denetimleri de dahil olmak üzere yönetilen denetimleri barındırma olanağı.  
  
- Daha fazla olay modeli. Bazı belge, çalışma kitabının ve çalışma olayları yerel Word ve Excel nesne modelleri yalnızca uygulama düzeyinde oluşturulur. Konak öğeleri belirli bir belge için olaylarını işlemek daha kolay bu olaylar belge düzeyinde sağlayın.  
  
### <a name="understand-host-items-in-document-level-projects"></a>Belge düzeyi projelerine konak öğeleri anlama  
 Belge düzeyi projelerine konak öğeleri, kodunuz için giriş noktası sağlar ve tasarımcılar çözümünüzü geliştirmenize yardımcı olabilirler.  
  
 <xref:Microsoft.Office.Tools.Word.Document> Ve <xref:Microsoft.Office.Tools.Excel.Worksheet> ilişkili belge veya çalışma, bir Windows Forms Tasarımcısı gibi görsel temsilini tasarımcıları konak öğeleri. Bu tasarımcı, belge veya çalışma doğrudan Word veya Excel içeriğini değiştirmek için ve denetimleri tasarım yüzeyine sürüklemek için kullanabilirsiniz. Daha fazla bilgi için [belge konak öğesi](../vsto/document-host-item.md) ve [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> Konak öğesi, bir kullanıcı arabirimine sahip denetimler için kapsayıcı olarak davranmaz. Bunun yerine, bu konak öğesi için tasarımcı gibi bir bileşeni sürükleyin olanak tanıyan bir bileşen Tepsisi işlevleri bir <xref:System.Data.DataSet>, kendi tasarım yüzeyine. Daha fazla bilgi için [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).  
  
 Konak öğeleri programlı olarak belge düzeyi projeleri oluşturulamaz. Bunun yerine, `ThisDocument`, `ThisWorkbook`, veya `Sheet` *n* Visual Studio projenize tasarım zamanında otomatik olarak oluşturur. sınıf. Konak öğeleri oluşturulan bu sınıflar türetilen ve kodunuz için giriş noktası sağlar. Daha fazla bilgi için [konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understand-host-items-in-vsto-add-in-projects"></a>VSTO eklentisi projelerine konak öğeleri anlama  
 Bir VSTO eklenti oluşturduğunuzda varsayılan olarak herhangi bir ana bilgisayar öğeleri erişiminiz olması değil. Ancak, oluşturabileceğiniz <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, ve <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğelerini Word ve Excel VSTO eklentileri zamanında.  
  
 Bir konak öğesi oluşturduktan sonra belgelere denetimler ekleme gibi görevleri gerçekleştirebilirsiniz. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Konak denetimleri  
 Konak denetimleri uzatma Word ve Excel nesne modellerinde çeşitli kullanıcı arabirimi (UI) nesneleri gibi `Microsoft.Office.Interop.Word.ContentControl` ve <xref:Microsoft.Office.Interop.Excel.Range> nesneleri.  
  
 Aşağıdaki konak denetimleri Excel projeleri için kullanılabilir:  
  
- [Grafik denetimi](../vsto/chart-control.md)  
  
- [ListObject denetimi](../vsto/listobject-control.md)  
  
- [NamedRange denetimi](../vsto/namedrange-control.md)  
  
- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)  
  
  Aşağıdaki konak denetimleri Word projeleri için kullanılabilir:  
  
- [Yer işareti denetimi](../vsto/bookmark-control.md)  
  
- [İçerik denetimleri](../vsto/content-controls.md)  
  
- [XMLNode denetimi](../vsto/xmlnode-control.md)  
  
- [XMLNodes denetimi](../vsto/xmlnodes-control.md)  
  
  Office belgeleri için eklenen konak denetimleri, yerel Office nesneleri gibi davranırlar; Ancak, olayları ve veri bağlama becerileri gibi ek işlevler konak denetimleri vardır. Örneğin, istediğinizde yerel olaylarını yakalamak <xref:Microsoft.Office.Interop.Excel.Range> Excel'de gereken ilk ele değişiklik olayı çalışma sayfası nesnesi. İçinde değişikliğinin olup olmadığını belirlemeniz gerekir sonra <xref:Microsoft.Office.Interop.Excel.Range>. Buna karşılık, <xref:Microsoft.Office.Tools.Excel.NamedRange> konak kontrolünde bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> doğrudan işleyen olayı.  
  
  Konak denetimlerinin ve konak öğesi arasındaki ilişki, bir Windows formu ve Windows Forms denetimlerinde arasındaki ilişkiye benzer. Bir Windows formunda metin kutusu denetimi yerleştirin gibi yerleştirdiğiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi. Konak denetimlerinin ve konak öğeleri arasındaki ilişki aşağıda gösterilmiştir.  
  
  ![Konak denetimlerinin ve konak öğeleri arasındaki ilişki](../vsto/media/hostitemscontrols.png "konak denetimlerinin ve konak öğeleri arasındaki ilişki")  
  
  Windows Forms denetimleri, Office çözümlerinde doğrudan Word ve Excel belge yüzeyine ekleyerek de kullanabilirsiniz. Daha fazla bilgi için [Windows Forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  Bir Word alt konak veya Windows Forms denetimleri ekleme desteklenmiyor.  
  
### <a name="add-host-controls-to-your-documents"></a>Konak denetimleri, belgelere ekleme  
 Belge düzeyinde projelerde, konak denetimleri Word belgelerine veya Excel çalışma sayfaları için tasarım zamanında aşağıdaki yollarla ekleyebilirsiniz:  
  
- Konak denetimleri ekleme belgenize aynı şekilde tasarım zamanında bir yerel nesne eklersiniz.  
  
- Konak denetimleri sürükleyin **araç kutusu** belgeler ve çalışma. Excel konak denetimleri kullanılabilir **Excel denetimleri** Excel projeleri ve Word konak denetimleri kullanılabilir sekmede **Word denetimleri** Word projelerinde sekmesi.  
  
- Konak denetimleri sürükleyin **veri kaynakları** penceresinden belgelerinizi ve çalışma. Bu, zaten verilere bağlı denetimler eklemenizi sağlar. Daha fazla bilgi için [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
  Belge düzeyi ve VSTO eklentisi projeleri, belgelere, çalışma zamanında bazı konak denetimleri de ekleyebilirsiniz. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Konak denetimleri belgelere ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
- [Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
- [Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
- [Nasıl yapılır: içerik ekleme denetimlerine Word belgeleri](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
- [Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
- [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="name-host-controls"></a>Adı konak denetimleri  
 Bir konak denetimi sürüklediğinizde **araç kutusu** belgenize denetimi otomatik olarak denetim türü, sonunda artan bir sayı ile kullanarak olarak adlandırılır. Örneğin, yer işaretleri adlandırılır **bookmark1**, **bookmark2**ve benzeri. Denetim eklemek için yerel bir işlev Word veya Excel kullanıyorsanız, kodu oluşturduğunuz sırada belirli bir ad verebilirsiniz. Değerini değiştirerek denetimlerinizi de yeniden adlandırabilirsiniz **adı** özelliğinde **özellikleri** penceresi.  
  
> [!NOTE]  
>  Konak denetimleri adı ayrılmış sözcükler kullanılamaz. Örneğin eklerseniz, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetiminin çalışma sayfasına ve adla değiştirin **sistem**, projeyi oluşturduğunuzda hatalar oluşur.  
  
### <a name="delete-host-controls"></a>Konak denetimleri Sil  
 Belge düzeyinde projelerde, konak denetimleri tasarım zamanında denetimi Word belgesi veya Excel çalışma sayfası seçip tuşlarına basarak silebilirsiniz **Sil** anahtarı. Ancak kullanmalıdır **ad tanımla** silmek için Excel'de iletişim kutusu <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimleri.  
  
 Tasarım zamanında bir belge için bir konak denetimi eklerseniz, kod içinde denetimi kullanmaya çalıştığınızda bir özel durum nedeniyle, bu program aracılığıyla çalışma zamanında kaldırmamalısınız. `Delete` Konak kontrolü yöntemi yalnızca çalışma zamanında bir belgeye eklediğiniz konak denetimleri kaldırır. Eğer `Delete` yöntemi bir konak denetiminin tasarım zamanında oluşturulan bir özel durumu oluşturulur.  
  
 Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> yöntemi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> yalnızca başarıyla siler <xref:Microsoft.Office.Tools.Excel.NamedRange> program aracılığıyla çalışma, dinamik ana bilgisayar denetimleri oluşturma olarak bilinir eklendiyse. Dinamik olarak oluşturulmuş konak denetimleri de kaldırılabilir denetimin adı geçirerek `Remove` yöntemi <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> veya <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliği. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Çözüm, son kullanıcıların, belgeye çalışma zamanında konak kontrolü silerseniz, beklenmedik bir şekilde başarısız olabilir. Belge koruma özelliklerini Word ve Excel konak denetimleri silinmesini korumak için kullanabilirsiniz. Daha fazla bilgi için [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Program aracılığıyla denetimleri sırasında kaldırmayın `Shutdown` belge veya çalışma olay işleyicisi. UI öğeleri artık kullanılabilir `Shutdown` olayı oluşur. Denetimleri uygulama kapatılmadan önce kaldırmak isterseniz, kodunuzu başka bir olay işleyicisi aşağıdaki gibi ekleyin `BeforeClose` veya `BeforeSave`.  
  
### <a name="program-against-host-control-events"></a>Konak denetimi olaylarına karşı programlama  
 Konak denetimleri Office nesnelerinin genişleten bir yöntem, olayları eklemektir. Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> Excel'de nesne ve <xref:Microsoft.Office.Interop.Word.Bookmark> Word nesne olayları gerekmez ancak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] programlanabilir olayları ekleyerek bu nesneleri genişletir. Erişebilir ve bu olaylara karşı aynı kodu Windows Forms'da denetimlerin olaylarını erişim yol: olay aşağı açılan listeden Visual Basic ve C# olay özellik sayfası aracılığıyla. Daha fazla bilgi için [izlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Ayarlı değil <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> özelliği <xref:Microsoft.Office.Interop.Excel.Application> Excel'e nesnesinde **false**. Bu özelliği ayarlamak **false** Excel konak denetimleri dahil, herhangi bir olayı göndermesini engelleme engeller.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)  
  