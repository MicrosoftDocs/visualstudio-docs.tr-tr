---
title: 'Nasıl yapılır: program aracılığıyla arama ve belgelerdeki metni değiştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6de96133a810898fe847cce71bb2711dd7c31dd9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822403"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Nasıl yapılır: program aracılığıyla arama ve belgelerdeki metni değiştirme
  <xref:Microsoft.Office.Interop.Word.Find> Nesnedir hem de bir üyesi <xref:Microsoft.Office.Interop.Word.Selection> ve <xref:Microsoft.Office.Interop.Word.Range> nesneleri ve bunlardan birini Microsoft Office Word belgelerinde metin aramak için kullanabilirsiniz. Replace komutu FIND komutu bir uzantısıdır.  
  
 Kullanan bir <xref:Microsoft.Office.Interop.Word.Find> Microsoft Office Word belgesi ve belirli bir metni, biçimlendirme ve stil Ara döngü nesnesini ve kullanmak <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> bulunan öğelerden herhangi birini değiştirmek için özellik.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-a-selection-object"></a>Bir seçim nesnesi kullanma  
 Kullandığınızda, bir <xref:Microsoft.Office.Interop.Word.Selection> metin seçili metin, belirttiğiniz ölçütlere göre yalnızca uygulanır herhangi bir arama şu anda bulunacak nesne. Varsa <xref:Microsoft.Office.Interop.Word.Selection> belge aranır sonra bir ekleme noktası ise. Arama ölçütleriyle eşleşen öğe bulunamadı, otomatik olarak seçilir.  
  
 Dikkat etmeniz önemlidir <xref:Microsoft.Office.Interop.Word.Find> ölçütlerdir birikimli ölçütleri önceki arama ölçütleri için eklenen anlamına gelir. Önceki aramalardan kullanarak biçimlendirmeyi Temizle <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> arama önce yöntemi.  
  
### <a name="to-find-text-using-a-selection-object"></a>Metin seçimi nesnesini kullanarak bulmak için  
  
1. Bir arama dizesi, bir değişkene atayın.  
  
    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2. Önceki aramalardan biçimlendirme temizleyin.  
  
    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3. Arama yürütmek ve sonuçları içeren bir ileti kutusu görüntüler.  
  
    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
   Aşağıdaki örnek, ayrıntılı bir yöntemi gösterir.  
  
   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="use-a-range-object"></a>Aralık nesnesi kullanma  
 Kullanarak bir <xref:Microsoft.Office.Interop.Word.Range> nesne hiçbir şey kullanıcı arabirimini görüntülemeden metin arama olanak sağlar. <xref:Microsoft.Office.Interop.Word.Find> Nesne döndürür **True** arama ölçütleri ile eşleşen metin bulunursa ve **False** Aksi takdirde. Ayrıca yeniden tanımladığı <xref:Microsoft.Office.Interop.Word.Range> metin bulunursa arama ölçütleriyle eşleşen nesne.  
  
### <a name="to-find-text-using-a-range-object"></a>Aralık nesnesi kullanarak metin bulmak için  
  
1. Tanımlayan bir <xref:Microsoft.Office.Interop.Word.Range> belge ikinci paragrafta içeren nesne.  
  
    Aşağıdaki kod örneği belge düzeyi özelleştirmesinde kullanılabilir.  
  
    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
    Aşağıdaki kod örneği, VSTO eklentisi içinde kullanılabilir. Bu örnek etkin belgeyi kullanır.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2. Kullanarak <xref:Microsoft.Office.Interop.Word.Range.Find%2A> özelliği <xref:Microsoft.Office.Interop.Word.Range> nesne, önce mevcut tüm biçimlendirme seçeneklerini temizleyin ve ardından arama dizesi için **bana Bul**.  
  
    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3. Bir ileti kutusu içinde arama sonuçlarını görüntülemek ve seçmek <xref:Microsoft.Office.Interop.Word.Range> görünür yapmak için.  
  
    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
    Arama başarısız olursa, ikinci paragraf seçilidir; başarılı olursa, arama ölçütlerini görüntülenir.  
  
   Aşağıdaki örnek, bir belge düzeyi özelleştirmesi için tam kod gösterilir. Bu örneği kullanmak için kodu çalıştırın `ThisDocument` projenizdeki sınıfı.  
  
   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
   Aşağıdaki örnek, VSTO eklentisi için tam kod gösterilmektedir. Bu örneği kullanmak için kodu çalıştırın `ThisAddIn` projenizdeki sınıfı.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="search-for-and-replace-text-in-documents"></a>Arama ve belgelerdeki metni değiştirme  
 Aşağıdaki kod, geçerli seçimi arar ve tüm dize oluşumlarını değiştirir **bana Bul** dizesiyle **bulunan**.  
  
### <a name="to-search-for-and-replace-text-in-documents"></a>İçin arama yapın ve belgelerdeki metni değiştirme  
  
1.  Aşağıdaki örnek kodu `ThisDocument` veya `ThisAddIn` projenizdeki sınıfı.  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> Sınıfında bir <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> yöntemi ve <xref:Microsoft.Office.Interop.Word.Replacement> ayrıca sınıfında kendi <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> yöntemi. Bul ve Değiştir işlemleri gerçekleştirirken her iki nesnenin ClearFormatting yöntemi kullanmanız gerekir. Yalnızca kullanırsanız <xref:Microsoft.Office.Interop.Word.Find> nesnesini değiştirme metni beklenmedik sonuçlar alabilirsiniz.  
  
2.  Kullanım <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> yöntemi <xref:Microsoft.Office.Interop.Word.Find> bulunan her öğenin değiştirilecek nesne. Değiştirilecek öğeleri belirtmek için kullanın *değiştirin* parametresi. Bu parametre aşağıdaki değerlerden biri olabilir <xref:Microsoft.Office.Interop.Word.WdReplace> değerleri:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> tüm öğeleri değiştirir.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> bulunan öğelerin hiçbiri değiştirir.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> bulunan ilk öğeyi değiştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Nasıl yapılır: program aracılığıyla bulunan öğeler arasında döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla tanımlama ve belgelerde aralıkları seçin](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Nasıl yapılır: program aracılığıyla aramalardan sonra seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  