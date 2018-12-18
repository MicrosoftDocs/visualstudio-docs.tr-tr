---
title: Özel düzenleyicilerde belge verileri ve belge görüntüleme | Microsoft Docs
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
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55f082711de306e9dd22fdf55e769282ad150f17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755294"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir düzenleyici iki bölümden oluşur: bir belge veri nesnesi ve bir belge görünümü nesnesi. Adları önermek gibi belge verileri nesne görüntülenecek metin verileri temsil eder ve belge görünümü nesnesi (veya "Görünüm") bir veya daha fazla windows belge veri nesnesi görüntüleneceği temsil eder.  
  
## <a name="document-data-object"></a>Belge veri nesnesi  
 Bir belge veri nesnesi bir metin arabelleğinde metin veri gösterimidir. Belge metninin ve diğer bilgileri depolar, belge Kalıcılık işler ve birden çok görünüm verilerini sağlayan bir COM nesnesi olduğu. Daha fazla bilgi için bkz.  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> ve [belge Windows](../extensibility/internals/document-windows.md).  
  
 Özel düzenleyiciler ve tasarımcılar özelliğini kullanmak için <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesne veya kendi özel arabellek. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Basitleştirilmiş ekleme modeli için standart bir düzenleyici izler, birden çok görünüm destekler ve birden çok görünüm yönetmek için kullanılan olay arabirimleri sağlar.  
  
## <a name="document-view-object"></a>Belge görünüm nesnesi  
 Kod ve diğer metin görüntüleyen bir pencere bir belge olarak bilinir görünüm veya görünüm. Bir düzenleyici oluşturduğunuzda, metin tek bir pencerede görüntülenir, tek bir görünüm veya metin birden fazla penceresinde görüntülenen birden çok görünüm seçebilirsiniz. Seçtiğiniz uygulama bağlıdır. Örneğin, yan yana düzenleme gerekiyorsa, birden çok görünüm seçin. Her görünüm çalıştırılan Belge tablosu (RDT) tümleşik geliştirme ortamının (IDE) bir giriş ile ilişkilidir. Görünüm windows bir projeye ait ya da bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesne.  
  
 Bir belge veri nesnesinin birden çok görünüm düzenleyiciniz destekliyorsa, belge verileri ve belge görünümü nesneleri ayrı olmalıdır. Aksi takdirde, bunlar birlikte gruplandırılabilir. Daha fazla bilgi için [birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md).  
  
 IDE çalıştırılan Belge tablosu her giriş için bir öğe tanımlayıcısı (ItemId) eşleştirerek görünümleri (örneğin, bir belge içeren bir çözüm kapatıldığında) olaylar hakkında bilgilendirir. Bunun hakkında daha fazla bilgi için bkz. [çalıştırılan Belge tablosu](../extensibility/internals/running-document-table.md).  
  
 Görünüm için özel bir düzenleyici oluşturmak için iki seçenek vardır. Görünüm bir ActiveX denetimi veya belge veri nesnesi kullanarak bir pencere içinde barındırıldığı yerinde etkinleştirme modeli biridir. Tarafından görünümü barındırıldığı Basitleştirilmiş ekleme modeli, ikincisi ise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> penceresi komutları işlemek için kullanılır. Yerinde etkinleştirme modeli hakkında daha fazla bilgi için bkz. [yerinde etkinleştirme](../misc/in-place-activation.md). Basitleştirilmiş ekleme modeli hakkında daha fazla bilgi için bkz: [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birden çok belge görünümünü destekleme](../extensibility/supporting-multiple-document-views.md)   
 [Basitleştirilmiş ekleme](../extensibility/simplified-embedding.md)   
 [Nasıl yapılır: belge verilerine görünüm ekleme](../extensibility/how-to-attach-views-to-document-data.md)   
 [Belge kilit tutucusu Yönetimi](../extensibility/document-lock-holder-management.md)   
 [Tek ve çoklu sekme görünümleri](../extensibility/single-and-multi-tab-views.md)   
 [Standart belge kaydetme](../extensibility/internals/saving-a-standard-document.md)   
 [Kalıcılık ve çalıştırılan Belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Bir projedeki bir dosyayı hangi düzenleyicinin açacağını belirleme](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Düzenleyici Fabrikaları](../extensibility/editor-factories.md)

