---
title: Office belgelerindeki Windows Forms denetimleri sınırlamaları
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 104b8b3449b2ffb689caf66d5c180817b633f83e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572965"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office belgelerindeki Windows Forms denetimleri sınırlamaları

Microsoft Office Word belgelerine veya Microsoft Office Excel çalışma sayfalarına eklenen Windows Forms denetimleri ve Windows Forms için eklenen Windows Forms denetimleri arasındaki bazı farklar vardır. Örneğin, eklediğinizde, bir <xref:Microsoft.Office.Tools.Word.Controls.Button> belgeye özellikler gibi kontrol <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, ve <xref:System.Windows.Forms.Control.TabIndex> beklediğiniz gibi davranır değil.

Bu farklılıklar çoğunu şekilde, Windows Forms denetimleri barındırılan belgelerde neden olur. Windows Forms denetimini bir belgeye eklendiğinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgesinde Windows Forms denetimi barındıran bir ActiveX denetimi katıştırır. Windows Forms denetimi doğrudan belgede katıştırılmış değil.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Yöntemleri ve özellikleri Windows Forms denetimleri sınırlamaları

Bir dizi yöntem ve aynı şekilde bir Windows formunda yaptıkları ve bu nedenle, onların kullanılmaması önerilir gibi bir belge üzerinde çalışmıyor Windows Forms denetimlerindeki özellikler vardır. Örneğin, gibi özellikleri ayarlamak <xref:System.Windows.Forms.Control.Dock> ve <xref:System.Windows.Forms.Control.Anchor> yalnızca belge yerine kapsayıcı ActiveX denetimi göre denetimin konumunu etkiler. Desteklenmeyen yöntemleri ve özellikleri Windows Forms denetimlerindeki Word ve Excel için listesi aşağıdadır:

- Excel denetimlerin desteklenmeyen özellikleri:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Desteklenmeyen yöntemleri ve özellikleri Word denetimlerinin:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

Ayrıca ayarlanamıyor <xref:System.Windows.Forms.Control.Left> veya <xref:System.Windows.Forms.Control.Top> bir Word belgesi üzerindeki metin uygun olarak Windows Forms denetimleri özelliği. Windows Forms denetimleri, aşağıdaki durumlarda metin uygun olarak eklenir:

- Program aracılığıyla Word belgesine bir denetim ekleyin ve konumu için bir aralığı belirten bir yöntem kullanın.

- Tasarım zamanında bir Word belgesi için bir Windows Forms denetimi ekleyin. Bu Denetim Tasarımcısı'nda değiştirerek değiştirebilirsiniz.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office belgelerindeki Windows Forms denetimleri farklılıkları

Windows Forms denetimleri genellikle aynı davranışı bir Office belgesi üzerinde bir Windows formunda yapın, ancak bazı farklar sahiptir. Aşağıdaki tabloda, Office belgelerindeki Windows Forms denetimleri için mevcut farklar açıklanmaktadır.

