---
title: Bir Windows Installer paketi yazma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edb0a1d385129600372fc26693aec729751a768c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512874"
---
# <a name="author-a-windows-installer-package"></a>Bir Windows Installer paketi yazma
Windows Installer model veri sürücülerinde. Dosyaları kopyalayın ve kayıt defteri girdilerini Yaz için bir yordam betik yazmak yerine, örneğin, dosya ve kayıt defteri verileri içeren veritabanı tabloları içindeki satırları ve sütunları yazar.  
  
## <a name="database-entries"></a>Veritabanı girişleri  
VSPackage'ı yüklemek için bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek için veritabanı girişleri içermelidir:  
  
- Sistem sürümlerini bulmak için arama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (AppSearch, CompLocator RegLocator DrLocator ve imza içeren Windows Installer tabloları kullanarak), VSPackage'ı destekler.  
  
- Hiçbir desteklenen bir sürümü yüklemeyi iptal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklenir veya başka bir sistem gereksinimi VSPackage'ı (LaunchCondition tabloyu kullanarak) karşılanmazsa.  
  
- Bağımlı dosyaları (dizin bileşeni ve dosya tabloları kullanarak) ve VSPackage'ı yükleyin.  
  
- VSPackage için uygun bilgileri (kayıt defteri tabloyu kullanarak) kayıt defterine ekleyin.  
  
- VSPackage'ı, tümleştirme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çağırarak **devenv.exe/Setup** (özel tabloyu kullanarak).  
  
Daha fazla bilgi için [Windows Installer](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Kurulum Araçları  
Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketleri için bir geliştirme ortamı sağlar. Aşağıdaki ücretsiz araçlar mevcuttur:  
  
- InstallShield limited edition  
  
   Visual Studio aracılığıyla sınırlı bir InstallShield sürümünü edinebilirsiniz **yeni proje** iletişim. Genişletin **diğer proje türleri** seçip **Kurulum ve dağıtım**. InstallShield şablonu seçin.  
  
- Windows Installer XML araç takımı  
  
   Windows Installer XML (WiX) araç takımı XML kaynak dosyalarından Windows Installer paketleri oluşturur. WiX araç takımı, Microsoft açık kaynak projesidir. Yürütülebilir dosyalar ve kaynak kodunu indirebilirsiniz [Wix toolset](http://sourceforge.net/projects/wix).  
  
   Tümleştirin ticari ürünleri için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanarak [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], bkz: [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Installer ile VSPackage yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)