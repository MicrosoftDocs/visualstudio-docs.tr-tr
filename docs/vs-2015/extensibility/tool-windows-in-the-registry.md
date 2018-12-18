---
title: Windows kayıt defterinde aracı | Microsoft Docs
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
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f24c51b3cf1a4930fa0cc496e12ffd31170389b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781913"
---
# <a name="tool-windows-in-the-registry"></a>Aracı Windows kayıt defteri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç pencereleri sağlayan VSPackages kaydetmeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gibi araç penceresi sağlayıcıları. Varsayılan olarak bunu Visual Studio Paketi şablonu kullanılarak oluşturulan araç pencereleri. Araç penceresi sağlayıcıları gibi varsayılan araç penceresi boyut ve konum, GUID araç penceresi bölmesi ve yerleştirme stilini olarak hizmet veren penceresinin görünürlük özniteliklerini belirtin sistem kayıt defteri anahtarları vardır.  
  
 Geliştirme sırasında kaynak koduna öznitelikleri ekleyerek ve ardından sonuç derlemesinde RegPkg.exe yardımcı programı çalıştırmaya araç pencereleri yönetilen aracı penceresi sağlayıcılarını kaydedin. Daha fazla bilgi için [araç penceresi kaydetme](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Yönetilmeyen araç penceresi sağlayıcılar kaydediliyor  
 Yönetilmeyen araç penceresi sağlayıcıları ile kaydetmeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sistem kayıt defterine ToolWindows bölümünde. Dinamik araç penceresini nasıl kaydedilmiş olabilir aşağıdaki .reg dosyasını parçası gösterir:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Yukarıdaki örnekte ilk anahtarında, sürüm numarası sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]7.1 veya 8.0, {f0e1e9a1-9860-484d-ad5d-367d79aabf55} alt araç penceresi bölmesi (DynamicWindowPane) ve varsayılan değer {GUID gibi 01069cdd-95ce-4620-ac21-ddff6c57f012} sağlayan araç penceresi VSPackage GUID'dir. Kayan ve DontForceCreate anahtarlarını açıklaması için bkz: [araç penceresi ekran yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
 İkinci isteğe bağlı anahtar ToolWindows\Visibility, görünür hale sağlayan araç penceresi gerektiren komutlarının GUID'leri belirtir. Bu durumda, belirtilen herhangi bir komut vardır. Daha fazla bilgi için [araç penceresi ekran yapılandırması](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage'ı temel bileşenleri](../misc/vspackage-essentials.md)

