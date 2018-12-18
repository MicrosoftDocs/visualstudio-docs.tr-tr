---
title: Proje türü tasarım kararları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62d1a0e78aebd39c1f305c3480d6a418b382b4fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781796"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir proje türü oluşturmadan önce proje türü ile ilgili çeşitli tasarım kararları yapmalısınız. Hangi türde projelerinizi içerecek öğeleri, proje dosyaları kalıcı nasıl ve hangi taahhüt modeli kullanacağınıza karar vermeniz gerekir.  
  
## <a name="project-items"></a>Proje öğeleri  
 Projenizi dosya ya da soyut nesneler kullanacak mısınız? Dosyaları kullanıyorsanız, başvuru veya dizin tabanlı dosyaları olacak mı? Yerel veya uzak dosyaları veya soyut nesnelere giderek misiniz?  
  
 Proje öğelerinde, dosyaları veya bir veritabanı havuzu veya veri bağlantıları nesneleri gibi daha soyut nesneleri Internet üzerinden olabilir. Öğeleri dosyalarıdır, proje başvurusu tabanlı veya dizin tabanlı bir proje olabilir.  
  
 Başvuru tabanlı projelerde birden fazla projede öğeleri görünür. Ancak, bir öğeyi temsil eden gerçek dosyayı yalnızca bir dizinde bulunur. Dizin tabanlı projelerde dizin yapısında tüm proje öğeleri var. Daha fazla bilgi için [projelerinde NIB: öğesi Yönetimi](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Yerel öğeler, uygulamanın yüklendiği bilgisayarda depolanır. Uzak öğeler, yerel bir ağda ayrı bir sunucuya veya başka bir yerde Internet üzerinde depolanabilir.  
  
## <a name="project-file-persistence"></a>Proje dosyası kalıcılığı  
 Veriler yaygın düz dosya sistemleri veya yapılandırılmış depolama alanında depolanır? Standart Düzenleyici veya projeye özgü Düzenleyicisi'ni kullanarak dosyaları açılacak?  
  
 Verilerini kalıcı hale getirmek için çoğu uygulama verilerini bir dosyaya kaydedin ve kullanıcı geri gerekir veya gözden geçirme bilgi değiştirdiğinizde okuyun.  
  
 Bileşik dosyalar olarak da bilinir, yapılandırılmış bir depolamada, genellikle birçok bileşen nesne modeli (COM) nesne tek bir dosyada kalıcı verilerini depolamak gerektiğinde kullanılır. Yapılandırılmış depolama ile birçok farklı yazılım bileşenlerini tek disk dosya paylaşabilir.  
  
 Öğeler, projenizdeki için Kalıcılık ile ilgili dikkate alınması gereken birkaç seçeneğiniz vardır. Aşağıdaki seçeneklerden herhangi birini gerçekleştirebilirsiniz:  
  
- Her dosyayı ayrı ayrı da değiştirildiğinde kaydedin.  
  
- Pek çok işlem tek bir yakalama **Kaydet** işlemi.  
  
- Dosyaları yerel olarak kaydedin ve ardından bir sunucuda yayımlayın veya uzak bir nesne için bir veri bağlantısı öğesi temsil ettiğinde proje öğeleri kaydedilirken başka bir yaklaşım kullanın.  
  
  Kalıcılık hakkında daha fazla bilgi için bkz: [proje kalıcılığı](../../extensibility/internals/project-persistence.md) ve [açma ve kaydetme proje öğeleri](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Proje taahhüt modeli  
 Kalıcı veri nesneleri açılacak doğrudan modu veya hizmetteki modunda?  
  
 Veri nesneleri doğrudan modda açıldığında, verilerde yapılan değişiklikleri hemen veya kullanıcının dosyayı el ile kaydettiğinde dahil edilir.  
  
 Veri nesneleri, hizmetteki modunu kullanarak açıldığında değişiklikleri bellekte geçici bir konuma kaydedilir ve kullanıcı dosyayı kaydetmeyi el ile seçer kadar iletilmez. O zaman tüm değişiklikleri birlikte olmalıdır veya hiçbir değişiklik yapılmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Projelerinde NIB: öğesi yönetimi](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Açma ve proje öğelerini kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Proje kalıcılığı](../../extensibility/internals/project-persistence.md)   
 [Proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md)   
 [Proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)   
 [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)

