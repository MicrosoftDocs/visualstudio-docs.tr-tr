---
title: Office uygulaması ve proje türüne göre kullanılabilen özellikler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fac14df471b0dfcda1d0bf4763158280211bc33
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672474"
---
# <a name="features-available-by-office-application-and-project-type"></a>Office uygulaması ve proje türüne göre kullanılabilen özellikler
  Visual Studio Proje şablonları, farklı iş senaryoları aşağıdaki türleri dahil olmak üzere Microsoft Office uygulamaları için destek birçok tür içerir:  
  
- Belge düzeyinde özelleştirmeler.  
  
- VSTO eklentileri.  
  
  Tüm uygulamalar, her proje türü kullanabilirsiniz. Örneğin, yalnızca Microsoft Office Word ve Microsoft Office Excel için belge düzeyi projelere kullanılabilir. Benzer şekilde, bazı özellikler yalnızca belirli türlerdeki proje ya da uygulama için kullanılabilir. Örneğin, Eylemler bölmesinde yalnızca belge düzeyinde projelerinde kullanılabilir ve Şerit uzantıları yalnızca bazı uygulamalar için kullanılabilir. Farklı proje türleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Office proje şablonları yalnızca bazı sürümlerinde kullanılabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Daha fazla bilgi için [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Proje türleri farklı Microsoft Office uygulamaları için kullanılabilir  
 Aşağıdaki tabloda, her proje türü ile kullanabileceğiniz uygulamalar gösterilmektedir.  
  
|Proje türleri|Microsoft Office uygulaması|  
|-------------------|----------------------------------|  
|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|  
|VSTO eklentileri|Excel<br /><br /> InfoPath (InfoPath 2013 ve InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proje<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Farklı proje türlerinde kullanılabilir özellikler  
 Proje türleri aşağıdaki tabloda gösterilen her bir özellik sağlar.  
  
|Özellik|Özelliği sağlayan proje türleri|Daha fazla bilgi|  
|-------------|--------------------------------------------|---------------------|  
|Eylemler bölmesi.|Belge düzeyi projeler.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)|  
|ClickOnce dağıtımı.|VS ve belge düzeyi projeler.|[Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)|  
|Özel görev bölmeleri.|VSTO eklentisi projeleri şu uygulamalar için:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Word|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|  
|Özel XML bölümleri.|Belge düzeyi projeler.<br /><br /> Aşağıdaki uygulamalar için uygulama düzeyi projeleri:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)|  
|Veri önbelleği.|Belge düzeyi projeler.|[Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)|  
|Bir nesneyi VSTO eklentisi diğer Microsoft Office çözümleri için kullanıma sunar.|VSTO eklentisi projeleri.|[VSTO eklentilerinde diğer Office Çözümlerinden kod arama](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Aşağıdaki konak denetimleri:<br /><br /> -Grafik<br />-ListObject<br />-NamedRange<br />-İçerik denetimleri<br />-Yer işareti|Belge düzeyi projeler.<br /><br /> VSTO eklentisi projelerine Word ve Excel için.|[Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|  
|Aşağıdaki konak denetimleri:<br /><br /> -Çalışma sayfalarına XMLMappedRange<br />-XMLNode<br />-XMLNodes|Belge düzeyi projeler.|[Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)|  
|Birden çok proje dağıtımı.|Belge düzeyi projeler.<br /><br /> VSTO eklentisi projeleri.|[İzlenecek yol: tek bir ClickOnce yükleyicisi birden çok Office çözümlerini dağıtma](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|  
|Outlook form bölgeleri.|VSTO eklentisi projelerine Outlook.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|  
|Dağıtım sonrası eylemler.|Belge düzeyi projeler.<br /><br /> VSTO eklentisi projeleri.|[İzlenecek yol: bir belgeyi son kullanıcının bilgisayarına ClickOnce yükleme sonrasında Kopyala](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Şerit özelleştirmeleri.|Belge düzeyi projeler.<br /><br /> VSTO eklentisi projeleri şu uygulamalar için:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 ve InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Proje<br />-Visio<br />-Word|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
|Görsel belge Tasarımcısı.|Belge düzeyi projeler.|[Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Konak öğelerine ve denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)   
 [Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  