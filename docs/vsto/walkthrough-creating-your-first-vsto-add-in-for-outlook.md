---
title: 'İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc0f2e7cc7dc40dc305f7860223b5d4acf19a573
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950969"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma
  Bu kılavuzda, Microsoft Office Outlook için VSTO eklentisi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler uygulamanın kendisinin Outlook öğesine açık olduğu bağımsız olarak kullanılabilir. Daha fazla bilgi için [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Outlook için Outlook VSTO eklenti projesinde oluşturuluyor.  
  
- Konu ve yeni bir e-posta iletisinin gövdesi, metin eklemek için Outlook nesne modeli kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Tamamlanmış projeyi VSTO eklentisi artık otomatik olarak geliştirme bilgisayarınızda çalıştırılır, böylece temizleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Visual Studio'da yeni bir Outlook projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde, bir Outlook VSTO eklenti projesini seçin.  
  
6.  İçinde **adı** kutusuna **FirstOutlookAddIn**.  
  
7.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstOutlookAddIn** proje ve açılır **ThisAddIn** Düzenleyicisi'nde kod dosyası.  
  
## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Metnin her yeni e-posta iletisine ekler kod yazma  
 Ardından, ThisAddIn kod dosyası için kodu ekleyin. Yeni kod metin her yeni e-posta iletisine eklemek için Outlook nesne modeli kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisAddIn kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisAddIn` sınıfı. Bu sınıf, kodunuz için bir giriş noktası sağlar ve Outlook nesne modeline erişim sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Kalanı `ThisAddIn` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisAddIn_Startup` Ve `ThisAddIn_Shutdown` olay işleyicileri. Outlook yüklediğinde ve VSTO eklenti bellekten olay işleyicilere çağrılır. Bu olay işleyicileri, VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, VSTO eklenti tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Konu ve her yeni e-posta iletisinin gövdesi, metin eklemek için  
  
1. ThisAddIn kod dosyasında, adında bir alan bildirmek `inspectors` içinde `ThisAddIn` sınıfı. `inspectors` Alan geçerli Outlook örneğini denetçisi windows derlemesine bir başvuru tutar. Bu başvuru atık toplayıcının için olay işleyicisini içeren belleği boşaltmasını engeller <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay.  
  
    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]  
  
2. Değiştirin `ThisAddIn_Startup` yöntemini aşağıdaki kod ile. Bu kod bir olay işleyicisi ekler <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay.  
  
    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]  
  
3. ThisAddIn kod dosyasında, aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod için bir olay işleyicisi tanımlar <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay.  
  
    Kullanıcı yeni bir posta iletisi oluşturduğunda, bu olay işleyicisi konu satırı ve ileti gövdesini metin ekler.  
  
    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]  
  
   Her yeni posta iletisini değiştirmek için aşağıdaki nesneler önceki kod örnekleri kullanın:  
  
-   `Application` Alanını `ThisAddIn` sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.Outlook.Application> Outlook'ün geçerli örneğini temsil eden nesne.  
  
-   `Inspector` Parametresi için olay işleyicisinin <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay. `Inspector` Parametresi bir <xref:Microsoft.Office.Interop.Outlook.Inspector> yeni bir posta iletisi Inspector penceresini temsil eden nesne. Daha fazla bilgi için [Outlook çözümleri](../vsto/outlook-solutions.md).  
  
## <a name="test-the-project"></a>Test projesi  
 Derleme ve projeyi çalıştırın, metin konu satırı ve yeni bir posta iletisi gövdesi göründüğünü doğrulayın.  
  
### <a name="to-test-the-project"></a>Projeyi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, proje için yapı çıkış klasöründe bulunan bütünleştirilmiş kod derlenir. Visual Studio ayrıca bulmak ve VSTO eklentisi yükleme Outlook sağlayan kayıt defteri girişleri kümesi oluşturur ve VSTO eklenti çalıştırmak, geliştirme bilgisayarının güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [Office çözüm derleme işlemine genel bakış](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  Outlook'ta yeni bir posta iletisi oluşturun.  
  
3.  Aşağıdaki metni konu satırı ve ileti gövdesi için eklendiğinden emin olun.  
  
     **Bu metin, kod kullanarak eklendi.**  
  
4.  Outlook'u kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye işiniz bittiğinde, VSTO eklentisi derleme, kayıt defteri girişleri ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırın. Aksi halde, VSTO eklentisi geliştirme bilgisayarında Outlook her açtığınızda çalışacaktır.  
  
### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bir temel VSTO eklentisi Outlook için oluşturduğunuz, VSTO eklentileri aşağıdaki konulardan geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Outlook için VSTO eklentileri kullanarak gerçekleştirebileceğiniz genel programlama görevleri. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   Outlook nesne modelini kullanma. Daha fazla bilgi için [Outlook çözümleri](../vsto/outlook-solutions.md).  
  
-   Kullanıcı Arabirimi, Outlook, örneğin, Şeride özel bir sekme ekleme veya kendi özel görev bölmesi oluşturarak özelleştirme. Daha fazla bilgi için [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Derleme ve VSTO eklentileri için Outlook hata ayıklama. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   Outlook için VSTO eklentileri dağıtma. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Outlook çözümleri](../vsto/outlook-solutions.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  