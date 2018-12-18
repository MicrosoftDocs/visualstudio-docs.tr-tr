---
title: 'İzlenecek yol: metin kutusunda düğme kullanarak bir belgede metin görüntüleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 132a94b6e91148d943d998ab7e4aab96d0d74960
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822574"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>İzlenecek yol: metin kutusunda düğme kullanarak bir belgede metin görüntüleme
  Bu yönerge, düğmeler ve belge düzeyi özelleştirmesinde metin kutuları için Microsoft Office Word nasıl kullanılacağını gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Tasarım zamanında bir belge düzeyi projede Word belgesi için denetimler ekleme.  
  
- Bir düğmeye tıklandığında, metin kutusu dolduruluyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Word belgesi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adıyla bir Word belgesi projesi oluşturma **Word Düğmem**. Sihirbazda **yeni belge oluşturma**.  
  
     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **Word Düğmem** için proje **Çözüm Gezgini**.  
  
## <a name="add-controls-to-the-word-document"></a>Word belgesi için denetimler ekleme  
 Kullanıcı arabirimi denetimleri, bir düğme ve metin kutusu Word belgesinde oluşur.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Bir düğme ve metin kutusu ekleme  
  
1. Belge Visual Studio tasarımcıda açık olduğundan emin olun.  
  
2. Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:Microsoft.Office.Tools.Word.Controls.TextBox> belgeye denetim.  
  
   > [!NOTE]  
   >  Word'de denetimleri bırakılan satır içi varsayılan metin. Yol denetimlerini değiştirebilirsiniz ve şekil nesneleri üzerinde varsayılan değiştirerek eklenir **Düzenle** sekmesinde **seçenekleri** iletişim kutusundaki Word.  
  
3. Üzerinde **görünümü** menüsünde tıklatın **Özellikler penceresi**.  
  
4. Bulma **TextBox1** içinde **özellikleri** pencere açılan kutusu ve değişiklik **adı** özelliği için metin kutusunun **görüntü metni**.  
  
5. Sürükleme bir **düğmesi** denetim belgeye ve aşağıdaki özellikleri değiştirin.  
  
   |Özellik|Değer|  
   |--------------|-----------|  
   |**Ad**|**E:System.Windows.Forms.Control.Click**|  
   |**Metin**|**Metin Ekle**|  
  
   Artık düğmesine tıklandığında çalıştırılacak olan kodu yazabilirsiniz.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Düğme tıklandığında, metin kutusunu doldurmak  
 Kullanıcının düğmesini her tıklayışında **Merhaba Dünya!** metin kutusuna eklenir.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Düğme tıklandığında metin kutusuna yazmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisDocument**ve ardından **kodu görüntüle** kısayol menüsünde.  
  
2.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> düğmesi olay işleyicisi.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  İçinde C#, düğme için bir olay işleyicisi eklemelisiniz <xref:Microsoft.Office.Tools.Word.Document.Startup> olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık belgenizi emin olmak için test iletisi **Merhaba Dünya!** Düğmeye tıkladığınızda, metin kutusunda görüntülenir.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Düğmesine tıklayın.  
  
3.  Onaylayın **Merhaba Dünya!** metin kutusunda görüntülenir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, düğme ve metin kutusu Word belgelerinde kullanmanın temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Birleşik giriş kutusu biçimini değiştirmek için kullanma. Daha fazla bilgi için [izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Grafik stilleri seçilecek radyo düğmelerini kullanarak. Daha fazla bilgi için [izlenecek yol: radyo düğmelerini kullanarak belgede grafik güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Word'ü kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)  
  
  