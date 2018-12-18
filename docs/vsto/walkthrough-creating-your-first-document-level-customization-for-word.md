---
title: 'İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma'
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
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c5c25163a49e51b0759e57318d6119edec97983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928821"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma
  Bu tanıtıcı kılavuz, Microsoft Office Word için belge düzeyi özelleştirmeyi oluşturma işlemini göstermektedir. Bu tür bir çözüm içinde oluşturduğunuz özellikler, yalnızca belirli bir belge açık olduğunda kullanılabilir. Belge düzeyi özelleştirmesi birçok farklı uygulama değişiklik yapmak için kullanamazsınız, örneğin, herhangi bir belge açık olduğunda, yeni bir Şerit sekmesi görüntüleme gibi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir Word belgesi projesi oluşturma.  
  
- Visual Studio Tasarımcısı'nda barındırılan belgeye metin ekleme.  
  
- Açıldığında, özelleştirilmiş belgeye metin ekleme Word nesne modeli kullanan kod yazma.  
  
- Geliştirme ve test etmek için proje çalıştırma.  
  
- Gereksiz derleme dosyaları ve güvenlik ayarları Geliştirme bilgisayarınızdan kaldırmak için projeyi temizleniyor.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Visual Studio'da yeni bir Word belgesi projesi oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**ve ardından **Office/SharePoint**.  
  
4.  Genişletilmiş altında **Office/SharePoint** düğümünü **Office eklentilerini** düğümü.  
  
5.  Proje şablonları listesinde, bir sözcük VSTO belgesi projesini seçin.  
  
6.  İçinde **adı** kutusuna **FirstDocumentCustomization**.  
  
7.  **Tamam**'ı tıklatın.  
  
     **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
8.  Seçin **yeni belge oluşturma**, tıklatıp **Tamam**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturur **FirstDocumentCustomization** proje ve ekler **FirstDocumentCustomization** belge ve projeye ThisDocument kod dosyası. **FirstDocumentCustomization** belge otomatik olarak tasarımcıda açılır.  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>Belgeyi tasarımcıda kapatıp yeniden yükleme  
 Projenizi geliştirirken, kasıtlı olarak veya yanlışlıkla belgeyi tasarımcıda kapatırsanız, yeniden açabilirsiniz.  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Belgeyi tasarımcıda kapatıp yeniden yükleme için  
  
1.  Tıklayarak belgeyi Kapat **Kapat** Tasarımcı penceresinin düğmesine (X).  
  
2.  İçinde **Çözüm Gezgini**, sağ **ThisDocument** kod dosyası ve tıklayın **Görünüm Tasarımcısı**.  
  
     \- veya -  
  
     İçinde **Çözüm Gezgini**, çift **ThisDocument** kod dosyası.  
  
## <a name="add-text-to-the-document-in-the-designer"></a>Belgeyi tasarımcıda metin ekleme  
 Belgeyi tasarımcıda açık değiştirerek kullanıcı arabirimi (UI) özelleştirmenizin tasarlayabilirsiniz. Örneğin, metin, tablolar veya Word denetimleri ekleyebilirsiniz. Tasarımcıyı kullanma hakkında daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Tasarımcıyı kullanarak, belgeye metin ekleme  
  
1.  Tasarımcıda açık belgede, aşağıdaki metni yazın.  
  
     **Bu metin, tasarımcıyı kullanarak eklendi.**  
  
## <a name="add-text-to-the-document-programmatically"></a>Belgesine program aracılığıyla metin ekleme  
 Ardından, kod ThisDocument kod dosyasına ekleyin. Yeni kod, ikinci paragrafa metin belgesine eklemek için Word nesne modeli kullanır. Varsayılan olarak, aşağıdaki oluşturulan kodun ThisDocument kod dosyasını içerir:  
  
