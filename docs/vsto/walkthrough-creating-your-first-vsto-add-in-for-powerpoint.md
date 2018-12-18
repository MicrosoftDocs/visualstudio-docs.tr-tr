---
title: 'İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma'
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
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cea6e61a1afd734ca0ae52a704a2d881371f5817
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882601"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma
  Bu kılavuzda, Microsoft Office PowerPoint için VSTO eklentisi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler uygulamanın kendisinin sunumlar açık olan bağımsız olarak kullanılabilir. Daha fazla bilgi için [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- PowerPoint için PowerPoint VSTO eklentisi proje oluşturma.  
  
- Her yeni slayta bir metin kutusu ekleme için PowerPoint nesne modelini kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Projeyi VSTO eklentisi artık otomatik olarak geliştirme bilgisayarınızda çalıştırılır, böylece temizleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde, bir PowerPoint VSTO eklenti projesini seçin.  
  
6.  İçinde **adı** kutusuna **FirstPowerPointAddIn**.  
  
7.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstPowerPointAddIn** proje ve açılır **ThisAddIn** Düzenleyicisi'nde kod dosyası.  
  
## <a name="write-code-that-adds-text-to-each-new-slide"></a>Her yeni slayta metin ekler kod yazma  
 Ardından, ThisAddIn kod dosyası için kodu ekleyin. Yeni kod, her yeni slayta bir metin kutusu ekleme için PowerPoint nesne modelini kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisAddIn kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisAddIn` sınıfı. Bu sınıf, kodunuz için bir giriş noktası sağlar ve PowerPoint nesne modeline erişim sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Kalanı `ThisAddIn` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisAddIn_Startup` Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri PowerPoint yüklediğinde ve VSTO eklenti bellekten çağrılır. Bu olay işleyicileri, VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, VSTO eklenti tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-text-box-to-each-new-slide"></a>Her yeni slayta bir metin kutusu ekleme  
  
1. ThisAddIn kod dosyasında, aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Bu kod için bir olay işleyicisi tanımlar [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayı <xref:Microsoft.Office.Interop.PowerPoint.Application> nesne.  
  
    Kullanıcı yeni bir slayt etkin sunuya eklediğinde, bu olay işleyicisi metin kutusuna yeni slayt üstüne ekler ve bazı metin metin kutusuna ekler.  
  
    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2. C# kullanıyorsanız, aşağıdaki kodu ekleyin `ThisAddIn_Startup` olay işleyicisi. Bu kod bağlanmak için gereken `Application_PresentationNewSlide` olay işleyicisi ile [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olay.  
  
    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
   Her yeni slayt değiştirmek için aşağıdaki nesneler önceki kod örnekleri kullanın:  
  
-   `Application` Alanını `ThisAddIn` sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.PowerPoint.Application> PowerPoint'ün geçerli örneğini temsil eden nesne.  
  
-   `Sld` Parametresi için olay işleyicisinin [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olay. `Sld` Parametresi bir <xref:Microsoft.Office.Interop.PowerPoint.Slide> yeni slayt temsil eden nesne. Daha fazla bilgi için [PowerPoint çözümleri](../vsto/powerpoint-solutions.md).  
  
## <a name="test-the-project"></a>Test projesi  
 Oluşturun ve projeyi çalıştırın, metin kutusuna bir sunuya eklediğiniz yeni slayt göründüğünü doğrulayın.  
  
### <a name="to-test-the-project"></a>Projeyi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, proje için yapı çıkış klasöründe yerleştirdiğiniz bütünleştirilmiş kod derlenir. Visual Studio ayrıca bulmak ve VSTO eklentisi yükleme PowerPoint sağlayan kayıt defteri girişleri kümesi oluşturur ve VSTO eklenti çalıştırmak, geliştirme bilgisayarının güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
2.  PowerPoint'te, yeni bir slayt etkin sunuya ekleyin.  
  
3.  Aşağıdaki metni slayt üst kısmındaki yeni bir metin kutusu eklendiğini doğrulayın.  
  
     **Bu metin, kod kullanarak eklendi.**  
  
4.  PowerPoint kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye işiniz bittiğinde, VSTO eklentisi derleme, kayıt defteri girişleri ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırın. Aksi halde, PowerPoint geliştirme bilgisayarınızda her açışlarında VSTO eklentisi çalışacaktır.  
  
### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 PowerPoint için temel bir VSTO eklentisi oluşturdunuz, VSTO eklentileri aşağıdaki konulardan geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   PowerPoint için VSTO eklentileri gerçekleştirebileceğiniz genel programlama görevleri. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   PowerPoint nesne modelini kullanma. Daha fazla bilgi için [PowerPoint çözümleri](../vsto/powerpoint-solutions.md).  
  
-   Kullanıcı Arabirimi, PowerPoint, örneğin, Şeride özel bir sekme ekleme veya kendi özel görev bölmesi oluşturarak özelleştirme. Daha fazla bilgi için [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Derleme ve PowerPoint için VSTO eklentileri'hata ayıklama. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   PowerPoint için VSTO eklentileri dağıtma. Daha fazla bilgi için [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  