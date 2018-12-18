---
title: Aracı Windows kayıt defterinde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 234a3f50865e77f2c6b5a4057e6766b26d7ff521
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138453"
---
# <a name="tool-windows-in-the-registry"></a>Kayıt defterinde araç pencereleri
Araç pencereleri sağlamak VSPackages kaydetmeniz gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olarak araç penceresi sağlayıcıları. Varsayılan olarak bunu Visual Studio Paketi şablonu kullanılarak oluşturulan araç pencereleri. Araç penceresi sağlayıcıları varsayılan aracı pencere boyutunu ve konumunu, aracı pencere bölmesine ve yerleştirme stilini hizmet veren penceresinin GUID gibi görünürlük öznitelikleri belirtin sistem kayıt defteri anahtarlarının vardır.  
  
 Geliştirme sırasında öznitelikleri kaynak koduna ekleyerek ve ardından sonuç derlemesinde RegPkg.exe yardımcı programını çalıştırarak aracı windows yönetilen aracı penceresi sağlayıcılarını kaydedin. Daha fazla bilgi için bkz: [araç penceresi kaydetme](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Yönetilmeyen araç penceresi sağlayıcıların kaydedilmesi  
 Yönetilmeyen araç penceresi sağlayıcıları kaydetmeniz gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistem kayıt defteri ToolWindows bölümünde. Aşağıdaki .reg dosyasını parça nasıl dinamik araç penceresi kayıtlı gösterir:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Yukarıdaki örnekte ilk anahtarında, sürüm numarası sürümüdür [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]7.1 veya 8.0, {f0e1e9a1-9860-484d-ad5d-367d79aabf55} alt aracı pencere bölmesine (DynamicWindowPane) ve varsayılan değeri {GUID gibi 01069cdd-95ce-4620-ac21-ddff6c57f012} araç penceresi sağlama VSPackage GUID'dir. Float ve DontForceCreate alt anahtarlarının açıklaması için bkz: [araç penceresi ekran yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
 İkinci isteğe bağlı anahtar ToolWindows\Visibility, görünür duruma getirilmek üzere araç penceresi gerektiren komutlar GUID'lerini belirtir. Bu durumda, belirtilen hiçbir komut vardır. Daha fazla bilgi için bkz: [araç penceresi ekran yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)