---
title: RegPkg yardımcı programı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130963"
---
# <a name="regpkg-utility"></a>RegPkg yardımcı programı
> [!NOTE]
>  Visual Studio'da paketleri kaydetmek için tercih edilen .pkgdef dosyalarını kullanarak yoludur. Bu uzantı dağıtımı için bir gereksinimdir VSIX dağıtımı için sistem kayıt defteri erişmek zorunda kalmadan sağlar. Pkgdef dosyaları kullanılarak oluşturulur [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md). Visual Studio paketi dağıtımı hakkında daha fazla bilgi için bkz: [sevkiyat Visual Studio uzantıları](../../extensibility/shipping-visual-studio-extensions.md).  
  
 RegPkg.exe yardımcı programı ile VSPackage kaydeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve dağıtım için hazırlar. Bu yardımcı program arka planda VSPackage geliştirme sırasında kullanılır. Böylece oluşturup bir VSPackage Deneysel kovanında çalıştırın derleme işleminin bir parçası çalışır.  
  
 RegPkg sistem kayıt defteri komut dosyaları çeşitli biçimlerde oluşturabilir. Bu komut dosyalarını .msi projeleri veya Windows Installer XML araç takımı dosyaları gibi dağıtım projelerinde dahil edebilirsiniz.  
  
 RegPkg.exe genellikle \< *Visual Studio SDK yükleme yolu*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg bu söz dizimi aşağıdaki gibidir:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Belirtilen adla kayıt gerçekleştirir  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kök dizini.  
  
 /regfile:filename  
 Kayıt defteri güncelleştiriliyor yerine .reg dosyasını oluşturur.  /Vrgfile veya /rgsfile veya /wixfile ile kullanılamaz.  
  
 /rgsfile:filename  
 Kayıt defteri güncelleştiriliyor yerine bir .rgs dosyası oluşturur.  /Vrgfile veya/regfile veya /wixfile ile kullanılamaz.  
  
 /vrgfile:filename  
 Kayıt defteri güncelleştiriliyor yerine bir .vrg dosyası oluşturur.  / Regfile veya /rgsfile veya /wixfile ile kullanılamaz.  
  
 /rgm  
 Rgs dosya yanı sıra .rgm dosyası oluşturur.  /Rgsfile ile birlikte olması gerekir.  
  
 /wixfile:filename  
 Kayıt defteri güncelleştiriliyor yerine bir Windows Installer XML araç takımı uyumlu dosyası oluşturur.  / Regfile veya /rgsfile veya /vrgfile ile kullanılamaz.  
  
 /codebase  
 Derleme yerine CodeBase kaydı zorlar.  
  
 /Assembly  
 CodeBase yerine derleme kaydı zorlar.  
  
 / kaydı  
 Bu paket kaydını siler.  Kullanılamaz  
  
 / regfile veya /vrgfile veya /rgsfile veya /wixfile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../../extensibility/internals/vspackages.md)  
 [RegPkg Paket Kaydı Sorunlarını Giderme](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)