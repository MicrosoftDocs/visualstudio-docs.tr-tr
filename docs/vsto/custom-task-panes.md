---
title: Özel görev bölmeleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4e8384bc86bf59216c353b0f4610d3863445781
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889769"
---
# <a name="custom-task-panes"></a>Özel görev bölmeleri
  Görev bölmeleri, genellikle bir Microsoft Office uygulamasının bir pencerede bir tarafı yerleştirilmiş kullanıcı arabirimi bölmeleri bulunur. Özel görev bölmeleri size kendi görev bölmesi oluşturun ve kullanıcıların çözümünüzün özelliklerine erişmek için tanıdık bir arabirim sağlamak için bir yol sağlar. Örneğin, arabirim belgeleri değiştirmek veya bir veri kaynağından verileri görüntülemek için kodu çalıştırmak denetimleri içerebilir.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Özel görev bölmesi, Eylemler Bölmesi'nden farklıdır. Eylemler bölmesinde, Microsoft Office Word ve Microsoft Office Excel için belge düzeyi özelleştirmeleri bir parçasıdır. Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Özel görev bölmeleri avantajları  
 Özel görev bölmeleri özelliklerinizi alışkın oldukları bir arabirim tümleştirmenize olanak tanır. Visual Studio araçları kullanarak özel görev bölmesi hızlı bir şekilde oluşturabilirsiniz.  
  
### <a name="familiar-user-interface"></a>Alışkın oldukları bir arabirim  
 Microsoft Office sistemi uygulamaların kullanıcılardır zaten görev bölmeleri kullanımıyla ilgili bilgi sahibi **stilleri ve biçimlendirme** Word görev bölmesinde. Özel görev bölmeleri, Microsoft Office sistemindeki diğer görev bölmeleri gibi davranır. Kullanıcılar, uygulama penceresinin farklı kenarlara özel görev bölmeleri sabitleyebileceğiniz veya penceresinde herhangi bir konuma özel görev bölmeleri sürükleyebilirsiniz. Bir VSTO aynı anda birden çok özel görev bölmelerini görüntüler eklenti oluşturabileceğiniz ve kullanıcılar her bir görev bölmesi ayrı ayrı denetleyebilir.  
  
### <a name="windows-forms-support"></a>Windows forms desteği  
 Windows Forms denetimleri, Visual Studio'da Office geliştirme araçlarını kullanarak oluşturduğunuz özel görev bölmesi kullanıcı arabiriminin temel alır. Tanıdık Windows Form Tasarımcısı kullanıcı arabirimi için bir özel görev bölmesi tasarlamak için kullanabilirsiniz. Görev bölmesindeki denetimlere veri kaynağına bağlamak için Windows Forms veri bağlama desteği de kullanabilirsiniz.  
  
## <a name="create-a-custom-task-pane"></a>Özel görev bölmesi oluşturun  
 Temel özel görev bölmesi iki adımda oluşturabilirsiniz:  
  
1. Windows Forms denetimleri ekleyerek, özel görev bölmesi için bir kullanıcı arabirimi oluşturma bir <xref:System.Windows.Forms.UserControl> nesne.  
  
