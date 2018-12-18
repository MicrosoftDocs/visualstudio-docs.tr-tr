---
title: Eylemler bölmesine genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8c7136c1f97f531600799f3aede30170813cf0a
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305682"
---
# <a name="actions-pane-overview"></a>Eylemler bölmesine genel bakış
  Eylemler bölmesi bir özelleştirilebilirdir **belge eylemleri** görev bölmesi, belirli Microsoft Office Word belgesi ya da Microsoft Office Excel çalışma kitabına eklenmiş. Eylemler bölmesinde içindeki diğer yerleşik görev bölmeleri yanı sıra Office görev bölmesi gibi barındırılan **XML kaynağı** görev bölmesinde Excel veya **stilleri ve biçimlendirme** Word görev bölmesinde. Windows Forms veya WPF denetimleri, Eylemler bölmesi kullanıcı arabirimini tasarlamak için kullanabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Word veya Excel için belge düzeyi özelleştirmesinde yalnızca eylemler bölmesi oluşturabilirsiniz. VSTO eklentisi içinde eylemler bölmesi oluşturamazsınız. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  Eylemler bölmesinde özel görev bölmeleri farklıdır. Özel görev bölmeleri, uygulama, belirli bir belge ile ilişkilidir. Özel görev bölmeleri VSTO eklentileri için bazı Microsoft Office uygulamaları oluşturabilirsiniz. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md).  

 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [bunu nasıl yaparım kullanım WPF denetimleri Excel eylemler bölmesindeki içinde?](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Eylemler bölmesini görüntüle  
 Eylemler bölmesi tarafından temsil edilen <xref:Microsoft.Office.Tools.ActionsPane> sınıfı. Bir belge düzeyi projesi oluşturduğunuzda, bu sınıfın bir örneği kullanılarak kodunuza kullanılabilir `ActionsPane` alanını `ThisWorkbook` (Excel için) veya `ThisDocument` (Word için) projenizde sınıf. Eylemler bölmesini görüntülemek için bir Windows Forms denetimine ekleme <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği `ActionsPane` alan. Aşağıdaki kod örneğinde adlı bir denetim ekler `actions` Eylemler bölmesine.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 Açıkça bir denetimi için ekledikten hemen sonra Eylemler bölmesinde çalışma zamanında görünür hale gelir. Eylemler bölmesinde görüntülendikten sonra dinamik olarak ekleyebilir veya kullanıcının eylemleri için yanıt denetimlerini kaldırma. Eylemler bölmesinde görüntülenecek kod genellikle, eklediğiniz `Startup` olay işleyicisine `ThisDocument` veya `ThisWorkbook` Eylemler bölmesi görünür olması kullanıcı ilk kez açıldığında belgenin. Ancak, yalnızca bir kullanıcının eylemi belgedeki yanıtta eylemler bölmesini görüntülemek isteyebilirsiniz. Örneğin, koda ekleyebilirsiniz `Click` belge üzerindeki bir denetimin olay.  

### <a name="add-multiple-controls-to-the-actions-pane"></a>Eylemler bölmesi için birden çok denetim ekleme  
 Eylemler bölmesine birden çok denetim eklediğinizde, denetimleri bir kullanıcı denetiminde grup ve ardından kullanıcı denetimine ekleyin <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliği. Bu işlem, aşağıdaki adımları içerir:  

1. Ekleyerek Eylemler bölmesinin kullanıcı arabirimi (UI) oluşturma bir **Eylemler bölmesi denetimi** veya **kullanıcı denetimi** projenize öğesi. Bu öğelerinin her ikisini de içeren özel bir Windows Forms <xref:System.Windows.Forms.UserControl> sınıfı. **Eylemler bölmesi denetimi** ve **kullanıcı denetimi** öğeleri eşdeğer; tek fark, adıdır.  

2. Windows Forms denetimlerine ekleme <xref:System.Windows.Forms.UserControl> Tasarımcısını kullanarak ya da kod yazarak.  

   > [!NOTE]  
   >  Bir WPF ekleyerek Eylemler bölmesi WPF denetimleri ekleyebilirsiniz <xref:System.Windows.Controls.UserControl> Windows Forms'a <xref:System.Windows.Forms.UserControl>. Daha fazla bilgi için [kullanım WPF denetimleri Office çözümlerinde](../vsto/using-wpf-controls-in-office-solutions.md).  

3. Özel kullanıcı denetimi örneğini bulunan denetimler ekleyin `ActionsPane` alanını `ThisWorkbook` (Excel için) veya `ThisDocument` (Word için) projenizde sınıf.  

   Bu işlem daha ayrıntılı bir şekilde gösteren örnekler için bkz. [nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hide-the-actions-pane"></a>Eylemler Bölmesini Gizle  
 Ancak <xref:Microsoft.Office.Tools.ActionsPane> sınıfında bir <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi ve bir <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliği kaldıramazsınız Eylemler bölmesinde kullanıcı arabiriminden tüm üyeleri kullanarak <xref:Microsoft.Office.Tools.ActionsPane> sınıfının kendisini. Çağırma <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi veya ayarı <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliğini **false** yalnızca eylemler bölmesindeki; denetimleri gizler görev bölmesinde gizlemez.  

 Çözümünüzü görev bölmesinde gizlemek için birkaç seçeneğiniz vardır:  

-   Word'ü için ayarlama <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> özelliği <xref:Microsoft.Office.Interop.Word.TaskPane> belge eylemler bölmesindeki temsil eden nesne **false**. Aşağıdaki kod örneği çalışmak üzere tasarlanmıştır `ThisDocument` projenizdeki sınıfı.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Excel için ayarlanan <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> özelliği <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> nesnesini **false**. Aşağıdaki kod örneği çalışmak üzere tasarlanmıştır `ThisWorkbook` projenizdeki sınıfı.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Word veya Excel için alternatif olarak ayarlayabilirsiniz <xref:Microsoft.Office.Core.CommandBar.Visible%2A> özelliğini temsil eden görev bölmesine komut çubuğunun **false**. Aşağıdaki kod örneği çalışmak üzere tasarlanmıştır `ThisDocument` veya `ThisWorkbook` projenizdeki sınıfı.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Belge açıldığında, Eylemler bölmesinde Temizle  
 Eylemler bölmesi görünür durumda durumdayken bir kullanıcı belgesini kaydettiğinde, Eylemler bölmesinde içeren herhangi bir denetim olup olmadığını her belge açıldığında eylemler bölmesi görünür durumda. Göründüğünde denetlemek istiyorsanız, çağrı <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> yöntemi `ActionsPane` alanındaki `Startup` olay işleyicisine `ThisDocument` veya `ThisWorkbook` belge açıldığında, Eylemler bölmesi görünür olmamasını sağlamak için.  

### <a name="determine-when-the-actions-pane-is-closed"></a>Eylemler bölmesinde kapatıldığında belirleme  
 Eylemler bölmesinde kapalı olduğunda hiçbir olay yok. Ancak <xref:Microsoft.Office.Tools.ActionsPane> sınıfında bir <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> olayı, bu olayın son kullanıcının Eylemler bölmesi kapandığında oluşmaz. Eylemler bölmesindeki denetimlere çağrılarak gizlendiğinde bunun yerine, bu olay tetiklenir <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi veya ayarlayarak <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliğini **false**.  

 Kullanıcının Eylemler bölmesi kapattığında, kullanıcı yeniden uygulamanın kullanıcı arabiriminde (UI) aşağıdaki yordamlardan birini gerçekleştirerek görüntüleyebilirsiniz.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Excel ve Word kullanıcı arabirimini kullanarak eylemler bölmesini görüntülemek için  

1.  Şerit üzerinde tıklayın **görünümü** sekmesi.  

2.  İçinde **Göster/Gizle** grubunda **belge eylemleri** iki durumlu düğme.  

## <a name="program-actions-pane-events"></a>Program Eylemler bölmesinde olayları  
 Eylemler bölmesine birden çok kullanıcı denetimi ekleyin ve ardından gösteren ve kullanıcı denetimleri gizleyerek belge olaylarına yanıt için kod yazma. XML Şeması öğelerini belgenize eşlerseniz, ekleme noktasını bir XML öğeleri içinde olduğunda, belirli kullanıcı denetimleri Eylemler bölmesinde gösterebilirsiniz. Daha fazla bilgi için [nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleştirme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) ve [nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarıyla eşleştirme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Konak denetimi, uygulama veya belge olaylarını dahil olmak üzere herhangi bir nesnenin olaylara yanıt vermek amacıyla kod da yazabilirsiniz. Daha fazla bilgi için [izlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Eylemler bölmesindeki denetimlere veri bağlama  
 Eylemler bölmesindeki denetimlere Windows Forms'da denetimleri aynı veri bağlama özellikleri vardır. Denetimler, veri kümeleri, yazılan veri kümeleri ve XML gibi veri kaynaklarına bağlayabilirsiniz. Daha fazla bilgi için [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Aynı veri kümesine eylemler bölmesindeki denetimlere ve belge denetimlere bağlayabilirsiniz. Örneğin, bir ana/ayrıntı ilişkisi arasında eylemler bölmesindeki denetimlere ve çalışma sayfasındaki denetimleri oluşturabilirsiniz. Daha fazla bilgi için [izlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validate-data-in-actions-pane-controls"></a>Eylemler bölmesinde denetimlerinde verileri doğrulama  
 Bir ileti kutusu görüntülerseniz, <xref:System.Windows.Forms.Control.Validating> Eylemler bölmesinde, olay üzerindeki bir denetimin olay işleyicisi, odağı denetimden ileti kutusu için ikinci bir kez yükseltilebilir. Bu sorunu önlemek için bir <xref:System.Windows.Forms.ErrorProvider> denetiminin tüm doğrulama hatası iletilerini görüntüler.  

## <a name="user-control-stacking-order"></a>Kullanıcı denetimi sıralaması  
 Birden çok kullanıcı denetimleri kullanıyorsanız, yatay veya dikey olarak yerleştirilmiş olup olmadığını eylemler bölmesindeki kullanıcı denetimleri düzgün yığın için kod yazabilirsiniz. Kullanıcı denetimleri eylemler bölmesindeki yığınlama sırasını kullanarak ayarlayabilirsiniz <xref:Microsoft.Office.Tools.StackStyle> numaralandırması <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> özelliği. Daha fazla bilgi için [nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Özelliği aşağıdaki gerçekleştirebileceğiniz <xref:Microsoft.Office.Tools.StackStyle> sabit listesi değerleri.  

|Yığın stili|Tanım|  
|--------------------|----------------|  
|FromBottom|Eylemler bölmesinin alt yığın.|  
|FromLeft|Eylemler bölmesinde soldan yığın.|  
|FromRight|Eylemler bölmesinde sağdan yığılır.|  
|FromTop|Eylemler bölmesinin üst kısmından yığın.|  
|Yok.|Yığın sıralaması tanımlanan; Sipariş geliştirici tarafından kontrol edilir.|  

 Aşağıdaki kod kümeleri <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Eylemler bölmesinin üst kullanıcı denetimleri yığın özelliği.  

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  

## <a name="anchor-controls"></a>Bağlantı denetimleri  
 Kullanıcının çalışma zamanında eylemler bölmesinde yeniden boyutlandırırsa, denetimleri ile Eylemler bölmesinde yeniden boyutlandırabilirsiniz. Kullanabileceğiniz <xref:System.Windows.Forms.Control.Anchor%2A> eylemler bölmesindeki denetimlere bağlantı için bir Windows Forms denetiminin özelliği. Ayrıca, aynı biçimde kullanıcı denetimini Windows Forms denetimlerini kenarına bağlanabilir. Daha fazla bilgi için [nasıl yapılır: Windows formlarında denetimleri sabitleme](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resize-the-actions-pane"></a>Eylemler bölmesinde yeniden boyutlandırma  
 Doğrudan boyutunu değiştiremezsiniz bir <xref:Microsoft.Office.Tools.ActionsPane> çünkü <xref:Microsoft.Office.Tools.ActionsPane> görev bölmesinde katıştırılır. Ancak, program aracılığıyla görev bölmesinde genişliğini ayarlayarak değiştirebilirsiniz <xref:Microsoft.Office.Core.CommandBar.Width%2A> özelliği <xref:Microsoft.Office.Core.CommandBar> temsil eden görev bölmesinde. Yatay olarak yerleştirildiğini veya kayan olan görev bölmesinde yüksekliğini değiştirebilirsiniz.  

 Kullanıcı kendi gereksinimlerine en uygun görev bölmesinde boyutunu seçebilir olmalıdır çünkü görev bölmesinde programlı olarak yeniden boyutlandırma önerilmez. Ancak, görev bölmesinde genişliğini yeniden boyutlandırmanız gerekir, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="reposition-the-actions-pane"></a>Eylemler bölmesinde yeniden konumlandırma  
 Doğrudan konumunu değiştiremezler <xref:Microsoft.Office.Tools.ActionsPane> çünkü görev bölmesinde gömülüdür. Ancak, program aracılığıyla görev bölmesinde ayarlayarak taşıyabilirsiniz <xref:Microsoft.Office.Core.CommandBar.Position%2A> özelliği <xref:Microsoft.Office.Core.CommandBar> temsil eden görev bölmesinde.  

 Kullanıcının kendi gereksinimlerine en uygun ekrandaki görev bölmesinde konumunu seçmek mümkün olması gerektiğinden programlı olarak görev bölmesinde yeniden konumlandırma önerilmez. Görev bölmesi, belirli bir konuma taşımanız gerekirse, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Son kullanıcılar, herhangi bir zamanda görev bölmesinde elle konumlandırabilirsiniz. Görev bölmesi programlı olarak belirttiğiniz konumda yerleşik kalacağından emin olmanın bir yolu yoktur. Ancak, yönlendirme değişiklikleri denetlemek ve Eylemler bölmesindeki denetimlere doğru yönde Yığılmış emin olun. Daha fazla bilgi için [nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Ayarı <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> ve <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> özelliklerini <xref:Microsoft.Office.Tools.ActionsPane> çünkü konumunu değiştirmez <xref:Microsoft.Office.Tools.ActionsPane> görev bölmesinde katıştırılmış nesne.  

 Görev bölmesi sabitlenmemişse ayarlayabileceğiniz <xref:Microsoft.Office.Core.CommandBar.Top%2A> ve <xref:Microsoft.Office.Core.CommandBar.Left%2A> özelliklerini <xref:Microsoft.Office.Core.CommandBar> temsil eden görev bölmesinde. Aşağıdaki kod bir yerleştirilmemiş görev bölmesinde belgenin sol üst köşesine taşır.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md)   
 [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [İzlenecek yol: Word eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Nasıl yapılır: denetim Eylemler bölmelerindeki Düzen yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
