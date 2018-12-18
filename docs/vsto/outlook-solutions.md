---
title: Outlook çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d0a79d48b8ff054e4c7bdb9151f3eefbf287b24
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831243"
---
# <a name="outlook-solutions"></a>Outlook çözümleri
  Visual Studio, Microsoft Office Outlook için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. VSTO eklentileri, Outlook otomatikleştirmek, Outlook özellikleri genişletmek veya Outlook kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz. VSTO eklentileri hakkında daha fazla bilgi için bkz. [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Bir Outlook VSTO eklenti projesinde oluşturma  
 Outlook projeleri kullanarak oluşturma **Outlook eklentisi** proje şablonunda **yeni proje** iletişim kutusu. Bu şablon, gerekli bütünleştirilmiş kod başvuruları ve proje dosyaları içerir.  
  
 Bir VSTO Eklenti projesinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO eklenti programlama modeli  
 Bir Outlook VSTO eklenti projesi oluşturduğunuzda, Visual Studio isimli bir sınıf oluşturur. `ThisAddIn`, çözümünüzün temeli. Bu sınıf kodunuzu yazmanız için bir başlangıç noktası sağlar ve ayrıca Outlook için VSTO eklenti nesne modeli sunar.  
  
 Hakkında daha fazla bilgi için `ThisAddIn` sınıfı ve bir VSTO eklenti, kullanabileceğiniz diğer özellikler bkz [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Outlook nesne modelini kullanarak Outlook otomatikleştirin  
 Outlook nesne modeli, Outlook otomatikleştirmek için kullanabileceğiniz birçok türü ortaya çıkarır. Bu türler ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:  
  
- Program aracılığıyla oluşturun ve e-posta iletisi gönderin.  
  
- Yeni toplantı istekleri gönderme.  
  
- Outlook klasörleri öğeleri arayın.  
  
  Daha fazla bilgi için [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Bir Outlook uygulamasının kullanıcı arabirimini özelleştirme  
  
|Görev|Daha fazla bilgi için|  
|----------|--------------------------|  
|Outlook Inspector Şeride özel sekmeler ekleme|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|  
|Outlook Inspector yerleşik bir sekmede özel gruplar ekleyin.|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|  
|Outlook Inspector görüntülenen özel görev bölmesi ekleme|[Özel görev bölmeleri](../vsto/custom-task-panes.md).|  
|Mevcut Outlook Form genişletir veya form bölgesi ekleme.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|  
  
 Outlook UI ve diğer Microsoft Office uygulamaları özelleştirme hakkında daha fazla bilgi için bkz. [Office UI özelleştirmesi](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)|Outlook nesne modeli tarafından sağlanan nesneler genel bir bakış sağlar.|  
|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|Tasarlamak, geliştirmek ve hata ayıklama form bölgeleri kolaylaştıracak Visual Studio tarafından sağlanan araçları açıklar.|  
|[İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook için VSTO eklentisi oluşturma işlemi gösterilmektedir.|  
|[Outlook 2010 Office geliştirme](http://go.microsoft.com/fwlink/?LinkId=199013)|Burada makaleler bulun ve başvuru belgeleri (Visual Studio kullanarak Office geliştirmeye özgü olmayan) Outlook çözümleri geliştirme hakkında MSDN Kitaplığı'nın alan.|  
  
  