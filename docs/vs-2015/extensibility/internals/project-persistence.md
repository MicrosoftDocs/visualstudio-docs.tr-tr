---
title: Proje kalıcılığı | Microsoft Docs
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
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff836f56601adeba7b3df675207701f6e2d6e7fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729551"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kalıcılık, projeniz için bir temel tasarım noktadır. Çoğu proje dosyaları temsil edecek proje öğeleri kullanın. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verisini dosya tabanlı olmayan projeleri de destekler. Proje ve proje dosyası tarafından sahip olunan dosyaları, her iki kalıcı gerekir. IDE kendisi veya bir proje öğesi kaydetmek için projeyi bildirir.  
  
 Şablonları projeleri için proje fabrikasına geçirilir. Şablonları, belirli bir proje türünü gereksinimlerine göre tüm proje öğelerinin başlatma desteklemelidir. Bu şablonları daha sonra proje dosyaları olarak kaydedilen ve IDE çözüm aracılığıyla yönetilir. Daha fazla bilgi için [oluşturma proje örnekleri tarafından kullanarak proje Fabrikalarını](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) ve [çözümleri](../../extensibility/internals/solutions.md).  
  
 Proje öğeleri, dosya tabanlı veya dosya tabanlı olmayan olabilir:  
  
-   Yerel veya uzak dosya tabanlı öğeleri olabilir. Uzak sistemde dosyaların kalıcı ise C# Web projelerinde, örneğin, uzak bir sistem dosyalarına yönelik bağlantıları yerel olarak kalıcı hale getirin.  
  
-   Dosya tabanlı olmayan öğeler için bir veritabanı veya havuz öğeleri kaydedebilirsiniz.  
  
## <a name="commit-models"></a>Yürütme modelleri  
 Proje öğeleri bulunduğu yere karar verdikten sonra uygun bir yürütme modeli seçmeniz gerekir. Örneğin, bir dosya tabanlı model ile yerel dosyaları, her proje otonom olarak kaydedilebilir. Bir depo modelde bir işlemde birden çok öğe kaydedebilirsiniz. Daha fazla bilgi için [proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).  
  
 Dosya adı uzantıları belirlemek için Projeler uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulamak bir nesnenin istemci etkinleştirme bilgi sağlayan bir arabirimi **Kaydet** iletişim kutusu — diğer bir deyişle, doldurmak için **Kaydet**  aşağı açılan listesinde ve ilk dosya adı uzantısı yönetin.  
  
 IDE çağrıları `IPersistFileFormat` arabirimde proje, proje kalıcı olması belirtmek için proje öğelerini uygun şekilde. Bu nedenle, dosya ve biçim tüm yönlerini nesnenin sahibi. Bu nesnenin biçim adını içerir.  
  
 Öğe olmadığı dosyaları durumda `IPersistFileFormat` nasıl dosya tabanlı olmayan hala geçerli olduğunu öğeleri kalıcı olarak tutulur. Proje için .vbp dosyaları gibi dosyalar [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projeleri veya .vcproj dosyaları [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projeleri gerekir ayrıca kalıcı.  
  
 Eylemler için çalıştırılan Belge tablosu (RDT) IDE inceler ve hiyerarşi komutları geçirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimleri. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Yöntemi öğesi değiştirilmiş olup olmadığını belirlemek için uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi değiştirilmiş öğesini kaydetmek için uygulanır.  
  
 Yöntemlerde `IVsPersistHierarchyItem2` arabirimi, öğeyi yeniden olup olmadığını ve öğeyi yeniden yüklemek olabilir, belirlemek için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi neden olmadan kaydedilmesini atılması değiştirilen öğeleri için uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: Yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

