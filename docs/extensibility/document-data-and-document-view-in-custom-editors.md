---
title: Özel düzenleyicilerde belge verileri ve belge görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2076f1a6c96aea717470fa1e955e5b9786f7fcc5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639821"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Belge verileri ve özel düzenleyicilerde belge görünümü
Özel bir düzenleyici iki bölümden oluşur: bir belge veri nesnesi ve bir belge görünümü nesnesi. Belge veri nesnesi adları önermek olarak görüntülenecek metin verileri temsil eder. Benzer şekilde, bir veya daha fazla windows belge veri nesnesi görüntüleneceği belge görünümü nesnesi (veya "Görünüm") temsil eder.  
  
## <a name="document-data-object"></a>Belge veri nesnesi  
 Bir belge veri nesnesi bir metin arabelleğinde metin veri gösterimidir. Belge metninin ve diğer bilgileri depolayan bir COM nesnesi olduğu. Belge veri nesnesi, ayrıca belge Kalıcılık işleme ve verileri birden çok görünüm sağlar. Daha fazla bilgi için bkz.  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> ve [belge Windows](../extensibility/internals/document-windows.md).  
  
 Özel düzenleyiciler ve tasarımcılar özelliğini kullanmak için <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesne veya kendi özel arabellek. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Basitleştirilmiş ekleme modeli için standart bir düzenleyici izler, birden çok görünüm destekler ve birden çok görünüm yönetmek için kullanılan olay arabirimleri sağlar.  
  
## <a name="document-view-object"></a>Belge görünüm nesnesi  
 Kod ve diğer metin görüntüleyen bir pencere bir belge olarak bilinir görünüm veya görünüm. Bir düzenleyici oluşturduğunuzda, metin tek bir pencerede görüntülenir ya da tek bir görünümde, seçebilirsiniz. Veya metin birden fazla penceresinde görüntülenen birden çok görünüm seçebilirsiniz. Seçtiğiniz uygulama bağlıdır. Örneğin, yan yana düzenleme gerekiyorsa, birden çok görünüm seçin. Her görünüm çalıştırılan Belge tablosu (RDT) tümleşik geliştirme ortamının (IDE) bir giriş ile ilişkilidir. Görünüm windows bir projeye ait ya da bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesne.  
  
 Bir belge veri nesnesinin birden çok görünüm düzenleyiciniz destekliyorsa, belge verileri ve belge görünümü nesneleri ayrı olmalıdır. Aksi takdirde, bunlar birlikte gruplandırılabilir. Daha fazla bilgi için [birden çok belge görünümünü desteklemek](../extensibility/supporting-multiple-document-views.md).  
  
 IDE çalıştırılan Belge tablosu her giriş için bir öğe tanımlayıcısı (ItemId) eşleştirerek görünümleri (örneğin, bir belge içeren bir çözüm kapatıldığında) olaylar hakkında bilgilendirir. Bunun hakkında daha fazla bilgi için bkz. [çalıştırılan Belge tablosu](../extensibility/internals/running-document-table.md).  
  
 Görünüm için özel bir düzenleyici oluşturmak için iki seçenek vardır. Görünüm bir ActiveX denetimi veya belge veri nesnesi kullanarak bir pencere içinde barındırıldığı yerinde etkinleştirme modeli biridir. Tarafından görünümü barındırıldığı Basitleştirilmiş ekleme modeli, ikincisi ise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> penceresi komutları işlemek için kullanılır. Yerinde etkinleştirme modeli hakkında daha fazla bilgi için bkz. [yerinde etkinleştirme](../extensibility/in-place-activation.md). Basitleştirilmiş ekleme modeli hakkında daha fazla bilgi için bkz: [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Birden çok belge görünümünü desteği](../extensibility/supporting-multiple-document-views.md)   
 [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md)   
 [Nasıl yapılır: görünümleri ekleme belge verileri](../extensibility/how-to-attach-views-to-document-data.md)   
 [Belge kilit tutucusu Yönetimi](../extensibility/document-lock-holder-management.md)   
 [Tek ve çoklu sekme görünümleri](../extensibility/single-and-multi-tab-views.md)   
 [Standart belge kaydetme](../extensibility/internals/saving-a-standard-document.md)   
 [Kalıcılık ve çalıştırılan Belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Hangi Düzenleyicisi, bir projede bir dosya açar belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Düzenleyici fabrikaları](../extensibility/editor-factories.md)