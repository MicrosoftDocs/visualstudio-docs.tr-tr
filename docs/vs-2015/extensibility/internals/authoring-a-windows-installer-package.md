---
title: Bir Windows Installer paketi yazma | Microsoft Docs
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
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c51696cd41083e81fb1561eb8707c4f4844b32d5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742648"
---
# <a name="authoring-a-windows-installer-package"></a>Windows Installer Paketi Yazma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows Installer model veri sürücülerinde. Dosyaları kopyalayın ve kayıt defteri girdilerini Yaz için bir yordam betik yazmak yerine, örneğin, dosya ve kayıt defteri verileri içeren veritabanı tabloları içindeki satırları ve sütunları yazar.  
  
## <a name="database-entries"></a>Veritabanı girişleri  
 VSPackage'ı yüklemek için bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek için veritabanı girişleri içermelidir:  
  
- Sistem sürümlerini bulmak için arama [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (AppSearch, CompLocator RegLocator DrLocator ve imza içeren Windows Installer tabloları kullanarak), VSPackage'ı destekler.  
  
- Hiçbir desteklenen bir sürümü yüklemeyi iptal [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yüklenir veya başka bir sistem gereksinimi VSPackage'ı (LaunchCondition tabloyu kullanarak) karşılanmazsa.  
  
- Bağımlı dosyaları (dizin bileşeni ve dosya tabloları kullanarak) ve VSPackage'ı yükleyin.  
  
- VSPackage için uygun bilgileri (kayıt defteri tabloyu kullanarak) kayıt defterine ekleyin.  
  
- VSPackage'ı, tümleştirme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çağırarak **devenv.exe/Setup** (özel tabloyu kullanarak).  
  
  Daha fazla bilgi için [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Kurulum Araçları  
 Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketleri için bir geliştirme ortamı sağlar. İki ücretsiz araçlar şunlardır:  
  
- InstallShield Limited Edition  
  
   Visual Studio aracılığıyla sınırlı bir InstallShield sürümünü edinebilirsiniz **yeni proje** iletişim. Genişletin **diğer proje türleri** seçip **Kurulum ve dağıtım**. InstallShield şablonu seçin.  
  
- Windows Installer XML Araç Takımı  
  
   Araç takımı XML kaynak dosyalarından Windows Installer paketleri oluşturur. Araç takımı, Microsoft açık kaynak projesidir. Yürütülebilir dosyalar ve kaynak kodunu indirebilirsiniz [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Tümleştirin ticari ürünleri için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kullanarak [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], bkz: [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

