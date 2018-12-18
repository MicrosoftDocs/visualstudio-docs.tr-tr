---
title: 'Nasıl yapılır: Office belgelerine Windows forms denetimleri ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b5a6246a79d2d1f910b6ca39ce290f6c325dbe6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892759"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme
  Belge düzeyi projesinde tasarım zamanında Microsoft Office Excel ve Microsoft Office Word belgelerine Windows Forms denetimleri ekleyebilirsiniz. Belge düzeyi özelleştirmeleri ve VSTO eklentileri çalışma zamanında denetimler ekleyebilirsiniz. Örneğin, ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> denetlemek için çalışma böylece kullanıcılar bir seçeneklerini listeden seçebilirsiniz.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında denetimler ekleme](#designtime)  
  
- [Belge düzeyi projelere çalışma zamanında denetimler ekleme](#runtimedoclevel)  
  
- [VSTO eklentileri çalışma zamanında denetimler ekleme](#runtimeaddin)  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [nasıl ı: ekleme denetimleri belgeye yüzey çalışma zamanında?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Tasarım zamanında denetimler ekleme  
 Bir belge düzeyi projede tasarım zamanında Windows Forms denetimleri eklemenin birkaç yolu vardır.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Belgeye bir Windows Forms denetimi sürükleyin  
  
1.  Oluşturun veya belgeyi tasarımcıda görünür olması, bir Excel çalışma kitabı projesi veya Word belgesi proje Visual Studio'da açın. Proje oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **ortak denetimleri** sekmesinde **araç kutusu**, eklemek istediğiniz denetim tıklayın ve belgeye sürükleyin.  
  
    > [!NOTE]  
    >  Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Belgedeki bir Windows Forms denetimi çizmek için  
  
1.  Oluşturun veya belgeyi tasarımcıda görünür olması, bir Excel çalışma kitabı projesi veya Word belgesi proje Visual Studio'da açın. Proje oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **ortak denetimleri** sekmesinde **araç kutusu**, eklemek istediğiniz denetim tıklayın.  
  
3.  Belge bulunmasını denetimin sol üst köşesinde istediğiniz tıklayın ve konum için denetimin sağ alt köşedeki istediğiniz yere sürükleyin.  
  
     Denetim belgeye belirtilen konum ve boyut ile eklenir.  
  
    > [!NOTE]  
    >  Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Tek-denetim tıklayarak belgeye bir Windows Forms denetimi eklemek için  
  
1.  Oluşturun veya belgeyi tasarımcıda görünür olması, bir Excel çalışma kitabı projesi veya Word belgesi proje Visual Studio'da açın. Proje oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **ortak denetimleri** sekmesinde **araç kutusu**, eklemek istediğiniz denetimi  
  
3.  Bir belge eklenecek denetimin istediğiniz yeri tıklatın.  
  
     Denetimin varsayılan boyutu belgeyle eklenir.  
  
    > [!NOTE]  
    >  Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Denetime çift tıklayarak, belgeye bir Windows Forms denetimi eklemek için  
  
1.  Oluşturun veya belgeyi tasarımcıda görünür olması, bir Excel çalışma kitabı projesi veya Word belgesi proje Visual Studio'da açın. Proje oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **ortak denetimleri** sekmesinde **araç kutusu**, eklemek istediğiniz denetimi çift tıklatın.  
  
     Denetim, belgenin veya etkin bölmeyi merkezindeki belgeye eklenir.  
  
    > [!NOTE]  
    >  Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Enter tuşuna basarak, belgeye bir Windows Forms denetimi eklemek için  
  
1.  Oluşturun veya belgeyi tasarımcıda görünür olması, bir Excel çalışma kitabı projesi veya Word belgesi proje Visual Studio'da açın. Proje oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **ortak denetimleri** sekmesinde **araç kutusu**, ekleyin ve basın istediğiniz denetimi **Enter** anahtarı.  
  
     Denetim, belgenin veya etkin bölmeyi merkezindeki belgeye eklenir.  
  
    > [!NOTE]  
    >  Excel'de bir denetimi seçtiğinizde göreceğiniz **=EMBED("WinForms.Control.Host","")** içinde **formül çubuğu**. Bu metin, gereklidir ve silinmemelidir.  
  
##  <a name="runtimedoclevel"></a> Belge düzeyi projelere çalışma zamanında denetimler ekleme  
 Bir belgeye çalışma zamanında Windows Forms denetimlerine programlı olarak ekleyebilirsiniz. Word'de yöntemlerini kullanın <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> özelliği `ThisDocument` sınıfı. Excel'de yöntemlerini kullanın <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> özelliği bir `Sheet` *n* sınıfı. Her yöntem farklı şekillerde denetimin konumunu belirtmenize olanak sağlayan birçok aşırı yüklemeye sahip.  
  
 Bir belgeye çalışma zamanında Windows Forms denetimi eklediğinizde, denetimin belge kapatıldığında belgede kalıcı olmaz. Belgeyi bir sonraki açılışında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Çalışma zamanında Windows Forms denetimi eklemek için  
  
1.  Ekle adına sahip bir yöntem kullanmak\<*denetim sınıf*> (burada *denetim sınıf* sınıfı adı gibi eklemek istediğiniz Windows Forms denetiminin <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir <xref:Microsoft.Office.Tools.Excel.Controls.Button> hücreye **C5** , `Sheet1` Excel için belge düzeyi projesinde.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> VSTO eklentileri çalışma zamanında denetimler ekleme  
 Herhangi bir açık belgeye çalışma zamanında Windows Forms denetimlerine programlı olarak ekleyebilirsiniz. İlk olarak, bir açık belge veya çalışma sayfasını temel alan bir ana bilgisayar öğesi oluşturun. Word'de yöntemlerini kullanın <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> yeni konak öğesi özelliği. Excel'de yöntemlerini kullanın <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> yeni konak öğesi özelliği. Her yöntem farklı şekillerde denetimin konumunu belirtmenize olanak sağlayan birçok aşırı yüklemeye sahip.  
  
 Bir belgeye çalışma zamanında Windows Forms denetimi eklediğinizde, denetimin belge kapatıldığında belgede kalıcı olmaz. Belgeyi bir sonraki açılışında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 VSTO eklentisi projeleri, ana bilgisayar öğeleri oluşturma hakkında daha fazla bilgi için bkz. [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Çalışma zamanında Windows Forms denetimi eklemek için  
  
1.  Ekle adına sahip bir yöntem kullanmak\<*denetim sınıf*> (burada *denetim sınıf* sınıfı adı gibi eklemek istediğiniz Windows Forms denetiminin <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  VSTO eklenti hedefleyen projeleri [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra bir başvuru eklemelisiniz *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* veya *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* Ekle erişebilmeniz için önce derleme\<*denetim sınıf*> yöntemleri.  
  
     Aşağıdaki kod örneğinde nasıl ekleneceğini gösterir. bir <xref:Microsoft.Office.Tools.Word.Controls.Button> etkin belgenin bir sözcük VSTO eklentisi kullanarak ilk paragrafa.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  