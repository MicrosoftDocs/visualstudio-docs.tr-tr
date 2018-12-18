---
title: 'İzlenecek yol: bir belgeye çalışma zamanında VSTO eklenti denetimler ekleme'
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
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 774e26388f5eb25fb0a16dee05557c6bf34a0ff0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951593"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>İzlenecek yol: bir belgeye çalışma zamanında VSTO eklenti denetimler ekleme
  Bir VSTO eklentisi kullanarak, Microsoft Office Word'ün herhangi bir açık belgeye denetimler ekleyebilirsiniz. Bu izlenecek yol ekleme olanağı Şerit kullanmayı gösterir. bir <xref:Microsoft.Office.Tools.Word.Controls.Button> veya <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye.  

 **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Word 2010 VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).  

 Bu izlenecek yol aşağıdaki görevleri gösterir:  

- Yeni bir Word VSTO eklentisi projesi oluşturma.  

- Bir kullanıcı arabirimi (UI) denetimler eklemek için belgenin sağlama.  

- Belgeye çalışma zamanında denetimler ekleme.  

- Belgeden denetimlerini kaldırma.  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  

## <a name="create-a-new-word-add-in-project"></a>Yeni bir Word eklenti projesi oluşturun  
 Bir sözcük VSTO eklentisi projesi oluşturarak başlayın.  

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Yeni bir Word VSTO eklenti projesi oluşturmak için  

1.  Adlı Word için VSTO eklentisi projesi oluşturun **WordDynamicControls**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Bir başvuru ekleyin **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** derleme. Bu başvuru, bu kılavuzda daha sonra belge program aracılığıyla bir Windows Forms denetimi eklemek için gereklidir.  

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Belgeye denetim eklemek için bir kullanıcı Arabirimi sağlar.  
 Word Şerite özel sekme ekleyin. Kullanıcılar onay kutularını belgeye denetim eklemek için sekmesinde seçebilir.  

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Belgeye denetim eklemek için bir UI sağlamak için  

1. Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  

2. İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)**.  

3. Yeni Şeridin adını değiştirmek **MyRibbon**, tıklatıp **Ekle**.  

    **MyRibbon.cs** veya **MyRibbon.vb** dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.  

4. Şerit Tasarımcısı'nda tıklatın **group1** grubu.  

5. İçinde **özellikleri** penceresinde değişiklik **etiket** özelliği **group1** için **ekleme denetimleri**.  

6. Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **onay kutusu** denetimi **group1**.  

7. Tıklayın **CheckBox1** seçin.  

8. İçinde **özellikleri** penceresinde, aşağıdaki özellikleri değiştirin.  


   | Özellik | Değer |
   |-----------|-----------------------|
   | **Ad** | **addButtonCheckBox** |
   | **Etiket** | **Ekle düğmesi** |


9. İkinci bir onay kutusu ekleme **group1**ve ardından aşağıdaki özellikleri değiştirin.  


   | Özellik | Değer |
   |-----------|---------------------------|
   | **Ad** | **addRichTextCheckBox** |
   | **Etiket** | **Zengin metin denetimi ekleme** |


10. Şerit Tasarımcısı'nda çift **Ekle düğmesi**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Olay işleyicisine **Ekle düğmesi** onay kutusu, Kod Düzenleyicisi'nde açılır.  

11. Şerit Tasarımcısına döndürür ve çift **zengin metin denetimi eklemek**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Olay işleyicisine **zengin metin denetimi eklemek** onay kutusu, Kod Düzenleyicisi'nde açılır.  

    Bu kılavuzda daha sonra bu olay işleyicileri denetimleri etkin belgede eklemek ve kaldırmak için kod ekleyeceksiniz.  

## <a name="add-and-remove-controls-on-the-active-document"></a>Etkin belgeyi denetimleri ekleyip  
 VSTO eklenti kodu etkin belgeye dönüştürmelisiniz bir <xref:Microsoft.Office.Tools.Word.Document> *konak öğesi* önce bir denetim ekleyebilirsiniz. Office çözümlerinde, yönetilen denetimleri denetimler için kapsayıcı olarak davranan konak öğeleri eklenebilir. Projelerinde, VSTO eklentisi, ana bilgisayar öğeleri çalışma zamanında kullanarak oluşturulabilir `GetVstoObject` yöntemi.  

 Yöntemlere ekleme `ThisAddIn` eklemek veya kaldırmak için çağrılabilir sınıfı bir <xref:Microsoft.Office.Tools.Word.Controls.Button> veya <xref:Microsoft.Office.Tools.Word.RichTextContentControl> etkin belgede. Bu kılavuzda daha sonra bu yöntemleri çağırır <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Şerit onay kutularının olay işleyicileri.  

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Etkin belge üzerinde denetimleri eklemek ve kaldırmak için  

1.  İçinde **Çözüm Gezgini**, çift *ThisAddIn.cs* veya *ThisAddIn.vb* dosyası Kod Düzenleyicisi'nde açın.  

