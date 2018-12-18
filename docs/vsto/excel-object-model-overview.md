---
title: Excel nesne modeline genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ca93cae45eed272b683275896efcf83229ca9a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880799"
---
# <a name="excel-object-model-overview"></a>Excel nesne modeline genel bakış
  Microsoft Office Excel kullanan çözümleri geliştirmek için Excel nesne modeli tarafından sağlanan nesneler ile etkileşim kurabilirsiniz. Bu konuda en önemli nesneleri sunar:  
  
- <xref:Microsoft.Office.Interop.Excel.Application>  
  
- <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
- <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Interop.Excel.Range>  
  
  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
  Nesne modeli, kullanıcı arabirimi yakından takip eder. <xref:Microsoft.Office.Interop.Excel.Application> Nesnesini temsil eden tüm uygulama ve her <xref:Microsoft.Office.Interop.Excel.Workbook> nesneyi içeren koleksiyonu `Worksheet` nesneleri. Burada, hücreleri temsil eden ana soyutlamadır <xref:Microsoft.Office.Interop.Excel.Range> tek tek veya grup hücre ile çalışmanıza olanak sağlayan nesne.  
  
  Excel nesne modeline ek olarak, Visual Studio'da Office projeleri sağlamak *konak öğelerini* ve *konak denetimlerini* Excel nesne modelinde bazı nesneler genişletin. Konak denetimlerinin ve konak öğelerinin bunlar genişletmek Excel nesneleri gibi davranırlar fakat aynı zamanda veri bağlama becerileri ve ek olaylar gibi ek işlevlere sahiptirler. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md) ve [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
  Bu konu Excel nesne modeline kısa bir genel bakış sağlar. Kaynaklar nerede edinebilirsiniz tüm Excel nesne modeli hakkında daha fazla bilgi için bkz [Excel nesne modeli belgeleri kullanın](#ExcelOMDocumentation).  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [bunu nasıl yaparım: kullanım olay işleyicileri içinde bir Excel 2007 Eklentisi?](http://go.microsoft.com/fwlink/?LinkID=130291), ve [bunu nasıl yaparım kullanım şekilleri kabarcık grafiği oluşturmak için Excel'de? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="access-objects-in-an-excel-project"></a>Bir Excel projesinde nesnelere erişme  
 Excel için yeni bir VSTO eklenti projesi oluşturduğunuzda, Visual Studio otomatik olarak oluşturur bir *ThisAddIn.vb* veya *ThisAddIn.cs* kod dosyası. Uygulama nesnesi kullanarak erişebileceğiniz `Me.Application` veya `this.Application`.  
  
 Excel için yeni bir belge düzeyi projesi oluşturduğunuzda, yeni bir Excel çalışma kitabı veya Excel Şablonu proje oluşturma seçeneğiniz vardır. Visual Studio aşağıdaki kod dosyalarını projenizde yeni Excel çalışma kitabı hem şablon projeleri için otomatik olarak oluşturur.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Kullanabileceğiniz `Globals` erişmek için projenizdeki sınıfı `ThisWorkbook`, `Sheet1`, `Sheet2`, veya `Sheet3` gelen ilgili sınıf dışında. Daha fazla bilgi için [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md). Aşağıdaki örnek çağrıları <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> yöntemi `Sheet1` kod birinde olup yerleştirilir bakılmaksızın `Sheet` *n* sınıfları veya `ThisWorkbook` sınıfı.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Verileri bir Excel belgesi ileri düzeyde yapılandırılmış olduğundan, hiyerarşik ve Basit Nesne modeli. Excel ile etkileşim kurmak isteyebilirsiniz nesneyi sağlar, ancak nesne modelinde iyi bir başlangıç kullanılabilir nesneler küçük bir kısmı odaklanarak alabilirsiniz. Bu nesneler aşağıdaki dört içerir:  
  
- Uygulama  
  
- Çalışma Kitabı  
  
- Çalışma Sayfası  
  
- Aralık  
  
  Excel ile çalışmanın çoğunu, bu dört nesneleri ve üyeleri ortalar.  
  
### <a name="application-object"></a>Uygulama nesnesi  
 Excel <xref:Microsoft.Office.Interop.Excel.Application> nesne Excel uygulamasını temsil eder. <xref:Microsoft.Office.Interop.Excel.Application> Nesnesi, çalışan bir uygulama, bu örneğe uygulanan seçenekleri hakkında bilgi büyük ölçüde kullanıma sunar ve geçerli kullanıcı nesnelerini örneğinde açın.  
  
> [!NOTE]  
>  Ayarlı değil <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> özelliği <xref:Microsoft.Office.Interop.Excel.Application> Excel'e nesnesinde **false**. Bu özellik false olarak ayarlamayı Excel konak denetimleri dahil, herhangi bir olayı göndermesini engelleme engeller.  
  
### <a name="workbook-object"></a>Çalışma kitabı nesnesi  
 <xref:Microsoft.Office.Interop.Excel.Workbook> Nesne tek bir çalışma kitabını Excel uygulamasında temsil eder.  
  
 Visual Studio'da Office geliştirme araçlarını genişletmek <xref:Microsoft.Office.Interop.Excel.Workbook> sağlayarak nesne <xref:Microsoft.Office.Tools.Excel.Workbook> türü. Bu tür tüm özelliklerine erişmenizi sağlar. bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesne. Daha fazla bilgi için [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Çalışma sayfası nesnesi  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> Nesne üyesi olduğu <xref:Microsoft.Office.Interop.Excel.Worksheets> koleksiyonu. Pek çok özelliklerini, yöntemlerini ve olaylarını <xref:Microsoft.Office.Interop.Excel.Worksheet> aynı veya benzer üyeleri tarafından sağlanan <xref:Microsoft.Office.Interop.Excel.Application> veya <xref:Microsoft.Office.Interop.Excel.Workbook> nesneleri.  
  
 Excel sağlayan bir <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyon özelliği olarak bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesne. Her üye <xref:Microsoft.Office.Interop.Excel.Sheets> koleksiyondur ya da bir <xref:Microsoft.Office.Interop.Excel.Worksheet> veya <xref:Microsoft.Office.Interop.Excel.Chart> nesne.  
  
 Visual Studio'da Office geliştirme araçlarını genişletmek <xref:Microsoft.Office.Interop.Excel.Worksheet> sağlayarak nesne <xref:Microsoft.Office.Tools.Excel.Worksheet> türü. Bu tür tüm özelliklerine erişmenizi sağlar. bir <xref:Microsoft.Office.Interop.Excel.Worksheet> nesne yanı sıra yeni özellikler gibi yeni olayları işlemek ve yönetilen denetimleri barındırma olanağı. Daha fazla bilgi için [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Aralık nesnesi  
 <xref:Microsoft.Office.Interop.Excel.Range> Nesnesi, çoğu Excel uygulamalarınız içinde kullanacağınız nesnedir. Excel içinde herhangi bir bölgeyi yönetebilirsiniz önce olarak express gerekir bir <xref:Microsoft.Office.Interop.Excel.Range> nesne ve yöntem ve bu aralığın özelliklerle çalışma. A <xref:Microsoft.Office.Interop.Excel.Range> nesnesi bir hücre, satır, sütun, bir veya daha fazla blok veya değil bitişik ve hatta hücre birden çok sayfada bir grup, hücre içeren bir hücre seçimini temsil eder.  
  
 Visual Studio genişletir <xref:Microsoft.Office.Interop.Excel.Range> sağlayarak nesne <xref:Microsoft.Office.Tools.Excel.NamedRange> ve <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> türleri. Bu tür çoğu aynı özelliklere sahip bir <xref:Microsoft.Office.Interop.Excel.Range> nesne yanı sıra yeni olaylar ve veri bağlama yeteneği gibi yeni özellikler. Daha fazla bilgi için [NamedRange denetimi](../vsto/namedrange-control.md) ve [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Excel nesne modeli belgeleri kullanın  
 Excel nesne modeli hakkında tam bilgi için Excel birincil birlikte çalışma derlemesi (PIA) başvuru ve VBA nesne modeli başvurusu başvurabilir.  
  
### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma bütünleştirilmiş kod başvurusu  
 Excel PIA başvuru belgeleri Excel için birincil birlikte çalışma derlemesi türlerini tanımlar. Bu belge aşağıdaki konumdan kullanılabilir: [Excel 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 PIA hem de PIA olayların nasıl uygulandığını, sınıfları ve arabirimleri arasındaki farkı gibi Excel PIA tasarımı hakkında daha fazla bilgi için bkz: [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindekigenelbakış](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu  
 Visual Basic for Applications (VBA) kodundaki sunulur şekilde VBA nesne modeli başvurusu Excel nesne modeline listelenmiştir. Daha fazla bilgi için [Excel 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türleri ve üyeleri Excel PIA karşılık gelir. Örneğin, VBA nesne modeli başvurusu çalışma sayfası nesnesi için karşılık gelen <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel PIA nesne. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da bu başvuruyu Visual Basic veya Visual C# VBA kodu Çevir ve bunları Visual Studio kullanarak oluşturduğunuz bir Excel projesinde kullanmak istiyorsanız gerekir.  
  
### <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Excel çözümleri](../vsto/excel-solutions.md)|Microsoft Office Excel için nasıl belge düzeyi özelleştirmeleri ve VSTO eklentileri oluşturabileceğiniz açıklanır.|  
|[Aralıklarla çalışma](../vsto/working-with-ranges.md)|Aralıkları ile genel görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|  
|[Çalışma sayfaları ile çalışma](../vsto/working-with-worksheets.md)|Çalışma sayfaları ile genel görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|  
|[Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)|Çalışma kitapları ile genel görevlerin nasıl gerçekleştirileceğini gösteren örnekler sağlar.|  
  
  