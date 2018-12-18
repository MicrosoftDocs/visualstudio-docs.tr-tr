---
title: 'İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fae4a6cc21264e62c5a12db79c8a937f0a366314
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843541"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme
  Bu izlenecek yol, onay kutularını biçimini değiştirmek için bir Microsoft Office Excel çalışma sayfasında kullanmanın temellerini gösterir. Oluşturma ve kod projenize eklemek için Visual Studio'da Office geliştirme araçlarını kullanın. Sonuç tamamlanmış bir örnek görmek için Excel denetimleri örneğine bakın [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Metin ve denetimlerin çalışma sayfasına ekleyin.  
  
-   Bir seçenek belirlendiğinde, metni biçimlendirin.  
  
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
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **My Excel biçimlendirme**. Emin olun **yeni belge oluşturma** seçilir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **My Excel biçimlendirme** için proje **Çözüm Gezgini**.  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>Çalışma sayfasına metin ve denetimler ekleme  
 Bu kılavuz için üç gerekir <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetimleri ve bazı metin bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi.  
  
### <a name="to-add-three-check-boxes"></a>Üç onay kutusunu eklemek için  
  
1.  Çalışma kitabı Visual Studio tasarımcısı ve açık olduğundan emin olun `Sheet1` açıktır.  
  
2.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> denetim ya da hücre yanına **B2** içinde **Sayfa1**.  
  
3.  Gelen **görünümü** menüsünde **özellikleri** penceresi.  
  
4.  Olduğundan emin olun **Checkbox1** nesne adı liste kutusunda görülebilir **özellikleri** penceresinde ve aşağıdaki özellikleri değiştirin:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**applyBoldFont**|  
    |**Metin**|**Kalın**|  
  
5.  İkinci bir onay kutusu üzerinde veya yakınında hücre sürükleyin **B4** ve aşağıdaki özellikleri değiştirin:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**ApplyItalicFont**|  
    |**Metin**|**İtalik**|  
  
6.  Üçüncü onay kutusu üzerinde veya yakınında hücre sürükleyin **B6** ve aşağıdaki özellikleri değiştirin:  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**applyUnderlineFont**|  
    |**Metin**|**Alt çizgi**|  
  
7.  Tutarken, tüm üç onay kutusu denetimini seçmek **Ctrl** anahtarı.  
  
8.  Excel'de biçimi sekmenin Yerleştir grubunda tıklatın **Hizala**ve ardından **Sola Hizala**.  
  
     Üç onay kutusu denetimi, sol tarafında, seçtiğiniz ilk denetim konumunda hizalanır.  
  
     Ardından, sürükleyin bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma denetimi.  
  
    > [!NOTE]  
    >  Ayrıca ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> yazarak denetim **textFont** içine **adı** kutusu.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Metin NamedRange denetimine eklemek için  
  
1. Gelen **Excel denetimleri** Sürükle araç kutusu sekmesi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **B9**.  
  
2. Doğrulayın **$B$ 9** düzenlenebilir metin kutusu ve söz konusu hücrenin görünür **B9** seçilir. Yüklü değilse, hücreyi tıklatın **B9** seçin.  
  
3. **Tamam**'ı tıklatın.  
  
4. Hücre **B9** adında bir aralığa dönüşür `NamedRange1`.  
  
    Çalışma sayfasında görünür bir gösterge yoktur ancak `NamedRange1` görünür **adı kutusuna** (hemen üstüne çalışma sol tarafta), hücre **B9** seçilir.  
  
5. Olduğundan emin olun **NamedRange1** nesne adı liste kutusunda görülebilir **özellikleri** penceresinde ve aşağıdaki özellikleri değiştirin:  
  
   |Özellik|Değer|  
   |--------------|-----------|  
   |**Ad**|**textFont**|  
   |**Value2**|**Bu metin biçimini değiştirmek için bir onay kutusuna tıklayın.**|  
  
   Ardından, bir seçenek belirlendiğinde, metni biçimlendirmek için kod yazın.  
  
## <a name="format-the-text-when-an-option-is-selected"></a>Bir seçenek belirlendiğinde, metin biçimlendirme  
 Bu bölümde, böylece kullanıcı biçimlendirme seçeneği seçtiğinde, çalışma sayfasındaki metin biçimi değiştirilir kod yazacaksınız.  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Bir onay kutusu seçildiğinde biçimini değiştirmek için seçili  
  
1.  Sağ **Sayfa1**ve ardından **kodu görüntüle** kısayol menüsünde.  
  
2.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyBoldFont` onay kutusunu:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyItalicFont` onay kutusunu:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyUnderlineFont` onay kutusunu:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  C# ' ta onay kutuları için olay işleyicileri eklemelisiniz <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> aşağıda gösterildiği gibi olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık, çalışma kitabınızı seçin veya onay kutusunu temizleyin, metni doğru biçimlendirildiğinden emin olmak için test edebilirsiniz.  
  
### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Seçin veya onay kutusunun işaretini kaldırın.  
  
3.  Metni doğru şekilde biçimlendirildiğini doğrulayın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, onay kutularını kullanarak ve Excel çalışma sayfalarında metin biçimlendirme temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Projeyi dağıtma. Daha fazla bilgi için [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
-   Bir düğmeye bir metin kutusunu doldurmak için kullanma. Daha fazla bilgi için [izlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  