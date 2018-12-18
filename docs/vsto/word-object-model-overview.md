---
title: Word nesne modeline genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 75a5f8e79bbd6dd34b046cbff6d59844a977efb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878017"
---
# <a name="word-object-model-overview"></a>Word nesne modeline genel bakış
  Visual Studio'da Word çözümleri geliştirirken, Word nesne modeli ile etkileşim kurun. Bu nesne modeli sınıfları ve arabirimleri Word için birincil birlikte çalışma derlemesi olarak sağlanır ve tanımlanan oluşur <xref:Microsoft.Office.Interop.Word> ad alanı.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Bu konu, Word nesne modeli kısa bir genel bakış sağlar. Kaynaklar nerede edinebilirsiniz tüm Word nesne modeli hakkında daha fazla bilgi için bkz [Word nesne modeli belgeleri kullanın](#WordOMDocumentation).  
  
 Word nesne modeli, belirli görevlerin gerçekleştirilmesi için kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Belgelerle çalışma](../vsto/working-with-documents.md)  
  
-   [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)  
  
-   [Tablolarla çalışma](../vsto/working-with-tables.md)  
  
##  <a name="understanding"></a> Word nesne modelini anlama  
 Word nesneyi ile etkileşim sağlar. Kullanıcı arabirimi yakından takip eden bir hiyerarşide bu nesneleri düzenlenir. Hiyerarşisinin en üstünde olan <xref:Microsoft.Office.Interop.Word.Application> nesne. Bu nesne, Word'ün geçerli örneğini temsil eder. <xref:Microsoft.Office.Interop.Word.Application> Nesnesini içeren <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>, ve <xref:Microsoft.Office.Interop.Word.Range> nesneleri. Bu nesnelerin her biri, birçok yöntemleri ve ve nesne ile etkileşime için erişebileceği bir özelliği vardır.  
  
 Aşağıdaki çizimde, Word nesne modeli hiyerarşisinde bu nesneler bir görünümü gösterilir.  
  
 ![Word nesne modeli grafiği](../vsto/media/wrwordobjectmodel.gif "Word nesne modeli grafiği")  
  
 İlk bakışta çakıştırmayı nesneler görüntülenir. Örneğin, <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Interop.Word.Selection> nesnelerdir hem üyeleri <xref:Microsoft.Office.Interop.Word.Application> nesne, ancak <xref:Microsoft.Office.Interop.Word.Document> nesne değil de bir üyesi <xref:Microsoft.Office.Interop.Word.Selection> nesne. Hem <xref:Microsoft.Office.Interop.Word.Document> ve <xref:Microsoft.Office.Interop.Word.Selection> nesneleri içeren <xref:Microsoft.Office.Interop.Word.Bookmark> ve <xref:Microsoft.Office.Interop.Word.Range> nesneleri. Aynı nesne türünü erişebileceğiniz birden çok yolu olduğundan bir çakışma var. Örneğin, biçimi geçerli bir <xref:Microsoft.Office.Interop.Word.Range> object; ancak geçerli seçim, belirli bir paragrafı, bir bölümü veya tüm belgeyi aralığı erişmek isteyebilir.  
  
 Aşağıdaki bölümlerde, en üst düzey nesnelerin ve birbiriyle nasıl etkileşim kurduklarını kısaca açıklanmaktadır. Bu nesneler, aşağıdaki beş içerir:  
  
- Uygulama nesnesi  
  
- Belge nesnesi  
  
- Nesne Seçimi  
  
- Aralık nesnesi  
  
- Yer işareti  
  
  Word nesne modeli yanı sıra, Visual Studio'da Office projeleri sağlamak *konak öğelerini* ve *konak denetimlerini* Word nesne modelinde bazı nesneler genişletin. Konak denetimlerinin ve konak öğelerinin bunlar genişletmek Word nesneleri gibi davranırlar fakat aynı zamanda veri bağlama becerileri ve ek olaylar gibi ek işlevlere sahiptirler. Daha fazla bilgi için [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md) ve [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
### <a name="application-object"></a>Uygulama nesnesi  
 <xref:Microsoft.Office.Interop.Word.Application> Nesne Word uygulamasını temsil eder ve tüm diğer nesnelerin üst. Üyeleri, genellikle sözcük bir bütün olarak uygular. Word ortamını denetlemek için özellik ve yöntemlerini kullanabilirsiniz.  
  
 VSTO eklentisi projelerinde erişebileceğiniz <xref:Microsoft.Office.Interop.Word.Application> kullanarak nesne `Application` alanını `ThisAddIn` sınıfı. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Belge düzeyinde projelerde erişebileceğiniz <xref:Microsoft.Office.Interop.Word.Application> kullanarak nesne <xref:Microsoft.Office.Tools.Word.Document.Application%2A> özelliği `ThisDocument` sınıfı.  
  
