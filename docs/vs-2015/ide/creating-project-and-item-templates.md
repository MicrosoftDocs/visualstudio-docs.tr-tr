---
title: Proje ve öğe şablonları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32c1c66484d5bdaff6ba37b8b37f7f86cb513e44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851666"
---
# <a name="creating-project-and-item-templates"></a>Proje ve öğe şablonları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje ve öğe şablonları, bazı temel kod ve kendi amaçları için kullanabilecekleri bir yapı kullanıcılara vermek yeniden kullanılabilir saptamalar sağlar.  
  
## <a name="visual-studio-templates"></a>Visual Studio şablonları  
 Bir dizi önceden tanımlanmış proje ve öğe şablonlarını yüklediğinizde yüklenen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Ve [!INCLUDE[csprcs](../includes/csprcs-md.md)] kullanılabilen Windows Forms uygulaması ve sınıf kitaplığı şablonları **yeni proje** iletişim kutusu, proje şablonları örnekleri verilmiştir. Yüklü öğe şablonları kullanılabilir **Yeni Öğe Ekle** iletişim kutusu ve kod dosyaları, XML dosyaları, HTML sayfaları ve stil sayfalarını gibi öğeleri içerir.  
  
 Bu şablonlar, kullanıcıların proje oluşturma veya genişleyen geçerli projeleri başlamak bir başlangıç noktası sağlar. Proje şablonları, belirli proje türü için gerekli dosyaları sağlar, standart derleme başvurularını içerir ve varsayılan proje özellikleri ve derleyici seçeneklerini ayarlayın. Öğe şablonları, yalnızca bir içerir, örneğin bir çok dosyalı öğe için doğru dosya adı uzantısına sahip boş dosya, saplama koda sahip bir kaynak kodu dosyaları, Tasarımcı bilgileri dosyası ve katıştırılmış kaynaklar karmaşıklığı değişebilir.  
  
 Yüklü Şablonlar yanı sıra **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları, kendi şablonlarınızı veya indirme ve topluluk tarafından oluşturulan şablonları yazabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md) ve [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Bir şablon içeriği  
 Tüm proje ve öğe şablonları ile birlikte yüklü olup olmadığını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya sizin tarafınızdan oluşturuldu, işlev aynı ilkeleri kullanarak ve benzer içeriğe sahip. Tüm şablonları aşağıdaki öğeleri içerir:  
  
- Şablonu kullanıldığında oluşturulan dosyalar. Bu, kaynak kodu dosyaları, katıştırılmış kaynaklar, proje dosyaları vb. içerir.  
  
- Bir .vstemplate dosyası. Bu dosya sağlayan meta veriler içeren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablonda görüntülemek için ihtiyaç duyduğu bilgileri **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları ve bir proje oluşturun veya öğesini şablonu. .Vstemplate dosyaları hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).  
  
  Bu dosyalar bir .zip dosyasına sıkıştırılmış ve doğru klasöre koymak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bunları otomatik olarak görüntüler. Proje şablonları görünür **Şablonlarım** bölümünü **yeni proje** iletişim kutuları ve öğe şablonları görünür **Yeni Öğe Ekle** iletişim kutuları. Şablon klasörleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: bulun ve düzenleme şablonlarını](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Başlangıç Paketleri  
 Başlangıç paketleri diğer topluluk üyeleriyle paylaşılabilen Gelişmiş şablonlardır. Starter Kit, belgeleri ve oluşturdukları kullanışlı, gerçek uygulamalar oluştururken, yeni araçlar ve programlama teknikleri öğrenin kullanıcılara yardımcı olmak için diğer kaynakları derlemek, kod örnekleri içerir. Temel içeriğini ve başlangıç paketleri için yordamlar şablonları olanlarla aynıdır. Daha fazla bilgi için [nasıl yapılır: başlangıç paketleri oluşturma](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)   
 [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)   
 [Nasıl Yapılır: Başlangıç Paketleri Oluşturma](../ide/how-to-create-starter-kits.md)



