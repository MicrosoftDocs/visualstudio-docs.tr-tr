---
title: 'İzlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b6c36e93d9dd8dd4ef81d0d124ae33e842a16d7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677247"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>İzlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme
  Bu yönerge, kullanıcıların Gizle veya Şerit üzerindeki iki durumlu bir düğmenin tıklayarak özel görev bölmesi oluşturma işlemini gösterir. Her zaman Microsoft Office uygulamaları, kullanıcıların özel görev bölmeleri göstermek veya gizlemek varsayılan bir yol sağlamaz çünkü, kullanıcıların, özel görev bölmesini Gizle veya görüntülemek için tıklayabileceği bir düğme gibi bir kullanıcı arabirimi (UI) öğesi oluşturmanız gerekir.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu izlenecek yolda Excel özellikle kullansa da, yukarıda listelenen tüm uygulamalar için izlenecek yol tarafından gösterilen kavramlar geçerlidir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Özel görev bölmesi, kullanıcı Arabirimi tasarlama.  
  
-   İki durumlu bir düğmenin Şerit ekleniyor.  
  
-   İki durumlu düğme özel görev bölmesi ile eşitleniyor.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel veya Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Eklenti projesi oluşturun  
 Bu adımda, Excel için VSTO eklentisi projesi oluşturur.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel eklenti projesi oluşturun **SynchronizeTaskPaneAndRibbon**, Excel eklentisi proje şablonunu kullanarak. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **ThisAddIn.cs** veya **ThisAddIn.vb** ekler ve kod dosyası **SynchronizeTaskPaneAndRibbon** için proje **Çözüm Gezgini**.  
  
## <a name="add-a-toggle-button-to-the-ribbon"></a>İki durumlu bir düğmenin şeridine ekleyin  
 Office uygulaması tasarım yönergelerinden biri olduğundan, kullanıcıların Office uygulaması UI denetimini her zaman olmalıdır. Kullanıcıların özel görev bölmesi denetimi etkinleştirmek için gösterir ve görev bölmesini gizler Şerit iki durumlu düğme ekleyebilirsiniz. İki durumlu düğme oluşturmak için bir **Şerit (Görsel Tasarımcı)** projeye öğe. Tasarımcı eklemenize ve yerleştirmenize, denetim özelliklerini ayarlamanıza ve denetim olaylarını yardımcı olur. Daha fazla bilgi için [Şerit Tasarımcısı](../vsto/ribbon-designer.md).  
  
### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Şerit için iki durumlu düğme eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)**.  
  
3.  Yeni Şeridin adını değiştirmek **ManageTaskPaneRibbon**, tıklatıp **Ekle**.  
  
     **ManageTaskPaneRibbon.cs** veya **ManageTaskPaneRibbon.vb** dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.  
  
4.  Şerit Tasarımcısı'nda tıklatın **group1**.  
  
5.  İçinde **özellikleri** penceresinde **etiket** özelliğini **Görev Bölmesi Yöneticisi**.  
  
6.  Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **ToggleButton** üzerine **Görev Bölmesi Yöneticisi** grubu.  
  
7.  Tıklayın **toggleButton1**.  
  
8.  İçinde **özellikleri** penceresinde **etiket** özelliğini **görev bölmesi**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi, kullanıcı arabirimi tasarımı  
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzene sahip bir kullanıcı denetiminin tasarlayabilirsiniz. Bu kılavuzda daha sonra özel görev bölmesini kullanıcı denetimi ekleyeceksiniz.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi kullanıcı arabiriminin tasarlamak için  
  
1.  Üzerinde **proje** menüsünü tıklatın **kullanıcı denetimi Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, kullanıcı denetimine adını değiştirmek **TaskPaneControl**, tıklatıp **Ekle**.  
  
     Kullanıcı denetimi Tasarımcısı'nda açılır.  
  
3.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **TextBox** kullanıcı denetimi için denetim.  
  
## <a name="create-the-custom-task-pane"></a>Özel görev bölmesi oluşturun  
 VSTO eklentisi başlatıldığında özel görev bölmesi oluşturmak için görev bölmesinde kullanıcı denetimi eklemek <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisi olay işleyicisi. Varsayılan olarak, özel görev bölmesi görünür olmaz. Bu kılavuzda daha sonra görüntülenen veya kullanıcının Şerit eklediğiniz ve iki durumlu düğmeyi tıkladığında görev bölmesini Gizle kod ekleyeceksiniz.  
  
