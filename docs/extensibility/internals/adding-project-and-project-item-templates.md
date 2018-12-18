---
title: Proje ekleme ve proje öğesi şablonları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db53ddce3161097347760026aea16a51f8098519
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499640"
---
# <a name="add-project-and-project-item-templates"></a>Proje ve proje öğesi şablonları ekleme
Kendi proje türleri oluşturduğunuzda, yeni projeleri ve proje öğeleri standardını kullanarak eklemek için destek sağlamalısınız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) iletişim kutuları. Aşağıdaki konular, projeleri ve proje öğeleri eklemek için farklı teknik tartışın.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Proje bağlamı](../../extensibility/internals/project-context.md)  
 Proje çoğu ortamda transpires ne için bağlam bilgisi sağlar açıklar.  
  
 [Proje önceliği](../../extensibility/internals/project-priority.md)  
 Bir proje öğesi genellikle hangi proje öğesini açmak için kullanılan belirsizlik önlemeye yardımcı olmak için bir proje üyesi olduğu açıklanmaktadır.  
  
 [Çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md)  
 Bir proje ve rol dosyaları açmak için kullanılan düzenleyicileri iki tür hakkında bilgi projenin bir proje öğesi açıldığında kullanmak için hangi Düzenleyicisi saptanırken çalar sağlar.  
  
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)  
 Neler olduğunu açıklar, bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje oluşturulur.  
  
 [Yeni Öğe Ekle iletişim kutusu öğeleri Ekle](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Öğeler ekleme işlemi açıklanır **Yeni Öğe Ekle** iletişim kutusu.  
  
 [Yeni Proje iletişim kutusu için dizinleri Ekle](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 VSPackage'ı tarafından sunulan özel şablonlar içeren yeni bir dizin kaydetme bir örnek sağlar.  
  
 [Yeni Öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Dizinler için yeni bir dizi kaydetme bir örnek sağlar **Yeni Öğe Ekle** iletişim kutusu.  
  
 [Proje sistemlerini genişletmeye yönelik IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Proje sistemlerini genişletmeye için kullanılan komut öğeleri farklı türlerini listeler.  
  
 [Projeleri için genellikle kullanılan nesnelerin Catıdlerini](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Genişletmek için kullanılan nesneleri için Catıdlerini listeler [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proje sistemleri.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md)  
 Doğası gereği bir proje için belirli bir düzenleyici bağlı bir öğeyi açmak için adım adım yönergeler sağlar.  
  
 [Nasıl yapılır: standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)  
 Standart Düzenleyici açmak için adım adım yönergeler sağlar.  
  
 [Proje alt türleri](../../extensibility/internals/project-subtypes.md)  
 Proje alt kavramsal konular için bağlantılar sağlar. Proje alt türleri genişleten varolan [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeleri.  
  
 [Proje türleri](../../extensibility/internals/project-types.md)  
 Yeni proje türleri tasarımı hakkında bilgi sağlayan ek konulara bağlantılar sağlar.