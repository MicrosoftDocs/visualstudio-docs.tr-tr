---
title: 'Nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma'
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
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: beee4dd4a67b03f278a296d4b5f129100212fd25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850366"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma
  Belgenin bir bölümünü koruduğunuzda, kullanıcıların belgenin bu bölümü içeriğini silme veya değiştirme engeller. İçerik denetimlerini kullanarak bir Microsoft Office Word belgesi kısımlarını korumak için birkaç yol vardır:  
  
- Bir içerik denetimi koruyabilirsiniz.  
  
- Bir içerik denetiminde değil belgenin bir bölümünü koruyabilir.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Bir içerik denetimi koruyun  
 Düzenleme veya bir içerik denetimi tasarım zamanında veya çalışma zamanında bir belge düzeyi projede denetimin özelliklerini ayarlayarak, kullanıcıların engelleyebilirsiniz.  
  
 Bir VSTO eklentisi projesi kullanarak belgeye çalışma zamanında ekleme içerik denetimleri de koruyabilir. Daha fazla bilgi için [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
### <a name="to-protect-a-content-control-at-design-time"></a>Tasarım zamanında bir içerik denetimi korumak için  
  
1.  Barındırılan belge içindeki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı, korumak istediğiniz içerik denetimi seçin.  
  
2.  İçinde **özellikleri** penceresinde birini veya ikisini de aşağıdaki özellikleri ayarlayın:  
  
    -   Kullanıcı denetimi düzenlemesini önlemek için ayarlanmış **LockContents** için **True**.  
  
    -   Kullanıcılar, silmesini önleyecek şekilde ayarlanmış **LockContentControl** için **True**.  
  
3.  **Tamam**'ı tıklatın.  
  
### <a name="to-protect-a-content-control-at-runtime"></a>Çalışma zamanında bir içerik denetimi korumak için  
  
1.  Ayarlama `LockContents` içerik denetimin özellik **true** kullanıcıların Denetim düzenlemesini önlemek ve ayarlamak için `LockContentControl` özelliğini **true** silmesini kullanıcıların önlemek için.  
  
     Aşağıdaki kod örneği kullanmayı gösterir <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> ve <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> iki farklı özelliklerini <xref:Microsoft.Office.Tools.Word.RichTextContentControl> bir belge düzeyi projede nesneleri. Bu kodu çalıştırmak için koda Ekle `ThisDocument` sınıfı proje ve çağrı `AddProtectedContentControls` yönteminden `ThisDocument_Startup` olay işleyicisi.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     Aşağıdaki kod örneği kullanmayı gösterir <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> ve <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> iki farklı özelliklerini <xref:Microsoft.Office.Tools.Word.RichTextContentControl> bir VSTO eklenti projesindeki nesneleri. Bu kodu çalıştırmak için koda Ekle `ThisAddIn` sınıfı proje ve çağrı `AddProtectedContentControls` yönteminden `ThisAddIn_Startup` olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Bir içerik denetiminde değil belgenin bir bölümünü koruyun  
 Kullanıcıların alanı koyarak bir belge alanını değiştirmesini engelleyebilirsiniz bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Aşağıdaki senaryolarda kullanışlıdır:  
  
-   İçerik denetimleri içermeyen bir alan korumak istiyorsunuz.  
  
-   İçerik denetimleri içeren bir alan korumak istediğiniz, ancak içerik denetimleri metin veya korumak istediğiniz diğer öğeleri değildir.  
  
> [!NOTE]  
>  Oluşturursanız, bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> katıştırılmış içerik denetimleri içeren, katıştırılmış içerik denetimleri otomatik olarak korunmaz. Kullanıcılar bir katıştırılmış içerik denetimi düzenlemesini önlemek için **LockContents** denetiminin özelliği.  
  
### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Tasarım zamanında bir alanı boyutundaki bir belgeyi korumak için  
  
1.  Barındırılan belge içindeki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı, korumak istediğiniz alanı seçin.  
  
2.  Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
    > [!NOTE]  
    >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  İçinde **denetimleri** grubunda **grubu** açılan düğmesine ve ardından **grubu**.  
  
     A <xref:Microsoft.Office.Tools.Word.GroupContentControl> içeren korumalı bölge oluşturulan otomatik olarak `ThisDocument` projenizdeki sınıfı. Tasarım zamanında grubu denetimini temsil eden bir kenarlık görünür, ancak çalışma zamanında görünür bir kenarlık yoktur.  
  
### <a name="to-protect-an-area-of-a-document-at-runtime"></a>Belgeye çalışma zamanında bir alanı korumak için  
  
1.  Programlı olarak koruyun ve ardından çağırmak istediğiniz alanı seçin <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> yöntemi oluşturmak için bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     Belge düzeyi projesi için aşağıdaki kod örneği belgedeki ilk paragrafa metin ilk paragrafa seçer ve ardından başlatır ekler bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Bu kodu çalıştırmak için koda Ekle `ThisDocument` sınıfı proje ve çağrı `ProtectFirstParagraph` yönteminden `ThisDocument_Startup` olay işleyicisi.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     Bir VSTO eklentisi projesi için aşağıdaki kod örneği, etkin belgedeki ilk paragrafa metin ilk paragrafa seçer ve ardından başlatır ekler bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Bu kodu çalıştırmak için koda Ekle `ThisAddIn` sınıfı proje ve çağrı `ProtectFirstParagraph` yönteminden `ThisAddIn_Startup` olay işleyicisi.  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [İçerik denetimleri](../vsto/content-controls.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)  
   