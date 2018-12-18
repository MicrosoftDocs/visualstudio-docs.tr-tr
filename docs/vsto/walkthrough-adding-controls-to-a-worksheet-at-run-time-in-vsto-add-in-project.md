---
title: 'İzlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b3671b00ecad0380dd38e770beeef703fa916fac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915704"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-runtime-in-vsto-add-in-project"></a>İzlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme
  Bir Excel VSTO eklentisi kullanarak herhangi bir açık çalışma sayfasına denetimler ekleyebilirsiniz. Bu izlenecek yol ekleme olanağı Şerit kullanmayı gösterir. bir <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>ve bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma. Bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Excel için VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir kullanıcı arabirimi (UI) denetimler eklemek için çalışma sayfasına sağlama.  
  
- Çalışma sayfasına denetimler ekleme.  
  
- Çalışma sayfasındaki denetimleri kaldırılıyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="create-a-new-excel-vsto-add-in-project"></a>Yeni bir Excel VSTO eklentisi projesi oluşturun  
 Excel VSTO eklenti projesinde oluşturarak başlayın.  
  
### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Yeni bir Excel VSTO eklenti projesi oluşturmak için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], adlı bir Excel VSTO eklentisi projesi oluşturun **ExcelDynamicControls**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Bir başvuru ekleyin **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** derleme. Bu başvuru, bu kılavuzda daha sonra çalışma program aracılığıyla bir Windows Forms denetimi eklemek için gereklidir.  
  
## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Bir çalışma sayfasına denetimler eklemek için bir kullanıcı Arabirimi sağlar.  
 Şerite özel sekme ekleyin. Kullanıcılar onay kutularını çalışma sayfasına denetimler eklemek için sekmesinde seçebilir.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Bir çalışma sayfasına denetimler eklemek için bir UI sağlamak için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)** ve ardından **Ekle**.  
  
     Adlı bir dosya **Ribbon1.cs** veya **Ribbon1.vb** Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.  
  
3.  Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, bir onay kutusu denetimi sürükleyin **group1**.  
  
4.  Tıklayın **CheckBox1** seçin.  
  
5.  İçinde **özellikleri** penceresinde, aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**Düğme**|  
    |**Etiket**|**Düğme**|  
  
6.  İkinci bir onay kutusu ekleme **group1**ve ardından aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**NamedRange**|  
    |**Etiket**|**NamedRange**|  
  
7.  Üçüncü bir onay kutusu ekleme **group1**ve ardından aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**ListObject**|  
    |**Etiket**|**ListObject**|  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Yönetilen denetimleri kapsayıcıları olarak davranan konak öğeleri yalnızca eklenebilir. VSTO eklentisi projeleri ile herhangi bir açık çalışma çalıştığından, VSTO eklentisi çalışma sayfası konak öğesi dönüştürür ve denetim eklemeden önce var olan bir konak öğesi alır. Olay işleyicisine oluşturmak için her denetim için kod ekleme bir <xref:Microsoft.Office.Tools.Excel.Worksheet> açık çalışma sayfasını temel alan ana bilgisayar öğesi. Ardından ekleyin bir <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>ve <xref:Microsoft.Office.Tools.Excel.ListObject> geçerli seçime konumunda.  
  
### <a name="to-add-controls-to-a-worksheet"></a>Bir çalışma sayfasına denetimler ekleme  
  
1.  Şerit Tasarımcısı'nda çift **düğmesi**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Olay işleyicisine **düğmesi** onay kutusu, Kod Düzenleyicisi'nde açılır.  
  
2.  Değiştirin `Button_Click` aşağıdaki kod ile olay işleyicisi.  
  
     Bu kod `GetVstoObject` ilk çalışma kitabındaki temsil eder ve ardından ekleyen bir ana bilgisayar öğesi almak için yöntemi bir <xref:Microsoft.Office.Tools.Excel.Controls.Button> şu anda seçili hücreden denetimi.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  İçinde **Çözüm Gezgini**seçin *Ribbon1.cs* veya *Ribbon1.vb*.  
  
