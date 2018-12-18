---
title: 'İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff261fd6032f3c666dfa3d745508586ffede6504
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884088"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma
  Bu izlenecek yol için kısayol menüleri oluşturma işlemini gösterir <xref:Microsoft.Office.Tools.Word.Bookmark> Word için belge düzeyi özelleştirmesinde denetimleri. Kullanıcı yer işaretindeki metnin tıkladığında bir kısayol menü görünür ve metni biçimlendirmek için kullanıcı seçeneklerini sunar.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- [Projeyi oluşturmak](#BKMK_CreateProject).  
  
- [Belgeye metin ve yer işaretleri eklemek](#BKMK_addtextandbookmarks).  
  
- [Bir kısayol menüsüne komut ekleme](#BKMK_AddCmndsShortMenu).  
  
- [Yer işareti metni biçimlendirebilir](#BKMK_formattextbkmk).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Proje oluşturma  
 İlk adım, Visual Studio'da bir Word belgesi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
-   Bu ada sahip bir Word belgesi projesi oluşturma **My yer işareti kısayol menüsünü**. Sihirbazda **yeni belge oluşturma**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **My yer işareti kısayol menüsünü** için proje **Çözüm Gezgini**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Belgeye metin ve yer işaretlerini Ekle  
 Metin belgenize ekleyin ve ardından iki örtüşen yer işareti ekleyin.  
  
### <a name="to-add-text-to-your-document"></a>Belgeye metin ekleme  
  
-   Proje Tasarımcısı'nda görüntülenen belgede aşağıdaki metni yazın.  
  
     **Bu, yer işaretindeki metnin sağ tıklattığınızda, bir kısayol menü oluşturma bir örnektir.**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize Bookmark denetimi eklemek için  
  
1. İçinde **araç kutusu**, gelen **Word denetimleri** sekmesinde, sürükleyin bir <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize denetimi.  
  
    **Yer işareti Denetimi Ekle** iletişim kutusu görüntülenir.  
  
2. "Metnin sağ tıklattığınızda bir kısayol menü oluşturma" sözcükler seçin ve ardından **Tamam**.  
  
    `bookmark1` belgeye eklenir.  
  
3. Başka bir <xref:Microsoft.Office.Tools.Word.Bookmark> "yer işaretindeki metnin sağ" sözcükleri denetimi.  
  
    `bookmark2` belgeye eklenir.  
  
   > [!NOTE]  
   >  "Metnin sağ tıklayın", olan hem de sözcükler `bookmark1` ve `bookmark2`.  
  
   Tasarım zamanında, bir belge için bir yer işareti eklediğinizde bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetim oluşturulur. Yer işareti birkaç olaylarına karşı programlama yapabilirsiniz. Kod yazabileceğiniz <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> olay işaretinin kullanıcı yer imi metinde tıklattığında kısayol menüsü görüntülenir.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Bir kısayol menüsüne komut ekleme  
 Düğmeler, belge sağ tıkladığınızda görüntülenen kısayol menüsüne ekleyin.  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>Bir kısayol menüsüne komut eklemek için  
  
1.  Ekleme bir **Ribbon XML** projeye öğe. Daha fazla bilgi için [nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  İçinde **Çözüm Gezgini**seçin **ThisDocument.vb** veya **ThisDocument.vb**.  
  
3.  Menü çubuğunda, **görünümü** > **kod**.  
  
     **ThisDocument** sınıf dosyası Kod Düzenleyicisi'nde açılır.  
  
4.  Aşağıdaki kodu ekleyin **ThisDocument** sınıfı. Bu kod yöntemini geçersiz kılar ve Şerit XML sınıf Office uygulamasına döndürür.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  İçinde **Çözüm Gezgini**, Şerit XML dosyasını seçin. Varsayılan olarak, Ribbon XML dosyasındaki Ribbon1.xml olarak adlandırılır.  
  
6.  Menü çubuğunda, **görünümü** > **kod**.  
  
     Şerit xml dosyası Kod Düzenleyicisi'nde açılır.  
  
7.  Kod Düzenleyicisi'nde Şerit XML dosyasının içeriğini aşağıdaki kodla değiştirin.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Bu kod, iki düğme belge sağ tıkladığınızda görüntülenen kısayol menüsüne ekler.  
  
8.  İçinde **Çözüm Gezgini**, sağ `ThisDocument`ve ardından **kodu görüntüle**.  
  
9. Aşağıdaki değişkenleri ve sınıf düzeyinde yer işareti değişkenini bildirir.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. İçinde **Çözüm Gezgini**, Şerit kod dosyasını seçin. Varsayılan olarak, Şerit kod dosyasını adlı **Ribbon1.cs** veya **Ribbon1.vb**.  
  
11. Menü çubuğunda, **görünümü** > **kod**.  
  
     Kod Düzenleyicisi'nde Şerit kod dosyasını açar.  
  
12. Şerit kod dosyasında, aşağıdaki yöntemi ekleyin. Belgenin kısayol menüsüne eklediğiniz iki düğme için bir geri arama yöntemi budur. Bu yöntem, bu düğmeler kısayol menüsünde görünür olup olmadığını belirler. Yer işareti içinde metin yalnızca sağ tıklattığınızda, kalın ve italik düğmeleri görünür.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Yer işareti metni Biçimlendir  
  
### <a name="to-format-the-text-in-the-bookmark"></a>Yer işareti metni biçimlendirmek için  
  
1.  Şerit kod dosyasında, ekleme bir `ButtonClick` işaretine biçimlendirme uygulamak için olay işleyicisi.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **Çözüm Gezgini**seçin **ThisDocument.vb** veya **ThisDocument.vb**.  
  
3.  Menü çubuğunda, **görünümü** > **kod**.  
  
     **ThisDocument** sınıf dosyası Kod Düzenleyicisi'nde açılır.  
  
4.  Aşağıdaki kodu ekleyin **ThisDocument** sınıfı.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Yer işaretleri çakıştığı durumu işlemek için kod yazmanız gerekir. Varsayılan olarak, bunu değil, kod Seçimdeki tüm yer imlerini için çağrılır.  
  
5.  C# ' ta yer işareti denetimleri için olay işleyicileri eklemelisiniz <xref:Microsoft.Office.Tools.Word.Document.Startup> olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Belgenizi yer işaretindeki metnin sağ tıkladığınızda kalın ve italik menü öğelerini kısayol menüsünde görünür ve metni doğru şekilde yapılandırıldığını doğrulamak için test edin.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  İlk yer işaretinde sağ tıklayın ve ardından **kalın**.  
  
3.  Doğrulayın tüm metinde `bookmark1` kalın olarak biçimlendirilir.  
  
4.  Çakıştığı yer işaretleri, metnin sağ tıklayın ve ardından **italik**.  
  
5.  Doğrulayın tüm metinde `bookmark2` italik ve yalnızca metin parçası `bookmark1` çakışan `bookmark2` italik.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Excel'de ana bilgisayar denetim olaylarına tepki vermek için kod yazın. Daha fazla bilgi için [izlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Bir yer işaretine biçimlendirme değiştirmek için bir onay kutusunu kullanın. Daha fazla bilgi için [izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word'ü kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Yer işareti denetimi](../vsto/bookmark-control.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  