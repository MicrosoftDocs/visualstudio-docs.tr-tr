---
title: Katkıda bulunan yeni öğe Ekle iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41947e3078eb3cd344774afe533a4fa0a9d8324a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511950"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna katkıda bulunma
Proje alt öğeleri için yeni bir tam dizin sağlayabilir **Yeni Öğe Ekle** kaydederek iletişim kutusu **Öğe Ekle** şablonlar altında **projeleri** kayıt defteri alt anahtarı.  
  
## <a name="register-add-new-item-templates"></a>Yeni Öğe Ekle şablonları kaydetme  
 Bu bölümde altında bulunan **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** kayıt defteri. Kayıt defteri girdilerini varsayar bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje kuramsal proje alt türü tarafından toplanır. Girişleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje aşağıda listelenmiştir.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 **AddItemTemplates\TemplateDirs** alt anahtar içerir, burada öğeler yapılan bulunan dizine olan yolu ile kayıt defteri girdilerini **Yeni Öğe Ekle** iletişim kutusu yerleştirilir.  
  
 Tüm ortam otomatik olarak yükleyen **AddItemTemplates** verileri altında **projeleri** kayıt defteri alt anahtarı. Bu veriler, temel proje uygulamaları için verilerin yanı sıra belirli proje alt türleri için verileri içerebilir. Her proje alt proje türü tarafından tanımlanan **GUID**. Proje alt alternatif kümesi olduğunu belirtebilirsiniz **Öğe Ekle** şablonları kullanılmalıdır belirli flavored proje örneği için destekleyerek `VSHPROPID_ AddItemTemplatesGuid` sabit listesinden alınmış <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> içinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Proje alt GUID değerini döndürmek için uygulaması. Varsa `VSHPROPID_AddItemTemplatesGuid` özelliği belirtilmedi, temel proje GUID kullanılır.  
  
 Öğeleri filtreleyebilirsiniz **Yeni Öğe Ekle** uygulayarak iletişim kutusu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> proje alt toplayıcısı nesne üzerinde arabirimi. Örneğin, bir veritabanı projesi toplayarak uygulayan bir proje alt bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje, filtreleyebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özel öğeleri gelen **Yeni Öğe Ekle** filtreleme uygulayarak ve iletişim kutusunu açın, ekleyebilirsiniz Veritabanı projeye özgü öğeleri destekleyerek `VSHPROPID_ AddItemTemplatesGuid` içinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Filtreleme ve öğeler ekleme hakkında daha fazla bilgi için **Yeni Öğe Ekle** iletişim kutusu, bkz: [Yeni Öğe Ekle iletişim kutusuna öğeleri ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Projeleri için genellikle kullanılan nesnelerin Catıdlerini](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)