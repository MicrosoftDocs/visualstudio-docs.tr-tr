---
title: 'Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 33afb16b9862f418f4d661bb5432ea4bb3866f16
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878615"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Nasıl yapılır: Word belgelerine yer işareti denetimi ekleme
  Belge düzeyinde projelerde eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> belgenin tasarım zamanında veya çalışma zamanında, projenizdeki denetimler. Projelerinde, VSTO eklentisi, eklediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> herhangi bir açık belgeye çalışma zamanında denetimler.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında yer işareti denetimi ekleme](#designtime)  
  
- [Çalışma zamanında bir belge düzeyi projede yer işareti denetimi ekleme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesinde yer işareti denetimi ekleme](#runtimeaddin)  
  
  Hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.Bookmark> denetimlerini, [yer işareti denetimi](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Tasarım zamanında yer işareti denetimi ekleme  
 Eklemek için çeşitli yollar vardır <xref:Microsoft.Office.Tools.Word.Bookmark> denetimleri tasarım zamanında bir belge düzeyinde projedeki belge:  
  
- Visual Studio'dan **araç kutusu**.  
  
   Sürükleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi **araç kutusu** belgenize. Zaten kullanıyorsanız, bu şekilde seçmek isteyebilirsiniz **araç kutusu** belgenize Windows Forms denetimleri ekleme.  
  
- Word'ün içinden.  
  
   Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi aynı şekilde belgenize yerel yer eklersiniz. Bu şekilde ekleme avantajı, oluşturma zamanında denetiminizi adlandırabilirsiniz olmasıdır.  
  
- Gelen **veri kaynakları** penceresi.  
  
   Sürükleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Bookmark> belgenizden denetimine **veri kaynakları** penceresi. Bu verileri aynı anda denetimine bağlamak istediğiniz durumlarda kullanışlıdır. Konak kontrolü ekleme bir Windows Form denetimi aynı şekilde ekleyebileceğiniz **veri kaynakları** penceresi. Daha fazla bilgi için [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Araç kutusundan bir belgeye Bookmark denetimi eklemek için  
  
1.  Açık **araç kutusu** tıklatıp **Word denetimleri** sekmesi.  
  
2.  Sürükleme bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgeye denetim.  
  
     **Yer işareti Ekle** iletişim kutusu görüntülenir.  
  
3.  Metin veya yer işareti olarak eklemek istediğiniz diğer öğeleri seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Varsayılan yer işareti adı tutmak istemiyorsanız adı değiştirebilirsiniz **özellikleri** penceresi.  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Word belgesinde bir yer işareti denetimi eklemek için  
  
1.  Barındırılan belge içindeki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı, yer işareti eklemek veya yer işaretinin içermesini istediğiniz metni seçmek istediğiniz imleci yerleştirin.  
  
2.  Üzerinde **Ekle** Şerit sekmesinde, **bağlantıları** grubunda **yer işareti** düğmesi.  
  
3.  İçinde **yer işareti** iletişim kutusunda, yeni yer işareti adını yazın ve tıklayın **Ekle**.  
  
##  <a name="runtimedoclevel"></a> Çalışma zamanında bir belge düzeyi projede yer işareti denetimi ekleme  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> denetimlerini programlı olarak çalışma zamanında belgenize yöntemleri kullanılarak <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliği `ThisDocument` projenizdeki sınıfı. Eklemek için kullanabileceğiniz iki yöntem aşırı yüklemesi vardır bir <xref:Microsoft.Office.Tools.Word.Bookmark> aşağıdaki yollarla denetimi:  
  
- Ekleme bir <xref:Microsoft.Office.Tools.Word.Bookmark> belirtilen aralıkta.  
  
- Ekleme bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgedeki yerel bir yer işaretine dayanır (diğer bir deyişle, bir <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Dinamik olarak oluşturulan <xref:Microsoft.Office.Tools.Word.Bookmark> denetimleri belge kapatıldığında belgede sürdürülmez. Ancak, bir yerel <xref:Microsoft.Office.Interop.Word.Bookmark> belgede kalır. Yeniden oluşturabileceğinizi bir <xref:Microsoft.Office.Tools.Word.Bookmark> temel yerel bir yer işaretini belgenin sonraki açılışında. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Belge, program aracılığıyla bir yer işareti denetimi eklemek için  
  
1.  İçinde `ThisDocument_Startup` projenizde, olay işleyicisi eklemek için aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Word.Bookmark> belgedeki ilk paragrafa denetimi.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Oluşturmak istiyorsanız bir <xref:Microsoft.Office.Tools.Word.Bookmark> varolan bir denetimi <xref:Microsoft.Office.Interop.Word.Bookmark>, kullanın <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> yöntemi ve mevcut geçişi <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesinde yer işareti denetimi ekleme  
 Ekleyebileceğiniz <xref:Microsoft.Office.Tools.Word.Bookmark> programlı bir şekilde herhangi bir açık belgeye bir VSTO eklenti kullanarak çalışma zamanında denetimler. Bunu yapmak için oluşturmak bir <xref:Microsoft.Office.Tools.Word.Document> barındıran bir açık belgeye dayalı öğesini ve ardından yöntemlerinin <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> bu konak öğesi özelliği. Eklemek için kullanabileceğiniz iki yöntem aşırı yüklemesi vardır bir <xref:Microsoft.Office.Tools.Word.Bookmark> aşağıdaki yollarla denetimi:  
  
- Ekleme bir <xref:Microsoft.Office.Tools.Word.Bookmark> belirtilen aralıkta.  
  
- Ekleme bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgedeki yerel bir yer işaretine dayanır (diğer bir deyişle, bir <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Dinamik olarak oluşturulan <xref:Microsoft.Office.Tools.Word.Bookmark> denetimleri belge kapatıldığında belgede sürdürülmez. Ancak, bir yerel <xref:Microsoft.Office.Interop.Word.Bookmark> belgede kalır. Yeniden oluşturabileceğinizi bir <xref:Microsoft.Office.Tools.Word.Bookmark> temel yerel bir yer işaretini belgenin sonraki açılışında. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  VSTO eklentisi projeleri, ana bilgisayar öğeleri oluşturma hakkında daha fazla bilgi için bkz. [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Belirli bir aralıkta yer işareti denetimi ekleme  
  
1.  Kullanım <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> yöntemi ve geçişinde <xref:Microsoft.Office.Interop.Word.Range> eklemek istediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Aşağıdaki kod örneğinde yeni bir ekler <xref:Microsoft.Office.Tools.Word.Bookmark> etkin belgeyi başlangıcına. Bu örneği kullanmak için kodu çalıştırın `ThisAddIn_Startup` Word VSTO eklenti projesinde olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Yerel bir yer işareti denetimine bağlı bir yer işareti denetimi ekleme  
  
1.  Kullanma <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> yöntemi ve mevcut geçişi <xref:Microsoft.Office.Interop.Word.Bookmark> yeni için temel olarak kullanmak istediğiniz <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Aşağıdaki kod örneği yeni bir oluşturur <xref:Microsoft.Office.Tools.Word.Bookmark> diğer bir deyişle ilk göre <xref:Microsoft.Office.Interop.Word.Bookmark> etkin belgedeki. Bu örneği kullanmak için kodu çalıştırın `ThisAddIn_Startup` Word VSTO eklenti projesinde olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Nasıl yapılır: yer işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)  
  
  