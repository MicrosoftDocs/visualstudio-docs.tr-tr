---
title: Yapılandırma dağıtımını yönetmek için proje | Microsoft Docs
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
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6ea732449c92b2dffb91c7e90ff738791b7c2f7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721354"
---
# <a name="project-configuration-for-managing-deployment"></a>Dağıtımı Yönetmek için Proje Yapılandırması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dağıtım, fiziksel olarak hata ayıklama ve yükleme için beklenen konuma bir yapı işleminden çıkış öğeleri taşıma işlemidir. Örneğin, bir Web uygulaması yerel makine üzerinde oluşturulmuş ve sonra sunucuda yerleştirilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dağıtım projeleri dahil, iki yolla destekler:  
  
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

