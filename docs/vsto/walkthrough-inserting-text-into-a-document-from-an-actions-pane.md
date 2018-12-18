---
title: 'İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme'
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
ms.openlocfilehash: b3b9683c5f41b81d529ad6f3347b54131f32f011
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948731"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme
  Bu yönerge, Microsoft Office Word belgesinde Eylemler bölmesi oluşturma işlemini gösterir. Eylemler bölmesinde girişini toplamak ve ardından metin belgeye gönderen iki denetimleri içerir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Bir arabirim, Eylemler bölmesi denetimi Windows Forms denetimleri kullanarak tasarlayın.  
  
-   Uygulama açıldığında eylemler bölmesini görüntüler.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Word belgesi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adıyla bir Word belgesi projesi oluşturma **My temel Actions Pane**. Sihirbazda **yeni belge oluşturma**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **My temel Actions Pane** için proje **Çözüm Gezgini**.  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>Belgeye metin ve yer işaretlerini Ekle  
 Eylemler bölmesinde yer işaretleri belgedeki metin gönderir. Belge tasarlamak için temel bir form oluşturmak için bir metin yazın.  
  
### <a name="to-add-text-to-your-document"></a>Belgeye metin ekleme  
  
1. Word belgenize aşağıdaki metni yazın:  
  
    **21 Mart 2008**  
  
    **Ad**  
  
    **Adresi**  
  
    **Bu, bir sözcük temel Eylemler bölmesinde örneğidir.**  
  
   Ekleyebileceğiniz bir <xref:Microsoft.Office.Tools.Word.Bookmark> ondan sürükleyerek belgenize denetimi **araç kutusu** kullanarak veya Visual Studio'da **yer işareti** iletişim kutusundaki Word.  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize Bookmark denetimi eklemek için  
  
1.  Gelen **Word denetimleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize denetimi.  
  
     **Yer işareti Denetimi Ekle** iletişim kutusu görüntülenir.  
  
2.  Sözcük Seç **adı**olmadan paragraf işaretlerini seçerek ve tıklayın **Tamam**.  
  
    > [!NOTE]  
    >  Paragraf işaretlerini, yer işareti dışında olmalıdır. Paragraf işaretlerini belgede görünmüyorsa tıklayın **Araçları** menüsünde **Microsoft Office Word Araçları** ve ardından **seçenekleri**. Tıklayın **görünümü** sekmesine tıklayın ve **paragraf işaretleri** onay kutusuna **Biçimlendirme işaretleri** bölümünü **seçenekleri** iletişim kutusu.  
  
3.  İçinde **özellikleri** penceresinde değişiklik **adı** özelliği **Bookmark1** için **showName**.  
  
4.  Sözcük Seç **adresi**, paragraf işaretlerini seçmeden.  
  
5.  Üzerinde **Ekle** Şerit sekmesinde, **bağlantıları** grubunda **yer işareti**.  
  
6.  İçinde **yer işareti** iletişim kutusuna **showAddress** içinde **yer işareti adı** kutusuna ve tıklatın **Ekle**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetimler ekleme  
 Eylemler bölmesi arabirimini tasarlamak için projeye Eylemler bölmesi denetimi ekleyin ve ardından Windows Forms denetimleri için Eylemler bölmesi denetimi ekleyin.  
  
### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için  
  
1.  Seçin **My temel Actions Pane** projesi **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **Eylemler bölmesi denetimi**, denetimin adını **InsertTextControl'ü,** tıklatıp **Ekle**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Windows Form denetimi için Eylemler bölmesi denetimi eklemek için  
  
1.  Eylemler bölmesi denetimi Tasarımcısı'nda görünür değilse, çift **InsertTextControl'ü**.  
  
2.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **etiket** Eylemler bölmesi denetimi için denetim.  
  
3.  Değişiklik **metin** etiket denetiminin özelliği **adı**.  
  
4.  Ekleme bir **Textbox** denetlemek için Eylemler bölmesi denetimi ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**GetName**|  
    |**Boyutu**|**130, 20**|  
  
5.  İkinci bir ekleme **etiket** denetlemek için Eylemler bölmesi denetimi ve değiştirme **metin** özelliğini **adresi**.  
  
6.  İkinci bir ekleme **Textbox** denetlemek için Eylemler bölmesi denetimi ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**GetAddress**|  
    |**Return kabul eder**|**TRUE**|  
    |**Çok satırlı**|**TRUE**|  
    |**Boyutu**|**130, 40**|  
  
7.  Ekleme bir **düğmesi** denetlemek için Eylemler bölmesi denetimi ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**addText**|  
    |**Metin**|**Ekle**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>Belgeye metin eklemek için kod ekleyin  
 Eylemler bölmesinde metni metin kutularında uygun ekleyen bir kod yazma <xref:Microsoft.Office.Tools.Word.Bookmark> belgedeki denetimleri. Kullanabileceğiniz `Globals` eylemler bölmesindeki denetimlere denetimleri belgeye erişmek için sınıf. Daha fazla bilgi için [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Eylemler bölmesinde yer işaretinde belgedeki metin eklemek için  
  
1.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisine **addText** düğmesi.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  C# ' düğmesine tıklayarak bir olay işleyicisi eklemeniz gerekir. Bu kodu koyabilirsiniz `InsertTextControl` Oluşturucusu çağrısından sonra `InitializeComponent`. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için kod ekleyin  
 Show actions pane denetim koleksiyonu için oluşturduğunuz denetimi ekleyin.  
  
### <a name="to-show-the-actions-pane"></a>Eylemler bölmesinde göstermek için  
  
1.  Eylemler bölmesi denetimi içinde yeni bir örneğini oluşturma `ThisDocument` sınıfı.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Word.Document.Startup> olay işleyicisine `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Belgenizi Eylemler bölmesinde belge açılır ve metin kutularına yazılı metne düğmesine tıklandığında işaretlerine eklenir doğrulamak için test edin.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Eylemler bölmesi görünür olduğunu doğrulayın.  
  
3.  Metin kutularına eylemler bölmesindeki adınızı ve adresinizi yazın ve tıklayın **Ekle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Eylemler bölmesi Excel'de oluşturun. Daha fazla bilgi için [nasıl yapılır: Excel çalışma kitaplarına Eylemler bölmesi ekleme](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).  
  
-   Eylemler bölmesindeki denetimlere veri bağlama. Daha fazla bilgi için [izlenecek yol: Word eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Nasıl yapılır: Excel çalışma kitaplarına Eylemler bölmesi ekleme](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))   
 [Nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Yer işareti denetimi](../vsto/bookmark-control.md)  
  
  