### <a name="to-create-the-custom-task-pane"></a>Özel görev bölmesi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **Excel**.  
  
2.  Sağ **ThisAddIn.cs** veya **ThisAddIn.vb** tıklatıp **kodu görüntüle**.  
  
3.  Aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod örneğini bildirir `TaskPaneControl` üyesi olarak `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]  
  
4.  Değiştirin `ThisAddIn_Startup` aşağıdaki kod ile olay işleyicisi. Bu kod ekler `TaskPaneControl` nesnesini `CustomTaskPanes` alan, ancak özel görev bölmesinde görüntülemez (varsayılan olarak, <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> özelliği <xref:Microsoft.Office.Tools.CustomTaskPane> sınıfı **false**). Visual C# kodu ayrıca bir olay işleyicisi ekler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> olay.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]  
  
5.  Aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Bu yöntem işleme <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> olay. Kullanıcının kapattığı zaman görev bölmesinde tıklayarak **Kapat** (X), geçiş durumu düğmesini Şerit üzerinde bu yöntemi güncelleştirmeleri düğmesi.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]  
  
6.  Aşağıdaki özelliği ekleyin `ThisAddIn` sınıfı. Bu özellik sunan özel `myCustomTaskPane1` diğer sınıflar için nesne. Bu kılavuzda daha sonra kod ekleyeceksiniz `MyRibbon` bu özelliği kullanan sınıf.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]  
  
## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>İki durumlu düğmeyi kullanarak özel görev bölmesini gösterme ve gizleme  
 Son adım, kullanıcı Şeritteki ve iki durumlu düğmeyi tıkladığında özel görev bölmesini gizler veya gösterir kod eklemektir.  
  
### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Görüntüleme ve iki durumlu düğmeyi kullanarak özel görev bölmesini Gizle  
  
1.  Şerit Tasarımcısı'nda çift **görev bölmesi** iki durumlu düğme.  
  
     Visual Studio otomatik olarak oluşturduğu adlı bir olay işleyicisi `toggleButton1_Click`, yürüten <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay. Visual Studio ayrıca açar *MyRibbon.cs* veya *MyRibbon.vb* dosyası Kod Düzenleyicisi'nde.  
  
2.  Değiştirin `toggleButton1_Click` aşağıdaki kod ile olay işleyicisi. Kullanıcı ve iki durumlu düğmeyi tıkladığında bu kodu görüntüler veya olup iki durumlu düğmeye basıldığında veya basılmamış bağlı olarak özel görev bölmesini gizler.  
  
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]  
  
## <a name="test-the-add-in"></a>Eklenti test  
 Projeyi çalıştırdığınızda, Excel, özel görev bölmesi görüntülemeden açılır. Kodu test etmek için Şerit Aç/Kapat düğmesine tıklayın.  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO eklenti test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
     Excel açıldığını onaylayın ve **eklentileri** sekmesi, Şerit üzerinde görünür.  
  
2.  Tıklayın **eklentileri** Şerit sekmesi üzerinde.  
  
3.  İçinde **Görev Bölmesi Yöneticisi** grubunda **görev bölmesi** iki durumlu düğme.  
  
     Görev bölmesi alternatif olarak görüntülenir ve iki durumlu düğmeyi tıklattığınızda gizli olduğunu doğrulayın.  
  
4.  Görev bölmesi görünür olduğunda tıklayın **Kapat** görev bölmesinde üst köşesindeki düğmeyi (X).  
  
     İki durumlu düğmesini basılı olmadığından göründüğünü doğrulayın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Özel görev bölmeleri aşağıdaki konulardan oluşturma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Özel görev bölmesi VSTO eklentisi için farklı bir uygulama oluşturun. Özel görev bölmeleri destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
-   Bir uygulamayı özel görev bölmesinden otomatikleştirme. Daha fazla bilgi için [izlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Özel görev bölmesi Outlook'ta açtığınız her e-posta iletisi oluşturun. Daha fazla bilgi için [izlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özel görev bölmeleri](../vsto/custom-task-panes.md)   
 [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [İzlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)  
  
  