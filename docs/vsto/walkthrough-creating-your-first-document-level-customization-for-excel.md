---
title: 'İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce16e3c2aca99acf6de9a7ce74c0c2ff46c0dcbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849040"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma
  Bu tanıtıcı kılavuz, Microsoft Office Excel için belge düzeyi özelleştirmeyi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler, yalnızca belirli bir çalışma kitabı açık olduğunda kullanılabilir. Belge düzeyi özelleştirmesi birçok farklı uygulama değişiklik yapmak için kullanamazsınız, örneğin, herhangi bir çalışma kitabını açtığınızda yeni bir Şerit sekmesi görüntüleme gibi.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir Excel çalışma kitabı projesi oluşturma.  
  
- Visual Studio Tasarımcısı'nda barındırılan bir çalışma sayfasına metin ekleniyor.  
  
- Açıldığında özelleştirilmiş bir çalışma sayfasına metin eklemek için Excel nesne modeli kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Gereksiz derleme dosyaları ve güvenlik ayarları, geliştirme bilgisayarınızdan kaldırmak için projeyi temizleniyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Visual Studio'da yeni bir Excel çalışma kitabı projesi oluşturmak için  
  
1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4. Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5. Proje şablonları listesinde, bir Excel VSTO eklenti projesini seçin.  
  
6. İçinde **adı** kutusuna **FirstWorkbookCustomization**.  
  
7. **Tamam**'ı tıklatın.  
  
    **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
