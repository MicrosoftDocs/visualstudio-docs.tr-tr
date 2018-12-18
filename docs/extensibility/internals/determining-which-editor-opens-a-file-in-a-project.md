---
title: Hangi Düzenleyicisi, bir projede bir dosya açar belirleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 655a5a28e3e16a1b07c52c37ef00d89d145a17a1
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498548"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Hangi Düzenleyicisi, bir projede bir dosya açar belirleme
Bir kullanıcı bir projede bir dosya açıldığında, ortam sonunda açma uygun Düzenleyici veya tasarımcı bu dosya için bir yoklama işlemine geçer. Ortamı tarafından kullanılan ilk yordam, hem standart hem de özel düzenleyiciler için aynıdır. Bir dosyayı açmak için kullanılacak düzenleyicileri yoklanırken ölçütleri çeşitli ortam kullanır ve VSPackage ortamıyla bu işlem sırasında koordine etmek gerekir.  
  
 Örneğin, bir kullanıcı seçtiğinde **açık** komutunu **dosya** menüsü, ardından seçerse *filename.rtf* (veya başka bir dosya ile bir *.rtf*uzantısı), ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Çözümdeki tüm proje örneklerini sonunda dolaşma her proje için uygulama. Projeleri Talep belgesinde önceliğe göre tanımlayan bayrakları kümesini döndürür. En yüksek öncelikli kullanarak, ortam uygun çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yöntemi. Yoklama işlemi hakkında daha fazla bilgi için bkz. [proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Çeşitli dosyalar projeleri, diğer projeleri tarafından talep edilmeyen tüm dosyaları talepleri. Bu şekilde, standart düzenleyicileri açmadan önce özel düzenleyicilerde belge açabilirsiniz. Çeşitli dosyalar projeleri talep bir dosya, ortam çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> standart düzenleyiciyle dosyayı açmak için yöntemi. Ortam denetimleri, iç işleyen bir kayıtlı düzenleyicileri listesi *.rtf* dosyaları. Bu liste, şu anahtarı kayıt defterinde bulunur:  
  
 **Hkey_local_machıne\software\microsoft\visualstudio\\\<sürüm > \Editors\\\<Düzenleyici fabrikası GUID > \Extensions**
  
 Ortam ayrıca sınıf tanımlayıcıları iade **HKEY_CLASSES_ROOT\CLSID** bir alt olan tüm nesneleri için anahtar **DocObject**. Dosya uzantısı var. bulunursa, uygulama Microsoft Word gibi katıştırılmış bir sürümünü yerinde Visual Studio'da oluşturulur. Bu belge nesneleri uygulayan bileşik dosyalar olmalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> arabirimi veya nesne uygulanmalı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> arabirimi.  
  
 Hiçbir Düzenleyici fabrikası için ise *.rtf* ortamı arar sonra kayıt defterinde dosyaları **HKEY_CLASSES_ROOT\\.rtf** anahtar ve var. belirtilen Düzenleyicisi açılır. Dosya uzantısı, bulunamazsa **HKEY_CLASSES_ROOT**, bir metin dosyası ise ortam dosyasını açmak için Visual Studio temel metin düzenleyicisini kullanır.  
  
 Temel metin düzenleyici başarısız olursa, dosyayı bir metin dosyası değil, ortam dosyası ikili düzenleyicisinin ardından kullanır gerçekleşir.  
  
 Ortam için bir düzenleyici bulamazsa *.rtf* uzantısı, kayıt defterindeki bu Düzenleyici fabrikası uygulayan VSPackage'ı yükler. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> yeni VSPackage yöntemi. VSPackage çağrıları `QueryService` için `SID_SVsRegistorEditor`kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Düzenleyici fabrikası ortamı ile kaydetmek için yöntemi.  
  
 Ortam, iç listesini bulmak için yeni kaydettiğiniz Düzenleyicisi Fabrika için kayıtlı düzenleyicileri şimdi yeniden denetler *.rtf* dosyaları. Uygulamanız ortam çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi oluşturmak için dosya adını ve görünümü türünü geçirerek.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>