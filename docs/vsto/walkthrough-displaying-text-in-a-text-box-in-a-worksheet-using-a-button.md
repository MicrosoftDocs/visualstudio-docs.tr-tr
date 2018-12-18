---
title: 'İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25294e9cb8f57036603ec4817fcbd59976a358a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840291"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme
  Bu kılavuzda, Microsoft Office Excel çalışma sayfaları ve Excel projeleri Visual Studio'da Office geliştirme araçlarını kullanarak oluşturmak nasıl düğme ve metin kutusu kullanmanın temellerini gösterir. Sonuç tamamlanmış bir örnek görmek için Excel denetimleri örneğine bakın [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Bir çalışma sayfasına denetimler ekleme.  
  
-   Bir düğmeye tıklandığında bir metin kutusunda doldurun.  
  
-   Projenizi test edin.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Bu adımda, Visual Studio kullanarak bir Excel çalışma kitabı projesi oluşturur.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **Excel Düğmem**. Emin olun **yeni belge oluşturma** seçilir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **Excel Düğmem** için proje **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme  
 Bu kılavuz için bir düğme ve metin kutusu ilk çalışma gerekir.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Bir düğme ve metin kutusu ekleme  
  
1. Doğrulayın **My Excel Button.xlsx** Visual Studio tasarımcıda açık çalışma kitabı ile `Sheet1` görüntülenir.  
  
2. Gelen **ortak denetimleri** Sürükle araç kutusu sekmesi bir <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> için `Sheet1`.  
  
3. Gelen **görünümü** menüsünde **Özellikler penceresi**.  
  
4. Olduğundan emin olun **TextBox1** nda görülebilir **özellikleri** pencere açılan kutusu ve değişiklik **adı** özelliği için metin kutusunun **görüntü metni**.  
  
5. Sürükleme bir **düğmesi** denetimi `Sheet1` ve aşağıdaki özellikleri değiştirin:  
  
   |Özellik|Değer|  
   |--------------|-----------|  
   |**Ad**|**E:System.Windows.Forms.Control.Click**|  
   |**Metin**|**Metin Ekle**|  
  
   Artık düğmesine tıklandığında çalıştırmak için kod yazın.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Düğme tıklandığında, metin kutusunu doldurmak  
 Kullanıcının düğmesini her tıklayışında **Merhaba Dünya!** metin kutusuna eklenir.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Düğme tıklandığında metin kutusuna yazmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **Sayfa1**ve ardından **kodu görüntüle** kısayol menüsünde.  
  
2.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> düğmesi olay işleyicisi:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  İçinde C#, bir olay işleyicisi eklemelisiniz <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> aşağıda gösterildiği gibi olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık, çalışma kitabınızı emin olmak için test iletisi **Merhaba Dünya!** Düğmeye tıkladığınızda, metin kutusunda görüntülenir.  
  
### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Düğmesine tıklayın.  
  
3.  Onaylayın **Merhaba Dünya!** metin kutusunda görüntülenir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, düğme ve metin kutusu, Excel çalışma sayfalarında kullanmanın temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Projeyi dağıtma. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
-   Biçimlendirme değiştirmek için onay kutularını kullanarak. Daha fazla bilgi için [izlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  