---
title: 'İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma'
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
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7fb6ece309fb0c5e7c67abf039d2b27a9f04236d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671423"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma
  Bu kılavuzda, Microsoft Office Project için VSTO eklentisi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler uygulamanın kendisinin projeleri açık olan bağımsız olarak kullanılabilir. Daha fazla bilgi için [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir proje VSTO eklentisi projesi oluşturma.  
  
- Yeni bir proje için bir görev eklemek için proje nesne modeli kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Tamamlanmış projeyi VSTO eklentisi artık otomatik olarak geliştirme bilgisayarınızda çalıştırılır, böylece temizleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] veya [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-project-in-visual-studio"></a>Visual Studio'da yeni bir proje oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde seçin **Project 2010 Eklentisi** veya **Project 2013 eklentisi**.  
  
6.  İçinde **adı** kutusuna **FirstProjectAddIn**.  
  
7.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstProjectAddIn** proje ve açılır **ThisAddIn** Düzenleyicisi'nde kod dosyası.  
  
## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Bir projeye yeni bir görev ekler kod yazma  
 Ardından, ThisAddIn kod dosyası için kodu ekleyin. Yeni kod, bir projeye yeni bir görev eklemek için proje nesne modeli kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisAddIn kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisAddIn` sınıfı. Bu sınıf, kodunuz için bir giriş noktası sağlar ve proje nesne modeli erişim sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Kalanı `ThisAddIn` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisAddIn_Startup` Ve `ThisAddIn_Shutdown` olay işleyicileri. Proje yüklediğinde ve VSTO eklenti bellekten olay işleyicilere çağrılır. Bu olay işleyicileri, VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, VSTO eklenti tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-task-to-a-new-project"></a>Yeni bir proje için bir görev eklemek için  
  
1. ThisAddIn kod dosyasında, aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod için bir olay işleyicisi tanımlar `NewProject` olayı `Microsoft.Office.Interop.MSProject.Application` sınıfı.  
  
    Kullanıcı yeni bir proje oluşturduğu zaman, bu olay işleyicisi, projeye bir görev ekler.  
  
    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
   Proje değiştirmek için aşağıdaki nesneler bu kod örneği kullanır:  
  
-   `Application` Alanını `ThisAddIn` sınıfı. `Application` Alan döndürür bir `Microsoft.Office.Interop.MSProject.Application` proje geçerli örneği temsil eden nesne.  
  
-   `pj` NewProject olayı için olay işleyicisi parametresi. `pj` Parametresi bir `Microsoft.Office.Interop.MSProject.Project` projeyi temsil eden nesne. Daha fazla bilgi için [proje çözümleri](../vsto/project-solutions.md).  
  
1.  C# kullanıyorsanız, aşağıdaki kodu ekleyin `ThisAddIn_Startup` olay işleyicisi. Bu kod bağlanır `Application_Newproject` NewProject olayı olay işleyicisi.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
  
## <a name="test-the-project"></a>Test projesi  
 Derleme ve projeyi çalıştırın, ortaya çıkan yeni projede yeni bir görev göründüğünü doğrulayın.  
  
### <a name="to-test-the-project"></a>Projeyi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın. Microsoft Project başlatır ve yeni boş bir proje otomatik olarak açılır.  
  
     Proje oluşturduğunuzda, proje için yapı çıkış klasöründe bulunan bütünleştirilmiş kod derlenir. Visual Studio ayrıca bulmak ve VSTO eklentisi yüklemek projeyi etkinleştirin kayıt defteri girişleri kümesi oluşturur ve VSTO eklenti çalıştırmak, geliştirme bilgisayarının güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [Office çözüm derleme işlemine genel bakış](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).  
  
2.  Yeni bir görev boş projeye eklendiğini doğrulayın.  
  
3.  Aşağıdaki metni göründüğünü doğrulayın **görev adı** görev alanı.  
  
     **Bu metin, kod kullanarak eklendi.**  
  
4.  Microsoft Project kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye işiniz bittiğinde, VSTO eklentisi derleme, kayıt defteri girişleri ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırın. Aksi halde, Microsoft Project geliştirme bilgisayarında her açışlarında VSTO eklentisi çalışacaktır.  
  
### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Bir temel VSTO eklentisi projesi oluşturduğunuz, VSTO eklentileri aşağıdaki konulardan geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   VSTO eklentileri için proje'nda gerçekleştirebileceğiniz genel programlama görevlerini: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   Projenin nesne modelini kullanma: [proje çözümleri](../vsto/project-solutions.md).  
  
-   Derleme ve VSTO eklentileri için proje hata ayıklama: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   VSTO eklentileri için proje dağıtma: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Proje çözümleri](../vsto/project-solutions.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  