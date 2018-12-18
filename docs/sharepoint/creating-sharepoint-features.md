---
title: SharePoint özellikleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56bc4dbd50bedc15fcf6c69cbc334fe09c6094cc
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325605"
---
# <a name="create-sharepoint-features"></a>SharePoint özellikleri oluşturma
  Daha kolay dağıtım için ilgili SharePoint Proje öğeleri gruplandırmak için bir SharePoint özelliğini kullanabilirsiniz. Özellikleri oluşturma kapsamlarını ayarlayın ve diğer özellikleri SharePoint özelliği Designer kullanarak bağımlılıklar olarak işaretleyin. Tasarımcı aynı zamanda her bir özelliğin tanımlayan bir XML dosyasıdır bir bildirim oluşturur.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint çözüm özellik ekleme
 Çözüm Gezgini veya paketleme Gezgini'ni kullanarak, bir özellik için SharePoint çözüm ekleyebilirsiniz. Bir özellik eklemek için aşağıdaki yöntemlerden birini kullanabilirsiniz.  
  
-   İçinde **Çözüm Gezgini**, kısayol menüsünü açın **özellikleri**ve ardından **ekleme özelliği**.  
  
-   İçinde **paketleme Gezgini'ni**, paket için kısayol menüsünü açın ve ardından **ekleme özelliği**.  
  
## <a name="using-the-feature-designer"></a>Özellik Tasarımcısı'nı kullanarak
 Bir SharePoint çözüm bir veya daha fazla SharePoint Çözüm Gezgini'nde özelliği düğümü altında gruplanmış özellikler içerebilir. Her bir özelliğin kendi sahip **özelliği Designer** özellik özellikleri özelleştirmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md). Özellikleri birbirinden ayırt etmek için başlık, açıklama, sürüm ve kapsam gibi özelliği özelliklerini yapılandırabilirsiniz.  
  
### <a name="feature-designer-options"></a>Özellik Tasarımcı seçenekleri
 Bir özellik oluşturduktan sonra özellik Tasarımcısı'nı özelleştirmek için kullanabilirsiniz.  
  
 Aşağıdaki tabloda özelliği Tasarımcısı'nda görüntülenen özellik özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|Başlık|İsteğe bağlı. Özelliğin varsayılan başlık kümesine *SolutionName* *FeatureName*.|  
|Açıklama|İsteğe bağlı. SharePoint özelliğinin açıklaması.|  
|Kapsam|Gerekli. Bir özellik kullanarak oluşturduysanız **Çözüm Gezgini**, kapsam Web'e varsayılan olarak ayarlanır.<br /><br /> -Grup: tüm sunucu grubu için özelliği etkinleştirin.<br /><br /> -Site: site koleksiyonundaki tüm web siteleri için özelliği etkinleştirin.<br /><br /> -Web: belirli bir web sitesi için özelliği etkinleştirin.<br /><br /> -WebApplication: bir web uygulamasındaki tüm web siteleri için özelliği etkinleştirin.|  
|Çözüm öğeleri|Özelliği için eklenen tüm SharePoint öğeleri.|  
|Öğe özelliği|Özelliği için eklenene SharePoint Proje öğeleri.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Ekleme ve SharePoint Proje öğeleri kaldırma
 Dağıtım için bir SharePoint özelliğini eklemek istediğiniz hangi SharePoint Proje öğeleri seçebilirsiniz. Kullanım **özelliği Designer** eklemek ve özelliklerine öğe kaldırmak ve özellik bildirimini görüntülemek için. Daha fazla bilgi için bkz: [nasıl yapılır: SharePoint özelliklerine öğe ekleyip](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Özellik bağımlılıkları ekleme
 Böylece, özellik etkinleştirilmeden önce SharePoint sunucusu bazı özellikleri etkinleştirir özellik bildirimi yapılandırabilirsiniz. İşlev veya veri için diğer özellikleri, SharePoint özelliği bağlıdır, örneğin, SharePoint sunucusu ilk olarak, özellik bağlıdır özelliklerinden herhangi birini etkinleştirmek deneyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: özellik bağımlılıkları ekleyip](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Nasıl yapılır: SharePoint özelliklerine öğe ekleyip](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Nasıl yapılır: özellik bağımlılıkları ekleyip](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  
