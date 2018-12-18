---
title: SharePoint Proje sistemini genişletme | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 028e7aab10ae1ee1de452e69c8148dac099039d0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326793"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint Proje sistemini genişletme
  SharePoint çözümlerini Visual Studio Proje şablonları ve öğe şablonları kümesi kullanarak oluşturabilirsiniz. Bu şablonlar birçok geliştirme senaryosu gereksinimlerini ancak burada size gereken işlevsellik sağlamıyorsa bazı durumlarda fark edebilirsiniz. Bu durumlarda, SharePoint Proje sisteminin genişletebilirsiniz.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint Proje sistem genel bakış
 SharePoint Proje sistem üzerinde temel bileşeni dayalı *SharePoint Proje öğeleri*. Bir SharePoint proje öğesi bir liste tanımı, Web Bölümü veya içerik türü gibi tek bir SharePoint özelleştirme temsil eder.  
  
 Bir SharePoint projesine bir veya daha fazla SharePoint Proje öğeleri içeren bir Visual Studio projesi ' dir. SharePoint projeleri özellikleri ve dağıtım için paketler proje öğeleri nasıl gruplandırılacağını tanımlamak ek bileşenler de içerir.  
  
 SharePoint Proje öğeleri ve SharePoint projeleri içeriği hakkında daha fazla bilgi için bkz: [öğe şablonları ve SharePoint Proje öğeleri için proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint Proje sistemini genişletme
 SharePoint Proje sistemini aşağıdaki yollarla genişletebilirsiniz:  
  
-   Kendi SharePoint proje öğesi türlerini tanımlama ve bunları yeni öğe şablonları ya da Visual Studio Proje şablonları ile ilişkilendirin. Örneğin, özel bir eylem ya da alan oluşturmak için bir SharePoint Proje öğe türüne tanımlayabilirsiniz. Daha fazla bilgi için bkz: [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Visual Studio'da yüklü olan SharePoint proje öğesi türleri genişletir. Örneğin, bir proje öğesi bir kısayol menü öğesi ekleyebilirsiniz **Çözüm Gezgini** ve geliştirici menü öğesi seçtiğinde proje öğesi özelleştirebilirsiniz. Daha fazla bilgi için bkz: [genişletmek SharePoint Proje öğeleri](../sharepoint/extending-sharepoint-project-items.md).  
  
-   SharePoint projeleri genişletir. Örneğin, öğeleri eklendiğinde veya SharePoint projelerden kaldırıldığında belirli görevler gerçekleştirmek için olay işleyicileri ekleyebilirsiniz. Daha fazla bilgi için bkz: [genişletmek SharePoint projeleri](../sharepoint/extending-sharepoint-projects.md).  
  
-   SharePoint Proje öğeleri ve SharePoint projeleri paketleme ve dağıtım davranışını genişletir. Örneğin, dağıtmak veya bir projeyi geri çekmek ya da Visual Studio belirli dağıtım adımları yürütüldüğünde ek özel görevler gerçekleştirebilirsiniz yürütmek için kendi dağıtım adımları oluşturabilirsiniz. Daha fazla bilgi için bkz: [genişletmek SharePoint paketleme ve dağıtım](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Ortak geliştirme görevleri
 SharePoint Proje sisteminin uzantılarında aşağıdaki yaygın görevleri gerçekleştirebilirsiniz:  
  
-   Özel bir dize verileri, proje öğeleri ve birkaç farklı türde proje dosyalarını kaydedin. Daha fazla bilgi için bkz: [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   SharePoint Proje sisteminin Visual Studio Otomasyon nesne modeli veya tümleştirme nesne modeli, karşılık gelen bir nesneye bir nesne Dönüştür veya tam tersi. Daha fazla bilgi için bkz: [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında Dönüştür](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)   
 [SharePoint projeleri genişletme](../sharepoint/extending-sharepoint-projects.md)   
 [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint Proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint Proje sistem türleri ve diğer Visual Studio Proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Visual Studio'da SharePoint araçları genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint Araç Uzantıları için Programlama Kavramları ve Özellikler](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  
