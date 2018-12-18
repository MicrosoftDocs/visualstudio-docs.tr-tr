---
title: VSTO eklentileri programlama kullanmaya başlayın
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8136a090dbf5e3c3f86ce9b4ade1321f7b36b829
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858894"
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO eklentileri programlama kullanmaya başlayın
  VSTO eklentileri, Microsoft Office uygulamalarını otomatikleştirmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz. Visual Studio kullanarak oluşturabileceğiniz nasıl VSTO Eklentileri Office çözümlerinin diğer türleri için karşılaştırma hakkında bilgi için bkz [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>VSTO eklentisi projeleri oluşturma  
 VSTO eklentisi proje şablonlarını kullanarak VSTO eklentisi projeleri oluşturma **yeni proje** iletişim kutusu. Bu şablonlar, gerekli bütünleştirilmiş kod başvuruları ve proje dosyaları içerir. Visual Studio içinde Office uygulamalarının çoğu için VSTO eklentisi proje şablonları sağlar.  
  
 Bir VSTO Eklenti projesinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>VSTO eklentisi projeleri geliştirme  
 Bir VSTO eklenti projesi oluşturduğunuzda, Visual Studio otomatik olarak oluşturur bir *ThisAddIn.vb* (içinde [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) veya *ThisAddIn.cs* (C# ') kod dosyası. Bu dosyayı içeren `ThisAddIn` , VSTO eklenti için temel sağlayan sınıf. Bu sınıfın üyeleri, VSTO eklentisi yüklenmedi veya kaldırıldığında, konak uygulamanın nesne modeline erişme ve uygulamanın özelliklerini genişletmek için kodu çalıştırmak için kullanabilirsiniz. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Nesne modelleri kullanarak uygulamaları otomatikleştirme  
 Microsoft Office uygulamasının nesne modellerini bir VSTO eklenti programlayabileceğiniz birçok türü ortaya çıkarır. Bu türler uygulamayı otomatikleştirmek için kullanabilirsiniz. Örneğin, program aracılığıyla oluşturma ve Outlook içinde bir e-posta iletisi göndermek veya belgeyi açın ve içeriği Word'de ekleyin. Konak uygulama kodundaki nesne modeline erişme hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Belirli Microsoft Office uygulamasının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)  
  
-   [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)  
  
-   [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath çözümleri](../vsto/infopath-solutions.md)  
  
-   [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)  
  
-   [Proje çözümleri](../vsto/project-solutions.md)  
  
-   [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Uygulamalar kullanıcı arabirimini özelleştirme  
 Bir VSTO eklentisi kullanarak konak uygulamanın kullanıcı arabirimini özelleştirmek için birçok farklı yol vardır:  
  
- Excel ve Word için belge yönetilen denetimler ekleyebilirsiniz. Daha fazla bilgi için [genişletmek Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO Add-Ins](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
- Uygulama destekliyorsa, Şerit özelleştirebilirsiniz. Daha fazla bilgi için [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
- Uygulama destekliyorsa, özel görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için [özel görev bölmeleri](../vsto/custom-task-panes.md).  
  
- Outlook için özel form bölgesi oluşturabilirsiniz. Daha fazla bilgi için [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
- Tüm Microsoft Office uygulamaları için Windows Forms, VSTO eklenti içinde görüntüleyebilirsiniz.  
  
  Microsoft Office UI uygulamaları özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Sonraki adımlar  
 VSTO eklentileri oluşturma konusunda bilgi almak için aşağıdaki izlenecek yollar bakın:  
  
- [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
  Bu izlenecek yollar size Office geliştirme araçlarını Visual Studio ve programlama modeli için VSTO eklentileri için tanıtır.  
  
  Size bazı yaygın görevleri Office projelerinde yol konuların listesi için bkz. [Office programlarındaki ortak görevler](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)  
  
  