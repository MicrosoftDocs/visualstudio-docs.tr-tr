---
title: Çeşitli dosyalar projeleri | Microsoft Docs
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
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5786eb21813125237a35ed185542b5f73bdc839
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777896"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje öğeleri bir kullanıcı oturum açtığında, IDE bir çözümde bir proje üyesi olmayan tüm öğeler için çeşitli dosyalar projeleri atar.  
  
 Projeleri, hangi Düzenleyici bir proje öğesi bir kullanıcı oturum açtığında kullanılan belirlemede önemli bir rol oynar. Bir proje, projeye özgü Düzenleyici ya da bir standart düzenleyici kullanarak belirli dosyaları açmaya tasarlanabilir.  
  
 Bir projeye özgü Düzenleyicisi genellikle kullanıcı özel bilgilere sahip veya projeyle özel arabirimlerini kullanan gerektirir. Daha fazla bilgi için [nasıl yapılır: açık projeye özgü düzenleyicileri](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Standart Düzenleyici herhangi bir dosyanın belirli bir uzantıya bir proje açabilirsiniz. Kullanıcı gibi bazı standart düzenleyicileri özelleştirebilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeleri için metin düzenleyici, ancak yine de kendi genel karakter korur. Standart düzenleyicileri kullanılarak oluşturulan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi.  
  
 Çözümdeki hiçbir proje proje öğesi açabilirsiniz yanıt verirse, herhangi bir dosyayı açan çeşitli dosyalar projeleri adlı özel bir proje IDE sağlar.  
  
 Bu özel Proje, projenin bağlamı dışında bir dosyanın açılması için sağlar. İşleme sırasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> yöntemi, çeşitli dosyalar projeleri her zaman çok düşük bir öncelikte yanıtlar. Bu nedenle, çeşitli dosyalar her zaman dosyaları açmak için herhangi bir yüksek öncelik projesine sayıları proje.  
  
 Çeşitli dosyalar projeleri açıkça ile oluşturmak kullanıcı gerektirmez **yeni proje** iletişim kutusu. Ayrıca, çeşitli dosyalar projeleri, proje üyelerin listesi kalıcı olarak yönetmez. İsteğe bağlı bir özellik, her kullanıcı için en son kullanılan dosyaların listesini kaydetmek için kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)

