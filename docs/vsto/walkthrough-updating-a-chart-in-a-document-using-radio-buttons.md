---
title: 'İzlenecek yol: radyo düğmelerini kullanarak belgede grafik güncelleştir'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e82c50c83a8824b4570779034b0480aa0615a30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904680"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>İzlenecek yol: radyo düğmelerini kullanarak belgede grafik güncelleştir
  Bu yönerge, radyo düğmeleri Microsoft Office Word için belge düzeyi özelleştirmesinde kullanıcıların belgeye grafik türlerini seçmek için seçenek sunmak için nasıl kullanılacağını gösterir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Grafik tasarım zamanında bir belge düzeyinde projedeki belge ekleme.  
  
- Bir kullanıcı denetimine ekleyerek radyo düğmelerini gruplandırma.  
  
- Bir seçenek belirlendiğinde, grafik stilini değiştirme.  
  
  Sonuç tamamlanmış bir örnek görmek için Word denetimleri örneğine bakın [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 İlk adım, bir Word belgesi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adıyla bir Word belgesi projesi oluşturma **My grafik seçenekleri**. Sihirbazda **yeni belge oluşturma**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Word belgesi açar ve ekler **My grafik seçenekleri** için proje **Çözüm Gezgini**.  
  
## <a name="add-a-chart-to-the-document"></a>Bir grafik belgesine Ekle  
  
### <a name="to-add-a-chart"></a>Bir grafik eklemek için  
  
1.  Visual Studio tasarımcıda Şerit üzerinde barındırılan bir Word belgesinde tıklatın **Ekle** sekmesi.  
  
2.  İçinde **metin** grubunda **Nesne Ekle** açılan düğmeyi seçeneğine tıklayıp **nesne**.  
  
     **Nesne** iletişim kutusu açılır.  
  
3.  İçinde **nesne türü** listesini **Yeni Oluştur** sekmesinde **Microsoft Graph grafiği** ve ardından **Tamam**.  
  
     Grafik ekleme noktasından belgeye eklenir ve **veri** bazı varsayılan verilerle penceresi görüntülenir.  
  
4.  Kapat **veri** penceresini grafik varsayılan değerleri kabul edin ve grafikten odağı taşımak için belgenin içine tıklayın.  
  
5.  Grafiği sağ tıklayın ve ardından **biçimi nesne**.  
  
6.  Üzerinde **Düzen** sekmesinde **biçimi nesne** iletişim kutusunda **kare** tıklatıp **Tamam**.  
  
## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle  
 Bir belge radyo düğmeleri, varsayılan olarak birbirini dışlamaz. Bunları doğru bunları bir kullanıcı denetimine ekleyerek ve ardından seçimi denetlemek için kod yazma işlev yapabilirsiniz.  
  
### <a name="to-add-a-user-control"></a>Bir kullanıcı denetimi eklemek için  
  
1.  Seçin **My grafik seçenekleri** projesi **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **kullanıcı denetimi**, denetimin adını **ChartOptions** tıklatıp **Ekle**.  
  
### <a name="to-add-windows-form-controls-to-the-user-control"></a>Windows Form denetimi için kullanıcı denetimi eklemek için  
  
1.  Kullanıcı denetimi Tasarımcısı'nda görünür değilse, çift **ChartOptions** içinde **Çözüm Gezgini**.  
  
2.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, ilk sürükleyin **radyo düğmesini** denetlemek için kullanıcı denetimi ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**columnChart**|  
    |**Metin**|**Sütun grafiği**|  
  
3.  İkinci bir ekleme **radyo düğmesini** kullanıcı Denetim ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**barChart**|  
    |**Metin**|**Çubuk grafik**|  
  
4.  Üçüncü bir ekleme **radyo düğmesini** kullanıcı Denetim ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**lineChart**|  
    |**Metin**|**Çizgi grafik**|  
  
5.  Dördüncü ekleme **radyo düğmesini** kullanıcı Denetim ve aşağıdaki özellikleri değiştirin.  
  
    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**areaBlockChart**|  
    |**Metin**|**Alan blok grafiği**|  
  
## <a name="add-references"></a>Başvuruları Ekle  
 Grafik bir belgede kullanıcı denetimi erişmek için bir başvuru olmalıdır `Microsoft.Office.Interop.Graph` projenizdeki derleme.  
  
### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft.Office.Interop.Graph derlemesine bir başvuru eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
     **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **.NET** sekmesinde **Microsoft.Office.Interop.Graph** tıklatıp **Tamam**. Bütünleştirilmiş kod sürümü 14.0.0.0 seçin.  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Bir radyo düğmesi seçildiğinde grafik stilini değiştirme  
 Düzgün çalışması için ortak olay üzerinde kullanıcı denetimi oluşturun düğmeleri olmak için Seçim türünü ayarlamak için bir özellik ekleyin ve bir yordam için oluşturmak `CheckedChanged` her radyo düğmelerinden oluşan olay.  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>Bir olay ve özellik üzerinde bir kullanıcı denetimi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**kullanıcı denetimine sağ tıklayın ve ardından **kodu görüntüle**.  
  
2.  Ekleme kodu oluşturmak için bir `SelectionChanged` olay ve `Selection` özelliğini `ChartOptions` sınıfı.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Radyo düğmeleri CheckedChange olayını işlemek için  
  
1.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `areaBlockChart` radyo düğmesini ve ardından olayı oluşturun.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `barChart` radyo düğmesi.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `columnChart` radyo düğmesi.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `lineChart` radyo düğmesi.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  C# ' ta radyo düğmesi için olay işleyicileri eklemeniz gerekir. Kod ekleyebilirsiniz `ChartOptions` yapıcısına çağrısı `InitializeComponent`. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="add-the-user-control-to-the-document"></a>Belgede kullanıcı denetimi Ekle  
 Çözüm derlediğinizde, yeni kullanıcı denetimi otomatik olarak eklenir **araç kutusu**. Ardından denetimi sürükleyebilir **araç kutusu** belgenize.  
  
### <a name="to-add-the-user-control-your-document"></a>Belgenizi kullanıcı denetimi eklemek için  
  
1.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     **ChartOptions** kullanıcı denetimi eklenir **araç kutusu**.  
  
2.  İçinde **Çözüm Gezgini**, sağ **ThisDocument.vb** veya **ThisDocument.vb**ve ardından **Görünüm Tasarımcısı**.  
  
3.  Sürükleme `ChartOptions` denetimi **araç kutusu** belge.  
  
     İçinde **özellikleri** penceresi, belgeye eklediğiniz yeni denetim adı `ChartOptions1`.  
  
## <a name="change-the-chart-type"></a>Grafik türünü değiştir  
 Kullanıcı denetimi belirlediğiniz seçeneğe göre grafik türünü değiştirmek için bir olay işleyicisi oluşturun.  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Belge içinde görüntülenen grafik türünü değiştirmek için  
  
1.  Eklemek için aşağıdaki olay işleyicisini `ThisDocument` sınıfı.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  İçinde C#, bir olay işleyicisi kullanıcı denetimi için eklemelisiniz <xref:Microsoft.Office.Tools.Word.Document.Startup> olay.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık bir radyo düğmesini seçtiğinizde grafik stilini doğru bir şekilde güncelleştirildiğinden emin olmak belgeye test edebilirsiniz.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Çeşitli radyo düğmeleri seçin.  
  
3.  Grafik stilini seçimle eşleşecek şekilde değiştiğini doğrulayın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Sonraki gelebilir bazı görevler aşağıda verilmiştir:  
  
-   Bir düğmeye bir metin kutusunu doldurmak için kullanma. Daha fazla bilgi için [izlenecek yol: metin kutusunda düğme kullanarak bir belgede metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Bir birleşik giriş kutusundan bir stil seçerek biçimlendirme değiştirin. Daha fazla bilgi için [izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Word'ü kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office belgelerindeki Windows Forms denetimleri sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  