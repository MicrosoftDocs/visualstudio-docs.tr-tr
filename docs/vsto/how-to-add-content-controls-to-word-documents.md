---
title: 'Nasıl yapılır: içerik ekleme denetimlerine Word belgeleri'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f654efacace3e4b7cbdfff8919309a09d4a544ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936972"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Nasıl yapılır: içerik ekleme denetimlerine Word belgeleri
  Belge düzeyi Word projelerinde, içerik denetimleri belgeye projenizde tasarım zamanında veya çalışma zamanında ekleyebilirsiniz. Word VSTO eklenti projesinde herhangi bir açık belgeye çalışma zamanında içerik denetimlerine ekleyebilirsiniz.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Bu konuda, aşağıdaki görevleri açıklanmaktadır:  
  
- [Tasarım zamanında içerik denetimleri ekleme](#designtime)  
  
- [Çalışma zamanında bir belge düzeyi projede içerik denetimleri ekleme](#runtimedoclevel)  
  
- [Çalışma zamanında VSTO eklenti projesindeki içerik denetimleri ekleme](#runtimeaddin)  
  
  İçerik denetimleri hakkında daha fazla bilgi için bkz: [içerik denetimleri](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> İçerik ekleme denetimleri tasarım zamanında  
 Belge düzeyi projesinde tasarım zamanında içerik denetimleri eklemenin birkaç yolu vardır:  
  
- Bir içerik denetimi ekleme **Word denetimleri** sekmesinde **araç kutusu**.  
  
- İçerik denetimi eklemek aynı şekilde belgenize Word'de yerel içerik denetimine eklersiniz.  
  
- Belgenizdeki içerikleri için bir içerik denetimi sürükleyin **veri kaynakları** penceresi. Denetim oluşturulduğunda denetimini verilere bağlama istediğinizde bu kullanışlıdır. Daha fazla bilgi için [nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md) ve [nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Araç kutusunu kullanarak belge bir içerik denetimi eklemek için  
  
1.  Barındırılan belge içindeki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı, içerik denetimi eklemek veya değiştirmek için içerik denetimi istediğiniz metni seçmek istediğiniz imleci yerleştirin.  
  
2.  Açık **araç kutusu** tıklatıp **Word denetimleri** sekmesi.  
  
3.  Denetimi aşağıdaki yollardan birini ekleyin:  
  
    -   Bir içerik denetimi çift **araç kutusu**.  
  
         veya  
  
    -   İçindeki içerik bir denetimi **araç kutusu** ve tuşuna **Enter** anahtarı.  
  
         veya  
  
    -   Bir içerik denetimi **araç kutusu** belge. İçerik denetimi, fare işaretçisi konumunu değil, geçerli seçime belgedeki eklenir.  
  
> [!NOTE]  
>  Ekleyemezsiniz bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> kullanarak **araç kutusu**. Yalnızca ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> Word veya çalışma zamanında.  
  
> [!NOTE]  
>  Visual Studio araç kutusu bir onay kutusu içerik denetimi sağlamaz. Belgeye bir onay kutusu içerik denetimi eklemek için oluşturmalısınız bir <xref:Microsoft.Office.Tools.Word.ContentControl> programlı olarak nesnesi. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Word belgesinde bir içerik denetimi eklemek için  
  
1.  Barındırılan belge içindeki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı, içerik denetimi eklemek veya değiştirmek için içerik denetimi istediğiniz metni seçmek istediğiniz imleci yerleştirin.  
  
2.  Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
    > [!NOTE]  
    >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  İçinde **denetimleri** grubunda, eklemek istediğiniz içerik denetiminin simgesine tıklayın.  
  
##  <a name="runtimedoclevel"></a> Çalışma zamanında bir belge düzeyi projede içerik denetimleri ekleme  
 İçerik denetimlerine programlı olarak çalışma zamanında belgenize yöntemleri kullanılarak ekleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliği `ThisDocument` projenizdeki sınıfı. Her yöntemin içerik denetimi aşağıdaki yollarla eklemek için kullanabileceğiniz üç aşırı yüklemeleri vardır:  
  
- Geçerli seçimde bir denetim ekleyin.  
  
- Belirli bir aralıkta bir denetim ekleyin.  
  
- Belge içindeki yerel içerik denetimine bağlı bir denetim ekleyin.  
  
  Dinamik olarak belge kapatıldığında içerik denetimleri kaybolacağından belgede oluşturuldu. Ancak, yerel bir içerik denetimi belgede kalır. Belgeyi bir sonraki açılışında bir yerel içerik denetimine bağlı bir içerik denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Word 2010 projesinde bir belge onay kutusu içerik denetimi eklemek için oluşturmalısınız bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesne. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Geçerli seçimde bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve yeni denetimin adı için tek bir parametreye sahip.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeyi başlangıcına. Bu kodu çalıştırmak için koda Ekle `ThisDocument` sınıfı proje ve çağrı `AddRichTextControlAtSelection` yönteminden `ThisDocument_Startup` olay işleyicisi.  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Belirli bir aralıkta bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve bir <xref:Microsoft.Office.Interop.Word.Range> parametresi.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeyi başlangıcına. Bu kodu çalıştırmak için koda Ekle `ThisDocument` sınıfı proje ve çağrı `AddRichTextControlAtRange` yönteminden `ThisDocument_Startup` olay işleyicisi.  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Bir yerel içerik denetimine bağlı bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve bir `Microsoft.Office.Interop.Word.ContentControl` parametresi.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgedeki her yerel zengin metin denetimi. Bu kodu çalıştırmak için koda Ekle `ThisDocument` sınıfı proje ve çağrı `CreateRichTextControlsFromNativeControls` yönteminden `ThisDocument_Startup` olay işleyicisi.  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Çalışma zamanında VSTO eklenti projesindeki içerik denetimleri ekleme  
 İçerik denetimlerini programlı olarak herhangi bir açık belgeye çalışma zamanında VSTO eklenti kullanarak ekleyebilirsiniz. Bunu yapmak için oluşturmak bir <xref:Microsoft.Office.Tools.Word.Document> barındıran bir açık belgeye dayalı öğesini ve ardından yöntemlerinin <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> bu konak öğesi özelliği. Her yöntemin içerik denetimi aşağıdaki yollarla eklemek için kullanabileceğiniz üç aşırı yüklemeleri vardır:  
  
- Geçerli seçimde bir denetim ekleyin.  
  
- Belirli bir aralıkta bir denetim ekleyin.  
  
- Belge içindeki yerel içerik denetimine bağlı bir denetim ekleyin.  
  
  Dinamik olarak belge kapatıldığında içerik denetimleri kaybolacağından belgede oluşturuldu. Ancak, yerel bir içerik denetimi belgede kalır. Belgeyi bir sonraki açılışında bir yerel içerik denetimine bağlı bir içerik denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [Office belgelerinde Dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  VSTO eklentisi projeleri, ana bilgisayar öğeleri oluşturma hakkında daha fazla bilgi için bkz. [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Belge onay kutusu içerik denetimi eklemek için oluşturmalısınız bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesne. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Geçerli seçimde bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve yeni denetimin adı için tek bir parametreye sahip.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> etkin belgeyi başlangıcına. Bu kodu çalıştırmak için koda Ekle `ThisAddIn` sınıfı proje ve çağrı `AddRichTextControlAtSelection` yönteminden `ThisAddIn_Startup` olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Belirli bir aralıkta bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve bir <xref:Microsoft.Office.Interop.Word.Range> parametresi.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> etkin belgeyi başlangıcına. Bu kodu çalıştırmak için koda Ekle `ThisAddIn` sınıfı proje ve çağrı `AddRichTextControlAtRange` yönteminden `ThisAddIn_Startup` olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Bir yerel içerik denetimine bağlı bir içerik denetimi eklemek için  
  
1.  Kullanım bir <xref:Microsoft.Office.Tools.Word.ControlCollection> adına sahip yöntemi `Add` \< *denetim sınıf*> (burada *denetim sınıf* gibi eklemekistediğiniziçerikdenetimisınıfadıdır<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), ve bir `Microsoft.Office.Interop.Word.ContentControl` parametresi.  
  
     Aşağıdaki kod örneğinde <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> yeni bir yöntem <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belge açıldıktan sonra bir belgedeki her yerel zengin metin denetimi. Bu kodu çalıştırmak için koda Ekle `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     C# ' de eklediğiniz gerekir `Application_DocumentOpen` olay işleyicisine <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> olay.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)  
  