---
title: 'İzlenecek yol: içerik denetimlerini kullanarak şablon oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e597f13d2627a8b3e40aa65926d1c990be839c38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833193"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>İzlenecek yol: içerik denetimlerini kullanarak şablon oluşturma
  Bu yönerge, yapılandırılmış ve yeniden kullanılabilir içerik bir Microsoft Office Word şablonu oluşturmak için içerik denetimlerini kullanan bir belge düzeyi özelleştirmeyi oluşturma işlemini gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word yeniden kullanılabilir belge parçalarını adlı bir koleksiyon oluşturmanıza etkinleştirir *yapı taşlarını*. Bu izlenecek yol, yapı taşları olarak iki tablo oluşturma işlemi gösterilmektedir. Her tablo düz metin veya tarihleri gibi içerikleri farklı türde içerebileceği çeşitli içerik denetimlerini içerir. Tablolardan birinin bir çalışan hakkındaki bilgileri içerir ve diğer tablodaki müşteri geri bildirimlerini içerir.  
  
 Bir belge şablonu oluşturduktan sonra tablo ya da belgeye birkaç ekleyebilirsiniz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> nesneleri, şablonda kullanılabilir yapı taşlarını görüntüler.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- İçeriği içeren bir tablo oluşturma bir Word şablonu tasarım zamanında denetler.  
  
- Birleşik giriş kutusu içerik denetimi ve bir açılır liste içerik denetimi program aracılığıyla doldurma.  
  
- Kullanıcıların, belirtilen tablo düzenlemelerini engelleme.  
  
- Tablo, bir şablon yapı taşları koleksiyonuna ekleme.  
  
- Bir içerik denetimi oluşturma şablonda kullanılabilir yapı taşlarını görüntüler.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-template-project"></a>Yeni bir Word şablonu projesi oluşturma  
 Word şablonu oluşturun, böylece kullanıcılar kendi kopyalarını kolayca oluşturabilir.  
  
### <a name="to-create-a-new-word-template-project"></a>Yeni bir Word şablonu projesi oluşturmak için  
  
1.  Adlı bir Word şablonu projesi oluşturun **ne MyBuildingBlockTemplate**. Sihirbazda, çözümdeki bir yeni belge oluşturun. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Yeni bir Word şablonu Tasarımcısı'nda açılır ve ekler **ne MyBuildingBlockTemplate** için proje **Çözüm Gezgini**.  
  
## <a name="create-the-employee-table"></a>Çalışan tablosu oluşturma  
 Kullanıcı bir çalışan hakkındaki bilgileri girebileceğiniz içerik denetimleri dört farklı tür içeren bir tablo oluşturun.  
  
### <a name="to-create-the-employee-table"></a>Çalışan tablosu oluşturmak için  
  
1. Barındırılan Word şablonunda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Şeritteki tasarımcıya tıklayın **Ekle** sekmesi.  
  
2. İçinde **tabloları** grubunda **tablo**ve iki sütun ve dört satır içeren bir tablo ekleyin.  
  
3. Aşağıdaki sütun benzeyecek şekilde ilk sütunundaki metni yazın:  
  
   ||  
   |-|  
   |**Çalışan adı**|  
   |**İşe Alınma Tarihi**|  
   |**Başlık**|  
   |**resmi**|  
  
4. İkinci sütunda ilk hücreye tıklayın (yanındaki **çalışan adı**).  
  
5. Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
   > [!NOTE]  
   >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. İçinde **denetimleri** grubunda **metin** düğmesi ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>ilk hücreye.  
  
7. İkinci sütunda ikinci hücreyi tıklatın (yanındaki **işe giriş tarihi**).  
  
8. İçinde **denetimleri** grubunda **tarih seçici** düğmesi ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> ikinci hücreye.  
  
9. İkinci sütunda üçüncü hücrede tıklayın (yanındaki **başlık**).  
  
10. İçinde **denetimleri** grubunda **birleşik giriş kutusu** düğmesi ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>üçüncü hücreye.  
  
11. İkinci sütunda son hücreye tıklayın (yanındaki **resim**).  
  
12. İçinde **denetimleri** grubunda **resim içerik denetimi** düğmesi ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") eklemek için bir <xref:Microsoft.Office.Tools.Word.PictureContentControl> son hücreye.  
  
## <a name="create-the-customer-feedback-table"></a>Müşteri geri bildirim tablosu oluşturma  
 Üç farklı türde kullanıcı müşteri geri bildirim bilgileri girebileceğiniz içerik denetimlerini içeren bir tablo oluşturun.  
  
### <a name="to-create-the-customer-feedback-table"></a>Müşteri geri bildirim tablo oluşturmak için  
  