|İşlevi|Fark|
|-------------------|----------------|
|Sekme düzenini denetleme|Bir Excel çalışma sayfası veya Word belgesi yerleştirilen denetimler aracılığıyla sekmesinde olamaz.|
|Denetim gruplandırma|Kullanarak bir <xref:System.Windows.Forms.GroupBox> birbirini dışlayan bir Office belgesine denetim. Doğrudan belgeye birden çok radyo düğmeleri eklediğinizde, radyo düğmeleri birbirini dışlamaz. Radyo düğmeleri birbirini dışlayan yapmak üzere kod yazabilirsiniz; Ancak, tercih edilen yaklaşım bir kullanıcı denetimi radyo düğmeleri ekleyin ve sonra kullanıcı denetimi belgeye eklemektir. Daha fazla bilgi için bkz: Word denetimleri örneği veya Excel denetimleri örneği ' [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).|
|Denetim türü|Belgelerde kullanılan Windows Forms denetimleri tarafından sağlanan bir sınıftaki sarılır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] denetimleri Excel çalışma sayfası veya Word belgesi için ek işlevler belirli vermektedir. Örneğin, bir **düğmesini** denetiminde bir Excel çalışma sayfası üzerinde türü olarak belirttiğinizden emin olun <xref:Microsoft.Office.Tools.Excel.Controls.Button> yerine <xref:System.Windows.Forms.Button> başvuran veya nesne atama.|
|Denetim konumu ve boyutu|Denetimin konumunu ve boyutunu ActiveX denetimi kapsayıcısı parçası olan özellikler tarafından belirlenir. ActiveX denetimi özellikleri, bir Windows Forms denetimi eşdeğer özelliklerini daha farklı değerler alır. Ayarladığınızda `Top`, `Left`, `Height`, veya `Width` bir denetimi özellikleri, onu ölçülür içinde piksel yerine işaret eder.|
|Word belgeleri konumu denetleme|Bir akış tabanlı düzene denetimleri eklerseniz, denetimler içeriğin bulunduğu içerik değiştikçe akar aklınızda bulundurun. Buradan sürüklediğinizde paragrafı denetimine bağlayamazsınız **araç** çünkü denetim Word belgesine metinle eklenir. Denetimi çift gibi denetim eklemek için başka bir yöntem kullanırsanız denetim resim eklemek için ayarladığınız Word seçeneğine göre eklenir.<br /><br /> Ayarlayamazsınız `Left` veya `Top` metinle bir denetim özelliği.<br /><br /> Üstbilgi ve altbilgisindeki ya da bir alt içinde denetimleri yerleştirilemiyor.|
|Denetim olayları|Denetim seçildiğinde, aşağıdaki sırada olaylar oluşur:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Denetimin seçili olmadığında, aşağıdaki sırada olaylar oluşur:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Denetim ölçeklendirme|% 100 dışında her şey için bir belgenin yakınlaştırma ayarını değiştirdiğinizde, bunlar görünmesine karşın denetimler, devre dışı belgeyle ölçeklendirin. Örneğin, belgenizi %130 yakınlaştırma olduğunda bir düğmeyi tıklatın varsa, onu bir ileti gösterir yakınlaştırma % 100'e ayarlanana kadar denetim devredışı. % 100 yakınlaştırma değiştirdiğinizde denetimleri düzgün çalışmaz.|
|Özellik değerlerini denetleme|Bir Windows formunda denetimlerin özelliklerini tamsayı değerine ayarlansa bile, tek bir Word belgesi denetimler için ayarlanır. Excel'de denetimlerin özellik değerleri için bir çift ayarlanır. Varsa `Height` ve `Width` özelliği bir denetimin çalışma sayfası üzerinde çalışma sayfası ya da ekran boyutunu aşıyor, değer kesilir.|
|Denetim yeniden boyutlandırma|Sekiz boyutlandırma birini kullanarak belge üzerinde denetimi yeniden boyutlandırma, yeni denetim boyutları yansıtılmaz **özellikleri** denetimi yansıtımaz kadar penceresi.|
|Denetim davranışı|Çalışma Sayfası penceresi ayrıldığında bir Excel çalışma sayfasındaki denetimleri beklenmedik şekilde davranabilir. Örneğin, erişim bir <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> çalışma sayfası üzerinde sadece windows birinde kullanılabilir olabilir.|
|Denetim adlandırma|Ayrılmış sözcükler adı denetimleri için kullanamazsınız. Örneğin eklerseniz, bir <xref:Microsoft.Office.Tools.Excel.Controls.Button> bir çalışma sayfasına ve adla değiştirin **sistem**, projeyi derlerken hataları oluşur.|
|Program aracılığıyla denetimleri ekleme|Denetimin Oluşturucusu belgenizi çalışma zamanında denetim eklemek için kullanmayın. Bunun yerine, tarafından sağlanan yardımcı yöntemler kullanın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Örneğin, <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> çalışma sayfasına bir düğme ekleme yöntemi. Bu yardımcı yöntemler tarafından desteklenmeyen bir denetim eklemek istiyorsanız, kullanabileceğiniz `AddControl` yöntemi. Daha fazla bilgi için bkz: [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Denetimleri kopyalama|Bir Windows Forms denetimi kopyalayın ve çalışma zamanında bir belgeye yapıştırın, boş bir kapsayıcı ActiveX denetimi belgeye yapıştırılan. Windows Forms denetimi yeni konumda görünmez ve özgün denetim arka plan kod ActiveX denetimi kapsayıcısı için kopyalanmaz.|

## <a name="limitations-in-document-level-projects"></a>Belge düzeyi projelerine sınırlamaları

Belge düzeyi projelerine belgelerindeki Windows Forms denetimleri kullanarak bazı sınırlamaları benzersizdir.

### <a name="control-support-at-design-time"></a>Tasarım zamanında denetim desteği

Bazı Windows Forms denetimleri çıkarılır **araç** bir Excel çalışma sayfası veya Word belgesi olduğunda Visual Studio tasarımcısında açın. Bu teknik sınırlamaları nedeniyle olur veya işlevi zaten Word veya Excel içinde kullanılabilir. Excel ve Word projelerini tüm Windows Forms denetimleri ve görünen diğer bileşenleri desteklemek **araç** zaman belge odağa sahip ve üçüncü taraf denetimlerini bir çalışma sayfası veya belge ekleyebilirsiniz.

> [!NOTE]
> Tüm denetimler çıkarılır **araç** zaman bir belge korunur. Belge koruması hakkında daha fazla bilgi için bkz: [koruma belge düzeyi çözümlerde belge](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Üçüncü taraf denetimleri olmalıdır <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini **true** Office çözümünde kullanılması için.

Aşağıdaki denetimleri ve bileşenleri kullanılamaz **araç**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Eski ActiveX denetimleri için destek

Varolan bir Word belgesine veya ActiveX denetimlerini içeren Excel çalışma kitabı kullanan bir belge düzeyi Office projesi oluşturursanız, ActiveX denetimlerini işlevselliğini kayıp değildir; Ancak, Visual Studio içinde belgelerinize yeni ActiveX denetimleri ekleme desteği yoktur. Örneğin, bir düğmesinden Word belgeniz varsa, **denetim** Visual Basic for Applications (VBA) makrosu araç, bu belgeyi Office projesinde kullanıldıktan sonra makrosu çalışmaya devam edecek. Ancak, ActiveX denetimlerini ve VBA makroları kaldırın ve Windows Forms denetimleri ile değiştirin ve yönetilen kodla önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Windows Forms denetimlerindeki Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)