### <a name="document-object"></a>Belge nesnesi  
 <xref:Microsoft.Office.Interop.Word.Document> Nesnedir Word programlamasında. Bir belge ve tüm içeriğini temsil eder. Bir belgeyi açın veya yeni bir belge oluşturmak, yeni oluşturduğunuz <xref:Microsoft.Office.Interop.Word.Document> eklenen nesne <xref:Microsoft.Office.Interop.Word.Documents> koleksiyonunu <xref:Microsoft.Office.Interop.Word.Application> nesne. Odağı olan belgeyi etkin belgeyi çağrılır. Tarafından temsil edilen <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> özelliği <xref:Microsoft.Office.Interop.Word.Application> nesne.  
  
 Visual Studio'da Office geliştirme araçlarını genişletmek <xref:Microsoft.Office.Interop.Word.Document> sağlayarak nesne <xref:Microsoft.Office.Tools.Word.Document> türü. Bu tür bir *konak öğesi* tüm özelliklerine erişim sağlar bir <xref:Microsoft.Office.Interop.Word.Document> nesne ve ek olaylar ve yönetilen denetimleri ekleme özelliği ekler.  
  
 Bir belge düzeyi projesi oluşturduğunuzda, erişebileceğiniz <xref:Microsoft.Office.Tools.Word.Document> oluşturulan kullanarak üyeleri `ThisDocument` projenizdeki sınıfı. Üyeleri erişebilir <xref:Microsoft.Office.Tools.Word.Document> kullanarak ana öğe **bana** veya **bu** kodda sözcüklerden `ThisDocument` kullanarak veya sınıf `Globals.ThisDocument` dışındaki kod `ThisDocument` sınıf. Daha fazla bilgi için [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md). Örneğin, ilk paragrafa belgede seçmek için aşağıdaki kodu kullanın.  
  
 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]  
  
 VSTO eklentisi projelerinde oluşturabileceğiniz <xref:Microsoft.Office.Tools.Word.Document> öğelerinin çalışma zamanında barındırın. Oluşturulan konak öğesi, ilişkili belge için denetimler eklemek için kullanabilirsiniz. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="selection-object"></a>Nesne Seçimi  
 <xref:Microsoft.Office.Interop.Word.Selection> Nesnesi şu anda seçili olan alanın temsil eder. Word kullanıcı arabiriminde kalın metin gibi bir işlem gerçekleştirdiğinizde, seçin veya metni vurgulayın ve biçimlendirme uygulayın. <xref:Microsoft.Office.Interop.Word.Selection> Nesne varsa her zaman bir belgede. Daha sonra hiçbir şey seçili ise, ekleme noktasını temsil eder. Ayrıca, bir seçim bitişik olmayan birden çok metin blokları kapsayabilir.  
  
### <a name="range-object"></a>Aralık nesnesi  
 <xref:Microsoft.Office.Interop.Word.Range> Nesne belgedeki bitişik bir alanı temsil eder ve bir başlangıç karakteri konumunu ve bitiş karakter konumu tarafından tanımlanır. Tek bir sınırlı olmamak <xref:Microsoft.Office.Interop.Word.Range> nesne. Birden çok tanımlayabilirsiniz <xref:Microsoft.Office.Interop.Word.Range> nesneleri aynı belgedeki. A <xref:Microsoft.Office.Interop.Word.Range> nesnesi şu özelliklere sahiptir:  
  
- Tek başına ekleme noktasını, bir metin aralığını veya tüm belgeyi oluşabilir.  
  
- Yazdırılamayan karakterler boşluk, sekme karakterleri ve paragraf işaretlerini gibi içerir.  
  
- Geçerli seçim tarafından temsil edilen alan olabilir ya da geçerli seçim farklı bir alanı temsil edebilir.  
  
- Her zaman görünür durumda olan bir seçim aksine bir belgede görünür değil.  
  
- Bir belge ile kaydedilmez ve yalnızca kod çalışırken bulunmaktadır.  
  
  Bir aralığın sonunda metin eklediğinizde, sözcük otomatik olarak eklenen metni eklemek için aralığı genişletir.  
  
