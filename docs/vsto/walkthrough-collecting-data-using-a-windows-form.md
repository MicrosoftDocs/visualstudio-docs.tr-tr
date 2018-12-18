---
title: 'İzlenecek yol: bir Windows formu kullanarak veri toplama'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d48f2a104505e6b6ea9942847d8cd4dd2f3e669
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900481"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>İzlenecek yol: bir Windows formu kullanarak veri toplayabilir.
  Bu izlenecek yol, bir Windows Form Microsoft Office Excel için belge düzeyi özelleştirmesinde açın, kullanıcıdan bilgi toplar ve bu bilgileri çalışma sayfası hücresine yazma gösterilmektedir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Excel için belge düzeyi projesi Bu izlenecek yolda özellikle kullansa da, diğer Office projeleri tarafından izlenecek yolda gösterilen kavramlar geçerlidir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 İlk adım, bir Excel çalışma kitabı projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **girdiWinFormu**seçip **yeni belge oluşturma** Sihirbazı'nda. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **girdiWinFormu** için proje **Çözüm Gezgini**.  
  
## <a name="add-a-namedrange-control-to-the-worksheet"></a>Çalışma sayfasına NamedRange Denetimi Ekle  
  
### <a name="to-add-a-named-range-to-sheet1"></a>Adlandırılmış aralık Sheet1 eklemek için  
  
1.  Hücresini seçin **A1** üzerinde `Sheet1`.  
  
2.  İçinde **adı** kutusuna **girdiFormu**.  
  
     **Adı** kutusudur sütun hemen üstündeki formül çubuğunun solunda bulunan **A** çalışma sayfası.  
  
3.  Tuşuna **girin**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi eklenir hücreye **A1**. Çalışma sayfasında görünür bir gösterge yoktur ancak **girdiFormu** görünür **adı** kutusu (yalnızca yukarıda çalışma sol tarafta) ve **özellikleri** penceresi zaman Hücre **A1** seçilir.  
  
## <a name="add-a-windows-form-to-the-project"></a>Projeye bir Windows formu Ekle  
 Kullanıcıdan bilgi istemek için bir Windows formu oluşturun.  
  
### <a name="to-add-a-windows-form"></a>Bir Windows formu eklemek için  
  
1. Projeyi seçin **girdiWinFormu** içinde **Çözüm Gezgini**.  
  
2. Üzerinde **proje** menüsünde tıklatın **Windows formu eklemek**.  
  
3. Form adı **GetInputString.vb** veya **GetInputString.cs olarak**ve ardından **Ekle**.  
  
    Yeni form Tasarımcısı'nda açılır.  
  
4. Ekleme bir <xref:System.Windows.Forms.TextBox> ve <xref:System.Windows.Forms.Button> form.  
  
5. Düğmeyi seçin, özelliğini bulun **metin** içinde **özellikleri** penceresinde metni değiştirip **Tamam**.  
  
   Ardından, kod ekleyin `ThisWorkbook.vb` veya `ThisWorkbook.cs` kullanıcının bilgilerini toplamak için.  
  
## <a name="display-the-windows-form-and-collecting-information"></a>Windows Form ve toplama bilgileri görüntüleme  
 Bir örneğini oluşturmak `GetInputString` Windows formu görüntülemek ve ardından çalışma sayfasındaki bir hücreye kullanıcının bilgileri yazın.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Görüntüleme formu ve bilgi toplamak için  
  
1. Sağ **ThisWorkbook.vb** veya **ThisWorkbook.cs** içinde **Çözüm Gezgini**ve ardından **Kodu Görüntüle**.  
  
2. İçinde <xref:Microsoft.Office.Tools.Excel.Workbook.Open> olay işleyicisine `ThisWorkbook`, form için bir değişken bildirmek için aşağıdaki kodu ekleyin `GetInputString` ve formu gösterin.  
  
   > [!NOTE]  
   >  C# içinde bir olay işleyicisi gösterildiği eklemelisiniz <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> aşağıdaki olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3. Adlı bir yöntem oluşturma `WriteStringToCell` , adlandırılmış bir aralığa metin yazar. Bu yöntem formdan olarak adlandırılır ve kullanıcının girişi geçirilir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi `formInput`, hücre **A1**.  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
   Ardından, forma düğmenin click işlemek için kod ekleyin olay.  
  
## <a name="send-information-to-the-worksheet"></a>Çalışma sayfasına bilgileri Gönder  
  
### <a name="to-send-information-to-the-worksheet"></a>Çalışma sayfasına bilgileri göndermek için  
  
1.  Sağ **GetInputString** içinde **Çözüm Gezgini**ve ardından **Görünüm Tasarımcısı**.  
  
2.  Düğmenin kod dosyasını açmak için düğmeyi çift tıklatın <xref:System.Windows.Forms.Control.Click> olay işleyicisi eklenir.  
  
3.  Metin kutusunda girişi alan işleve göndermek için olay işleyicisine kod ekleyin `WriteStringToCell`ve ardından formu kapatın.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="test"></a>Test  
 Artık proje çalıştırabilirsiniz. Windows Form görüntülenir ve girişinizi çalışma sayfasında görüntülenir.  
  
### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Windows Form göründüğünden emin olun.  
  
3.  Tür **Hello World** metin kutusuna ve ardından **Tamam**.  
  
4.  Onaylayın **Hello World** hücrede görünür **A1** çalışma sayfası.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol, bir Windows Form ve çalışma veri geçirme gösteren temellerini gösterir. Gerçekleştirmek isteyebileceğiniz diğer görevler aşağıdakileri içerir:  
  
-   Bir Excel çalışma kitabı veya Word belgesi Windows Forms denetimleri kullanın. Daha fazla bilgi için [Windows Forms denetimleri Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Belge düzeyinde özelleştirme veya bir VSTO eklentisi Microsoft Office uygulamasının kullanıcı arabirimini değiştirin. Daha fazla bilgi için [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Word'ü kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)   
 [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)  
  
  