---
title: Proje türü tasarım kararları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bd6d2188b46093c5bfe18f9cabe985a953c000f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869489"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
Yeni bir proje türü oluşturmadan önce proje türü ile ilgili çeşitli tasarım kararları yapmalısınız. Hangi türde projelerinizi içerecek öğeleri, proje dosyaları kalıcı nasıl ve hangi taahhüt modeli kullanacağınıza karar vermeniz gerekir.  
  
## <a name="project-items"></a>Proje öğeleri  
 Projenizi dosya ya da soyut nesneler kullanacak mısınız? Dosyaları kullanıyorsanız, başvuru veya dizin tabanlı dosyaları olacak mı? Yerel veya uzak dosyaları veya soyut nesnelere giderek misiniz?  
  
 Proje öğelerinde, dosyaları veya bir veritabanı havuzu veya veri bağlantıları nesneleri gibi daha soyut nesneleri Internet üzerinden olabilir. Öğeleri dosyalarıdır, proje başvurusu tabanlı veya dizin tabanlı bir proje olabilir.  
  
 Başvuru tabanlı projelerde birden fazla projede öğeleri görünür. Ancak, bir öğeyi temsil eden gerçek dosyayı yalnızca bir dizinde bulunur. Dizin tabanlı projelerde dizin yapısında tüm proje öğeleri var.  
  
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
 [Açma ve proje öğelerini kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Proje kalıcılığı](../../extensibility/internals/project-persistence.md)   
 [Proje modeli öğeleri](../../extensibility/internals/elements-of-a-project-model.md)   
 [Proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)   
 [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)