---
title: Visio çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7fc3f699cd33f2bb45487ca1329d812cfbeb950
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671553"
---
# <a name="visio-solutions"></a>Visio çözümleri
  Visual Studio, Microsoft Office Visio için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. VSTO eklentileri, Visio otomatikleştirmek, Visio özellikleri genişletmek veya Visio kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz.  
  
 VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri programlama başlama](../vsto/getting-started-programming-vsto-add-ins.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md). Microsoft Office ile programlamada yeniyseniz, bkz. [başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **İçin geçerlidir:** Bu konu başlığı altındaki bilgiler Visio 2010 VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio nesne modelini kullanarak Visio otomatikleştirin  
 Visio nesne modeline Visio diyagramları kuruluş şemaları, akış çizelgeleri, proje zaman çizelgesi, ağ şemaları, office alanları ve daha fazlasını oluşturmak için otomatik hale getirmek için kullanabileceğiniz çok sayıda sınıfa kullanıma sunar. API ortak görevleri gerçekleştirmek için kod yazmanıza olanak tanır:  
  
- Yapısı ve konumu şekilleri ve diyagramları metni.  
  
- İş mantığı temelinde şekil davranışını ve kullanıcı girişi yönetin.  
  
- Diyagram görselleştirme kaydırma ve yakınlaştırma gibi denetleyin.  
  
- Uygulama kullanıcı Arabirimi özelleştirin.  
  
- Dış veri Visio'ya içeri aktarma, şekilleri Bağla ve bir sayfada grafiksel olarak görüntüleyebilirsiniz.  
  
  Adım adım yordamları ve kod örnekleri, belgeler ve şekiller çalışmak için Visio nesne modeline kullanma [Visio belgeleriyle çalışma](../vsto/working-with-visio-documents.md) ve [Visio şekilleri ile çalışma](../vsto/working-with-visio-shapes.md).  
  
  Visio nesne modeline bir VSTO eklentisi erişmek için `Application` alanını `ThisAddIn` projenizdeki sınıfı. `Application` Alan döndürür bir `Microsoft.Office.Interop.Visio.Application` Visio'nün geçerli örneğini temsil eden nesne. Daha fazla bilgi için [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
  Visio nesne modeline çağrı, Visio için birincil birlikte çalışma derlemesi (PIA) türleri kullanın. PIA, yönetilen kodda VSTO eklentisi ve Visio COM nesne modeli arasında bir köprü görevi görür. Visio PIA tüm türlerinde tanımlanan `Microsoft.Office.Interop.Visio` ad alanı. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz: [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Visio nesne modeline genel bakış  
 Visio nesne modeline genel bakış bulabilirsiniz [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md), Visio nesne modeli başvurusu ve SDK'ları bağlantılar içerir.  
  
## <a name="customize-the-user-interface-of-visio"></a>Visio kullanıcı arabirimini özelleştirme  
 Visio UI şu özelleştirme seçeneklerini içerir.  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Şeridi özelleştirme.|[Şeride Genel Bakış](../vsto/ribbon-overview.md)|  
  
 UI özelleştirme hakkında daha fazla bilgi için bkz: VBA başvuru belgelerine [Visio.UIObject](/office/vba/api/Visio.UIObject) sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office çözümleri geliştirmesine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)   
 [Visio 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199017)  
  