---
title: Yapılandırma dağıtımını yönetmek için proje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d3f632f7b271e3272a38dd79653b4c2ff238220
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951541"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
Dağıtım, fiziksel olarak hata ayıklama ve yükleme için beklenen konuma bir yapı işleminden çıkış öğeleri taşıma işlemidir. Örneğin, bir Web uygulaması yerel makine üzerinde oluşturulmuş ve sonra sunucuda yerleştirilir.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dağıtım projeleri dahil, iki yolla destekler:  
  
- Dağıtım işlemi konu.  
  
- Dağıtım işlemi Yöneticisi.  
  
  Çözümleri dağıtılmadan önce ilk dağıtım seçeneklerini yapılandırmak için bir dağıtım projesi eklemelisiniz. Dağıtım projesi zaten mevcut değilse seçtiğinizde oluşturmak istiyorsanız istenir **çözüm dağıtma** gelen **derleme** menü veya çözüme sağ tıklayın. Tıklayarak **Evet** açılır **Yeni Proje Ekle** iletişim kutusuyla **uzaktan Dağıtma Sihirbazı'nı** Seçili proje.  
  
  Uzaktan Dağıtma Sihirbazı'nı (Windows veya Web) uygulama türü, dahil etmek için proje çıktı grupları, dahil etmek istediğiniz herhangi bir ek dosyaları ve dağıtmak istediğiniz uzak bilgisayarı için ister. Sihirbazın son sayfasında, seçilen seçeneklerin bir özetini görüntüler.  
  
  Dağıtım işleminin konu olan projeler için alternatif bir ortam taşınmalıdır çıkış öğeleri oluşturur. Bu öğe için bir parametre olarak açıklanmıştır çıkış <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> olan birincil amaç Eğer projeleri Grup çıkışlarına izin vermek arabirim. Öğesinin uygulanmasına ilişkin daha fazla bilgi için `IVsProjectCfg2`, bkz: [çıkış için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).  
  
  Dağıtım işlemini yönetebilir, dağıtım projeleri dağıtma komutunu etkinleştir ve bu komut seçildiğinde yanıt. Dağıtım projeleri uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> dağıtımını gerçekleştirme ve çağrı yapmak için arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> rapor arabirimi durumu olayları dağıtın.  
  
  Yapılandırmaları, derleme veya dağıtım işlemlerini etkileyen bağımlılıkları belirtebilirsiniz. Derleme veya dağıtım bağımlılıklarıdır yerleşik veya önce veya sonra yapılandırmaları yerleşik veya dağıtıldığı dağıtılan projeleri. Projeleri arasındaki yapı bağımlılıklarını ile açıklanmıştır <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> arabirim ve bağımlılıkları ile dağıtma <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> arabirimi. Daha fazla bilgi için [derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md)   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)