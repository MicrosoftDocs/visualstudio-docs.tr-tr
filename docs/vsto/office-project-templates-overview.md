---
title: Office proje şablonlarına genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1ad35b9aecc9e7559902104f447cbbec3415b49
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934333"
---
# <a name="office-project-templates-overview"></a>Office proje şablonlarına genel bakış
  Visual Studio'da Microsoft Office geliştirici araçları, aşağıdaki Office çözüm türlerini oluşturmak için proje şablonları içerir:  
  
- [Belge düzeyinde özelleştirmeler](#DocLevel)  
  
- [VSTO eklentileri](#AppLevel)  
  
  Office çözümlerinin bu türlerinin ayrıntılı bir karşılaştırması için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
  Office proje şablonları kullanılabilir **yeni proje** iletişim kutusunun **Office** düğümünün **Visual C#** ve **Visual Basic**dil düğümleri. Her şablon, derleme başvuruları ve hata ayıklama ayarları dahil olmak üzere, hedef uygulamaya uygun yapılandırmaya sahip bir proje oluşturur.  
  
  Her proje, belirli bir çözüm türü üzerinde çalışmaya başlamanızı sağlayacak dosyaları ve kodu sunar. Her bir proje için üretilen kod, başlangıç ve kapatma olayı işleyicilerini içerir. Yüklendiğinde çözümünüzü başlatmak ve kaldırıldığında çözümünüzü temizlemek için, bu olay işleyicilerine kod ekleyebilirsiniz. Daha fazla bilgi için [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md) ve [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Office geliştirme araçları Visual Studio'nun belirli sürümlerinde yer alır. Daha fazla bilgi için [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a> Belge düzeyinde özelleştirmeler  
 **Office** düğümünde **yeni proje** iletişim kutusu başlamanızı sağlayacak şu proje şablonlarını Word ve Excel için belge düzeyi özelleştirmeleri oluşturmaya sunar:  
  
- **Word 2013 ve 2016 VSTO belgesi**  
  
- **Word 2013 ve 2016 VSTO şablonu**  
  
- **Excel 2013 ve 2016 VSTO çalışma kitabı**  
  
- **Excel 2013 ve 2016 VSTO şablonu**  
  
- **Word 2010 VSTO belgesi**  
  
- **Word 2010 VSTO şablonu**  
  
- **Excel 2010 VSTO çalışma kitabı**  
  
- **Excel 2010 VSTO şablonu**  
  
  Word Belgesi ve Excel Çalışma Kitabı proje şablonları, belirli bir belgeyi veya çalışma sayfasını temel alan bir çözüm oluşturmaya başlamanızı sağlayacak kodu sunar. Bu tür çözümlerde kodunuz sadece Word veya Excel'de ilişkili belge açıksa çalışır.  
  
  Word Şablonu ve Excel Şablonu proje şablonları, Word Belgesi ve Excel Çalışma Kitabı proje şablonlarıyla aynı şekilde davranır. Bununla birlikte, Word Şablonu ve Excel Şablonu proje şablonları, kullanıcıların çözümünüzdeki özelleştirilmiş şablonun yeni yerel belge veya çalışma kitabı kopyalarını oluşturmasını kolaylaştırır. Çözümünüzdeki özellikler, kullanıcının şablondan oluşturduğu yeni belgeden kullanılabilir.  
  
> [!NOTE]  
>  Yönetilen kod uzantılarına başvuran Word şablonları genel VSTO eklentileri kullanılamaz. Şablon Word'ün Başlangıç dizininden yüklenirse, derleme çağrılmaz. Daha fazla bilgi için [genel şablonların ve Excel eklentilerinin (.xla dosyaları) sınırlamaları](#Limitations)  
  
 Bu proje türleriyle çalışmaya başlama hakkında bilgi için aşağıdaki konulara bakın:  
  
-   [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)  
  
-   [Word çözümleri](../vsto/word-solutions.md)  
  
-   [Excel çözümleri](../vsto/excel-solutions.md)  
  
-   [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> VSTO eklentileri  
 **Office/SharePoint** düğümünde **yeni proje** iletişim kutusu başlamanızı sağlayacak şu proje şablonlarını sunar VSTO eklentileri oluşturma.  
  
- **Excel 2013 ve 2016 VSTO eklentisi**  
  
- **InfoPath 2013 VSTO eklentisi**  
  
- **Outlook 2013 ve 2016 VSTO eklentisi**  
  
- **PowerPoint 2013 ve 2016 eklentisi**  
  
- **Project 2013 ve 2016 eklentisi**  
  
- **Visio 2013 ve 2016 eklentisi**  
  
- **Word 2013 ve 2016 eklentisi**  
  
- **Excel 2010 Eklentisi**  
  
- **InfoPath 2010 Eklentisi**  
  
- **Outlook 2010 Eklentisi**  
  
- **PowerPoint 2010 Eklentisi**  
  
- **Project 2010 Eklentisi**  
  
- **Visio 2010 Eklentisi**  
  
- **Word 2010 Eklentisi**  
  
  Bu proje şablonlarından birini temel alan bir proje oluşturduğunuzda, çözümünüzdeki kod ilişkili uygulama açıldığı zaman çalışır. Belge düzeyinde projelerin aksine, kodunuz tek bir belgeyle ilişkili değildir.  
  
  Bu proje türleriyle çalışmaya başlama hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)  
  
- [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)  
  
- [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>Belge ve şablon çözümleri  
 Word belgesi veya Excel çalışma kitabı etrafında bir çözüm tasarladığınızda, bu belgeyi kullanıcılarınıza sunmanın en iyi yoluna karar vermelisiniz.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bazı durumlarda her kullanıcıya belgenin bir kopyasını vermek isteyebilirsiniz. Bu durumda, çözümünüzü Excel veya Word belgesi projesi olarak oluşturun.  
  
 Diğer durumlarda, bir şablonu sunucuda kullanıma açmak isteyebilirsiniz; böylelikle her kullanıcı şablonu açıp yerel kopyasını belge olarak kaydedebilir. Bu durumda, çözümünüzü Excel veya Word şablonu projesi olarak oluşturun.  
  
## <a name="comparison"></a>Karşılaştırma  
 Aşağıdaki tabloda belgeler ile şablonlar arasındaki farklar ana hatlarıyla açıklanmıştır.  
  
|Belgeler|Şablonlar|  
|---------------|---------------|  
|Kullanıcılar, salt okunur olmadığı sürece belgeyi açıp değiştirebilir. Kaydedilen tüm değişiklikler özgün belgede tutulur.|Kullanıcılar yeni bir belge olarak yerel kopya oluşturmak üzere şablonu açabilir. Özel izinler verilmediği sürece özgün belgede değişiklik yapamazlar.|  
|Belge açılınca <xref:Microsoft.Office.Tools.Word.Document.Open> olay.|Şablon açılınca <xref:Microsoft.Office.Tools.Word.Document.New> olay.|  
  
##  <a name="Limitations"></a> Genel şablonların ve Excel eklentilerinin (.xla dosyaları) sınırlamaları  
 Belgelere, çalışma kitapları ve şablonlar, genel şablon veya Excel VSTO eklentileri (.xla dosyaları) düzgün çalışmayabilir.  
  
## <a name="word-templates"></a>Word şablonları  
 Bir Microsoft Office Word şablonunun yönetilen kod uzantıları varsa, şablonun bir genel şablon olarak iliştirilmesi veya Word'ün başlangıç dizininden yüklenmesi durumunda proje derlemesi çağrılmaz. Ayrıca belge, bir Office çözümünün parçası olan şablonun biçimini tanımaz.  
  
## <a name="excel-add-ins-xla-files"></a>Excel eklentilerinin (.xla dosyaları)  
 Office için bir Excel VSTO eklentisi oluşturma projesi yok (*.xla* dosyası). Bir çalışma kitabını .xla dosyası olarak kaydetmek mümkündür, ancak bu desteklenen bir işlem değildir ve önerilmez. Yönetilen kod uzantıları bir çalışma kitabını kaydetmeniz, bir **Microsoft Office Excel Eklentisi (\*.xla)** dosyasını seçebileceğiniz içinde **eklentileri** başka bir çalışma kitabına uygulamak için iletişim kutusu. Bazı durumlarda, kodunuzu, VSTO eklentisi uygulanır, ancak Office çözümünün böyle bir kullanımı desteklenmiyor sonra hedef çalışma kitabında çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Excel için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Word için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  