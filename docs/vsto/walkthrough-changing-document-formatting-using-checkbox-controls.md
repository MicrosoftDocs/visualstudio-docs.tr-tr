---
title: 'İzlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86cf89f7853308e93c55e30deae17786fdb3e413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863938"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>İzlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme
  Bu yönerge Windows Forms denetimleri Microsoft Office Word için belge düzeyi özelleştirmesinde metin biçimlendirmesini değiştirmek için nasıl kullanılacağını gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Belge düzeyi projesindeki belgeye metin ve denetimi tasarım zamanında ekleniyor.  
  
- Bir seçenek belirlendiğinde, metin biçimlendirmesi.  
  
  Sonuç tamamlanmış bir örnek görmek için Word denetimleri örneğine bakın [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Word belgesi projesi oluşturmaktır.  
  
### <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
  
1.  Adıyla bir Word belgesi projesi oluşturma **My Word biçimlendirme**. Sihirbazda **yeni belge oluşturma**.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **My Word biçimlendirme** için proje **Çözüm Gezgini**.  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Word belgesine metin ve denetimler ekleme  
 Bu kılavuzda üç onay kutusunu ve biraz metin ekleyin bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetlemek için Word belgesi. Onay kutularını seçenekleri, kullanıcıya metin biçimlendirmesi için sunar.  
  
### <a name="add-three-check-boxes"></a>Üç onay kutusu ekleme  
  
1.  Belge Visual Studio tasarımcıda açık olduğundan emin olun.  
  
2.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ilk sürükleyin <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> belgeye denetim.  
  
3.  İçinde **özellikleri** penceresinde, aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**applyBoldFont**|  
    |**Metin**|**Kalın**|  
  
4.  Tuşuna **Enter** ekleme noktasını ilk onay kutusunun altına taşımak için.  
  
5.  Belgeye ikinci onay kutusu ekleme `ApplyBoldFont` onay kutusunu işaretleyin ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**ApplyItalicFont**|  
    |**Metin**|**İtalik**|  
  
6.  Tuşuna **Enter** ekleme noktasını ikinci onay kutusunun altına taşımak için.  
  
7.  Üçüncü onay kutusu belgeye ekleme `ApplyItalicFont` onay kutusunu işaretleyin ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**applyUnderlineFont**|  
    |**Metin**|**Alt çizgi**|  
  
### <a name="add-text-and-a-bookmark-control"></a>Metin ve bir yer işareti denetimi ekleme  
  
1. Ekleme noktasını onay kutusu denetimi altına taşıyın ve aşağıdaki metni yazın:  
  
    **Bu metin biçimini değiştirmek için bir onay kutusuna tıklayın.**  
  
2. Gelen **Word denetimleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgeye denetim.  
  
    **Yer işareti Denetimi Ekle** iletişim kutusu görüntülenir.  
  
3. Belgeye eklediğiniz metin seçin ve tıklayın **Tamam**.  
  
    A <xref:Microsoft.Office.Tools.Word.Bookmark> adlı Denetim **Bookmark1** belgedeki seçili metni eklenir.  
  
4. İçinde **özellikleri** penceresinde değiştirin **(ad)** özelliğini **fontText.**  
  
   Ardından, bir onay kutusu işaretli ya da seçili metni biçimlendirmek için kod yazın.  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Bir onay kutusu işaretli veya temizlenmiş metin biçimi  
 Kullanıcı biçimlendirme seçeneği seçtiğinde, belgedeki metin biçimini değiştirebilirsiniz.  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>Bir onay kutusu işaretli olduğunda biçimlendirmeyi Değiştir  
  
1.  Sağ `ThisDocument` içinde **Çözüm Gezgini**ve ardından **kodu görüntüle** kısayol menüsünde.  
  
2.  İçin C# yalnızca aşağıdaki sabitleri ekleyin **ThisDocument** sınıfı.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyBoldFont` onay kutusu.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyItalicFont` onay kutusu.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine `applyUnderlineFont` onay kutusu.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  İçinde C#, metin kutuları için olay işleyicileri eklemelisiniz <xref:Microsoft.Office.Tools.Word.Document.Startup> olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık seçin veya onay kutusunu temizleyin, metni doğru şekilde biçimlendirildiğinden emin olmak belgeye test edebilirsiniz.  
  
### <a name="test-your-document"></a>Belgenizi test edin  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Seçin veya onay kutusunun işaretini kaldırın.  
  
3.  Metni doğru şekilde biçimlendirildiğini doğrulayın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, onay kutularını kullanarak ve program aracılığıyla Word belgelerinde biçimlendirme metin değiştirme temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Bir düğmeye bir metin kutusunu doldurmak için kullanın. Daha fazla bilgi için [izlenecek yol: metin kutusunda düğme kullanarak bir belgede metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Grafik stilleri seçilecek radyo düğmelerini kullanarak. Daha fazla bilgi için [izlenecek yol: radyo düğmelerini kullanarak belgede grafik güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  

## <a name="see-also"></a>Ayrıca bkz.  
 [Word'ü kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  