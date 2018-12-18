---
title: "Nasıl yapılır: Visual Studio'da Office projeleri oluşturma"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6930ce085405c010e59e13adb8a3d380cff28d0e
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672775"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da Office projeleri oluşturma
  Kullanabileceğiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSTO eklentisi ve belge düzeyi özelleştirmeleri Microsoft Office uygulamaları için. Bu proje türleri hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Bir VSTO eklenti projesi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**. Tümleşik geliştirme ortamınız (IDE) kullanmak için ayarlanmış olup olmadığını [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Geliştirme Ayarları'nda **dosya** menüsünde seçin **yeni** > **proje**.  
  
    **Yeni proje** iletişim kutusu görüntülenir.  
  
   > [!NOTE]  
   >  Office projeleri hedef [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] varsayılan olarak. Daha fazla bilgi için [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).  
  
2. Şablonlar bölmesinde, kullanmak istediğiniz dil için düğümü genişletin **Office/SharePoint**.  
  
3. Seçin **Office eklentilerini** düğümü.  
  
4. Proje şablonları listesinde, VSTO eklentisi proje şablonu seçin. Kullanılabilir VSTO eklenti projesi şablonlarının bir listesi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Proje şablonları görünür değilse seçtiğinizde **Office eklentilerini** düğümünün olduğundan emin olun **.NET Framework 4** veya daha sonra iletişim kutusunun üstündeki birleşik giriş kutusunda seçilir. Office proje şablonları, her iki .NET Framework sürümleri için görülebilir.  
  
5. İçinde **adı** proje için bir ad yazın. Varsayılan olarak, proje adı çözüm adı olarak da kullanılır.  
  
6. İçinde **konumu** kutusunda, projeyi oluşturmak istediğiniz yolu girin. Mutlak ve Evrensel Adlandırma Kuralı (UNC) yollarını kullanabilirsiniz. HTTP, FTP veya diğer protokol yollarını kullanmayın.  
  
    Konumlar aşağıdaki biçimlere sahiptir:  
  
   * [*sürücü*\]\:  
  
   * \\\\*Sunucu*\\*paylaşımı*  
  
     Konumda şu karakterleri kullanmayın:  
  
   * Yıldız işareti (*)  
  
   * Dikey çubuk (|)  
  
   * İki nokta üst üste (:) (Sürücü harfini hariç).  
  
   * Çift tırnak işareti (") (boşluk içeren yollar gereksinim tırnak işaretleri.)  
  
   * Küçüktür (\<)  
  
   * Büyüktür (>)  
  
   * Soru işareti (?)  
  
   * Yüzde işareti (%)  
  
7. Seçin **Tamam** düğmesi.
  
    > [!NOTE]  
    >  Eklenti projeleri, oluşturulduğunda daima kaydedilir. Geçici proje olarak oluşturulamazlar. Geçici projeler hakkında daha fazla bilgi için bkz: [geçici projeler](https://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Belge düzeyi özelleştirme projesi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**. IDE'nizi Visual Basic geliştirme ayarlarını kullanmaya ayarlanmışsa **dosya** menüsünde seçin **yeni** > **proje**.  
  
    **Yeni proje** iletişim kutusu görüntülenir.  
  
   > [!NOTE]  
   >  Office projeleri hedef [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] varsayılan olarak.  Daha fazla bilgi için [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).  
  
2. Şablonlar bölmesinde, kullanmak istediğiniz dil için düğümü genişletin **Office/SharePoint**.  
  
3. Seçin **Office eklentilerini** düğümü.  
  
4. Proje şablonları listesinde, bir belge düzeyi projesi şablonu seçin. Kullanılabilir belge düzeyi projesi şablonlarının bir listesi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Proje şablonları görünür değilse seçtiğinizde **Office eklentilerini** düğümünün olduğundan emin olun **.NET Framework 4** veya daha sonra iletişim kutusunun üstündeki birleşik giriş kutusunda seçilir. Office proje şablonları, her iki .NET Framework sürümleri için görülebilir.  
  
5. İçinde **adı** proje için bir ad yazın. Varsayılan olarak, bu ad belge için de kullanılır. IDE'nizi Visual C# geliştirme ayarlarını veya genel geliştirme ayarlarını kullanmaya ayarlanmışsa, konum ve çözüm adı da girin.  
  
   > [!NOTE]  
   >  Proje konumunun yolunda veya proje isminde temsilci karakterleri kullanamazsınız. Ayrıca, çevrimdışı kullanım için bir çözüm dağıtmayı planlıyorsanız proje adındaki karakterler HTTP protokolü belirtimlerine uymalıdır.  
  
6. Seçin **Tamam** düğmesi.  
  
    **Office Project Sihirbazı için Visual Studio Araçları** açılır.  
  
7. Seçin **yeni belge oluşturma** çözümü için yeni bir belge oluşturmak istiyorsanız **mevcut belgeyi kopyalamak** var olan bir belgeyi özelleştirmek istiyorsanız.  
  
    Yeni bir belge oluşturursanız, ismi belirtin **adı** kutusunda ve kullanarak belgenin biçimini seçin **biçimi** kutusu. Kullanılabilir biçimler hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md).  
  
    Var olan bir belgeyi kullanıyorsanız, belgede konumunu **mevcut belgenin tam yolu** kutusu. Mutlak veya UNC yollarını kullanabilirsiniz. HTTP, FTP veya diğer protokol yollarını kullanmayın.  
  
    Konumlar aşağıdaki biçimlere sahiptir:  
  
   - [*sürücü*\]\:  
  
   - \\\\*Sunucu*\\*paylaşımı*  
  
     Konumda şu karakterleri kullanmayın:  
  
   - Yıldız işareti (*)  
  
   - Dikey çubuk (|)  
  
   - İki nokta üst üste (:) (Sürücü harfini hariç).  
  
   - Çift tırnak işareti (") (boşluk içeren yollar gereksinim tırnak işaretleri.)  
  
   - Küçüktür (\<)  
  
   - Büyüktür (>)  
  
   - Soru işareti (?)  
  
   - Yüzde işareti (%)  
  
   > [!NOTE]  
   >  Varolan bir belgeyi kullanıyorsanız, bir [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] proje, yalnızca programında oluşturulan veya buna dönüştürülen belgeleri kullanın [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Benzer şekilde, bir sözcükteki var olan bir belgeyi kullanıyorsanız, 2010 projesinde, yalnızca programında oluşturulan veya Word 2010 dönüştürülen belgeleri kullanın. Word'ün önceki bir sürümde oluşturulmuş bir belgeyi kullanıyorsanız, bazı özellikler belgesinde devre dışı bırakılır. Bu özellikleri kullanan kod yazmayı denerseniz projenizde hatalarla karşılaşabilirsiniz. Bir belgeyi dönüştürmek için açılır [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ve Word 2010 üzerinde **dosya** sekmesini Şerit üzerinde **bilgisi** > **Dönüştür**.  
  
8. Seçin **son**.  
  
9. Aşağıdaki durumlarda Word'de Güven Merkezi'ndeki güvenilir konum listesine proje klasörünü ve alt klasörlerini ekleyin:  
  
   - Temel alan bir Word belgesi oluşturuyorsunuz bir *.docm* dosya ve belge bir VBA projesi içermekte ya da barındıran Windows Forms denetimleri. Proje klasörünü güvenilir konum listesine eklemek belgenin tasarım zamanında beklenildiği gibi çalıştığından emin olun yardımcı olur.  
  
   - Temel alan bir Word Şablonu proje oluşturmakta olduğunuz bir *.dotx* dosya. Böylece çalıştırın ve proje hatalarını ayıklamaya proje klasörünü güvenilir konum listesine eklemeniz gerekir.  
  
     Belgeyi güvenilir konumlara eklemek hakkında daha fazla bilgi için Microsoft Office çevrimiçi web sitesine bakın [oluşturma, kaldırma veya değişiklik dosyalarınız için güvenilen bir konum](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)   
 [Office çözümlerinin işbirlikçi geliştirmesi](../vsto/collaborative-development-of-office-solutions.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
