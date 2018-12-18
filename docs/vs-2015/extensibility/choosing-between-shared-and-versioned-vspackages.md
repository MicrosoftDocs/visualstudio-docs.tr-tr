---
title: Paylaşılan ve sürümü tutulan Vspackage'lar arasında seçim yapma | Microsoft Docs
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
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9fcae5b736310424f220d08aefa4e061e1f6c860
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756835"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Paylaşılan ve Sürümü Tutulan VSPackage’lar Arasında Seçim Yapma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'nun farklı sürümleri aynı bilgisayarda bulunabilir. VSPackage'ları herhangi bir karışımını destekleyebilmesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümleri.  
  
 VSPackage yan yana yüklemeleri iki stratejileri, paylaşılan stratejisi ya da tutulan stratejisi üzerinden etkinleştirebilirsiniz. Her ikisini birden çok sürümünün varlığı uyum [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve sürümleri ilişkili [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Paylaşılan stratejide bir VSPackage'ı birden çok sürümünü kullanmak için kayıtlı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Tutulan stratejide birden çok VSPackage DLL'leri yüklenen her sürümü için bir tane [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] destek.  
  
## <a name="shared-vspackages"></a>Paylaşılan VSPackage'ları  
 Paylaşılan bir VSPackage'ı kullanarak uygun içinde birden çok sürümünü aynı VSPackage'ı kullandığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Paylaşılan bir VSPackage'ı uygulamak için aşağıdaki adımları izlemelisiniz:  
  
-   VSPackage, birden çok sürümü ile uyumlu hale getirmek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu nedenle iki şekilde de kullanılabilir:  
  
    -   Yalnızca en eski sürümünü özelliklerini kullanarak, VSPackage sınırlamak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] destek.  
  
    -   Sürümüne uyum sağlamak için VSPackage program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalıştığı içinde. Ardından, yeni hizmetler için sorgu başarısız olursa, VSPackage'ı eski sürümlerinde desteklenen diğer hizmet sunabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   VSPackage'ı uygun şekilde kaydedin. Daha fazla bilgi için [VSPackage kaydı](../extensibility/internals/vspackage-registration.md) ve [yönetilen VSPackage kaydı](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Dosya uzantılarını uygun şekilde kaydedin. Daha fazla bilgi için [yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Uygun sürümleri için VSPackage dağıtan bir yükleyici oluşturma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Daha fazla bilgi için [yükleme VSPackage'ları ile Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) ve [bileşen Yönetim](../extensibility/internals/component-management.md).  
  
-   Kayıt çakışma sorunu giderir. Daha fazla bilgi için [VSPackage kaydı](../extensibility/internals/vspackage-registration.md).  
  
-   Paylaşılan ve sürümü tutulan dosyaları birden çok sürümünün kaldırılması ve güvenli yüklenmesine izin vermek için başvuru sayımını uyduğunuzdan emin olun. Daha fazla bilgi için [bileşen Yönetim](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Sürümü tutulan Vspackage'lar  
 Tutulan VSPackage stratejisi altında bir VSPackage'ı her sürümü için oluşturduğunuz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] destek. Bunu yapmanın uygun sonraki sürümleri tarafından sağlanan hizmetlerin avantajlarından yararlanmak beklediğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], diğerleri etkilenmeden her VSPackage geliştirebilirsiniz. Bununla birlikte, tek bir kod tabanını veya birden çok bağımsız kod tabanlarında, birden çok ikili dosyaları oluşturma tutulan stratejisi paylaşılan stratejisi değerinden daha fazla ilk geliştirme gerektirdiği. Her sürümü için ayrı bir kurulum veya sürümleri algılayan tek bir kurulum oluşturmanız gerekir çünkü Ayrıca, ek kurulum çalışması gerekebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklenen ve, VSPackage'ı destekler.  
  
## <a name="binary-compatibility"></a>İkili uyumluluğu  
 Genel olarak, Visual Studio sonraki sürümleri için Visual Studio'nun önceki sürümleriyle geliştirilmiş yerel kodlu VSPackages ikili uyumluluğu sağlar. Bununla birlikte, üç önemli özel durum vardır:  
  
- Belirli bir ortak dil çalışma zamanı sürümü, VSPackage'ı kullanır ardından hangi sürümünde belirlemelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalışır.  
  
- VSPackage belirli bir özelliğini başka bir VSPackage'ı veya başka bir ürün üzerinde bir bağımlılık olabilir. Sonuç olarak, yalnızca bağımlılık burada sağlanırsa VSPackage'ı çalıştırabilirsiniz.  
  
- VSPackage bir güvenlik düzeltme tarafından etkilenebilecek bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hizmet paketi veya sonraki bir sürümü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu gibi durumlarda, önceki bir sürümü ile VSPackage geliştirilen [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] sürümlerinde çalışmayabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] güvenlik düzeltme uygulandıktan sonra. Ancak, paketiniz sonraki bir sürümü ile yeniden oluşturun ve önceki sürümlerinde de çalıştırmak sahip.  
  
  Yönetilen VSPackages bir sürümü kullanılarak oluşturulur gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] hedef sürümü, eşleşen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  VSPackage ikili dosyalarınız için ikili uyumluluğu için planlama yanı sıra, ayrıca çözümünü göz önünde bulundurun ve proje dosya biçimleri. Yeni bir proje türü, VSPackage oluşturur, bunu yalnızca bir sürüm veya birden çok sürümünü çalıştırıp çalıştıramayacağını karar vermelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Daha fazla bilgi için [özel projeleri yükseltme](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Bileşen Yönetimi](../extensibility/internals/component-management.md)