### <a name="content-control-objects"></a>İçerik denetimi nesneleri  
 A <xref:Microsoft.Office.Interop.Word.ContentControl> giriş ve sunu metin ve diğer Word belgelerinde içerik türlerini denetlemek bir yol sağlar. A <xref:Microsoft.Office.Interop.Word.ContentControl> Word belgelerinde zengin metin denetimi, bir tarih seçici veya birleşik giriş kutusu gibi kullanım için optimize edilmiş birçok farklı kullanıcı Arabirimi türlerini görüntüleyebilirsiniz. Ayrıca bir <xref:Microsoft.Office.Interop.Word.ContentControl> kullanıcıların belgenin veya şablonun bölümlerini düzenlemesini önlemek için.  
  
 Visual Studio genişletir <xref:Microsoft.Office.Interop.Word.ContentControl> nesnesine birden çok farklı bir konak denetimi. Oysa <xref:Microsoft.Office.Interop.Word.ContentControl> nesne türlerinden herhangi birini içerik denetimleri için kullanılabilen farklı UI görüntüleyebilir, Visual Studio İçerik her denetim için farklı bir tür sağlar. Örneğin, kullanabileceğiniz bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> veya zengin metin denetimi oluşturmak için kullanabileceğiniz bir <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> tarih seçici oluşturma. Bu konak denetimleri yerel gibi davranır <xref:Microsoft.Office.Interop.Word.ContentControl>, ancak ek olaylar ve veri bağlama becerileri gerekir. Daha fazla bilgi için [içerik denetimleri](../vsto/content-controls.md).  
  
### <a name="bookmark-object"></a>Yer işareti  
 <xref:Microsoft.Office.Interop.Word.Bookmark> Nesne bitişik bir alan belgede, başlangıç konumu hem bitiş konumu temsil eder. Bir konumu bir belge veya bir belgede metin için kapsayıcı olarak işaretlemek için yer işaretlerini kullanabilirsiniz. A <xref:Microsoft.Office.Interop.Word.Bookmark> nesne ekleme noktasını oluşur veya tüm belge büyüklüğünde olabilir. A <xref:Microsoft.Office.Interop.Word.Bookmark> apart buradan ayarlayın aşağıdaki özelliklere sahip <xref:Microsoft.Office.Interop.Word.Range> nesnesi:  
  
- Tasarım zamanında yer işaretinin adı verebilirsiniz.  
  
- <xref:Microsoft.Office.Interop.Word.Bookmark> nesneler, belge ile kaydedilir ve böylece kod çalışmadığında veya belge kapatıldığında silinmez.  
  
- Yer işaretleri gizli veya görünür hale ayarlayarak <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> özelliği <xref:Microsoft.Office.Interop.Word.View> nesnesini **false** veya **true**.  
  
  Visual Studio genişletir <xref:Microsoft.Office.Interop.Word.Bookmark> sağlayarak nesne <xref:Microsoft.Office.Tools.Word.Bookmark> konak kontrolü. <xref:Microsoft.Office.Tools.Word.Bookmark> Konak denetimi yerel gibi davranır <xref:Microsoft.Office.Interop.Word.Bookmark>, ancak ek olaylar ve veri bağlama özellikleri vardır. Aynı şekilde bir Windows formunda metin kutusu denetimi veri bağlamak için bir yer işareti denetimi belgesinde verileri bağlayabilirsiniz. Daha fazla bilgi için [yer işareti denetimi](../vsto/bookmark-control.md).  
  
##  <a name="WordOMDocumentation"></a> Word nesne modeli belgeleri kullanın  
 Word nesne modeli hakkında tam bilgi için sözcük birincil birlikte çalışma derlemesi (PIA) başvuru ve Visual Basic for Applications (VBA) nesne modeli başvurusu başvurabilirsiniz.  
  
### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma bütünleştirilmiş kod başvurusu  
 Word PIA başvuru belgeleri, Word için birincil birlikte çalışma derlemesi türlerini tanımlar. Bu belge aşağıdaki konumdan kullanılabilir: [Word 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Sınıfları ve arabirimleri arasındaki farkı PIA hem de PIA olayların nasıl uygulandığı, örneğin Word PIA tasarımı hakkında daha fazla bilgi için bkz: [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindekigenelbakış](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu  
 VBA koduna sunulur şekilde VBA nesne modeli başvurusu Word nesne modeli listelenmiştir. Daha fazla bilgi için [Word 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199772).  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türlerine ve üyelerine Word PIA karşılık gelir. Örneğin, belge nesnesi VBA nesne modeli başvurusu için karşılık gelen <xref:Microsoft.Office.Interop.Word.Document> Word PIA nesne. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da bu başvuru Visual Basic veya Visual VBA kodu çevir C# bunları Visual Studio kullanarak oluşturduğunuz bir Word projesinde kullanmak istiyorsanız .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Belgelerle çalışma](../vsto/working-with-documents.md)   
 [Belgelerde metinle çalışma](../vsto/working-with-text-in-documents.md)   
 [Tablolarla çalışma](../vsto/working-with-tables.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  