-   Kısmi bir tanımını `ThisDocument` belgenin programlama modelini temsil eder ve Word nesne modeline erişim sağlar sınıfını. Daha fazla bilgi için [belge konak öğesi](../vsto/document-host-item.md) ve [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md). Kalanı `ThisDocument` sınıfı değiştirmemeniz gereken bir gizli kod dosyasında tanımlanır.  
  
-   `ThisDocument_Startup` Ve `ThisDocument_Shutdown` olay işleyicileri. Belge açılır ve bu olay işleyiciler çağırılır. Bu olay işleyicilerini belge açıldığında özelleştirme başlatmak ve belge kapatıldığında, özelleştirme tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Kod kullanarak ikinci bir metin paragrafı sağlandığında belgeye eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisDocument**ve ardından **kodu görüntüle**.  
  
     Kod dosyasını Visual Studio'da açılır.  
  
2.  Değiştirin `ThisDocument_Startup` aşağıdaki kod ile olay işleyicisi. Belge açıldığında, bu kod, ikinci bir metin paragrafı sağlandığında belgeye ekler.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Bu kod, ilk paragrafa erişmek için dizin değeri 1 kullanır. <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> özelliği. Visual Basic ve Visual C#, 0 tabanlı diziler kullanmasına karşın, birçok koleksiyonun Word nesne modelinde alt dizi sınırları 1'dir. Daha fazla bilgi için [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="test-the-project"></a>Test projesi  
  
### <a name="to-test-your-document"></a>Belgenizi test etmek için  
  
1.  Tuşuna **F5** oluşturup projeyi çalıştırın.  
  
     Proje oluşturduğunuzda, belge ile ilişkili bütünleştirilmiş kod derlenir. Visual Studio projesi yapı çıkış klasöründe bir kopyasını belge ve derleme koyar ve çalıştırmak özelleştirmeyi etkinleştirmek için geliştirme bilgisayarında güvenlik ayarlarını yapılandırır. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
2.  Belgede, aşağıdaki metni gördüğünüzü doğrulayın.  
  
     **Bu metin, tasarımcıyı kullanarak eklendi.**  
  
     **Bu metin, kod kullanarak eklendi.**  
  
3.  Belgeyi Kapat.  
  
## <a name="clean-up-the-project"></a>Projeyi Temizle  
 Bir projeyi geliştirmeye bitirdikten sonra derleme çıktısı klasörü ve yapı işlemi tarafından oluşturulan güvenlik ayarları dosyaları kaldırmanız gerekir.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Tamamlanmış projeyi geliştirme bilgisayarınızda temizlemek için  
  
1.  Visual Studio'da üzerinde **derleme** menüsünde tıklatın **çözümü Temizle**.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Word için basit bir belge düzeyi özelleştirmesi oluşturduktan sonra aşağıdaki konulardan özelleştirmeleri geliştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Belge düzeyi özelleştirmelerde gerçekleştirebileceğiniz genel programlama görevlerini: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).  
  
-   Word için belge düzeyi özelleştirmeleri özgü programlama görevleri: [Word çözümleri](../vsto/word-solutions.md).  
  
-   Word nesne modelini kullanarak: [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).  
  
-   Word kullanıcı arabirimini özelleştirme, örneğin, göre Şerite özel sekme ekleme veya kendi Eylemler bölmesi oluşturma: [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
-   Word nesne modeli (örneğin, belgelerdeki yönetilen denetimleri ve Word denetimleri verilere kullanarak Windows Forms veri bağlama kullanarak mümkün olmayan görevleri gerçekleştirmek için Visual Studio'da Office çözümleri tarafından sağlanan genişletilmiş Word nesneleri kullanma model bağlama): [otomatikleştirmek genişletilmiş nesneleri kullanarak Word'ü](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Derleme ve Word için belge düzeyi özelleştirmeleri hata ayıklama: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
-   Word için belge düzeyi özelleştirmeleri dağıtma: [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word çözümleri](../vsto/word-solutions.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)   
 [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)   
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)  
  
  