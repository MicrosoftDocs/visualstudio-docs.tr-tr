---
title: Bileşen Yönetimi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00a6ea41d631c171700db75361b7aa0beed81cc2
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510874"
---
# <a name="component-management"></a>Bileşen Yönetimi
Windows Installer görevlerin birimleri (bazen WICs veya yalnızca bileşenleri olarak adlandırılır), Windows Yükleyici bileşenleri adlandırılır. Bir GUID, yükleme ve başvuru sayımı Windows Installer kullanan ayarları için temel birimdir her WIC tanımlar.  
  
 VSPackage yükleyicinizi oluşturmak için birden çok ürünlerin kullanabilseniz de, Windows Installer'ın kullanımı bu tartışma varsayılır (*.msi*) dosyaları. Böylece her zaman doğru başvuru sayımı gerçekleşir yükleyicinizi oluştururken, dosyayı dağıtım doğru bir şekilde yönetmeniz gerekir. Sonuç olarak, farklı sürümlerini ürünü değil müdahale veya birbiriyle yükleme karışımında Kes ve senaryoları kaldırın.  
  
 Windows Yükleyicisi'nde başvuru sayımı, bileşen düzeyinde gerçekleşir. Kaynaklarınızı dikkatli bir şekilde düzenlemeniz gerekir — dosyaları, kayıt defteri girdileri ve benzeri — bileşenlere. Diğer kuruluş düzeyi vardır — modülleri, özellikler ve ürünleri gibi — farklı senaryolarda yardımcı olabilir. Daha fazla bilgi için [Windows Installer Temelleri](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Yan yana yüklemesi için Kurulum yazma yönergeleri  
  
-   Yazar dosyaları ve kayıt defteri anahtarlarını, kendi bileşenlerine sürümleri arasında paylaşılır.  
  
     Bunun yapılması, bunları bir sonraki sürümünde kolayca kullanmasına olanak tanır. Örneğin, küresel olarak kayıtlı bir tür kitaplıklarını dosya uzantıları, diğer öğeleri kayıtlı **HKEY_CLASSES_ROOT**ve benzeri.  
  
-   Paylaşılan bileşenler ayrı birleştirme modülleri gruplayın.  
  
     Bu strateji, yazar doğru ilerletme yan yana yükleme için yardımcı olur.  
  
-   Paylaşılan dosyaları ve kayıt defteri anahtarlarını sürümleri arasında aynı Windows Yükleyici bileşenlerini kullanarak yükleyin.  
  
     Farklı bir bileşen kullanırsanız, dosyaları ve kayıt defteri girdilerini tutulan bir VSPackage kaldırılır ancak başka bir VSPackage yüklüdür kaldırılır.  
  
-   Oluşturulan ve paylaşılan öğeleri aynı bileşende karıştırmayın.  
  
     Bunun yapılması, genel bir konum ve yalıtılmış konumlara sürümlü öğeleri paylaşılan öğeleri yüklemek mümkün kılar.  
  
-   Tutulan dosyalarının olduğu noktaya paylaşılan kayıt defteri anahtarlarını yok.  
  
     Bunu yaparsanız, başka bir sürümü tutulan VSPackage yüklendiğinde paylaşılan anahtarların üzerine yazılır. Dosyanın ikinci sürümü kaldırdıktan sonra anahtar işaret ettiği dosya kayboluyor.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Paylaşılan ve sürümü tutulan Vspackage'lar arasında seçin](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage Kurulum senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)