2.  Aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod bildirir <xref:Microsoft.Office.Tools.Word.Controls.Button> ve <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye eklediğiniz denetimlerini temsil eden nesneleri.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  

3.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Kullanıcı tıkladığında **Ekle düğmesi** Şerit onay kutusunu, bu yöntemi ekler bir <xref:Microsoft.Office.Tools.Word.Controls.Button> onay kutusunun seçili olduğundan geçerli seçime <xref:Microsoft.Office.Tools.Word.Controls.Button> onay kutusu işaretli değilse.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  

4.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Kullanıcı tıkladığında **zengin metin denetimi eklemek** Şerit onay kutusunu, bu yöntemi ekler bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> onay kutusunun seçili olduğundan geçerli seçime <xref:Microsoft.Office.Tools.Word.RichTextContentControl> onay kutusu işaretli değilse.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Düğme denetimini Belge kaydedildiğinde Kaldır  
 Belgenin kaydedilip kapatılan Windows Forms denetimleri kalıcı değildir. Ancak, bir ActiveX sarmalayıcısının üretimi için her denetim, belgede kalır ve bu sarmalayıcı kenarlığını belge açıldığında son kullanıcılar tarafından görülebilir. VSTO eklentileri dinamik olarak oluşturulan Windows Forms denetimlerinde temizlemek için birkaç yolu vardır. Bu izlenecek yolda, program aracılığıyla kaldırma <xref:Microsoft.Office.Tools.Word.Controls.Button> olduğunda Belge kaydedildiğinde denetim.  

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Düğme denetimini Belge kaydedildiğinde kaldırmak için  

1.  İçinde *ThisAddIn.cs* veya *ThisAddIn.vb* kod dosyası, aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Bu yöntem için bir olay işleyicisidir <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay. Kaydedilen belge varsa bir <xref:Microsoft.Office.Tools.Word.Document> , olay işleyicisi ilişkili konak öğesi ana öğeyi alır ve kaldırır <xref:Microsoft.Office.Tools.Word.Controls.Button> varsa denetimi.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  

2.  C# ' ta için aşağıdaki kodu ekleyin `ThisAddIn_Startup` olay işleyicisi. Bu kod C# dilinde bağlanmak için gereken `Application_DocumentBeforeSave` olay işleyicisi ile <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay.  

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Ekleme ve kullanıcı onay kutularını Şerit üzerindeki tıkladığında denetimlerini kaldırma  
 Son olarak, değişiklik <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> onay kutularının olay işleyicileri, eklediğiniz Şerit denetimleri belgesinde eklemek veya kaldırmak için.  

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Kullanıcı onay kutularını Şerit üzerindeki tıkladığında eklemek veya kaldırmak için denetimleri  

1.  İçinde *MyRibbon.cs* veya *MyRibbon.vb* kod dosyası, oluşturulan yerine `addButtonCheckBox_Click` ve `addRichTextCheckBox_Click` aşağıdaki kod ile olay işleyicileri. Bu kodu çağırmak için bu olay işleyicileri'ı yeniden tanımladığı `ToggleButtonOnDocument` ve `ToggleRichTextControlOnDocument` eklediğiniz yöntemleri `ThisAddIn` bu kılavuzda daha önce açıklanan sınıfı.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  

## <a name="test-the-solution"></a>Çözüm test  
 Denetim belgeye özel Şerit sekmesinden seçerek ekleyin. Belgeyi kaydettiğinizde <xref:Microsoft.Office.Tools.Word.Controls.Button> denetimi kaldırılır.  

### <a name="to-test-the-solution"></a>Çözümü test etmek için.  

1.  Tuşuna **F5** projeyi çalıştırın.  

2.  Etkin belgedeki basın **Enter** yeni eklemek için birkaç kez paragraflar belge boş.  

3.  İlk paragrafa seçin.  

4.  Tıklayın **eklentileri** sekmesi.  

5.  İçinde **ekleme denetimleri** grubunda **Ekle düğmesi**.  

     İlk paragrafa bir düğme görüntülenir.  

6.  Son paragrafı seçin.  

7.  İçinde **ekleme denetimleri** grubunda **zengin metin denetimi eklemek**.  

     Zengin metin içerik denetimi, paragraf son eklenir.  

8.  Belgeyi kaydedin.  

     Düğme belgeden kaldırılır.  

## <a name="next-steps"></a>Sonraki adımlar  
 VSTO eklentilerinde aşağıdaki konulardan denetimleri hakkında daha fazla bilgi edinebilirsiniz:  

-   Word eklenti dinamik denetim örneği, belgeye çalışma zamanında diğer pek çok denetimi türleri ekleyin ve belge açıldığında denetimleri yeniden nasıl oluşturulduğunu gösteren bir örnek için bkz [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  

-   Excel için VSTO eklentisi kullanarak bir çalışma sayfasına denetimler ekleme yapmayı gösteren bir kılavuz için bkz. [izlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  

## <a name="see-also"></a>Ayrıca bkz.  
 [Word çözümleri](../vsto/word-solutions.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Word belgelerini ve Excel çalışma kitaplarını VSTO eklentileri çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  

