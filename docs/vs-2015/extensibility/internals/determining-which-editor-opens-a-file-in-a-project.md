---
title: Hangi Düzenleyicisi, bir projede bir dosya açar belirleme | Microsoft Docs
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
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 832fd838246c075087700494b09757184be687a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741610"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Projedeki Bir Dosyayı Hangi Düzenleyicinin Açacağını Belirleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kullanıcı bir projede bir dosya açıldığında, ortam sonunda açma uygun Düzenleyici veya tasarımcı bu dosya için bir yoklama işlemine geçer. Ortamı tarafından kullanılan ilk yordam, hem standart hem de özel düzenleyiciler için aynıdır. Bir dosyayı açmak için kullanılacak düzenleyicileri yoklanırken ölçütleri çeşitli ortam kullanır ve VSPackage ortamıyla bu işlem sırasında koordine etmek gerekir.  
  
 Örneğin, bir kullanıcı seçtiğinde **açık** komutunu **dosya** menüsü, ardından seçerse `filename`.rtf (veya başka bir dosyayı .rtf uzantılı) ortamı çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Çözümdeki tüm proje örneklerini sonunda dolaşma her proje için uygulama. Projeleri Talep belgesinde önceliğe göre tanımlayan bayrakları kümesini döndürür. En yüksek öncelikli kullanarak, ortam uygun çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yöntemi. Yoklama işlemi hakkında daha fazla bilgi için [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Çeşitli dosyalar projeleri, diğer projeleri tarafından talep edilmeyen tüm dosyaları talepleri. Bu şekilde, standart düzenleyicileri açmadan önce özel düzenleyicilerde belge açabilirsiniz. Çeşitli dosyalar projeleri talep bir dosya, ortam çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> standart düzenleyiciyle dosyayı açmak için yöntemi. Ortam kayıtlı düzenleyicileri .rtf dosyaları işleyen bir iç listesini denetler. Bu liste, şu anahtarı kayıt defterinde bulunur:  
  
 [Hkey_local_machıne\software\microsoft\visualstudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Ortam HKEY_CLASSES_ROOT\CLSID anahtarının alt anahtar DocObject sahip herhangi bir nesne için sınıf tanımlayıcıları da denetler. Dosya uzantısı var. bulunursa, uygulama Microsoft Word gibi katıştırılmış bir sürümünü yerinde Visual Studio'da oluşturulur. Bu belge nesneleri uygulayan bileşik dosyalar olmalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> arabirimi veya nesne uygulanmalı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> arabirimi.  
  
 .Rtf dosyaları kayıt defterinde hiçbir Düzenleyici fabrikası sonra ortamı HKEY_CLASSES_ROOT görünüyor \\.rtf anahtar ve düzenleyici belirtilen var. açar. Dosya uzantısı HKEY_CLASSES_ROOT bulunmazsa, ortam bir metin dosyası ise, dosyayı açmak için Visual Studio temel metin düzenleyicisini kullanır.  
  
 Temel metin düzenleyici başarısız olursa, dosyayı bir metin dosyası değil, ortam dosyası ikili düzenleyicisinin ardından kullanır gerçekleşir.  
  
 Bir ortam bir düzenleyici .rtf uzantısı, kayıt defterinde bulunamadı, bu Düzenleyici fabrikası uygulayan VSPackage'ı yükler. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> yeni VSPackage yöntemi. VSPackage çağrıları `QueryService` için `SID_SVsRegistorEditor`kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Düzenleyici fabrikası ortamı ile kaydetmek için yöntemi.  
  
 Ortam artık yeniden yeni kaydettiğiniz Düzenleyici fabrikası .rtf dosyaları bulmak için kayıtlı düzenleyicileri iç listesini denetler. Uygulamanız ortam çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi oluşturmak için dosya adını ve görünümü türünü geçirerek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

