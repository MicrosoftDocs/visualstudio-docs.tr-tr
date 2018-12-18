---
title: Çeşitli dosyalar proje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a637b37590a0aaf321a4e04896b2cbe12c29691f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129983"
---
# <a name="miscellaneous-files-project"></a>Çeşitli dosyalar proje
Proje öğeleri bir kullanıcı oturum açtığında, IDE çeşitli dosyalar projesine bir çözümdeki tüm projeleri üyesi olmayan tüm öğeleri atar.  
  
 Projeleri hangi Düzenleyicisi bir proje öğesi bir kullanıcı oturum açtığında kullanılan belirlemede önemli bir rol oynar. Bir projeye özgü Düzenleyici ya da standart düzenleyicisi kullanarak bazı dosyaları açmak için bir proje tasarlanabilir.  
  
 Bir projeye özgü Düzenleyici genellikle kullanıcı özel bilgi veya projeden özel arabirimlerini kullanan olması gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: açık projeye özgü düzenleyicileri](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Standart Düzenleyici herhangi dosya belirli bir uzantıya herhangi bir projede açabilirsiniz. Kullanıcı bazı standart düzenleyicileri gibi özelleştirebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeleri için metin düzenleyici, ancak yine kendi ortak karakter korur. Standart Düzenleyici kullanılarak oluşturulan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi.  
  
 Proje çözümdeki bir proje öğesi açabilirsiniz yanıt verirse, IDE herhangi bir dosyayı açar çeşitli dosyalar proje adlı özel bir proje sağlar.  
  
 Bir proje bağlamı dışında bir dosyanın açılması için bu özel Proje sağlar. İşlenmesi sırasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> yöntemi, çeşitli dosyalar proje her zaman çok düşük bir öncelik ile yanıtlar. Bu nedenle, çeşitli dosyalar her zaman veriyor dosyaları açabilir tüm yüksek öncelikli projesine proje.  
  
 Çeşitli dosyalar proje açıkça ile oluşturmak kullanıcı gerektirmez **yeni proje** iletişim kutusu. Ayrıca, çeşitli dosyalar proje proje üyelerin listesi kalıcı olarak yönetmez. Her kullanıcı için en son kullanılan dosya listesi kaydetmek için isteğe bağlı bir özellik kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Nasıl yapılır: açık projeye özgü düzenleyiciler](../../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: standart düzenleyicileri açın](../../extensibility/how-to-open-standard-editors.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)