---
title: Excel çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 917a83a434dc27074b0d786f64fcdbdc5fd294d3
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027399"
---
# <a name="excel-solutions"></a>Excel çözümleri
  Visual Studio, Microsoft Office Excel için belge düzeyi özelleştirmeleri ve VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Excel otomatikleştirin, Excel özelliklerini genişletmek ve Excel kullanıcı arabirimini (UI) özelleştirmek için bu çözümleri kullanabilirsiniz. Belge düzeyi özelleştirmeleri ve VSTO eklentileri arasındaki farklar hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  

> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:  

-   [Excel otomatikleştirmek](#automating).  

-   [Excel için belge düzeyi özelleştirmeleri geliştirme](#doclevel).  

-   [Excel için VSTO eklentileri geliştirme](#applevel).  

-   [Excel kullanıcı arabirimini özelleştirme](#UI).  

##  <a name="automating"></a> Excel otomatikleştirin  
 Excel nesne modeli, Excel otomatikleştirmek için kullanabileceğiniz birçok türü ortaya çıkarır. Örneğin, programlı olarak grafikler oluşturun, çalışma biçimlendirin ve aralıkları ve hücrelerin değerlerini ayarlayın. Daha fazla bilgi için [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  

 Visual Studio'daki Excel çözümleri geliştirirken aynı zamanda kullanabilirsiniz *konak öğelerini* ve *konak denetimlerini* Çözümlerinizdeki. Bunlar gibi Excel nesne modeli, yaygın olarak kullanılan belirli nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Excel.Worksheet> ve <xref:Microsoft.Office.Interop.Excel.Range> nesneleri. Genişletilmiş nesneler temel Excel nesneleri gibi davranırlar fakat nesnelere veri bağlama becerileri ve ek olaylar ekleyin. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md).  

##  <a name="doclevel"></a> Excel için belge düzeyi özelleştirmeleri geliştirme  
 Microsoft Office Excel için belge düzeyinde bir özelleştirme belirli bir çalışma kitabı ile ilişkili bir derleme içerir. Derleme, genellikle UI'yi özelleştirerek ve Excel otomatikleştirerek çalışma kitabı genişletir. İlişkili çalışma kitabını Excel'de açık olduğunda bir VSTO Excel ile ilişkili olan eklentiyi bir özelleştirmede uyguladığınız işlevsellik kullanılabilir.  

 Excel için belge düzeyi özelleştirme projesi oluşturmak için Excel çalışma kitabı veya Excel Şablonu proje şablonlarını kullanma **yeni proje** Visual Studio'nun iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 Belge düzeyi özelleştirmelerinin hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md).  

### <a name="excel-customization-programming-model"></a>Excel özelleştirme programlama modeli  
 Excel için belge düzeyi projesi oluşturduğunuzda, Visual Studio çözümünüzün temeli olan çeşitli sınıflar oluşturur: `ThisWorkbook`, `Sheet1`, `Sheet2`, ve `Sheet3`. Bu sınıflar, çözümünüz ile ilişkili çalışma sayfaları ve çalışma kitabı temsil ve kodunuzu yazmanız için bir başlangıç noktası sağlar.  

 Bunlar hakkında daha fazla bilgi için oluşturulan sınıflar ve kullanabileceğiniz diğer özellikler bir belge düzeyi projede bkz [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  

##  <a name="applevel"></a> Excel için VSTO eklentileri geliştirin  
 VSTO eklentisi için Microsoft Office Excel Excel tarafından yüklenen bir derleme içerir. Derleme, genellikle UI'yi özelleştirerek ve Excel otomatikleştirerek Excel genişletir. Belirli bir çalışma kitabı ile ilişkilendirilen belge düzeyi özelleştirmesinin aksine bir VSTO eklentide uyguladığınız işlevsellik, herhangi tek bir çalışma kitabına sınırlı değildir.  

 Excel için VSTO eklentisi projesi oluşturmak için Excel çalışma kitabı veya Excel Şablonu proje şablonlarını kullanma **yeni proje** Visual Studio'nun iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 VSTO eklentileri nasıl çalıştığı hakkında genel bilgi için bkz. [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Excel eklenti programlama modeli  
 Bir Excel VSTO eklenti projesi oluşturduğunuzda, Visual Studio isimli bir sınıf oluşturur. `ThisAddIn`, çözümünüzün temeli. Bu sınıf kodunuzu yazmanız için bir başlangıç noktası sağlar ve ayrıca bir Excel için VSTO eklenti nesne modeli sunar.  

 Hakkında daha fazla bilgi için `ThisAddIn` sınıfı ve bir VSTO eklenti, kullanabileceğiniz diğer Visual Studio özellikleri görmek [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  

##  <a name="UI"></a> Excel kullanıcı arabirimini özelleştirme  
 Excel kullanıcı arabirimini özelleştirmek için birçok farklı yol vardır. Bazı seçenekleri tüm proje türleri için kullanılabilir ve diğer seçenekleri yalnızca VSTO eklentileri veya belge düzeyi özelleştirmeleri için kullanılabilir.  

### <a name="options-for-all-project-types"></a>Tüm proje türleri için Seçenekler  
 Aşağıdaki tabloda, hem belge düzeyi özelleştirmeleri ve VSTO eklentileri için kullanılabilen seçenekleri listeler.  

|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Şeridi özelleştirme.|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
|Windows Forms veya genişletilmiş Excel denetimleri herhangi bir açık çalışma için VSTO eklentisi veya belge düzeyi özelleştirmesi için özelleştirilmiş çalışma kitabında çalışma sayfası ekleyin.|[Nasıl yapılır: Office belgelerine Windows forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  

### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri seçenekleri  
 Aşağıdaki tabloda, yalnızca belge düzeyi özelleştirmeleri tarafından kullanılabilen seçenekleri listeler.  

|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Çalışma kitabına Eylemler bölmesi ekleme.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Bir çalışma sayfasına XML düğümüyle eşlendiğine genişletilmiş aralık denetimleri ekleyin.|[Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  

### <a name="options-for-vsto-add-ins"></a>VSTO eklentileri için seçenekleri  
 Aşağıdaki tabloda yalnızca VSTO eklentileri için kullanılabilen seçenekleri listeler.  

|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Özel görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|  

### <a name="related-topics"></a>İlgili konular  

| Başlık | Açıklama |
| - | - |
| [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md) | Excel nesne modeli tarafından sağlanan ana türlerine genel bir bakış sağlar. |
| [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md) | Genişletilmiş nesneler hakkında bilgi sağlar (tarafından sağlanan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), Excel çözümleri kullanabilirsiniz. |
| [Genelleştirme ve yerelleştirme Excel çözümleri](../vsto/globalization-and-localization-of-excel-solutions.md) | Windows ayarları İngilizce dışındaki bilgisayarlarda çalıştırılan Excel çözümleri ilgili özel konular hakkında bilgi içerir. |
| [Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md) | Excel çalışma sayfalarına Windows Forms denetimlerini nasıl ekleyebileceğinizi açıklar. |
| [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Excel için temel bir belge düzeyi özelleştirmeyi oluşturma işlemini gösterir. |
| [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Excel için temel bir VSTO eklentisi oluşturma işlemini gösterir. |
| [İzlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Bir Windows Forms düğme eklemek gösterilmiştir bir <xref:Microsoft.Office.Tools.Excel.NamedRange>ve bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma zamanında VSTO eklenti kullanarak. |
| [Birlikte yazmayı ve eklentileri anlama](./understanding-coauthoring-and-addins.md) | Birlikte yazmayı uyum sağlayacak şekilde çözümlerinizi yapmanız gerekebilir ayarlamalar açıklar. |
| [Excel 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199011) | Makaleler ve Excel çözümleri geliştirme hakkında başvuru belgelerine bağlantılar sağlar. Bu, Visual Studio kullanarak Office geliştirmeye özgü değildir. |