1. Word şablonu, daha önce eklediğiniz çalışan tablosunun satırı tıklatın ve basın **Enter** yeni bir paragrafa eklemek için.  
  
2. Şerit üzerinde tıklayın **Ekle** sekmesi.  
  
3. İçinde **tabloları** grubunda **tablo**ve iki ve üç satır içeren bir tablo ekleyin.  
  
4. Aşağıdaki sütun benzeyecek şekilde ilk sütunundaki metni yazın:  
  
   ||  
   |-|  
   |**Müşteri adı**|  
   |**Memnuniyet derecesi**|  
   |**Açıklamalar**|  
  
5. İkinci sütunda ilk hücreye tıklayın (yanındaki **müşteri adı**).  
  
6. Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
7. İçinde **denetimleri** grubunda **metin** düğmesi ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>ilk hücreye.  
  
8. İkinci sütunda ikinci hücresinde tıklayın (yanındaki **memnuniyeti derecelendirme**).  
  
9. İçinde **denetimleri** grubunda **açılır listede** düğmesi ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") eklemek için bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ikinci hücreye.  
  
10. İkinci sütunda son hücreye tıklayın (yanındaki **açıklamaları**).  
  
11. İçinde **denetimleri** grubunda **zengin metin** düğmesi ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") bir eklemekiçin<xref:Microsoft.Office.Tools.Word.RichTextContentControl>son hücreye.  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Birleşik giriş kutusu ve aşağı açılan liste program aracılığıyla doldurma  
 Tasarım zamanında içerik denetimlerini kullanarak başlatabilirsiniz **özellikleri** penceresinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bunları ilk durumlarına dinamik olarak ayarlamanıza olanak sağlayan çalışma zamanında da başlatabilirsiniz. Bu kılavuz için kodu girişleri doldurmak için kullanın. <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ve <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> çalışma zamanında görebilirsiniz, böylece bu nesnelerin nasıl.  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>İçerik denetimleri UI'ını program aracılığıyla değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisDocument.vb** veya **ThisDocument.vb**ve ardından **Kodu Görüntüle**.  
  
2.  Aşağıdaki kodu ekleyin `ThisDocument` sınıfı. Bu kod, bu kılavuzda daha sonra kullanacağınız birçok nesne bildirir.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı. Bu kod girişleri ekler <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ve <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> tablolar ve kümelerini kullanıcı önce bu denetimlerin her birinden görüntülenen yer tutucu metni bunları düzenler.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>Kullanıcılar çalışan tablonuzu düzenlemesini engelleyebilir.  
 Kullanım <xref:Microsoft.Office.Tools.Word.GroupContentControl> çalışan tablosunu korumak için daha önce bildirilen nesne. Kullanıcılar, tabloyu koruduktan sonra tabloda içerik denetimleri yine de düzenleyebilirsiniz. Ancak, bunlar ilk sütunundaki metni düzenleyemez veya tablo ekleme veya satırları ve sütunları silme gibi diğer yollarla değiştirin. Nasıl kullanılacağı hakkında daha fazla bilgi için bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> belgenin bir bölümünü korumak için bkz: [içerik denetimleri](../vsto/content-controls.md).  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>Kullanıcıların çalışan tablonuzu düzenlemesini önlemek için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı, önceki adımda eklediğiniz koddan sonra. Bu kod içinde tablo koyarak çalışan tablosunu düzenleme kullanıcıların engeller <xref:Microsoft.Office.Tools.Word.GroupContentControl> daha önce bildirilen nesne.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>Tabloları yapı taşı koleksiyona Ekle  
 Böylece kullanıcılar, belgeye oluşturmuş olduğunuz tablolar ekleyebilir tabloları belge derleme taşları şablondaki koleksiyonuna ekleyin. Belge derleme taşları hakkında daha fazla bilgi için bkz: [içerik denetimleri](../vsto/content-controls.md).  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Şablon yapı taşları tabloları eklemek için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı, önceki adımda eklediğiniz koddan sonra. Bu kod, şablonu yeniden kullanılabilir tüm yapı taşlarını içeren Microsoft.Office.Interop.Word.BuildingBlockEntries koleksiyonuna tabloları içeren yeni yapı taşları ekler. Yeni yapı taşları adlı yeni bir kategoride tanımlanan **çalışan ve müşteri bilgilerinin** ve yapı taşı türüne atanan `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı, önceki adımda eklediğiniz koddan sonra. Bu kod, şablondan tabloları siler. Tablolar, artık yeniden kullanılabilir şablon yapı taşları Galerisine eklediğiniz için gereklidir. Böylece korunan çalışan tablosunun silinebilir kod, ilk belge tasarım moduna geçirir.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Yapı taşlarını görüntüler bir içerik denetimi oluşturma  
 Daha önce oluşturulan yapı taşlarını (tablolar) erişim sağlayan bir içerik denetimi oluşturun. Kullanıcılar, belgeye tabloları eklemek için bu denetime tıklayabilirsiniz.  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Yapı taşlarını görüntüler bir içerik denetimi oluşturmak için  
  
1.  Aşağıdaki kodu ekleyin `ThisDocument_Startup` yöntemi `ThisDocument` sınıfı, önceki adımda eklediğiniz koddan sonra. Bu kod başlatır <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> daha önce bildirilen nesne. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Kategoride tanımlanan tüm yapı taşlarını görüntüler **çalışan ve müşteri bilgilerinin** ve Yapı bloğu türü `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>Test projesi  
 Kullanıcılar, belge çalışan veya müşteri geri bildirim tablosunda eklemek için Yapı Taşı Galerisi denetimlerinde tıklayabilirsiniz. Kullanıcılar, yazın veya içerik denetimleri tabloların hem de yanıtlar seçin. Kullanıcılar, müşteri geri bildirim tablo diğer bölümlerini değiştirebilir, ancak bunlar çalışan tablosunu diğer bölümlerini değiştirebilir olmamalıdır.  
  
