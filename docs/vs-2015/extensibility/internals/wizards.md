---
title: Sihirbazlar | Microsoft Docs
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
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbf2eceeb3ae8a3870954d53f8d85c46f3322d24
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747595"
---
# <a name="wizards"></a>Sihirbazlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir sihirbaz oluşturduktan sonra genellikle eklemek istediğiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başkalarının da kullanabilmesi için tümleşik geliştirme ortamı (IDE). Eklenen Sihirbazı ardından görünür **Yeni Proje Ekle** veya **Yeni Öğe Ekle** iletişim kutuları. Görmek için **Yeni Proje Ekle** veya **Yeni Öğe Ekle** iletişim kutuları, sağ tıklayın, açık bir çözümde **Çözüm Gezgini**, işaret **Ekle**, ve ardından **yeni proje** veya **yeni öğe**.  
  
 Sihirbazlar uygulanabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanıcıların bir ağaç görünümünü açtıklarında kullanılabilir değerler arasından seçim **Yeni Proje Ekle** iletişim kutusu veya **Yeni Öğe Ekle** iletişim kutusu veya ne zaman sağ bir öğeyi **Çözüm Gezgini**.  
  
 Sihirbazı, yeni bir proje veya ites adını yerelleştirme seçeneği sağlar ve bunlar Sihirbazı'nı seçtiğinizde, kullanıcıların göreceği simgesi belirleyebilirsiniz. Ayrıca yeni öğeler kullanılabilir diğer öğeleri göre görünme sırasını denetleyebilirsiniz: Öğeleri alfabetik olarak düzenlenmiş gerekmez.  
  
 Açıldığında, sihirbaza geçirilir özel parametrelere göre farklı şekilde başlayan bir Sihirbazı da sağlayabilirsiniz.  
  
 Bu bölümdeki konular, neden kullanan dosyalarının tartışmak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Yeni Proje Ekle** ve **Yeni Öğe Ekle** kullanılabilir sihirbazları ve şablonlar arasındaki Sihirbazı'nı listelemek için iletişim kutuları ve Sihirbazı IDE'de düzgün çalışması için karşılaması gereken gereksinimleri.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Dizin tanımı dosyaları şablonu genel bir bakış sağlar ve bunların klasörleri, sihirbaz .vsz dosyasına ve iletişim kutularında bir proje ile ilişkili şablon dosyaları görüntülemek için IDE içindeki işlevleri açıklanmaktadır.  
  
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Nasıl sihirbazları IDE başlatıldığında açıklar ve üç .vsz dosyasının bölümlerini listeler.  
  
 [Sihirbaz Arabirimi (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Açıklar `IDTWizard` sihirbazlar IDE içinde çalışacak şekilde uygulamalıdır arabirimi.  
  
 [Bağlam Parametreleri](../../extensibility/internals/context-parameters.md)  
 Sihirbazlar nasıl uygulandığını ve IDE, uygulama için bağlam parametreleri başarılı olduğunda ne olacağını açıklar.  
  
 [Özel Parametreler](../../extensibility/internals/custom-parameters.md)  
 Özel Parametreler sihirbaz başlatıldıktan sonra sihirbazın işlemi denetlemek için kullanmayı açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Yeni proje türleri tasarımı hakkında bilgi sağlayan ek konulara bağlantılar sağlar.  
  
 [İzlenecek yol: Sihirbaz oluşturma](http://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 İçin nasıl bir sihirbaz oluşturacağınızı gösterir.  
  
 [Projeleri Genişletme](../../extensibility/extending-projects.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeler ve çözümler, kod dosyaları ve kaynak dosyalarını ve kaynak denetimi uygulamak nasıl düzenlemek için.