2. Özel görev bölmesi kullanıcı denetimine ileterek örneği <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> VSTO eklenti nesne. Bu koleksiyona yeni bir döndürür <xref:Microsoft.Office.Tools.CustomTaskPane> görev bölmesinde değiştirme ve kullanıcı olaylarına yanıt vermek için kullanabileceğiniz bir nesne.  
  
   Daha fazla bilgi için [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="create-the-user-interface"></a>Kullanıcı arabirimi oluşturma  
 Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan tüm özel görev bölmeleri içeren bir <xref:System.Windows.Forms.UserControl> nesne. Bu kullanıcı denetimi, özel görev bölmesi, kullanıcı arabirimi sağlar. Tasarım zamanında veya çalışma zamanında kullanıcı denetimi oluşturabilirsiniz. Kullanıcı denetiminin tasarım zamanında oluşturursanız, görev bölmesinin kullanıcı arabirimi oluşturmak için Windows Form Tasarımcısı'nı kullanabilirsiniz.  
  
### <a name="instantiate-the-custom-task-pane"></a>Özel görev bölmesini örneği  
 Özel görev bölmesi kullanıcı arabiriminin içeren bir kullanıcı denetimi oluşturduktan sonra örneklemek sahip olduğunuz bir <xref:Microsoft.Office.Tools.CustomTaskPane>. Bunu yapmak için kullanıcı denetimine geçirmek <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> eklentide, VSTO birini çağırarak <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemleri. Bu koleksiyonu olarak kullanıma sunulan `CustomTaskPanes` alanını `ThisAddIn` sınıfı. Aşağıdaki kod örneği çalışmak üzere tasarlanmıştır `ThisAddIn` sınıfı.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> Yeni bir yöntem dönüş <xref:Microsoft.Office.Tools.CustomTaskPane> nesne. Bu nesne, görev bölmesinde değiştirme ve kullanıcı olaylarına yanıt vermek için kullanabilirsiniz.  
  
### <a name="control-the-task-pane-in-multiple-windows"></a>Birden çok Windows görev bölmesi denetimi  
 Özel görev bölmeleri, kullanıcıya bir belgeye veya öğeye bir görünümünü sunan bir belge çerçevesi penceresinin ile ilişkilidir. Görev bölmesi, yalnızca ilişkili pencere görüntülendiğinde görülebilir.  
  
 Özel görev bölmesi hangi pencere görüntüleyeceğini belirlemek için uygun kullanın <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesinde oluşturduğunuzda yöntemi aşırı yüklemesi:  
  
- Görev bölmesinde etkin pencere ile ilişkilendirilecek kullanın <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemi.  
  
- Görev bölmesi, belirli bir pencere tarafından barındırılan bir belge ilişkilendirmek için kullanın <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemi.  
  
  Bazı Office uygulamaları açık yönergeler oluşturmak veya birden fazla penceresi açık olduğunda, görev bölmesini görüntülemek ne zaman gerektirir. Bu görev bölmesi ile ilgili belgelerin veya öğelerin uygulamadaki görünmesini sağlamak için kodunuzu özel görev bölmesinde örneklemek nereye dikkate alınması gereken önemli sağlar. Daha fazla bilgi için [windows uygulaması içinde özel görev bölmeleri yönetme](#Managing).  
  
## <a name="access-the-application-from-the-task-pane"></a>Görev bölmesinden uygulama erişimi  
 Kullanıcı denetimi uygulamadan otomatik hale getirmek isterseniz, doğrudan nesne modelini kullanarak erişebileceğiniz `Globals.ThisAddIn.Application` kodunuzda. Statik `Globals` sınıfı erişim sağlar `ThisAddIn` nesne. `Application` Alan bu nesnenin nesne modelini uygulamanın giriş noktasıdır.  
  
 Hakkında daha fazla bilgi için `Application` alanını `ThisAddIn` nesne, bkz: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Bir uygulamayı özel görev bölmesinden otomatikleştirme gösteren bir kılavuz için bkz. [izlenecek yol: uygulamayı özel görev bölmesinden otomatik](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Hakkında daha fazla bilgi için `Globals` sınıfı [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="manage-the-user-interface-of-the-task-pane"></a>Görev bölmesi kullanıcı arabiriminin yönetme  
 Görev bölmesinde oluşturduktan sonra özelliklerini ve olaylarını kullanabilirsiniz <xref:Microsoft.Office.Tools.CustomTaskPane> görev bölmesinin kullanıcı arabirimi denetim ve kullanıcı görev bölmesinde değiştiğinde yanıt vermek için nesne.  
  
### <a name="make-the-custom-task-pane-visible"></a>Özel görev bölmesi görünür yapmak  
 Varsayılan olarak, görev bölmesinde görünür değil. Görev bölmesi görünür yapmak için ayarlamalısınız <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> özelliğini **true**.  
  
 Kullanıcılar kapatabilirsiniz bir görev bölmesi herhangi bir zamanda tıklayarak **kapatmak** görev bölmesinde üst köşesindeki düğmeyi (X). Ancak, özel görev bölmesini yeniden açmak kullanıcılar için varsayılan yolu yoktur. Bir kullanıcı özel görev bölmesi kapanıyorsa görüntülemek için bir yol sağlama sürece, kullanıcı özel görev bölmesi yeniden görüntüleyemezsiniz.  
  
 VSTO eklenti içinde özel görev bölmesi oluşturursanız, kullanıcılar, özel görev bölmesini Gizle veya görüntülemek için tıklayabileceği bir düğme gibi bir kullanıcı Arabirimi öğesi da oluşturmanız gerekir. Özel görev bölmesini Şerit özelleştirmeye destekleyen bir Microsoft Office uygulamasında oluşturursanız, Şerit görüntüler veya özel görev bölmesi gizleyen bir düğme olan denetim grubu ekleyebilirsiniz. Bunun nasıl yapılacağını gösteren bir kılavuz için bkz. [izlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Ekleyebileceğiniz, özel görev bölmesini Şerit özelleştirmeye desteklemeyen bir Microsoft Office uygulamasında oluşturursanız, bir <xref:Microsoft.Office.Core.CommandBarButton> , özel görev bölmesini gizler veya gösterir.  
  
### <a name="modify-the-appearance-of-the-task-pane"></a>Görev bölmesi görünüşünü değiştirme  
 Özelliklerini kullanarak özel görev bölmesi konumunu ve boyutunu denetleyebilirsiniz <xref:Microsoft.Office.Tools.CustomTaskPane> nesne. Diğer birçok değişikliği özelliklerini kullanarak özel görev bölmesi görünümüne hale getirebilirsiniz <xref:System.Windows.Forms.UserControl> özel görev bölmesinde yer alan nesne. Örneğin, özel görev bölmesi için bir arka plan görüntüsü kullanarak belirtebileceğiniz <xref:System.Windows.Forms.Control.BackgroundImage%2A> kullanıcı denetiminin özelliği.  
  
 Kullanarak bir özel görev bölmesinden yapabilirsiniz değişiklikler aşağıdaki tabloda listelenmiştir <xref:Microsoft.Office.Tools.CustomTaskPane> özellikleri.  
  
|Görev|Özellik|  
|----------|--------------|  
|Görev bölmesi boyutunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Görev bölmesinde konumunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Görev bölmesini gizler veya görünür yapmak için|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Kullanıcı görev bölmesinde konumunu değiştirmesini engellemek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="program-custom-task-pane-events"></a>Program özel görev bölmesi olayları  
 VSTO kullanıcı özel görev bölmesi değiştirdiğinde yanıt vermek için eklenti isteyebilirsiniz. Örneğin, kullanıcı bölmesinde yönünü dikey yatay olarak değiştirirse, denetimleri yeniden konumlandırmak isteyebilirsiniz.  
  
 Aşağıdaki tabloda özel görev bölmesini kullanıcının yaptığı değişiklikleri yanıt işleyebileceği olayları listeler.  
  
|Görev|Olay|  
|----------|-----------|  
|Kullanıcı görev bölmesinde konumu değiştiğinde yanıt vermesi.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Yanıt vermek için kullanıcı görev bölmesini gizler veya görünür hale getirir.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="clean-up-resources-used-by-the-task-pane"></a>Görev bölmesi tarafından kullanılan kaynakları temizleyin  
 Özel görev bölmesi, oluşturduktan sonra <xref:Microsoft.Office.Tools.CustomTaskPane> VSTO eklenti çalıştığı sürece nesne bellekte kalır. Kullanıcı tıkladıktan sonra bile, nesne bellekte kalır **Kapat** görev bölmesinde üst köşesindeki düğmeyi (X).  
  
 VSTO eklentisi çalışırken görev bölmesi tarafından kullanılan kaynakları temizlemek için kullanmak <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> yöntemleri. Bu yöntemler belirtilen kaldırma <xref:Microsoft.Office.Tools.CustomTaskPane> nesnesinden `CustomTaskPanes` toplama ve arama <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> nesnesinin yöntemi.  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi kaldırıldığında özel görev bölmesi tarafından kullanılan kaynakları otomatik olarak temizler. Çağırmayın <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> yöntemleri `ThisAddIn_Shutdown` projenizdeki olay işleyicisi. Bu yöntemler oluşturmaz bir <xref:System.ObjectDisposedException>, çünkü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tarafından kullanılan kaynakları temizler <xref:Microsoft.Office.Tools.CustomTaskPane> önce nesne `ThisAddIn_Shutdown` çağrılır. Hakkında daha fazla bilgi için `ThisAddIn_Shutdown`, bkz: [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Birden çok uygulama penceresi içinde özel görev bölmeleri yönetme  
 Belgeler ve diğer öğeleri görüntülemek için birden çok windows kullanan uygulamayı özel görev bölmesi oluşturduğunuzda, kullanıcı olmasını beklerken görev bölmesinde göründüğünden emin olmak için ek adımlar uygulaması gerekir.  
  
 Özel görev bölmeleri tüm uygulamalarda bir kullanıcıya bir belgeye veya öğeye bir görünümünü sunan bir belge çerçevesi penceresinin ile ilişkilidir. Görev bölmesi, yalnızca ilişkili pencere görüntülendiğinde görülebilir. Ancak, tüm uygulamalar aynı şekilde belge çerçeve pencereleri kullanın.  
  
 Aşağıdaki uygulama gruplarını farklı geliştirme gereksinimleri vardır:  
  
- [Outlook](#Outlook)  
  
- [Word, InfoPath ve PowerPoint](#WordAndInfoPath)  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [görev bölmeleri ı: yönetme Word VSTO eklentileri bunu nasıl?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Outlook  
 Outlook için bir özel görev bölmesi oluşturduğunuzda, özel görev bölmesi, belirli bir Gezgin veya denetleyici pencere ile ilişkilidir. Gezginler bir klasörün içeriğini görüntüleyen pencereler, ve denetçiler bir e-posta iletisi veya görev gibi bir öğeyi görüntülemek windows.  
  
 Birden çok Gezgini veya Inspector'ı windows ile özel görev bölmesini görüntülemek istiyorsanız, bir Gezgin veya denetleyici penceresi açıldığında, özel görev bölmesinde yeni bir örneğini oluşturmak gerekir. Bunu yapmak için bir Gezgin veya denetleyici penceresi oluşturulurken bir olayı işlemek ve ardından görev bölmesinde olay işleyicisi oluşturun. Ayrıca gizlemek için Gezgini ve denetçisi olayları işleyebilir veya görüntü görev bölmeleri hangi pencerenin bağlı olarak görünür.  
  
 Görev bölmesi belirli Gezgini veya Inspector ile ilişkilendirmek için <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesi oluşturun ve geçirmek için yöntem <xref:Microsoft.Office.Interop.Outlook.Explorer> veya <xref:Microsoft.Office.Interop.Outlook.Inspector> nesnesini *penceresi* parametresi. Özel görev bölmeleri oluşturma hakkında daha fazla bilgi için bkz. [özel görev bölmeleri genel bakış](../vsto/custom-task-panes.md).  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
  Inspector Windows'un durumunu izlemek için aşağıdaki denetçisi ile ilgili olayları işleyebilir:  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Özel görev bölmesini Outlook içinde birden çok örneğini engelle  
 Outlook windows birden fazla özel görev bölmesi görüntülenmesini engellemek için özel görev bölmesinden kaldırma açıkça `CustomTaskPanes` koleksiyonunu `ThisAddIn` her penceresi kapatıldığında sınıfı. Çağrı <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> yöntemi bir pencere, gibi kapalı olduğunda bir olayda <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> veya <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Özel görev bölmesi açıkça kaldırmazsanız, birden fazla özel görev bölmesini Outlook windows görüntülenebilir. Outlook windows bazen geri dönüştürür ve geri windows kendilerine iliştirilmiş bir özel görev bölmeleri başvuruları korur.  
  
##  <a name="WordAndInfoPath"></a> Word, InfoPath ve PowerPoint  
 Word, InfoPath ve PowerPoint her belge farklı belge çerçeve penceresinde görüntüler. Bu uygulamalar için özel görev bölmesi oluşturduğunuzda, özel görev bölmesi, yalnızca belirli bir belgeyle ilişkilidir. Kullanıcı farklı bir belgeyi açtığında, önceki belge tekrar görünene kadar özel görev bölmesini gizlenir.  
  
 Birden çok belge ile özel görev bölmesini görüntülemek istiyorsanız, kullanıcı yeni bir belge oluşturur veya var olan bir belgeyi açar özel görev bölmesinde yeni bir örneğini oluşturun. Bunu yapmak için bir belge oluşturulan açıldığında veya başlatılan olayları işlemek ve ardından görev bölmesinde olay işleyicileri oluşturun. Ayrıca gizlemek için belge olayları işleyebilir veya görüntü görev bölmeleri hangi belge bağlı olarak görünür.  
  
 Görev bölmesi belirli belge penceresi ile ilişkilendirilecek kullanın <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesi oluşturun ve geçirmek için yöntem bir <xref:Microsoft.Office.Interop.Word.Window> (Word) için <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (InfoPath için), veya <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (için PowerPoint) için *penceresi*parametresi.  
  
### <a name="word-events"></a>Word olayları  
 Word'de belge pencereleri durumunu izlemek için aşağıdaki olayları işleyebilir:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>InfoPath olayları  
 InfoPath belge pencerelerinin durumunu izlemek için aşağıdaki olayları işleyebilir:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>PowerPoint olayları  
 Belge pencereleri PowerPoint'te durumunu izlemek için aşağıdaki olayları işleyebilir:  
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14)) 
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [İzlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [İzlenecek yol: Outlook'ta e-posta iletileri ile birlikte özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
