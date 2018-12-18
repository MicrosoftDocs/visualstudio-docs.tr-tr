---
title: Proje türü temel bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7daf114bb31019a499bc17e287df923107ee1a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891576"
---
# <a name="project-type-essentials"></a>Proje Türü Temel Bileşenleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje birden fazla dil için APIleri içerir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayrıca, kendi proje türleri oluşturmanızı sağlar.  
  
 Özel komutlar, düzenleyiciler ve araç pencerelerini eklemek istiyorsanız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], yeni bir proje türü oluşturmak zorunda kalmadan yapabilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Araç Pencerelerini Genişletme ve Özelleştirme](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Benzer şekilde, sağlanan davranışını özelleştirmek istiyorsanız [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] yapabileceğiniz proje türleri, proje alt türleri kullanarak. Daha fazla bilgi için [proje alt türleri](../../extensibility/internals/project-subtypes.md).  
  
  Yeni bir proje türü dışında bir dil tabanlı projeler için oluşturmalısınız [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir veya daha fazlasını desteklemek istiyorsanız:  
  
- Derleme  
  
- Dağıtım  
  
- Birden çok yapılandırma  
  
- Kaynak denetimi  
  
- Hata Ayıklama  
  
- Çözüm Gezgini'nde proje öğeleri  
  
- **Proje Aç** veya **yeni proje** iletişim kutuları  
  
- Proje iç içe geçme  
  
- Proje türleri özellikleri hakkında daha fazla bilgi için aşağıdakilere bakın:  
  
- Proje türleridir kümesi arabirimleri uygulayan nesneler vspackage'ta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bekliyor. C# proje türü geliştirmek için kullanıyorsanız, yönetilen paket çerçevesini proje sınıfları için gerekli arabirimleri uygulayabilir ve bu uygulamayı devral olanak verir. Daha fazla bilgi için [bir proje türü (C#) uygulamak için yönetilen paket çerçevesini kullanarak](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- C++ geliştiricileri için HierUtil Kitaplığı'nda sınıflar benzer bir şekilde çalışır. Daha fazla bilgi için [derleme içinde değil: Proje türü (C++) uygulamak için HierUtil7 proje sınıfları kullanarak](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Bir .exe veya .dll derleme tipik kaynak kodu dosyaları dışında veri proje türlerini destekler. Örneğin, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] veritabanı projeleri diskte depolanan dosyaların komut ve sorgu için başvurular içerir ve komutları ekleme **Çözüm Gezgini** yürütmek için betikleri ve bir veritabanı, ancak projeleri sorguları desteklemez davranış oluşturun. Daha fazla bilgi için [açma ve kaydetme proje öğeleri](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Tüm dosyaları kullanmak bir proje türü yok. Örneğin, bir proje türü, bir veritabanında onunla ilişkili tüm verileri saklayabilirsiniz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje türleri, projeleri ve proje öğeleri için verileri nasıl kalıcı üzerinde tam denetim verir. Daha fazla bilgi için [proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).  
  
- Proje türleri sağlamalıdır bir *proje fabrikası*, bir proje örneği oluşturan bir nesne olan her tür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açmak veya bu proje türüne göre bir proje oluşturmak için bildirilir. Daha fazla bilgi için [oluşturma proje örnekleri tarafından kullanarak proje Fabrikalarını](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Proje türleri, projeleri ve proje öğeleri için şablonlar sağlamanız gerekir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcılar yeni projeler oluşturmak ve yeni öğeler eklemek için var olan projeleri şablonları kullanır. Daha fazla bilgi için [ekleme proje ve proje öğesi şablonları](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Proje türleri hata ayıklama ve yayın gibi birden çok yapılandırmaları destekler. Kullanıcılar, farklı bir proje yapılandırmaları sağladığınız özellik sayfalarını kullanarak değiştirebilirsiniz. Daha fazla bilgi için [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)