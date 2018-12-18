---
title: 'İzlenecek Yol: Radyo Düğmelerini Kullanarak Çalışma Sayfasında Grafik Güncelleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aff631d8c9b6bd65b8ae91c5d936d2669764791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866447"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>İzlenecek Yol: Radyo Düğmelerini Kullanarak Çalışma Sayfasında Grafik Güncelleme
  Bu izlenecek yol, kullanıcı seçenekleri arasında kolayca geçiş yapmak için bir yol sağlamak için Microsoft Office Excel çalışma sayfasında radyo düğmeleri kullanmanın temellerini gösterir. Bu durumda, bir grafik stilini seçeneklerini değiştirin.  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 Sonuç tamamlanmış bir örnek görmek için Excel denetimleri örneğine bakın [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).  

 Bu izlenecek yol aşağıdaki görevleri gösterir:  

-   Radyo düğmelerinden oluşan bir grup çalışma sayfasına ekleme.  

-   Bir seçenek belirlendiğinde, grafik stilini değiştirme.  

> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  

## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  

## <a name="add-a-chart-to-a-worksheet"></a>Bir çalışma sayfasına bir grafik ekleyin  
 Mevcut bir çalışma kitabını özelleştirir bir Excel çalışma kitabı projesi oluşturabilirsiniz. Bu kılavuzda, bir çalışma kitabına bir grafik ekleyin ve ardından yeni bir Excel çözümde bu çalışma kitabını kullanın. Bu kılavuzda açıklanan veri kaynağı adlı bir çalışma sayfası, **grafiği için veri**.  

### <a name="to-add-the-data"></a>Veri eklemek için  

1. Microsoft Excel'de açın.  

2. Sağ **Sheet3** sekmesine ve ardından **Yeniden Adlandır** kısayol menüsünde.  

3. Sayfasına yeniden adlandır **grafiği için veri**.  

4. Aşağıdaki veriler ekleyin **grafiği için veri** hücre A4 olan ile üst sol köşe ve E8 sağ alt köşesindeki.  

   ||S1|S2|Q3|S4|  
   |-|--------|--------|--------|--------|  
   |Batı|500|550|550|600|  
   |Doğu|600|625|675|700|  
   |Kuzey|450|470|490|510|  
   |Güney|800|750|775|790|  

   Ardından, verileri görüntülemek için birinci çalışma sayfasına bir grafik ekleyin.  

### <a name="to-add-a-chart-in-excel"></a>Excel'de bir grafik eklemek için  

1.  Üzerinde **Ekle** sekmesinde **grafikleri** grubunda **sütun**ve ardından **tüm grafik türleri**.  

2.  İçinde **Grafik Ekle** iletişim kutusu, tıklayın **Tamam**.  

3.  Üzerinde **tasarım** sekmesinde **veri** grubunda **veri Seç**.  

4.  İçinde **veri kaynağı Seç** iletişim kutusu, tıklama **Chartdata aralığı** kutusuna ve herhangi bir varsayılan seçimi temizleyin.  

5.  İçinde **grafiği için veri** sayfasında, sol üst köşedeki E8 için sağ alt köşesindeki A4 içerir sayıları içeren olan hücre bloğu seçin.  

6.  İçinde **veri kaynağı Seç** iletişim kutusu, tıklayın **Tamam**.  

7.  Grafiğin sağ üst köşedeki hücre ile hizalanır. böylece yeniden konumlandırmak **E2**.  

8.  C sürücüsüne dosyanızı kaydedin ve adlandırın **ExcelChart.xlsx**.  

9. Excel'den çıkın.  

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 Bu adımda, temel bir Excel çalışma kitabı projesi oluşturacaksınız **ExcelChart** çalışma kitabı.  

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  

1.  Adlı bir Excel çalışma kitabı projesi oluşturun **My Excel grafik**. Sihirbazda **mevcut belgeyi kopyalamak**.  

     Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Tıklayın **Gözat** düğmesi ve bu kılavuzda daha önce oluşturulan çalışma kitabını göz atın.  

3.  **Tamam**'ı tıklatın.  

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **My Excel grafik** için proje **Çözüm Gezgini**.  

## <a name="set-properties-of-the-chart"></a>Grafiğin özelliklerini ayarlama  
 Mevcut bir çalışma kitabını kullanan yeni bir Excel çalışma kitabı projesi oluşturduğunuzda, konak denetimleri tüm adlandırılmış aralıklar, liste nesneleri ve çalışma kitabının grafikleri için otomatik olarak oluşturulur. Adını değiştirebilirsiniz <xref:Microsoft.Office.Tools.Excel.Chart> kullanarak denetim **özellikleri** penceresi.  

### <a name="to-change-the-name-of-the-chart-control"></a>Grafik denetimi adını değiştirmek için  

1.  Seçin <xref:Microsoft.Office.Tools.Excel.Chart> Denetim Tasarımcısı'nda ve şu özelliklerde değişiklik **özellikleri** penceresi.  

    |Özellik|Değer|  
    |--------------|-----------|  
    |**Ad**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>Denetimler ekleme  
 Bu çalışma, radyo düğmeleri kullanıcıların kolayca grafik stilini değiştirmek için bir yol sağlamak için kullanır. Ancak, radyo düğmeleri özel olması gerekir; bir düğme seçildiğinde diğer düğmesi grubunda aynı zamanda seçilebilir. Bir çalışma sayfasına birkaç radyo düğmeleri eklediğinizde, bu davranışı varsayılan olarak gerçekleşmez.  

 Bu davranışı bir kullanıcı denetimi radyo düğmelerini gruplandırma eklemenin bir yolu, kodunuzu kullanıcı denetimi arkasında yazın ve ardından çalışma sayfasına kullanıcı denetimi ekleyin.  

