---
title: Proje çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be194bb2812f46163a6844a9fa038ee79b5f0e7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677742"
---
# <a name="project-solutions"></a>Proje çözümleri
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] Microsoft Office Project için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. VSTO eklentileri, proje otomatikleştirmek, proje özellikleri genişletmek veya proje kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz.  
  
 VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri programlama başlama](../vsto/getting-started-programming-vsto-add-ins.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md). Microsoft Office ile programlamada yeniyseniz, bkz. [başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Proje projenin nesne modelini kullanarak otomatik hale getirin.  
 Proje nesne modeli proje otomatikleştirmek için kullanabileceğiniz birçok türü ortaya çıkarır. Bu tür, program aracılığıyla oluşturma ve bir projede görevleri değiştirme gibi ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar.  
  
 Bir VSTO eklentisi proje nesne modeli erişmek için `Application` alanını `ThisAddIn` projenizdeki sınıfı. `Application` Alan döndürür bir `Microsoft.Office.Interop.MsProject.Application` proje geçerli örneği temsil eden nesne. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Proje nesne modeline çağrı için birincil birlikte çalışma derlemesi için proje türleri kullanın. Birincil birlikte çalışma derlemesi, yönetilen kodda VSTO eklenti projesinde COM nesne modeli arasında köprü görevi görür. Tüm proje birincil birlikte çalışma derlemesi türlerinde tanımlanan `Microsoft.Office.Interop.MSProject` ad alanı. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Proje nesne modeli belgeleri kullanın  
 Proje nesne modeli hakkında tam bilgi için proje VBA nesne modeli başvurusu başvurabilir. Visual Basic for Applications (VBA) kodundaki sunulur şekilde VBA nesne modeli başvurusu proje nesne modeli listelenmiştir. Daha fazla bilgi için [Project 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türlerine ve üyelerine proje birincil birlikte çalışma derlemesi (PIA) karşılık gelir. VBA nesne modeli başvurusu Takvim nesnesinde, karşılık gelen `Microsoft.Office.Interop.MSProject.Calendar` proje PIA'yı yazın. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da, bunları Visual kullanarak oluşturduğunuz bir proje VSTO eklenti projesinde kullanmak istiyorsanız, Visual Basic veya Visual C# bu başvuruyu VBA kodu Çevir gerekir Studio.  
  
> [!NOTE]  
>  Şu anda proje birincil birlikte çalışma derlemesi için başvuru belgeleri yoktur.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Proje birincil birlikte çalışma derlemesi altyapı türleri  
 Proje PIA'yı kullanan kod yazarken, VBA başvurusunda bahsedilmeyen birçok tür fark edebilirsiniz. Bu ek türleri, yönetilen kod için projenin COM tabanlı nesne modelinde Çevir yardımcı, kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.  
  
 Daha fazla bilgi için [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Proje kullanıcı arabirimini özelleştirme  
 Proje kullanıcı Arabirimi aşağıdaki yollarla özelleştirebilirsiniz.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Proje Şeritteki özel sekmeler ekleme|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
  
 Project UI ve diğer Microsoft Office uygulamalarının özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Project 2010 ve Project Server 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  