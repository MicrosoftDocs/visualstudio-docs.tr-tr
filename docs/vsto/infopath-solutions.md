---
title: InfoPath çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ae2882cbf38349eac57f1dfb731cc7d717769a4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670864"
---
# <a name="infopath-solutions"></a>InfoPath çözümleri
  Visual Studio, Microsoft Office InfoPath 2013 ve InfoPath 2010 için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. InfoPath Office 2016'da kullanılamıyor.  
  
> [!NOTE]  
>  Office 2016'yı yükledikten olsa bile, yine de bir VSTO eklentisi InfoPath için oluşturabilirsiniz. Yalnızca InfoPath 2013 veya Office 2013 yan yana ile Office 2016 yükleyin.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümleri için karşılaştırma küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
 VSTO eklentileri InfoPath için VSTO eklentileri için diğer Microsoft Office uygulamalarına benzerdir. Bu tür çözümler, uygulama tarafından yüklenen bir derlemeyi oluşur. Son kullanıcılar, bu derlemenin hangi form veya form ne olursa olsun, işlev şablonu açık erişim sağlayabilirler. VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri programlama başlama](../vsto/getting-started-programming-vsto-add-ins.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015, Visual Studio'nun önceki sürümlerinde sağlanan InfoPath form şablon projelerini içermez. Ayrıca, açın veya Visual Studio'nun önceki bir sürümde oluşturulmuş bir InfoPath form şablonu projesi düzenlemek için Visual Studio 2015 kullanamazsınız. Ancak, açın ve bir InfoPath form şablonu projesi uygulamalar için Visual Studio araçları kullanarak düzenleyin. Daha fazla bilgi için [InfoPath 2010 VSTO 2008 projelerde çalışabilirsiniz.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automate-infopath-by-using-an-add-in"></a>InfoPath eklenti kullanarak otomatik hale getirin.  
 InfoPath nesne modelini Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan Office VSTO ek bileşeni erişmek için kullanın `Application` alanını `ThisAddIn` projenizdeki sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.InfoPath.Application> InfoPath'ün geçerli örneğini temsil eden nesne. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Bir VSTO eklentisi InfoPath nesne modelini çağırdığınızda, InfoPath için birincil birlikte çalışma derlemesi türleri kullanın. Birincil birlikte çalışma derlemesi, VSTO eklentisi yönetilen kodda ve InfoPath COM nesne modeli arasında bir köprü görevi görür. InfoPath birincil birlikte çalışma derlemesi içindeki tüm türler tanımlanır <xref:Microsoft.Office.Interop.InfoPath> ad alanı. InfoPath birincil birlikte çalışma derlemesi hakkında daha fazla bilgi için bkz: [birincil birlikte çalışma derlemesi hakkında Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Genel olarak, birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Bir eklentiyi kullanarak InfoPath'in kullanıcı arabirimini özelleştirme  
 InfoPath için VSTO eklentisi oluşturma için birkaç farklı kullanıcı Arabirimi özelleştirme seçeneğiniz vardır. Aşağıdaki tabloda bu seçeneklerden bazıları listelenmektedir.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Özel görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|  
|Özel sekmeler, InfoPath Şeritte ekleyin.|[InfoPath için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 InfoPath ve diğer Microsoft Office uygulamaları özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Microsoft Office InfoPath birincil birlikte çalışma derlemesi hakkında](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [InfoPath 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  