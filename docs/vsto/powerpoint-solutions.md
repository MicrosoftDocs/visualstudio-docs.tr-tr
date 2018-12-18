---
title: PowerPoint çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7a2775526a088129060fc6375958b08cf6b19eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906565"
---
# <a name="powerpoint-solutions"></a>PowerPoint çözümleri
  Visual Studio, Microsoft Office PowerPoint için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. VSTO eklentileri, PowerPoint otomatikleştirmek, PowerPoint özellikleri genişletmek veya PowerPoint kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz.  
  
 VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri programlama başlama](../vsto/getting-started-programming-vsto-add-ins.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md). Microsoft Office ile programlamada yeniyseniz, bkz. [başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [: oluşturma bir eklenti Microsoft PowerPoint için bunu nasıl?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint PowerPoint nesne modelini kullanarak otomatik hale getirin.  
 PowerPoint nesne modeli, PowerPoint otomatikleştirmek için kullanabileceğiniz birçok türü ortaya çıkarır. Bu türler ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:  
  
- Program aracılığıyla oluşturma ve sunu biçimlendirin.  
  
- Ekleyip slaytları sunuları izleyebilirsiniz.  
  
- Ekleyin veya bir slayt diyagramdaki şekilleri değiştirin.  
  
  Bir VSTO eklentisi PowerPoint nesne modeli erişmek için `Application` alanını `ThisAddIn` projenizdeki sınıfı. `Application` Alan döndürür bir <xref:Microsoft.Office.Interop.PowerPoint.Application> PowerPoint'ün geçerli örneğini temsil eden nesne. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
  PowerPoint nesne modeline çağrı, PowerPoint birincil birlikte çalışma derlemesi türleri kullanın. Birincil birlikte çalışma derlemesi, VSTO eklentisi yönetilen kodda ve PowerPoint COM nesne modeli arasında bir köprü görevi görür. PowerPoint birincil birlikte çalışma derlemesi içindeki tüm türler tanımlanır <xref:Microsoft.Office.Interop.PowerPoint> ad alanı. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> PowerPoint nesne modeli belgeleri kullanın  
 PowerPoint nesne modeli hakkında tam bilgi için PowerPoint birincil birlikte çalışma derlemesi (PIA) başvuru ve VBA nesne modeli başvurusu başvurabilir.  
  
### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma bütünleştirilmiş kod başvurusu  
 PowerPoint PIA başvuru belgeleri, PowerPoint birincil birlikte çalışma derlemesi türleri açıklanmaktadır. Bu belge aşağıdaki konumdan kullanılabilir: [PowerPoint 2010 birincil birlikte çalışma bütünleştirilmiş kod başvurusu](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Sınıfları ve arabirimleri arasındaki farkı PIA hem de PIA olayların nasıl uygulandığı, örneğin PowerPoint PIA tasarımı hakkında daha fazla bilgi için bkz: [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu  
 Visual Basic for Applications (VBA) kodundaki sunulur şekilde VBA nesne modeli başvurusu PowerPoint nesne modeli listelenmiştir. Daha fazla bilgi için [PowerPoint 2010 nesne modeli başvurusu](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Tüm nesnelerin ve üyelerin VBA nesne modeli başvurusu türlerine ve üyelerine PowerPoint birincil birlikte çalışma derlemesi (PIA) karşılık gelir. Örneğin, sunu nesnesi VBA nesne modeli başvurusu için karşılık gelen <xref:Microsoft.Office.Interop.PowerPoint.Presentation> PowerPoint PIA'yı yazın. VBA nesne modeli başvurusu çoğu özellikleri, yöntemleri ve olayları için kod örnekleri sağlasa da, bunları kullanarak oluşturduğunuz bir PowerPoint VSTO eklenti projesinde kullanmak istiyorsanız, Visual Basic veya Visual C# bu başvuruyu VBA kodu Çevir gerekir Visual Studio.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>PowerPoint kullanıcı arabirimini özelleştirme  
 PowerPoint kullanıcı Arabirimi aşağıdaki yollarla değiştirebilirsiniz.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Özel görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|  
|Şeride özel sekmeler ekleme|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
|Şeritteki yerleşik bir sekmeyi özel gruplar ekleyin.|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 PowerPoint UI ve diğer Microsoft Office uygulamaları özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  