### <a name="to-test-the-employee-table"></a>Çalışan tablonuzu test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Tıklayın **, ilk Yapı bloğu seçmek** ilk Yapı Taşı Galerisi içerik denetimi görüntülenecek.  
  
3.  Aşağı açılan oku tıklatın **Özel Galeri 1** denetimi başlık ve seçin **çalışan tablonuzu**.  
  
4.  Sağındaki hücreyi tıklatın **çalışan adı** hücre ve bir ad yazın.  
  
     Bu hücreye yalnızca metin ekleyebilirsiniz doğrulayın. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> Yalnızca metin, resim veya bir tablo gibi içerik olmayan diğer türleri eklemek kullanıcıların sağlar.  
  
5.  Sağındaki hücreyi tıklatın **işe giriş tarihi** hücre ve bir tarih tarih seçiciden seçin.  
  
6.  Sağındaki hücreyi tıklatın **başlık** hücre ve birleşik giriş kutusuna iş başlıklarından birini seçin.  
  
     İsteğe bağlı olarak, listede olmayan bir iş unvanı adını yazın. Bu mümkün olur çünkü <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> girişleri listesinden seçin veya kendi girişler yazmak için kullanıcıların sağlar.  
  
7.  Simgesini sağındaki hücrede **resim** hücre ve görüntülemek için bir görüntü için göz atın.  
  
8.  Satırlar veya sütunlar tabloya eklenecek deneyin ve satırları ve sütunları tablodan silmeyi deneyin. Tabloyu değiştiremezsiniz doğrulayın. <xref:Microsoft.Office.Tools.Word.GroupContentControl> Herhangi bir değişiklik yapmanızı önler.  
  
### <a name="to-test-the-customer-feedback-table"></a>Müşteri geri bildirim tablo test etmek için  
  
1.  Tıklayın **seçin, ikinci bir yapı taşı** ikinci Yapı Taşı Galerisi içerik denetimi görüntülenecek.  
  
2.  Aşağı açılan oku tıklatın **Özel Galeri 1** denetimi başlık ve seçin **müşteri tablosu**.  
  
3.  Sağındaki hücreyi tıklatın **müşteri adı** hücre ve bir ad yazın.  
  
4.  Sağındaki hücreyi tıklatın **memnuniyeti derecelendirme** hücre ve kullanılabilir seçeneklerden birini belirleyin.  
  
     Kendi giriş yazamazsınız doğrulayın. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Kullanıcıların yalnızca bir girdi listesinden seçmesine izin verir.  
  
5.  Sağındaki hücreyi tıklatın **açıklamaları** hücre ve bir açıklama yazın.  
  
     İsteğe bağlı olarak, metin, resim veya katıştırılmış bir tablo gibi dışındaki bazı içerik ekleyin. Bu mümkün olur çünkü <xref:Microsoft.Office.Tools.Word.RichTextContentControl> kullanıcıların metin dışında içerik eklemesine olanak sağlar.  
  
6.  Tabloya satır veya sütun ekleyebilir ve tablodan satırları ve sütunları silebilirsiniz doğrulayın. Bu olasıdır, tablonun koyarak koruduğu değil çünkü bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Şablon kapatın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu konu başlığından içerik denetimleri kullanma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   İçerik denetimleri, bir belgeye ekli özel XML parçaları olarak da adlandırılan, XML parçalarının bağlayın. Daha fazla bilgi için [izlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [İçerik denetimleri](../vsto/content-controls.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  