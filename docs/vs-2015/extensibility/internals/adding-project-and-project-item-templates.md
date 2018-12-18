---
title: Proje ekleme ve proje öğesi şablonları | Microsoft Docs
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
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88411bd5fe985c398bd9e4e09ed3bcfb6a7610f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780223"
---
# <a name="adding-project-and-project-item-templates"></a>Proje ve Proje Öğesi Şablonları Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kendi proje türleri oluşturduğunuzda, yeni projeleri ve proje öğeleri standardını kullanarak eklemek için destek sağlamalısınız [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE) iletişim kutuları. Aşağıdaki konular, projeleri ve proje öğeleri eklemek için farklı teknik tartışın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Bağlamı](../../extensibility/internals/project-context.md)  
 Proje çoğu ortamda transpires ne için bağlam bilgisi sağlar açıklar.  
  
 [Proje Önceliği](../../extensibility/internals/project-priority.md)  
 Bir proje öğesi genellikle hangi proje öğesini açmak için kullanılan belirsizlik önlemeye yardımcı olmak için bir proje üyesi olduğu açıklanmaktadır.  
  
 [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)  
 Bir proje ve rol dosyaları açmak için kullanılan düzenleyicileri iki tür hakkında bilgi projenin bir proje öğesi açıldığında kullanmak için hangi Düzenleyicisi saptanırken çalar sağlar.  
  
 [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)  
 Neler olduğunu açıklar, bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proje oluşturulur.  
  
 [Yeni Öğe Ekleme İletişim Kutularına Öğe Ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Öğeler ekleme işlemi açıklanır **Yeni Öğe Ekle** iletişim kutusu.  
  
 [Yeni Proje İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 VSPackage'ı tarafından sunulan özel şablonlar içeren yeni bir dizin kaydetme bir örnek sağlar.  
  
 [Yeni Öğe Ekleme İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Dizinler için yeni bir dizi kaydetme bir örnek sağlar **Yeni Öğe Ekle** iletişim kutusu.  
  
 [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Proje sistemlerini genişletmeye için kullanılan komut öğeleri farklı türlerini listeler.  
  
 [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Genişletmek için kullanılan nesneleri için Catıdlerini listeler [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] proje sistemleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)  
 Doğası gereği bir proje için belirli bir düzenleyici bağlı bir öğeyi açmak için adım adım yönergeler sağlar.  
  
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)  
 Standart Düzenleyici açmak için adım adım yönergeler sağlar.  
  
 [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)  
 Proje alt kavramsal konular için bağlantılar sağlar. Proje alt türleri genişleten varolan [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projeleri.  
  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Yeni proje türleri tasarımı hakkında bilgi sağlayan ek konulara bağlantılar sağlar.

