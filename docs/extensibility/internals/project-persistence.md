---
title: Proje Kalıcılık | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b85bb6155ca25abec67b582dc4d877dbd8290501
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131130"
---
# <a name="project-persistence"></a>Proje kalıcılığı
Kalıcılık projeniz için bir temel tasarım konusudur. Çoğu projeleri dosyaları temsil edecek proje öğeleri kullanın; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verisini dosya tabanlı olmayan projeleri de destekler. Proje ve proje dosyası tarafından sahip olunan her iki dosya kalıcı gerekir. IDE kendisini veya bir proje öğesi kaydetmek için projeyi bildirir.  
  
 Projeler için şablonlar, proje Fabrika geçirilir. Şablonları belirli proje türü gereksinimlerine göre tüm proje öğeleri başlatma desteklemelidir. Bu şablonları daha sonra proje dosyalarını kaydettiğiniz ve IDE çözüm aracılığıyla tarafından yönetilir. Daha fazla bilgi için bkz: [oluşturma proje örnekleri tarafından kullanarak proje Fabrikalarını](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) ve [çözümleri](../../extensibility/internals/solutions.md).  
  
 Proje öğeleri dosya tabanlı ya da dosya tabanlı olmayan olabilir:  
  
-   Dosya tabanlı öğeleri, yerel veya uzak olabilir. Dosyaları kendileri uzak sistemde kalır ancak C# Web projelerinde, örneğin, uzak bir sisteme dosyalarına yönelik bağlantıları yerel olarak kalıcı olmasını sağlar.  
  
-   Dosya tabanlı olmayan öğeler için bir veritabanı veya depo öğeleri kaydedebilirsiniz.  
  
## <a name="commit-models"></a>Modelleri Yürüt  
 Proje öğeleri bulunduğu karar verildikten sonra uygun yürütme modeli seçmeniz gerekir. Örneğin, bir dosya tabanlı modelinde yerel dosyalarla, her proje otonom olarak kaydedilebilir. Bir depo modelinde, bir işlemde birkaç öğeleri kaydedebilirsiniz. Daha fazla bilgi için bkz: [proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).  
  
 Dosya adı uzantılarını belirlemek için projeleri uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulamak bir nesnenin istemci etkinleştirme bilgileri sağlayan arabirim **Kaydet** iletişim kutusu — diğer bir deyişle, doldurmak için **kayıt türü**  aşağı açılan listesinde ve ilk dosya adı uzantısı yönetme.  
  
 IDE çağrıları `IPersistFileFormat` proje kendi proje kalıcı olursa belirtmek için proje arabirimde öğelerini uygun şekilde. Bu nedenle, kendi dosyasını ve biçimini tüm yönlerini nesnenin sahibi. Bu nesnenin biçimini adını içerir.  
  
 Burada öğeleri olmayan dosyaları durumda `IPersistFileFormat` hala nasıl dosya tabanlı olmayan olan öğeleri kaldı. Proje için .vbp dosyaları gibi dosyalar [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeleri veya .vcproj dosyaları [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projeleri, gerekir de kalıcı hale.  
  
 Eylemler için çalışan belge tablosu (RDT) IDE inceler ve hiyerarşi komutları geçirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimleri. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Yöntemi öğesi değişiklik olup olmadığını belirlemek için uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi değiştirilmiş öğesini kaydetmek için uygulanır.  
  
 Yöntemlere `IVsPersistHierarchyItem2` arabirimi öğeyi yeniden olup olmadığını ve öğe olabiliyorsa, yeniden belirlemek için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi, kaydedilen olmadan atılmak üzere değiştirilen öğeler neden uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)