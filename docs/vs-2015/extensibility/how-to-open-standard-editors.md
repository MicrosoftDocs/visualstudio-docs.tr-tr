---
title: 'Nasıl yapılır: standart düzenleyicileri açma | Microsoft Docs'
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
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6829ba4d1267d7a17c609f973b5ee6b570e9ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742500"
---
# <a name="how-to-open-standard-editors"></a>Nasıl yapılır: standart düzenleyicileri açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standart Düzenleyici açıldığında, dosyayı bir projeye özgü Düzenleyici belirtmek yerine bir dosya türü için standart bir düzenleyici belirlemek IDE sağlar.  
  
 Uygulamak için aşağıdaki yordamı tamamlayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yöntemi. Bu, bir proje dosyası'ı standart düzenleyicisinde açar.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Standart düzenleyiciyle OpenItem yöntemi uygulamak için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) belge veri nesnesi dosyası zaten açık olup olmadığını belirlemek için.  
  
2.  Dosya zaten açık değilse, dosya çağırarak resurface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> değerini belirterek yöntemi `IDO_ActivateIfOpen` için `grfIDO` parametresi.  
  
     Dosya açıksa ve arama projesinde değerinden farklı bir projeye belge sahibi, projeniz başka bir projeden açılmasını Düzenleyicisi olan bir uyarı alır. Dosya penceresini kullanıma sunulur.  
  
3.  Çalıştırılan Belge tablosu içinde değil veya belge açık değilse, çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi (`OSE_ChooseBestStdEditor`) dosyası için standart bir düzenleyiciyi açın.  
  
     Yöntemini çağırdığınızda, IDE aşağıdaki görevleri gerçekleştirir:  
  
    1.  IDE düzenleyicileri tarar / {guidEditorType} / hangi Düzenleyicisi belirlemek için kayıt defteri alt anahtarında uzantıları dosyayı açabilir ve bunu yapmak için en yüksek önceliğe sahip.  
  
    2.  Hangi düzenleyicinin dosyayı açabilmek için IDE belirledi sonra IDE çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Bu yöntem editör'ün uygulamasını çağırmak IDE için gerekli olan bilgileri döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> ve yeni açılan Belge site.  
  
    3.  Son olarak, IDE genel Kalıcılık arabirimi kullanarak belge yükler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  IDE daha önce hiyerarşi öğesini veya hiyerarşi kullanılabilir olduğunu belirlerse, IDE çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> proje düzeyi bağlamı için projenin metodunda <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> geri ile geçirilecek işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> yöntem çağrısı.  
  
4.  Döndürür bir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE çağırdığında, IDE işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> projenizi projenizden Düzenleyici get bağlamı izin vermek istiyorsanız.  
  
     Bu adım gerçekleştirildiğinde düzenleyiciye proje teklifi ek hizmetleri sağlar.  
  
     Belge görünüm nesnesi ve belge görünümü bir pencere çerçevesinde başarıyla yerleştirildi, nesne verilerini çağrılarak başlatılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Açma ve proje öğelerini kaydetme](../extensibility/internals/opening-and-saving-project-items.md)   
 [Nasıl yapılır: projeye özgü düzenleyicileri açma](../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl yapılır: açık belgeler için düzenleyicileri açma](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