4.  Üzerinde **görünümü** menüsünde tıklatın **Tasarımcısı**.  
  
5.  Şerit Tasarımcısı'nda çift **NamedRange**.  
  
6.  Değiştirin `NamedRange_Click` aşağıdaki kod ile olay işleyicisi.  
  
     Bu kod `GetVstoObject` ilk çalışma kitabındaki temsil eder ve ardından tanımlayan bir ana bilgisayar öğesi almak için yöntemi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> şu anda seçili hücrenin veya hücre denetimi.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  Şerit Tasarımcısı'nda çift **ListObject**.  
  
8.  Değiştirin `ListObject_Click` aşağıdaki kod ile olay işleyicisi.  
  
     Bu kod `GetVstoObject` ilk çalışma kitabındaki temsil eder ve ardından tanımlayan bir ana bilgisayar öğesi almak için yöntemi bir <xref:Microsoft.Office.Tools.Excel.ListObject> şu anda seçili hücrenin veya hücre.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Şerit kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="remove-controls-from-the-worksheet"></a>Çalışma sayfasından denetimlerini kaldırma  
 Çalışma kaydedildi ve denetimler kalıcı olmaz. Program aracılığıyla oluşturulan tüm Windows Formları denetimleri çalışma kaydedilir veya çalışma kitabını tekrar açıldığında yalnızca anahat denetimin görünür önce kaldırmanız gerekir. Kodu <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> Windows Forms denetimleri oluşturulan konak öğesinin denetimleri koleksiyondan kaldırır. olay. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
### <a name="to-remove-controls-from-the-worksheet"></a>Çalışma sayfasındaki denetimleri kaldırmak için  
  
1.  İçinde **Çözüm Gezgini**seçin *ThisAddIn.cs* veya *ThisAddIn.vb*.  
  
2.  Üzerinde **görünümü** menüsünde tıklatın **kod**.  
  
3.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Bu kod ilk çalışma kitabında alır ve ardından `HasVstoObject` çalışma oluşturulan çalışma sayfası nesnesi sahip olup olmadığını denetlemek için yöntem. Oluşturulan çalışma sayfası nesnesi denetimleri varsa, kod söz konusu çalışma sayfası nesnesi alır ve denetimleri kaldırma denetim koleksiyonu yinelenir.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  İçinde C#, bir olay işleyicisi için oluşturmalısınız <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> olay. Bu kodu koyabilirsiniz `ThisAddIn_Startup` yöntemi. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md). Değiştirin `ThisAddIn_Startup` yöntemini aşağıdaki kod ile.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="test-the-solution"></a>Çözüm test  
 Denetimler, Şeritteki özel bir sekme seçerek çalışma sayfasına ekleyin. Çalışma sayfası kaydettiğinizde, bu denetimlerin kaldırılır.  
  
### <a name="to-test-the-solution"></a>Çözümü test etmek için.  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Sheet1'deki herhangi bir hücreyi seçin.  
  
3.  Tıklayın **eklentileri** sekmesi.  
  
4.  İçinde **group1** grubunda **düğmesi**.  
  
     Bir düğme seçili hücrede görünür.  
  
5.  Sheet1 içinde farklı bir hücreyi seçin.  
  
6.  İçinde **group1** grubunda **NamedRange**.  
  
     Adlandırılmış aralık seçili hücre için tanımlanır.  
  
7.  Hücre bir dizi içinde Sayfa1 seçin.  
  
8.  İçinde **group1** grubunda **ListObject**.  
  
     Bir liste nesnesi için seçili hücreleri eklenir.  
  
9. Çalışma sayfasını kaydedin.  
  
     Sheet1 artık eklenen denetimleri görünür.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konu Excel VSTO eklentisi projeleri denetimleri hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Bir çalışma sayfasına denetimler kaydetme hakkında bilgi edinmek için Excel VSTO eklenti dinamik bkz [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Excel çözümleri](../vsto/excel-solutions.md)   
 [Windows forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [ListObject denetimi](../vsto/listobject-control.md)  
  
  