### <a name="to-add-a-user-control"></a>Bir kullanıcı denetimi eklemek için  

1.  Seçin **My Excel grafik** projesi **Çözüm Gezgini**.  

2.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  

3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **kullanıcı denetimi**, denetimin adını **ChartOptions** tıklatıp **Ekle**.  

### <a name="to-add-radio-buttons-to-the-user-control"></a>Kullanıcı denetimini radyo düğmeleri eklemek için  

1. Kullanıcı denetimi Tasarımcısı'nda görünür değilse, çift **ChartOptions** içinde **Çözüm Gezgini**.  

2. Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **radyo düğmesini** denetlemek için kullanıcı denetimi ve aşağıdaki özellikleri değiştirin.  


   | Özellik | Değer |
   |----------|------------------|
   | **Ad** | **columnChart** |
   | **Metin** | **Sütun grafiği** |


3. İkinci bir radyo düğmesi kullanıcı denetimine ekleyin ve aşağıdaki özellikleri değiştirin.  


   | Özellik | Değer |
   |----------|---------------|
   | **Ad** | **barChart** |
   | **Metin** | **Çubuk grafik** |


4. Kullanıcı denetimi için üçüncü bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.  


   | Özellik | Değer |
   |----------|----------------|
   | **Ad** | **lineChart** |
   | **Metin** | **Çizgi grafik** |


5. Kullanıcı denetimine dördüncü bir radyo düğmesi ekleyin ve aşağıdaki özellikleri değiştirin.  

   |Özellik|Değer|  
   |--------------|-----------|  
   |**Ad**|**areaBlockChart**|  
   |**Metin**|**Alan blok grafiği**|  

   Ardından, radyo düğmesine tıklandığında, grafik güncellemek için kod yazın.  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Bir radyo düğmesi seçildiğinde grafik stilini değiştirme  
 Artık grafik stilini değiştirmek için kod ekleyebilirsiniz. Bunu yapmak için ortak olay üzerinde kullanıcı denetimi oluşturun, seçim türünü ayarlamak için bir özellik ekleyin ve oluşturmak için bir olay işleyicisi `CheckedChanged` her radyo düğmelerinden oluşan olay.  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Bir olay ve özellik üzerinde bir kullanıcı denetimi oluşturmak için  

1.  İçinde **Çözüm Gezgini**kullanıcı denetimine sağ tıklayın ve ardından **kodu görüntüle**.  

2.  Kodu `ChartOptions` sınıfı oluşturmak için bir `SelectionChanged` olay ve `Selection` özelliği.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Radyo düğmelerinin CheckedChanged olayı işlemek için  

1.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `areaBlockChart` radyo düğmesini ve ardından olayı oluşturun.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `barChart` radyo düğmesi.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `columnChart` radyo düğmesi.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  Grafik türü kümesinde `CheckedChanged` olay işleyicisine `lineChart` radyo düğmesi.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  C# ' ta radyo düğmesi için olay işleyicileri eklemeniz gerekir. Kod ekleyebilirsiniz `ChartOptions` yapıcısına çağrısı `InitializeComponent`. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>Çalışma sayfasına kullanıcı denetimi Ekle  
 Çözüm derlediğinizde, yeni kullanıcı denetimi otomatik olarak eklenir **araç kutusu**. Ardından denetimi sürükleyebilir **araç kutusu** çalışma için.  

### <a name="to-add-the-user-control-your-worksheet"></a>Çalışma kullanıcı denetimi eklemek için  

1.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  

     **ChartOptions** kullanıcı denetimi eklenir **araç kutusu**.  

2.  İçinde **Çözüm Gezgini**, sağ **Sheet1.vb** veya **Sheet1.cs**ve ardından **Görünüm Tasarımcısı**.  

3.  Sürükleme **ChartOptions** denetimi **araç kutusu** çalışma.  

     Adlı yeni bir denetim `my_Excel_Chart_ChartOptions1` projenize eklenir.  

4.  Denetimin adını değiştirmek **ChartOptions1**.  

## <a name="change-the-chart-type"></a>Grafik türünü değiştir  
 Grafik türünü değiştirmek için kullanıcı denetimi seçeneğe göre stilini ayarlar bir olay işleyicisi oluşturun.  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Çalışma sayfasında görüntülenen grafik türünü değiştirmek için  

1.  Eklemek için aşağıdaki olay işleyicisini `Sheet1` sınıfı.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  C# içinde bir olay işleyicisi kullanıcı denetimi için eklemelisiniz <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> aşağıda gösterildiği gibi olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>Uygulamayı test etme  
 Artık bir radyo düğmesini seçtiğinizde grafik doğru biçimlendirilmiş doğrulamak için çalışma kitabınızı test edebilirsiniz.  

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  

1.  Tuşuna **F5** projeyi çalıştırın.  

2.  Çeşitli radyo düğmeleri seçin.  

3.  Grafik stilini seçimle eşleşecek şekilde değiştiğini doğrulayın.  

## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, radyo düğmeleri ve grafik stilleri çalışma sayfalarında kullanmanın temellerini gösterir. Sonraki gelebilir bazı görevler aşağıda verilmiştir:  

-   Projeyi dağıtma. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  

-   Bir düğmeye bir metin kutusunu doldurmak için kullanma. Daha fazla bilgi için [izlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  

-   Onay kutularını kullanarak çalışma sayfasındaki biçimlendirmeyi Değiştir. Daha fazla bilgi için [izlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  

## <a name="see-also"></a>Ayrıca bkz.  
 [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)  

