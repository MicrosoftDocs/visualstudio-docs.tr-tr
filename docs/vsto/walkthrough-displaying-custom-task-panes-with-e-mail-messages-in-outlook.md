---
title: "İzlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c25121e96005486450397938aad3c24f89d26cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828474"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>İzlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme
  Bu izlenecek yolda oluşturulan veya açılan her e-posta iletisiyle bir özel görev bölmesi benzersiz bir örneğini görüntülemek nasıl gösterir. Kullanıcılar, görüntülemek veya her e-posta iletisini Şeritteki bir düğmeyi kullanarak özel görev bölmesini gizle.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Birden çok Gezgini veya Inspector'ı windows ile bir özel görev bölmesini görüntülemek için özel görev bölmesi açıldığında her penceresi için bir örneğini oluşturmanız gerekir. Özel görev bölmeleri Outlook Windows davranış hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  Bu izlenecek yol, VSTO eklentisi kod kod ardındaki mantığı hakkında konuşmak amacıyla kolaylaştırmak için küçük bölümler sunar.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   Özel görev bölmesi kullanıcı arabirimini (UI) tasarlama.  
  
-   Özel Şerit kullanıcı Arabirimi oluşturma.  
  
-   E-posta iletileri ile özel Şerit kullanıcı arabirimini görüntüleniyor.  
  
-   Inspector windows ve özel görev bölmelerini yönetmek için bir sınıf oluşturma.  
  
-   Başlatma ve VSTO eklentisi tarafından kullanılan kaynakları temizleme.  
  
