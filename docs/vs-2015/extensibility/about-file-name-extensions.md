---
title: Dosya adı uzantıları hakkında | Microsoft Docs
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
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 680f9e9f79430ea53da3566686b058c44894e494
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776089"
---
# <a name="about-file-name-extensions"></a>Dosya Adı Uzantıları Hakkında
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage dosya uzantısına kaydolduğunuzda, bunu bir sürümü ile ilişkilendirirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu sürümü, birden çok önemli ise, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir bilgisayarda yüklü.  
  
 Vspackage'lar için dosya uzantıları HKEY_CLASSES_ROOT anahtarıyla ilişkili program tanımlayıcısı (ProgID) için işaret eden bir varsayılan değer altında kayıtlı.  
  
 .Vcproj dosya uzantısı için kayıt bilgileri örneği verilmiştir:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 İle ilişkili dosyaları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tutulan bir ProgID gibi olmalıdır `VisualStudio.vcproj.8.0`ürünün ürün sürümleri arasında dosya uzantısı ilişkilendirmeyi korumak için yan yana yüklemelerine izin vermek için. Sürüme özgü ProgID de açık düzenleme gibi ve benzeri üzerine yazmasını ya da diğer uygulamalar veya sürümleri tarafından üzerine yazılmasını kaygısı olmadan standart fiiller kullanmanıza olanak tanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Bazı durumlarda, bir dosya uzantısıyla ilişkili ProgID değiştirilmemelidir. Örneğin, ProgID .htm dosya uzantısı için (ProgID htmlfile =) çok sayıda işletim sisteminde yer kodlanmış zordur ve yaygın olarak bilinen ve kullanılan .htm ve .html dosyalarının ile ilişkidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Dosya Adı Uzantıları için Dosya İşleyicileri Belirtme](../extensibility/specifying-file-handlers-for-file-name-extensions.md)

