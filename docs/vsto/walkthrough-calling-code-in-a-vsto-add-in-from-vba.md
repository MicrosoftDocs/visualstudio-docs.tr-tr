---
title: "İzlenecek yol: çağrı VBA'dan kod bir VSTO eklenti"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e46cf9032cae7d6400822be7d72394a7845314f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843827"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>İzlenecek yol: çağrı VBA'dan kod bir VSTO eklenti
  Bu yönerge, VSTO eklentisi Visual Basic for Applications (VBA) ve COM, VSTO eklentileri için dahil olmak üzere, başka bir Microsoft Office çözümü için bir nesneyi göstermek nasıl gösterir.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Bu izlenecek yolda Excel özellikle kullansa da, izlenecek yol gösterilen kavramlar, Visual Studio tarafından sağlanan tüm VSTO eklentisi proje şablonuna uygulanabilir.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Diğer Office Çözümlerinden kullanıma sunulabilecek bir sınıf tanımlama.  
  
- Diğer Office çözümlerine sınıfı gösterme.  
  
- VBA koddan sınıfının yöntemini çağırma.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>VSTO eklentisi projesi oluşturun  
 İlk adım, Excel için VSTO eklentisi projesi oluşturmaktır.  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Adlı bir Excel VSTO eklentisi projesi oluşturun **ExcelImportData**, Excel VSTO eklentisi proje şablonunu kullanarak. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açılır **ThisAddIn.cs** veya **ThisAddIn.vb** ekler ve kod dosyası **ExcelImportData** için proje **Çözüm Gezgini**.  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Diğer Office Çözümlerinden kullanıma sunabileceğiniz bir sınıfını tanımlar  
 Çağırmak için bu kılavuzun amacı olan `ImportData` adlı bir sınıfın yöntemini `AddInUtilities` VSTO eklenti VBA kodu içinde. Bu yöntem, etkin çalışma sayfasının A1 hücresine bir dize yazar.  
  
 Kullanıma sunmak için `AddInUtilities` sınıf başka bir Office çözümü için sınıf genel ve COM görünür yapmanız gerekir Ayrıca kullanıma gerekir [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) sınıfında arabirimi. Aşağıdaki yordamda kod bu gereksinimleri karşılayan yollarından biri gösterilmektedir. Daha fazla bilgi için [VSTO eklentilerinde diğer Office Çözümlerinden kod çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Diğer Office Çözümlerinden kullanıma sunabileceğiniz bir sınıfını tanımlamak için  
  
1.  Üzerinde **proje** menüsünü tıklatın **sınıfı Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, değiştirmek için yeni sınıfın adı **AddInUtilities**, tıklatıp **Ekle**.  
  
     **AddInUtilities.cs** veya **AddInUtilities.vb** dosyası Kod Düzenleyicisi'nde açılır.  
  
3.  Dosyasının en üstüne aşağıdaki deyimleri ekleyin.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Değiştirin `AddInUtilities` aşağıdaki kodla sınıfı.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Bu kod yapar `AddInUtilities` sınıf için COM görünür ve ekler `ImportData` sınıfı için yöntemi. Kullanıma sunmak için [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimi `AddInUtilities` ayrıca sınıfında <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği ve COM'a görünür bir arabirim uygular  
  
## <a name="expose-the-class-to-other-office-solutions"></a>Diğer Office çözümleri sınıfı  
 Kullanıma sunmak için `AddInUtilities` diğer Office Çözümlerinden sınıfı, geçersiz kılma <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yönteminde `ThisAddIn` sınıfı. Geçersiz kılmada bir örneğini döndürür `AddInUtilities` sınıfı.  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Diğer Office çözümlerine AddInUtilities sınıfı oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, genişletme **Excel**.  
  
2.  Sağ **ThisAddIn.cs** veya **ThisAddIn.vb**ve ardından **kodu görüntüle**.  
  
3.  Aşağıdaki kodu ekleyin `ThisAddIn` sınıfı.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Çözüm hatasız oluşturulduğunu doğrulayın.  
  
## <a name="test-the-vsto-add-in"></a>Test VSTO eklentisi  
 Çağırabilirsiniz `AddInUtilities` Office çözümleri birkaç farklı türde bir sınıftan. Bu kılavuzda, bir Excel çalışma kitabında VBA kodunu kullanır. Office çözümlerini de kullanabilirsiniz diğer türleri hakkında daha fazla bilgi için bkz. [çağrı kod VSTO eklentileri diğer Office Çözümlerinden](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO eklenti test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Excel'de, etkin çalışma kitabının bir etkin çalışma kitabı (*.xlsm) olarak kaydedin. Masaüstü gibi uygun bir konuma kaydedin.  
  
3.  Şerit üzerinde tıklayın **Geliştirici** sekmesi.  
  
    > [!NOTE]  
    >  Varsa **Geliştirici** sekme görünür değilse, önce görünür olmalıdır. Daha fazla bilgi için [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  İçinde **kod** grubunda **Visual Basic**.  
  
     Visual Basic Düzenleyicisi açılır.  
  
5.  İçinde **proje** penceresinde çift **ThisWorkbook**.  
  
     Kod dosyası `ThisWorkbook` nesnesini açar.  
  
6.  Aşağıdaki VBA kodu için kod dosyasını ekleyin. Bu kod önce temsil eden bir COMAddIn nesnesini alır **ExcelImportData** VSTO eklentisi. Ardından, kod çağırmak için COMAddIn nesnesinin nesne özelliği kullanır `ImportData` yöntemi.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Tuşuna **F5**.  
  
8.  Doğrulayın yeni **aktarılan veriler** sayfası çalışma kitabına eklenmiş. A1 hücresini içeren dize ayrıca doğrulayın **verilerimi budur**.  
  
9. Excel'den çıkın.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 VSTO eklentilerinde aşağıdaki konulardan programlama hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Kullanım `ThisAddIn` konak uygulama otomatikleştirmek ve VSTO eklenti projesindeki diğer görevleri gerçekleştirmek için sınıf. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   VSTO eklentisi içinde özel görev bölmesi oluşturun. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md) ve [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Bir VSTO eklentisi Şeritte özelleştirin. Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md) ve [nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [VSTO eklentilerinde diğer Office Çözümlerinden kod arama](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  