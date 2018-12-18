---
title: 'İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma'
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
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf20b3f742bfc5ff6de6af080f3651f9d9027234
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940976"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma
  Bu tanıtıcı kılavuz, Microsoft Office Word için VSTO eklentisi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler uygulamanın kendisinin belgeler açık olduğu bağımsız olarak kullanılabilir.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir sözcük VSTO eklentisi projesi oluşturma.  
  
- Word nesne modeli kaydedildiğinde, belgeye metin ekleme kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Tamamlanmış projeyi VSTO eklentisi artık otomatik olarak geliştirme bilgisayarınızda çalıştırılır, böylece temizleme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Visual Studio'da yeni bir Word VSTO eklenti projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde, bir sözcük VSTO eklenti projesini seçin.  
  
6.  İçinde **adı** kutusuna **FirstWordAddIn**.  
  
7.  **Tamam**'ı tıklatın.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstWordAddIn** proje ve düzenleyicide ThisAddIn kod dosyasını açar.  
  
## <a name="write-code-to-add-text-to-the-saved-document"></a>Kaydedilmiş bir belgeye metin eklemek için kod yazma  
 Ardından, ThisAddIn kod dosyası için kodu ekleyin. Yeni kod, kaydedilen her belge için ortak metin eklemek için Word nesne modeli kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisAddIn kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisAddIn` sınıfı. Bu sınıf, kodunuz için bir giriş noktası sağlar ve Word nesne modeline erişim sağlar. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Kalanı `ThisAddIn` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisAddIn_Startup` Ve `ThisAddIn_Shutdown` olay işleyicileri. Word yüklediğinde ve VSTO eklenti bellekten olay işleyicilere çağrılır. Bu olay işleyicileri, VSTO Eklenti yüklendiğinde başlatmak ve kaldırıldığında, VSTO eklenti tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Bir metin paragrafı sağlandığında kaydedilmiş belgeye eklemek için  
  
1. ThisAddIn kod dosyasında, aşağıdaki kodu ekleyin `ThisAddIn` sınıfı. Yeni kod için bir olay işleyicisi tanımlar <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> bir Belge kaydedildiğinde gerçekleşmek üzereyken olay.  
  
    Kullanıcı bir belgeyi kaydettiğinde, olay işleyicisi belgenin başlangıcında yeni metin ekler.  
  
    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
   > [!NOTE]  
   >  Bu kod, ilk paragrafa erişmek için bir dizin değeri 1 kullanır. <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> koleksiyonu. Visual Basic ve Visual C#, 0 tabanlı diziler kullanmasına karşın, birçok koleksiyonun Word nesne modelinde alt dizi sınırları 1'dir. Daha fazla bilgi için [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
2. C# kullanıyorsanız, aşağıdaki gerekli kodu eklemek `ThisAddIn_Startup` olay işleyicisi. Bu kod bağlanmak için kullanılan `Application_DocumentBeforeSave` olay işleyicisi ile <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay.  
  
    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
   Belge kaydedildiğinde değiştirmek için aşağıdaki nesneler önceki kod örnekleri kullanın:  
  
-   `Application` Alanını `ThisAddIn` sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.Word.Application> Word'ün geçerli örneğini temsil eden nesne.  
  
-   `Doc` Parametresi için olay işleyicisinin <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> olay. `Doc` Parametresi bir <xref:Microsoft.Office.Interop.Word.Document> kaydedilen belgeyi temsil eden nesne. Daha fazla bilgi için [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).  
  
## <a name="test-the-project"></a>Test projesi  
  
### <a name="to-test-the-project"></a>Projeyi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, proje için yapı çıkış klasöründe bulunan bütünleştirilmiş kod derlenir. Visual Studio ayrıca keşfedip VSTO eklenti Word sağlayan kayıt defteri girişleri kümesi oluşturur ve VSTO eklenti çalıştırmak, geliştirme bilgisayarının güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
2.  Word'de etkin belgeyi Kaydet.  
  
3.  Aşağıdaki metni belgeye eklendiğinden emin olun.  
  
     **Bu metin, kod kullanarak eklendi.**  
  
4.  Word'ü kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye işiniz bittiğinde, VSTO eklentisi derleme, kayıt defteri girişleri ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırın. Aksi takdirde, VSTO eklentisi Word geliştirme bilgisayarınızda açık her zaman çalışmaya devam eder.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Tamamlanmış projeyi geliştirme bilgisayarınızda temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Word için basit bir VSTO eklentisi oluşturdunuz, VSTO eklentileri aşağıdaki konulardan geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   VSTO eklentilerinde gerçekleştirebileceğiniz genel programlama görevlerini: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
-   Word VSTO eklentileri belirli programlama görevleri: [Word çözümleri](../vsto/word-solutions.md).  
  
-   Word nesne modelini kullanarak: [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).  
  
-   Word kullanıcı arabirimini özelleştirme, örneğin, göre Şerite özel sekme ekleme veya kendi özel görev bölmesi oluşturuluyor: [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Derleme ve Word için VSTO eklentileri hata ayıklama: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   Word için VSTO eklentileri dağıtma: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word çözümleri](../vsto/word-solutions.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  