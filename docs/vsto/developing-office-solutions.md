---
title: Office çözümleri geliştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a95c5f5767e227c35763cfaea1e3619093fffda3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833076"
---
# <a name="develop-office-solutions"></a>Office çözümleri geliştirme
  Sonra Visual Studio'da Office geliştirme araçlarını kullanarak bir proje tasarlayın ve proje dosyalarını kurduğunuzda, özel kullanıcı arabirimi (UI) ve kod uygulama hakkında yoğunlaşabilirsiniz başlayabilirsiniz.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümleri için karşılaştırma küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="office-solutions-programming-model"></a>Office çözümleri programlama modeli  
 Office nesne modeli, çeşitli programlayabileceğiniz nesneleri gösterir. Yönetilen kod kullanarak Office çözümleri program her Office birincil birlikte çalışma derlemelerindeki türlerini kullanan kod yazın. Visual Studio'da Office proje şablonları kullanarak oluşturduğunuz çözümlerde, ayrıca projenizde oluşturulan sınıflar karşı doğrudan kod yazma. Daha fazla bilgi için [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Office çözümleri farklı türde program  
 Oluşturmakta olduğunuz çözüm türü projenizde kullanabileceğiniz özellikleri belirler. Örneğin, Windows Forms denetimleri ve genişletilmiş Office denetimleri ekleyebilirsiniz (adlı *konak denetimlerini*) öğeleri sürükleyerek, belge düzeyinde özelleştirmeler için **araç kutusu** Visual Studio'da tasarım zamanında . Bir VSTO eklentisi geliştiriyorsanız, ancak yalnızca bu tür denetimler belgelerine çalışma zamanında kod yazarak ekleyebilirsiniz.  
  
 Çözümleri farklı türleri için özel özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md).  
  
- [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md).  
  
- [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md).  
  
  Office çözümleri ve projeleri oluşturmanıza yardımcı olacak yordamlar planlamanıza yardımcı olacak arka plan bilgileri için bkz. [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)|Office çözümlerinde kod yazma farklı yönlerini açıklar.|  
|[VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)|VSTO eklentileri ve ilgili programlama görevlerini programlama modeli genel bakış sağlar.|  
|[Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)|Belge düzeyi özelleştirmeleri ve ilgili programlama görevlerini programlama modeli genel bakış sağlar.|  
|[Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)|VSTO eklentileri ve belge düzeyi özelleştirmeleri kullanarak kullanıcı Arabirimi, Office uygulamalarını özelleştirebileceğiniz farklı yollarını açıklar.|  
|[Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)|Office çözümlerinde, denetimlere veri bağlama ve verileri belge düzeyi özelleştirmelerdeki önbelleğe alma gibi verilerle çalışabilirsiniz farklı yollarını açıklar.|  
|[Otomatik kaydetme Office çözümlerini nasıl etkiler?](./how-autosave-impacts-office-solutions.md)|Office çözümleri için otomatik kaydetme etkinken yapmanız gerekebilir ayarlamalar açıklar.|
|[Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)|Office çözümleri oluşturma sırasında karşılaşabileceğiniz genel sorunları çözmek için ipuçları sağlar.|  
|[Office'te iş parçacığı desteği](../vsto/threading-support-in-office.md)|Office çözümlerinde birden çok iş parçacığı ile çalışmaya genel bir bakış sağlar.|  
|[Office projelerinde erişilebilirlik](../vsto/accessibility-in-office-projects.md)|Office çözümlerinde kullanılabilir erişilebilirlik özelliklerini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Nasıl yapılır: gelen okuma ve yazma için belge özellikleri](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Nasıl yapılır: Office Çok Dilde Kullanıcı arabirimini hedefleme](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [İzlenecek yol: ilk VSTO eklentinizi Outlook için oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [İzlenecek yol: PowerPoint için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [İzlenecek yol: ilk VSTO eklentinizi projesi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [İzlenecek yol: Word için ilk VSTO eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  