---
title: 'İzlenecek yol: Program NamedRange denetimi olaylarına karşı'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f8b55cda9576a0203857b3fdaeccbb205b42168
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812524"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>İzlenecek yol: Program NamedRange denetimi olaylarına karşı
  Bu izlenecek yolda nasıl ekleneceğini gösterir. bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Microsoft Office Excel çalışma ve Visual Studio'da Office geliştirme araçlarını kullanarak olaylarına karşı programlama denetimi.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Ekleme bir <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma denetimi.  
  
-   Karşı programlamak <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim olaylarına.  
  
-   Projenizi test edin.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Bu adımda, Visual Studio kullanarak bir Excel çalışma kitabı projesi oluşturur.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel çalışma kitabı projesi oluşturun **Alanım adlı aralığı olayları**. Emin olun **yeni belge oluşturma** seçilir. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve ekler **Alanım adlı aralığı olayları** için proje **Çözüm Gezgini**.  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Çalışma sayfası aralıklarına adlı ve metin Ekle  
 Konak denetimleri genişletilmiş Office nesneleri için bunları ekleyebilirsiniz aynı şekilde belgenize yerel nesne eklersiniz. Örneğin, bir Excel ekleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimini açarak çalışma sayfasına **Ekle** işaret menüsünde **adı**seçip **tanımla**. De ekleyebilirsiniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> ondan sürükleyerek denetimi **araç kutusu** çalışma sayfasına.  
  
 Bu adımda, iki adlandırılmış aralık denetimleri kullanarak çalışma ekleyeceksiniz **araç kutusu**ve ardından çalışma sayfasına metin ekleyin.  
  
### <a name="to-add-a-range-to-your-worksheet"></a>Bir aralık çalışma sayfanıza eklemek için  
  
1.  Doğrulayın *Alanım adlı aralığı Events.xlsx* Visual Studio tasarımcıda açık çalışma kitabı ile `Sheet1` görüntülenir.  
  
2.  Gelen **Excel denetimleri** Sürükle araç kutusu sekmesi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **A1** içinde `Sheet1`.  
  
     **NamedRange Denetimi Ekle** iletişim kutusu görüntülenir.  
  
3.  Doğrulayın **$A$ 1** düzenlenebilir metin kutusu ve söz konusu hücrenin görünür **A1** seçilir. Yüklü değilse, hücreyi tıklatın **A1** seçin.  
  
4.  **Tamam**'ı tıklatın.  
  
     Hücre **A1** adında bir aralığa dönüşür `namedRange1`. Çalışma sayfasında görünür bir gösterge yoktur ancak `namedRange1` görünür **adı** kutusunu (sol taraftaki çalışma hemen üzerinde bulunur), hücre **A1** seçilir.  
  
5.  Başka bir <xref:Microsoft.Office.Tools.Excel.NamedRange> hücre denetimi **B3**.  
  
6.  Doğrulayın **$B$ 3** düzenlenebilir metin kutusu ve söz konusu hücrenin görünür **B3** seçilir. Yüklü değilse, hücreyi tıklatın **B3** seçin.  
  
7.  **Tamam**'ı tıklatın.  
  
     Hücre **B3** adında bir aralığa dönüşür `namedRange2`.  
  
### <a name="to-add-text-to-your-worksheet"></a>Çalışma sayfanızda metin eklemek için  
  
1. Hücredeki **A1**, aşağıdaki metni yazın:  
  
    **NamedRange denetimi örneği budur.**  
  
2. Hücredeki **A3** (sol tarafındaki `namedRange2`), aşağıdaki metni yazın:  
  
    **Olayları:**  
  
   Aşağıdaki bölümlerde, metin ekleyen bir kod yazacaksınız `namedRange2` ve özelliklerini değiştirir `namedRange2` yanıt olarak Denetim <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, ve <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> olayları `namedRange1`.  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick olaya yanıt vermek için kod ekleyin  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick olayı olarak namedRange2 metin eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **Sheet1.vb** veya **Sheet1.cs** seçip **Kodu Görüntüle**.  
  
2.  Kod ekleyin. Bu nedenle `namedRange1_BeforeDoubleClick` olay işleyicisi aşağıdaki gibi görünür:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  C# ' ta adlandırılmış aralık için olay işleyicileri gösterildiği eklemelisiniz <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> aşağıdaki olay. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>Değişiklik olaya yanıt vermek için kod ekleyin  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Değişiklik olayı olarak namedRange2 metin eklemek için  
  
1.  Kod ekleyin. Bu nedenle `NamedRange1_Change` olay işleyicisi aşağıdaki gibi görünür:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Excel'de bir hücreye çift tıklayarak düzenleme moduna girmesidir çünkü bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> olay metin için hiçbir değişiklik olmasa bile seçimi aralığın dışında hareket ettiğinde gerçekleşir.  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>SeçimDeğiştirme olaya yanıt vermek için kod ekleyin  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SeçimDeğiştirme olayı olarak namedRange2 metin eklemek için  
  
1.  Kod ekleyin. Bu nedenle **böylece NamedRange1_SelectionChange** olay işleyicisi aşağıdaki gibi görünür:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Excel'de bir hücreye çift seçimi aralığı taşımanız neden olduğu bir <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> olaylarının önce <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> olayı oluşur.  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Olayları açıklayan bu metin doğrulamak için çalışma kitabınızı sınayabilirsiniz artık bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim olayları oluştuğunda başka bir adlandırılmış aralığına eklenir.  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  İmlecinizi, `namedRange1`, doğrulayın metin ilgili <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> olay eklenir ve çalışma sayfasına bir açıklama eklenir.  
  
3.  İçinde çift tıklayarak `namedRange1`, doğrulayın metin ilgili <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> olayları kırmızı italik metin ile eklenir `namedRange2`.  
  
4.  Dışına tıklayana `namedRange1` ve değişiklik olayı çıkarken oluştuğunu not metni değişiklik yapıldı olsa bile düzenleme modu.  
  
5.  İçinde metin değiştirmek `namedRange1`.  
  
6.  Dışına tıklayana `namedRange1`, doğrulayın metin ilgili <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> mavi metne ile olay eklenir `namedRange2`.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bu izlenecek yol olaylarına karşı programlama temelleri gösterir bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi. Sonraki gelebilir bir görev şu şekildedir:  
  
-   Projeyi dağıtma. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange denetimi](../vsto/namedrange-control.md)   
 [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)   
 [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  