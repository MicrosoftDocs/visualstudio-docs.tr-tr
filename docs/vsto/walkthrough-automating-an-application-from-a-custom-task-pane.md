---
title: 'İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25d6dd29f989f1ea2bbf95ce2b32e7d031e1953e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676747"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme
  Bu yönerge, PowerPoint otomatikleştiren bir özel görev bölmesi oluşturma işlemini gösterir. Kullanıcı tıkladığında özel görev bölmesi tarihler bir slayta ekler. bir <xref:System.Windows.Forms.MonthCalendar> üzerinde özel görev bölmesi denetimi.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu izlenecek yolda PowerPoint özellikle kullansa da, yukarıda listelenen tüm uygulamalar için izlenecek yol tarafından gösterilen kavramlar geçerlidir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Özel görev bölmesi, kullanıcı arabirimi tasarlama.  
  
-   PowerPoint özel görev bölmesinden otomatikleştirme.  
  
-   Özel görev bölmesi, PowerPoint'te görüntüleniyor.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 veya [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Eklenti projesi oluşturun  
 İlk adım, PowerPoint için VSTO eklentisi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir PowerPoint VSTO eklentisi projesi oluşturun **MyAddIn**, PowerPoint eklenti proje şablonunu kullanarak. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **ThisAddIn.cs** veya **ThisAddIn.vb** ekler ve kod dosyası **MyAddIn** için proje **Çözüm Gezgini**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi, kullanıcı arabirimi tasarımı  
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzene sahip bir kullanıcı denetiminin tasarlayabilirsiniz. Bu kılavuzda daha sonra özel görev bölmesini kullanıcı denetimi ekleyeceksiniz.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi kullanıcı arabiriminin tasarlamak için  
  
1.  Üzerinde **proje** menüsünü tıklatın **kullanıcı denetimi Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, kullanıcı denetimine adını değiştirmek **MyUserControl**, tıklatıp **Ekle**.  
  
     Kullanıcı denetimi Tasarımcısı'nda açılır.  
  
3.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **MonthCalendar** kullanıcı denetimi için denetim.  
  
     Varsa **MonthCalendar** kontrolü kullanıcı denetiminin tasarım yüzeyine daha büyük, kullanıcı denetimi uyacak şekilde yeniden boyutlandırın **MonthCalendar** denetimi.  
  
## <a name="automate-powerpoint-from-the-custom-task-pane"></a>PowerPoint özel görev bölmesinden otomatikleştirme  
 VSTO eklentisi amacı, seçilen tarihten etkin sunu ilk slaytta eklemektir. Kullanım <xref:System.Windows.Forms.MonthCalendar.DateChanged> değiştiğinde seçilen tarihten eklenecek denetimin olay.  
  
### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Özel görev bölmesinden PowerPoint otomatik hale getirmek için  
  
1.  Tasarımcıda çift <xref:System.Windows.Forms.MonthCalendar> denetimi.  
  
     **MyUserControl.cs** veya **MyUserControl.vb** dosya açılır ve bir olay işleyicisi için <xref:System.Windows.Forms.MonthCalendar.DateChanged> olay oluşturulur.  
  
2.  Aşağıdaki kod dosyasının en üstüne ekleyin. Bu kod için diğer ad oluşturur <xref:Microsoft.Office.Core> ve <xref:Microsoft.Office.Interop.PowerPoint> ad alanları.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Aşağıdaki kodu ekleyin `MyUserControl` sınıfı. Bu kod bildirir bir <xref:Microsoft.Office.Interop.PowerPoint.Shape> nesnenin bir üyesi olarak `MyUserControl`. Aşağıdaki adımda bunu kullanacaksınız <xref:Microsoft.Office.Interop.PowerPoint.Shape> bir metin kutusu etkin sunu bir slayt eklemek için.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Değiştirin `monthCalendar1_DateChanged` aşağıdaki kod ile olay işleyicisi. Bu kod, bir metin kutusu etkin sunu ilk slaytta ekler ve ardından şu anda seçilen tarihten metin kutusuna ekler. Bu kod `Globals.ThisAddIn` PowerPoint nesne modeli erişmek için nesne.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  İçinde **Çözüm Gezgini**, sağ **MyAddIn** proje ve ardından **yapı**. Projenin hatasız oluşturulduğunu doğrulayın.  
  
## <a name="display-the-custom-task-pane"></a>Özel görev bölmesini görüntüle  
 VSTO eklentisi başlatıldığında özel görev bölmesini görüntülemek için görev bölmesinde kullanıcı denetimi Ekle <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisi olay işleyicisi.  
  
### <a name="to-display-the-custom-task-pane"></a>Özel görev bölmesini görüntülemek için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **PowerPoint**.  
  
2.  Sağ **ThisAddIn.cs** veya **ThisAddIn.vb** tıklatıp **kodu görüntüle**.  
  
3.  Aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod örneğini bildirir `MyUserControl` ve <xref:Microsoft.Office.Tools.CustomTaskPane> üyesi olarak `ThisAddIn` sınıfı.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Değiştirin `ThisAddIn_Startup` aşağıdaki kod ile olay işleyicisi. Bu kod yeni bir oluşturur <xref:Microsoft.Office.Tools.CustomTaskPane> ekleyerek `MyUserControl` nesnesini `CustomTaskPanes` koleksiyonu. Kod ayrıca görev bölmesini görüntüler.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="test-the-add-in"></a>Eklenti test  
 Projeyi çalıştırdığınızda, PowerPoint açılır ve VSTO eklentisi özel görev bölmesini görüntüler. Tıklayın <xref:System.Windows.Forms.MonthCalendar> kodu test etmek için denetimi.  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO eklenti test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Özel görev bölmesi görünür olduğunu doğrulayın.  
  
3.  Bir tarihi tıklayın <xref:System.Windows.Forms.MonthCalendar> görev bölmesi denetimi.  
  
     Tarih ilk slaytta etkin sunu eklenir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Özel görev bölmeleri aşağıdaki konulardan oluşturma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Özel görev bölmesi VSTO eklentisi için farklı bir uygulama oluşturun. Özel görev bölmeleri destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
-   Özel görev bölmesini görüntülemek veya gizlemek için kullanılan bir Şerit düğmesi oluşturun. Daha fazla bilgi için [izlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Özel görev bölmesi Outlook'ta açtığınız her e-posta iletisi oluşturun. Daha fazla bilgi için [izlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özel görev bölmeleri](../vsto/custom-task-panes.md)   
 [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [İzlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  