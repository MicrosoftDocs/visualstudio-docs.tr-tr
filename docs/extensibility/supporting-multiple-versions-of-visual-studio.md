---
title: Visual Studio'nun birden çok sürümünü destekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3837116a33dc5608f75e48e3397273f65e5ea260
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817996"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio'nun Birden Çok Sürümünü Destekleme
Terim *yan yana* yükleyin ve birden çok sürümünü aynı bilgisayarda bir ürün tutmak anlamına gelir. VSPackage'ları için birden fazla Visual Studio sürümleri aynı bilgisayarda yüklü bir kullanıcısı olabilir anlamına gelir. Ancak, tek bir Visual Studio sürümüne yüklenen, VSPackages sürümlerini yan yana sahip olamaz.  
  
 Visual Studio sürümlerini yan yana yüklenmiş olabilir, VSPackage yapmadan önce aşağıdakileri dikkate alın:  
  
- İzlemek istediğiniz hangi yan yana uygulama stratejisi belirlemeniz gerekir.  
  
   Daha fazla bilgi için [seçme arasında paylaşılan ve sürümü tutulan Vspackage'lar](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
- Çözüm ve proje dosya biçimleri uygulaması stratejinizi sığması gerekir.  
  
   Daha fazla bilgi için [özel projeleri yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) ve [yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Böylece sürümlenmiş bileşenler ve tüm sürümler arasında paylaşılan bileşenleri doğru yüklü ve kayıtlı olan yükleyicinizi uygulaması stratejinizi işlemesi gerekir.  
  
   Daha fazla bilgi için [yükleme VSPackage'ları ile Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) ve ayrıca [bileşen Yönetim](../extensibility/internals/component-management.md).  
  
  > [!NOTE]
  >  Visual Studio sürümünü yüklemek de ilgili sürümünü yükler [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Örneğin, Visual Studio 2010 ve Visual Studio 2012 aynı bilgisayara yüklenmesi de 4.0 ve 4.5 sürümlerini yükler [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]sırasıyla.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Paylaşılan ve Sürümü Tutulan VSPackage’lar Arasında Seçim Yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Yan yana, VSPackage sorunlarını gidermek nasıl açıklar.  
  
 [Yan Yana Dağıtım için Dosya Adı Uzantılarını Kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 VSPackage dosya ilişkilendirmeleri yan yana senaryoda nasıl kaydedebilirsiniz açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Installer ile VSPackage Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
