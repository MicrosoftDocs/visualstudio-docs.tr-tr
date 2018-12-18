---
title: 'İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a9b7540a42dbaf7b7079793158d33d761199720
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949909"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma
  Bu tanıtıcı kılavuz Microsoft Office Excel için uygulama düzeyi eklentiyi oluşturma işlemini gösterir. Bu tür bir çözüm içinde oluşturduğunuz özellikler uygulamanın kendisinin çalışma kitaplarını açık olan bağımsız olarak kullanılabilir.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Excel VSTO eklenti projesinde Excel için oluşturuluyor.  
  
- Kaydedildiğinde bir çalışma kitabına metin eklemek için Excel nesne modeli kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Tamamlanmış projeyi VSTO eklentisi artık otomatik olarak geliştirme bilgisayarınızda çalıştırılır, böylece temizleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Visual Studio'da yeni bir Excel VSTO eklenti projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde seçin **Excel 2010 Eklentisi** veya **Excel 2013 eklentisi**.  
  
6.  İçinde **adı** kutusuna **FirstExcelAddIn**.  
  
7.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstExcelAddIn** proje ve düzenleyicide ThisAddIn kod dosyasını açar.  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Kaydedilen çalışma kitabına metin eklemek için kod yazma  
 Ardından, ThisAddIn kod dosyası için kodu ekleyin. Yeni kod, etkin çalışma sayfasının ilk satırında ortak metin eklemek için Excel nesne modeli kullanır. Etkin çalışma sayfası kullanıcı çalışma kitabı kaydettiğinde, açık olan bir çalışma sayfası ' dir. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisAddIn kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisAddIn` sınıfı. Bu sınıf, kodunuz için bir giriş noktası sağlar ve Excel nesne modeline erişim sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Kalanı `ThisAddIn` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisAddIn_Startup` Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri Excel yüklediğinde ve VSTO eklenti bellekten çağrılır. Bu olay işleyicileri, VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, eklentiniz tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Kaydedilen çalışma kitabına metin satırı eklemek için  
  
1. ThisAddIn kod dosyasında, aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Yeni kod için bir olay işleyicisi tanımlar <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> bir çalışma kitabı kaydedildiğinde gerçekleşmek üzereyken olay.  
  
    Kullanıcı bir çalışma kitabı kaydettiğinde, olay işleyicisi etkin çalışma başlangıcında yeni metin ekler.  
  
    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2. C# kullanıyorsanız, aşağıdaki gerekli kodu eklemek `ThisAddIn_Startup` olay işleyicisi. Bu kod bağlanmak için kullanılan `Application_WorkbookBeforeSave` olay işleyicisi ile <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> olay.  
  
    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
   Çalışma kitabı kaydedildiğinde değiştirmek için aşağıdaki nesneler önceki kod örnekleri kullanın:  
  
-   `Application` Alanını `ThisAddIn` sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.Excel.Application> Excel'ün geçerli örneğini temsil eden nesne.  
  
-   `Wb` Parametresi için olay işleyicisinin <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> olay. `Wb` Parametresi bir <xref:Microsoft.Office.Interop.Excel.Workbook> kaydedilmiş bir çalışma kitabı temsil eden nesne. Daha fazla bilgi için [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
## <a name="test-the-project"></a>Test projesi  
  
### <a name="to-test-the-project"></a>Projeyi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, proje için yapı çıkış klasöründe bulunan bütünleştirilmiş kod derlenir. Visual Studio ayrıca bulmak ve VSTO eklentisi yükleme Excel sağlayan kayıt defteri girişleri kümesi oluşturur ve VSTO eklenti çalıştırmak, geliştirme bilgisayarının güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
2.  Excel'de çalışma kitabını kaydedin.  
  
3.  Aşağıdaki metni çalışma kitabına eklendiğinden emin olun.  
  
     **Bu metin, kod kullanarak eklendi.**  
  
4.  Excel'i kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye işiniz bittiğinde, VSTO eklentisi derleme, kayıt defteri girişleri ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırın. Aksi takdirde, VSTO eklentisi, Excel, geliştirme bilgisayarınızda her açtığınızda çalışmaya devam eder.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Tamamlanmış projeyi geliştirme bilgisayarınızda temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Excel için temel bir VSTO eklentisi oluşturdunuz, VSTO eklentileri aşağıdaki konulardan geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   VSTO eklentilerinde gerçekleştirebileceğiniz genel programlama görevlerini: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   Excel VSTO eklentileri belirli programlama görevleri: [Excel çözümleri](../vsto/excel-solutions.md).  
  
-   Excel nesne modelini kullanarak: [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
-   Excel kullanıcı arabirimini (UI) özelleştirme, örneğin, göre Şerite özel sekme ekleme veya kendi özel görev bölmesi oluşturuluyor: [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Derleme ve Excel için VSTO eklentileri hata ayıklama: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   Excel için VSTO eklentileri dağıtma: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel çözümleri](../vsto/excel-solutions.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  