-   Birlikte özel görev bölmesini Şerit iki durumlu düğme eşitleniyor.  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya Microsoft Outlook 2010.  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [ı: kullanım görev bölmeleri Outlook'ta bunu nasıl?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Özel görev bölmeleri, VSTO eklentileri uygulanır. Outlook için VSTO eklentisi projesi oluşturarak başlayın.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Oluşturma bir **Outlook eklentisi** adlı proje **OutlookMailItemTaskPane**. Kullanım **Outlook eklentisi** proje şablonu. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır *ThisAddIn.cs* veya *ThisAddIn.vb* ekler ve kod dosyası **OutlookMailItemTaskPane** için proje **Çözüm Gezgini**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi, kullanıcı arabirimi tasarımı  
 Özel görev bölmeleri için görsel tasarımcı yoktur ancak bir kullanıcı denetimiyle istediğiniz kullanıcı arabirimini tasarlayabilirsiniz. Bu VSTO eklentisi özel görev bölmesinde içeren basit bir kullanıcı Arabirimi olan bir <xref:System.Windows.Forms.TextBox> denetimi. Bu kılavuzda daha sonra özel görev bölmesini kullanıcı denetimi ekleyeceksiniz.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesi kullanıcı arabiriminin tasarlamak için  
  
1.  İçinde **Çözüm Gezgini**, tıklayın **OutlookMailItemTaskPane** proje.  
  
2.  Üzerinde **proje** menüsünü tıklatın **kullanıcı denetimi Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, kullanıcı denetimine adını değiştirmek **TaskPaneControl**ve ardından **Ekle**.  
  
     Kullanıcı denetimi Tasarımcısı'nda açılır.  
  
4.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **TextBox** kullanıcı denetimi için denetim.  
  
## <a name="design-the-user-interface-of-the-ribbon"></a>Şeridin kullanıcı arabirimini tasarlayabileceğiniz  
 Bu VSTO eklentisi için hedeflerinden kullanıcılar her e-posta iletisini Şeritteki özel görev bölmesinden görüntülemek veya gizlemek için bir yol vermektir. Kullanıcı arabirimini sağlamak için kullanıcıların özel görev bölmesini Gizle veya görüntülemek için tıklayabileceği ve iki durumlu bir düğmenin görüntüler özel bir Şerit UI oluşturun.  
  
### <a name="to-create-a-custom-ribbon-ui"></a>Özel bir Şerit kullanıcı arabirimini oluşturmak için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)**.  
  
3.  Yeni Şeridin adını değiştirmek **ManageTaskPaneRibbon**, tıklatıp **Ekle**.  
  
     *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.  
  
4.  Şerit Tasarımcısı'nda tıklatın **group1**.  
  
5.  İçinde **özellikleri** penceresinde **etiket** özelliğini **Görev Bölmesi Yöneticisi**.  
  
6.  Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, bir ToggleButton denetimi sürükleyin **Görev Bölmesi Yöneticisi** grubu.  
  
7.  Tıklayın **toggleButton1**.  
  
8.  İçinde **özellikleri** penceresinde **etiket** özelliğini **görev bölmesi**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Özel Şerit kullanıcı arabirimini e-posta iletileri ile görüntüleme  
 Bu anlatımda oluşturduğunuz özel görev bölmesi, e-posta iletilerini içeren Inspector'ı windows ile görünen şekilde tasarlanmıştır. Bu nedenle, yalnızca bu windows ile özel, Şerit kullanıcı arabirimini görüntülemek için özelliklerini ayarlayın.  
  
### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>E-posta iletileri ile özel Şerit kullanıcı arabirimini görüntülemek için  
  
1.  Şerit Tasarımcısı'nda tıklatın **ManageTaskPaneRibbon** Şerit.  
  
2.  İçinde **özellikleri** penceresinde, aşağı açılan listeyi tıklatın **RibbonType**seçip **Microsoft.Outlook.Mail.Compose** ve  **Microsoft.Outlook.Mail.Read**.  
  
## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Inspector windows ve özel görev bölmeleri yönetmek için bir sınıf oluşturun  
 Hangi VSTO eklentisi hangi özel görev bölmesi belirli e-posta iletisiyle ilişkili olduğunu bulduğu bazı durumlar vardır. Bu gibi durumlarda, aşağıdakileri içerir:  
  
- Kullanıcının e-posta iletisine kapattığı zaman. Bu durumda, VSTO eklentisi VSTO eklentisi tarafından kullanılan kaynakları doğru şekilde temizlendiğinden emin olmak için karşılık gelen özel görev bölmesi kaldırmalısınız.  
  
- Kullanıcının özel görev bölmesi kapattığı zaman. Bu durumda, VSTO eklentisi e-posta iletisinin Şerit üzerindeki iki durumlu düğme durumunu güncelleştirmeniz gerekir.  
  
- Kullanıcı, Şeritteki ve iki durumlu düğmeyi tıkladığında. Bu durumda, VSTO eklentisi gerekir Gizle veya ilgili görev bölmesini görüntüleyin.  
  
  VSTO eklenti hangi özel görev bölmesi her açık e-posta iletisiyle ilişkili izlemek, etkinleştirmek için çiftlerini saran özel bir sınıf oluşturun <xref:Microsoft.Office.Interop.Outlook.Inspector> ve <xref:Microsoft.Office.Tools.CustomTaskPane> nesneleri. Bu sınıf, her e-posta iletisi için yeni bir özel görev bölmesi nesnesi oluşturur ve karşılık gelen e-posta iletisi kapalı olduğunda özel görev bölmesi siler.  
  
### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Inspector windows ve özel görev bölmeleri yönetmek için bir sınıf oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ *ThisAddIn.cs* veya *ThisAddIn.vb* dosya ve ardından **Kodu Görüntüle**.  
  
2.  Dosyasının en üstüne aşağıdaki deyimleri ekleyin.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Aşağıdaki kodu ekleyin *ThisAddIn.cs* veya *ThisAddIn.vb* dışında dosya `ThisAddIn` sınıfı (Visual C# için bu kod içinde ekleme `OutlookMailItemTaskPane` ad alanı). `InspectorWrapper` Sınıfı yöneten bir çift <xref:Microsoft.Office.Interop.Outlook.Inspector> ve <xref:Microsoft.Office.Tools.CustomTaskPane> nesneleri. Aşağıdaki adımlarda bu sınıf tanımını tamamlanır.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Önceki adımda eklediğiniz koddan sonra aşağıdaki oluşturucuyu ekleyin. Bu oluşturucu oluşturur ve başlatır, ilişkili olduğu yeni bir özel görev bölmesi <xref:Microsoft.Office.Interop.Outlook.Inspector> geçirilen nesne. C# ' ta Oluşturucu ayrıca olay işleyicilerine ekler <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> olayı <xref:Microsoft.Office.Interop.Outlook.Inspector> nesne ve <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> olayı <xref:Microsoft.Office.Tools.CustomTaskPane> nesne.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Önceki adımda eklediğiniz koddan sonra aşağıdaki yöntemi ekleyin. Bu yöntem için bir olay işleyicisidir <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> olayı <xref:Microsoft.Office.Tools.CustomTaskPane> bulunan nesne `InspectorWrapper` sınıfı. Her kullanıcının açar veya kapatır özel görev bölmesi Bu kod, iki durumlu düğme durumunu güncelleştirir.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Önceki adımda eklediğiniz koddan sonra aşağıdaki yöntemi ekleyin. Bu yöntem için bir olay işleyicisidir <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> olayı <xref:Microsoft.Office.Interop.Outlook.Inspector> geçerli e-posta iletisi içeren nesne. E-posta iletisi kapalı olduğunda olay işleyicisi kaynakları serbest bırakır. Olay işleyicisi geçerli bir özel görev bölmesinden da kaldırır. `CustomTaskPanes` koleksiyonu. Bu, sonraki e-posta iletisi açıldığında özel görev bölmesini birden çok örneğini önlemeye yardımcı olur.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Önceki adımda eklediğiniz koddan sonra aşağıdaki kodu ekleyin. Bu kılavuzda daha sonra görüntülemek veya özel görev bölmesi gizlemek için özel Şerit arabirimdeki bir yöntem bu özelliğin çağıracaksınız.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Başlatma ve eklenti tarafından kullanılan kaynakları temizleme  
 Kodu `ThisAddIn` VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, VSTO eklentisi tarafından kullanılan kaynakları temizlemek için bir sınıf. VSTO eklentisi için bir olay işleyicisi ayarlayarak başlatın <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay ve bu olay işleyicisi için tüm mevcut e-posta iletilerini geçirerek. VSTO eklentisi kaldırıldığında, olay işleyicisi ayırma ve VSTO eklentisi tarafından kullanılan nesneleri temizleyin.  
  
### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Başlatmak ve VSTO eklentisi tarafından kullanılan kaynakları temizlemek için  
  
1. İçinde *ThisAddIn.cs* veya *ThisAddIn.vb* tanımını bulun, dosya `ThisAddIn` sınıfı.  
  
2. Aşağıdaki bildirimi ekleyin `ThisAddIn` sınıfı:  
  
   - `inspectorWrappersValue` Alanı içeren tüm <xref:Microsoft.Office.Interop.Outlook.Inspector> ve `InspectorWrapper` VSTO eklentisi tarafından yönetilen nesneler.  
  
   - `inspectors` Alan geçerli Outlook örneğini denetçisi windows derlemesine bir başvuru tutar. Bu başvuru atık toplayıcının için olay işleyicisini içeren belleği boşaltmasını engeller <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> sonraki adımda tanımlayacağınız olay.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3. Değiştirin `ThisAddIn_Startup` yöntemini aşağıdaki kod ile. Bu kod bir olay işleyicisi ekler <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> geçirir ve var olan her <xref:Microsoft.Office.Interop.Outlook.Inspector> nesnesi için olay işleyicisi. Outlook çalışmaya başladıktan sonra kullanıcı için VSTO eklentisi yüklenirse, VSTO eklentisi bu bilgileri zaten açık olan tüm e-posta iletileri için özel görev bölmeleri oluşturmak için kullanır.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4. Değiştirin `ThisAddIn_ShutDown` yöntemini aşağıdaki kod ile. Bu kod ayırır <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay işleyicisi ve VSTO eklentisi tarafından kullanılan nesneleri temizler.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5. Aşağıdaki <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay işleyicisine `ThisAddIn` sınıfı. Yeni bir <xref:Microsoft.Office.Interop.Outlook.Inspector> içeren bir e-posta iletisi yöntemi yeni bir örneğini oluşturur `InspectorWrapper` e-posta iletisi ve ilgili görev bölmesi arasındaki ilişkiyi yönetmek için nesne.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6. Aşağıdaki özelliği ekleyin `ThisAddIn` sınıfı. Bu özellik sunan özel `inspectorWrappersValue` dışındaki kod alanı `ThisAddIn` sınıfı.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Hata olmadan derlediğinden emin olmak için projenizi derleyin.  
  
### <a name="to-build-your-project"></a>Projenizi yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **OutlookMailItemTaskPane** proje ve ardından **yapı**. Projenin hata olmadan derlediğinden emin olun.  
  
## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Birlikte özel görev bölmesini Şerit iki durumlu düğme Eşitle  
 Görev bölmesi görünür ve görev bölmesinde gizlenen basılmamış görünür olduğunda basılı iki durumlu düğme görünecektir. Özel görev bölmesi düğmesi durumunu eşitlemek için değiştirme <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay işleyicisi.  
  
### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Özel görev bölmesi iki durumlu düğme ile eşitlemek için  
  
1.  Şerit Tasarımcısı'nda çift **görev bölmesi** iki durumlu düğme.  
  
     Visual Studio otomatik olarak oluşturduğu adlı bir olay işleyicisi `toggleButton1_Click`, yürüten <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay. Visual Studio ayrıca açar *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosyası Kod Düzenleyicisi'nde.  
  
2.  Üstüne aşağıdaki deyimleri ekleyin *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosya.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Değiştirin `toggleButton1_Click` aşağıdaki kod ile olay işleyicisi. Kullanıcı ve iki durumlu düğmeyi tıkladığında, bu yöntem gizler veya geçerli denetçisi pencere ile ilişkili özel görev bölmesini görüntüler.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="test-the-project"></a>Test projesi  
 Proje hata ayıklamaya başladığınızda, Outlook açar ve VSTO eklentisi yüklenir. VSTO eklentisi özel görev bölmesi açıldığında her e-posta iletisi benzersiz bir örneğini gösterir. Kodu test etmek için birkaç yeni e-posta iletisi oluşturun.  
  
### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisi test etmek için  
  
1. Tuşuna **F5**.  
  
2. Outlook'ta tıklayın **yeni** yeni bir e-posta iletisi oluşturmak için.  
  
3. E-posta iletisini Şeritteki tıklatın **eklentileri** sekmesine ve ardından **görev bölmesi** düğmesi.  
  
    Doğrulayın başlıklı bir görev bölmesi **My görev bölmesi** e-posta iletisi görüntülenir.  
  
4. Görev bölmesinde yazın **ilk görev bölmesi** metin kutusuna.  
  
5. Görev bölmesini kapatın.  
  
    Doğrulayın durumunu **görev bölmesi** artık basıldığında, düğme değiştirir.  
  
6. Tıklayın **görev bölmesi** düğmesini tekrar.  
  
    Görev bölmesi açılır ve metin kutusu hala dizenin bulunduğunu doğrulayın **ilk görev bölmesi**.  
  
7. Outlook'ta tıklayın **yeni** ikinci bir e-posta iletisi oluşturmak için.  
  
8. E-posta iletisini Şeritteki tıklatın **eklentileri** sekmesine ve ardından **görev bölmesi** düğmesi.  
  
    Doğrulayın başlıklı bir görev bölmesi **My görev bölmesi** e-posta iletisi görüntülenir ve bu görev bölmesinde metin kutusu boştur.  
  
9. Görev bölmesinde yazın **ikinci görev bölmesi** metin kutusuna.  
  
10. Odak ilk e-posta iletisi için değiştirin.  
  
     Bu e-posta iletisiyle ilişkili görev bölmesinde hala görüntülediğini doğrulamak **ilk görev bölmesi** metin kutusuna.  
  
    Bu VSTO eklentisi ayrıca daha fazla işleme Gelişmiş deneyebileceğiniz senaryoları. Örneğin, e-postaları kullanarak görüntülerken davranışını sınayabilirsiniz **sonraki öğeyi** ve **önceki öğeyi** düğmeleri. VSTO eklentisi kaldırma, birden fazla e-posta iletilerini ve VSTO eklentisi sonra yeniden davranışı da test edebilirsiniz.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Özel görev bölmeleri aşağıdaki konulardan oluşturma hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Özel görev bölmesi VSTO eklentisi için farklı bir uygulama oluşturun. Özel görev bölmeleri destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
-   Bir Microsoft Office uygulamasının özel görev bölmesini kullanarak otomatik hale getirin. Daha fazla bilgi için [izlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Bir Şerit düğmesi, bir özel görev bölmesini görüntülemek veya gizlemek için kullanılan Excel'de oluşturun. Daha fazla bilgi için [izlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Özel görev bölmeleri](../vsto/custom-task-panes.md)   
 [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)   
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  