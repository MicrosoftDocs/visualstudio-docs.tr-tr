---
title: Paylaşılan ve sürümü tutulan Vspackage'lar arasında seçim yapma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bb3cebb9cdc00f6e4ef486ef6330cf2b18c6dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817308"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Paylaşılan ve sürümü tutulan Vspackage'lar arasında seçin
Visual Studio'nun farklı sürümleri aynı bilgisayarda bulunabilir. VSPackage'ları herhangi bir karışımını destekleyebilmesi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sürümleri.  
  
 VSPackage yan yana yüklemeleri iki stratejileri, paylaşılan stratejisi ya da tutulan stratejisi üzerinden etkinleştirebilirsiniz. Her ikisini birden çok sürümünün varlığı uyum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve sürümleri ilişkili [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Paylaşılan stratejide bir VSPackage'ı birden çok sürümünü kullanmak için kayıtlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Tutulan stratejide birden çok VSPackage DLL'leri yüklenen her sürümü için bir tane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] destek.  
  
## <a name="shared-vspackages"></a>Paylaşılan VSPackage'ları  
 Paylaşılan bir VSPackage'ı kullanarak uygun içinde birden çok sürümünü aynı VSPackage'ı kullandığınızda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Paylaşılan bir VSPackage'ı uygulamak için aşağıdaki adımları izlemelisiniz:  
  
- VSPackage, birden çok sürümü ile uyumlu hale getirmek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bu nedenle iki şekilde de kullanılabilir:  
  
  - Yalnızca en eski sürümünü özelliklerini kullanarak, VSPackage sınırlamak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] destek.  
  
  - Sürümüne uyum sağlamak için VSPackage program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştığı içinde. Ardından, yeni hizmetler için sorgu başarısız olursa, VSPackage'ı eski sürümlerinde desteklenen diğer hizmet sunabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- VSPackage'ı uygun şekilde kaydedin. Daha fazla bilgi için [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) ve [yönetilen VSPackage kaydı](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için [yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Uygun sürümleri için VSPackage dağıtan bir yükleyici oluşturma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Daha fazla bilgi için [Windows Installer ile VSPackage yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) ve [bileşen Yönetim](../extensibility/internals/component-management.md).  
  
- Kayıt çakışma sorunu giderir. Daha fazla bilgi için [VSPackage kaydı](../extensibility/internals/vspackage-registration.md).  
  
- Paylaşılan ve sürümü tutulan dosyaları birden çok sürümünün kaldırılması ve güvenli yüklenmesine izin vermek için başvuru sayımını uyduğunuzdan emin olun. Daha fazla bilgi için [bileşen Yönetim](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Sürümü tutulan Vspackage'lar  
 Tutulan VSPackage stratejisi altında bir VSPackage'ı her sürümü için oluşturduğunuz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] destek. Bunu yapmanın uygun sonraki sürümleri tarafından sağlanan hizmetlerin avantajlarından yararlanmak beklediğiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], diğerleri etkilenmeden her VSPackage geliştirebilirsiniz. Bununla birlikte, tek bir kod tabanını veya birden çok bağımsız kod tabanlarında, birden çok ikili dosyaları oluşturma tutulan stratejisi paylaşılan stratejisi değerinden daha fazla ilk geliştirme gerektirdiği. Her sürümü için ayrı bir kurulum veya sürümleri algılayan tek bir kurulum oluşturmanız gerekir çünkü Ayrıca, ek kurulum çalışması gerekebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklenen ve, VSPackage'ı destekler.  
  
## <a name="binary-compatibility"></a>İkili uyumluluğu  
 Genel olarak, Visual Studio sonraki sürümleri için Visual Studio'nun önceki sürümleriyle geliştirilmiş yerel kodlu VSPackages ikili uyumluluğu sağlar. Bununla birlikte, üç önemli özel durum vardır:  
  
- Belirli bir ortak dil çalışma zamanı sürümü, VSPackage'ı kullanır ardından hangi sürümünde belirlemelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalışır.  
  
- VSPackage belirli bir özelliğini başka bir VSPackage'ı veya başka bir ürün üzerinde bir bağımlılık olabilir. Sonuç olarak, yalnızca bağımlılık burada sağlanırsa VSPackage'ı çalıştırabilirsiniz.  
  
- VSPackage bir güvenlik düzeltme tarafından etkilenebilecek bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hizmet paketi veya sonraki bir sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bu gibi durumlarda, önceki bir sürümü ile VSPackage geliştirilen [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sürümlerinde çalışmayabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] güvenlik düzeltme uygulandıktan sonra. Ancak, paketiniz sonraki bir sürümü ile yeniden oluşturun ve önceki sürümlerinde de çalıştırmak sahip.  
  
  Yönetilen VSPackages bir sürümü kullanılarak oluşturulur gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] hedef sürümü, eşleşen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
  VSPackage ikili dosyalarınız için ikili uyumluluğu için planlama yanı sıra, ayrıca çözümünü göz önünde bulundurun ve proje dosya biçimleri. Yeni bir proje türü, VSPackage oluşturur, bunu yalnızca bir sürüm veya birden çok sürümünü çalıştırıp çalıştıramayacağını karar vermelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Daha fazla bilgi için [özel projelerini yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Installer ile VSPackage yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Bileşen Yönetimi](../extensibility/internals/component-management.md)