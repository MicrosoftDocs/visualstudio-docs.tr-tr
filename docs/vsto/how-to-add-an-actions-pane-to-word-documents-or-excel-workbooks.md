---
title: 'Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f70511d0490032204789dc037a13847a10b5cbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948367"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Nasıl Yapılır: Word Belgelerine veya Excel Çalışma Kitaplarına Eylemler Bölmesi Ekleme
  Microsoft Office Word belgesi veya Microsoft Excel çalışma kitabına Eylemler bölmesi ekleme için önce bir Windows Forms kullanıcı denetimi oluşturun. Ardından, kullanıcı denetimine ekleyin <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği `ThisDocument.ActionsPane` alan (Word) veya `ThisWorkbook.ActionsPane` projenizdeki alan (Excel).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Kullanıcı denetimi oluşturma  
 Aşağıdaki yordam, Word kullanıcı denetimi oluşturma veya Excel proje gösterir. Ayrıca bir düğme tıklandığında, metin belge veya çalışma kitabındaki Yazar kullanıcı denetimine ekler.  
  
#### <a name="to-create-the-user-control"></a>Kullanıcı denetimi oluşturmak için  
  
1.  Word veya Excel belge düzeyi projenizi Visual Studio'da açın.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Eylemler bölmesi denetimi**, adlandırın **HelloControl**, tıklatıp **Ekle**.  
  
    > [!NOTE]  
    >  Alternatif olarak ekleyebileceğiniz bir **kullanıcı denetimi** projenize öğesi. Tarafından oluşturulan sınıflar **Eylemler bölmesi denetimi** ve **kullanıcı denetimi** öğeleri işlevsel olarak eşdeğerdir.  
  
4.  Gelen **Windows Forms** sekmesinde **araç** sürükleyin bir **düğmesi** denetimi denetimi sürükleyin.  
  
    > [!NOTE]  
    >  Denetim Tasarımcısı'nda görünür değilse, çift tıklayarak **HelloControl** içinde **Çözüm Gezgini**.  
  
5.  Koda ekleme <xref:System.Windows.Forms.Control.Click> düğmesi olay işleyicisi. Aşağıdaki örnek, bir Microsoft Office Word belgesi için kod gösterir.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  C# ' düğmesine tıklayarak bir olay işleyicisi eklemeniz gerekir. Bu kodu koyabilirsiniz `HelloControl` Oluşturucusu çağrısından sonra `InitializeComponent`.  
  
     Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesi kullanıcı denetimi Ekle  
 Eylemler bölmesinde göstermek için kullanıcı denetimine ekleme <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği `ThisDocument.ActionsPane` alan (Word) veya `ThisWorkbook.ActionsPane` alan (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesi kullanıcı denetimi eklemek için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument` veya `ThisWorkbook` sınıf düzeyi bildirimle sınıfı (Bu kod bir yönteme eklemeyin).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` olay işleyicisine `ThisDocument` sınıfı veya `ThisWorkbook_Startup` olay işleyicisine `ThisWorkbook` sınıfı.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  