8. Seçin **yeni belge oluşturma**, tıklatıp **Tamam**.  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstWorkbookCustomization** proje ve aşağıdaki dosyalar projeye ekler.  
  
   - *FirstWorkbookCustomization*.xlsx - proje Excel çalışma kitabında temsil eder. Tüm çalışma sayfaları ve grafikleri içerir.  
  
   - Sheet1 (*.vb* Visual Basic için dosya veya *.cs* dosya Visual C#)-ilk çalışma kitabındaki için tasarım yüzeyi ve kod sağlayan bir çalışma. Daha fazla bilgi için [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).  
  
   - Sheet2 (*.vb* Visual Basic için dosya veya *.cs* dosya Visual C#)-ikinci çalışma kitabındaki için tasarım yüzeyi ve kod sağlayan bir çalışma.  
  
   - Sheet3 (*.vb* Visual Basic için dosya veya *.cs* dosya Visual C#)-üçüncü çalışma kitabındaki için tasarım yüzeyi ve kod sağlayan bir çalışma.  
  
   - ThisWorkbook (*.vb* Visual Basic için dosya veya *.cs* dosya Visual C#)-tasarım yüzeyini ve çalışma kitabını düzeyi özelleştirmeleri için kod içerir. Daha fazla bilgi için [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).  
  
     Sheet1 kod dosyası Tasarımcısı'nda otomatik olarak açılır.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Tasarımcı sayfalarında kapatıp yeniden yükleme  
 Projenizi geliştirirken, kasıtlı olarak veya yanlışlıkla bir çalışma kitabı veya çalışma Tasarımcısı'nda kapatırsanız, yeniden açabilirsiniz.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Bir çalışma sayfasını tasarımcıda kapatıp yeniden yükleme için  
  
1.  Çalışma kitabına tıklayarak kapatın **Kapat** Tasarımcı penceresinin düğmesine (X).  
  
2.  İçinde **Çözüm Gezgini**, sağ **Sayfa1** kod dosyası ve tıklayın **Görünüm Tasarımcısı**.  
  
     \- veya -  
  
     İçinde **Çözüm Gezgini**, çift **Sayfa1** kod dosyası.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Tasarımcıda bir çalışma sayfasına metin Ekle  
 Tasarımcıda açık olan çalışma değiştirerek kullanıcı arabirimi (UI) özelleştirmenizin tasarlayabilirsiniz. Örneğin, metin hücrelere ekleme, formülleri uygulama veya Excel denetimleri ekleme. Tasarımcıyı kullanma hakkında daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Tasarımcıyı kullanarak çalışma sayfasına metin eklemek için  
  
1.  Tasarımcıda açık çalışma sayfasında hücreyi **A1**, aşağıdaki metni yazın.  
  
     **Bu metin, tasarımcıyı kullanarak eklendi.**  
  
> [!WARNING]  
>  Bu metin satırı hücrenin eklerseniz **A2**, bu örnekte başka bir kod tarafından üzerine yazılır.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına program aracılığıyla metin ekleme  
 Ardından, kod Sayfa1 kod dosyasına ekleyin. Yeni kod, çalışma kitabına metin ikinci satırı eklemek için Excel nesne modeli kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun Sheet1 kod dosyasını içerir:  
  
-   Kısmi bir tanımını `Sheet1` çalışma programlama modelini temsil eder ve Excel nesne modeline erişim sağlar sınıfını. Daha fazla bilgi için [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md) ve [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md). Kalanı `Sheet1` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `Sheet1_Startup` Ve `Sheet1_Shutdown` olay işleyicileri. Bu olay işleyicileri Excel yüklediğinde ve özelleştirmenizi bellekten çağrılır. Bu olay işleyicilerini yüklendiğinde özelleştirme başlatmak ve kaldırıldığında, özelleştirme tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Metnin ikinci bir satır kod kullanarak çalışma sayfasına eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **Sayfa1**ve ardından **kodu görüntüle**.  
  
     Kod dosyasını Visual Studio'da açılır.  
  
2.  Değiştirin `Sheet1_Startup` aşağıdaki kod ile olay işleyicisi. Bu kod, Sayfa1 açıldığında çalışma sayfasına metin ikinci satırı ekler.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Test projesi  
  
### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, çalışma kitabı ile ilişkili bütünleştirilmiş kod derlenir. Visual Studio projesinin yapı çıkış klasöründe çalışma kitabı ve derleme bir kopyasını getirir ve çalıştırmak özelleştirmeyi etkinleştirmek için geliştirme bilgisayarında güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
2.  Çalışma kitabı, aşağıdaki metni gördüğünüzü doğrulayın.  
  
     **Bu metin, tasarımcıyı kullanarak eklendi.**  
  
     **Bu metin, kod kullanarak eklendi.**  
  
3.  Çalışma kitabı kapatın.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye bitirdikten sonra derleme çıktısı klasörü ve yapı işlemi tarafından oluşturulan güvenlik ayarları dosyaları kaldırmanız gerekir.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Tamamlanmış projeyi geliştirme bilgisayarınızda temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Excel için temel bir belge düzeyi özelleştirme oluşturduktan sonra aşağıdaki konulardan özelleştirmeleri geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Belge düzeyi özelleştirmelerde gerçekleştirebileceğiniz genel programlama görevlerini: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
-   Excel için belge düzeyi özelleştirmeleri özgü programlama görevleri: [Excel çözümleri](../vsto/excel-solutions.md).  
  
-   Excel nesne modelini kullanarak: [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).  
  
-   Excel kullanıcı arabirimini özelleştirme, örneğin, göre Şerite özel sekme ekleme veya kendi Eylemler bölmesi oluşturma: [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Excel nesne modeli (örneğin, belgelerdeki yönetilen denetimleri ve Excel denetimleri kullanarak Windows Forms veri bağlama kullanarak mümkün olmayan görevleri gerçekleştirmek için Visual Studio'da Office geliştirme araçları tarafından sağlanan genişletilmiş Excel nesneleri kullanma veri bağlama modelini): [otomatikleştirmek genişletilmiş nesneleri kullanarak Excel](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Derleme ve Excel için belge düzeyi özelleştirmeleri hata ayıklama: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   Excel için belge düzeyi özelleştirmeleri dağıtma: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel çözümleri](../vsto/excel-solutions.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)   
 [Genişletilmiş nesneleri kullanarak Excel'i otomatikleştirmek](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  