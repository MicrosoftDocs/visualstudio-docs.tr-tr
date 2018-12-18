---
title: Hizmetleri kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: e5d8aa9e6652aa41e59d160c5cf25aacd3390572
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219693"
---
# <a name="registering-services"></a>Hizmetleri kaydediliyor
İsteğe bağlı yükleme desteklemek için bir hizmet sağlayıcısı, küresel hizmetler ile kaydetmelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Geliştirme sırasında paketler için kaynak koduna öznitelikleri ekleyerek ve ardından paketlerini derlemek Hizmetleri ve hizmeti geçersiz kılmaları yönetilen hizmet sağlayıcıları kaydetme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Bu paket kaydetme ve dağıtımı için hazırlanma elde edilen derleme üzerinde RegPkg.exe yardımcı programı çalıştırır. Daha fazla bilgi için [nasıl yapılır: Hizmet kayıt](../misc/how-to-register-a-service.md).  
  
 Yönetilmeyen hizmet sağlayıcıları ile sağladıkları hizmetler kaydetmeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hizmetleri'nde sistem kayıt defterine bölümünü geçersiz kılar, bölüm veya hizmet. Aşağıdaki .reg dosyasını parçası nasıl SVsTextManager, hizmete kayıtlı gösterir:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 Yukarıdaki örnekte, sürüm numarası sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]7.1 veya 8.0, ' % s'anahtarı {F5E7E71D-1401-11d1-883B-0000F87579D2} hizmeti, SVsTextManager ve varsayılan değer {hizmet tanımlayıcısı (SID) gibi F5E7E720-1401-11D1-883B-0000F87579D2} GUID metin Yöneticisi hizmeti sağlayan VSPackage paketidir.  
  
## <a name="remote-services-and-background-threads"></a>Uzak Hizmetleri ve arka plan iş parçacıkları  
 Sağladığınız hizmetlerin uzaktan veya arka plan iş parçacığı için otomatik olarak kullanılabilir değil. Kullanılabilir hale getirmek oluşturun ve bir tür kitaplığını kaydetmek gerekir.  
  
 Visual Studio Kitaplığı'nı (VSL) kullanan yönetilmeyen koddan, tür kitaplığı bu şekilde kaydedebilirsiniz:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Yönetilen koddan oluşturma sonrası adımı böyle ekleyebilirsiniz:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)